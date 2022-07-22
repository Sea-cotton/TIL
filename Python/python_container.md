> # 컨테이너

#### 

#### 컨테이너란?

- 여러 개의 값(데이터)을 담을 수 있는 것(객체)로, 서로 다른 자료형을 저장할 수 있음

- 컨테이너의 분류
  
  - 순서가 있는 데이터(Ordered) vs. 순서가 없는 데이터(Unordered)
  
  - *주의) 순서대로 나열되었다(ordered)는 것이 정렬되었다(sorted)를 보장하는 것은 아니다.*

----

#### 컨테이너의 분류

- 컨테이너
  
  - 시퀀스형
    
    - 리스트 *(가변형)*
    
    - 튜플 *(불변형)*
    
    - 레인지 *(불변형)*
  
  - 비시퀀스형
    
    - 세트 *(가변형)*
    
    - 딕셔너리 *(가변형)*

---

#### 1. 시퀀스형

##### 1-1) 리스트

- 여러 개의 값을 **순서가 있는 구조로 저장**하고 싶을 때 사용

- 리스트의 생성과 접근
  
  - 리스트는 대괄호([ ]) 혹은list()를 통해 생성
    
    - 파이썬에서는 어떠한 자료형도 저장할 수 있으며, 리스트 안에 리스트도 넣을 수 있음
    
    - 생성된 이후 내용 변경이 가능 -> 가변 자료형
    
    - 이러한 유연성 때문에 파이썬에서 가장 흔히 사용
  
  - 순서가 있는 시퀀스로 인덱스를 통해 접근 가능
    
    - 값에 대한 접근은 list[i]
      
      ```python
      # 리스트명 = [요소1, 요소2, 요소3, ...]
      
      list_a = []
      list_b = [1, 2, 3]
      list_c = ['Life', 'is', 'too', 'short']
      list_d = [1, 2, 3, 'Python', ['리스트', '안에', '리스트']]
      ```
      
      |                | 객체 1 | 객체 2 | 객체 3 | 객체 4 | 객체 5 | 객체 6 | 객체 7 |
      |:--------------:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
      | Positive index | 0    | 1    | 2    | 3    | 4    | 5    | 6    |
      | Negative index | -7   | -6   | -5   | -4   | -3   | -2   | -1   |

- 리스트의 생성과 접근 예시
  
  ```python
  my_list = []
  another_list = list()
  print(type(my_list)) # <class 'list'>
  print(type(another_list)) # <class 'list'>
  
  location = ['서울', '대전', '구미', '광주', '부울경']
  print(location) # ['서울', '대전', '구미', '광주', '부울경']
  print(type(location)) # <class 'list'>
  print(location[0]) # 서울
  ```
  
  - 리스트는 담고있는 요소를 바꿀 수 있다 - > 가변 자료형(mutable)
    
    ```python
    location[0] = '양양'
    print(location) # ['양', '대전', '구미', '광주', '부울경']    
    ```

- 리스트의 생성과 접근 문제(이중접근)
  
  ```python
  boxes = ['A', 'B', ['apple', 'banana', 'cherry']]
  
  print(len(boxes)) # 3
  print(boxes[2]) # ['apple', 'banana', 'cherry']
  print(boxes[2][-1]) # cherry
  print(boxes[-1][1][0]) # b
  ```

- boxes의 3번째 요소들 중, 마지막 요소를 negative index로 접근하여 출력해 봅시다.
  
  ```python
  print(boxes[2][-1]) # cherry
  print(boxes[-1][-1]) # cherry
  ```

- boxes의 마지막 요소들 중, 두번째 요소의 첫번째 문자열을 출력해 봅시다.
  
  ```python
  print(boxes[-1][1][0]) # b
   print(boxes[2][1][0]) # b
  ```

#### 1-2) 튜플

- 여러 개의 값을 순서가 있는 구조로 저장하고 싶을 때 사용

- 파이썬에서는 값을 전달할 때 튜플을 사용한다.
  
  ```python
  another_tuple = 1, 2
  print(another_tuple)
  print(type(another_tuple))
  ```

