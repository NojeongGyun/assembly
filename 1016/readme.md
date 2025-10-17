<pre>
- <mark>어셈블리 명령어</mark> -
어셈블리 명령어는 총 4가지로 1형식, 2형식, 3형식, 4형식이 있습니다. 각 사용할 때의 사용 형식은  
1형식 - 연산자
2형식 - 연산자 Operand1
3형식 - 연산자 Operand1 Operand2
4형식 - 연산자 Operand1 Operand2 Operand3
로 형식이 증가 될수록 피연산자가 1개씩 늘어나는걸 볼 수 있습니다. 
연산자는 Operands에 대한 명령이고, Operand에서는 메모리, 레지스터, 숫자를 넣을 수 있습니다.
명령어 형식은 단순히 구조에만 치중되어 있는 것이 아니라, 사용 시 여러 가지 주의사항도 있습니다.

<b>어셈블리 명령어 주의 사항</b>
3형식부터 2개 이상의 Operand가 사용이 되는데, 명령어를 실행 할 떄 Operand끼리의 데이터 크기가 같아야하고,  메모리 to 메모리 즉, 메모리끼리의 행동이 제한됩니다.

ex) - Operand 데이터 크기 예시 -
    MOV EAX, EBX(32비트, 32비트) 가능(o) 
    MOV EAX AH(32비트, 8비트) 불가능(x)

    - 메모리 to 메모리 예시 -
    MOV [1000h] [2000h] (2000h메모리에서 1000h메모리로 이동) 불가능(x)

- 여기서 데이터 크기가 다른 것 끼리 매칭하거나, 메모리 to 메모리를 해결 할 수 있는 방법이 있습니다.
데이터 크기가 다른 것 끼리 매칭 할려면 레지스터 0확장, 메모리 to 메모리를 해결 할려면 레지스터를 이용하여 옮기는 방법입니다.
먼저 레지스터0확장부터 살펴보자면  MOVZX 비트수reg(32비트, 16비트만 가능), 비트수reg/mem(16비트, 8비트만 가능) 이고 왼쪽레지스터가 오른쪽 레지스터 or 메모리의 데이터  크기보다 커야 합니다. 
    
ex) 
    - 레지스터 0확장 -
      .data
      myWord DW 1234h   ; Define word(DW)는 16비트이기에 myword라는 변수 선언 후 16비트 1234h의 메모리를 넣음 (DB =8비트, DW = 16비트, DD = 32비트, DQ = 64비트)
      
      .code
      MOV BX, 5678h
      MOVZX EAX, myWord ; 16비트 메모리 → 32비트 레지스터 0확장 EAX는 (0000 0000 0000 0000 0001 0010 0011 0100) 데이터 저장
      MOVZX EBX, BX     ; 16비트 레지스터 → 32비트 레지스터 0확장 EBX는 (0000 0000 0000 0000 0101 0110 0111 1000) 데이터 저장

    - 메모리 to 메모리 해결(1) [데이터만 이동]-
      .data
      source DW 1234h // 원본 메모리
      target DW 0     // 목적지 메모리

      .code
      MOV AX, source // source -> AX
      MOV [target], AX // "source"를 담은 AX레지스터가 "target"으로 선언된 메모리에 데이터 복사 이동 


    - 메모리 to 메모리 해결(2) [서로 바꾸기]-
      .data
      var1 DW 1234h // var1 변수에 1234h 16비트값을 넣기
      var2 DW 5678h // var2 변수에 5678h 16비트 값을 넣기

      .code
      MOV AX, var1 // var1 → AX
      XCHG AX, var2 // XCHG는 서로의 데이터 값을 바꾸는 연산자입니다. [varl] 이 들어있는 AX레지스터의 데이터와 [var2]의 데이터를 서로 바꿉니다.   var2 = AX(var1)
      MOV var1, AX // var2의 데이터 값이 들어있는 AX레지스터의 데이터를 var1에 넣습니다.   var1 = AX(var2)      

    

<b>overlapping value</b> -
overlapping은 하나의 물리적 저장 공간을 여러 이름이나 레지스터가 겹쳐서 사용하는 것을 의미합니다.

ex) - 오버랩핑 사례 -
    mov eax 0 // eax의 저장값 : 00000000h 
    mov al 99h // eax의 저장값 : 00000099h
    mov ah 88h // eax의 저장값 : 00008899h
    mov eax 12345678h  // eax의 저장값 : 12345678h
    mov ax 1234h // eax의 저장값 : 12341234h

