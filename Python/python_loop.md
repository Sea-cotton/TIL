> # 반복문

- 특정 조건을 만족할 때 까지 같은 동작을 꼐속 반복하고 싶을 때 사용
- 반복문의 종류
  - while 문
    - 종료 조건에 해당하는 코드를 통해 반복문을 종료시켜야 함
  - for 문
    - 반복가능한 객체를 모두 순회하면 종료(별도의 종료조건 필요x)
    - ‘횟수’ : 별찍기
  - 반복 제어
    - break, continue, for-else

### while 문

- 조건식이 참인 경우 반복적으로 코드 실행
  
  - 조건이 참인 동안 들여쓰기 된 코드 블록 실행
  
  - 코드 블록 모두 실행되고, 다시 조건식을 검사하며 반복적으로 실행
    
    - 조건식 확인 → 코드 실행 → 조건식 확인 → 코드 실행…
  
  - 종료 조건 반드시 필요(무한루프 방지)
    
    ```python
    while 조건:
        # Code block
    ```

### for 문

- 시퀀스(string, tuple, list, range)를 포함한 순회 가능한 객체(iterable)의 요소를 모두 순회
  
  - 처음부터 끝까지 모두 순회하므로 별도의 종료조건 필요하지 않음
  - 횟수로 반복함

- iterable
  
  - 순회할 수 있는 자료형(string, list, dict, tuple, range, set 등)
  
  - 순회형 함수(range, enumerate)
    
    ```python
    for 변수명 in iterable:
        # Code block
    ```

- 순서도
  
  - start → 시퀀스의 마지막 값에 접근하였는가
    
    - No : print(fruit)
    - yes : print(’끝’)
    
    ```python
    for fruit in ['apple', 'mango', 'banana']:
        print(fruit)
    print('끝')
    
    # 결과
    apple
    mango
    banana
    끝
    ```

- 문자열(String) 순회 : 사용자가 입력한 문자를 한 글자씩 출력
  
  ```python
  chars = input()  # happy
  
  for char in chars:
      print(char)
  
  # range 활용 (앞에것 권장)
  
  for idx in range(len(chars)):
      print(chars[idx])
  ```

- 딕셔너리(Dictionary) 순회
  
  - 딕셔너리는 기본적으로 key를 순회하며, key를 통해 값을 활용
  
  ```python
  grades = {'john' : 80, 'eric' : 90}
  for student in grades:
      print(student)
  
  #
  john
  eric
  
  # value도 함께 출력
  
  for student in grades:
      print(student, grades[student])
  
  #
  john 80
  eric 90
  ```

- 추가 메서드를 활용한딕셔너리 순회 (더 많이쓰는 방식)
  
  - `key()` : key로 구성된 결과
  - `values()` : value로 구성된 결과
  - `items()` : (Key, value)의 튜플로 구성된 결과
  
  ```python
  grades = {'john' : 80, 'eric' : 90}
  print( 필기참조
  ```

- enumerate 순회 ( 자주씀)
  
  - `enumerate()` : 인덱스와 객체를 쌍으로 담은 열거형(enumerate) 객체 반환
    - (index, value) 형태의 tuple로 구성된 열거 객체를 반환
    - enumerate(list, start)
      - start 기본값=0
      - start 지정하면 해당 값부터 순차적으로 증가
  
  ```python
  members = 필기참조
  ```

- **List Comprehension (엄청 자주쓴다!)**
  
  - 표현식과 제어문을 통해 특정 값을 가진 리스트를 간결하게 생각하는 방법
    
    ```python
    [code for 변수 in iterable]
    [code for 변수 in iterable if 조건식]
    ```
  
  - 1~3의 세제곱의 결과가 담긴 리스트를 만들기
    
    ```python
    cubic_list= [number ** 3 for number in range(1,4)]
    print(cubic_list)
    
    # [1, 8, 27]
    ```

- Dictionary Comprhension
  
  - 표현식과 제어문을 통해 특정 값을 가진 딕셔너리를 간결하게 생각하는 방법
    
    ```python
    {key: value for 변수 in iterable}
    {key: value for 변수 in iterable if 조건식}
    ```
  
  - 1~3의 세제곱의 결과가 담긴 리스트를 만들기
    
    ```python
    cubic_list= {number: number ** 3 for number in range(1,4)]
    print(cubic_list)
    
    # {1: 1, 2: 8, 3: 27}
    ```

### 반복문 제어

- break : 반복문을 종료
  
  ```python
  n = 0
  while True:
      if n == 3:
          break  # n = 3이 되는 순간 while문 종료, 밑에 코드들 실행x
      print(n)
      n += 1
  
  # 결과
  0
  1
  2
  ```
  
  ```python
  for i in range(10)
      if i > 1:
          print('0과 1만 필요해!')
          break # i = 2되면 for문 종료, 밑에 코드 실행 x
      print(i)
  
  # 결과
  0
  1
  '0과 1만 필요해!'
  ```

- continue : continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행
  
  ```python
  for i in range(6):
      if i % 2 == 0:
          continue # 이후 코드인 print(i)가 실행되지 않고 바로 다음 반복을 실행
      print(i)
  
  #
  1
  3
  5
  ```

- for-else
  
  - 끝까지 반복문을 실행한 이후에 else문 실행
  
  - 주의) break를 통해 중간에 종료되는 경우 else문은 실행되지 않음
    
    ⇒ break가 제대로 실행되었는지 판단하기 위해 else를 쓰기도 함
    
    ```python
    for char in 'apple':
        if char = 'b':
            print('b!')
            break
    else:
        print('b가 없습니다.')
    
    # b가 없습니다.
    ```
    
    ```python
    for char in 'banana':
        if char = 'b':
            print('b!')
            break # break로 중단됨 - else구문 실행x
    else:
        print('b가 없습니다.')
    
    # b!
    ```

- pass
  
  - 아무것도 하지 않음(문법적으로 필요하지만, 할 일이 없을 때 사용)
  
  - 반복문이 아니어도 사용 가능
    
    ```python
    # i가 2일 때
    for i in range(4):
        if i == 2:
            pass
        print(i)
    
    #
    0
    1
    2
    3
    ```