- 리스트와의 차이점 : 생성 후, 담고 있는 값 변경 불가(불변 자료형)

- 항상 소괄호 형태로 사용
  
  ```python
  print((1, 2, 3, 1)) # (1, 2, 3, 1)
  print(tuple((1, 2, 3, 1))) # (1, 2, 3, 1)
  print(type((1, 2, 3, 1)) # <class 'tuple'>
  ```

- 소괄호(()) 혹은 tuple()을 통해 생성

- 튜플은 수정 불가능한(immutable) 시퀀스로 인덱스로 접근 가능

- 값에 대한 접근은 my_tuple[i]
  
  ```python
  # 값 접근
  a = (1, 2, 3, 1)
  print(a[1]) # 2
  
  #값 변경 => 불가능
  a[1] = '3' # TypeError : 'tuple' object does not support item assignment
  ```

- 튜플 생성 주의사항
  
  - 단일 항목의 경우
    
    - 하나의 항목으로 구성된 튜플은 생성 시 값 뒤에 쉼표를 붙여야 함
      
      ```python
      b = (3,)
      print(type(b)) # <class 'tuple'>
      
      # b = (3) 이면 이건 튜플이 아니라 그냥 괄호 우선순위 쳐준거임
      ```
  
  - 복수 항목의 경우
    
    - 마지막 항목에 붙은 쉼표는 없어도 되지만, 넣는 것을 권장(Trailing comma)
      
      ```python
      # 둥근 괄호를 사용해서 튜플 생성하기
      tuple_a = (1,)
      print(tuple_a) # (1,)
      print(type(tuple_a)) # <class 'tuple'>
      
      tuple_b = (1, 2, 3,)
      print(tuple_b) # (1, 2, 3,)
      print(type(tuple_b)) # <class 'tuple'>
      
      #둥근 괄호 없이 튜플 생성하기
      a = 1,
      print(a) # (1,)
      print(type(a)) # <class 'tuple'>
      
      b = 1, 2, 3
      print(b) # (1, 2, 3,)
      print(type(b)) # <class 'tuple'>
      ```

- 튜플 대입(Tuple assignment)
  
  - 튜플 대입이란?
    
    - 우변의 값을 좌변의 변수에 한 번에 할당하는 과정
  
  - 튜플은 일반적으로 파이썬 내부에서 활용
    
    - 추후 함수에서 복수의 값을 반환할 때에도 사용
      
      ```python
      x, y = 1, 2
      print(x, y) # 1 2
      
      # 실제로 tuple로 처리
      x, y = (1, 2)
      print(x, y) # 1, 2
      ```

- 주의(헷갈리지 말기)
  
  ```python
  a , b = 1, 2, 3  # 이건 에러떠서 안됨
  
  b = 1, 2, 3 # 이건 가능하다. 튜플이니까
  print(b) # (1, 2, 3)
  print(type(b)) # <class 'tuple'>
  ```

- list는 ` get() `함수를 지원하지 않는다.

##### 

##### 1-3) Range

- Range의 정의
  
  - 숫자의 시퀀스를 나타내기 위해 사용
  
  - 주로 반복문과 함께 사용됨
    
    ```python
    print(range(4)) # range(0, 4)
    
    #담겨 있는 숫자를 확인하기 위하여 리스트로 형변환(실제 활용시에는 형번환 필요x)
    print(list(range(4))) # [0, 1, 2, 3]
    
    print(type(range(4))) # <class 'range'>
    ```

- range의 사용방법
  
  - 기본형 : range(n)
    
    - 0부터 n-1까지의 숫자의 시퀀스
  
  - 범위 지정 : range(n, m)
    
    - n부터 m-1까지의 숫자의 시퀀스
  
  - 범위 및 스텝 지정 : range(n, m, s)
    
    - n부터 m-1까지 s만큼 증가시키며 숫자의 시퀀스
      
      ```python
      # 0부터 특정 숫자까지
      print(list(range(3))) # [0, 1, 2]
      
      # 숫자의 범위
      print(list(range(1, 5))) # [1, 2, 3, 4]
      
      # step 활용
      print(list(range(1, 5, 2))) # [1, 3]
      ```