- eax의 레지스터는 32비트이고, ax는 eax절반인 eax레지스터의 오른쪽 16비트, ah은 ax의 절반인 ax레지스터의 왼쪽 8비트, al은 ax의 절반인 ax레지스터인 오른쪽 8비트를 담당하고 있습니다. 간단하게 텍스트 그림으로 표현한다면

    - text 그림 -
EAX 레지스터 00000000 00000000 00000000 00000000  
                 AX레지스터   (00000000 00000000)                        
                 AH레지스터   (00000000)
                        AL레지스터     (00000000)

- text 그림처럼 EAX레지스터 하위 16비트가 AX, AX레지스터 상위/하위 8비트가 AH/AL로 할당되어 있는 걸 볼 수 있고, 떄문에 오버랩핑이 될 수 있었던 이유를 알 수 있었습니다.

- <mark>flagregister</mark> -
플래그 레지스터는 하나의 명령어를 종료하기 위해 연산 결과나 상태를 플래그 레지스터에 보고 후 저장 하는 레지스터를 의미합니다. 플래그 레지스터는 16(flags), 32(EFLAGS), 64(RFLAGS)비트가 있고, 8비트 단위로 나누어서 접근 할 수 있습니다. 8비트 상태 플레그를 살펴보자면
7	SF (Sign Flag) - 결과가 음수면 1, 나머지는 0
6	ZF (Zero Flag) - 연산 결과가 0이면 Flag는 1이되고, 나머지는 0
5	0 (항상 0)
4	AF (Auxiliary Carry Flag) - 4번쨰 비트에서 자리올림이 발생하면 1, 아니면 0(인덱스 1부터 시작 기준)
3	0 (항상 0)
2	PF (Parity Flag) - 결과의 1 비트 개수가 짝수면 1, 나머지는 0
1	1 (항상 1)
0	CF (Carry Flag) - 덧셈/뺄셈 시 자리 올림/내림 발생일 때 1, 나머지는 0(무부호일떄)

- 이고 LAHF 명령으로 이 값이 AH레지스터에 저장이 됩니다. 반대인 명령어인 SAHF는 AH의 값이 하위 8비트 플래그 레지스터에 저장을 합니다. 
FLAGS를 표현하기 위해서 16비트 안에 있는 11번째 인덱스에 OF가 있습니다. 
11 OF (Overflow Flag) - Overflow가 되면 1, 아니면 0 으로 설정값이 바뀝니다.
    
- overflow란 지정된 비트가 표현할 수 있는 수 보다 더 크거나, 아니면 작게 값이 할당 되었을 떄 일어나는 상황입니다.

    ex) 
    - overflow 예시(1) -
    mov al, 127 // al(8비트)레지스터에 정수 127 데이터 저장
    add al, 1 // al레지스터에 정수 1을 더함 -> 128

    - overflow 예시(2) -
    mov al, -128 // al <- (-128)
    sub al, -1 // al < - (-128 - (-1))

- al은 8비트의 데이터 크기를 가지고 있습니다. 8비트는 정수를 -128~127까지 표현할 수 있는 크기입니다. "overflow 예시(1)"에서는 표현할 수 있는 정수보다 더 크게 잡아서 overflow가 일어났고, "overflow 예시(2)" 에서는 표현 할 수 있는 정수보다 더 작게 잡아서 overflow가 일어난걸 알수 있습니다. 이때 OF = 1의 값으로 바뀝니다.
    

- <mark>off-set</mark> -
주소 값은 설정한 바이트 크기에 따라 달라집니다. 예를 들어 DB의 크기로 여러개 생성하여 어셈블리 명령어를 수행 하려고 하면 주소값은 1바이트 증가됩니다.
하지만 DW로 크기를 설정하면 주소값은 2바이트 증가합니다. DW는 4바이트, DQ는 8바이트 입니다.

ex) - BYTE 크기 -
    .data
    arrayA BYTE 10h, 20h, 30h 

    .code
    mov al, arrayA // 10h값이 al(8비트)레지스터에 들어감
    mov al, [arrayA + 1] arrayA의 주소에서 1바이트 증가된 주소값이 들어감. 즉 20h
    mov al, [arrayA + 2] arrayA의 주소에서 2바이트 증가된 주소값이 들어감. 즉 30h

    - WORD 크기 -
    .data
    arrayB WORD 1111h, 2222h, 3333h

    .code
    mov ax, arrayB // 1111h를 ax(16비트)레지스터에 들어감
    mov ax, [arrayB + 2] arrayB의 주소에서 2바이트 증가된 주소값이 들어감. 즉 2222h
    mov ax, [arrayB + 4] arrayB의 주소에서 4바이트 증가된 주소값이 들어감. 즉 3333h

