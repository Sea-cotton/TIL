> # 데이터 구조

## 데이터 구조 활용

- 데이터 구조 활용을 위해서는 메서드 활용
- 메서드는 클래스 내부에 정의한 함수, 사실상 함수 동일
- 쉽게 설명하면 객체의 기능
- `데이터 구조.메서드()` 형태로 활용
- 파이썬 공식 문서의 표기법
  - python 구문이 아니며, 문법을 표현하기 위한 것
  - `str.replace(old, new[, count])`
    - old, new는 필수 / [,count] 선택적 인자를 의미함

---

## 순서가 있는 데이터 구조(시퀀스형)

### 문자열

- 모든 문자는 str타입(변경 불가능한 immutable)
  
  ```python
  word = 'hello'
  print(word) # hello
  
  word = 'test'
  print(word) # test
  ```
  
  - 기존의 문자열을 변경하는게 아니라, 변경된 문자열을 새롭게 만들어서 반환하는 것임
    - ex) replace, strip, title 등

- 문자열 조회/탐색 및 검증 메서드
  
  | 문법          | 설명                                                         |
  | ----------- | ---------------------------------------------------------- |
  | s.find(x)   | x의 첫 번째 위치를 반환, 없으면 -1을 반환                                 |
  | s.index(x)  | x의 첫 번재 위치를 반환, 없으면 오류 발생(프로그램이 멈춘다)                       |
  | s.isalpha() | 알파벳 문자 여부(숫자가 아닌)<br/> *단순 알파벳이 아닌 유니코드 상 Letter (한국어도 포함) |
  | s.isupper() | 대문자 여부                                                     |
  | s.islower() | 소문자 여부                                                     |
  | s.istitle() | 타이틀 형식 여부(첫글자 대문자, 나머지 소문자)                                |
  | s.isspace() | 공백으로만 이루어져있는지 여부                                           |
  
  - `.find(x)`
    
    ```python
    print('apple'.find('p')) # 1
    print('apple'.find('k')) # -1
    ```
  
  - `.index(x)`
    
    ```python
    print('apple'.index('p')) # 1
    print('apple'.index('k')) # ValueError: substring not found
    ```
  
  - 검증 메서드
    
    ```python
    print('abc'.isalpha()) # True
    print('ㄱㄴㄷ'.isalpha()) # True
    print('Ab'.isupper()) # False
    print('ab'.islower()) # True
    print('Title Title!'.istitle()) # True
    print('   n'.isspace()) # False
    print('\n \t '.isspace()) # True
    ```
    
    - `.isdemical()` , `.isdigit()`, `.isnumeric()` : 보통 `isdecimal()` 정도만 써서 숫자여부를 확인한다

- 문자열 변경 메서드
  
  | 문법                             | 설명                                                      |
  | ------------------------------ | ------------------------------------------------------- |
  | s.replace(old,new[,count])     | -바꿀 대상 글자를 새로운 글자로 바꿔서 반환<br/>-count를 지정하면, 해당 개수만큼만 시행 |
  | s.strip([chars])               | -공백이나 특정 문자를 제거<br/>-문자열을 지정하지 않으면 공백을 제거함              |
  | s.split(sep=None, maxsplit=-1) | 공백이나 특정문자를 기준으로 분리                                      |
  | 'separator’.join([iterable])   | 구분자로 iterable을 합침                                       |
  | s.caplitalize()                | 가장 첫 번재 글자를 대문자로 변경                                     |
  | s.title()                      | 문자열 내 띄어쓰기 기준으로 각 단어의 첫 글자는 대문자로, 나머지는 소문자로 변환          |
  | s.upper()                      | 모두 대문자로 변경                                              |
  | s.lower()                      | 모두 소문자로 변경                                              |
  | s.swapcase()                   | 대←→ 소문자 서로 변경                                           |
  
  - `s.strip([chars])`
    
    - 특정한 문자들을 지정하면,(순서 상관없이 모든 조합)
      - 양쪽을 제거하거나(strip)
      - 왼쪽을 제거하거나(lstrip)
      - 오른쪽을 제거(rstrip)
    - 문자열을 지정하지 않으면 공백을 제거함
      
      ```python
      b = 'hihihihahahahihi'
      
      # rstrip 메서드로 b의 오른쪽에서부터 글자 hi를 제거해봅시다.
      b.rstrip('ih') # 'hihihihahaha'
      
      # lstrip 메서드로 b의 왼쪽에서부터 글자 hi를 제거해봅시다.
      b.lstrip('hi') # 'ahahahihi'
      ```
      
      ```python
      c = 'monty python'
      
      # rstrip 메서드로 c의 오른쪽에서부터 글자 ' python'을 제거해봅시다.
      c.rstrip('python') # 'monty '
      c.rstrip(' python') # 'm'
      ```
      - `c.rstrip(' python')` : ‘monty’만 남을 것 같지만 ‘공백, p, y, t, h, o, n’이 들어간 모든 문자를 제거해서 m만 남게된다.
      
      ```python
      # '.'을 제거하려면?
      a = 'ssafy.python.com'
      print(a.strip('.')) # ssafy.python.com <-제거되지 않음
      print(a.replace('.', '')) # ssafypythoncom
      ```
  
  - `s.split(sep=None, maxsplit=-1)`
    
    - 문자열을 특정한 단위로 나눠 [리스트]로 반환
      
      - sep이 None이거나 지정되지 않으면 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음.
      - maxsplit이 -1인 경우에는 제한이 없음
  
  - `'separator’.join([iterable])`
    
    - 반복가능한(iterable) 컨테이너 요소들을 separator(구분자)로 합쳐 문자열 반환
    
    - iterable에 문자열이 아닌 값 있으면 TypeError 발생

