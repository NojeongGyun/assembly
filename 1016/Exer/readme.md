<pre>
<b> Q.4.9.1(1). What will be the value in EDX after each of the lines marked (a) and (b) execute? </b>
  (각 (a)와 (b)로 표시된 줄이 실행된 후 EDX 레지스터에 저장될 값은 무엇입니까?)
              .data
              one WORD 8002h
              two WORD 4321h
              .code
              mov edx,21348041h
              movsx edx,one ; (a)
              movsx edx,two ; (b) 

A. (a)의 EDX = 11118002h  (b)의 EDX = 00004321h   1로 채운 이유는 one은 MSB가 1이라 음수이기에 1로 채웠고, two는 MSB가 0이라 양수이기에 0으로 채웠습니다.

<b>Q.4.9.1(2). What will be the value in EAX after the following lines execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,1002FFFFh
              inc ax
A. 10020000h 

<b> Q.4.9.1(3). What will be the value in EAX after the following lines execute? </b>
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,30020000h
              dec ax
A. 3002FFFFh

<b>Q.4.9.1(4). What will be the value in EAX after the following lines execute? </b>
  (다음 명령들이 실행된 후 EAX 레지스터에 저장될 값은 무엇입니까?)
              mov eax,1002FFFFh
              neg ax
A. 10020001h

<b>Q.4.9.1(5). What will be the value of the Parity flag after the following lines execute? </b>
  (다음 명령들이 실행된 후 **Parity 플래그(PF)**의 값은 무엇입니까?)
              mov al,1
              add al,3
A.  0001 + 0011 == 0100 입니다. PF는 비트 1의 개수가 짝수면 1이고, 홀수면 0입니다. 그러므로 PF = 0입니다.

<b>Q.4.9.1(6). What will be the value of EAX and the Sign flag after the following lines execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터의 값과 **Sign Flag(SF)**의 값은 무엇입니까?)
              mov eax,5
              sub eax,6
A. 00000005h - 00000006h == FFFFFFFFh  음수인지 아닌지는 MSB에서 1이면 음수입니다. 음수이면 SF가 1이 되고 아니면 0입니다. 그렇기에 SF = 1 입니다.

<b>Q.4.9.1(7). In the following code, the value in AL is intended to be a signed byte. Explain how the Overflow flag helps, or does not help you, 
to determine whether the final value in AL falls within a valid signed range.</b>
  (다음 코드에서 AL 레지스터의 값은 부호 있는(Byte) 값으로 간주됩니다. Overflow Flag(OF)가 
  최종 AL 값이 유효한 부호 있는 범위(-128 ~ 127) 내에 있는지를 판단하는 데 도움이 되는지, 그렇지 않은지를 설명하세요.)
            mov al,-1
            add al,130
A. al은 1바이트 크기이므로 범위는 -128~127로 제한됩니다. al에 -1 + 130의 계산 결과인 범위 밖인 129가 들어와 overflow가 일어나게 됩니다. 이 떄문에 OF = 1 
로 변하고, OF가 1이라는 정보로 범위밖이라는 정보를 얻을 수 있습니다.



<b>Q.4.9.1(8). What value will RAX contain after the following instruction executes?</b>
  (다음 명령이 실행된 후 RAX 레지스터에는 어떤 값이 저장됩니까?)
            mov rax,44445555h
A. rax는 8바이트로 이루어진 레지스터입니다. 0확장을 하면 0000000044445555h 입니다.

<b>Q.4.9.1(9). What value will RAX contain after the following instructions execute?</b>
  (다음 명령들이 실행된 후 RAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            dwordVal DWORD 84326732h
            .code
            mov rax,0FFFFFFFF00000000h
            mov rax,dwordVal
A. 0000000084326732h

<b>Q.4.9.1(10). What value will EAX contain after the following instructions execute?</b>
  (다음 명령들이 실행된 후 EAX 레지스터에는 어떤 값이 저장됩니까?)
            .data
            dVal DWORD 12345678h
            .code
            mov ax,3
            mov WORD PTR dVal+2,ax
            mov eax,dVal
A. 00035678h 입니다. 이유는 word단위로 쪼개면 daval은 0바이트~1바이트 5678h, 2바이트~3바이트 1234h입니다.
ax레지스터는 2바이트의 크기를 차지합니다. daval의 주소에 2바이트 떨어진 곳에 ax 값인 0003h를 넣는 것이기에 00035678h 입니다.


 

