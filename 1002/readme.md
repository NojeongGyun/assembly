1. In 32-bit mode, aside from the stack pointer (ESP), what other register points to variables on the stack? 
  (32비트 모드에서, 스택 포인터(ESP) 이외에 스택에 있는 변수들을 가리키는 다른 레지스터는 무엇인가?)
A. EBP
  
  
2. Name at least four CPU status flags. 
  (최소 네 개 이상의 CPU 상태 플래그를 말하시오.)
A. CF, OF, SF, ZF
  
  
3. Which flag is set when the result of an unsigned arithmetic operation is too large to fit into the destination?
  (부호 없는(Unsigned) 산술 연산 결과가 목적지 레지스터에 담기에는 너무 클 때 설정되는 플래그는 무엇인가?)
A. CF
  
  
4. Which flag is set when the result of a signed arithmetic operation is either too large or too small to fit into the destination? 
  (부호 있는(signed) 산술 연산 결과가 너무 커서 또는 너무 작아서 목적지 레지스터에 담기지 못할 때 설정되는 플래그는 무엇인가?)
A. OF
  

5. (True/False): When a register operand size is 32 bits and the REX prefix is used, the R8D register is available for programs to use.
  ([참/거짓] 레지스터 연산 피연산자 크기가 32비트이고 **REX 접두사(REX prefix)**가 사용될 때, 프로그램에서 R8D 레지스터를 사용할 수 있다.)
A. 거짓 80비트
  

6. Which flag is set when an arithmetic or logical operation generates a negative result?
  (산술 연산이나 논리 연산의 결과가 음수일 때 설정되는 플래그는 무엇인가?)
A. SF
  
  
7. Which part of the CPU performs floating-point arithmetic?
  (CPU의 어느 부분이 부동소수점(floating-point) 연산을 수행하는가?)
A. FPU
  
  
8. On a 32-bit processor, how many bits are contained in each floating-point data register?
  (32비트 프로세서에서 각 부동소수점(Floating-point) 데이터 레지스터는 몇 비트를 포함하는가?)
A. 80비트

  
9. (True/False): The x86-64 instruction set is backward-compatible with the x86 instruction set.
  ([참/거짓] x86-64 명령어 집합은 x86 명령어 집합과 하위 호환(backward-compatible)이 된다.)
A. 참

  
10. (True/False): In current 64-bit chip implementations, all 64 bits are used for addressing.
  ([참/거짓] 현재 64비트 칩 구현에서, 모든 64비트가 메모리 주소 지정(addressing)에 사용된다.)
A. 
  
11. (True/False): The Itanium instruction set is completely different from the x86 instruction set.
  ([참/거짓] Itanium 명령어 집합은 x86 명령어 집합과 완전히 다르다.)
A. 몰라
  
  
12. (True/False): Static RAM is usually less expensive than dynamic RAM.
  ([참/거짓] 정적 RAM(Static RAM, SRAM)은 일반적으로 동적 RAM(DRAM)보다 저렴하다.)
A. 거짓 DRAM이 더 비쌈     

  
13. (True/False): The 64-bit RDI register is available when the REX prefix is used.
  ([참/거짓] REX 접두사가 사용될 때 64비트 RDI 레지스터를 사용할 수 있다.)
A. 참


14. (True/False): In native 64-bit mode, you can use 16-bit real mode, but not the virtual-8086 mode.
  ([참/거짓] 네이티브 64비트 모드에서는 16비트 실모드(real mode)는 사용할 수 있지만, 가상 8086 모드(virtual-8086 mode)는 사용할 수 없다.)
A.몰라
  
  
15. (True/False): The x86-64 processors have 4 more general-purpose registers than the x86 processors.
  ([참/거짓] x86-64 프로세서는 x86 프로세서보다 일반 목적 레지스터를 4개 더 가지고 있다.)
A. 거짓 8개 더 가지고있음

17. (True/False): DRAM can only be erased using ultraviolet light.
  ([참/거짓] DRAM은 자외선(UV)으로만 지울 수 있다.)
A. 거짓  전원을 끄면 자동으로 지워짐
  
  
18. (True/False): In 64-bit mode, you can use up to eight floating-point registers.
  ([참/거짓] 64비트 모드에서는 최대 8개의 부동소수점(Floating-point) 레지스터를 사용할 수 있다.)
A. 거짓   최대 16개
  
24. (True/False): VRAM stands for virtual random access memory.
  ([참/거짓} VRAM은 "Virtual Random Access Memory(가상 임의 접근 메모리)"를 의미한다.)
A. 
  
26. Why do game programs often send their sound output directly to the sound card’s hardware ports?
  (게임 프로그램이 소리 출력을 종종 사운드 카드의 하드웨어 포트로 직접 보내는 이유는 무엇인가?)
