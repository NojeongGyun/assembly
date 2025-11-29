<pre>
<mark>9.9.1</mark> 
Q1. Which Direction flag setting causes index registers to move backward through memory 
  when executing string primitives?
  (어떤 방향 플래그 설정이 문자열 처리 명령어 실행 시 인덱스 레지스터가 메모리에서 뒤로 이동하게 만드나요?)
A. DF = 1

2. When a repeat prefix is used with STOSW, what value is added to or subtracted from the
index register?
3. In what way is the CMPS instruction ambiguous?
4. When the Direction flag is clear and SCASB has found a matching character, where does
EDI point?
5. When scanning an array for the first occurrence of a particular character, which repeat prefix would be best?
6. What Direction flag setting is used in the Str_trim procedure from Section 9.3?
7. Why does the Str_trim procedure from Section 9.3 use the JNE instruction?
8. What happens in the Str_ucase procedure from Section 9.3 if the target string contains a
digit?
9. If the Str_length procedure from Section 9.3 used SCASB, which repeat prefix would be
most appropriate?
10. If the Str_length procedure from Section 9.3 used SCASB, how would it calculate and
return the string length?
11. What is the maximum number of comparisons needed by the binary search algorithm when
an array contains 1,024 elements?
12. In the FillArray procedure from the Binary Search example in Section 9.5, why must the
Direction flag be cleared by the CLD instruction?
13. In the BinarySearch procedure from Section 9.5, why could the statement at label L2 be
removed without affecting the outcome?
14. In the BinarySearch procedure from Section 9.5, how might the statement at label L4 be
eliminated?

<mark>9.9.2</mark>
1. Show an example of a base-index operand in 32-bit mode.
2. Show an example of a base-index-displacement operand in 32-bit mode.
3. Suppose a two-dimensional array of doublewords has three logical rows and four logical
columns. Write an expression using ESI and EDI that addresses the third column in the second row. (Numbering for rows and columns starts at zero.)
4. Write instructions using CMPSW that compare two arrays of 16-bit values named sourcew
and targetw.
5. Write instructions that use SCASW to scan for the 16-bit value 0100h in an array named
wordArray, and copy the offset of the matching member into the EAX register.
6. Write a sequence of instructions that use the Str_compare procedure to determine the larger
of two input strings and write it to the console window.
7. Show how to call the Str_trim procedure and remove all trailing "@" characters from a
string.
8. Show how to modify the Str_ucase procedure from the Irvine32 library so it changes all
characters to lower case.
9. Create a 64-bit version of the Str_trim procedure.
10. Show an example of a base-index operand in 64-bit mode.
11. Assuming that EBX contains a row index into a two-dimensional array of 32-bit integers
named myArray and EDI contains the index of a column, write a single statement that
moves the content of the given array element into the EAX register.
12. Assuming that RBX contains a row index into a two-dimensional array of 64-bit integers
named myArray and RDI contains the index of a column, write a single statement that
moves the content of the given array element into the RAX register






















  
</pre>
