<pre>
1. <b>Provide examples of three different instruction mnemonics.</b>
  (세 가지 다른 명령어 니모닉(Mnemonic)의 예시를 제시하시오.)
A. MOV, ADD, JMP

2. <b></b>What is a calling convention, and how is it used in assembly language declarations?</b>
  (호출 규약(calling convention)이란 무엇이며, 어셈블리 언어 선언에서 어떻게 사용되는가?)
A. 함수가 다른 함수를 호출할 때, 매개변수 전달, 반환값 처리, 스택 관리 방법을 정의한 규칙이고, 어셈블리 언어에서 함수를 선언하거나 정의할 때 사용됩니다.
  
3.<b>How do you reserve space for the stack in a program?</b>
  (프로그램에서 스택을 위한 공간은 어떻게 예약(할당)하는가?)
A. 스택 포인터를 조정하거나 지역 변수를 선언하여 예약니다.

4. <b> Explain why the term assembler language is not quite correct.</b>  
  (왜 “assembler language(어셈블러 언어)”라는 용어가 정확하지 않은지 설명하시오.)
A. 어셈블러는 어셈블리언어를 기계어로 바꾸어 소통하는 도구이므로 어셈블러 언어는 맞지 않습니다.
  
5. <b>Explain the difference between big endian and little endian. Also, look up the origins of this term on the Web</b>  
  (빅 엔디안과 리틀 엔디안의 차이점을 설명하고, 이 용어의 유래를 웹에서 찾아보세요.)
A. 빅 엔디안은 가장 중요한 바이트(MSB)를 가장 낮은 메모리 주소에 저장하고, 반대로 리틀 엔디안은 가장 덜 중요한 바이트(LSB)를 가장 낮은 메모리 주소에 저장합니다.
  실제 용어 사용은 Cohen, 이름의 아이디어는 Swift의 소설에서 유래 되었습니다.

6. <b>Why might you use a symbolic constant rather than an integer literal in your code?</b>  
  (코드에서 정수 리터럴(integer literal) 대신 **기호 상수(symbolic constant)를 사용하는 이유는 무엇인가?)
A. 기호 상수는 코드 가독성, 유지보수, 오류 방지, 재사용성을 높이기 때문에 정수 리터럴보다 선호됩니다.

7. <b> How is a source file different from a listing file?</b> 
  (소스 파일(source file)과 리스트 파일(listing file)은 어떻게 다른가?)
A. 소스파일은 작성한 원래의 프로그램 코드를 담고 있는 파일이고, 리스트 파일은 어셈블러나 컴파일러가 소스 파일을 처리하면서 출력한 결과물입니다. 떄문에 디버깅과 분석용으로 사용됩니다.

8. <b>How are data labels and code labels different?</b>
  (데이터 레이블(data label)과 코드 레이블(code label)은 어떻게 다른가?)
A. 데이터 레이블은 메모리 내 데이터 위치를 나타내는 이름이고, 코드 레이블은 로그램 내 명령어 위치를 나타내는 이름입니다. 각각 데이터 저장 공간 참고할떄, 프로그램 흐름 제어할 떄 사용됩니다.
  
9. <b>(True/False): An identifier cannot begin with a numeric digit.</b>  
  (<mark>[참/거짓]</mark>식별자는 숫자(digit)로 시작할 수 없다)
A. 참(문자나 언더바(_)로만 시작 가능)
  
10. <b>(True/False): A hexadecimal literal may be written as 0x3A</b>
  (<mark>[참/거짓]</mark>16진수 리터럴은 0x3A처럼 쓸 수 있다.)
A. 참

11. <b>(True/False): Assembly language directives execute at runtime.</b>  
  (<mark>[참/거짓]</mark>어셈블리 언어 지시자(directives)는 런타임에 실행된다.)
A. .data, .text, DB, EQU 등의 지시자는 컴파일/어셈블 시 처리되고, 런타임에는 실행되지 않습니다.

