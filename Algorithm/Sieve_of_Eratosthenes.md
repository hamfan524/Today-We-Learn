# 에라토스테네스의 체 (sieve of Eratosthenes) 

```
수학에서 에라토스테네스의 체는 소수를 찾는 방법이다. 
고대 그리스 수학자 에라토스테네스가 발견하였다.
코딩 알고리즘에서 소수를 구할 때도 이 방법을 사용합니다.
```
<br><br>

## :exclamation: 에라토스테네스의 체 이해하기

```
소수가 되는 수의 배수를 지우면 남은 건 소수가 된다는 알고리즘
```
<br>
아래는 위키백과에 나온 에라토스테네스의 체를 구하는 방법입니다.<br>


<img width = 400 src=https://user-images.githubusercontent.com/96968834/230614183-225c4eaa-25e9-4d31-9af6-ded7b43b0080.png>

<image src=https://user-images.githubusercontent.com/96968834/230613914-44bd296a-f490-4c5d-b36e-621680b1e678.gif>

<br><br>


## 코드 및 해설

```java
import java.io.*;

public class Algorithm {

    static boolean[] isPrime;
    
    static void isPrime(int n){ 
        isPrime = new boolean[n+1]; // N번째의 수 까지 받기위해 N+1까지 동적할당
        
        for(int i = 0; i < isPrime.length; i++){
            isPrime[i] = true; // boolean배열의 default값은 false이므로 true로 바꿔주기
        }
        
        isPrime[0] = isPrime[1] = false; // 0과 1은 소수가 아니니깐 false
        
        for(int i = 2; i <= Math.sqrt(n); i++){ // 2부터 n의 제곱근까지의 모든 수를 확인
            if(isPrime[i]){ // 해당수가 소수라면, 해당수를 제외한 배수들을 모두 false 처리하기
                for(int j = i*i; j<= n; j += i){//그 이하의 수는 모두 검사했으므로 i*i부터 시작
                    isPrime[j] = false;
                }
            }
        }
    } // isPrime 함수 종료  // 시간복잡도는 O(n loglogn) 입니다.
```



## reference
- https://firework-ham.tistory.com/8
