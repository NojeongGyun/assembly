<pre>
- <mark>Stack Frame</mark> -
Stack Frame이란 프로그램에서 함수(서브루틴)가 호출될 때마다 스택에 자동으로 만들어지는 독립적인 작업 공간입니다.
프로시저가 호출되면 스택 프레임이 만들어지고, 매개변수가 있으면 변수를 담은 인수가 저장디는 곳은 스택 프레임입니다.  

- <mark> call by</mark> -
<b>Call by value</b> -
스택에 값을 올려두고, 값을 호출함
  
<b>Call by reference</b> -
스택에 값에 대한 주소를 할당받아, 주소를 호출하여 값을 받음

- <mark>EBP</mark> -
EBP는 현재 스택 프레임의 기준점 역할을 합니다. ESP는 push와 pop을 하면 위치가 변하지만 EBP는 변하지 않아 매개변수·지역변수를 쉽게 접근할 수 있게 해줍니다.
..
[EBP + 12] ← 두 번쨰 인자
[EBP + 8] ← 첫 번째 인자 
[EBP + 4] ← return address 
[EBP + 0] ← old EBP 
[EBP - 4] ← 첫 번째 지역 변수 
[EBP - 8] ← 두 번째 지역 변수
..
- + 0바이트와 + 4바이트는 고정이고, +8, +12, +16...은 인자를 나타내고, -4, -8,-12...은 지역변수를 나타냅니다.
만약 지역변수를 스택에서 제거하려면 ESP를 EBP 값으로 되돌리면 됩니다.
  
- <mark>STDCALL</mark> -
STDCALL은 함수 호출 규약 중 하나로, 함수가 return할 때 인수를 정리합니다. 즉 호출한 쪽이 아니라, 함수가 스택에서 인자를 제거합니다.
ex) ret 12 //ret 12는 반환과 동시에 12바이트만큼 스택을 정리(pop)하는 명령입니다. 스택은 push 할 때 ESP가 내려가고, pop 할 때 ESP가 올라갑니다.
             따라서 ret 12는 ESP를 12바이트 증가시켜, 4바이트 인자 3개를 한꺼번에 제거하는 것과 같다.
- <mark>명령어 및 지시어 그리고 관련 연산자</mark> -
<b>LEA</b> -
LEA명령어는 간접 피연산자의 주소를 반환하는 명령어 입니다.
ex) mov eax, [ebx]   ; ebx가 가리키는 주소의 값을 eax에 저장함
    lea eax, [ebx]   ; ebx가 가리키는 주소를 eax에 저장함

<b>ENTER</b> -
ENTER 명령어는 호출된 프로시저를 위해 자동으로 스택 프레임을 생성한다. 이 명령어는 지역 변수를 위한 스택 공간을 확보하고, EBP를 스택에 저장할 떄 사용됩니다.
ENTER 명령어 사용방법은 첫 번째 오퍼랜드는 지역 변수를 위해 확보할 스택 공간의 바이트 수를 지정하는 상수이고, 두 번째 오퍼랜드는 해당 프로시저의 중첩 수준을 지정합니다.
ex) ENTER 12, 1 // 지역 변수 공간 12바이트 확보, 상위 EBP 1개 더 저장

<b>LEAVE</b> -
LEAVE 명령어는 프로시저의 스택 프레임을 종료합니다. LEAVE는 이전 ENTER 명령어의 동작을 되돌려서, 프로시저가 호출될 때의 값으로 ESP와 EBP를 복원합니다.
LEAVE 명령어는 사실상 1. mov esp, ebp  2.pop ebp  두개의 명령을 합쳐 놓은 것입니다.

<b>LOCAL</b> -
LOCAL지시어는 하나 이상의 지역 변수를 이름을 붙여서 선언하고, 각 변수에 크기 속성을 지정합니다.
ex) LOCAL var1:DWORD, var2:BYTE // var1은 DWORD크기로, var2는 BYTE크기로 변수 지정

<b>INVOKE</b> -
INVOKE 지시어는 MODEL 지시어의 언어 규칙에 따라 인수들을 스택에 push하고, 그 후 해당 프로시저를 호출합니다. 
INVOKE는 여러 개의 인수를 한 줄에 전달할 수 있기 때문에 CALL 명령어를 편리하게 대체합니다.
ex) - Call -
    push param3
    push param2
    push param1
    call Func

    - invoke(1) -
  INVOKE Func, param1, param2, param3

    - invoke(2) -
  INVOKE Func,
         param1,
         param2,
         param3

- invoke 명령어는 invoke(2)처럼 각 인수를 소스 코드에서 여러줄에 나누어 작성 할 수도 있습니다.

<b>ADDR</b> -
ADDR 연산자는 INVOKE로 프로시저를 호출할 때 포인터 인자를 전달하는 데 사용될 수 있습니다.
ex) INVOKE FillArray, ADDR myArray, LENGTHOF myArray // myArray의 주소를 인자로 넘김

<b>PROC</b> -
PROC 지시어는 쉼표로 구분된 이름 있는 매개변수 목록을 사용하여 프로시저(서브루틴)를 선언할 수 있게 해준다.
PROC 지시어를 사용하면, 이름을 가진 매개변수들을 콤마로 구분하여 선언하는 형태로 프로시저를 정의할 수 있습니다.
ex) MyProc PROC param1:DWORD, param2:BYTE // param1은 [ebp+8], param2는 [ebp+12]와 같은 위치에 존재하게 해줌
    ...
    ...
    MyProc ENDP


- <mark>재귀 서브루틴</mark> -
재귀 서브 루틴은 직접 또는 간접적으로 자기 자신을 호출하는 서브루틴을 말합니다. 만약 종료 조건이 없다면 무한 반복하여 해당 내용을 실행하기에 종료조건을 넣어야합니다.
재귀 서브 루틴은 임시 데이터를 스택 매개변수에 저장하는 경우가 있는데, 재귀 호출이 종료되어 차례로 되돌아갈 때, 스택에 저장된 데이터는 유용하게 사용될 수 있습니다.

- <mark>데이터 전달 방향</mark> -
데이터가 어디에서 어디로 전달되는지에 따라 입력 매개변수, 출력 매개변수, 입출력 매개변수 3가지로 나눌수 있습니다.

<b>입력 매개변수</b> -
1.호출자가 값을 전달 
2. 프로시저에서 읽기만 가능

<b>출력 매개변수</b> -
1. 프로시저가 값을 설정
2. 호출자에서 읽음

<b>입출력 매개변수</b> -
1. 호출자가 값을 전달 
2. 프로시저에서 읽고 수정 
3. 호출자에게 반영
  

p16 
예시잘보기
  
p17
  Enter을 하면 Leave를 함


p38깊이 안들어감
  
p49
subl@0 EXTERN subl@0:PROC 둘다 사용하면 없어도 에러가 나지 않고, subl만 사용하면 없으면 에러가 납니다.

p52
외부에서 허용할때는 public, 쓸때는 EXTERNDEF을 씀
















































  
</pre>
