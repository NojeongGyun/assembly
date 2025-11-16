<pre>
<mark>7.9.1</mark> -
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


















  

  
</pre>
