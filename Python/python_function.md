> # 함수

- 함수를 쓰는 이유?
  - 분해 : 기능을 분해하고 재사용 가능하게 만듬
  - 추상화

### 함수 기초

- 함수의 종류 (3가지)
  
  - 내장 함수
    
    - 파이썬에 기본적으로 포함된 함수
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1bb6d986-0de0-4e06-9f40-0b8fe54507a3/Untitled.png)
  
  - 외장 함수
    
    - import문을 통해 사용하며, 외부 라이브러리에서 제공하는 함수
  
  - 사용자 정의 함수
    
    - 직접 사용자가 만드는 함수

- 함수의 정의
  
  - 특정한 기능을 하는 코드의 조각

- 함수의 기본 구조
  
  ```python
  keyword func_name(parameters)
      """Docstring
      """
        function body
  ```
  
  - 선언과 호출(define & call) : 생성과 실행
  - 입력(Input)
  - 문서화(Docstring)
  - 범위(Scope)
  - 결과값(Output)

### 선언과 호출

- 함수의 선언은 def 키워드를 활용함

- 들여쓰기를 통해 Function body(실행될 코드 블록)을 작성함
  
  - Docstring은 함수 body앞에 선택적으로 작성 가능
    - 작성 시에는 반드시 첫 번째 문장에 문자열 “””

- 함수는 parameter를 넘겨줄 수 있음

- 함수는 동작 후에 return을 통해 결괏값을 전달함

- 함수를 사용하기 위해서는 먼저 함수를 정의해야 함
  
  ```python
  def function_name(parameter):
      # code block
      return returning_value
  ```

- 함수는 함수명() 으로 호출하여 사용
  
  - parameter가 있는 경우, 함수명(값1, 값2,..)로 호출
  
  ```python
  def foo():
      return True
  
  def add(x, y):
      return x + y
  ```

- 함수 실행 순서 예시
  
  ```python
  num1 = 0
  num2 = 1
  
  def func1(a, b):
      return a + b    # def 로 함수를 선언만 함(실행x)
  
  def func2(a, b):
      return a - b    # def 로 함수를 선언만 함(실행x)
  
  def fucn3(a, b)
      return func1(a, 5) + func2(5, b)    # def 로 함수를 선언만 함(실행x)
  
  result = func3(num1, num2) # 이 때 함수들을 사용한다
  print(result) # 9
  ```

### 함수의 결과값(Output)

- 값에 따른 함수의 종류
  
  - void function : 명시적인 return 값이 없는 경우, None을 반환하고 종료
    
    ```python
    # Void function
    print('hello python') #hello python
    ```

- Value returning function
  
  - 함수 실행 후, return문을 통해 값 반환
  
  - return을 하게 되면, 값 반환 후 함수가 바로 종료
    
    ```python
    #value returning function
    float('3.14') # 3.14
    ```

- 주의) print 함수와 return의 차이점
  
  - print를 사용하면 호출(사용)될 때 마다 값이 출력됨(주로 테스트를 위해 사용)
  - 데이터 처리를 위해서는 return 사용

- 두 개 이상의 값 반환
  
  - return은 항상 하나의 값 만을 반환
    
    ```python
    #문제 있는 코드
    
    def minus_and_product(x, y):
        return x - y
        return x * y
    
    y = minus_and_product(4, 5)
    print(y) # -1
    ```
  
  - 해결법 ) 반환 값으로 튜플 사용
    
    ```python
    def minus_and_product(x, y):
        return x - y,  x * y
    
    y = minus_and_product(4, 5)
    print(y) # (-1, 20)
    print(type(y)) # <class 'tuple'>
    ```

- 정리
  
  - return X → None
  
  - return O → 하나를 반환
    
    - 여러 개를 원하면, Tuple 활용(혹은 리스트와 같은 컨테이너 활용)
      
      ```python
      # 똑바로 읽어도 거꾸로 읽어도 같은 단어를 찾는 함수
      word_list = ['우영우', '기러기', '별똥별', '파이썬']
      def is_palindrome(word_list):
          palindrome_list = []
          for word in word_list:
              if word == word[::-1]:
                  palindrome_list.append(word)
          return palindrome_list
      print(is_palindrome(word_list))
      
      #['우영우', '기러기', '별똥별']
      ```

