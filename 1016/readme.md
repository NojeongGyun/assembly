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
      myWord DW 1234h   ; Define word(DW)는 16비트이기에 myword라는 변수 선언 후 16비트 1234h의 메모리를 넣음 
      
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
플래그 레지스터는 하나의 명령어를 종료하기 위해 연산 결과나 상태를 플래그 레지스터에 보고 후 저장 하는 레지스터를 의미합니다. 이 기록을 바탕으로 조건 분기, 산술 연산 결과 처리, 인터럽트 제어 등 수행합니다. https://github.com/NojeongGyun/assembly/tree/main/0918


연산 결과나 상태를 플래그 레지스터에 보고 하고, 하나의 명령이 종료되게 됩니다.
플래그 레지스터도 비트 크기가 있기에 .data 세그먼트에 비트 할당을 하게 한 후 .code 세그먼트에서 씁니다.
아니면 크기당 이미 만들어져있는 플래그 레지스터를 바로 쓸수 도 있습니다. 
EFLAGS(16비트) RFLAGS(32비트)
section .data
saveflags db 0      ; 1바이트 (8비트)
saveflags16 dw 0    ; 2바이트 (16비트)
saveflags32 dd 0    ; 4바이트 (32비트)
saveflags64 dq 0    ; 8바이트 (64비트)

section .code
mov saveflags16, ax    (16비트, 16비트)
mov saveflags, ah      (8비트, 8비트)

lahf는 플래그 레지스터의 8비트 값을 뽑아 냅니다. 
그 다음 mov saveflags, ah가 나오는데 ah를 flag 레지스터에 넣습니다.

WORD(16비트 레지스터)

p21 carry에 대한 설명
add를 해서 carry가 발생하면 CF = 1
빼기를 해서 carry가 발생해도 CF = 1

p23 3번쨰 비트가 carry가 발생하면 AC = 1이 됩니다. 
p23 비트에서 1의 개수가 홀수면 PF = 0, 비트의 1의개수가 짝수면 PF = 1이입니다.


p24 할당된 비트보다 더 큰 값이 나타나면 overflow가 나타남. OF = 1 
p26을 보면 neg 명령어를 쓰면 부호가 바뀌는데 이 값이 할당된 비트 값보다 많으면 overflow가 일어 난다. OF = 1이 되고, 음수 값이여도 오버플로우가 일어납니다 (이때는 음수 값보다 작을때) OF = 1

p32 OFFSET은 사용된 바이트의 거리입니다.       bVal BYTE ? 는 bval 변수 선언만 하고 값을 넣지 않았기에 OFFSET은 1이 됩니다.

p34 ??? 중요
~
~
p39 [A]는 A의 주소의 값을 가져옵니다. 

p43 WORD이면 인덱스가 2증가할때마다 배열의 값이 들어옵니다. [0, 2, 4..., ] OFFSET 각 2
DWORD이면 인덱스가 4증가할때마다 배열의 값이 들어옵니다. [0, 4, 8, 12...] OFFSET 각 4

p46 PBYTE TYPEDEF PTR BYTE 알기

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
