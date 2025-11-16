<pre>
- <mark>7.9.1</mark> -
Q1.<b>In the following code sequence, show the value of AL after each shift or rotate instruction has executed</b>
  (다음 코드 시퀀스에서, 각각의 쉬프트(shift) 또는 로테이트(rotate) 명령어가 실행된 후 AL 레지스터의 값을 보여라.)
  mov al,0D4h
  shr al,1 ; a.
  
  mov al,0D4h
  sar al,1 ; b.
  
  mov al,0D4h
  sar al,4 ; c.
  
  mov al,0D4h
  rol al,1 ; d.
A. a - 68h, b - EAh, c - FDh, d - A9h

Q2.<b>In the following code sequence, show the value of AL after each shift or rotate instruction has executed</b>
  (다음 코드 시퀀스에서, 각각의 쉬프트(shift) 또는 로테이트(rotate) 명령어가 실행된 후 AL 레지스터의 값을 보여라.)
  mov al,0D4h
  ror al,3 ; a.
  
  mov al,0D4h
  rol al,7 ; b.
  
  stc
  mov al,0D4h
  rcl al,1 ; c.
  
  stc
  mov al,0D4h
  rcr al,3 ; d.
A. a - 9Ah, b - 6Ah, c - A9h, d - 3Ah

Q3.<b>What will be the contents of AX and DX after the following operation?</b>
  (다음 연산이 끝난 후 AX와 DX 레지스터의 내용은 무엇인가?)
  mov dx,0
  mov ax,222h
  mov cx,100h
  mul cx
A. DX -	0002h, AX -	2200h

Q4.<b>What will be the contents of AX after the following operation?</b>
  (다음 연산이 끝난 후 AX 레지스터의 내용은 무엇인가?)
  mov ax,63h
  mov bl,10h
  div bl
A. AX - 0306h

Q5.<b>What will be the contents of EAX and EDX after the following operation?</b>
  (다음 연산이 끝난 후 EAX와 EDX 레지스터의 내용은 무엇인가?)
  mov eax,123400h
  mov edx,0
  mov ebx,10h
  div ebx
A. EAX - 00012340h, EDX	- 00000000h

Q6.<b>What will be the contents of AX and DX after the following operation?</b>
  (다음 연산이 끝난 후 AX와 DX 레지스터의 내용은 무엇인가?)
  mov ax,4000h
  mov dx,500h
  mov bx,10h
  div bx
A. ax는 몫, dx는 나머지를 저장하는데, ax레지스터 정수 허용 범위보다 몫이 더 크기에 over flow가 발생하여, 하위 16개의 비트 값만 넣으면
  ax = 0400h, dX = 0000h 입니다.
  
Q7.<b>What will be the contents of BX after the following instructions execute?</b>
  (다음 명령들이 실행된 후 BX 레지스터에는 어떤 값이 들어가게 되는가?)
  mov bx,5
  stc  // carry flag를 1로 만듬
  mov ax,60h
  adc bx,ax
A. bx - 0066h

Q8.<b> Describe the output when the following code executes in 64-bit mode</b>
  (다음 코드가 64비트 모드에서 실행될 때 출력이 어떻게 되는지 설명하라.)
  .data
  dividend_hi QWORD 00000108h
  dividend_lo QWORD 33300020h
  divisor QWORD 00000100h
  
  .code
  mov rdx,dividend_hi
  mov rax,dividend_lo
  div divisor
A. RAX - 000000000108000000333000h, RDX - 20h

Q9.<b>The following program is supposed to subtract val2 from val1. Find and correct all logic errors (CLC clears the Carry flag)</b>
  (다음 프로그램은 val1에서 val2를 빼려고 만든 것이다. 모든 논리적 오류를 찾아 수정하라. (CLC는 Carry 플래그를 0으로 만든다))
  .data
  val1 QWORD 20403004362047A1h
  val2 QWORD 055210304A2630B2h
  result QWORD 0
    
  .code
  mov cx,8 ; loop counter
  mov esi,val1 ; set index to start
  mov edi,val2
  clc ; clear Carry flag
  top:
    mov al,BYTE PTR[esi] ; get first number
    sbb al,BYTE PTR[edi] ; subtract second
    mov BYTE PTR[esi],al ; store the result
    dec esi
    dec edi
  loop top
  
A. .data
  val1    QWORD 20403004362047A1h
  val2    QWORD 055210304A2630B2h
  result  QWORD 0

.code
mov rcx, 8                
mov rsi, OFFSET val1   
mov rdi, OFFSET val2     
mov rbx, OFFSET result    

  add rsi, 7
  add rdi, 7
  add rbx, 7
  
  clc                       ; clear carry
  
  top:
      mov al, [rsi]
      sbb al, [rdi]
      mov [rbx], al
  
      dec rsi
      dec rdi
      dec rbx
  loop top