### 함수의 입력(Input)

- Parameter와 Argument (혼동하기 쉬운 개념)
  
  - Parameter : 함수를 정의할 때, 함수 내부에서 사용되는 변수 - 선언할 때 씀
  
  - Argument : 함수를 호출할 때, 넣어주는 값 - 호출할 때 씀
    
    ```python
    def function(ham):  # parameter : ham
        return ham
    
    function('spam')   # argument : 'spam'
    # 함수 리턴값 : spam
    ```

- Argument
  
  - 함수 호출 시 함수의 parameter를 통해 전달되는 값
  - Argument는 소괄호 안에 할당 : `func_name(argument)`
    - 필수 Argument : 반드시 전달되어야 하는 argument
    - 선택 Argument : 값을 전달하지 않아도 되는 경우는 기본값이 전달

- Positional Arugments (기본)
  
  - 기본적으로 함수 호출 시 Argument는 위치에 따라 함수 내에 전달됨
  - 즉, 아무런 지정도 없으면 Positional Argument
    - `def add(x, y)` ⇒ `add(2, 3)` ⇒ `x = 2`, `y = 3`

- Keyword Arguments
  
  - 직접 변수의 이름으로 특정 Argument를 전달할 수 있음
  
  - Keyword Argument 다음에 Positional Argument를 활용할 수 없음
    
    ⇒마지막에 사용하는게 좋음
    
    ```python
    def add(x, y):
        return x + y
    
    1. add(x = 2, y = 5) # 가능
    2. add(2, y = 5) # 가능
    3. add(x = 2, 5) # 에러 발생!
    ```

- Default Arguments Values
  
  - 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 함
    
    - 정의된 것 보다 더 적은 개수의 argument들로 호출될 수 있음
    
    ```python
    def add(x, **y = 0**):
        return x + y
    
    add(2)
    
    def add(x, **y = 0**):
        x = 2
        return x + y
    ```

- 정해지지 않은 여러 개의 Arguments 처리
  
  - print함수의 Arguments 개수가 변해도 잘 동작하는 이유?
    
    ```python
    print('hello')
    # hello
    
    print('you', 'need', 'python')
    # you need python
    ```
    
    - 애스터리스크(Asterisk) 혹은 어패킹 연산자라고 불리는 * 덕분에.

- 가변 인자`(*args)`
  
  - 가변 인자 : 여러 개의 Positional Argument를 하나의 필수 parameter로 받아서 사용
  
  - 언제 사용하는가? : 몇 개의 Positional Argument를 받을지 모르는 함수를 정의할 때 유용
  
  - ‘튜플’로 값을 모아서 사용함
    
    ```python
    def add(*args):
            for arg in args:
                    print(arg)
    
    add(2)
    add(2, 3, 4, 5)
    ```

