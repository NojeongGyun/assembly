<pre>
<b>1. In 32-bit mode, aside from the stack pointer (ESP), what other register points to variables on the stack? </b>
  (32비트 모드에서, 스택 포인터(ESP) 이외에 스택에 있는 변수들을 가리키는 다른 레지스터는 무엇인가?)
A. EBP 
  
  
<b>2. Name at least four CPU status flags. </b>
  (최소 네 개 이상의 CPU 상태 플래그를 말하시오.)
A. ZF, SF, CF, OF 
  
  
<b>3. Which flag is set when the result of an unsigned arithmetic operation is too large to fit into the destination?</b>
  (부호 없는(Unsigned) 산술 연산 결과가 목적지 레지스터에 담기에는 너무 클 때 설정되는 플래그는 무엇인가?)
A. CF
  
  
<b>4. Which flag is set when the result of a signed arithmetic operation is either too large or too small to fit into the destination? </b>
  (부호 있는(signed) 산술 연산 결과가 너무 커서 또는 너무 작아서 목적지 레지스터에 담기지 못할 때 설정되는 플래그는 무엇인가?)
A. OF
  

<b>5. (True/False): When a register operand size is 32 bits and the REX prefix is used, the R8D register is available for programs to use.</b>
  (<mark>[참/거짓]</mark> 레지스터 연산 피연산자 크기가 32비트이고 **REX 접두사(REX prefix)**가 사용될 때, 프로그램에서 R8D 레지스터를 사용할 수 있다.)
A. 참
  

<b>6. Which flag is set when an arithmetic or logical operation generates a negative result?</b>
  (산술 연산이나 논리 연산의 결과가 음수일 때 설정되는 플래그는 무엇인가?)
A. SF
  
  
<b>7. Which part of the CPU performs floating-point arithmetic?</b>
  (CPU의 어느 부분이 부동소수점(floating-point) 연산을 수행하는가?)
A. FPU
  
  
<b>8. On a 32-bit processor, how many bits are contained in each floating-point data register?</b>
  (32비트 프로세서에서 각 부동소수점(Floating-point) 데이터 레지스터는 몇 비트를 포함하는가?)
A. 80bit

  
<b>9. (True/False): The x86-64 instruction set is backward-compatible with the x86 instruction set.</b>
  (<mark>[참/거짓]</mark> x86-64 명령어 집합은 x86 명령어 집합과 하위 호환(backward-compatible)이 된다.)
A. 참

  
<b>10. (True/False): In current 64-bit chip implementations, all 64 bits are used for addressing.</b>
  (<mark>[참/거짓]</mark> 현재 64비트 칩 구현에서, 모든 64비트가 메모리 주소 지정(addressing)에 사용된다.)
A. 거짓 - 48비트 또는 52비트만 실제 주소 지정에 사용함

  
<b>11. (True/False): The Itanium instruction set is completely different from the x86 instruction set.</b>
  ([참/거짓] Itanium 명령어 집합은 x86 명령어 집합과 완전히 다르다.)
A. 참
  
  
<b>12. (True/False): Static RAM is usually less expensive than dynamic RAM.</b>
  (<mark>[참/거짓]</mark> 정적 RAM(Static RAM, SRAM)은 일반적으로 동적 RAM(DRAM)보다 저렴하다.)
A. 거짓 - SRAM은 빠르고 전력 소모가 적고, 구조가 복잡해 비싸지면 DRAM은 그 반대입니다. 
  
  
<b>13. (True/False): The 64-bit RDI register is available when the REX prefix is used.</b>
  (<mark>[참/거짓]</mark> REX 접두사가 사용될 때 64비트 RDI 레지스터를 사용할 수 있다.)
A. 거짓 - REX 접두사는 32비트 범용레지스터를 64비트로 확장할 떄 사용되는데, RDI는 기본적으로 64비트 레지스터가 사용가능합니다.


<b>14. (True/False): In native 64-bit mode, you can use 16-bit real mode, but not the virtual-8086 mode.</b>
  (<mark>[참/거짓]</mark> 네이티브 64비트 모드에서는 16비트 실모드(real mode)는 사용할 수 있지만, 가상 8086 모드(virtual-8086 mode)는 사용할 수 없다.)
A. 참
  
  
<b>15. (True/False): The x86-64 processors have 4 more general-purpose registers than the x86 processors.</b>
  (<mark>[참/거짓]</mark> x86-64 프로세서는 x86 프로세서보다 일반 목적 레지스터를 4개 더 가지고 있다.)
