# 버블 정렬 (Bubble Sort)
> * 버블 정렬은 서로 인접한 두 원소를 비교하여 크기가 순서대로 되어 있지 않으면 서로 교환하며 정렬합니다.
> * 선택 정렬과 기본 개념이 유사합니다. 

## 정렬 과정

1. 첫 번째 원소부터 마지막 원소까지 차례대로 인접한 원소를 비교합니다.
2. 서로 비교하여 앞 원소가 더 크다면 서로 위치를 교환해줍니다.
3. 한 사이클이 완료가 되면, 해당 사이클에 마지막에 위치시킨 원소는 정렬이 완료된 것을 알 수 있습니다.
4. 이렇게 한 사이클을 수행할 때마다 마지막에 위치시킨 원소는 정렬이 완료되며 정렬에서 제외되는 데이터가 하나씩 늘어납니다.

## GIF로 이해하기
![버블정렬](https://user-images.githubusercontent.com/37105602/213360147-6407aaf7-da9e-4198-a39e-258f26e08f47.gif)

## 특징
* 공간 복잡도
    * 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)입니다.
* 시간 복잡도
    * 탐색이 (n-1)번, (n-2)번 ... 1번 진행되므로 n(n-1)/2, 즉 O(n²)입니다.
    * 최선, 평균, 최악의 경우 시간복잡도는 O(n²)으로 동일합니다.

### 장점
* 구현이 매우 간단하고, 소스코드가 직관적입니다.
* n개 원소에 대해 n개의 메모리를 사용하기에 데이터를 하나씩 정밀 비교가 가능합니다.
### 단점
* 최선이든 최악이든 O(n²)이라는 시간복잡도를 가지기 때문에 비효율적입니다.
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

# Bubble Sort
for i in range(n - 1): 
    for j in range(n - (i + 1)): 
        if numbers[j] >= numbers[j + 1]: # 1.
            numbers[j], numbers[j + 1] = numbers[j + 1], numbers[j] # 2.

for n in numbers:
    print(n)
```

1. 만약 앞의 원소가 뒤의 원소보다 크다면
2. 두 개의 자리를 바꿔줍니다.
## Reference
- https://jinhyy.tistory.com/9