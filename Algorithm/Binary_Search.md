# 이분탐색 (Binary Search)
>`정렬되어 있는(이분 탐색의 주요 조건) 배열`에서 데이터를 찾으려 시도할 때,   
>순차탐색처럼 처음부터 끝까지 하나씩 모든 데이터를 체크하여 값을 찾는 것이 아니라  
>**탐색 범위를 절반씩 줄여가며 찾아가는 Search 방법**입니다.

## 탐색 과정
- 우선 정렬되어 있는 배열이어야 합니다.
- `low`와 `high`로 `mid`값을 설정합니다.
- `mid`와 내가 구하고자 하는 값과 비교합니다.
- 구할 값이 `mid`보다 높으면 : `low` = `mid + 1`  
 구할 값이 `mid`보다 낮으면 : `high` = `mid - 1`
- `low` > `high`가 될 때까지 계속 반복합니다.


## Gif로 이해하기
![binary-and-linear-search-animations](https://user-images.githubusercontent.com/37105602/216249926-49944a28-221c-4845-89d6-249bb17df83c.gif)

## 특징
* 시간복잡도  
유한 정렬 배열의 크기를 N이라 하면,  
배열 내에 탐색 값이 없는 최악의 경우,  
N 1/2 1/2 * 1/2... 으로 범위 내 원소가 하나가 될 때까지 진행하므로  
`N*(1/2)K = 1 -> K = log2N`으로 수식화 할 수 있고,  
양 변에 2K를 곱하고 log2를 취하여 정리하면  
`O(log2N)`으로 시간 복잡도를 나타낼 수 있습니다.

## 📌 예제 (Baekjoon)
[백준 - 수 찾기](https://www.acmicpc.net/problem/1920)

>문제
![image](https://user-images.githubusercontent.com/37105602/216254323-30972d7a-bbd2-4e66-86d7-b24bc9b56500.png)

>풀이

n개의 정수가 들어있는 집합 A안에  
다른 m개의 정수가 포함되어 있는지 확인하는 문제입니다.

집합 자료형을 사용하면 간단하게 풀 수 있지만, 이분탐색을 사용하여 해결해보겠습니다.
### 코드(Python)
```Python
def binary(l, nList, low, high):
    if low > high:
        return 0
    mid = (low + high) // 2
    if l == nList[mid]:
        return 1
    elif l < nList[mid]:
        return binary(l, nList, low, mid - 1)
    else:
        return binary(l, nList, mid + 1, high)

n = int(input())
A = sorted(map(int, input().split()))
m = input()
M = map(int, input().split())

for l in M:
    low = 0
    high = len(A) - 1
    print(binary(l, A, low, high))
```
index를 기준으로 low high를 나누고

이분탐색의 탐색 종료 조건은 

mid 값이 찾으려는 수랑 같으면 return 을 해주고

찾는 값이 없을때 low가 high보다 커질경우 종료합니다.

 
## Reference
https://www.penjee.com  
https://kangworld.tistory.com/65