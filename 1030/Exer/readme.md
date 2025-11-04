<pre>
<mark>5.8.1 Qustion</mark> -
Q1.<b>Which instruction pushes all of the 32-bit general-purpose registers on the stack?</b>
  (어떤 명령어가 모든 32비트 범용 레지스터들을 스택에 푸시(push)합니까?)
A. PUSHAD 입니다.

Q2.<b>Which instruction pushes the 32-bit EFLAGS register on the stack?</b>
  (어떤 명령어가 32비트 EFLAGS 레지스터를 스택에 푸시(push)합니까?)
A.PUSHFD 입니다.

Q3.<b>Which instruction pops the stack into the EFLAGS register?</b>
  (어떤 명령어가 스택의 값을 EFLAGS 레지스터로 pop(꺼내서 저장)합니까?)
A. POPFD 입니다.

Q4.<b> Challenge: Another assembler (called NASM) permits the PUSH instruction to list multiple
specific registers. Why might this approach be better than the PUSHAD instruction in MASM? Here is a NASM example:
PUSH EAX EBX ECX</b>
  (다른 어셈블러(NASM)는 PUSH 명령어에서 여러 개의 특정 레지스터를 나열하는 것을 허용한다. 왜 이 방식이 MASM의 PUSHAD 명령어보다 더 나은 접근법일까?)
A. MASM 방식이 더 좋은 이유는 필요한 레지스터만 선택해서 PUSH를 할 수 있기 떄문입니다.

Q5.<b>Challenge: Suppose there were no PUSH instruction. Write a sequence of two other instructions that would accomplish the same as push eax.</b>
  (PUSH 명령어가 없다고 가정해보자. push eax와 동일한 동작을 하는 명령어 두 개를 작성하라.)
A. sub esp, 4
   mov [esp], eax

Q6<b>(True/False): The RET instruction pops the top of the stack into the instruction pointer.</b>
  ([<mark>참/거짓</mark>] RET 명령어는 스택의 최상단 값을 꺼내서(IP/EIP/ RIP)에 넣는다.)
A. 참

Q7<b>(True/False): Nested procedure calls are not permitted by the Microsoft assembler unless the NESTED operator is used in the procedure definition.</b>
   ([<mark>참/거짓</mark>] NESTED 연산자를 사용하지 않으면 Microsoft 어셈블러(MASM)는 중첩된 프로시저 호출을 허용하지 않는다.)
A. 거짓 - MASM에서는 중첩된 프로시저 호출은 기본적으로 허용됩니다.

Q8.<b>(True/False): In protected mode, each procedure call uses a minimum of 4 bytes of stack space</b>
  ([<mark>참/거짓</mark>] 보호 모드(protected mode)에서는 각 프로시저 호출이 최소 4바이트의 스택 공간을 사용한다.)
A. 참

Q9.<b>(True/False): The ESI and EDI registers cannot be used when passing 32-bit parameters to procedures.</b>
  ([<mark>참/거짓</mark>] 프로시저에 32비트 매개변수를 전달할 때 ESI와 EDI 레지스터는 사용할 수 없다.)
A. 거짓 - 32비트 보호 모드에서 프로시저 매개변수를 전달하는 방식은 호출 규약에 따라 다르지만, 어떤 레지스터든(ESI, EDI 포함) 매개변수로 사용할 수 있다.

Q10.<b>(True/False): The ArraySum procedure (Section 5.2.5) receives a pointer to any array of doublewords.</b>
   ([<mark>참/거짓</mark>] ArraySum 프로시저(5.2.5절)는 어떤 이중워드(doubleword) 배열이든 그 포인터를 전달받는다.)
A. 참

Q11.<b> (True/False): The USES operator lets you name all registers that are modified within a procedure. </b>
  ([<mark>참/거짓</mark>] USES 연산자는 프로시저 안에서 수정되는 모든 레지스터의 이름을 지정할 수 있게 해준다.)
A. 참

Q12.<b>(True/False): The USES operator only generates PUSH instructions, so you must code POP instructions yourself.</b>
  ([<mark>참/거짓</mark>] USES 연산자는 PUSH 명령만 생성하므로, POP 명령은 프로그래머가 직접 작성해야 한다.)
A. 거짓 - 프로시저 시작부에서 PUSH 명령어를 생성하고, RET명령어 만나기 직전 POP명령어를 생성합니다.

Q13.<b>(True/False): The register list in the USES directive must use commas to separate the register names.</b>
  ([<mark>참/거짓</mark>] USES 지시어에서 레지스터 목록은 쉼표(,)로 구분해서 써야 한다.)
