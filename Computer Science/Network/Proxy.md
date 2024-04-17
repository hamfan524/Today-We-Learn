# Proxy

```
프록시 서버는 클라이언트가 자신을 통해 다른 네트워크 서비스에 간접적으로 
접속할 수 있게 해주는 서버

==> 프록시(Proxy)란 '대리' 라는 의미를 갖고 있으며, 서버와 서버사이의 중계기 역할
```
<img width =800 src="https://github.com/minwoogi/Android_Kotlin_info/assets/96968834/038ab6ab-295e-4498-b410-c31a3ce99c4d">

<br><br>

## 사용이유 :hammer:

프록시를 쓰는 이유는 보안상의 이유로 직접 통신할 수 없는 두 점사이에서 대리로 통신을 수행하여 <br>
보안성, 성능, 안정성을 향상 시키기 위해서 사용<br>


```
보통 웹은 클라이언트에서 서버로, 서버에서 클라이언트로 통신하며 데이터를 전달한다.
이때 필연적으로 중복되는 데이터를 반복하여 전달하는 상황이 발생하는데, 

-> 이렇게 동일한 요청을 매번 처리하는 것은 곧 리소스 낭비 와 서버의 부하 로 이어지게 된다.
때문에 본 서버에 도달하기 전에 새로운 서버(proxy server)를 미리 배치하여 중복 요청에
대해 (연산이 필요없는) 동일한 응답을 할 수 있다면, 클라이언트에겐 빠른 속도의 서비스를,
서버에게는 불필요한 부하를 줄이는 효과를 낼 수 있다.
```

<br><br>

## Proxy 종류

```1``` Forward Proxy<br>

```2``` Reverse Proxy<br>

<br><br>


## Forward Proxy

```
사용자가 google.com 에 연결하려고 하면 사용자 PC 가 직접 연결하는게 아니라 포워드 프록시 서버가 요청을 받아서  
google.com 에 연결하여 그 결과를 클라이언트에 전달(forward) 해 줍니다.

포워드 프록시는 대개 캐슁 기능이 있으므로 자주 사용되는 컨텐츠라면 월등한 성능 향상을 가져올 수 있으며 
정해진 사이트만 연결하게 설정하는 등 웹 사용 환경을 제한할수 있으므로 
보안이 매우 중요한 기업 환경등에서 많이 사용합니다.
```
<img witdh=800 src="https://github.com/minwoogi/Android_Kotlin_info/assets/96968834/21359c8d-55e1-4bc4-abe3-672e6d126c21">


<br><br>

## Reverse Proxy

```
리버스 프록시는 아래 그림 처럼 웹서버/WAS 앞에 놓여 있는 것을 말합니다. 
클라이언트는 웹서비스에 접근할때 웹서버에 요청하는 것이 아닌, 프록시로 요청하게 되고, 
프록시가 배후(reverse)의 서버로부터 데이터를 가져오는 방식입니다.
클라이언트쪽으로 데이터(response)를 밀어주는게 포워드라면, 그 반대편인 서버 쪽으로 데이터(request)를 밀어주는 것이 리버스 프록시 라고 합니다.

```
<img witdh=800 src="https://github.com/minwoogi/Android_Kotlin_info/assets/96968834/a21e258d-9dd5-4bf4-b2d9-1c6cd90c8b36">


<br><br>



---
출처
https://inpa.tistory.com/entry/NETWORK-%F0%9F%93%A1-Reverse-Proxy-Forward-Proxy-%EC%A0%95%EC%9D%98-%EC%B0%A8%EC%9D%B4-%EC%A0%95%EB%A6%AC
