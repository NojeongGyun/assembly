<pre>
- 6.10.1 -
Q1.<b>What will be the value of BX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 BX 레지스터의 값은 얼마가 될까요?)
  mov bx,0FFFFh
  and bx,6Bh
A. 006Bh

Q2.<b>What will be the value of BX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 BX 레지스터의 값은 얼마가 될까요?)
  mov bx,91BAh
  and bx,92h
A. 0092h

Q3.<b> What will be the value of BX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 BX 레지스터의 값은 얼마가 될까요?)
  mov bx,0649Bh
  or bx,3Ah
A. 64BBh

Q4.<b>What will be the value of BX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 BX 레지스터의 값은 얼마가 될까요?)
  mov bx,029D6h
  xor bx,8181h
A. A857h

Q5.<b>What will be the value of EBX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 EBX 레지스터의 값은 얼마가 될까요?)
  mov ebx,0AFAF649Bh 
  or ebx,3A219604h
A. BFAFF69Fh

Q6.<b>What will be the value of RBX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 RBX 레지스터의 값은 얼마가 될까요?)
  mov rbx,0AFAF649Bh
  xor rbx,0FFFFFFFFh
A. F0509B64h

Q7.<b>In the following instruction sequence, show the resulting value of AL where indicated, in binary</b>
  (다음 명령어 순서에서, 표시된 부분마다 AL 레지스터의 결과 값을 2진수(binary) 로 보이시오.)
  mov al,7Ah
  not al ; a.
  
  mov al,3Dh
  and al,74h ; b.
  
  mov al,9Bh
  or al,35h ; c.
  
  mov al,72h
  xor al,0DCh ; d.
A. a - 85h, b - 34h, c - BFh, d - AEh

Q8.<b>In the following instruction sequence, show the resulting value of AL where indicated, in hexadecimal</b>
  (다음 명령어 순서에서, 표시된 지점마다 **AL 레지스터의 결과 값을 16진수(HEX)**로 보이시오.)
  mov al,7Ah
  not al ; a.
  
  mov al,3Dh
  and al,74h ; b.
  
  mov al,9Bh
  or al,35h ; c.
  
  mov al,72h
  xor al,0DCh ; d.
A. a - 85h, b - 34h, c - BFh, d - AEh
  
Q9.<b>In the following instruction sequence, show the values of the Carry, Zero, and Sign flags where indicated</b>
  (다음 명령어 순서에서, 표시된 지점마다 Carry(캐리), Zero(제로), Sign(부호) 플래그의 값을 보이시오.)
  mov al,00001111b
  test al,00000010b ; a. CF= ZF= SF=
  mov al,00000110b
  cmp al,00000101b ; b. CF= ZF= SF=
  mov al,00000101b
  cmp al,00000111b ; c. CF= ZF= SF=
A. a(CF=0, ZF=0, SF=0), b(CF=0, ZF=0, SF=0), c(CF=1, ZF=0, SF=1)

Q10.<b>Which conditional jump instruction executes a branch based on the contents of ECX?</b>
  (ECX 레지스터의 값에 따라 분기(branch)를 실행하는 조건부 점프 명령어는 무엇인가요?)
A. loop, loope/loopz, loopne/loopnz 

Q11.<b> How are JA and JNBE affected by the Zero and Carry flags?</b>
  (JA와 JNBE 점프 명령어는 Zero 플래그(ZF)와 Carry 플래그(CF)에 어떤 영향을 받나요?)
A. JA와 JNBE는 ZF와 CF 둘 다 0일 때만 점프합니다.

Q12.<b>What will be the final value in EDX after this code executes?</b>
  (이 코드가 실행된 후 EDX 레지스터의 최종 값은 무엇인가요?)
     mov edx,1
     mov eax,7FFFh
     cmp eax,8000h
     jl L1
     mov edx,0
  L1:
A. EDX = 1

Q13.<b>What will be the final value in EDX after this code executes?</b>
 (이 코드가 실행된 후 EDX 레지스터의 최종 값은 무엇인가요?)
     mov edx,1
     mov eax,7FFFh
     cmp eax,8000h
     jb L1
     mov edx,0
  L1:
A. EDX = 1

Q14.<b>What will be the final value in EDX after this code executes?</b>
  (이 코드가 실행된 후 EDX 레지스터의 최종 값은 무엇인가요?)
     mov edx,1
     mov eax,7FFFh
     cmp eax,0FFFF8000h
     jl L2
     mov edx,0
  L2:
A. EDX = 0

Q15.<b>(True/False): The following code will jump to the label named Target</b>
  ([<mark>참/거짓</mark>] 다음 코드는 Target이라는 레이블로 점프할까요?)
  mov eax,-30
  cmp eax,-50
  jg Target
A. 참

Q16.<b>(True/False): The following code will jump to the label named Target.</b>
  ([<mark>참/거짓</mark>] 다음 코드는 Target이라는 레이블로 점프할까요?)
  mov eax,-42
  cmp eax,26
  ja Target
A. 참

Q17.<b>What will be the value of RBX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 RBX 레지스터의 값은 무엇이 될까요?)
  mov rbx,0FFFFFFFFFFFFFFFFh
  and rbx,80h
A. rbx = 0000000000000080h

Q18.<b>What will be the value of RBX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 RBX 레지스터의 값은 무엇이 될까요?)
  mov rbx,0FFFFFFFFFFFFFFFFh
  and rbx,808080h
A. rbx = 0000000000808080h

Q19.<b>What will be the value of RBX after the following instructions execute?</b>
  (다음 명령어들이 실행된 후 RBX 레지스터의 값은 무엇이 될까요?)
  mov rbx,0FFFFFFFFFFFFFFFFh
  and rbx,80808080h
A. rbx = 80808080h

- 6.10.2 -
Q1.<b>Write a single instruction that converts an ASCII digit in AL to its corresponding binary
value. If AL already contains a binary value (00h to 09h), leave it unchanged.</b>
(AL 레지스터에 있는 ASCII 숫자(예: '0' = 30h, '1' = 31h … '9' = 39h)를 해당하는 2진 값(0~9)으로 변환하는 단일 명령어를 작성하세요.
만약 AL이 이미 0~9(00h~09h) 범위의 2진 값이면 그대로 두세요.)
A. sub al, 30h

Q2.<b>Write instructions that calculate the parity of a 32-bit memory operand. 
  Hint: Use the formula presented earlier in this section: B0 XOR B1 XOR B2 XOR B3.</b>
(32비트 메모리 피연산자의 **패리티(parity)**를 계산하는 명령어들을 작성하세요.
힌트: 이전에 소개된 공식 B0 XOR B1 XOR B2 XOR B3를 사용하세요. 여기서 B0, B1, B2, B3는 32비트 값을 바이트 단위로 나눈 것입니다.)
A. mov al, byte ptr [mem32]      ; B0 → AL
   xor al, byte ptr [mem32+1]    ; B0 XOR B1
   xor al, byte ptr [mem32+2]    ; XOR B2
   xor al, byte ptr [mem32+3]    ; XOR B3

Q3.<b>Given two bit-mapped sets named SetX and SetY, write a sequence of instructions that generate a 
  bit string in EAX that represents members in SetX that are not members of SetY.</b>
(SetX와 SetY라는 비트맵 집합이 주어졌을 때, EAX에 SetX에는 속하지만 SetY에는 속하지 않는 멤버를 나타내는 비트 문자열을 생성하는 명령어 시퀀스를 작성하세요.)
A. mov eax, [SetX]   
   mov ebx, [SetY]  
   not ebx          
   and eax, ebx      

Q4.<b>Write instructions that jump to label L1 when the unsigned integer in DX is less than or equal to the integer in CX.</b>
  (DX 레지스터에 있는 부호 없는(unsigned) 정수가 CX 레지스터에 있는 값보다 작거나 같으면, L1 레이블로 점프하는 명령어를 작성하세요.)
A. cmp dx, cx   
   jbe L1      

Q5.<b>Write instructions that jump to label L2 when the signed integer in AX is greater than the integer in CX.</b>
  (AX 레지스터에 있는 부호 있는(signed) 정수가 CX 레지스터에 있는 값보다 크면, L2 레이블로 점프하는 명령어를 작성하세요.)