A. 운영체제를 거치면 시간이 많이 걸리지만, 하드웨어 포트로 보내면 실시간 소리 출력이 가능하기 떄문입니다.

1. Provide examples of three different instruction mnemonics.
  (세 가지 다른 명령어 니모닉(Mnemonic)의 예시를 제시하시오.)
A.  mov, add, sub, inc, dec

2. What is a calling convention, and how is it used in assembly language declarations?
  (호출 규약(calling convention)이란 무엇이며, 어셈블리 언어 선언에서 어떻게 사용되는가?)
A 함수 호출 시 인자 전달, 함수값 반환, 레지스터/ 메모리 사용 방법을 정한 규칙입니다. 
  
3.How do you reserve space for the stack in a program?
  (프로그램에서 스택을 위한 공간은 어떻게 예약(할당)하는가?)
A 스택 공간은 스택 포인터를 감소 시켜 로컬 변수와 임시 데이터를 위한 공간을 확보함으로써 예약한다. 

4.  Explain why the term assembler language is not quite correct.  
  (왜 “assembler language(어셈블러 언어)”라는 용어가 정확하지 않은지 설명하시오.)
A. 어셈블러는 어셈블리 언어를 해독하는 기계이므로 어셈블러 언어는 맞지 않다.
  
5. Explain the difference between big endian and little endian. Also, look up the origins of this term on the Web  
  (빅 엔디안과 리틀 엔디안의 차이점을 설명하고, 이 용어의 유래를 웹에서 찾아보세요.)
A

6. Why might you use a symbolic constant rather than an integer literal in your code?  
  (코드에서 정수 리터럴(integer literal) 대신 **기호 상수(symbolic constant)를 사용하는 이유는 무엇인가?)
A. 가독성과 유지 보수성을 높기 때문입니다.

7.  How is a source file different from a listing file? 
  (소스 파일(source file)과 리스트 파일(listing file)은 어떻게 다른가?)
A 소스파일은 입력 코드, 리스트 파일은 기계어 + 주소 가 포함된 출력 문서입니다.

8. How are data labels and code labels different?
  (데이터 레이블(data label)과 코드 레이블(code label)은 어떻게 다른가?)
A. 데이터 레이블은 데이터 상 데이터 위치를 나타내고, 코드 레이블은 실행될 데이터의 위치를 나타냅니다.
  
9. (True/False): An identifier cannot begin with a numeric digit.  
  ([참/거짓]식별자는 숫자(digit)로 시작할 수 없다)
A 참
  
10. (True/False): A hexadecimal literal may be written as 0x3A
  ([참/거짓]16진수 리터럴은 0x3A처럼 쓸 수 있다.)
A. 참

13. Name the four basic parts of an assembly language instruction
  (어셈블리 언어 명령어의 네 가지 기본 구성 요소를 말하시오.)
A. 레이블, 명령어, 피연산자, 주석

14 (True/False): MOV is an example of an instruction mnemonic.
  ([참/거짓]MOV는 명령어 기호(instruction mnemonic)의 예이다.)
A

15. (True/False): A code label is followed by a colon (:), but a data label does not end with a colon.
  ([참/거짓]코드 레이블은 콜론(:)으로 끝나지만, 데이터 레이블은 콜론으로 끝나지 않는다.)
A
  
16. Show an example of a block comment.
  (블록 주석(block comment)의 예를 보여라.)
A /* 안령하세요 허잇 */

17.  Why is it not a good idea to use numeric addresses when writing instructions that access variables?
  (변수를 접근하는 명령어를 작성할 때, 숫자 주소(numeric address)를 사용하는 것이 좋지 않은 이유는 무엇인가?)
A. 가독성이 떨어지고, 유지보수가 힘들어서 숫자 주소를 사용하지 않는다.

18. What type of argument must be passed to the ExitProcess procedure?
  (ExitProcess라는 함수(프로시저)에 전달해야 하는 인자는 어떤 타입인가?)
A unsigned int

19. Which directive ends a procedure?  
  (어떤 지시어가 프로시저를 끝내는가?)
A ENDP

20. In 32-bit mode, what is the purpose of the identifier in the END directive?
  (32비트 모드에서, END 지시어에 있는 식별자의 목적은 무엇인가?)
A. 어셈블리에게 프로그램의 시작 주소를 지정하는 것입니다.
  
21. What is the purpose of the PROTO directive?
  (PROTO 지시어의 목적은 무엇인가?)
A 어셈블리어에서 함수(프로시저)의 이름, 인자 타입과 개수를 미리 선언하여 호출 시 검증할 수 있게 하는 것