### 리스트(List)

- 리스트 메서드
  
  | 문법                     | 설명                                                          |
  | ---------------------- | ----------------------------------------------------------- |
  | L.append(x)            | 리스트 마지막에 항목 x를 추가                                           |
  | L.insert(i, x)         | 리스트 인덱스 i에 항목 x를 삽입                                         |
  | L.remove(x)            | 리스트가 가장 왼쪽에 있는 항목(첫 번째)x를 제거.<br/>항목이 존재하지 않을 경우 ValueError |
  | L.pop()                | 리스트 가장 오른쪽에 있는 항목(마지막)을 반환 후 제거                             |
  | L.pop(i)               | 리스트의 인덱스 i에 있는 항목을 반환 후 제거                                  |
  | L.extend(m)            | 순회형 m의 모든 항목들의 리스트 끝에 추가( +=과 같은 기능)                        |
  | L.index(x, start, end) | 리스트에 있는 항목 중 가장 왼족에 있는 항목 x의 인덱스를 반환                        |
  | L.reverse()            | 리스트를 거꾸로 정렬                                                 |
  | L.sort()               | 리스트를 정렬(매개변수 이용가능)                                          |
  | L.count(x)             | 리스트에서 항목x가 몇 개 존재하는지 갯수를 반환                                 |
  
  - `insert(i,x)`
    
    - 정해진 위치 i에 값을 추가한다
    
    - i가 리스트 길이보다 큰 경우는 맨 뒤에 넣는다
      
      ```python
      cafe = ['starbucks', 'tomntoms', 'hollys']
      cafe.insert(0, 'start')
      # ['start', 'starbucks', 'tomntoms', 'hollys', 'coffee']
      
      cafe.insert(len(cafe), 'end')
      # ['starbucks', 'tomntoms', 'hollys', 'coffee', 'end']
      
      cafe.insert(10000, 'start')
      # ['starbucks', 'tomntoms', 'hollys', 'coffee', 'end']
      ```
  
  - `.extend(iterable)`
    
    - 리스트에 iterable의 항목을 추가함
      
      ```python
      cafe = ['starbucks', 'tomntoms', 'hollys']
      cafe.extend(['coffee'])
      print(cafe)
      # ['starbucks', 'tomntoms', 'hollys', 'coffee']
      # cafe += ['coffee']와 같은 결과
      
      cafe.extend('coffee')
      print(cafe)
      # ['starbucks', 'tomntoms', 'hollys', 'c', 'o', 'f', 'f', 'e, 'e']
      # 문자열 'coffee'의 항목들이 추가됨
      ```
  
  - `.remove(x)`
    
    - 리스트에서 값이 x인 것 삭제
    
    - x가 없을 경우 ValueError
      
      ```python
      numbers = [1, 2, 3, 'hi']
      numbers.remove('hi')
      print(numbers) # [1, 2, 3]
      ```
  
  - `.pop(i)`
    
    - 정해진 위치i에 있는 값을 삭제하고, 그 항목을 반환함
    
    - i가 지정되지 않으면, 마지막 항목을 삭제하고 반환함
      
      ```python
      numbers = ['hi', 1, 2, 3]
      numbers.pop()
      print(numbers) # ['hi', 1, 2]
      
      numbers.pop(0)
      print(numbers) # [1, 2, 3]
      ```
  
  - `.clear()`
    
    - 모든 항목을 삭제함
      
      ```python
      numbers = [1, 2, 3]
      numbers.clear()
      print(numbers) # []
      ```
  
  - `.index(x)`
    
    - x값을 찾아 해당 index 값을 반환
    
    - 없는 경우 ValueError
      
      ```python
      numbers = [1, 2, 3, 4]
      print(numbers.index(3)) # 2
      ```
  
  - `.count(x)`
    
    - 원하는 값의 갯수를 반환함
      
      ```python
      numbers = [1, 2, 3, 1, 1]
      print(numbers.count(1)) # 3
      print(numbers.count(100)) # 0
      ```
  
  - `.sort()`
    
    - list에서만 사용하는 메서드
    
    - 원본 리스트를 정렬함. None 반환
      
      ⇒ 정렬된 것을 변수로 쓰지 않도록 주의!(None임)
    
    - sorted 함수와 비교할 것(원본 변경 없이 정렬된 리스트를 새로 만들어 반환)
    
    - 파라미터 : key, reverse
      
      - `.sort(reverse=True)`
      
      ```python
      numbers = [3, 2, 5, 1]
      result = numbers.sort()
      print(numbers, result) # [1, 2, 3, 5] None
      # 원본이 변경되고 None 값 반환
      
      result = sorted(numbers)
      print(numbers, result) # [3, 2, 5, 1] [1, 2, 3, 5]
      # 정렬된 리스트를 반환. 원본 변경 없음
      ```
  
  - `.reverse()`
    
    - 순서를 반대로 뒤집음(정렬x)
    
    - .sort()와 마찬가지로 원본을 변경하고 None을 반환함
      
      ```python
      numbers = [3, 2, 5, 1]
      result = numbers.reverse()
      print(numbers, result) # [1, 5, 2, 3] None
      ```

