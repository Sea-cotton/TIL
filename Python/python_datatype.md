> # 자료형

#### 

#### 자료형(Datatype) 분류

- 사용할 수 있는 데이터의 종류를 자료형이라고 함

- 수치형(Numeric Type)
  
  - int (정수, integer)
  
  - float (부동소수점, 실수, floating point number)
  
  - complex (복소수, complex number)

- 문자열(String Type)

- 불린형(Boolean Type)

- None

----

#### 수치형(Numeric Type)

- 정수 자료형(int)
  
  - 0, 100, -200 과 같은 정수를 표현하는 자료형
  
  - 일반적인 수학 연산(사칙 연산) 가능
  
  - 여러 진수 표현 가능
    
    - 2진수(binary) : 0b
    
    - 8진수(octal) : 0o
    
    - 16진수(hexademical) : 0x

- 실수 자료형(float)
  
  - 유리수와 무리수를 포함하는 '실수'를 다루는 자료형
  
  - 0.1, 100.0 , -0.0001 등
  
  - 실수 연산 시 주의할 점(부동 소수점)
    
    ```python
    print(3.2 - 3.1) # 0.1000000000009
    print(1.2 - 1.1) # 0.0999999999997
    
    # 연산의 결과가 0.1이 아니다!
    ```
    
    - 컴퓨터는 2진수, 사람은 10진법을 사용
    
    - 10진수 0.1을 2진수로 표현하면 0.0001100..같이 무한대로 반복-> 근사값만 표시
    
    - 이런 증상을 'Floating point rounding error' 라고 함
  
  - 부동 소수점-해결책
    
    - 값 비교 과정에서 정수가 아닌 실수면 주의!
    
    - 매우 작은 수보다 작은지 확인하거나 math 모듈 활용
      
      ```python
      # 1. 임의의 작은 수 활용
      print(abs(a - b) <= 1e-10) # True
      
      # 2. python 3.5 이상 - math 모듈 활용
      import math
      print(math.isclose(a, b)) # True
      ```

----

#### 문자열 자료형(String Type)

- 문자열 자료형의 정의
  
  - 모든 문자는 str 타입
  
  - 문자열은 작은따옴표(') 나 큰따옴표(") 활용하여 표기
  
  - 따옴표 안에 따옴표를 표현할 경우
    
    - 작은따옴표가 들어 있는 경우는 큰따옴표로 문자열 생성
    
    - 큰따옴표가 들어있는 경우는 작은따옴표로 문자열 생성
  
  - 삼중 따옴표(Triple Quotes)
    
    - 작은 따옴표나 큰따옴표를 삼중으로 사용
    
    - 따옴표 안에 따옴표를 넣을 때,
    
    - 여러 줄을 나눠 입력할 때 편리
      
      ```python
      print('''문자열 안에 '작은따옴표'나
      "큰따옴표"를 사용할 수 있고
      여러 줄을 사용할 때도 편리하다.''')
      
      # 출력 결과
      문자열 안에 '작은따옴표'나
      "큰따옴표"를 사용할 수 있고
      여러 줄을 사용할 때도 편리하다.
      ```

- 문자열 연산
  
  - 덧셈
    
    - 문자열 덧셈은 문자열을 **연결**
      
      ```python
      print("Hello" + "World") # HelloWorld
      ```
  
  - 곱셈
    
    ```python
    print("Python" * 3) # PythonPythonPython
    ```

- String Interpolation(문자열을 변수를 활용하여 만드는 법)
  
  - %-formatting : 옛날 방식
  
  - str.format() : 옛날 방식
  
  - f-strings : python 3.6+ 부터 지금까지 쓰임
    
    ```python
    name = 'Kim'
    score = 4.5
    
    print(f'Hello, {name}! 성적은 {score}')
    # Hello, Kim! 성적은 4.5
    
    import datetime
    today = datetime.datetime.now()
    print(today) # 2022-07-08 16:04:15.200411
    
    print(f'오늘은 {today:%y}년 {today:%m}월 {today:%d}일')
    # 오늘은 22년 07월 08일
    
    pi = 3.141592
    print(f'원주율은 {pi:.3}. 반지름이 2일 때 원의 넓이는 {pi*2*2}')
    # 원주율은 3.14. 반지름이 2일 때 원의 넓이는 12.566368
    ```

- Escape sequence
  
  - 역슬래시가 뒤에 특정 문자가 와서 특수한 기능을 하는 문자 조합
    
    | 예약 문자 | 내용(의미)          |
    | ----- | --------------- |
    | \n    | 줄 바꿈            |
    | \t    | 탭               |
    | \r    | 캐리지 리턴(커서를 앞으로) |
    | \0    | 널(Null)         |
    | \\\   | \               |
    | \’    | 단일인용부호(’)       |
    | \”    | 이중인용부호(”)       |

---

#### None

- 파이썬 자료형 중 하나

- 값이 없음을 표현

- 일반적으로 반환 값이 없는 함수에서 사용하기도 한다

----

#### 불린형(Boolean)

- 논리 자료형으로 참과 거짓을 표현하는 자료형

- True 또는 False를 값으로 가짐

- 비교 / 논리 연산에서 활용됨
  
  - 비교 연산자 활용 예시
    
    - 수학에서 등호, 부등호와 동일한 개념
    
    - 주로 조건문에 사용, 값을 비교할 때 사용
    
    - 결과는 True / False 값을 리턴
      
      ```python
      print(3 > 6) # False
      print(3.0 == 3) # True
      print('3' != 3) # True
      print('Hi' == 'hi') # False
      ```
  
  - 논리 연산자
    
    - 일반적으로 비교 연산자와 함께 사용
      
      | 연산자     | 내용                         |
      | ------- | -------------------------- |
      | A and B | A와 B 모두 True시, True        |
      | A or B  | A와 B 모두 False시, False      |
      | Not     | True를 False로, False를 True로 |
      
      ```python
      num = 100
      print(num >= 100 and num % 3 == 1) # True
      ```
  
  - 논리 연산자 주의할 점 / not 연산자
    
    - Falsy : False는 아니지만 False로 취급 되는 다양한 값
      
      - 0, 0.0, (), [], {}, None, ""(빈 문자열)
      
      - 0 = False, 1 = True
    
    - 논리 연산자도 우선 순위가 존재
      
      - not and or 순으로 우선 순위가 높음
        
        ```python
        print(not True) # False
        print(not 0) # True
        print(not 'hi') # False
        print(not True and False or not False) # True
        # 위와 같음
        print(((not true)and False) or (not False)) # True
        ```
  
  - 논리 연산자의 단축 평가
    
    - 결과가 확실한 경우 두번째 값은 확인않고 첫번째 값 반환
    
    - and 연산에서 첫번째 값이 False인 경우 무조건 False => 첫번째 값 반환
    
    - or 연산에서 첫번째 값이 True 인 경우 무조건 True => 첫번째 값 반환
    
    - 0은 False, 1은 True
      
      ```python
      print(3 and 5) # 5
      print(3 and 0) # 0
      print(0 and 3) # 0
      print(0 and 0) # 0
      
      print(5 or 3) # 5
      print(3 or 0) # 3
      print(0 or 3) # 3
      print(0 or 0) # 0
      
      a = 5 and 4
      print(a) # 4
      
      b = 5 or 3
      print(b) # 5
      
      c = 0 and 5
      print(c) # 0
      
      d = 5 or 0
      print(d) # 5
      ```
