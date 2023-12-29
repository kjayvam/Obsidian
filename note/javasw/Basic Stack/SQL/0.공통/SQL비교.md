### 주제 : #SQL비교 

___

### DROP | TRUNCATE | DELETE  : 

| DROP | TRUNCATE | DELETE |
| :-: | :-: | :-: |
| DDL | DDL | DML 
| ROLLBACK 불가능 | ROLLBACK 불가능 | COMMIT 이전 ROLLBACK 가능
| AUTO COMMIT | AUTO COMMIT | 사용자 COMMIT
| 테이블이 사용했던 스토리지를 모두 공개 | 테이블이 사용했던 스토리지 중 최초 테이블 생성 시 할당된 스토리지만 남기고 공개 | 데이터를 모두 DELETE해도 사용했던 스토리지는 공개되지 않음
| 테이블의 정의 자체를 완전히 삭제 | 테이블을 최초 생성된 초기상태로 만듦 | 데이터만 삭제

### GROUP BY | DISTINCT  : 

| GROUP BY | DISTINCT |
| :-: | :-: |
| 그룹 함수를 사용 | 그룹 함수 X 
| 그룹 함수를 사용하여 특정 컬럼의 값을 기준으로 행을 그룹화 | 중복된 행을 제거
