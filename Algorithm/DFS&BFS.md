# DFS & BFS
그래프 알고리즘으로, 경로를 찾는 문제에서 자주 사용됩니다.

## 깊이 우선 탐색 (DFS, Depth-First Search)
>Root Node 혹은 다른 임의의 Node에서 다음 분기(Branch)로 넘어가기 전에 해당 Branch를 완벽하게 탐색하는 방법입니다.

### 특징
* `Stack` 또는  `Deque`, `재귀함수`를 이용하여 구현합니다.
* 경로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게되면 다른 방향으로 다시 탐색을 진행합니다.
* 모든 노드를 방문하는 경우에 이 방법을 사용합니다.

### 시간복잡도 
* 인접 리스트 : O(V + E)
* 인접 행렬 : O(V^2)
>접점(V), 간선(E)

### Gif로 이해하기

![Depth-First-Search](https://user-images.githubusercontent.com/37105602/220048244-6d907432-21ac-4c3d-948c-4087a0c7c2a4.gif)


## 너비 우선 탐색 (BFS, Breadth-First Search)
>루트노드 또는 다른 임의의 노드에서 인접한 노드를 먼저 탐색하는 방법입니다.

### 특징
* `Queue` 또는 `Deque`를 이용하여 구현합니다.
* 모든 노드를 방문하는 경우보다는 주로 두 노드 사이의 최단 경로를 찾고 싶을 때 이 방법을 선택합니다.

### 시간복잡도
* 인접 리스트 : O(V + E)
* 인접 행렬 : O(V^2)
>접점(V), 간선(E)

### Gif로 이해하기

![Breadth-First-Search-Algorithm](https://user-images.githubusercontent.com/37105602/220048310-bd3bc245-5169-4f4b-b637-62e6d5094786.gif)

## 📌예제 (Baekjoon)
[바이러스](https://www.acmicpc.net/problem/2606)

>문제

<img width="1042" alt="image" src="https://user-images.githubusercontent.com/37105602/220061351-037a6c71-f27b-4679-9d4e-175d6eaece45.png">

>풀이  

1번 컴퓨터와 연결된 컴퓨터들을 찾는  `연결 요소 찾기 문제`입니다.  
그것을 싸잡아 하나의 연결 요소라고 합니다. DFS와 BFS 둘 다로 풀 수 있는 적당한 난이도의 문제로, 그래프 탐색 연습하기 좋은 문제 입니다.

* DFS - 재귀함수
* BFS - Deque

### DFS 코드
```Python
read = sys.stdin.readline

def dfs(start, dic):
  visited.append(start)
  for i in dic[start]:
    if i not in visited:
      dfs(i, dic)
  return len(visited) - 1

dic = {}
visited = []

for i in range(int(read())):
  dic[i + 1] = set()

for _ in range(int(read())):
  a, b = map(int, read().split())
  dic[a].add(b)
  dic[b].add(a)

print(dfs(1,dic))
```

### BFS 코드
```Python
from collections import deque
import sys
read = sys.stdin.readline

def bfs(start, dic):
  q = deque()
  q.append(start)

  while q:
    start = q.popleft()
    for i in dic[start]:
      if i not in visited:
        visited.append(i)
        q.append(i)

  return len(visited) - 1

dic = {}
visited = []

for i in range(int(read())):
  dic[i + 1] = set()
for _ in range(int(read())):
  a, b = map(int, read().split())
  dic[a].add(b)
  dic[b].add(a)

print(bfs(1, dic))
```


## Reference
https://developer-mac.tistory.com/64