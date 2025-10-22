


























 Q.4.9.1(1). What will be the value in EDX after each of the lines marked (a) and (b) execute? 
  (각 (a)와 (b)로 표시된 줄이 실행된 후 EDX 레지스터에 저장될 값은 무엇입니까?)
              .data
              one WORD 8002h
              two WORD 4321h
              .code
              mov edx,21348041h
              movsx edx,one ; (a)
              movsx edx,two ; (b) 

A. 

Q.4.9.1(2). What will be the value in EAX after the following lines execute?
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,1002FFFFh
              inc ax
A. 

 Q.4.9.1(3). What will be the value in EAX after the following lines execute? 
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,30020000h
              dec ax
A.

Q.4.9.1(4). What will be the value in EAX after the following lines execute? 
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,1002FFFFh
              neg ax
A. 

Q.4.9.1(5). What will be the value of the Parity flag after the following lines execute? 
  (다음 명령들이 실행된 후 **Parity 플래그(PF)**의 값은 무엇입니까?)
              mov al,1
              add al,3
A.  

Q.4.9.1(6). What will be the value of EAX and the Sign flag after the following lines execute?
  (다음 명령들이 실행된 후 EAX 레지스터의 값과 **Sign Flag(SF)**의 값은 무엇입니까?)
              mov eax,5
              sub eax,6
A.

Q.4.9.1(7). In the following code, the value in AL is intended to be a signed byte. Explain how the Overflow flag helps, or does not help you, 
to determine whether the final value in AL falls within a valid signed range.
  (다음 코드에서 AL 레지스터의 값은 부호 있는(Byte) 값으로 간주됩니다. Overflow Flag(OF)가 
  최종 AL 값이 유효한 부호 있는 범위(-128 ~ 127) 내에 있는지를 판단하는 데 도움이 되는지, 그렇지 않은지를 설명하세요.)
            mov al,-1
            add al,130
A. 



Q.4.9.1(8). What value will RAX contain after the following instruction executes?
  (다음 명령이 실행된 후 RAX 레지스터에는 어떤 값이 저장됩니까?)
            mov rax,44445555h
A. 

