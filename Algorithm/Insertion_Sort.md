# 삽입 정렬 (Insertion Sort)
>삽입정렬은 현재 비교하고자 하는 target(타겟)과 그 이전의 원소들과 비교하며 자리를 교환하는 정렬 방법입니다.

## 정렬 과정
1. 현재 타겟이 되는 숫자와 이전 위치에 있는 원소들을 비교합니다. (처음은 두번째 원소부터 시작합니다)
2. 타겟이 되는 숫자가 이전 위치에 있던 원소보다 작다면 위치를 서로 교환합니다.
3. 그 다음 타겟을 찾아 위와 같은 방법으로 반복합니다.

## GIF로 이해하기

![삽입정렬](https://user-images.githubusercontent.com/37105602/213679428-aaa564af-2167-4432-8de4-08c7b07e7010.gif)

## 특징
* 공간 복잡도
    - 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)입니다.
* 시간 복잡도 
    - 최선의 경우 : 데이터가 이미 정렬된 케이스 - `O(n)`
        - 삽입정렬은 break 키워드가 존재합니다. 
        - 이미 정렬된 상태라면 원소의 바로 앞 원소와 비교 시 break 키워드를 통해 바로 for문을 탈출합니다.
        - 따라서 시간복잡도는 외부 for문에 의해 결정되어 O(n)입니다.
    - 최악의 경우 : 데이터가 역순으로 정렬되어 있는 케이스 - `O(n²)`
        - 역순으로 저장되어있는 데이터를 정렬하려면 매 사이클마다 첫 번째 원소까지 방문해서 데이터의 위치를 변경해야 합니다.
        - 탐색이 (n-1)번, (n-2)번 ... 1번 진행되므로 n(n-1)/2, 즉 O(n²)입니다.
    - 최선 : `O(n)`, 평균/최악 : `O(n²)`
### 장점
* Selection Sort나 Bubble Sort과 같은 O(n²) 알고리즘에 비교하여 상대적으로 빠릅니다.
* 대부분의 배열 값들이 이미 정렬되어 있는 경우에는 매우 효율적일 수 있습니다.
### 단점
* 평균과 최악인 상황에선 시간복잡도가 O(n²)이므로 비효율적입니다.
* 원소의 개수가 많아지면 비교 횟수가 많아져 성능이 저하 됩니다.


## 📌 예제 (Baekjoon)
[백준 - 수 정렬하기](https://www.acmicpc.net/problem/2750)

>문제

<img width="1058" alt="스크린샷 2023-01-18 오후 6 01 12" src="https://user-images.githubusercontent.com/37105602/213128316-d9ee24f1-88c2-4acd-bc3c-4db6ea27511b.png">

>풀이

힌트를 보면 시간복잡도가 O(n²)인 정렬 알고리즘으로도 풀 수 있습니다.  

### 코드(Python)
```Python
n = int(input())
numbers = []

for _ in range(n):
    numbers.append(int(input()))

# Insertion Sort
for i in range(1, n):
    for j in range(i, 0, -1):      
        if numbers[j - 1] > numbers[j]:       # 1. 
            numbers[j], numbers[j - 1] = numbers[j - 1], numbers[j]     # 2.

for n in numbers:
    print(n)
``` 
1. 이전 인덱스의 값과 현재 인덱스의 값을 비교합니다.
2. 작은 값을 앞으로 보내줍니다.

## Reference
- https://jinhyy.tistory.com/9
