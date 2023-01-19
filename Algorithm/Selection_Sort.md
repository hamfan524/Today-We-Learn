# 선택 정렬 (Selection Sort)
> 선택정렬은 현재 위치에 들어갈 값을 찾아서 바꾸는 알고리즘입니다.

## 정렬 과정

1. 현재 정렬되지 않은 가장 맨 앞의 인덱스를 선택한다.
2. 현재 인덱스의 다음 인덱스부터 끝까지 가장 작은 값을 찾으면 현재 인덱스의 값과 바꿔준다.
3. 다음 인덱스에서 위 과정을 반복한다.

## GIF으로 이해하기
![선택정렬](https://user-images.githubusercontent.com/37105602/213121599-b4e758f5-4f16-4dce-a141-aecf7da2d0ec.gif)

## 특징
* 공간 복잡도
    - 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)입니다.
* 시간 복잡도 
    - 탐색이 (n-1)번, (n-2)번 ... 1번 진행되므로 O(n²)입니다.
    - 최선, 평균, 최악의 경우 시간복잡도는 O(n²)으로 동일합니다.

### 장점
- 선택정렬 또한 버블정렬과 마찬가지로 구현이 쉬운편에 속하는 정렬법입니다.
- 정렬을 위한 비교 횟수는 많지만 실제로 교환하는 횟수는 적기 때문에 교환이 일어나야 하는 자료상태에서 효율적으로 사용될 수 있습니다.
- 버블정렬과 비교했을 때, 시간복잡도는 같지만 실제로 시간을 측정해보면 버블 정렬에 비해 조금 더 빠른 정렬 방식입니다.

### 단점
- 항상 O(n²)이라는 시간복잡도를 갖기 때문에 시간이 오래걸리는 정렬 방식입니다.

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

# Selection Sort
for i in range(n):                      
    for j in range(i + 1, n):           
        if numbers[i] > numbers[j]:     
            numbers[i], numbers[j] = numbers[j], numbers[i]
            
for n in numbers:
    print(n)
```

## Reference
- https://jinhyy.tistory.com/9
