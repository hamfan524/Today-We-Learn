# 힙 정렬
완전 이진 트리를 기본으로 하는 [힙(Heap)](../Data%20Structure/Heap.md) 자료구조를 기반으로한 정렬 방식입니다.  
최대 힙 트리나 최소 힙 트리를 구성해서 정렬을 합니다.

*완전 이진 트리란?*
> 삽입할 때 왼쪽부터 차례대로 추가하는 이진 트리

## 정렬 과정
1. 정렬해야 할 n개의 요소를 최대 또는 최소 힙으로 구성합니다.(완전 이진 트리 형태)
2. 현재 힙 루트는 최댓값 또는 최솟값이 존재합니다. 루트의 값을 마지막요소(말단 노드와 바꾼 후에, 힙의 사이즈를 하나 줄입니다.
3. 힙의 사이즈가 1보다 크면 위 과정들을 반복합니다.

## GIF로 이해하기
![heapsort2](https://user-images.githubusercontent.com/37105602/214554718-564e9161-2fa6-4ae2-869c-7a1e97db44c5.gif)


## 특징
* 공간 복잡도
    - 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)입니다.
* 시간 복잡도 
    - 힙 구조 생성시 연산 수는 힙의 높이와 동일하므로 O(logN)이 됩니다.
    - 따라서 힙 정렬의 전체 시간 복잡도는 힙 생성(Heapify)알고리즘 시간 복잡도 **O(logN)** * 전체 데이터 수 **N** = `O(NlogN)` 입니다.

### 장점
* 최악의 상황에도 시간복잡도가 O(NlogN)이라 성능이 좋습니다.
* 가장 큰 값이나 가장 작은 값을 구할 때 유용합니다.
### 단점
* 일반적으로 속도만 비교하면 [퀵 정렬](./Quick_Sort.md)이 평균적으로 더 빠릅니다. 그래서 자주 사용하지 않습니다.
## 📌 예제 (Baekjoon)
[백준 - 수 정렬하기](https://www.acmicpc.net/problem/2750)

>문제

<img width="1058" alt="스크린샷 2023-01-18 오후 6 01 12" src="https://user-images.githubusercontent.com/37105602/213128316-d9ee24f1-88c2-4acd-bc3c-4db6ea27511b.png">

>풀이  

입력 값들을 오름차순으로 정렬하는 문제입니다.  
최대 힙을 이용하여 HeapSort로 정렬합니다.
### 코드(Python)
```Python
def heap_sort(arr):
    n = len(arr)
    for i in range(n//2 - 1, -1, -1):       # 최대 힙 초기화
        heapify(arr, n, i)
    for i in range(n-1, 0, -1):     # extract 연산
        swap(arr, 0, i)
        heapify(arr, i, 0)

def heapify(arr, n, i):
    p = i
    l = i * 2 + 1
    r = i * 2 + 2

    if l < n and arr[p] < arr[l]:   # 왼쪽 자식노드
        p = l
    if r < n and arr[p] < arr[r]:   # 오른쪽 자식노드
        p = r 
    if i != p:                      # 부모노드 < 자식노드
        swap(arr, p, i)
        heapify(arr, n, p)

def swap(arr, a, b):    # 요소 교환
    arr[a], arr[b] = arr[b], arr[a]

n = int(input())
numbers = []

for _ in range(n):
    numbers.append(int(input()))

heap_sort(numbers)

for n in numbers:
    print(n)
```

## Reference
[자료구조 - 힙(Heap)](../Data%20Structure/Heap.md)  
https://www.codesdope.com/course/algorithms-heapsort/