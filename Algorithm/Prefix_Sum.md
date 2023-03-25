# 누적합 

```
- 배열의 일부 구간에 대한 합을 빠르게 구할 수 있게 해주는 스킬

- n개의 원소로 이루어진 배열이 주어졌을 때 반복문을 통해 배열의 합을 구하려면 O(n)이 걸리는데 
  부분합을 이용하면 모든 부분합을 O(1)에 바로 구하기 가능

- 누적합은 문제에서 수열이 주어지고 어떤 구간의 값의 합을 구해야 할 때 쓰일 수 있습니다.
```


## :one: 1차원 배열


ex) 다음과 같은  배열이 있다고 가정하자.
```
arr = [2 , 5 , 1 , 4 , 3 , 2]

sum = [2 , 7 , 8 , 12 , 15 , 17]
```
위 배열에서 연속된 구간의 합, 예를들어 arr[2]부터 arr[4]까지의<br>
합을 구하려고 한다면 3개의 원소값을 참조해야한다.

이러한 점을 보완하기 위해서 누적합 수열 sum을 도입한다.
<br><br>
:exclamation: sum[R]는 arr[0]부터 arr[R]까지의 모든 원소의 합을 값으로 갖는다. 또한 arr[L]부터 arr[R]까지의 부분합은 sum[R] - sum_list[L-1]로 정의할 수 있다.

<img src=https://user-images.githubusercontent.com/96968834/226092240-b5d13b83-4e56-4acb-9ebc-363b4f3b952d.JPG>

<br><br>

## :two: 2차원 배열

<br>

```
빨간 부분 (3, 3)부터 (5, 5)의 합을 어떻게 구할 수 있을까?
 prefixSum[5][5]는 (1,1)부터 (5,5)까지의 합을 나타내므로 해당 부분에서 
 저 녹색 부분(prefixSum[2,5])을 빼주고, 노란 부분(prefixSum[5][2])을 빼주고, 
 두번 빠진 녹색과 노란색이 만나는 부분(prefixSum[2][2])를 한번 더 더해주면 될 것이다.


즉, (3,3)부터 (5,5)까지의 2차원 구간합 = prefixSum[5][5] -
prefixSum[5][3-1] - prefixSum[3-1][5] + prefixSum[3-1][3-1] = 36
```
<img src=https://user-images.githubusercontent.com/96968834/227722437-deb678ae-f69c-43bf-80f5-aa499acb02a7.png>


```
(x1, y1)부터 (x2, y2) 까지(x1<=x2, y1<=y2)라고 보면 
구하고자 하는 2차원 구간합

prefixSum[x2][y2] - prefixSum[x2][y1-1] - prefixSum[x1-1][y2] + prefixSum[x1-1][y1-1]
```




<br><br>

## 풀어볼만한 문제들


1. 백준 10986 나머지합
https://www.acmicpc.net/problem/10986

2. 백준 11660 구간 합 구하기5
https://www.acmicpc.net/problem/11660

<br>

 --------------- 
## Reference

https://nahwasa.com/entry/%EB%88%84%EC%A0%81-%ED%95%A9prefix-sum-2%EC%B0%A8%EC%9B%90-%EB%88%84%EC%A0%81%ED%95%A9prefix-sum-of-matrix-with-java

