> # 4865_글자수

- 풀이



```python
#1.

import sys
sys.stdin = open('input.txt')

tc = int(input())

for t in range(1, tc+1):
    pattern = input()
    text = input()
    p_dict = {i: 0 for i in pattern}    # pattern의 각 문자를 딕셔너리의 key로 지정, value는 0으로 초기화
    
    # 딕셔너리의 key를 순회하며 text의 각 문자를 비교
    for i in p_dict:       # for i in pattern (x)
        for j in text:
            if i == j:
                p_dict[i] += 1          # key가 text의 각 문자와 같다면, 해당 key의 value를 1씩 증가시킨다.
    
    # 딕셔너리의 value 중 최대값 구하기
    maxV = 0
    for i in p_dict:
        if p_dict[i] > maxV:
            maxV = p_dict[i]

    result = maxV

    print(f'#{t} {result}')
```