25.  Which data directive creates a 32-bit signed integer variable?
  (어떤 데이터 지시어가 32비트 부호 있는 정수 변수를 생성하는가?)
A. DD

26. Which data directive creates a 16-bit signed integer variable?
  (어떤 데이터 지시어가 16비트 부호 있는 정수 변수를 생성하는가?)
A. DW

27. Which data directive creates a 64-bit unsigned integer variable?
  (어떤 데이터 지시어가 64비트 부호 없는 정수 변수를 생성하는가?)
A.  QWORD

28. Which data directive creates an 8-bit signed integer variable?
  (어떤 데이터 지시어가 8비트 부호 있는 정수 변수를 생성하는가?)
 A. DB 

29. Which data directive creates a 10-byte packed BCD variable?
  (어떤 데이터 지시어가 10바이트 패킹된 BCD 변수를 생성하는가?)
A. DT


<3.9.2>
1. Define four symbolic constants that represent integer 25 in decimal, binary, octal, and hexadecimal formats
  (정수 25를 10진수, 2진수, 8진수, 16진수 형식으로 나타내는 네 개의 기호 상수를 정의하라.)
A. 10진수 - [DEC_CONST  EQU 25], 
   2진수 - [BIN_CONST  EQU 11001b] 
   8진수 - [OCT_CONST  EQU 31o]       
   16진수 - [HEX_CONST  EQU 19h]
  
2. Find out, by trial and error, if a program can have multiple code and data segments.
  (시행착오(trial and error)를 통해, 프로그램이 여러 개의 코드와 데이터 세그먼트를 가질 수 있는지 알아보라.)
A. 
  .data
  var1 DB 10

  .data
  var2 DB 20
  
  .code
  start1:
      mov al, var1
  
  .code
  start2:
      mov bl, var2
  
  END start1
  
- 여러개의 .data의 세그먼트와 여러개의 코드를 가지고도 실행이 된다.

3. Create a data definition for a doubleword that stored it in memory in big endian format.
  (빅 엔디안(big endian) 형식으로 메모리에 저장되는 더블워드(doubleword, 32비트) 변수를 정의하라.)
A.  32비트값 12345678h   myval DB 12h 34h 

6. Given the number 456789ABh, list out its byte values in little-endian order.
  (숫자 456789ABh를 리틀 엔디안(Little-endian) 순서로 메모리에 저장할 때 각 바이트 값을 나열하라)
A. ABh, 89h, 67h, 45h

7. Declare an array of 120 uninitialized unsigned doubleword values
  (120개의 초기화되지 않은 부호 없는 더블워드(DWORD) 값으로 이루어진 배열을 선언하라.)
A. myval DWORD 120 DUP(?)

8. Declare an array of byte and initialize it to the first 5 letters of the alphabet
  (바이트 배열을 선언하고 알파벳 첫 5글자로 초기화하라.)
A. myArray DB 'A','B','C','D','E'

9. Declare a 32-bit signed integer variable and initialize it with the smallest possible
  (32비트 부호 있는 정수 변수를 선언하고, 가능한 가장 작은 값으로 초기화하라.)
A. num DW 대충 - (2의 31승) 이라는뜻

10. Declare an unsigned 16-bit integer variable named wArray that uses three initializers.
  (wArray라는 이름의 16비트 부호 없는 정수 변수를 선언하고, 세 개의 초기값을 사용하라.)
A. wArray DW 1000h, 2000h, 3000h

11. Declare a string variable containing the name of your favorite color. Initialize it as a nullterminated string.
  (좋아하는 색 이름을 담는 문자열 변수를 선언하고, 널(null) 종료 문자열로 초기화하라.)
A. favoriteColor DB 'Blue',0 

12. Declare an uninitialized array of 50 signed doublewords named dArray
  (dArray라는 이름의 50개 부호 있는 더블워드(DWORD) 배열을 초기화하지 않고 선언하라.)
A. dArray DD 50 DUP(?) 

13. Declare a string variable containing the word “TEST” repeated 500 times.
  (문자열 변수 하나를 선언하고, ‘TEST’라는 단어를 500번 반복하여 초기화하라.)
A. mystring DB 500 DUP("T", "E", "S", "T")

14. Declare an array of 20 unsigned bytes named bArray and initialize all elements to zero
  (bArray라는 이름의 20개 부호 없는 바이트 배열을 선언하고, 모든 요소를 0으로 초기화하라.)
A. bArray DB 20 DUP(0)

15. Show the order of individual bytes in memory (lowest to highest) for the following doubleword variable: val1 DWORD 87654321h
  (val1 DWORD 87654321h 변수의 메모리에서 바이트 순서(낮은 주소 → 높은 주소)를 보여라.)




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
