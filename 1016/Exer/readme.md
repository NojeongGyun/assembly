<pre>
<b> Q.4.9.1(1). What will be the value in EDX after each of the lines marked (a) and (b) execute? </b>
  (각 (a)와 (b)로 표시된 줄이 실행된 후 EDX 레지스터에 저장될 값은 무엇입니까?)
              .data
              one WORD 8002h
              two WORD 4321h
              .code
              mov edx,21348041h
              movsx edx,one ; (a)
              movsx edx,two ; (b) 

A. (a)의 EDX = 11118002h  (b)의 EDX = 00004321h   1로 채운 이유는 one은 MSB가 1이라 음수이기에 1로 채웠고, two는 MSB가 0이라 양수이기에 0으로 채웠습니다.

<b>Q.4.9.1(2). What will be the value in EAX after the following lines execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,1002FFFFh
              inc ax
A. 10020000h 

<b> Q.4.9.1(3). What will be the value in EAX after the following lines execute? </b>
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,30020000h
              dec ax
A. 3002FFFFh

<b>Q.4.9.1(4). What will be the value in EAX after the following lines execute? </b>
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,1002FFFFh
              neg ax
A. 10020001h

<b>Q.4.9.1(5). What will be the value of the Parity flag after the following lines execute? </b>
  (다음 명령들이 실행된 후 **Parity 플래그(PF)**의 값은 무엇입니까?)
              mov al,1
              add al,3
A.  0001 + 0011 == 0100 입니다. PF는 비트 1의 개수가 짝수면 1이고, 홀수면 0입니다. 그러므로 PF = 0입니다.

<b>Q.4.9.1(6). What will be the value of EAX and the Sign flag after the following lines execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터의 값과 **Sign Flag(SF)**의 값은 무엇입니까?)
              mov eax,5
              sub eax,6
A. 00000005h - 00000006h == FFFFFFFFh  음수인지 아닌지는 MSB에서 1이면 음수입니다. 음수이면 SF가 1이 되고 아니면 0입니다. 그렇기에 SF = 1 입니다.

<b>Q.4.9.1(7). In the following code, the value in AL is intended to be a signed byte. Explain how the Overflow flag helps, or does not help you, 
to determine whether the final value in AL falls within a valid signed range.</b>
  (다음 코드에서 AL 레지스터의 값은 부호 있는(Byte) 값으로 간주됩니다. Overflow Flag(OF)가 
  최종 AL 값이 유효한 부호 있는 범위(-128 ~ 127) 내에 있는지를 판단하는 데 도움이 되는지, 그렇지 않은지를 설명하세요.)
            mov al,-1
            add al,130
A. al은 1바이트 크기이므로 범위는 -128~127로 제한됩니다. al에 -1 + 130의 계산 결과인 범위 밖인 129가 들어와 overflow가 일어나게 됩니다. 이 떄문에 OF = 1 
로 변하고, OF가 1이라는 정보로 범위밖이라는 정보를 얻을 수 있습니다.



<b>Q.4.9.1(8). What value will RAX contain after the following instruction executes?</b>
  (다음 명령이 실행된 후 RAX 레지스터에는 어떤 값이 저장됩니까?)
            mov rax,44445555h
A. rax는 8바이트로 이루어진 레지스터입니다. 0확장을 하면 0000000044445555h 입니다.