- 주소 값이 일부로 조정 되어야 할때는 ALIGN라는 명령어를 통해 주소 정렬을 할 수 있습니다. 예를 들어 4정렬로 주소를 저장하고 싶다라고 한다면
ALIGN 4를 써 주소값은 4의 배수가 되고, 되지 않는다면 아무 값이 없고 크기만 먹는 패딩이 부족한 만큼 들어가게 됩니다.

ex)
    - ALIGN 예시 -
    bVal BYTE ?   : 00404000h ~ 00404000h // bVal을 주소를 쓰게 되면 BYTE는 인덱스 1바이트가 추가되기에 다음 주소는 00404001h임
    ALIGN 2        // 여기서 주소인덱스를 2의 배수로 설정하여, 2의 배수가 될려면 1바이트가 더 필요해, 패딩이 1바이트 추가가 됨 00404001h + 패딩(1바이트) -> 00404002h
    wVal WORD ?  : 00404002h ~ 00404003h // WORD는 2바이트 주소인덱스 추가 -> 다음 주소 인덱스는 00404004h
    ALIGN 4     //  여기서 주소인덱스를 4의 배수로 재설정하였는데 다음 주소 인덱스는 4의 배수인 00404004h이기에 패딩을 추가 하지 않음
    dVal DWORD ? : 00404004h ~ 00404007h // DWORD는 4바이트 주소 인덱스 추가 -> 다음 주소 인덱스는 00404008h
    dVall2 DWORD ? : 00404008h ~ 0040400Ch // DOWRD는 4바이트 주소 인덱스 추가 -> 다음 주소 인덱스는 0040400Dh
    
<b>PTR operator</b> -
PTR연산자는 메모리에 접근할 때 데이터 크기(자료형)를 명시하는 연산자 입니다. 

ex) 
    data
    mydouble DWORD 12345678h
    
    .code
    mov b1, BYTE PTR mydouble // b1는 1바이트 크기를 가지고, 그 크기에 맞게 78h의 값을 가지게 됩니다.
    mov b2, BYTE PTR [mydouble + 1] b2는 1바이트 크기를 가지고, 56h의 값을 가지게 됩니다. 
    mov b3, BYTE PTR [mydouble + 2] b3는 1바이트 크기를 가지고, 34h의 값을 가지게 됩니다. 
    mov b4, BYTE PTR [mydouble + 3] b4는 1바이트 크기를 가지고, 12h의 값을 가지게 됩니다. ( +1, +2, +3한 이유는 그만큼의 BYTE(1바이트) 바이트가 사용되었기에 증가됨)
    
    mov a1, WORD PTR mydouble // a1은 2바이트 크기를 가지고, 그 크기에 맞게 5678h의 값을 가지게 됩니다.
    mov a2, WORD PTR [mydouble + 2] a2는 2바이트 크기를 가지고, 1234h의 값을 가지게 됩니다. (+2한 이유는 앞에서 WORD(2바이트) 바이트가 사용되었기에 증가됨)

<b>OFFSET operator</b> -
OFFSET연산자는 해당 주소인덱스를 가져오는 연산자입니다.
ex)
    - OFFSET 연산자 예시(1) -
    .data
    arrayB BYTE 10h, 20h, 30h 
    
    .code
    mov esi, OFFSET arrayB // esi레지스터에 arrayB주소 인덱스를 저장
    mov al,[esi] // esi레지스터의 주소에 대한 값을 al레지스터에 저장(10h)
    inc esi // esi의 값 1증가
    mov al,[esi] // esi레지스터의 주소에 대한 값을 al레지스터에 저장(20h)
    inc esi // esi의 값 1증가
    mov al,[esi] // esi레지스터의 주소에 대한 값을 al레지스터에 저장(30h)

- []는 주소에 있는 값을 불러오는 것이고, OFFSET을 통한 esi는 주소이므로, +1증가 될떄마다 주소인덱스가 1 증가되며 al에 값이 복사 후 이동 되었습니다. 
  arrayB는 바이트 크기의 배열이기에, 1씩 증가하면 값이 나오는 것이고, 다른 크기의 단위를 하면 그만큼 바이트를 추가해야 값이 나옵니다.

