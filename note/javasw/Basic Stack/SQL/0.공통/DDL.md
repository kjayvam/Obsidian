### 주제 : #DDL #DataDefinitionLanguage #정의어

___

### 설명 : 

> DDL은 데이터베이스의 구조를 정의하거나 변경하는 데 사용되는 데이터 조작 언어입니다. 
> 데이터베이스 개체의 생성, 수정, 삭제 등을 처리하는데 사용됩니다. 
> DDL은 데이터베이스 스키마를 정의하며, 테이블, 인덱스, 뷰, 제약 조건 등을 관리합니다.

### 명령어 : 

>[!note] CREATE : 
> 새로운 데이터베이스 객체를 생성합니다. (테이블, 뷰, 인덱스 등을 생성)
> Oracle, MySQL은 CREATE 명령을 실행하면 자동으로 커밋 됩니다. 
> (SQL Server은 자동 커밋이 안됩니다.)
> 
> ```
> CREATE TABLE 테이블명 (컬럼명 데이터타입 조건) ;
> ```
> 
> ```
> CREATE TABLE Employees (
> 	EmployeeID INT PRIMARY KEY,
> 	FirstName VARCHAR(50),
> 	LastName VARCHAR(50),
> 	FOREIGN KEY(LastName) REFERENCES 테이블명(컬럼명) ON DELETE CASCADE
> );
> ```

>[!note] ALTER :
> 이미 존재하는 데이터베이스 객체의 구조를 변경합니다. 
> 테이블에 열을 추가, 제거, 수정하거나 제약 조건을 변경할 수 있습니다.
> 
> | 명령어 | 내용 | 
> | -: | -: |
> | ALTER COLUMN | 칼럼을 변경하는 역할
> | ADD COLUMN | 칼럼을 추가하는 역할
> | DROP COLUMN | 칼럼을 삭제하는 역할
> | MODIFY COLUMN | 칼럼을 수정하는 역할
> | RENAME COLUMN | 칼럼을 변경하는 역할 
> | ADD CONSTRAIN | 칼럼을 제약조건을 기반해서 추가하는 역할
> | DROP CONSTRAIN | 칼럼을 제약조건을 기반해서 삭제하는 역할
> 
> ```
> ALTER TABLE 테이블명 ALTER COLUMN 컬럼명 데이터타입 조건 ;
> ```
> 
> ```
> ALTER TABLE Employees ADD email VARCHAR(100);
> ALTER TABLE Employees ADD CONSTRAINT id_pk PRIMARY KEY;
> ALTER TABLE Employees ADD DROP COLUMN email;
> ```

>[!note] DROP : 
> 데이터베이스 객체를 삭제합니다. 
> 주의해서 사용해야 하며, 삭제 후에는 해당 객체와 관련된 데이터도 함께 삭제될 수 있습니다.
> 
> ```
> DROP TABLE Employees;
> ```
> 
> ```
> DROP TABLE 테이블명;
> ```

>[!note] TRUNCATE : 
> 테이블의 모든 데이터를 삭제하지만 테이블 구조는 유지됩니다. 
> DELETE보다 빠르며 롤백이 불가능합니다.
> 
> ```
> TRUNCATE TABLE 테이블명;
> ```
> 
> ```
> TRUNCATE TABLE Employees;
> ```

>[!note] RENAME :
> 데이터베이스 객체의 이름을 변경합니다.
> 
> ```
> ALTER TABLE 테이블명 RENAME TO 변경테이블명 ;
> RENAME 테이블명 TO 변경테이블명 ;
> ```
> 
> ```
> ALTER TABLE Employees RENAME TO EmployeeInfo ;
> RENAME Employees TO EmployeeInfo ;
> ```

>[!note] COMMENT : 
> 데이터베이스 객체에 주석을 추가합니다.
> 
> ```
> COMMENT ON TABLE Employees
> IS 'Stores information about company employees.';
> ```

>[!note] 옵션 : 
>
> CASCADE : 부모테이블의 레코드가 삭제되면 자식 테이블의 관련 레코드도 자동으로 삭제
>
>  CONSTRAINT : 제약조건을 지정할 때 사용
>  
> ```
> CONSTRAINT 제약조건명1 PRIMARY KEY (기본키의 속성이명)
> CONSTRAINT 제약조건명2 UNIQUE
> CONSTRAINT 제약조건명3 NOT NULL
> CONSTRAINT 제약조건명4 CHECK (체크범위)
> ```
> 
> ```
> CREATE TABLE 테이블명 (
> 	컬럼명 데이터타입 조건, 
> 	CONSTRAINT 제약조건명 PRIMARY KEY (기본키의 속성명)
> );
> ```
> 
> REFERENCES : 외래키를 지정할 때 사용
> 
> ```
> CREATE TABLE 테이블명 (
> 	컬럼명 데이터타입 REFERENCES 테이블명(컬럼명) ON DELETE CASCADE
> );
> > CREATE TABLE 테이블명 (
> 	컬럼명 데이터타입 REFERENCES 테이블명(컬럼명) ON DELETE SET NULL
> );
> ```

___

### 출처(참고문헌)

- [SQL 쿼리문 보기 좋게 정렬해주는 사이트](https://zzznara2.tistory.com/663)

___

### 연결문서

- [[SQL문]]
- [[과목 2-0]]
- [[과목 2-1]]
