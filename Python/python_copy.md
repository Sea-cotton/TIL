> # 얕은 복사와 깊은 복사

### 복사 방법

- 할당
  
  - 대입 연산자(=)
    
    - 대입 연산자를 통한 복사는 해당 객체에 대한 객체 참조를 복사
    
    - 해당 주소의 일부 값을 변경하는 경우 이를 참조하는 모든 변수에 영향
      
      ⇒ 얕은 복사를 통해 해결(Slice 연산자)
      
      ```python
      original_list = [1, 2, 3]
      copy_list = original_list
      print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]
      
      copy_list[0] = 'hello'
      print(original_list, copy_list) # ['hello', 2, 3] ['hello', 2, 3]
      # copy_list의 값만 바꿨는데 original_list에도 영향을 미침
      
      # 얕은 복사
      original_list = [1, 2, 3]
      copy_list = original_list[:]
      print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]
      
      copy_list[0] = 'hello'
      print(original_list, copy_list) # [1, 2, 3] ['hello', 2, 3]
      ```
  
  ### 얕은 복사(shallow coppy)
  
  - Slice 연산자를 활용하여 같은 원소를 가진 리스트지만 연산된 결과를 복사(다른 주소)
    
    ```python
    a = [1, 2 ['a', 'b']]
    b = a[:]
    print(a, b) # [1, 2, 3] [1, 2, 3]
    
    b[0] = 5
    print(a, b) # [1, 2, 3] [5, 2, 3]
    ```
  
  - 주의사항
    
    - 복사하는 리스트의 원소가 주소를 참조하는 경우
    
    - 1차원에서만 가능함 : 리스트 안에 리스트가 있으면 또 주소를 복사하기 때문에
      
      ```python
      a = [1, 2, ['a', 'b']]
      b = a[:]
      print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]
      
      b[2][0] = 0
      print(a, b) # [1, 2, [0, 'b'] [1, 2, [0, 'b']]
      ```
  
  ### 깊은 복사(deep copy)
  
  - 얕은 복사의 문제점 해결(이차원 복사 가능)
  
  - 주소가 아니라 있는 그대로 복사한다.
    
    ```python
    import copy
    a = [1, 2 ['a', 'b']]
    b = copy.deepcopy(a)
    print(a, b) # [1, 2 ['a', 'b']] [1, 2 ['a', 'b']]
    
    b[2][0] = 0
    print(a, b) # [1, 2 ['a', 'b']] [1, 2, [0, 'b']]
    ```
    
    ```python
    import copy
    
    a = [[1, 2, 3], [4, 5, 6]], [7, 8, 9]]
    b = copy.deepcopy(a)
    print(a, b) # [[1, 2, 3], [4, 5, 6]], [7, 8, 9]] [[1, 2, 3], [4, 5, 6]], [7, 8, 9]]
    
    b[0][2] = 'hello'
    print(a, b) # [[1, 2, 3], [4, 5, 6]], [7, 8, 9]] [[1, 2, 'hello'], [4, 5, 6]], [7, 8, 9]]
    ```
    
    