ex)
    - OFFSET 연산자 예시(2) -
    .data
    arrayB WORD 1111h, 2222h, 3333h 
    
    .code
    mov esi, OFFSET arrayB
    mov ax, [esi] // AX = 1111h
    add esi, 2  // WORD는 크기가 2바이트라서 2증가
    mov ax, [esi]  // AX = 2222h
    add esi, 2
    mov ax, [esi] // AX = 3333h

<b>TYPE</b> -
TYPE의 명령어는 데이터 크기를 알수 있는 명령어 입니다. 
ex)
    - TYPE 사용 예시 -
    .data
    arrayD DWORD 100h, 200h, 300h, 400h
    
    .code
    mov esi, 3 * TYPE arrayD // arrayD의 배열의 데이터 크기는 DWORD로 값은 4바이트 입니다. 4(BYTE) * 3의 값인 12가 esi에 저장 됩니다.
    mov eax, arrayD(esi) // arrayD의 시작값에서 esi값을 주소의 값을 eax에 저장합니다   eax <- 400h

<b>pointer</b> -
포인터는 다른 변수나 데이터가 저장된 메모리 주소를 저장하는 변수입니다. pointer 타입에는 PBYTE, PWORD, PDWORD가 있고, BYTE, WORD, DWORD 타입의 포인터입니다.
포인터 타입을 쓰기 전에는 선언 후 사용 할 수 있습니다.

ex) 
    - 포인터 사용 예시 -
    PBYTE TYPEDEF PTR BYTE //PBTYE 선언
    PWORD TYPEDEF PTR WORD // PWORD 선언
    PDWORD TYPEDEF PTR DWORD // PDWORD 선언
        
    .data
    arrayB BYTE 10h,20h,30h // BYTE크기의 배열 arrayB
    arrayW WORD 1,2,3 // WORD크기의 배열 arrayW
    arrayD DWORD 4,5,6 // DWORD크기의 배열 arrayD
    
    ptr1 PBYTE arrayB // arrayB의 시작 주소를 ptr1에 저장
    ptr2 PWORD arrayW // arrayW의 시작 주소를 ptr2에 저장
    ptr3 PDWORD arrayD // arrayD의 시작 주소를 ptr3에 저장

    .code
    mov esi,ptr1 // arrayB의 시작 주소가 담긴 ptr1을 esi에 저장
    mov al,[esi] // arrayB의 시작 주소의 값을 al에 저장  al < - 10h
    mov al,[esi + 1] // arrayB의 시작 주소에서 1BYTE 후의 값을 al에 저장   al <- 20h
    mov al, [esi + 2] // arrayB의 시작 주소에서 2BYTE 후의 값을 al에 저장   al <- 30h
        
    mov esi,ptr2 // arrayW의 시작 주소가 담긴 ptr2을 esi에 저장
    mov ax,[esi] // arrayW의 시작 주소의 값을 ax에 저장  ax < - 1
    mov ax,[esi + 2] // arrayW의 시작 주소에서 2BYTE 즉 WORD만큼 후의 주소값을 ax에 저장  ax < - 2
    mov ax,[esi + 4] // arrayW의 시작 주소에서 4BYTE만큼 후의 주소값을 ax에 저장  ax < - 3
        
    mov esi,ptr3 // arrayD의 시작 주소가 담긴 ptr3을 esi에 저장
    mov eax,[esi] // arrayD 의 시작 주소의 값을 eax에 저장  eax < - 4
    mov eax,[esi + 4] // arrayD 의 시작 주소에서 4BYTE 즉 DWORD만큼 후의 주소값을 eax에 저장  eax < - 5
    mov eax,[esi + 8] // arrayD 의 시작 주소에서 8BYTE만큼 후의 주소값을 eax에 저장  eax < - 6

- 

p51 cx 레지스터는 loop하기 위한 레지스터입니다. ...
ax 레지스터는 sum하기 위한 레지스터입니다.
jump , loop, 있음
~


p54 source byte "This is the source string",0  에서 마지막 0은  Null값입니다.



Q. 인의예지신과 중도에 대해 설명
측은지심, 광명지신, 십이지신, 


연습문제에서 문제냄(하지만 영어로)
Q.
64비트 레지스터에 대한 기능을 설명하시오. (CS, DS, SS, ES, FS, GS)

Q. flag레지스터의 종류 설명하기(8비트) 그리고 이 값이 언제 reset 되는지도 확인
zero, carry, Parity, overflow, sign, Auxiliary carry 

</pre>