Q.4.9.1(9). What value will RAX contain after the following instructions execute?
  (다음 명령들이 실행된 후 RAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            dwordVal DWORD 84326732h
            .code
            mov rax,0FFFFFFFF00000000h
            mov rax,dwordVal
A. 

Q.4.9.1(10). What value will EAX contain after the following instructions execute?
  (다음 명령들이 실행된 후 EAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            dVal DWORD 12345678h
            .code
            mov ax,3
            mov WORD PTR dVal+2,ax
            mov eax,dVal
A. 

Q.4.9.1(11). What will EAX contain after the following instructions execute?
  (다음 명령들이 실행된 후 EAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            .dVal DWORD ?
            .code
            mov dVal,12345678h
            mov ax,WORD PTR dVal+2   
            add ax,3                  
            mov WORD PTR dVal,ax      
            mov eax,dVal             
A. 

Q.4.9.1(12). (Yes/No): Is it possible to set the Overflow flag if you add a positive integer to a negative integer? 
  ([Yes/No] 양수와 음수를 더할 때 **Overflow Flag(OF)**가 설정될 수 있나요?)
A. 

Q.4.9.1(13). (Yes/No): Will the Overflow flag be set if you add a negative integer to a negative integer and produce a positive result?
  ([Yes/No]두 음수를 더했는데 결과가 양수가 되면 Overflow Flag(OF)가 설정되나요?)
A. 

Q.4.9.1(14). (Yes/No): Is it possible for the NEG instruction to set the Overflow flag?
  ([Yes/No] NEG 명령어가 Overflow Flag(OF)를 설정할 수 있나요?)
A. 

Q.4.9.1(15). (Yes/No): Is it possible for both the Sign and Zero flags to be set at the same time? Use the following variable definitions for Questions 16–19
  ([Yes/No]Sign Flag(SF)와 Zero Flag(ZF)가 동시에 설정될 수 있나요?)
A. 


Use the following variable definitions for Questions 16–19: (다음 변수 정의를 사용하여 16–19번 문제를 풀어보세요)
.data
var1 SBYTE -4,-2,3,1
var2 WORD 1000h,2000h,3000h,4000h
var3 SWORD -16,-42
var4 DWORD 1,2,3,4,5

Q.4.9.1(16). For each of the following statements, state whether or not the instruction is valid
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
A. 

Q.4.9.1(17). What will be the hexadecimal value of the destination operand after each of the following instructions execute in sequence?
  (다음 명령들이 순서대로 실행된 후, 목적 피연산자의 16진수 값은 무엇이 될까요?)
              .data
              var1 SBYTE -4,-2,3,1
              var2 WORD 1000h,2000h,3000h,4000h
              var3 SWORD -16,-42
              var4 DWORD 1,2,3,4,5
  
              mov al, var1 ; a.
              mov ah,[var1+3] ; b.
A.

Q.4.9.1(18). What will be the value of the destination operand after each of the following instructions execute in sequence?
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
A. 

Q.4.9.1(19) What will be the value of the destination operand after each of the following instructions execute in sequence?
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
A. 

  
Q.4.9.2(1). Write a sequence of MOV instructions that will exchange the upper and lower words in a doubleword variable named three.
  (three라는 이름의 doubleword(32비트) 변수에서 상위 WORD(16비트)와 하위 WORD(16비트)를 서로 교환하는 MOV 명령어 시퀀스를 작성하시오.)
A. 

Q.4.9.2(2). Using the XCHG instruction no more than three times, reorder the values in four 8-bit registers from the order A,B,C,D to B,C,D,A. 
  (최대 3번 이하의 XCHG 명령어를 사용하여, 레지스터에 저장된 값의 순서를 A, B, C, D → B, C, D, A 로 바꾸시오.)
A. 
  
Q.4.9.2(3). Transmitted messages often include a parity bit whose value is combined with a data byte to produce an even number of 1 bits.
Suppose a message byte in the AL register contains01110101. Show how you could use the Parity flag combined with an arithmetic instruction 
to determine if this message byte has even or odd parity.
  (전송되는 메시지에는 데이터 바이트와 결합되어 1비트의 개수가 짝수가 되도록 하는 패리티 비트가 포함되는 경우가 많다.
만약 AL 레지스터에 01110101이 들어있다면, 패리티 플래그(PF) 와 산술/논리 명령을 이용하여 이 바이트가 짝수 패리티인지 홀수 패리티인지 판별하는 방법을 보여라.)
A. 

Q.4.9.2(4). Write code using byte operands that adds two negative integers and causes the Overflow flag to be set.
  (바이트(byte, 8비트) 단위 연산을 사용해서 두 개의 음수 정수(negative integers) 를 더한 뒤 오버플로우 플래그(OF)가 1이 되도록 만드는 어셈블리 코드를 작성하라.)
A. 

Q.4.9.2(5).  Write a sequence of two instructions that use addition to set the Zero and Carry flags at the same time
  (덧셈(add) 명령어를 이용해서 Zero Flag(ZF) = 1, Carry Flag(CF) = 1 를 동시에 설정되도록 만드는 2개의 명령어를 작성하라.)
A. 

Q.4.9.2(6). Write a sequence of two instructions that set the Carry flag using subtraction. 
  (뺄셈(subtraction) 명령어를 이용해서 Carry Flag(CF)를 1로 설정하는 2개의 명령어 작성)
A. 

Q.4.9.2(7). Implement the following arithmetic expression in assembly language: EAX = –val2 + 7 – val3 + val1. 
  Assume that val1, val2, and val3 are 32-bit integer variables.
  (다음 산술식을 어셈블리 언어로 구현하라 : EAX = –val2 + 7 – val3 + val1   | "val1, val2, val3는 32비트 정수입니다.")
A. 
Q.4.9.2(8).  Write a loop that iterates through a doubleword array and calculates the sum of its elements using a scale factor with indexed addressing.
  (스케일 팩터와 인덱스 주소를 사용해서 doubleword 배열의 모든 요소를 반복하며 합계를 계산하는 루프를 작성하라.)
A.          

  

Q.4.9.2(9). Implement the following expression in assembly language: AX = (val2 + BX) –val4. Assume that val2 and val4 are 16-bit integer variables.
  (AX 레지스터에 (val2 + BX) – val4 수식을 어셈블리 언어로 구현하라.)
A. 

Q.4.9.2(10). Write a sequence of two instructions that set both the Carry and Overflow flags at the same time 
  (CF(Carry Flag)와 OF(Overflow Flag)를 동시에 1로 설정하는 2개의 명령어를 작성하라.)
A. 

Q.4.9.2(11). Write a sequence of instructions showing how the Zero flag could be used to indicate unsigned overflow after executing INC and DEC instructions.
  (INC(1 증가)와 DEC(1 감소) 명령 후 Zero Flag(ZF)가 unsigned overflow를 나타내는 경우를 보여주는 명령어 시퀀스를 작성하라.)
A


Q.4.9.2(12). Insert a directive in the given data that aligns myBytes to an even-numbered address.
  (데이터 섹션에서 myBytes 변수를 **짝수 주소(even-numbered address)**에 정렬하도록 지시어를 삽입하라.)
A.             


Q.4.9.2(13). What will be the value of EAX after each of the following instructions execute?
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
A.

Q.4.9.2(14).  Write a single instruction that moves the first two bytes in myBytes to the DX register. The resulting value will be 2010h.
  (myBytes 배열의 첫 번째 두 바이트를 DX 레지스터로 이동시키는 한 줄짜리 명령어를 작성하라. 결과적으로 DX = 2010h 가 되어야 한다.)
A.             


Q.4.9.2(15).  Write an instruction that moves the second byte in myWords to the AL register.  
  (myWords 배열의 두 번째 바이트를 AL 레지스터로 이동하는 명령어를 작성하라.)
A.              



Q.4.9.2(16). Write an instruction that moves all four bytes in myBytes to the EAX register 
  (myBytes 배열의 모든 4바이트를 EAX 레지스터로 이동하는 명령어를 작성하라.)
A.             


Q.4.9.2(17). Insert a LABEL directive in the given data that permits myWords to be moved directly to a 32-bit register.
  (myWords 배열을 32비트 레지스터(EAX, EBX 등)로 바로 이동할 수 있도록 데이터 섹션에 LABEL 지시어를 추가하라.)
A.             


Q.4.9.2(18). Insert a LABEL directive in the given data that permits myBytes to be moved directly to a 16-bit register.        
  (myBytes 배열을 16비트 레지스터(DX, AX 등)로 바로 이동할 수 있도록 데이터 섹션에 LABEL 지시어를 추가하라.)
A.            
