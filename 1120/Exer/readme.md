<pre>
<mark>8.10.1</mark>
Q1.Which statements belong in a procedure’s epilogue when the procedure has stack parameters and local variables?
  (지역변수와 스택 인자가 있는 프로시저의 에필로그(함수 끝부분)에 어떤 명령들이 들어가야 하나?)
A. mov esp, ebp // 스택 포인터 복원
   pop ebp // 이전 프레임 포인터 복원
   ret 
입니다. 

Q2. When a C function returns a 32-bit integer, where is the return value stored?
  (C 함수가 32비트 정수를 반환할 때, 그 값은 어디에 저장되는가?)
A. EAX

Q3. How does a program using the STDCALL calling convention clean up the stack after a procedure call?
  (STDCALL 호출 규약을 사용하는 프로그램에서, 함수 호출 후 스택은 어떻게 정리되는가?)
A. callee(피호출자)가 ret N 명령으로 스택을 정리한다.

Q4. How is the LEA instruction more powerful than the OFFSET operator?
  (LEA 명령어가 OFFSET보다 더 강력한 이유는?)
A. LEA는 복잡한 주소 계산(레지스터 + 오프셋 + 배수)을 수행할 수 있고, OFFSET은 단순히 컴파일 타임 주소만 제공한다.

Q5. In the C++ example shown in Section 8.2.3, how much stack space is used by a variable of type int?
  (8.2.3절의 C++ 예제에서 int 타입 변수는 스택에서 얼마나 공간을 차지하는가?)
A. 4 bytes

Q6. What advantages might the C calling convention have over the STDCALL calling convention?
  (C 호출 규약(CDECL)이 STDCALL보다 가질 수 있는 장점은?)
A. 가변 인자 함수 지원, 컴파일러 간 호환성 좋음

Q7. (True/False): When using the PROC directive, all parameters must be listed on the same line.
  ([<mark>참/거짓</mark>] PROC 지시자를 쓸 때, 모든 매개변수는 한 줄에 적어야 한다.)
A. 거짓 - 여러줄에 적어도 됨

Q8. (True/False): If you pass a variable containing the offset of an array of bytes to a procedure that expects a pointer to an array of words, the assembler will flag this as an error.
  ([<mark>참/거짓</mark>] byte 배열의 주소를 word 배열 주소로 받는 함수에 넘기면, 어셈블러가 오류를 발생시킨다.)
A. 거짓 - 주소값이라 오류는 나지 않는 대신, 원하는 값이 안나올 수 있음

Q9. (True/False): If you pass an immediate value to a procedure that expects a reference parameter, you can generate a general-protection fault.
  ([<mark>참/거짓</mark>] 참조 매개변수를 기대하는 함수에 즉시값(immediate)을 넘기면, 일반 보호 오류(GP fault)가 발생할 수 있다.)
A. 참

<mark>8.10.2</mark>
Q1.  Here is a calling sequence for a procedure named AddThree that adds three doublewords
(assume that the STDCALL calling convention is used): 1 push 10h
                                                      2 push 20h
                                                      3 push 30h
                                                      4 call AddThree
