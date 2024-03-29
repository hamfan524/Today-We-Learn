# 이상현상

> `이상 현상(Anomaly)`은 테이블을 설계할 때 잘못 설하여 데이터를 삽입, 삭제, 수정할 때 논리적으로 발생하는 오류를 말합니다.   
>   
> `이상현상`이 생기지 않도록 설계하는 것이 정규화를 하여 좋은 관계형 데이터베이스를 설계하는 목적 중 하나입니다.


---
### 예시 표
![image](https://github.com/hamfan524/Today-We-Learn/assets/37105602/57e3aa20-d75f-4d61-bc0f-a2455a76f928)


### 1. 삽입이상 (Insertion Anomaly)
> 데이터를 삽입할 때, 불필요한 데이터까지 삽입해야 테이블에 추가할 수 있는 현상

위 릴레이션에 아직 강의를 수강하지 않은 학생 정보를 삽입할 경우에는 과목번호와 성적에 Null값이 들어가야하는 일이 생깁니다.   

![image](https://github.com/hamfan524/Today-We-Learn/assets/37105602/98c76ec6-5215-4b8d-bb4c-3f9dafdc67ba)

만약, `학번과 과목번호가 기본키`라면 기본키는 `Null이 될 수 없으므로, 테이블에 추가할 수 없는 현상이 발생`합니다.

### 2. 갱신이상(Update Anomaly)
> 중복된 데이터 중 일부만 수정되어 데이터 모순이 일어나는 현상

`학번이 123인 학생`의 학과를 `"컴퓨터"에서 "화학"으로 변경`하게 되면,   
학번이 123인 학생의 모든 튜플(행)에서 학과이름을 변경해야 하지만, 실수로 `일부만 변경하고 나머지는 변경하지 않는 경우`

### 3. 삭제이상(Deletion Anomaly)
> 어떤 정보를 삭제하면, 그 자료가 포함된 튜플 전체가 삭제됨으로써 원하지 않는 데이터까지 삭제되는 현상

![image](https://github.com/hamfan524/Today-We-Learn/assets/37105602/b4ab7bcd-e440-4317-a1d5-56ae4244a269)

- `학번이 300인 학생`이 수강을 취소하게 되면 `C-73인 강의에 대한 정보`와 `300인 학생에 대한 정보도 함께 삭제`됩니다.

