> # 조건문

- 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용

### 기본 형식

- 조건문에는 참/거짓에 대한 조건식
  
  - 조건이 참인 경우 들여쓰기 되어있는 코드 블록을 실행
  
  - 이외의 경우 else 이후 들여쓰기 되어있는 코드 블록을 실행 (선택적으로 활용 가능)
  
  - 들여쓰기 주의!!
    
    ```python
    if 조건 == True:
        # Run this Code block
    else:
        # Run this Code block
    ```

- 조건문 예시
  
  ```python
  a = 5
  if a > 5:
      print('5 초과')
  else:
      print('5 이하;'')
  print(a)
  
  # 결과
  5 이하
  5
  ```

- 조건문 실습 문제 : 변수 num의 값의 홀수/짝수 여부를 출력*(num은 input을 통해 입력받음)*
  
  ```python
  num = int(input('숫자 입력'))
  if num % 2 == 1:
      print('홀수')
  else:
      print('짝수')
  ```
  
  - 주의) `input()`으로 입력받는 건 ‘문자열’이므로 앞에 꼭 `int()`를 붙여줘야한다.

### 복수 조건문

- 복수의 조건식을 활용할 경우 elif를 활용하여 표현함
  
  ```python
  if 조건:
      # Code block
  elif 조건:
      # Code block
  elif 조건:
      # Code block
  else:
      # Code block
  ```

- 실습 문제 : 미세먼지 농도에 따른 위험등급이 다음과 같을 때, dust 값에 따라 등급을 출력하는 조건식을 작성하시오(단, 조건식 완료 후 미세먼지 확인 완료라는 문구를 출력)
  
  ```python
  dust = 80
  if dust > 150:
      print('매우 나쁨')
  elif dust > 80:
      print('나쁨')
  elif dust > 30:
      print('보통')
  else:
      print('좋음')
  print('미세먼지 확인 완료!')
  
  # 결과
  보통
  미세먼지 확인 완료!
  ```
  
  - 조건식을 동시에 검사하는게 아니라, 위에서부터 하나씩 순차적으로 비교한다(순서도를 생각)

### 중첩 조건문

- 조건문은 다른 조건문에 중첩되어 사용될 수 있음

- 들여쓰기 주의
  
  ```python
  if 조건:
      # Code block
      if 조건:
          # Code block
  else:
      # Code block
  ```

- 예시 : 위의 코드에서 중첩조건문을 활용하여 농도값이 300이 넘는 경우 ‘실외 활동을 자제해주세요’를 추가로 출력하고 음수인 경우 ‘값이 잘못되었습니다’를 출력
  
  ```python
  dust = 500
  if dust > 150:
      print('매우 나쁨')
      if dust > 300:
          print('실외 활동을 자제하세요.')
  elif dust > 80:
      print('나쁨')
  elif dust > 30:
      print('보통')
  elif dust >= 0:
      print('좋음')
  else:
      print('값이 잘못 되었습니다.')
  
  # 결과
  보통
  미세먼지 확인 완료!
  ```

### 조건 표현식

- 조건 표현식(Coditional Expression)이란?
  
  - 조건 표현식을 일반적으로 조건에 따라 값을 정할 때 활용
  
  - 삼항 연산자(Ternary Operator)로 부르기도 함
    
    ```python
    true인 경우 값 if 조건 else false인 경우 값
    ```

- 실습 문제 : num이 정수일 때, 아래 코드는 무엇인가? ‘절댓값을 저장하는 코드’
  
  ```python
  value = num if num > = 0 else -num
  ```

- 조건문 → 삼항 연산자
  
  ```python
  # 조건문
  num = 2
  if num % 2:
      result = '홀수입니다'
  else:
      result = '짝수입니다'
  print(reslut)
  
  # 삼항 연산자
  num = 2
  result = '홀수입니다' if num % 2 else '짝수입니다'
  print(result)
  ```

- 삼항연산자 → 조건문
  
  ```python
  # 삼항 연산자
  num = -5
  value = num if num >= 0 else 0 
  print(value)
  
  # 조건문
  num = -5
  if num > = 0:
      value = num
  else:
      value = 0
  print(value)
  ```
