> # 1216_회문2

- 풀이



```python
import sys
sys.stdin = open('input.txt')

def palindrome(arr):    # 회문 리스트를 구하는 함수를 작성
    pal_list = []       # 회문을 넣어줄 리스트
    for i in range(100):
        for k in range(1, 101):     # k = 회문의 길이(1~100까지)
            for j in range(100-k+1):
                if arr[i][j:j+k] == arr[i][j:j+k][::-1]:
                    pal_list.append(arr[i][j:j+k])

    return pal_list


for _ in range(10):
    t = input()
    arr = [list(input()) for _ in range(100)]
    zip_arr = list(zip(*arr))       # zip 함수를 통해 전치행렬을 구함

    all_pal_list = palindrome(arr) + palindrome(zip_arr)    # 행+열의 모든 회문이 담긴 리스트

    # 가장 긴 회문의 길이 구하기
    maxV = 0
    for i in range(len(all_pal_list)):  # 회문 리스트의 길이만큼 순회
        if len(all_pal_list[i]) > maxV:
            maxV = len(all_pal_list[i])

    result = maxV

    print(f'#{t} {result}')
```
