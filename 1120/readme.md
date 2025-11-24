<pre>
- <mark>Stack Frame</mark> -
Stack Frame이란 프로그램에서 함수(서브루틴)가 호출될 때마다 스택에 자동으로 만들어지는 독립적인 작업 공간입니다.
프로시저가 호출되면 스택 프레임이 만들어지고, 매개변수가 있으면 변수를 담은 인수가 저장디는 곳은 스택 프레임입니다.  

- <mark> call by</mark> -
<b>Call by value</b> -
스택에 값을 올려두고, 값을 호출함
  
<b>Call by reference</b> -
스택에 값에 대한 주소를 할당받아, 주소를 호출하여 값을 받음

[EBP + 8] ← 첫 번째 인자 [EBP + 4] ← return address [EBP + 0] ← old EBP [EBP - 4] ← 첫 번째 지역 변수 [EBP - 8] ← 두 번째 지역 변수

  
p9
push를 하면 pop을 무조권 해야합니다. 오류가 발생함

p11
ret 8을 하는이유?

p

ebp는 [ebp+8]부터는 현재 함수가 받은 인자들(parameter)이 저장되는 것”이다.
-4부터는 지역변수 영역
  
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
