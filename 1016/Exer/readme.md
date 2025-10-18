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
A. mov ax, WORD PTR three      
   mov bx, WORD PTR three+2   
   mov WORD PTR three, bx      
   mov WORD PTR three+2, ax

<b>Q.4.9.2(2). Using the XCHG instruction no more than three times, reorder the values in four 8-bit registers from the order A,B,C,D to B,C,D,A. </b>
  (최대 3번 이하의 XCHG 명령어를 사용하여, 레지스터에 저장된 값의 순서를 A, B, C, D → B, C, D, A 로 바꾸시오.)
A. XCHG A, D
   XCHG B, C
   XCHG D, B
  
<b>Q.4.9.2(3). Transmitted messages often include a parity bit whose value is combined with a data byte to produce an even number of 1 bits.
Suppose a message byte in the AL register contains01110101. Show how you could use the Parity flag combined with an arithmetic instruction </b>
to determine if this message byte has even or odd parity.
  (전송되는 메시지에는 데이터 바이트와 결합되어 1비트의 개수가 짝수가 되도록 하는 패리티 비트가 포함되는 경우가 많다.
만약 AL 레지스터에 01110101이 들어있다면, 패리티 플래그(PF) 와 산술/논리 명령을 이용하여 이 바이트가 짝수 패리티인지 홀수 패리티인지 판별하는 방법을 보여라.)
A. MOV AL, 0111 0101b
   ADD AL, 0   // 산술 명령을 써 값을 변환하지 않고 Al의 PF값은 PF = 0인걸 알 수 있습니다. 

<b>Q.4.9.2(4). Write code using byte operands that adds two negative integers and causes the Overflow flag to be set.</b>
  (바이트(byte, 8비트) 단위 연산을 사용해서 두 개의 음수 정수(negative integers) 를 더한 뒤 오버플로우 플래그(OF)가 1이 되도록 만드는 어셈블리 코드를 작성하라.)
A. mov al, -128
   add al, -1

<b>Q.4.9.2(5).  Write a sequence of two instructions that use addition to set the Zero and Carry flags at the same time</b>
  (덧셈(add) 명령어를 이용해서 Zero Flag(ZF) = 1, Carry Flag(CF) = 1 를 동시에 설정되도록 만드는 2개의 명령어를 작성하라.)
A. mov al, 0FFh
   add al, 1

<b>Q.4.9.2(6). Write a sequence of two instructions that set the Carry flag using subtraction. </b>
  (뺄셈(subtraction) 명령어를 이용해서 Carry Flag(CF)를 1로 설정하는 2개의 명령어 작성)
A. mov al, 0FFh
   sub al, -1

<b>Q.4.9.2(7). Implement the following arithmetic expression in assembly language: EAX = –val2 + 7 – val3 + val1. 
  Assume that val1, val2, and val3 are 32-bit integer variables.</b>
  (다음 산술식을 어셈블리 언어로 구현하라 : EAX = –val2 + 7 – val3 + val1   | "val1, val2, val3는 32비트 정수입니다.")
A. mov eax, val2
   neg eax
   add eax, 7
   sub eax, val3
   add eax, val1

<b>Q.4.9.2(8).  Write a loop that iterates through a doubleword array and calculates the sum of its elements using a scale factor with indexed addressing.</b>
  (스케일 팩터와 인덱스 주소를 사용해서 doubleword 배열의 모든 요소를 반복하며 합계를 계산하는 루프를 작성하라.)
A. mov eax, 0       
   mov ecx, 0          

  LoopStart:
      mov ebx, [array + ECX*4] 
      add eax, EBX             
      inc ecx                  
      cmp ecx, array_size      
      jl LoopStart 

<b>Q.4.9.2(9). Implement the following expression in assembly language: AX = (val2 + BX) –val4. Assume that val2 and val4 are 16-bit integer variables.</b>
  (AX 레지스터에 (val2 + BX) – val4 수식을 어셈블리 언어로 구현하라.)
A. mov ax, val2  
   add ax, bX     
   sub ax, val4 

