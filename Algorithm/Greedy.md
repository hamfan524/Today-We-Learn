# 그리디 (Greedy)
> - 그리디 알고리즘은 탐욕 알고리즘 또는 욕심쟁이 알고리즘이라고도 불립니다.  
>- ```미래를 생각하지 않고 각 단계에서 가장 최선의 선택을 하는 기법```입니다.  
>- 그렇기 때문에 최종적인 결과 도출에 대한 최적해를 보장해주는 것은 아닙니다.

## 각 단계에서 가장 최선의 선택이란
>그리디 알고리즘의 각 단계에서 최선의 선택 예시를 보겠습니다.

<img width="600" alt="1f" src="https://user-images.githubusercontent.com/37105602/212823411-e4795758-69fb-4405-8df8-c5f2b7f50514.png">

문제) 시작노드로부터 시작하여 거쳐가는 노드 값의 합이 최대인 경우의 결과값을 구하시오.
* 최적의 해와 그리디의 결과 값이 달라지는 걸 볼 수 있습니다.
* 우리는 가장 좋은 결과가 ```'시작 - 6 - 56'```을 거치는 경로가 가장 큰 수를 도출하는 것을 알 수 있습니다.
* 하지만 그리디 알고리즘을 사용하면 시작 노드에서부터 가장 큰 수인 '20'을 선택하게 됩니다.
* 결론적으로 그리디 알고리즘은 ```'시작 - 20 - 17'```를 가장 최대인 경우로 선택하게 됩니다.

이처럼 그리디 알고리즘은 현재 상황에서 가장 좋은 결과를 선택하는 방식입니다.  
이런 이유 때문에 그리디 알고리즘을 사용하는 문제는 간단한 문제로 나올 가능성이 매우 큽니다.

## 그리디 알고리즘의 정당성
그리디 알고리즘으로 최적해를 도출하기 위해서는 두가지 조건을 만족해야 합니다.
1. 탐욕적 선택 속성 (greedy choice property)  
탐욕적인 선택이 항상 안전하다는 것이 보장된다는 의미입니다.  
 즉, 그리디한 선택이 언제나 최적해를 보장해야 합니다.
2. 최적 부분 구조 (optimal substructure)
부분 최적해(Local optimum)들이 모여 전체 최적해(Global optimum)를 구할 수 있는 경우입니다.  
즉, 전체 문제가 여러부분 문제로 분할되며, 이 단계 하나하나에 대한 최적해가 도출되어야 한다는 의미입니다.


## 📌예제 (Baekjoon)
[백준 - 동전 0](https://www.acmicpc.net/problem/11047)

>문제

<img width="1200" alt="1f" src="https://user-images.githubusercontent.com/37105602/212828615-6321a8fe-b1b3-4b69-870f-08e90cefa1e9.png">

>풀이  

입력으로 들어온 동전들을 사용하여 K원을 만드는데 필요한 ```동전 개수의 최솟값```을 출력하는 것이 목적입니다.
1. i >= 2 인 경우에 Ai는 Ai-1의 배수이기 때문에 그리디 알고리즘을 사용하는 문제입니다.
2. ```가장 큰 동전부터 시작해서 몫을 카운트해주고, 나머지 동전을 내림차순으로 반복```합니다.
3. 이때 K가 0이 되면, 반복문을 빠져나옵니다.

동전|K|동전의 수|나머지
---|---|---|---
50000|4200|0|4200
10000|4200|0|4200
5000|4200|0|4200
1000|4200|```4```|200
500|200|0|200
100|200|```2```|0
50|0|-|-
10|-|-|-
5|-|-|-
1|-|-|-

### 코드
```Python
n, k = map(int, input().split())

money = []
count = 0

for i in range(n):
  m = int(input())
  money.append(m)

for i in reversed(money):
  if i <= k:
    count += k // i
    k = k % i

print(count)
```