- range의 사용방법2 - 역순
  
  ```python
  print(list(range(6, 1, -1))) # [6, 5, 4, 3, 2]
  print(list(range(6, 1, -2))) # [6, 4, 2]
  print(list(range(6, 1, 1))) # []
  ```

- 0부터 -9까지 담긴 range를 만들고 list로 형 변환을 해 봅시다.
  
  ```python
  c = range(0, -10, -1)
  print(list(c))
  
  # 결과
  [0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
  ```

##### 

##### 1-4) 슬라이싱 연산자

- 시퀀스를 특정 단위로 슬라이싱
  
  - 인덱스와 콜론을 사용하여 문자열의 특정 부분만 잘라낼 수 있음
  
  - 슬라이싱을 이용하여 문자열을 나타낼 때 콜론을 기준으로 **앞 인덱스에 해당하는 문자는 포함**되지만 **뒤 인덱스에 해당하는 문자는 미포함**
    
    ```python
    # 리스트([1:4]에서 1은 포함 4는 미포함)
    print([1, 2, 3, 5][1:4]) # [2, 3, 5]
    
    # 튜플
    print((1, 2, 3)[:2]) # (1, 2)
    
    #range
    print(range(10)[5:8]) # range(5, 8)
    
    #문자열
    print('abcd'[2:4]) # cd
    ```

- 시퀀스를 k간격으로 슬라이싱
  
  ```python
  # 리스트
  print([1, 2, 3, 5][0:4:2]) # [1, 3]
  
  # 튜플
  print((1, 2, 3, 5)[0:4:2]) # (1, 2)
  
  #range
  print(range(10)[1:5:3]) # range(1, 5, 3)
  
  #문자열
  print('abcdefg'[1:3:2]) # b
  ```

- 문자열 슬라이싱 예제
  
  - s = 'abcdefghi'
  
  - s[2:5] -> 'cde'
  
  - s[:3] -> 'abc'
  
  - s[::] -> 'abcdefghi' *( s[0:len(s):1] 과 동일 )*
  
  - s[::-1] -> 'ihgfedcba' *( s[-1:-(len(s)+1):-1] 과 동일 )
  
  - s[5:] -> 'fghi'
  
  - s[5:2:-1] -> 'fed'
    
    |       | a   | b   | c   | d   | e   | f   | g   | h   | i   |
    | ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
    | index | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   |
    | index | -9  | -8  | -7  | -6  | -5  | -4  | -3  | -2  | -1  |

---

#### 2. 비시퀀스형

##### 2-1) 셋(Set)

- Set이란 중복되는 요소 없이, 순서에 상관없는 데이터들의 묶음
  
  - 데이터의 중복을 허용하지 않기 때문에 중복되는 원소가 있다면 하나만 저장
  
  - 순서가 없기 때문에 인덱스를 이용한 접근 불가능

- 수학에서의 집합을 표현한 컨테이너
  
  - 집합 연산이 가능(여집합을 표현하는 연산자는 별도로 존재 X)
  
  - 중복된 값이 존재하지 않음

- 담고 있는 요소를 삽입, 변경, 삭제 가능 -> 가변 자료형(mutable)

- 셋(Set) 생성
  
  - 중괄호({}) 혹은 set()을 통해 생성
    
    - 빈 Set을 만들기 위해서는 반드시 set()을 활용해야 함
  
  - 순서가 없어 별도의 값에 접근할 수 없음
    
    ```python
    # Set는 중복 값 제거
    print({1, 2, 3, 1, 2}) # {1, 2, 3}
    print(type{1, 2, 3}) # <class 'set'>
    
    # 빈 중괄호는 Dictionary
    blank = {}
    print(type(blank)) # <class 'dict'>
    blank_set = set()
    print(type(blank_set)) # <class 'set'>
    
    # Set은 순서가 없어 인덱스 접근 등 특정 값에 접근할 수 없음
    print({1, 2, 3}[0]) # TypeError : 'set' object is not subscriptable
    ```