<b>Q.4.9.2(10). Write a sequence of two instructions that set both the Carry and Overflow flags at the same time </b>
  (CF(Carry Flag)와 OF(Overflow Flag)를 동시에 1로 설정하는 2개의 명령어를 작성하라.)
A. mov al, 7Fh    
   add al, 81h

<b>Q.4.9.2(11). Write a sequence of instructions showing how the Zero flag could be used to indicate unsigned overflow after executing INC and DEC instructions.</b>
  (INC(1 증가)와 DEC(1 감소) 명령 후 Zero Flag(ZF)가 unsigned overflow를 나타내는 경우를 보여주는 명령어 시퀀스를 작성하라.)
A. mov al, 0FFh   
  inc al        // overflow
  
  mov al, 00h  
  dec al       // underflow

<b>Q.4.9.2(12). Insert a directive in the given data that aligns myBytes to an even-numbered address.</b>
  (데이터 섹션에서 myBytes 변수를 **짝수 주소(even-numbered address)**에 정렬하도록 지시어를 삽입하라.)
A.             .data
                ALIGN 2
                myBytes BYTE 10h,20h,30h,40h
                myWords WORD 3 DUP(?),2000h
                myString BYTE "ABCDE"

<b>Q.4.9.2(13). What will be the value of EAX after each of the following instructions execute?</b>
  (다음에 나오는 각각의 명령어가 실행된 후, EAX의 값이 무엇인지 구하라.)
                .data
                myBytes BYTE 10h,20h,30h,40h
                myWords WORD 3 DUP(?),2000h
                myString BYTE "ABCDE"
  
                mov eax,TYPE myBytes ; a.
                mov eax,LENGTHOF myBytes ; b.
                mov eax,SIZEOF myBytes ; c.
                mov eax,TYPE myWords ; d.
                mov eax,LENGTHOF myWords ; e.
                mov eax,SIZEOF myWords ; f.
                mov eax,SIZEOF myString ; g.
A. a - eax = 1,  b - eax = 4,  c - eax = 4,  d - eax = 2,  e - eax = 4,  f - eax = 8,  g - eax = 5 

<b>Q.4.9.2(14).  Write a single instruction that moves the first two bytes in myBytes to the DX register. The resulting value will be 2010h.</b>
  (myBytes 배열의 첫 번째 두 바이트를 DX 레지스터로 이동시키는 한 줄짜리 명령어를 작성하라. 결과적으로 DX = 2010h 가 되어야 한다.)
A.             .data
                myBytes BYTE 10h,20h,30h,40h
                myWords WORD 3 DUP(?),2000h
                myString BYTE "ABCDE"

                mov Dx, WORD PTR myBytes

<b>Q.4.9.2(15).  Write an instruction that moves the second byte in myWords to the AL register. </b> 
  (myWords 배열의 두 번째 바이트를 AL 레지스터로 이동하는 명령어를 작성하라.)
A.              .data
                myBytes BYTE 10h,20h,30h,40h
                myWords WORD 3 DUP(?),2000h
                myString BYTE "ABCDE" 

                mov al, [myWords + 2]

<b>Q.4.9.2(16). Write an instruction that moves all four bytes in myBytes to the EAX register </b>
  (myBytes 배열의 모든 4바이트를 EAX 레지스터로 이동하는 명령어를 작성하라.)
A.             .data
                myBytes BYTE 10h,20h,30h,40h
                myWords WORD 3 DUP(?),2000h
                myString BYTE "ABCDE" 

                mov eax, DWORD PTR myBytes

<b>Q.4.9.2(17).  Insert a LABEL directive in the given data that permits myWords to be moved directly to a 32-bit register.
  (myWords 배열을 32비트 레지스터(EAX, EBX 등)로 바로 이동할 수 있도록 데이터 섹션에 LABEL 지시어를 추가하라.)
A.              .data
                myBytes BYTE 10h,20h,30h,40h
                myWords WORD 3 DUP(?),2000h
                myString BYTE "ABCDE" 

                

  
</pre>