Q10.<b>What will be the hexadecimal contents of RAX after the following instructions execute in 64-bit mode?</b>
  (64비트 모드에서 아래 명령들이 실행된 후 RAX 레지스터에는 어떤 16진수 값이 들어가는가?)
  .data
  multiplicand QWORD 0001020304050000h
  
  .code
  imul rax,multiplicand, 4
A. rax - 0004080C10140000h

- <mark>7.9.2</mark> -
Q1.<b> Write a sequence of shift instructions that cause AX to be sign-extended into EAX. In other words,
the sign bit of AX is copied into the upper 16 bits of EAX. Do not use the CWD instruction.</b>
(X의 부호비트를 EAX 전체(상위 16비트까지)로 확장하라. CWD 금지. Shift 명령만 사용해서 sign-extend 만들기.)
A. movzx eax, ax   
   shl eax, 16     
   sar eax, 16     

Q2.<b>Suppose the instruction set contained no rotate instructions. Show how you would use SHR and a conditional 
jump instruction to rotate the contents of the AL register 1 bit to the right.</b>
(명령어 집합에 rotate 명령이 없다고 가정하자. SHR 명령과 조건 분기(conditional jump) 명령을 사용하여 AL 레지스터의 내용을 오른쪽으로 1비트 ‘회전(rotate)’시키는 방법을 보여라.)
A. shr al, 1          
   jnc no_carry        

   or al, 80h       
   jmp done

   no_carry:
   and al, 7Fh     
   done:

Q3.<b>Write a logical shift instruction that multiplies the contents of EAX by 16.</b>
  (EAX 값을 16배로 만드는 논리 쉬프트 명령을 하나 작성하라.)
A. shl eax, 4

Q4.<b>Write a logical shift instruction that divides EBX by 4</b>
  (EBX를 4로 나누는 논리적 쉬프트 명령을 작성하라.)
A. shr ebx, 2

Q5.<b>Write a single rotate instruction that exchanges the high and low halves of the DL register.</b>
  (DL 레지스터(8비트)의 상위 4비트와 하위 4비트를 서로 바꾸는 단일 회전(rotate) 명령어를 작성하라.)
A. ror dl, 4

