# DBMS 데이터 언어 _ SQL 종류
> SQL (Structured Query Language)   
> : 규격화된, 규칙을 정해놓은 질의 언어

[1. DDL (데이터 정의어)](#ddldata-definition-language-데이터-정의어)   
[2. DML (데이터 조작어)](#dmldata-manipulation-language-데이저-조작어)   
[3. DCL (데이터 제어어)](#dcldata-control-language-데이터-제어어)   
[4. TCL (트랜잭션 제어어)](#tcltransaction-control-language-트랜잭션-제어어)

![image](https://github.com/hamfan524/Today-We-Learn/assets/37105602/2604939a-d3b1-41a3-b5ab-5af7170946f5)


## DDL(Data Definition Language, 데이터 정의어)
> - 데이터베이스의 `구조` 또는 `스키마(schema)`를 `정의하는 언어`   
> - 데이터를 생성, 수정, 삭제하는 등의 데이터의 전체 골격을 결정하는 역할을 하는 언어

명령어|기능
:---:|:---:
CREATE| 데이터베이스의 `객체를 생성`
ALTER| 데이터베이스의 `구조 변경`
DROP| 데이터베이스의 `객체를 삭제` (테이블의 모든 데이터와 구조를 삭제)
RENAME| 데이터베이스의 객체 이름을 변경
COMMENT|데이터에 주석 등을 추가
TRUNCATE|테이블에 할당된 모든 공간을 포함하여 모든 레코드를 제거(테이블 객체의 저장공간 재사용 가능)

## DML(Data Manipulation Language, 데이저 조작어)
> - 데이터베이스의 데이터를 관리하는데 사용    
> - 정의된 데이터베이스에 입력된 레코드를 `조회`하거나 `수정`, `삭제`하는 등의 역할을 하는 언어

명령어|기능
:---:|:---:
SELECT| 데이터베이스에서 데이터 `조회`
INSERT| 테이블에 데이터 `삽입`(추가)
UPDATE| 테이블 내의 기존 데이터 `수정`
DELETE| 테이블에서 데이터를 `삭제`
MERGE|데이터가 테이블에 존재하지 않으면 INSERT, 존재하면 UPDATE를 수행
CALL|PL/SQL 또는 JAVA 서브 프로그램 호출
EXPLAIN PLAN|데이터 접근 경로를 해석(SQL문이 어떻게 실행 / 작동하는지에 대한 점검 / 분석을 할 수 있도록 도와줌)
LOCK TABLE|동시성 제어
## DCL(Data Control Language, 데이터 제어어)
> - 데이터베이스 `권한`을 부여하는 언어

명령어|기능
:---:|:---:
GRANT| 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 `권한을 부여`
REVOKE| GRANT 명령어로 부여한 특정 작업에 대한 수행 `권한을 회수, 박탈`
COMMIT| 데이터베이스의 객체를 삭제 (테이블의 모든 데이터와 구조를 삭제)
ROLLBACK| 데이터베이스의 객체 이름을 변경

## TCL(Transaction Control Language, 트랜잭션 제어어)
> - 데이터의 보안, 무결성, 회복, 병행 수행제어 등을 정의하는 언어

명령어|기능
:---:|:---:
COMMIT| 트랜잭션의 작업 `결과를 저장` (트랜잭션 완료)
ROLLBACK| 트랜잭션의 작업을 취소 후, 데이터베이스를 `마지막 COMMIT 지점으로 복구`
SAVEPOINT| 
SET TRANSACTION| 트랜잭션 지정