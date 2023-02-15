# Database Key
**Key** : 검색, 정렬시 Tuple(튜플)을 구분할 수 있는 기준이 되는 Attribute(속성)

튜플 : 릴레이션을 구성하는 각각의 행, 속성의 모임으로 구성됩니다.  
파일 구조에서는 레코드와 같은 개념, **튜플의 수 = 카디널리티(Cardinality)** = 기수 = 대응수 

## 종류
![image](https://user-images.githubusercontent.com/37105602/218786671-a8e77cb2-03a4-4c34-a4d5-f823523fe86e.png)

1. [후보키](#후보키candidate-key)
2. [기본키](#기본키primary-key)
3. [대체키](#대체키alternate-key)
4. [슈퍼키](#슈퍼키super-key)
5. [외래키](#외래키foreign-key)

## 후보키(Candidate Key)
>Tuple을 유일하게 식별하기 위해 사용하는 속성들의 부분 집합  (기본키로 사용할 수 있는 속성들)

### 조건
* 유일성 : Key로 하나의 Tuple을 유일하게 식별할 수 있음
* 최소성 : 꼭 필요한 속성으로만 구성

### 예시)
![image](https://user-images.githubusercontent.com/37105602/218791824-4ff076cc-4c95-4f28-939a-31ffe677bd7e.png)

위 릴레이션 속성들 중에서 `[고객아이디]`속성은 각 `Tuple`들을 구분 할 수 있기 때문에 후보키가 될 수 있습니다.  
하지만, `[고객이름]` 속성은 세상엔 동명이인이 존재하기 때문에 불가능합니다.  

(후보키 => 고객아이디)  
-> 같은 아이디를 가지는 고객은 없기 때문
## 기본키(Primary Key)
>후보키 중 선택한 Main Key

데이터베이스 설계자나 관리자는 여러 후보키 중에서 기본적으로 사용할 키를 반드시 선택해야 하는데 이것이 **기본키(primary key)**입니다.  

### 특징
* Null 값을 가질 수 없음
* 동일한 값이 중복될 수 없음

### 예시)
![image](https://user-images.githubusercontent.com/37105602/218794104-e8fa2c69-e003-4136-8c6f-8341bbfb1e87.png)

후보키는 여러개 존재할 수 있습니다.  
위 에서는 `[고객아이디]` , `[고객이름+주소]`로 두가지 후보키가 존재합니다.  
*일반적으로 같이 사는 가족의 주소는 같지만 이름까지 같은 경우는 없기 때문에 (고객이름+주소) 도 후보키로 가능합니다.*

하지만, 어떤 후보키를 기본키로 지정해야 하는지는 데이터베이스 관리자나 설계자의 몫입니다.  
하지만 위 예시에선 `[고객아이디]`가 기본키로 가장 적합합니다.

## 대체키(Alternate Key)
>후보키 중 기본키를 제외한 나머지 키 = 보조키

![image](https://user-images.githubusercontent.com/37105602/218796276-76f753af-66f0-41d0-ad89-bc58a5eca242.png)

대체키는 기본키로 선택되지 못한 나머지 후보키들입니다.

## 슈퍼키(Super Key)
>유일성은 만족하지만, 최소성은 만족하지 못하는 키

유일성(uniqueness)은 키가 갖추어야 하는 기본 특성으로, 하나의 릴레이션에서 키로 지정된 속성 값은 투플마다 달라야 한다는 의미입니다.  
즉, 키 값이 같은 튜플은 존재할 수 없습니다.

## 외래키(Foreign Key)
>다른 릴레이션의 기본키를 그대로 참조하는 속성의 집합





## Reference
https://ddecode.tistory.com/entry/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4DB-4%EA%B4%80%EA%B3%84%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%EC%9D%98-%ED%82%A4key%EC%9D%98-%EC%A2%85%EB%A5%98