A. 거짓 - MASM의 USES 연산자는 레지스터 이름을 공백으로 구분하여, 쉼표를 사용하지 않는다.

Q14.<b>Which statement(s) in the ArraySum procedure (Section 5.2.5) would have to be modified so
it could accumulate an array of 16-bit words? Create such a version of ArraySum and test it.</b>
  (5.2.5절의 ArraySum 프로시저에서, 16비트 워드 배열을 더할 수 있게 하려면 어떤 문장(statement)들을 수정해야 하는가? 
  또한, 그런 버전의 ArraySum을 작성하고 테스트하라.)
A. ArraySum PROC
    push esi        ; save ESI, ECX
    push ecx
    mov eax,0       ; set the sum to zero

    L1:
        movzx edx, WORD PTR [esi] ; read 16-bit element
        add eax, edx              ; add to sum
        add esi, TYPE WORD        ; move to next element
    
        loop L1
    
        pop ecx       ; restore ECX, ESI
        pop esi
        ret           ; sum returned in EAX
    ArraySum ENDP

Q15.<b>What will be the final value in EAX after these instructions execute? </b>
  (다음 명령어들이 실행된 후 EAX 레지스터에 최종적으로 어떤 값이 들어가게 되는가?)
    push 5
    push 6
    pop eax
    pop eax
  
A. EAX = 5

Q16.<b>Which statement is true about what will happen when the example code runs?</b>
  (예시 코드가 실행될 때 어떤 진술이 참인가?)
   1: main PROC
   2: push 10
   3: push 20
   4: call Ex2Sub
   5: pop eax
   6: INVOKE ExitProcess,0
   7: main ENDP
   8:
   9: Ex2Sub PROC
  10: pop eax
  11: ret
  12: Ex2Sub ENDP
  
  a. EAX will equal 10 on line 6 (6번 줄에서 EAX 레지스터 값이 10이 될 것이다)
  b. The program will halt with a runtime error on Line 10 (10번 줄에서 프로그램이 런타임 에러를 내고 멈출 것이다.)
  c. EAX will equal 20 on line 6 (6번 줄에서 EAX 레지스터 값이 20이 될 것이다.)
  d. The program will halt with a runtime error on Line 11 (11번 줄에서 프로그램이 런타임 에러를 내고 멈출 것이다.)
  
A. 2,3번쨰 코드에서 push 10, 20을 하여 스택 top값이 20이 저장되어있습니다. 그 다음 call을 하여 5번쨰 실행 주소를 스택에 저장하여
  스택 Top에 5번째 실행 주소가 들어가있는데 보통은 ret의 명령을 사용하여 프로시저를 빠져나오는데 이 실행주소가 필요한데, 10번째 코드
  에서 eax값에 5번째 실행 주소를 넣고 ret을 만나 20을 호출하게 되어 실행되지 않습니다. 따라서 정답은 D가 맞습니다.

Q17.<b>Which statement is true about what will happen when the example code runs?</b>
  (예시 코드가 실행될 때 무엇이 일어나는지에 대해 어떤 문장이 참인가?)
  1: main PROC 
  2: mov eax,30 
  3: push eax 
  4: push 40 
  5: call Ex3Sub 
  6: INVOKE ExitProcess,0 
  7: main ENDP 
  8: 
  9: Ex3Sub PROC 
  10: pusha
  11: mov eax,80
  12: popa
  13: ret
  14: Ex3Sub ENDP

  a. EAX will equal 40 on line 6 (6번 줄에서 EAX 레지스터 값이 40이 될 것이다.)
  b. The program will halt with a runtime error on Line 6 (프로그램이 6번 줄에서 런타임 오류로 멈출 것이다.)
  c. EAX will equal 30 on line 6 (6번 줄에서 EAX 레지스터 값이 30이 될 것이다.)
  d. The program will halt with a runtime error on Line 13 (프로그램이 13번 줄에서 런타임 오류로 멈출 것이다.)
  
A. 2번쨰 줄에서 eax에 30을 넣습니다. push가 되더라도 eax값은 여전히 남아있고, call Ex3Sub를 받아 9번쨰 줄로 jump 후
  pusha 명령어를 통해 eax레지스터를 포함한 레지스터 값들을 전부 스택에 저장하게 됩니다. 그 후 eax에 80이라는 값을 받게 되는데, popa명령어로
  인해 다시 eax는 30값을 얻게 됩니다. 따라서 정답은 C 입니다.

Q18.<b></b>

























  
</pre>
