```python
#1.

import sys
sys.stdin = open('input.txt')

tc  = int(input())

for t in range(1, tc+1):
    N, M = map(int, input().split())
    arr = [list(input()) for _ in range(N)]
    result = []


    # 행 순회
    for i in range(N):
        for j in range(N - M + 1):
            if arr[i][j:j + M] == arr[i][j:j + M][::-1]:
                result.append(''.join(arr[i][j:j + M]))

    # 열 순회
    for i in range(N-M+1):
        for j in range(N):
            column = []
            for k in range(M):
                column.append(arr[i + k][j])
            if column == column[::-1]:
                result.append(''.join(column))

    ans = ''.join(result)
    print(f'#{t} {ans}')
```
