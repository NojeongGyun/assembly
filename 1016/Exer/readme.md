<pre>
<b> Q.4.9.1(1) What will be the value in EDX after each of the lines marked (a) and (b) execute?
              .data
              one WORD 8002h
              two WORD 4321h
              .code
              mov edx,21348041h
              movsx edx,one ; (a)
              movsx edx,two ; (b) 
</b>
A. 
