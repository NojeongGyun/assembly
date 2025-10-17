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
to determine whether the final value in AL falls within a valid signed range.
  (다음 코드에서 AL 레지스터의 값은 부호 있는(Byte) 값으로 간주됩니다. Overflow Flag(OF)가 
  최종 AL 값이 유효한 부호 있는 범위(-128 ~ 127) 내에 있는지를 판단하는 데 도움이 되는지, 그렇지 않은지를 설명하세요.)
            mov al,-1
            add al,130
A. 

