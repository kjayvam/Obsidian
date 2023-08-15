### 주제 : #DDL #DataDefinitionLanguage #정의어

___

### 설명 : 

> DDL은 데이터베이스의 구조를 정의하거나 변경하는 데 사용되는 데이터 조작 언어입니다. 
> 데이터베이스 개체의 생성, 수정, 삭제 등을 처리하는데 사용됩니다. 
> DDL은 데이터베이스 스키마를 정의하며, 테이블, 인덱스, 뷰, 제약 조건 등을 관리합니다.

### 명령어 : 

>[!note] CREATE : 
> 새로운 데이터베이스 객체를 생성합니다. 
> 예를 들어, 테이블, 뷰, 인덱스 등을 생성할 수 있습니다.
> ```
> CREATE TABLE Employees (
> 	EmployeeID INT PRIMARY KEY,
> 	FirstName VARCHAR(50),
> 	LastName VARCHAR(50)
> );
> ```

>[!note] ALTER :
> 이미 존재하는 데이터베이스 객체의 구조를 변경합니다. 
> 테이블에 열을 추가, 제거, 수정하거나 제약 조건을 변경할 수 있습니다.
> ```
> ALTER TABLE Employees
> ADD Email VARCHAR(100);
> ```

>[!note] DROP : 
> 데이터베이스 객체를 삭제합니다. 
> 주의해서 사용해야 하며, 삭제 후에는 해당 객체와 관련된 데이터도 함께 삭제될 수 있습니다.
> ```
> DROP TABLE Employees;
> ```

>[!note] TRUNCATE : 
> 테이블의 모든 데이터를 삭제하지만 테이블 구조는 유지됩니다. 
> DELETE보다 빠르며 롤백이 불가능합니다.
> ```
> TRUNCATE TABLE Employees;
> ```

>[!note] RENAME :
> 데이터베이스 객체의 이름을 변경합니다.
> ```
> ALTER TABLE Employees
> RENAME TO EmployeeInfo;
> ```

>[!note] COMMENT : 
> 데이터베이스 객체에 주석을 추가합니다.
> ```
> COMMENT ON TABLE Employees
> IS 'Stores information about company employees.';
> ```

___

### 출처(참고문헌)

- [SQL 쿼리문 보기 좋게 정렬해주는 사이트](https://zzznara2.tistory.com/663)

___

### 연결문서

- [[SQL문]]

