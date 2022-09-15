> # 5174_subtree

```python
#1. 재귀함수를 통해 순회한 정점 수 리턴


import sys
sys.stdin = open('input.txt')

# 순회한 정점 수를 리턴하는 함수
def counting(n):
    if n == 0:      # 서브트리가 비어있다면
        return 0
    else:
        L = counting(ch1[n])
        R = counting(ch2[n])
        return L + R + 1

T = int(input())
for tc in range(1, T+1):
    E, root = map(int, input().split())
    arr = list(map(int, input().split()))
    V = E+1

    # 부모를 인덱스로 자식 번호 저장
    ch1 = [0]*(V+1)
    ch2 = [0]*(V+1)

    for i in range(E):
        p, c = arr[i*2], arr[i*2+1]
        if ch1[p] == 0:     # 아직 자식이 없으면
            ch1[p] = c      # 자식1로 저장
        else:
            ch2[p] = c

    print(f'#{tc} {counting(root)}')

```


