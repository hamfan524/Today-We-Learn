# 백트래킹(Backtracking)

> `백트래킹(Backtracking) 알고리즘`은 조건을 만족하는 해를 찾기 위해서 선택 가능한 모든 경우의 수를 시도하며, 선택한 경로가 해결책으로 이어지지 않으면 이전 단계로 돌아가서 다른 경로를 시도하는 알고리즘입니다.

일반적으로 백트래킹 알고리즘은 [깊이 우선 탐색(DFS, Depth First Search)](./DFS%26BFS.md)을 기반으로 합니다.

## ❗특징

![image](https://user-images.githubusercontent.com/37105602/235315908-55a6ca39-68aa-4fb8-9173-ed32411544c5.png)

1. 제약 조건을 만족하는 모든 해를 찾는 것이 목표입니다.
2. 가능한 모든 경우의 수를 시도하며, 일단 해결책으로 이어지지 않으면 이전 단계로 돌아가서 다른 경우를 시도합니다.
3. 문제의 크기가 커질수록 불필요한 계산이 많아지기 때문에, 적절한 `가지치기(pruning) 기법`이 필요합니다.
4. 백트래킹은 불필요한 탐색을 하지 않는 부분에서, 모든 경우의 수를 탐색하는 `DFS 알고리즘`과는 차이점이 있습니다.

**※ 가지치기를 얼마나 잘하느냐에 따라 호율성이 결정됩니다.**

## ❗백트래킹 알고리즘

```Python
Backtrack(x)
    if x is not a solution
        return false
    if x is a new solution
        add to list of solutions
    backtrack(expand x)
```
## 📌 예제 (Baekjoon)
[백준 - N과 M(2)](https://www.acmicpc.net/problem/15650)

>문제
![image](https://user-images.githubusercontent.com/37105602/235316709-1198d71b-95c1-4c32-8fd6-dcf330ace36e.png)

>풀이

이 문제는 n개의 자연수 중에서 중복 없이 m개를 고르는 모든 경우를 출력하는 문제입니다.

`combinations 함수`를 사용하여 조합으로 쉽게 풀이가 가능하지만,  
`백트래킹`을 이용하여 코드를 작성해보겠습니다.

### 코드(Python)
```Python
n, m = map(int, input().split())

def backtracking(selected, depth):
    # 개수가 m과 같으면 출력
    if depth == m:
        print(' '.join(map(str, selected)))
        return
    
    # 현재까지 선택한 숫자들 중 가장 큰 숫자보다 큰 숫자들만 선택
    start = selected[-1] + 1 if selected else 1
    for i in range(start, n+1):
        backtracking(selected + [i], depth + 1)

backtracking([], 0)
```
