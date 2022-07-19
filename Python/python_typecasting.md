> # 형 변환(Typecasting)

#### 암시적 형변환

- 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환
  
  - bool
  
  - Numeric type (int, float)
    
    ```python
    print(True + 3) # 4
    print(3 + 5.0) # 8.0
    ```

- 표현하는 범위가 큰 형태로 형 번환이 이루어진다.
  
  - 정수 * 실수 ⇒ 실수 (값을 손실없이 저장)
  
  - boolean + integer ⇒ boolean이 자동으로 integer로 바뀌어 연산됨
    
    ```python
    a = True + 10
    print(a, type(a))
    
    # 결과
    11 <class 'int'>
    ```
  
  - int, float, complex
    
    ```python
    int_num = 2
    float_num = 5.0
    complex_num = 3 + 5j
    
    res = int_num + float_num
    print(type(res)) # <class 'float'>
    
    res = int_num + complex_num
    print(type(res)) # <class 'complex'>
    ```

#### 명시적 형 변환

- 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환하는 경우

- int
  
  - str, float => int
  
  - 단, 형식에 맞는 문자열만 정수로 변환 가능
  
  - int + str 연산 불가능 → 명시적 형변환 해줘야됨 
    
    ```python
    # 문자열은 암시적 타입 변환이 되지 않음
    print('3' + 4) # TypeError : can only concatenate str (not "int") to str
    
    # 명시적 타입 변환이 필요함
    print(int('3') + 4) # 7
    
    # 정수 형식이 아닌 경우 타입 변환할 수 없음
    print(int('3.5') + 5) # ValueError : invalid literal for int() with base 10 : '3.5'
    ```
  
  - ‘3.5’를 바로 int로 바꿀 수 없다. float으로 바꾼 뒤에 다시 int로 해줘야됨
    
    ```python
    a = '3.5'
    b = float(a)
    int(b) # 3
    ```

- float
  
  - str(참고), int -> float
  
  - 단, 형식에 맞는 문자열만 float으로 전환 가능
    
    ```python
    print('3.5' + 3.5) # TypeError : can only concatenate str (not "int") to str
    
    # 정수 형식인 경우에도 float로 타입 변환
    print(float('3')) # 3.0
    
    # float 형식이 아닌 경우 타입 변환할 수 없음
    print(float('3/4) + 5.3) # ValueError : could not convert string to float: '3/4'
    ```

- str
  
  - int, float, list, tuple, dict -> str
    
    ```python
    print(str(1)) # 1
    print(str(1.0)) # 1.0
    print(str[1, 2, 3]) # [1, 2, 3]
    print(str(1, 2, 3)) # (1, 2, 3)
    print(str{1, 2, 3}) # {1, 2, 3}
    ```

- 컨테이너 형 변환

|            | string | list        | tuple       | range | set         | dictionary |
| ---------- | ------ | ----------- | ----------- | ----- | ----------- | ---------- |
| string     |        | o           | o           | x     | o           | x          |
| list       | o      |             | o           | x     | o           | x          |
| tuple      | o      | o           |             | x     | o           | x          |
| range      | o      | o           | o           |       | o           | x          |
| set        | o      | o           | o           | x     |             | x          |
| dictionary | o      | o<br>(key만) | o<br>(key만) | x     | o<br>(key만) |            |

- range → str 형변환
  
  ```python
  r = range(1, 5)
  print(str(r))
  
  # 결과
  range(1, 5) # range( ) 그대로 나온다
  ```

- dictionary 형변환 : key값만 변환되지만, `.values()`를 붙이면 value로도 변환 가능하다
  
  ```python
  d = {'name': 'ssafy', 'year': 2020}
  print(str(d))
  print(list(d))
  print(tuple(d))
  print(set(d))
  
  # 결과
  {'name': 'ssafy', 'year': 2020}
  ['name', 'year']
  ('name', 'year')
  {'year', 'name'}
  
  print(list(d.values())) 
  
  # 결과
  ['ssafy', 2020]
  ```