- Set 사용하기
  
  - 셋을 활용하면 다른 컨테이너에서 중복된 값을 쉽게 제거할 수 있음
  
  - 단, 이후 순서가 무시되므로 순서가 중요한 경우 사용x
  
  - 아래의 리스트에서 고유한 지역의 개수는?
    
    ```python
    my_list = ['서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산']
    
    print(len(set(my_list))) # 4
    ```
  
  - 아래의 리스트에서 고유한 지역을 등장한 순서대로 출력하시오
    
    ```python
    my_list = ['서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산']
    
    # Set을 사용하는 순간 순서가 사라짐(실행할 때마다 순서가 변경됨)
    print(set(my_list)) # {'광주', '서울', '부산', '대전'}
    ```

- Set 연산자
  
  - | : 합집합
  
  - & : 교집합
  
  - -: 차집합
  
  - ^ : 대칭차집합
  
  - 여집합은 없음
    
    ```python
    A_set = {1, 2, 3, 4}
    B_set = {1, 2, 3, "Hello", (1, 2, 3)}
    
    print(A_Set | B_set) # {1, 2, 3, 4, (1, 2, 3), "Hello"}
    print(A_Set & B_set) # {1, 2, 3}
    print(B_Set - A_set) # {(1, 2, 3), "Hello"}
    print(A_Set ^ B_set) # {"Hello", 4, (1, 2, 3)}
    ```

##### 

##### 2-2) 딕셔너리

- 딕셔너리의 정의
  
  - 키-값(key-value) 쌍으로 이뤄진 자료형(3.7부터는 ordered, 이하 버전은 unordered)
  
  - Dictionary의 키(key)
    
    - key는 변경 불가능한 데이터(immutable)만 활용 가능
      
      - string, integer, float, boolean, tuple, range
  
  - 각 키의 값(values)
    
    - 어떤 형태든 관계없음

- 딕셔너리에는 중복된 key는 존재할 수 없다. 중복된 키의 밸류는 가장 마지막에 적힌 것으로 확정된다.
  
  ```python
  dict_a = {1: 1, 2: 2, 3: 3, 1: 4}
  print(dict_a)
  
  # 결과
  {1: 4, 2: 2, 3: 3}
  ```

- 딕셔너리 생성
  
  - 중괄호({}) 혹은 dict()을 통해 생성
  
  - key를 통해 value에 접근
    
    ```python
    dict_a = {}
    print(type(dict_a)) # <class 'dict'>
    
    dict_b = dict()
    print(type(dict_b)) # <class 'dict'>
    
    dict_a = {'a': 'apple', 'b': 'banana', 'list': [1, 2, 3]}
    print(dict_a) # {'a': 'apple', 'b': 'banana', 'list': [1, 2, 3]}
    print(dict_a['list']) # [1, 2, 3]
    
    dict_b = dict('a': 'apple', 'b': 'banana', 'list': [1, 2, 3])
    print(dict_b) # {'a': 'apple', 'b': 'banana', 'list': [1, 2, 3]}
    ```

- 키 값 확인 : `.keys()`
  
  ```python
  print(phone_book.keys()), type(phone_book.keys()))
  
  # 결과
  dict_keys(['서울', '구미', '대전', '광주', '부산'])  <class 'dict_keys'>
  ```

- 밸류값 확인`.values()`
  
  ```python
  print(phone_book.values())
  ```

- key와 value 확인 : `.items()`  -> 주로 반복문에 쓰인다.
  
  ```python
  print(phone_book.items())
  
  # 결과
  dict_items([('서울', '02'), ('구미', '054'), ('대전', '042'), ('광주', '061'), ('부산', '051')])
  
  # 반복문에 활용 (필기참조)
  for key, value in phone_book.items():
      print(key, value)
  
  # 결과
  서울 02
  구미 054
  대전 042
  광주 061
  부산 051
  ```

- `.get()` 함수로 키에 맞는 값을 가지고 올 수 있다.
  
  - ex) movie.get('genre_ids') : 'movie' 딕셔너리에서 'genre_ids' 키에 맞는 값을 추출

---