<b>Q.4.9.1(9). What value will RAX contain after the following instructions execute?</b>
  (다음 명령들이 실행된 후 RAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            dwordVal DWORD 84326732h
            .code
            mov rax,0FFFFFFFF00000000h
            mov rax,dwordVal
A. 0000000084326732h

<b>Q.4.9.1(10). What value will EAX contain after the following instructions execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            dVal DWORD 12345678h
            .code
            mov ax,3
            mov WORD PTR dVal+2,ax
            mov eax,dVal
A. 00035678h 입니다. 이유는 word단위로 쪼개면 daval은 0바이트~1바이트 5678h, 2바이트~3바이트 1234h입니다.
ax레지스터는 2바이트의 크기를 차지합니다. daval의 주소에 2바이트 떨어진 곳에 ax 값인 0003h를 넣는 것이기에 00035678h 입니다.

<b>Q.4.9.1(11). What will EAX contain after the following instructions execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            .dVal DWORD ?
            .code
            mov dVal,12345678h
            mov ax,WORD PTR dVal+2    //  ax에 1234h저장
            add ax,3                  //  ax에 1237h저장
            mov WORD PTR dVal,ax      // dval에 하위 4비트에 1237h저장 
            mov eax,dVal              // eax는 00001237h
A. 12341237h

<b>Q.4.9.1(12). (Yes/No): Is it possible to set the Overflow flag if you add a positive integer to a negative integer? </b>
  ([<mark>Yes/No</mark>] 양수와 음수를 더할 때 **Overflow Flag(OF)**가 설정될 수 있나요?)
A. No.  두 양수와 음수는 범위를 벗어나지 않는 다는 전제가 OF에 깔려있기에 OF는 무조권 0이 됩니다.

<b>Q.4.9.1(13). (Yes/No): Will the Overflow flag be set if you add a negative integer to a negative integer and produce a positive result?</b>
  ([<mark>Yes/No</mark>]두 음수를 더했는데 결과가 양수가 되면 Overflow Flag(OF)가 설정되나요?)
A. Yes    범위보다 작아지면 오버플로우가 발생하고, 해당 최대 음수제한 정수에서 넘어간 절대값 만큼 양수가 됩니다.

<b>Q.4.9.1(14). (Yes/No): Is it possible for the NEG instruction to set the Overflow flag?</b>
  ([<mark>Yes/No</mark>] NEG 명령어가 Overflow Flag(OF)를 설정할 수 있나요?)
A. Yes   항상 범위에서 음수제한 값이 양수 제한값보다 한개더 많기에 최소 음수 제한 값을 neg(부호 반전) 시킬 때에 한에서 오버플로우가 발생합니다.

<b>Q.4.9.1(15). (Yes/No): Is it possible for both the Sign and Zero flags to be set at the same time? Use the following variable definitions for Questions 16–19</b>
  ([<mark>Yes/No</mark>]Sign Flag(SF)와 Zero Flag(ZF)가 동시에 설정될 수 있나요?)
A. No    ZF는 값이 0이 되면 ZF = 1 로 되는데 SF는 음수일 떄 SF = 1로 설정이 되어, 두개 동시에 1이 되지않는다.


Use the following variable definitions for Questions 16–19: (다음 변수 정의를 사용하여 16–19번 문제를 풀어보세요)
.data
var1 SBYTE -4,-2,3,1
var2 WORD 1000h,2000h,3000h,4000h
var3 SWORD -16,-42
var4 DWORD 1,2,3,4,5

<b>Q.4.9.1(16). For each of the following statements, state whether or not the instruction is valid</b>
  (다음 명령어들 각각이 유효한지 여부를 말하시오.)
              .data
              var1 SBYTE -4,-2,3,1
              var2 WORD 1000h,2000h,3000h,4000h
              var3 SWORD -16,-42
              var4 DWORD 1,2,3,4,5
  
              a. mov ax,var1?     
              b. mov ax,var2
              c. mov eax,var3
              d. mov var2,var3
              e. movzx ax,var2
              f. movzx var2,al
              g. mov ds,ax
              h. mov ds,1000h
A.  a, c, d, f, h가 틀리고 나머지는 다 맞습니다.
a가 틀린 이유는 ax는 2바이트 레지스터고, var1은 1바이트 메모리입니다. 데이터의 크기가 맞지 않아 오류
c가 틀린 이유는 eax는 4바이트 레지스터고, var3는 2바이트 메모리입니다. 데이터의 크기가 맞지 않아 오류
d가 틀린 이유는 메모리 to 메모리기에 오류
f가 틀린 이유는 레지스터에 메모리 값이 저장되어야하는데 반대이므로 오류
h가 틀린 이유는 세그먼트 레지스터에 즉시 값을 바로 넣을 수 없습니다. 넣고 싶다면 레지스터에 값을 할당 후 레지스터로 넣어야합니다.

<b>Q.4.9.1(17). What will be the hexadecimal value of the destination operand after each of the following instructions execute in sequence?</b>
  (다음 명령들이 순서대로 실행된 후, 목적 피연산자의 16진수 값은 무엇이 될까요?)
              .data
              var1 SBYTE -4,-2,3,1
              var2 WORD 1000h,2000h,3000h,4000h
              var3 SWORD -16,-42
              var4 DWORD 1,2,3,4,5
  
              mov al, var1 ; a.
              mov ah,[var1+3] ; b.
A. al = FCh , ah = 01h 입니다.

<b>Q.4.9.1(18). What will be the value of the destination operand after each of the following instructions execute in sequence?</b>
  (각 명령 실행 후 AX 레지스터(목적지 operand)에 어떤 값이 들어가나요?)
                .data
              var1 SBYTE -4,-2,3,1
              var2 WORD 1000h,2000h,3000h,4000h
              var3 SWORD -16,-42
              var4 DWORD 1,2,3,4,5

              mov ax,var2 ; a.
              mov ax,[var2+4] ; b.
              mov ax,var3 ; c.
              mov ax,[var3-2] ; d.
A. a - ax = 1000h    b - ax = 3000h  c - ax = FFF0h  d - 4000h

<b>Q.4.9.1(19) What will be the value of the destination operand after each of the following instructions execute in sequence?</b>
  (다음 명령어들이 순서대로 실행된 후, 목적지 오퍼랜드(EDX 레지스터)의 값은 무엇인가?)
              .data
              var1 SBYTE -4,-2,3,1                             0000 0100     1111 1100
              var2 WORD 1000h,2000h,3000h,4000h
              var3 SWORD -16,-42
              var4 DWORD 1,2,3,4,5
  
              mov edx,var4 ; a.
              movzx edx,var2 ; b.
              mov edx,[var4+4] ; c.
              movsx edx,var1 ; d.
A. a - edx = 00000001h    b - edx = 00001000h  c - edx = 00000002h    d - FFFFFFFCh

  
<b>Q.4.9.2(1). Write a sequence of MOV instructions that will exchange the upper and lower words in a doubleword variable named three.</b>
  (three라는 이름의 doubleword(32비트) 변수에서 상위 WORD(16비트)와 하위 WORD(16비트)를 서로 교환하는 MOV 명령어 시퀀스를 작성하시오.)
A. 


  
  
</pre>