A. 거짓 - x86 프로세서는 [EAX, EBX, ECX, EDX, ESI, EDI, EBP, ESP] 총 8개를 가지고 있고, x86-64프로세서는 x64프로세스의 레지스터를 포함하고 R8 ~ R15 까지 추가가 되어 
  x86-64는 x86보다 8개를 더 가지고 있습니다.
  
  
<b>16. (True/False): The 64-bit version of Microsoft Windows does not support virtual-8086 mode.</b>
  (<mark>[참/거짓]</mark> 64비트 버전의 Microsoft Windows는 가상 8086 모드(virtual-8086 mode)를 지원하지 않는다.)
A. 참


<b>17. (True/False): DRAM can only be erased using ultraviolet light.</b>
  (<mark>[참/거짓]</mark> DRAM은 자외선(UV)으로만 지울 수 있다.)
A. DRAM은 휘발성으로 전원공급만 끊어도 데이터를 지울수 있습니다.
  
  
<b>18. (True/False): In 64-bit mode, you can use up to eight floating-point registers.</b>
  (<mark>[참/거짓]</mark> 64비트 모드에서는 최대 8개의 부동소수점(Floating-point) 레지스터를 사용할 수 있다.)
A. 참

  
<b>19. (True/False): A bus is a plastic cable that is attached to the motherboard at both ends, but does not sit directly on the motherboard.</b>
  (<mark>[참/거짓]</mark> 버스(Bus)는 양쪽 끝이 메인보드에 연결되어 있지만, 메인보드 위에 직접 놓이지 않는 플라스틱 케이블이다.)
A. 거짓 - 버스는 CPU, 메모리, I/O 장치 간 데이터를 전달하는 신호 통로를 의미합니다.
  
  
<b>20. (True/False): CMOS RAM is the same as static RAM, meaning that it holds its value without any extra power or refresh cycles.</b>
  (<mark>[참/거짓}</mark> CMOS RAM은 정적 RAM(SRAM)과 같아서, 추가 전력 공급이나 리프레시(refresh) 없이 값을 유지한다.)
A. 거짓 - CMOS RAM은 휘발성이므로 전력 공급 없이는 데이터 저장을 할 수 없다.

  
<b>21. (True/False): PCI connectors are used for graphics cards and sound cards.</b>
  (<mark>[참/거짓}</mark> PCI 커넥터는 그래픽 카드와 사운드 카드에 사용된다.)
A. 참

  
<b>22. (True/False): The 8259A is a controller that handles external interrupts from hardware devices.</b>
  (<mark>[참/거짓}</mark> 8259A는 하드웨어 장치로부터 오는 외부 인터럽트를 처리하는 컨트롤러이다.)
A. 참
  
  
<b>23. (True/False): The acronym PCI stands for programmable component interface. </b>
  (<mark>[참/거짓}</mark> PCI라는 약어는 "Programmable Component Interface"를 의미한다.)
A. 거짓 - Peripheral Component Interconnect
  
  
<b>24. (True/False): VRAM stands for virtual random access memory.</b>
  (<mark>[참/거짓}</mark> VRAM은 "Virtual Random Access Memory(가상 임의 접근 메모리)"를 의미한다.)
A. 거짓 - Virtual Random Access Memory가 아닌 Video Random Access Memory 입니다.
  
  
<b>25. At which level(s) can an assembly language program manipulate input/output?</b>
  (어셈블리어 프로그램은 어느 수준(level)에서 입출력(I/O)을 조작할 수 있는가?)
A. 하드웨어 수준에서 CPU의 IN/OUT 명령어로 직접 포트 입출력 할 수 있고, 운영체제 수준에서 인터럽트나 시스템 콜을 통해 I/O 수행 할 수 있습니다.
  
  
<b>26. Why do game programs often send their sound output directly to the sound card’s hardware ports?</b>
  (게임 프로그램이 소리 출력을 종종 사운드 카드의 하드웨어 포트로 직접 보내는 이유는 무엇인가?)
A. 하드웨어 자원을 관리하는 운영체제가 하드웨어에 접근하려면 지연이 걸리기에 하드웨어에 포트로 보내 지연시간을 줄이고, 속도를 높일 수 있기 떄문입니다. 
  

</pre>