- 패킹 / 언패킹
  
  - 가변 인자를 이해하기 위해서는 패킹, 언패킹을 이해해야 함
  
  - 패킹 : 여러 개의 데이터를 묶어서 변수에 할당하는 것
    
    ```python
    numbers = (1, 2, 3, 4, 5)  # 패킹
    print(numbers) # (1, 2, 3, 4, 5)
    ```
  
  - 언패킹 : 시퀀스 속의 요소들을 여러 개의 변수에 나누어 할당하는 것
    
    ```python
    numbers = (1, 2, 3, 4, 5)
    a, b, c, d, e = numbers  # 언패킹
    print(a, b, c, d, e) # 1 2 3 4 5
    
    a b = 1, 2 # 튜플을 언패킹 한 것과 같다
    ```
  
  - 언패킹시 변수의 개수와 할당하고자 하는 요소의 갯수가 동일해야함
    
    ```python
    numbers = (1, 2, 3, 4, 5)  # 패킹
    a, b, c, d, e, f = numbers  # 언패킹
    # ValueError: not enough values to unpack (expected 6, got 5)
    ```
  
  - 언패킹시 왼쪽의 변수에 asterisk(*)를 붙이면, 할당하고 남은 요소를 리스트에 담을 수 있음
    
    ```python
    numbers = (1, 2, 3, 4, 5)  # 패킹
    
    a, b, *rest = numbers   # 1, 2 를 제외한 나머지를 rest에 대입
    print(a, b, rest) # 1 2 [3, 4, 5]
    
    a, *rest, e = numbers   # 1, 5 를 제외한 나머지를 rest에 대입
    print(rest) # [2, 3, 4]
    ```
  
  - Asterisk(*)와 가변 인자
    
    - *는 스퀸스 언패킹 연산자라고도 불리며, 말 그대로 시퀀스를 풀어 헤치는 연산자
      
      - 주로 튜플이나 리스트를 언패킹하는데 사용
      - - 를 활용하여 가변 인자를 만들 수 있음
      
      ```python
      def func(*args):
              print(args)
              print(type(args))
      
      func(1, 2, 3, 'a', 'b')
      
      #결과
      
      (1, 2, 3, 'a', 'b')
      <class 'tuple'>
      ```
  
  - 가변 인자 예시
    
    - packing을 통해 받은 모든 숫자들의 합을 구하는 함수 만들기
      
      ```python
      def sum_all(*numbers): # (1, 2, 3) 으로 합쳐짐
              result = 0
              for number in numbers:
                              result += number
              return result
      
      print(sum_all(1, 2, 3))  # 6
      print(sum_all(1, 2, 3, 4, 5, 6))  # 21
      ```
    
    - 반드시 받아야하는 인자와, 추가적인 인자를 구분해서 사용할 수 있음
      
      ```python
      def print_family_name(father, mother, *pets):
              print(f'아버지: {father}')
              print(f'어머니: {mother}')
              print('반려동물들..')
              for name in pets:
                      print(f'반려동물: {name}')
      
      print_family_name('아부지', '어무니', '멍멍이', '냥냥이')
      
      # 결과
      아버지: 아부지
      어머니: 어무니
      반려동물들..
      반려동물: 멍멍이
      반려동물: 냥냥이
      ```

- 가변 키워드 인자(**kwargs)
  
  - 몇 개의 키워드 인자를 받을 지 모르는 함수를 정의할 때 유용
  
  - **kwargs는 딕셔너리로 묶여 처리되며, parameter에 **를 붙여 표현 ( 딕셔너리 형태로 모아줌)
    
    ```python
    def family(**kwargs):
            for key, value in kwargs.items():
                    print(key, ":", value)
    family(father= '아부지', mother= '어무니', baby='아기') # 입력할 때 key 문자열로 쓰지x
    
    # 결과
    father: 아부지
    mother: 어무니
    baby: 아기
    ```
  
  - 예시
    
    - 반드시 받아야하는 키워드 인자와, 추가적인 키워드 인자를 구분해서 사용할 수 있음
    
    ```python
    def print_family_name(father, mother, **pets):
            print("아버지 :", father)
            print("어머니 :", mother)
            if pets:   # **pets가 입력되지 않으면 False(빈 값)으로 간주되어 실행되지 않음
                    print('반려동물들..')
                    for species, name in pets.items():
                            print(f'{species} : {name}')
    
    print_family_name('아부지', '어무니', dog='멍멍이', cat='냥냥이')
    
    # 결과
    아버지 : 아부지
    어머니 : 어무니
    반려동물들..
    반려동물: 멍멍이
    반려동물: 냥냥이
    ```

