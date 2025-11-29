<pre>
- <mark>문자열 처리 명령어</mark> -
MOVS(문자열 복사), CMPS(문자열 비교), STOS (저장), LODS (로드), SCAS (검색) 가 있습니다. 해당 명령어 모두 ESI/EDI의 값을 변경 시키는 명령들 입니다.
해당 기능을 수행 할 떄 크기를 1바이트로 수행하고 싶다면, B(Byte)를 명령어 뒤에 붙이고, 2바이트는 W(WORD), 4바이트는 D(DOUBLE WORD)를 붙여 사용합니다.

<b>ESI</b> -
ESI는 원본 메모리 주소를 가리키는 레지스터입니다. 목적의 문자를 읽어오는 위치를 가리킬 떄 사용합니다.

<b>EDI</b> -
EDI는 목적지 메모리 주소를 가리키는 레지스터입니다. 목적의 문자를 쓰는 위치를 가리킬 떄 사용합니다.

<b>MOVS</b> -
ESI에서 원하는 바이트를 읽어서 EDI에 저장합니다. 원래는 x86 자체 구조 때문에 메모리 to 메모리는 되지 않지만, MOVS 명령은 메모리 to 메모리가 가능합니다.
MOVSB/MOVSW/MOVSD - 1BYTE/2BYTE/4BYTE

<b>CMPS</b>-
ESI의 주소의 값*([ESI])와 EDI의 주소의 값([EDI])를 비교하여 ZF, CF 등의 플래그에 영향을 줍니다.
CMPSB/CMPSW/CMPSD - 1BYTE/2BYTE/4BYTE    
    
<b>STOS</b> -
AL/AX/EAX에서 ESI의 주소에 값([ESI])을 저장합니다. 
STOSB/STOSW/STOSD(AL/AX/EAX)- 1BYTE/2BYTE/4BYTE

<b>LODS</b> -
ESI의 주소의 값([ESI])을 AL/AX/EAX에 저장합니다. STOS와 상반되는 명령입니다.
STOSB/STOSW/STOSD(AL/AX/EAX)- 1BYTE/2BYTE/4BYTE

<b>SCAS</b> -
ESI 주소의 값([EDI])과 AL/AX/EAX 비교하여 ZF 등 플래그 설정합니다. STOS & LODS와 CMPS를 합친 개념이라고 봐도 무방합니다.
SCANSB,SCANSW/SCANSD - 1BYTE/2BYTE/4BYTE
    
- <mark>반복 접두사</mark> -
반복 접두사란 명령어를 여러 번 자동으로 반복하게 만드는 접두사입니다. 반복 접두사는 REP, REPZ | REPE, REPNZ | REPENE가 있습니다.

<b>REP</b> -
REP 반복 접두사는 ECX가 ECX > 0 조건에 만족할 떄까지 반복합니다. 즉 ECX가 0이 되면 반복이 종료되니다.

<b>REPZ | REPE</b> -
REPZ와 REPE는 이름만 다르지 기능을 같고, ECX > 0 조건에 만족하거나, 아니면 ZF = 1 조건에 만족하면 반복합니다. 
즉 ECX가 0이 되거나 혹은 ZF가 0이 되는 조건에서 둘 중 하나라도 만족하면 반복을 종료합니다.

<b>REPNZ | REPENE</b> -
REPNZ와 REPNE는 이름만 다르지 기능을 같고, ECX > 0 조건에 만족하거나, 아니면 ZF = 0 조건에 만족하면 반복합니다. 
즉 ECX가 0이 되거나 혹은 ZF가 1이 되는 조건에서 둘 중 하나라도 만족하면 반복을 종료합니다. REPZ | REPE 기능과 상반되는 명령입니다.

- <mark>DF</mark> -
Direction Flag(DF)는 문자열 처리 명령에서 ESI/EDI가 증가할지 감소할지 결정하는 플래그이며, CLD(증가), STD(감소)로 설정됩니다.
만약 CLD나 STD를 사용하지 않고 문자열 처리 명령을 사용하면, 기본적으로 CLD가 적용 됩니다.
    
<b>CLD</b> -
DF = 0인 상태로 설정이 됩니다. 이 뜻은 해당 위치에서 ESI/EDI가 증가한다는 말입니다.
ex) ESI = 1000 // 1000부터 1004까지 "HELLO"라는 문자가 있다고 가정 (영문자는 1바이트)    
    EDI = 2000 // ESI주소로 부터 받을 시작 주소(2000)    
    CLD        // 문자열 처리 명령어인 MOVSB를 시행할 떄 마다 ESI/EDI 1씩 증가 시키는 명령    
    MOVSB      // EDI[2000] <- ESI[2000] ('H')
    MOVSB      // EDI[2001] <- ESI[2001] ('E')
    MOVSB      // EDI[2002] <- ESI[2002] ('L')
    MOVSB      // EDI[2003] <- ESI[2003] ('L')
    MOVSB      // EDI[2004] <- ESI[2004] ('O')

<b>STD</b> -
DF = 1인 상태로 설정이 됩니다. 이 뜻은 해당 위치에서 ESI/EDI가 감소한다는 뜻입니다.
ex) ESI = 1004 // 1000부터 1004까지 "HELLO"라는 문자가 있다고 가정    
    EDI = 2004 // ESI로부터 받은 시작 주소(2004)    
    STD        // 문자열 처리 명령어인 MOVSB를 시행할 떄 마다 ESI/EDI 1씩 감소 시키는 명령    
    MOVSB      // EDI[2004] <- ESI[2004] ('O')
    MOVSB      // EDI[2003] <- ESI[2003] ('L')
    MOVSB      // EDI[2002] <- ESI[2002] ('L')
    MOVSB      // EDI[2001] <- ESI[2001] ('E')
    MOVSB      // EDI[2000] <- ESI[2000] ('H')

- <mark>Two-Dimensional Arrays</mark> -
2차원 배열은 행과 열로 이루어진 표 형태의 배열을 말합니다. 어셈블리에서 2차원 배열 자료형이 따로 존재하지 않아, 2차원 배열을 1차원 배열로 씁니다.
2차원 배열을 1차원 배열로 쓸 수 있는 Row-major order, Column-major order 이렇게 2가지 방법이 있습니다.

<b>Column-major order</b> -
열 우선방식으로, 1열이 끝나면 2열, 2열이 끝나면 3열,... 이런 방법으로 반복되어 1차원 배열로 구성하는 방식입니다.
        
<b>Row-major order</b> -
행 우선방식으로, 1행이 끝나면 2행으로 가고, 2행이 끝나면 3행,.. 이런 방법으로 반복되어 1차원 배열로 구성하는 방식입니다.

- <mark>base-index</mark> -
레지스터는 각자의 사용 방식이 있는데 base주소를 저장할려고 하면 Ebx,bx,...를 씁니다. 하지만 레지스터들은 범용이기에 다른 레지스터를 써도 상관 없습니다.
어셈블리에 배열이 있다면 base주소는 시작 배열주소를 기준으로 삼습니다. 데이터의 지정된 크기에 따라 다음 배열을 알고 싶다면 + 1, + 2, +4, ...(BYTE/WORD/DWORD...)
를 base주소에 더하여 알 수 있습니다.

</pre>
