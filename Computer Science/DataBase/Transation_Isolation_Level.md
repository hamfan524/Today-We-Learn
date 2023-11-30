# 트랜잭션의 격리 수준(Transaction Isolation Level)

<br>

```
여러 트랜잭션이 동시에 처리될 때,
특정 트랜잭션이 다른 트랜잭션에서 변경하거나 조회하는 데이터를 볼 수 있게 허용할지 여부를 결정하는 것
```

<br>

## 격리 수준 ( ANSI/ISO SQL standard( SQL192 ) ):lock:

> - SERIALIZABLE
> - REPEATABLE READ
> - READ COMMITTED
> - READ UNCOMMITED

<br>

```
트랜잭션의 격리 수준은 격리(고립) 수준이 높은 순서대로
SERIALIZABLE -> REPEATABLE READ -> READ COMMITTED -> READ UNCOMMITED
```

<br>

## SERIALIZABLE

> - 가장 엄격한 격리 수준
> - 신형 트랜잭션이 읽은 데이터를 후행 트랜잭션이 갱신하거나 삭제하지 못할 뿐만 아니라 중간에 새로운 레코드를 산입하는 것도 막아주는 격리수준
> - 트랜잭션 순차적 처리로 인한 동시 처리 성능 (매우)저하

<br>

```
Serializable은 데이터의 안정성을 위배하는 어떤 것도 발생할
수 없을 정도로 높은 고립성을 가지고 있다.

하지만 그로 인해 동시성이 많이 떨어진다.그래서 하나의 데이터 영역에 READ가 발생할 때 어떤 DML도 발생할 수 없어서 많은 문제를 야기한다.

그래서  대부분의 RDBMS는 Read Commited나 Repeatable Read로
고립성을 유지하여 트랜잭션을 지원한다.
```

<br>

## Repeatable Read

> - 선행 트랜잭션이 읽은 데이터는 트랜잭션이 종료될 때가지 후행 트랜잭션이 <br> 갱신하거나 삭제하는 것을 불허함으로써 같은 데이터를 두 번 쿼리했을 때 <br>일관성 있는 결과를 리턴한다.
> - Phantom Read 현상은 여전히 발생함.( InnoDB는 발생하지 않음)
> - MySQL 의 InnoDB 에서 기본으로 사용되는 격리수준.
> - DB2, SQL Server의 경우 트랜잭션 고립화 수준은 Repeatable Read로 변경하면 읽은 데이터에 걸린 공유 Lock을 <br>
>   커밋할 때까지 유지하는 방식으로 구현함.
> - Oracle은 이 레벨을 명시적으로 지원하지 않지만 for update 절을 이용해 구현가능.
>   SQL Server 등에서도 for update절을 사용할 수 있지만 커서를 명시적으로 선언할때만 사용 가능함.

<br><br>

## Read Committed

> - Dirty Read 방지 : 트랜잭션이 커밋되어 확정된 데이터만 읽는 것을 허용
> - 오라클 같은 DBMS가 기본모드로 채택하고 있는 격리수준
> - Non-Repeatable Read, Phantom Read 현상은 여전히 발생
> - DB2, SQL Server, Sybase의 경우 일기 공유 Lock을 이용해서 구현, 하나의 <br> 레코드를 읽을 때 Lock을 설정하고 해당 레코드를 빠져 나가는 순간 Lock 해제
> - Oracle은 Lock을 사용하지 않고 쿼리시작 시점의 Undo 데이터를 제공하는 방식으로 구현

<br><br>

## Read Uncommitted

> - 트랜잭션에서 처리 중인, 아직 커밋되지 않은 데이터를 다른 트랜잭션이 읽는 것을 허용
> - Dirty Read, Non-Repeatable Read, Phantom Read 현상 발생
> - Oracle은 이 레벨을 지원하지 않음

<br><br>

---

|      level      | Dirty Read | Non-Repeatable Read |      Phantom Read      |
| :-------------: | :--------: | :-----------------: | :--------------------: |
| READ UNCOMMITED |    발생    |        발생         |          발생          |
| READ COMMITTED  |    없음    |        발생         |          발생          |
| REPEATABLE READ |    없음    |        없음         | 발생(MySQL은 거의없음) |
|  SERIALIZABLE   |    없음    |        없음         |          없음          |

---

### ref

https://mangkyu.tistory.com/299
<br>
https://hyeyul-k.tistory.com/18