- 가변 인자(*args)와 가변 키워드 인자( ** kwargs) 동시 사용 예시
  
  ```python
  def print_family_name(*parents, **pets):
          print("아버지 :", parents[0])
          print("어머니 :", parents[1])
          if pets:
                  print("반려동물들..")
                  for title, name in pets.items():
                          print('{} : {}'.format(title, name))
  
  print_family_name('아부지', '어무니', dog='멍멍이', cat='냥냥이')
  
  # 결과
  
  아버지 : 아부지
  어머니 : 어무니
  반려동물들..
  dog : 멍멍이
  cat : 냥냥이
  ```

### Python의 범위(scope)

- 함수는 코드 내부에 local scope를 생성하며,
  
  그 외의 공간인 global scope로 구분

- scope
  
  - global scope : 코드 어디에서든 참조(사용)할 수 있는 공간
  - local scope : 함수가 만든 scope. 함수 내부에서만 참조 가능

- variable
  
  - global variable : global scope에 정의된 변수
  - local variable : local scope에 정의된 변수

- 변수 수명주기(lifecycle)
  
  - 변수는 각자의 수명주기가 존재
    - built-in scope : 파이썬이 실행된 이후부터 영원히 유지
    - global scope : 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
    - local scope : 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

- 예시
  
  ```python
  def func():
          a = 20
          print('local', a)  # local 20
  
  func()
  print('global', a) # NameError : name 'a' is not defiend
  ```

- 이름 검색 규칙(Name Resolution)

- 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있음

- 아래와 같은 순서로 이름을 찾아나가며, LEGB Rule 이라고 부름
  
  - Local scope : 지역 범위 (현재 작업 중인 범위)
  
  - Enclosed scope : 지역 범위 한 단계 위 범위
  
  - Global scope : 최상단에 위치한 범위
  
  - Built-in scope : 모든 것을 담고 있는 범위(정의하지 않고 사용할 수 있는 모든 것)
    
    - ex) print()
  
  - def를 기준으로 가장 안에 있는것은 Local
  
  - def를 기준으로 밖에는 global, 안에는 local 이라고 기억하면 됨.

- 함수 내에서는 바깥 Scope의 변수에 접근 가능하나, 수정은 할 수 없음

- 예시
  
  ```python
  print(sum) # <built_in function sum>
  print(sum(range(2))) # 1
  sum = 5
  print(sum) # 5
  print(sum(range(2))) # TypeError: 'int' object is not callable
  ```
  
  ```python
  a = 0
  b = 1
  def enclose():
          a = 10
          c = 3
          def local(c):
                  print(a, b, c)  # 10 1 300
          local(300)
          print(a, b, c) # 10 1 3
  enclosed()
  print(a, b) # 0 1
  ```

- global 문
  
  - 현재 코드 블록 전체에 적용되며, 나열된 식별자(이름)이 global variable임을 나타냄
    
    - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없음
    - global에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 함.
  
  - 예시
    
    ```python
    # 함수 내부에서 글로벌 변수 변경하기
    a = 10
    def func1():
            global a
            a = 3
    
    print(a) # 10
    func1()
    print(a) # 3
    ```
  
  - global 관련 에러
    
    ```python
    # global 주의 사항
    a = 10
    def func1():
            print(a) # global a 선언 전에 사용
            global a
            a = 3
    
    print(a)
    func1()
    print(a) 
    
    #SyntaxError: name 'a' is used prior to global declaration
    ```
    
    ```python
    # global 주의 사항
    a = 10
    def func1(a):
            global a # parameter에 global 사용 불가
            a = 3
    
    print(a)
    func1(3)
    print(a) 
    
    #SyntaxError: name 'a' is parameter and global
    ```

- nonlocal : 자주 쓰진 않음 ← 필기 날렷어
  
  - global을 제외하고 가장 가까운(둘러싸고 있는) scope의 변수를 연결하도록 함
    - nonlocal에 나열된 이름은 같은 코드 블록에서 nonlocal의 앞에 등장할 수 없음
    - nonlocal에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 함
  - global과는 달리 이미 존재하는 이름과의 연결만 가능함