Draw a picture of the procedure’s stack frame immediately after EBP has been pushed on the runtime stack.
(다음 호출 코드가 있다(STDCALL 규약 사용): 1 ~ 4, 프로시저 AddThree에 진입할 때, EBP가 push된 직후의 스택 프레임을 그리시오.
A.      30h[EBP + 16]
        20h[EBP + 12]
        10h[EBP + 8]
return addr[EBP + 4]
old EBP    [EBP + 0]

Q2.  Create a procedure named AddThree that receives three integer parameters and calculates and returns their sum in the EAX register.
  (세 개의 정수 파라미터를 받고, 그 합을 EAX에 넣어서 반환하는 AddThree 프로시저를 작성하라.)
A. AddThree PROC
    push ebp
    mov  ebp, esp

    mov eax, [ebp+8]
    add eax, [ebp+12]
    add eax, [ebp+16]

    mov esp, ebp
    pop ebp
    ret 12          
AddThree ENDP

Q3. Declare a local variable named pArray that is a pointer to an array of doublewords.
  (doubleword 배열을 가리키는 포인터 pArray를 지역 변수로 선언하라.)
A. LOCAL pArray:PTR DWORD

Q4. Declare a local variable named buffer that is an array of 20 bytes.
  (20바이트 크기의 buffer 배열을 지역 변수로 선언하라.)
A. LOCAL buffer[20]:BYTE

Q5. Declare a local variable named pwArray that points to a 16-bit unsigned integer
  (16비트 unsigned integer를 가리키는 포인터 pwArray를 지역 변수로 선언하라.)
A. LOCAL pwArray:PTR WORD

Q6. Declare a local variable named myByte that holds an 8-bit signed integer
  (8비트 signed integer를 저장하는 myByte 지역 변수를 선언하라.)
A. LOCAL myByte:SBYTE

Q7. Declare a local variable named myArray that is an array of 20 doublewords.
  (20개의 doubleword로 이루어진 배열 myArray를 지역 변수로 선언하라.)
A. LOCAL myArray[20]:DWORD

Q8. Create a procedure named SetColor that receives two stack parameters: forecolor and backcolor, and calls the SetTextColor procedure from the Irvine32 library.
  (forecolor, backcolor 두 개의 스택 파라미터를 받고, Irvine32의 SetTextColor 함수를 호출하는 SetColor 프로시저를 작성하라.)
A. SetColor PROC
    push ebp
    mov  ebp, esp

    mov eax, [ebp+8]     
    mov ebx, [ebp+12]    
    call SetTextColor

    mov esp, ebp
    pop ebp
    ret 8                
SetColor ENDP
  
Q9. Create a procedure named WriteColorChar that receives three stack parameters: char,
forecolor, and backcolor. It displays a single character, using the color attributes specified in
forecolor and backcolor.
  (char, forecolor, backcolor 세 파라미터를 받고, 주어진 색상으로 문자 하나를 출력하는 WriteColorChar 프로시저 생성)
A. WriteColorChar PROC
    push ebp
    mov  ebp, esp

    movzx eax, byte ptr [ebp+8]   ; char
    mov   ebx, [ebp+12]           ; forecolor
    mov   ecx, [ebp+16]           ; backcolor

    call SetTextColor
    call WriteChar                ; eax 의 문자 출력

    mov esp, ebp
    pop ebp
    ret 12
  WriteColorChar ENDP
  
Q10. Write a procedure named DumpMemory that encapsulates the DumpMem procedure in the
Irvine32 library. Use declared parameters and the USES directive. The following is an
example of how it should be called: INVOKE DumpMemory, OFFSET array, LENGTHOF
array, TYPE array.
  (Irvine32의 DumpMem을 감싸는 DumpMemory 프로시저를 만들고, USES 지시자와 명시적 파라미터를 사용하라.)
A. DumpMemory PROTO addr:PTR BYTE, length:DWORD, elemType:DWORD

  DumpMemory PROC USES esi edi ebx,
      addr:PTR BYTE,
      length:DWORD,
      elemType:DWORD
  
      INVOKE DumpMem, addr, length, elemType
  
      ret
  DumpMemory ENDP

Q11. Declare a procedure named MultArray that receives two pointers to arrays of doublewords,
and a third parameter indicating the number of array elements. Also, create a PROTO declaration for this procedure.
  (MultArray라는 프로시저를 선언하라. 매개변수는 다음 세 개: doubleword 배열 포인터 1, doubleword 배열 포인터 2, 요소 개수 또한 이 프로시저의 PROTO 선언도 작성하라.)
A. MultArray PROC,
    pArr1:PTR DWORD,
    pArr2:PTR DWORD,
    count:DWORD
    
    ret
    MultArray ENDP

</pre>
  
</pre>
