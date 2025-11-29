<pre>
<mark>9.9.1</mark> 
Q1. Which Direction flag setting causes index registers to move backward through memory 
  when executing string primitives?
  (어떤 방향 플래그 설정이 문자열 처리 명령어 실행 시 인덱스 레지스터가 메모리에서 뒤로 이동하게 만드나요?)
A. DF = 1

Q2. When a repeat prefix is used with STOSW, what value is added to or subtracted from the
index register?
  (반복 접두사가 STOSW와 함께 사용될 때, 인덱스 레지스터에 더해지거나 빼지는 값은 무엇인가요?)
A. EDI, ESI
  
Q3. In what way is the CMPS instruction ambiguous?
  (CMPS 명령어가 모호한 방식으로 작동하는 이유는 무엇인가요?)
A. CMPS 명령어는 비교할 데이터 크기가 명시되지 않아 모호합니다.
  
Q4. When the Direction flag is clear and SCASB has found a matching character, where does
EDI point?
  (방향 플래그(Direction Flag, DF)가 clear(0)일 때, SCASB 명령어가 일치하는 문자를 찾으면, EDI는 어디를 가리키나요?)
A. SCASB가 일치하는 문자를 찾으면, EDI는 1만큼 증가하여 그 다음 메모리 위치를 가리킵니다.
  
Q5. When scanning an array for the first occurrence of a particular character, which repeat prefix would be best?
  (특정 문자의 첫 번째 발생을 찾기 위해 배열을 스캔할 때, 어떤 반복 접두사(repeat prefix)가 가장 좋을까요?)
A. REPE 접두사
  
Q6. What Direction flag setting is used in the Str_trim procedure from Section 9.3?
  (Str_trim 절차에서 사용하는 방향 플래그(Direction Flag, DF)의 설정은 무엇인가요? (9.3 섹션에서))
A. 방향 플래그(Directional Flag, DF)를 1로 설정입니다.

Q7. Why does the Str_trim procedure from Section 9.3 use the JNE instruction?
  (Str_trim 절차에서 JNE 명령어를 사용하는 이유는 무엇인가요? (9.3 섹션에서))
A. JNE를 사용하는 이유는 공백이 아닌 문자를 발견했을 때, 그 문자를 처리하기 위해 점프하도록 하기 위함입니다.

Q8. What happens in the Str_ucase procedure from Section 9.3 if the target string contains a
digit?
  (Str_ucase 절차에서, 만약 대상 문자열에 숫자가 포함되어 있으면 어떻게 되나요? (9.3 섹션에서))
A. 문자열에 숫자가 포함되어 있으면, 그 숫자는 변환되지 않고 그대로 남습니다.
  
Q9. If the Str_length procedure from Section 9.3 used SCASB, which repeat prefix would be
most appropriate?
  (Str_length 절차에서 SCASB를 사용한다면, 가장 적합한 반복 접두사는 무엇인가요? (9.3 섹션에서))
A. REPE 접두사
  
Q10. If the Str_length procedure from Section 9.3 used SCASB, how would it calculate and
return the string length?
  (Str_length 절차에서 SCASB 명령어를 사용하면 문자열의 길이를 어떻게 계산하고 반환하나요? (9.3 섹션에서))
A. REPE와 SCASB 명령어로 널 문자를 찾고, 그 후 DI - SI - 1을 계산하여 길이를 반환합니다.
  
Q11. What is the maximum number of comparisons needed by the binary search algorithm when
an array contains 1,024 elements?
  (배열에 1,024개의 요소가 있을 때 이진 탐색 알고리즘이 필요한 최대 비교 횟수는 얼마인가요?)
A. 2 ^ 10 = 1024 이므로 총 10번입니다. 
  
Q12. In the FillArray procedure from the Binary Search example in Section 9.5, why must the
Direction flag be cleared by the CLD instruction?
  (Binary Search 예제의 FillArray 절차에서 방향 플래그를 CLD 명령어로 클리어해야 하는 이유는 무엇인가요? (9.5 섹션에서))
A. SI와 DI가 증가하도록 하여 배열에 값을 올바르게 채우기 위함입니다.
  
Q13. In the BinarySearch procedure from Section 9.5, why could the statement at label L2 be
removed without affecting the outcome?
  (BinarySearch 절차에서 9.5 섹션에 있는 L2 라벨의 명령어를 제거해도 결과에 영향을 미치지 않는 이유는 무엇인가요?)
A. 흐름을 유지하기 위한 추가적인 처리일 뿐이며, 다른 조건문이나 반복문에서 이미 충분히 처리되고 있기 때문입니다.
  
Q14. In the BinarySearch procedure from Section 9.5, how might the statement at label L4 be
eliminated?
  (BinarySearch 절차에서 9.5 섹션에 있는 L4 라벨의 명령어를 어떻게 제거할 수 있을까요?)
A. 조건문 통합이나 불필요한 점프 제거를 통해 L4 라벨의 명령어를 제거할 수 있습니다.

<mark>9.9.2</mark>
Q1. Show an example of a base-index operand in 32-bit mode.
  (32비트 모드에서 base-index operand의 예를 보여주세요.)
A. mov eax, [ebx + esi*4]
  
Q2. Show an example of a base-index-displacement operand in 32-bit mode.
  (32비트 모드에서 base-index-displacement operand의 예를 보여주세요.)
A. mov eax, [ebx + esi*4 + 8]
  
Q3. Suppose a two-dimensional array of doublewords has three logical rows and four logical
columns. Write an expression using ESI and EDI that addresses the third column in the second row. (Numbering for rows and columns starts at zero.)
  [해석]
두 차원 배열이 있으며, 이 배열은 3개의 논리적 행과 4개의 논리적 열을 가지고 있습니다. ESI와 EDI를 사용하여 두 번째 행의 세 번째 열을 주소 지정하는 표현식을 작성하세요. (행과 열의 번호는 0부터 시작합니다.)
A. mov eax, [esi + edi*4 + 4*4]
  
Q4. Write instructions using CMPSW that compare two arrays of 16-bit values named sourcew and targetw.
  (16비트 값으로 구성된 두 배열 sourcew와 targetw를 비교하는 CMPSW 명령어를 사용한 어셈블리 코드를 작성하세요.)
A.  mov esi, offset sourcew    
    mov edi, offset targetw    
    mov ecx, 4                
  
    compare_loop:
      cmpsw                   
      je  elements_equal    
  
    loop compare_loop     

elements_equal:
   
  
Q5. Write instructions that use SCASW to scan for the 16-bit value 0100h in an array named
wordArray, and copy the offset of the matching member into the EAX register.
  ()
A. 
  
Q6. Write a sequence of instructions that use the Str_compare procedure to determine the larger
of two input strings and write it to the console window.
  ()
A. 
  
Q7. Show how to call the Str_trim procedure and remove all trailing "@" characters from a string.
  ()
A. 
  
Q8. Show how to modify the Str_ucase procedure from the Irvine32 library so it changes all characters to lower case.
  ()
A. 
  
Q9. Create a 64-bit version of the Str_trim procedure. 
  ()
A.
  
Q10. Show an example of a base-index operand in 64-bit mode.
  ()
A. 
  
Q11. Assuming that EBX contains a row index into a two-dimensional array of 32-bit integers
named myArray and EDI contains the index of a column, write a single statement that
moves the content of the given array element into the EAX register.
  [해석]

A.
  
Q12. Assuming that RBX contains a row index into a two-dimensional array of 64-bit integers
named myArray and RDI contains the index of a column, write a single statement that
moves the content of the given array element into the RAX register
  [해석]

A. 


</pre>
