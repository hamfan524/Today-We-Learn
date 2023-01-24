# 퀵 정렬 (Quick Sort)
> 퀵 정렬은 병합정렬과 비슷하게 `분할정복 알고리즘`입니다.  
평균적으로 매우 빠른 속도를 자랑하는 정렬 방법입니다.

## 정렬 과정
1. 리스트 안에 있는 한 요소를 선택합니다. 이렇게 고른 원소를 `pivot(피벗)`이라고 합니다. **(선택 한 요소에 따라 속도가 달라집니다)**
2. pivot을 기준으로 pivot보다 작은 요소들은 모두 pivot의 왼쪽으로 옮기고, pivot보다 큰 요소들은 모두 pivot의 오른쪽으로 옮깁니다.
3. pivot을 제외한 왼쪽 리스트와 오른쪽 리스트를 다시 정렬합니다.  
    1) 분할된 왼쪽 리스트와 오른쪽 리스트도 다시 pivot을 정하고 pivot을 기준으로 2개의 부분리스트로 나눕니다.
    2) 재귀를 사용하여 부분 리스트들이 더 이상 분할이 불가능 할 때까지 반복합니다.

## GIF로 이해하기
![퀵정렬](https://user-images.githubusercontent.com/37105602/214249469-0944554f-4dac-4edb-9595-62d0037be9c6.gif)

## 특징
* 공간 복잡도
    - 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)입니다.

* 시간 복잡도
    - 두 그룹으로 분할하는데 `O(N)`의 시간이 걸리고 분할된 단계를 `O(logN)`만큼 수행하므로 평균 시간 복잡도는 `O(NlogN)`입니다.
    - 분할한 결과가 한쪽으로 몰리는 최악의 경우에는 `O(n²)`입니다.

### 장점
* 평균 속도가 매우 빠릅니다.
    - 시간 복잡도가 O(NlogN)을 가지는 다른 정렬 알고리즘과 비교했을 때도 가장 빠릅니다.
* 배열 안에서 위치만 교환하는 방식이기 때문에 추가적인 메모리 공간을 필요로 하지 않습니다.
### 단점
* 중복된 키값이 순서대로 바뀌지 않을 수 있어 `not-stable(불안정)`한 정렬입니다.
* 이미 정렬된 배열에서는 오히려 수행시간이 더 많이 걸리는 단점이 있습니다.

## 📌 예제 (Baekjoon)
[백준 - 수 정렬하기](https://www.acmicpc.net/problem/2750)

>문제

<img width="1058" alt="스크린샷 2023-01-18 오후 6 01 12" src="https://user-images.githubusercontent.com/37105602/213128316-d9ee24f1-88c2-4acd-bc3c-4db6ea27511b.png">

>풀이  

입력 값들을 오름차순으로 정렬하는 문제입니다.  
퀵 정렬 알고리즘을 이용하여 정렬합니다.

### 코드(Python)
```Python
def quick_sort(arr):
    def sort(low, high):    
        if high <= low:
            return
        mid = partition(low, high)
        sort(low, mid - 1)
        sort(mid, high)

    def partition(low, high):
        pivot = arr[(low + high) // 2]
        while low <= high:
            while arr[low] < pivot:
                low += 1
            while arr[high] > pivot:
                high -= 1
            if low <= high:
                arr[low], arr[high] = arr[high], arr[low]
                low += 1
                high -= 1
        return low

    return sort(0, len(arr) - 1)

n = int(input())
numbers = []

for _ in range(n):
    numbers.append(int(input()))

quick_sort(numbers)

for n in numbers:
    print(n)
```

- 리스트의 정 가운데 있는 값을 pivot 값으로 선택합니다.
- 시작 인덱스(low)는 계속 증가시키고, 끝 인덱스(high)는 계속 감소시키기 위한 while루프를 두 인덱스가 서로 교차해서 지나칠 때까지 반복합니다.
- 시작 인덱스(low)가 가리키는 값과 pivot 값을 비교해서 더 작은 경우 반복해서 시작 인덱스 값을 증가시킵니다. (pivot 값보다 큰데 좌측에 있는 값을 찾기 위해)
- 끝 인덱스(high)가 가리키는 값과 pivot값을 비교해서 더 큰 경우 반복해서 끝 인덱스 값을 감소시킵니다. (pivot 값보다 작은데 우측에 있는 값을 찾기 위해)
- 두 인덱스가 아직 서로 교차해서 지나치지 않았다면 시작 인덱스(low)가 가리키는 값과 끝 인덱스(high)가 가리키는 값을 상호 교대(swap)시킵니다. (잘못된 위치에 있는 두 값의 위치를 바꾸기 위해)
- 상호 교대 후, 다음 값을 가리키기 위해 두 인덱스를 각자 진행 방향으로 한 칸씩 이동 시킵니다.
- 두 인덱스가 서로 교차해서 지나치게 되어 while 루프를 빠져나왔다면 다음 재귀 호출의 분할 기준점이 될 시작 인덱스를 리턴합니다.

## Reference
- https://jinhyy.tistory.com/9
- https://www.daleseo.com/sort-quick/