A. cmp ax, cx   
   jg L2        

Q6.<b>Write instructions that first clear bits 0 and 1 in AL. Then, if the destination operand is equal to zero, 
  the code should jump to label L3. Otherwise, it should jump to label L4</b>  
(먼저 AL 레지스터의 비트 0과 1을 0으로 클리어하세요. 그 다음 AL의 값이 0이면 L3 레이블로 점프하고, 그렇지 않으면 L4 레이블로 점프하도록 코드를 작성하세요.
A. and al, 0FCh  
   cmp al, 0    
   je L3         
   jne L4       

Q7.<b>Implement the following pseudocode in assembly language. Use short-circuit evaluation and assume that val1 and X are 32-bit variables.</b>
(다음 의사코드를 어셈블리 언어로 구현하세요. 1. 단락 평가(short-circuit evaluation)**를 사용합니다. 2. val1과 X는 32비트 변수입니다. 
3. if( val1 > ecx ) AND ( ecx > edx ) 
      X = 1 
   else 
      X = 2;
)
A. mov eax, [val1]   
   cmp eax, ecx      
   jle ELSE          
  
   cmp ecx, edx     
   jle ELSE          
  
   mov dword ptr [X], 1
   jmp END_IF
  
   ELSE:
   mov dword ptr [X], 2
  
   END_IF:

Q8.<b>Implement the following pseudocode in assembly language. Use short-circuit evaluation and assume that X is a 32-bit variable.</b>
(다음 의사코드를 어셈블리 언어로 구현하세요. 1. **단락 평가(short-circuit evaluation)**를 사용합니다. 2. X는 32비트 변수입니다.
3. if( ebx > ecx ) OR ( ebx > val1 )
      X = 1
   else
      X = 2
)
A.  cmp eax, ebx        
    jle ELSE_LABEL    
    
    cmp ecx, edx        
    jle ELSE_LABEL     
    
    mov dword ptr [X], 1
    jmp END_IF
    
    ELSE_LABEL:
    mov dword ptr [X], 2
    
    END_IF:

Q9.<b>Implement the following pseudocode in assembly language. Use short-circuit evaluation and assume that X is a 32-bit variable.</b>
(다음 의사코드를 어셈블리 언어로 구현하세요. 1. **단락 평가(short-circuit evaluation)**를 사용합니다. 2. X는 32비트 변수입니다.
3. (ebx > ecx AND ebx > edx) OR ( edx > eax )
      X = 1
   else
      X = 2
)
A. cmp ebx, ecx       
   jle CHECK_OR       
    
   cmp ebx, edx      
   jle CHECK_OR        
    
   mov dword ptr [X], 1
   jmp END_IF
    
   CHECK_OR:
   cmp edx, eax      
   jle ELSE_LABEL      
    
   mov dword ptr [X], 1
   jmp END_IF
    
   ELSE_LABEL:
   mov dword ptr [X], 2
    
   END_IF:

Q10.<b>Implement the following pseudocode in assembly language. Use short-circuit evaluation and assume that A, B, and N are 32-bit signed integers.</b>
(다음 의사코드를 어셈블리 언어로 구현하세요. 1. 단락 평가(short-circuit evaluation) 사용 2. A, B, N은 32비트 부호 있는(signed) 정수
3. while N > 0
     if N != 3 AND (N < A OR N > B)
       N = N – 2
     else
       N = N – 1
    end whle
)
A. WHILE_LOOP:
    mov eax, [N]      
    cmp eax, 0
    jle END_WHILE      

    cmp eax, 3
    je ELSE_BRANCH   

    cmp eax, [A]       
    jl IF_BRANCH      
    cmp eax, [B]      
    jg IF_BRANCH       

  ELSE_BRANCH:
    sub eax, 1
    jmp UPDATE_N

  IF_BRANCH:
    sub eax, 2

  UPDATE_N:
    mov [N], eax
    jmp WHILE_LOOP

  END_WHILE:
       
</pre>
