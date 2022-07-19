> # 인덱싱/슬라이싱 (Indexing/Slicing)

#### 인덱싱 : 시퀀스의 특정 인덱스 값에 접근할 수 있다.

- 해당 인덱스가 없는 경우 IndexError 발생

- 리스트에 인덱싱을 통해 접근
  
  ```python
  a = [1, 2, 3]
  a[2] # 3
  
  # 바로 이렇게 표현할 수도 있다. 
  [1, 2, 3][2]
  ```

- 튜플을 인덱싱을 통해 값에 접근
  
  ```python
  (1, 2, 3)[2] # 3
  ```

- range을 인덱싱을 통해 값에 접근 *(range는 필요할 때만 값을 전달해준다.)*
  
  ```python
  range(3)[2] # 2
  ```

- 문자열을 인덱싱을 통해 값에 접근
  
  ```python
  b = 'abc'
  b[0]
  
  #'a'
  ```

- 찾고자 하는 인덱스가 존재하지 않을 때 오류 발생
  
  ```python
  'apple'[99]
  # IndexError: string index out of range
  ```

---

### 슬라이싱

- 시퀀스를 특정 단위로 자를 수 있다.

- `Sequence[start : end [:step ]]`
  
  - step은 옵션. 설정안해도 기본값은 1. 즉, 1씩 증가하며 자르겠다는 뜻

- 슬라이싱 작동원리 예제
  
  ```python
  print([1, 2, 3, 4][1:4]) # [2, 3, 4]
  print((1, 2, 3)[:2]) # (1, 2)
  print(range(10)[5:8]) # range(5, 8) -> list에 넣으면 5, 6, 7
  print('abcd'[2:4]) # cd
  ```

- 시퀀스를 k 간격으로 슬라이싱 할 수 있다
  
  ```python
  print([1, 2, 3, 4][0:4:2]) # [1, 3]
  
  s = 'abcdefghi'
  print(s[:3]) # abc
  print(s[5:]) # fghi
  print(s[::]) # abcdefghi
  print(s[::-1]) # ihgfedcba
  ```