Q6.<b>Write a single SHLD instruction that shifts the highest bit of the AX register into the lowest bit position of DX and shifts DX one bit to the left.</b>
  (AX 레지스터의 최상위 비트(MSB)를 DX 레지스터의 최하위 비트(LSB)로 옮기고, 동시에 DX를 1비트 왼쪽으로 이동시키는 명령어를 작성하라.
A. shld dx, ax, 1

Q7.<b>Write a sequence of instructions that shift three memory bytes to the right by 1 bit position.</b>
  (메모리의 3바이트 데이터를 1비트씩 오른쪽으로 시프트하는 명령어들을 작성하라.)
  - Use the following test data -
  byteArray BYTE 81h,20h,33h
  
A.  mov al, byte ptr [byteArray+0]  
    shr al, 1                      
    mov bl, al                   
    mov al, byte ptr [byteArray+1] 
    rcr al, 1                       
    mov byte ptr [byteArray+1], al   
    mov al, byte ptr [byteArray+2] 
    rcr al, 1                       
    mov byte ptr [byteArray+2], al 
    mov byte ptr [byteArray+0], bl   

Q8.<b>Write a sequence of instructions that shift three memory words to the left by 1 bit position. Use the following test data</b>
  (3개의 메모리 워드(각 16비트) 데이터를 1비트씩 왼쪽으로 이동시키는 명령어 시퀀스를 작성하라.)
   - Use the following test data -
    wordArray WORD 810Dh, 0C064h,93ABh

A.  mov ax, word ptr [wordArray+4] 
    shl ax, 1                    
    mov cx, ax                  
    shr ax, 16-1                     
    mov word ptr [wordArray+4], cx
    
    mov ax, word ptr [wordArray+2]
    shl ax, 1
    rcl ax, 1                       
    mov word ptr [wordArray+2], ax

    mov ax, word ptr [wordArray+0]
    shl ax, 1
    rcl ax, 1                       
    mov word ptr [wordArray+0], ax

Q9.<b>Write instructions that multiply 5 by 3 and store the result in a 16-bit variable val1.</b>
  (숫자 5와 3을 곱하고, 결과를 16비트 변수 val1에 저장하는 어셈블리 명령어를 작성하라.)
A. .data
    val1 WORD 0     
  
    .code
    mov ax, 5        
    imul ax, 3       
    mov val1, ax     

Q10.<b>Write instructions that divide 276 by 10 and store the result in a 16-bit variable val1.</b>
  (숫자 276을 10으로 나누고, 몫(quotient)을 16비트 변수 val1에 저장하는 어셈블리 명령어를 작성하라.
A. .data
    val1 WORD 0     
    
    .code
    mov ax, 276      
    mov bx, 10      
    cwd            
    div bx           
    mov val1, ax     

Q11.<b> Implement the following C++ expression in assembly language, using 32-bit unsigned operands</b>
  (주어진 C++ 식을 32비트 unsigned 변수를 사용해서 어셈블리로 구현하시오)
  val1 = (val2 * val3) / (val4 - 3)
A. .data
    val1 DWORD 0
    val2 DWORD 100
    val3 DWORD 5
    val4 DWORD 20
    
    .code
    mov eax, val2     
    imul eax, val3      
    
    mov ebx, val4      
    sub ebx, 3          
    
    xor edx, edx      
    div ebx            
    
    mov val1, eax       

Q12.<b> Implement the following C++ expression in assembly language, using 32-bit signed operands</b>
  (주어진 C++ 식을 32비트 unsigned 변수를 사용해서 어셈블리로 구현하시오)
  val1 = (val2 / val3) * (val1 + val2)
A. .data
    val1 DWORD 10
    val2 DWORD 50
    val3 DWORD 5
    
    .code
    mov eax, val2   
    cdq                
    idiv dword ptr [val3] 
    mov ebx, val1
    add ebx, val2     
    imul eax, ebx      
    mov val1, eax    

Q13.<b>Write a procedure that displays an unsigned 8-bit binary value in decimal format. Pass the
binary value in AL. The input range is limited to 0 to 99, decimal. The only procedure you can call from the book’s link library is WriteChar. 
The procedure should contain approximately eight instructions. Here is a sample call</b>
AL 레지스터에 있는 0~99 범위의 8비트 unsigned 값을 십진수(decimal) 문자열로 변환하여 출력하는 프로시저를 작성하라.
명령어 수는 약 8개 정도이고, 출력은 책에서 제공하는 WriteChar만 사용 가능
A. PrintDec PROC
      mov ah, 0              
      mov bl, 10             
      div bl                 
      add al, '0'            
      call WriteChar         
      add ah, '0'           
      call WriteChar        
      ret
  PrintDec ENDP

Q14.<b> Challenge: Suppose AX contains 0072h and the Auxiliary Carry flag is set as a result of
adding two unknown ASCII decimal digits. Use the Intel 64 and IA-32 Instruction Set Reference to determine what output the AAA instruction would produce. Explain your answer.</b>
문제: AAA를 실행하면 AL과 AH가 어떻게 변하고, CF/AF가 어떻게 되는지 설명하라.
AX = 0072h, Auxiliary Carry(AC) 플래그가 세트됨 (즉, 하위 4비트 덧셈에서 자리 올림 발생) , AAA (ASCII Adjust after Addition) 명령어를 실행하면 AL 레지스터가 **BCD(Decimal Adjusted)**로 변환됨.

A. AAA는 AF가 세트되면 하위 4비트에 6을 더하고 상위 자리 올림을 수행하기에 AL = 78h, AH = 01h, CF = 1, AF = 1 

Q15.<b> Challenge: Using only SUB, MOV, and AND instructions, show how to calculate x = n mod y, assuming that you are given the values of n and y. 
You can assume that n is any 32-bit unsigned integer, and y is a power of 2.</b>
SUB, MOV, AND 명령어만 사용해서 x = n mod y를 계산하는 방법을 보여주세요. n과 y의 값이 주어져 있다고 가정하고, n은 32비트 부호 없는 정수이고, y는 2의 거듭제곱이라고 가정합니다.
A. mov eax, n      
   mov ebx, y      
   sub ebx, 1     
   and eax, ebx    
   mov x, eax      

Q16.<b>Challenge: Using only SAR, ADD, and XOR instructions (but no conditional jumps), write code that calculates the absolute value of the signed 
integer in the EAX register. Hints: A number can be negated by adding 1 to it and then forming its one’s complement. Also, if
you XOR an integer with all 1s, its 1s are reversed. On the other hand, if you XOR an integer with all zeros, the integer is unchanged.</b>
EAX 레지스터에 들어있는 부호 있는 정수의 절댓값을 계산하라. 사용할 수 있는 명령어는 SAR, ADD, XOR 뿐이며, 조건문이나 점프는 사용 불가.
힌트:
 1. 수를 **부호 반전(negate)**하려면, 1을 더한 후 1의 보수(complement)를 취하면 됨.
 2. XOR를 사용하면 특정 패턴과 비트 단위로 반전 가능: XOR 0 → 값 그대로, XOR 0xFFFFFFFF → 모든 비트 반전

A. mov ebx, eax     
  sar eax, 31       
  add ebx, eax      
  xor ebx, eax 
  mov eax, ebx   

</pre>