### 튜플(Tuple)

- 튜플 관련 메서드
  
  - 튜플은 값을 변경할 수 없기 때문에 값에 영향을 미치지 않는 메서드만을 지원
  
  - 리스트 메서드 중 항목을 변경하는 메서드들을 제외하고 대부분 동일
  
  - 인덱스 접근, 반복결합 연산자(*), 확장연산자(값을 병합해서 재할당) 가능
  
  - `.extend()`는 값을 변경하기 때문에 지원하지 않음.
    
    ```python
    day_name = ('월', '화', '수', '목', '금')
    
    # 인덱스로 접근
    print(day_name[-2]) # 목
    
    # 반복 결합 연산자
    print(day_name * 2)
    # ('월', '화', '수', '목', '금', '월', '화', '수', '목', '금')
    
    # 확장 연산자
    day_name += False, True
    # ('월', '화', '수', '목', '금', False, True)
    ```

## 순서가 없는 데이터구조(비시퀀스형)

### 셋(set)

| 문법              | 설명                                                       |
| --------------- | -------------------------------------------------------- |
| s.copy()        | 셋의 얕은 복사본을 반환                                            |
| s.add(x)        | 항목 x가 셋 s에 없다면 추가                                        |
| s.pop()         | 셋 s에서 랜덤하게 항목을 반환하고, 해당 항목을 제거<br/>set이 비어있을 경우 KeyError |
| s.remove(s)     | 항목 x를 셋 s에서 삭제<br/>항목이 존재하지 않을 경우 KeyError               |
| s.discard(x)    | 항목 x가 셋 s에 있는 경우 항목 x를 셋 s에서 삭제 (없어도 에러 발생하지 않음)         |
| s.update(t)     | 셋 t에 있는 모든 항목 중 셋 s에 없는 항목을 추가                           |
| s.clear()       | 모든 항목을 제거                                                |
| s.isdisjoint(t) | 셋 s가 셋 t의 서로 같은 항목을 하나라도 갖고 있지 않은 경우, True 반환            |
| s.issubset(t)   | 셋 s가 셋 t의 하위 셋인 경우, True 반환                              |
| s.issuperset(t) | 셋 s가 셋 t의 상위 셋인 경우, True 반환                              |

