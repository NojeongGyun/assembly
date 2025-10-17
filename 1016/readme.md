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
    
.data 를 붙이면 모두 변수가 됩니다. 즉 변수 선언을 할 때에는 .data 영역에 변수와 그에 대한 값을 쓴다.



p5 다음에 실행할 주소를 가지고 있는 것이 ip   internet protocal이랑 다름
처음에 할당받는 ip는 엔트리포인트를 가져온다.

BYTE 1바이트
WORD 2바이트
DWORD 4바이트

p6 이미 저장했던 DWORD값에 WORD값을 0을 넣어 1234 0000h 가 됩니다.

p7 ecx, 0 인데 ecx, WORD로 하면 (16비트, 32비트) 서로 오퍼랜드의 비트 크기가 달라서 실행 오류가 납니다.

p8 ax, bytetal (16비트, 8비트) 원래는 실행이 되지 않는데 
코드를 보면 byteVal에 1BYTE크기의 숫자를 넣고, MOVEZX ax, byteVal 명령어가 있습니다. 위에서 선언한 MOVZX 16reg, reg/mem8 를 써서 캐스팅을 하였기에 
16비트, 8비트는 실행이 되지 않는데 실행이 되게 됩니다. 만약 ADD ax, byteVal 을 실행한다고 하면 위에 예외처리가 되어있지 않기 때문에 코드 실행 오류가 납니다. 

p10 플래그 레지스터에 대한 설명
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

p11 xchg는 서로 바꾸는 명령어입니다. xchg val1, val2를 하면 메모리와 메모리를 서로 맞바꾸는거기에 실행 오류가 납니다.
그렇기에 사전에 mov ax = val1(레지스터, 메모리)로 ax의 레지스터에 val1이라는 값을 이전 시키고, xchg ax, val2 (레지스터, 메모리)를 실행하면 ax의 값인 val1과 val2의 값이 서로 바뀌게 되고
ax == val2가 되는데, 다시 레지스터에서 메모리로 옮기는 작업인 mov val1 ax(메모리, 레지스터)를 실행하여 본래 목적이었던 메모리 val1과 val2의 값이 서로 변경된 것을 확인할 수 있습니다.

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
