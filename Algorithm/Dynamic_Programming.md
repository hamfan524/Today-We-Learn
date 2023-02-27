# 동적계획법 (Dynamic Programming)

> 하나의 큰 문제를 여러 개의 작은 문제로 나누어서  
 그 결과를 저장하여 다시 큰 문제를 해결할 때 사용하는 방법

동적계획법, 즉 DP는 실행 시간을 줄이기 위해 많이 사용되는 수학적 접근 방식의 알고리즘 입니다.  
기본적으로 분할 정복 알고리즘과 비슷하지만 가장 큰 차이점은 **동적 계획법에서는 쪼개진 작은 문제가 중복**되고,  
 **분할 정복은 절대로 중복되지 않습니다.**

![image](https://user-images.githubusercontent.com/37105602/221555327-a7f06cfb-6fd5-4d91-94b2-524b7f3f7022.png)

## 조건
두 가지 조건을 만족해야 동적 계획법으로 문제풀이가 가능합니다.  
1. [Overlapping Subproblem](#1️⃣-overlapping-subproblems) : 겹치는 부분 문제
2. [Optimal Substructure](#2️⃣-optimal-substructure) :  최적 부분 구조

### 1️⃣ Overlapping Subproblems
DP는 기본적으로 문제를 나누고 그 문제의 결과 값을 재활용해서 전체 답을 구합니다.  
그래서 `동일한 작은 문제들이 반복하여 나타나는 경우에 사용 이 가능`합니다.

즉, DP는 부분 문제의 결과를 저장하여 재 계산하지 않을 수 있어야 하는데,  
해당 `부분 문제가 반복적으로 나타나지 않는다면 재사용이 불가능하니 부분 문제가 중복되지 않는 경우에는 사용할 수 없습니다.`

### 2️⃣ Optimal Substructure
`부분 문제의 최적 결과 값을 사용해 전체 문제의 최적 결과를 낼 수 있는 경우`를 의미합니다. 그래서 특정 문제의 정답은 문제의 크기에 상관없이 항상 동일합니다.

## 사용방법

DP는 `특정한 경우에 사용하는 알고리즘이 아니라 하나의 방법론이므로 다양한 문제해결에 쓰일 수 있습니다.`  
그래서 DP를 적용할 수 있는 문제인지를 알아내는 것부터 코드를 짜는 과정이 난이도가 쉬운 것부터 어려운 것까지 다양합니다.

1. DP로 풀 수 있는 문제인지 확인
2. 문제의 변수 파악
3. 변수 간 관계식 만들기(점화식)
4. 메모(memoization or tabulation)
5. 기저 상태 파악
6. 구현

## 메모이제이션(Memoization)
>한 번 계산한 문제는 다시 계산하지 않도록 저장해두고 활용하는 방식

### 예시) fibonacci함수
```
fibonacci(5) = fibonacci(4) + fibonacci(3)
fibonacci(4) = fibonacci(3) + fibonacci(2)
fibonacci(3) = fibonacci(2) + fibonacci(1)

이처럼 같은 연산이 계속 반복적으로 이용될 때, 메모이제이션을 활용하여 값을 미리 저장해두면 효율적
```
피보나치 구현에 재귀를 활용했다면 시간복잡도는 O(2^n)이지만, 동적 계획법을 활용하면 O(N)으로 해결할 수 있습니다.



## 구현 방식
동적 계획법의 구현 방식에는 두 가지 방법이 있습니다.
- **Top-down** : 큰 문제를 작은 문제로 쪼개어 푸는 방법 (재귀함수) 
- **Bottom-up** : 작은 문제부터 차근차근 구하는 방법 (반복문)

> Bottom-up 은 해결이 용이하지만, 가독성이 떨어짐  
Top-down은 가독성이 좋지만, 코드 작성이 어려움


## 📌예제 (Baekjoon)
[1로 만들기](https://www.acmicpc.net/problem/1463)
>문제
<img width="1057" alt="image" src="https://user-images.githubusercontent.com/37105602/221562187-88391cfb-d63c-439f-b8e8-507b82985e62.png">

>풀이

[Overlapping Subproblem](#1️⃣-overlapping-subproblems)와, [Optimal Substructure](#2️⃣-optimal-substructure) 2가지 조건을 모두 만족하므로,  
`DP`를 이용하여 풀이가 가능합니다.

일단, 2와 3으로 나누어 떨어지지 않는 경우는 무조건 1을 빼야 하기 때문에

dp[i] = dp[i - 1] + 1을 통해 횟수를 +1 추가 합니다.

그리고나서, dp[i]가 2 와 3으로 나누어 떨어지는 경우에는

1을 빼는 것 보다 나누어 떨어지는게 훨씬 이득이기 때문에

min(dp[i], dp[i//2]+1)을 통해 최소값을 선택하면 됩니다.

### 코드 (Python) - Bottom-up(반복문)
```Python
import sys
input = sys.stdin.readline

n = int(input())

dp = {
  0 : 0,
  1 : 0,
}

for i in range(2, n + 1):
  dp[i] = dp[i - 1] + 1

  if i % 2 == 0:
    dp[i] = min(dp[i], dp[i // 2] + 1)

  if i % 3 == 0:
    dp[i] = min(dp[i], dp[i // 3] + 1)

print(dp[n])
```
### 코드 (Python) - Up-down(재귀함수)
```Python
import sys
input = sys.stdin.readline

num = int(input())

dp = {
  0 : 0,
  1 : 0,
}

def rec(n):
    if n in dp.keys():
        return dp[n]
    if n % 3 == 0 and n % 2 == 0:
        dp[n] = min(rec(n//3) + 1, rec(n//2) + 1)
    elif n % 3 == 0:
        dp[n] = min(rec(n//3) + 1, rec(n-1) + 1)
    elif n % 2 == 0:
        dp[n] = min(rec(n//2) + 1, rec(n-1) + 1)
    else:
        dp[n] = rec(n-1) + 1
    return dp[n]

print(rec(num))
```

## Reference
https://velog.io/@polynomeer/%EB%8F%99%EC%A0%81-%EA%B3%84%ED%9A%8D%EB%B2%95Dynamic-Programming