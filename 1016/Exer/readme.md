<pre>
<b> Q.4.9.1(1) What will be the value in EDX after each of the lines marked (a) and (b) execute? </b>
  (각 (a)와 (b)로 표시된 줄이 실행된 후 EDX 레지스터에 저장될 값은 무엇입니까?)
              .data
              one WORD 8002h
              two WORD 4321h
              .code
              mov edx,21348041h
              movsx edx,one ; (a)
              movsx edx,two ; (b) 

A. (a)의 EDX = 11118002h  (b)의 EDX = 00004321h   1로 채운 이유는 one은 MSB가 1이라 음수이기에 1로 채웠고, two는 MSB가 0이라 양수이기에 0으로 채웠습니다. 
