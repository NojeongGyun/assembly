<pre>
- <mark>문자열 처리 명령어</mark> -
MOVS(문자열 복사), CMPS(문자열 비교), STOS (저장), LODS (로드), SCAS (검색) 가 있습니다. 해당 명령어 모두 ESI/EDI의 값을 변경 시키는 명령들 입니다.
해당 기능을 수행 할 떄 크기를 1바이트로 수행하고 싶다면, B(Byte)를 명령어 뒤에 붙이고, 2바이트는 W(WORD), 4바이트는 D(DOUBLE WORD)를 붙여 사용합니다.

<b>ESI</b> -
ESI는 원본 메모리 주소를 가리키는 레지스터입니다. 목적의 문자를 읽어오는 위치를 가리킬 떄 사용합니다.

<b>EDI</b> -
EDI는 목적지 메모리 주소를 가리키는 레지스터입니다. 목적의 문자를 쓰는 위치를 가리킬 떄 사용합니다.

<b>MOVS</b> -

    
<b>CMPS</b>-

    
<b>STOS</b> -

    
<b>LODS</b> -

    
<b>SCAS</b> -

    
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

<b>STD</b>
DF = 1인 상태로 설정이 됩니다. 이 뜻은 해당 위치에서 ESI/EDI가 감소한다는 뜻입니다.
ex) ESI = 1004 // 1000부터 1004까지 "HELLO"라는 문자가 있다고 가정    
    EDI = 2004 // ESI로부터 받은 시작 주소(2004)    
    STD        // 문자열 처리 명령어인 MOVSB를 시행할 떄 마다 ESI/EDI 1씩 감소 시키는 명령    
    MOVSB      // EDI[2004] <- ESI[2004] ('O')
    MOVSB      // EDI[2003] <- ESI[2003] ('L')
    MOVSB      // EDI[2002] <- ESI[2002] ('L')
    MOVSB      // EDI[2001] <- ESI[2001] ('E')
    MOVSB      // EDI[2000] <- ESI[2000] ('H')
  
p2 
ESI, EDI는 소스인덱스, 목적인덱스로 쓰임
레지스터는 각 기능이 있지만, 기능 없이 범용으로도 쓰임

MOVE - 이동  
CMP - 비교
STO - 저장
LOAD - 불러오기

+ sb, sw, sd 는 메모리 to 메모리(문자열만 가능)

p3
rep - 카운터 레지스터(REX, ECX, CX..)가 0이 될 때까지 반복하는 것
RSI - 읽기
RDI - 쓰기

movsb - 메모리에 복사하는 명령어인데, RSI(원본), RDI(목적지)가 필요한 이유는 말 그대로 목적지에 원본을 저장하기 때문이다.
rep movsb RDI RSI //  ECX만큼 RSI[0] -> RDI[0], RSI[1] -> RDI[1]... RSI[ECX] -> RDI[ECX] 
                      위치는 RSI, RDI는 ECX만큼 주소값이 증가하고, 값은 RSI는 그대로고, RDI는 ECX만큼의 수만큼 앞의 문자열이 바뀝니다.


p7
repe - RCX = 0, ZF = 1일때까지 반복

p11
cmp는 무조권 결과를 플래그레지스터에 저장하기에 레지스터에 따라 점프할지말지 결정함

p25
bx의 목적


p27 에서 C언어로 실행하시오.
  viscode - 

정렬을 하는 이유 - 시간을 덜 들여 값을 찾기 위해서




  
</pre>