- `.add(elem)`
  
  - 셋에 값을 추가
    
    ```python
    a = {'사과', '바나나', '수박'}
    a.add('딸기')
    print(a) # {'바나나', '딸기', '사과', '수박'}
    ```

- `.update(*others)`
  
  - 여러 값을 추가
    
    ```python
    a = {'사과', '바나나', '수박'}
    a.add(['딸기', '바나나', '참외'])
    print(a) # {'참외', '바나나', '딸기', '사과', '수박'}
    ```

- `.pop()`
  
  - 임의의 원소를 제거해 반환
    
    ```python
    a = {'사과', '바나나', '수박'}
    a.pop()
    print(a) # {'사과', '수박'}
    ```

### 딕셔너리(Dictionary)

| 문법                           | 설명                                                                    |
| ---------------------------- | --------------------------------------------------------------------- |
| d.clear()                    | 모든 항목을 제거                                                             |
| d.copy()                     | 딕셔너리 d의 얕은 복사본을 반환                                                    |
| d.keys()                     | 딕셔너리 d의 모든 키를 담은 뷰를 반환                                                |
| d.values()                   | 딕셔너리 d의 모든 값을 담은 뷰를 반환                                                |
| d.items()                    | 딕셔너리 d의 모든 키-값의 쌍을 담은 뷰를 반환                                           |
| d.get(k)                     | 키 k의 값을 반환하는데, 키 k가 딕셔너리 d에 없을 경우 None을 반환                            |
| d.get(k, v)                  | 키 k의 값을 반환하는데, 키 k가 딕셔너리에 없을 경우 v를 반환                                 |
| d.setdefault(key,[, default] | 키 k의 값을 반환하는데, 키 k가 딕셔너리에 없을 경우 default 값을 갖는 키  k를 삽입한 후 default를 반환 |
| d.pop(v)                     | 키 k의 값을 반환하고 키 k인 항목을 딕셔너리 d에서 삭제하는데, 키 k가 딕셔너리에 없을 경우 KeyError 발생    |
| d.pop(k, v)                  | 키 k의 값을 반환하고 키 k인 항목을 딕셔너리 d에서 삭제하는데, 키 k가 딕셔너리 d에 없을 경우 v를 반환        |
| d.update([other])            | 딕셔너리 d의 값을 매핑하여 업데이트                                                  |

- `.get(key[,default])`
  
  - key를 통해 value를 가져옴
  
  - KeyError가 발생하지 않으며, default 값을 설정할 수 있음(기본:None)
    
    ```python
    my_dict = {'apple': '사과', 'banana': '바나나'}
    my_dict['pineapple'] # KeyError: 'pineapple'
    
    print(my_dict.get('pineapple') # None
    print(my_dict.get('apple') # 사과
    print(my_dict.get('pineapple', 0) # 0
    ```

- `.pop(key[,dafault])`
  
  - key 가 딕셔너리에 있으면 제거하고 해당 값을 반환
  
  - 그렇지 않으면 default를 반환
  
  - default값이 없으면 KeyError
    
    ```python
    my_dict = {'apple': '사과', 'banana': '바나나'}
    data = my_dict.pop('apple')
    print(data, my_dict) # 사과 {'banana': '바나나'}
    
    data = my_dict.pop('pineapple')
    print(data, my_dict) # KeyError: 'pineapple'
    
    data = my_dict.pop('pineapple', 0)
    print(data, my_dict) # 0 {'apple': '사과', 'banana': '바나나'}
    ```

- `.update()`
  
  - 값을 제공하는 key, value로 덮어씀
    
    ```python
    my_dict = {'apple': '사', 'banana': '바나나'}
    my_dict.update(apple='사과')
    print(my_dict) # {'apple': '사과', 'banana': '바나나'}
    ```
  
  - 자료가 있으면 수정을하고, 없으면 새로 추가한다.    
  
  - 여러개의 값을 한번에 수정가능
    
    
