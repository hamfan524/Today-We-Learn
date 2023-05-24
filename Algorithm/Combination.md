# 조합(Combination)

```
조합이란 n 개의 숫자 중에서 r 개의 수를 순서 없이 뽑는 경우를 말한다.
```

<br>

ex) [1,2,3] 이라는 배열에서 2개의 수를 순서 없이 뽑으면<br>
```[1,2] [1,3] [2,3]``` 이렇게 3가지 나온다.<br>

순열을 뽑았을 때 나오는 ```[2, 1], [3, 1], [3, 2]``` 등은 중복이라 제거된다.<br><br><br>

```
여러 가지 방법이 있지만 핵심은 하나입니다.

배열을 처음부터 마지막까지 돌며

1. 현재 인덱스를 선택하는 경우
2. 현재 인덱스를 선택하지 않는 경우

이렇게 두가지로 모든 경우를 완전탐색 해주시면 됩니다.
```

<br><br>

## :one: 백트래킹

arr	- 조합을 뽑아낼 배열 <br>
output	- 조합에 뽑혔는지 체크하는 배열<br>
n	- 배열의 길이<br>
r	- 조합의 길이<br><br>

순열과 달리 조합은 r 을 유지할 필요가 없으므로 숫자를 하나 뽑을때마다 r 을 하나씩 줄여줍니다. <br>
r == 0 일 때가 r 개의 숫자를 뽑은 경우입니다.
<br>

```java
static void combination(int[] arr, boolean[] visited, int start, int n, int r) {
    if(r == 0) {
        print(arr, visited, n);
        return;
    } 

    for(int i=start; i<n; i++) {
        visited[i] = true;
        combination(arr, visited, i + 1, n, r - 1);
        visited[i] = false;
    }
}
```
<br><br>


## :two: 재귀

```java
static void comb(int[] arr, boolean[] visited, int depth, int n, int r) {
    if (r == 0) {
        print(arr, visited, n);
        return;
    }

    if (depth == n) {
        return;
    }

    visited[depth] = true;
    comb(arr, visited, depth + 1, n, r - 1);

    visited[depth] = false;
    comb(arr, visited, depth + 1, n, r);
}
```