- 함수의 범위 주의!!
  
  - 기본적으로 함수에서 선언된 변수는 local scope에 생성되며, 함수 종료 시 사라짐
  - 해당 scope에 변수가 없는 경우 LEGB rule에 의해 이름을 검색함
    - 변수에 접근은 가능, 수정은 불가능
    - 값을 할당하는 경우 해당 scope의 이름공간에 새롭게 생성되기 때문
    - **단, 함수 내에서 필요한 상위 scope 변수는 argument로 넘겨서 활용할 것**
  - 상위 scope에 있는 변수를 수정하고 싶다면 global, nonlocal 키워드를 활용 가능
    - 단, 코드 복잡해지면서 변수의 변경을 추적하기 어렵고, 예기치 못한 오류 발생
    - **가급적 사용x, 함수 값을 바꾸고자 한다면 항상 argument로 넘기고 리턴 값을 사용 하는 것을 추천!**

### 함수의 문서화(Doc-string)

### 함수 응용

- 내장 함수
  
  - ## `map(function, iterable)`
  
  - `filter(function, iterable)`
  
  - `zip(*iterables)`
    
    - 복수의 interable을 모아 튜플을 원소로 하는 zip object를 반환
    - 보통 가로, 세로를 바꿀 때 씀

- lambda 함수
  
  - `lambda[parameter] : 표현식`
  
  - 표현식을 계산한 결과값을 반환하는 함수로, 이름이 없는 함수여서 익명함수라고도 불림
  
  - ‘표현식’은 print 찍었을 때 ‘값’으로 나오는 것.
    
    - `if a > 80 은 표현식이 아니다!`
    - def function(a) pass 함수호출. 즉, 값이 어찌됐든 나오니 표현식이다.
  
  - 특징
    
    - return문을 가질 수 없음
    - 간편 조건문 외 조건문이나 반복문을 가질 수 없음
  
  - 장점
    
    - 함수를 정의해서 사용하는 것보다 간결하게 사용
    - def를 사용할 수 없는 곳에서도 사용 가능
    
    ```python
    # 삼각형의 넓이를 구하는 공식 - def
    def triangle_area(b, h):
            return 0.5 * b * h
    print(triangle_area(5, 6)) # 15.0
    
    # 삼각형의 넓이를 구하는 공식 - 람다
    triangle_area = lambda b, h : 0.5 * b * h
    print(triangle_area(5,6)) # 15.0
    ```

- 재귀 함수(recursive function)
  
  - 자기 자신을 호출하는 함수
  
  - 무한한 호출을 목표로 하는 것이 아니며, 알고리즘 설계 및 구현에서 유용하게 활용
    
    - 알고리즘 중 재귀 함수로 로직을 표현하기 쉬운 경우가 있음(ex. 점화식)
    - 변수의 사용이 줄어들며, 코드의 가독성이 높아짐
  
  - 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성
  
  - 예시 : Factorial
    
    ```python
    def factorial(n):
            if n == 0 or n == 1:
                    return 1
            else:
                    return n * factorial(n-1)
    print(factorial(4)) # 24
    
    # 과정
    4 * f(3) 
    4 * 3 * f(2)
    4 * 3 * 2 * f(1)
    4 * 3 * 2 * 1 # (base case 도달)
    ```
  
  - 주의 사항
    
    - 재귀 함수는 base case에 도달할 때까지 함수를 호출함
    - 메모리 스택이 넘치게 되면(stack overflow) 프로그램이 동작하지 않게 됨
    - 파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 1000번으로, 호출 횟수가 이를 넘어가게 되면 Recursion Error 발생
  
  - Facotrial 코드를 반복문으로 작성
    
    ```python
    def fact(n):
            result = 1
            while n > 1:
                    result *= n
                    n -= 1
            return result
    
    print(fact(4)) # 24
    ```
  
  - 반복문 vs 재귀함수
    
    - 알고리즘 자체가 재귀적인 표현이 자연스러운 경우 재귀함수를 사용함
    - 재귀 호출은 변수 사용을 줄여줄 수 있음
    - 재귀 호출은 입력 값이 커질수록 연산 속도가 오래 걸림
