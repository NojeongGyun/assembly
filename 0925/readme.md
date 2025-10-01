<pre>
- <mark>Entry point</mark> -
엔트리 포인트란 가장 처음으로 실행이 시작되는 지점으로 java에는 public static void main(String[] args)가 엔트리 포인트, c는  main()가 엔트리 포인트인데
어셈블리는 마지막 End 엔트리포인트의 변수가 있으면, 엔트리포인트 변수가 엔트리포인트가 된다.
ex) <code>
    .data
    val DWORD 5
  
    .code
    main PROC
    mov eax, val
    main ENDP
  
    test PROC
    mov eax, 10
    test ENDP
  
    <mark>END main</mark>
    </code>
- 마지막에 END main이라는 main 엔트리포인트의 변수가 있으므로  main PROC가 엔트리 포인트이다.

      
- <mark>Segment</mark>
세그먼트는 프로그램을 담는 메모리의 구역입니다. 종류는 크게 5가지로, 3장에서 나오는 세그먼트 3가지만 설명 드리겠습니다.

<b>데이터 세그먼트</b> -
데이터 세그먼트는 변수, 상수, 배열 등을 지정할 떄 사용되는 세그먼트입니다. 
사용할 떄 .data를 사용하여 그 안에 변수이름 - 저장공간 크기 - 변수에 넣을 값   이런식으로 사용됩니다.
ex) <code>
    .data
    val1 DWORD 5 
    </code>
- 변수 이름: val1, 공간: 4바이트(DWORD), 값: 5 입니다. 

<b>코드 세그먼트</b> -
코드 세그먼트는 CPU가 직접 읽고 실행하는 공간으로 .data에 있는 변수들을 여기로 끌고와 레지스터와 함께 사용됩니다.
사용 할떄는 어셈블리 명령어를 필두로 보통은 나머지 2개의 값, 변수, 레지스터가 오고, 오른쪽에서 왼쪽으로 어셈블리 명령어에 따라 값이 오른쪽에서 왼쪽으로 행동 됩니다.
어셈블리 명령어는 mov(값 복사), add(덧셈), sub(뺄셈),jmp(분기 점프),call(함수 호출), ret(함수 반환), neg(부호 반전)가 있고, 나머지가 모두 피연산자인 Operand입니다.
보통 사용될때 Two-Operand방식으로 사용되는데, one-Operand, Three-Operand도 가끔 사용됩니다.
ex) <code>
    .code
    mov eax, val1 /* eax레지스터에 val1변수의 값을 이동(move)시킴) */
    add eax, 6 /* eax레지스터에 있는 값과 6을 더함(add) */
    </code>
- 예시에서 보셨듯, 어셈블리 명령어를 먼저 사용한 후 나머지 값(Operand)들이 오게 되고 Operand가 2개이므로 mov.... add.... 은 Two-Operand입니다. 

<b>스택 세그먼트</b> -
스택 세그먼트는 함수 호출, 지역 변수, 임시 저장용으로 사용하는 메모리 영역으로 갑을 스택에서 꺼내거나(pop) 스택에 저장(push)을 할 수 있습니다.
ex) <code>
    .stack 100h  /* 스택 크기 256바이트 지정 */
    
    .code
    main PROC
    push eax         /* eax 값을 스택에 저장 */
    mov eax, 5
    pop eax          /* 스택에서 값 꺼내 eax에 저장 */
    ret
    main ENDP
    <code>


- <mark>Litterals</mark> -

<b>Integer Litterals</b> -   
정수 뒤에 어떤 문자를 붙이냐에 따라 진법이 바뀝니다.

<b>10진수</b> -
숫자 뒤에 아무것도 붙이지 않거나, d를 붙이면 10진수
ex) 26, 26d
      
<b>2진수</b> -
숫자 뒤에 b를 붙이면 binary
ex) 1000101b

<b>8진수</b> -
숫자 뒤에 q나 o를 붙이면 8진수
ex) 42q, 53o

<b>16진수</b> -
숫자 뒤에 h를 붙이면 16진수
ex) 1Ah, 123Bh


- <mark>연산자 우선순위</mark> -
연산자는 각 레벨을 받는데 레벨이 낮을 수록 더 늦게 연산됩니다.
() - 1Lv
+, -(부호) - 2Lv
* , /  - 3LV
MOD    - 4LV
+, -(더하기, 뺴기) - 5LV 

