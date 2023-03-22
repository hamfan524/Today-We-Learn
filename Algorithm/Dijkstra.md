# 다익스트라 (Dijkstra)

>Dijkstra의 알고리즘은 가중 그래프에서 시작 노드와 다른 모든 노드 사이의 최단 경로를 찾는 데 사용되는  그래프 검색 알고리즘입니다

## 검색 과정
1. 시작 노드의 거리를 0으로 설정하고 다른 모든 노드의 거리를 무한대로 설정하여 시작합니다. 
2. 그런 다음 우선 순위 대기열에 시작 노드를 추가합니다
3. 알고리즘을 반복할 때마다 우선순위 대기열에서 최소 거리를 가진 노드를 선택하고 인접 노드를 대기열에 추가하고 필요한 경우 거리를 업데이트합니다. 
4. 모든 노드를 방문할 때까지 프로세스가 계속됩니다.

## Gif로 이해하기

![dijkstra](https://user-images.githubusercontent.com/37105602/226551463-4e187de1-0f36-4fcb-8dc9-6fdf6d0f797b.gif)

## 특징

- [DP](./Dynamic_Programming.md)를 활용하는 최단 경로 탐색 알고리즘입니다.
- 각 반복에서 계산된 거리가 최적임을 보장합니다.  
- 즉, 지금까지 방문한 각 노드에 대한 최단 경로를 나타냅니다.  
- 알고리즘이 완료되면 그래프의 모든 노드까지의 거리를 읽을 수 있으며 거리가 가장 작은 노드를 역추적하여 두 노드 사이의 최단 경로를 찾을 수 있습니다.

컴퓨터 네트워크의 라우팅, 지도에서 도시 간의 최단 경로 찾기, 제조 프로세스의 일정 최적화와 같은 다양한 응용 프로그램에 널리 사용됩니다.

### 시간복잡도
- Dijkstra 알고리즘은 O(E log V)의 시간 복잡도를 가집니다.
>접점(V), 간선(E)

## 📌 예제 (Baekjoon)
[최소비용 구하기](https://www.acmicpc.net/problem/1916)

>문제

<img width="1121" alt="image" src="https://user-images.githubusercontent.com/37105602/226565753-4eff66af-8f15-478b-a9a4-258691ea6077.png">

>풀이

다익스트라를 구현하기 위해 두 가지를 저장해야 합니다.

- 해당 정점까지의 최단 거리를 저장

- 정점을 방문했는 지 저장

방향 그래프로 버스 노선을 입력하고, 효율적인 다익스트라 구현을 위해 우선순위 큐를 사용합니다.

### 코드
```Python
import sys
from heapq import heappush, heappop   # 우선순위 큐 

input = sys.stdin.readline
inf = sys.maxsize

# 입력
n = int(input())
m = int(input())
graph = [[] for _ in range(n + 1)]
dp = [inf] * (n + 1)
heap = []

def dijkstra(start):
    dp[start] = 0
    heappush(heap, [0, start])   # 시작 노드부터 탐색 시작
    while heap:
        w, n = heappop(heap)
        if  dp[n] < w:     # 기존 최단거리보다 멀다면 무시
            continue
        for n_n, wei in graph[n]:
            n_w = wei + w   # 인접노드까지의 거리
            if n_w < dp[n_n]:   # 기존 거리 보다 짧으면 갱신
                dp[n_n] = n_w
                heappush(heap, [n_w, n_n])  # 다음 인접 거리를 계산 하기 위해 큐에 삽입

for _ in range(m):
    d, a, v = map(int, input().split())
    graph[d].append([a, v])

d_c, a_c = map(int, input().split())

dijkstra(d_c)
print(dp[a_c])
```

## Reference

https://velog.io/@woonchoi/Dijkstra-%EB%8B%A4%EC%9D%B5%EC%8A%A4%ED%8A%B8%EB%9D%BC-%EC%B5%9C%EB%8B%A8%EA%B1%B0%EB%A6%AC