12. <b>(True/False): Assembly language directives can be written in any combination of uppercase and lowercase letters.</b>
  (<mark>[참/거짓]</mark>어셈블리 언어 지시자는 대문자와 소문자를 혼합하여 작성할 수 있다.)
A. 참

13. <b>Name the four basic parts of an assembly language instruction</b>
  (어셈블리 언어 명령어의 네 가지 기본 구성 요소를 말하시오.)
A. 레이블, 연산자, 주석, 피연산자

14 <b>(True/False): MOV is an example of an instruction mnemonic.</b>
  (<mark>[참/거짓]</mark>MOV는 명령어 기호(instruction mnemonic)의 예이다.)
A. 참

15. <b>(True/False): A code label is followed by a colon (:), but a data label does not end with a colon.</b>
  (<mark>[참/거짓]</mark>코드 레이블은 콜론(:)으로 끝나지만, 데이터 레이블은 콜론으로 끝나지 않는다.)
A. 참(데이터 레이블은 아무것도 없이 끝남)
  
16. <b>Show an example of a block comment.</b>
  (블록 주석(block comment)의 예를 보여라.)
A. COMMENT !  블록 주석입니다 !

17. <b> Why is it not a good idea to use numeric addresses when writing instructions that access variables?</b>
  (변수를 접근하는 명령어를 작성할 때, 숫자 주소(numeric address)를 사용하는 것이 좋지 않은 이유는 무엇인가?)
A. 읽기 어렵고, 유지보수 힘들며, 오류 위험이 크고 이식성이 떨어지기 때문입니다. 그렇기에 데이터 레이블을 씁니다.

18. <b>What type of argument must be passed to the ExitProcess procedure?</b>
  (ExitProcess라는 함수(프로시저)에 전달해야 하는 인자는 어떤 타입인가?)
A. DWORD 타입입니다.

19. <b>Which directive ends a procedure?</b>  
  (어떤 지시어가 프로시저를 끝내는가?)
A. ENDP입니다.

20. <b>In 32-bit mode, what is the purpose of the identifier in the END directive?</b>
  (32비트 모드에서, END 지시어에 있는 식별자의 목적은 무엇인가?)
A. 프로그램의 시작 지점(엔트리 포인트)을 지정하는 역할을 합니다.
  
21. <b>What is the purpose of the PROTO directive?</b>
  (PROTO 지시어의 목적은 무엇인가?)
A. 프로시저의 원형을 선언하여, 호출 시 매개변수와 호출 규칙을 어셈블러가 확인할 수 있도록 하는 역할을 합니다.
  
22. <b>(True/False): An Object file is produced by the Linker.</b>
  (<mark>[참/거짓]</mark>객체 파일(Object file)은 링커(Linker)에 의해 생성된다.)
A. 거짓(객체 파일은 어셈블러가 생성함)

23. <b>(True/False): A Listing file is produced by the Assembler</b>  
  (<mark>[참/거짓]</mark>리스트 파일(Listing file)은 어셈블러에 의해 생성된다.)
A. 참

24. <b>(True/False): A link library is added to a program just before producing an Executable file.</b>
  (<mark>[참/거짓]</mark>링크 라이브러리는 실행 파일을 생성하기 바로 전에 프로그램에 추가된다.)
A. 참

25. <b> Which data directive creates a 32-bit signed integer variable?</b>
  (어떤 데이터 지시어가 32비트 부호 있는 정수 변수를 생성하는가?)
A. DD

26. <b>Which data directive creates a 16-bit signed integer variable?</b>
  (어떤 데이터 지시어가 16비트 부호 있는 정수 변수를 생성하는가?)
A. DW

27. <b>Which data directive creates a 64-bit unsigned integer variable?</b>
  (어떤 데이터 지시어가 64비트 부호 없는 정수 변수를 생성하는가?)
A. DQ

28. <b>Which data directive creates an 8-bit signed integer variable?</b>
  (








  
</pre>