<b>Character Litterals</b> -
캐릭터 리터럴은 문자 1개를 의미하며, 아스키 코드를 이용하여 숫자를 캐릭터 리터럴로 변환도 가능합니다.

<b>String Litterals</b>
스트링 리터럴은 문자 1개 이상을 의미하며, 쓸때는 ' '로 뭍거나 " "로 문자열을 묶어서 만듭니다. Character랑 다른점은 마지막에 String의 끝값이 어디인지 알려주는 Null값이 포함되어있다는 점입니다.
문자열을 만들 떄 주의 사항은 첫 글자는 _(언더바)나 문자(A~Z, a~z)이여야 되고, 문자열에 특수문자를 쓰면 안된다는 점이 있습니다.

        
- <mark>라벨</mark> -
라벨은 참조를 쉽게 할수 있게 이름을 붙이는 것을 의미합니다. 라벨에는 데이터 라벨, 코드 라벨이 있습니다. 

<b>데이터 라벨</b> -
데이터 라벨은 .data 세그먼트 안에서 변수나 상수의 이름을 붙이는 것입니다.
ex) <code>
    .data
    val1 DWORD 5 
    </code>
- 예시의 데이터 라벨은 val1인 변수입니다.

<b>코드 라벨</b> -
코드 라벨은 .code 세그먼트 안에서 명령어 위치에 붙이는 이름으로 점프(jmp)나 함수(call)할 때 위치 참조용으로 쓰입니다.
ex) <code>
    .code
    main PROC
    start:
    mov eax, val1
    add eax, val2
    jmp end_label

    end_label:
    mov sum, eax
    ret
    main ENDP
    </code>
- 예시에서 start와, end_label이 코드 라벨이고, start안에 jmp 분기가 있어 start라벨에서 end_label라벨로 넘어 갑니다.


- <mark>주석</mark> -
주석이란 프로그램 코드 안에 작성하는 설명용 문장으로 코드를 읽는 사람에게 의미 전달하거나 나중에 유지보수나 수정할 때 도움줍니다.
어셈블러 주석에는 ;(세미클론)을 이용한 한줄 주석이 있고, COMMENT 지시어를 이용한 블럭 주석이 있습니다.

<b>한줄 주석</b> -
코드 단 한줄에 주석을 다는 방식으로 작성한 코드 옆에 ;을 붙이고 멘트를 적으면 됩니다.
ex)
        mov eax, 5    ; eax에 5를 저장
- "eax에 5를 저장" 이 바로 주석입니다.

<b>블럭 주석</b> -
블럭 주석은 원하는 만큼을 지정하여 주석을 다는 형식입니다. COMMENT! 나 COMMENT &를 먼저 쓰고, 주석을 끝내고 싶을 때 !, &를 사용하면 됩니다.
ex)
COMMENT! 안녕하십니까
            hi
        !

COMMENT &
        오늘 날씨가
        매우 좋네요
        ㅎㅎ
        &

- <mark>NOP</mark> -
NOP는 No Operation으로 1바이트만 차지하고, 아무일도 일어나지 않는 명령어입니다. CPU는 메모리 접근 단위가 정해져 있어서, 4바이트로 맞추면 속도가 빨라져 보통은 4바이트 정렬 떄문에 사용합니다.
ex) <code>
    mov eax, 5      /* 2바이트 명령어라고 가정 */
    nop             /* 1바이트 추가 -> 총 2바이트 */
    nop             /* 1바이트 추가 -> 총 3바이트 */  
    add eax, 2      /* 다음 명령어 4바이트 경계에 위치 */
    </code>
- 예시처럼 nop는 아무일도 하지 않는 명령어인데, 4바이트를 맞추기 위해서 명령어를 사용해 바이트를 차치합니다.

        
</pre>



레이블 - 데이터레이블, 코드 레이블(.file에 사용함)


오퍼랜드 명령의 대상이 되는것(p13)
오퍼랜드가 1,2,3개가 될수도 있음(p13)
계산하면 데스네이션으로 들어감

Description은 사람한테 감(p16)
block comment

The nop(4바이트를 맞춰야 하기에 그 미만이 되면 부족한 만큼 아무의미 없는 내용을 추가함) p17













$사인 0,1,2 위에서 아래로 순서를 지정(p43)
