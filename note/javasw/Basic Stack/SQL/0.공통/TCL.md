### 주제 : #TCL #TransactionControlLanguage #트랜젝션제어어

___

### 설명 : 

> 트랜잭션(Transaction)은 데이터베이스의 논리적 연산단위로서 밀접히 관련되어 분리될 수 없는 데이터베이스 조각을 가리킵니다.
> TCL은 데이터베이스 트랜잭션을 제어하는 데 사용되는 데이터 제어 언어입니다. 
> 데이터베이스의 트랜잭션 관리와 데이터 무결성을 유지하기 위해 사용됩니다. 
> TCL은 데이터베이스 작업의 원자성, 일관성, 격리성 및 지속성을 보장하는데 중점을 둡니다.

### 명령어 : 

>[!note] COMMIT : 
> 트랜잭션의 변경 사항을 데이터베이스에 영구적으로 저장하고, 트랜잭션을 종료합니다. 
> COMMIT 후에는 변경 사항이 지속적으로 유지됩니다.
> 
>```
> UPDATE Account SET Balance = Balance - 100 WHERE AccountNumber = '123';
> UPDATE Account SET Balance = Balance + 100 WHERE AccountNumber = '456';
> COMMIT;
>```

>[!note] ROLLBACK :
> 트랜잭션의 변경 사항을 취소하고 이전 상태로 되돌립니다. 
> 트랜잭션이 중간에 실패하거나 오류가 발생한 경우 사용됩니다.
> 
> ``` 
> 오라클
> ROLLBACK TO 세이브포인트명 ;
> SQL Server
> ROLLBACK TRANSACTION 세이브포인트 ; 
> ROLLBACK TRAN 세이브포인트명 ; 
> ```
>```
> BEGIN;
> UPDATE Inventory SET Quantity = Quantity - 10 WHERE ProductID = 123;
> UPDATE Orders SET Status = 'Shipped' WHERE OrderID = 789;
> ROLLBACK;
>```

>[!note] SAVEPOINT : 
> 트랜잭션 내에서 중간에 저장점을 설정하여, 해당 지점 이전의 변경 사항을 롤백할 수 있습니다.
> 
> ```
> 오라클
> SAVEPOINT 세이브포인트명 ;
> SQL Server
> SAVE TRANSACTION 세이브포인트명 ;
> SAVE TRAN 세이브포인트명 ;
> ```
>```
> BEGIN;
> UPDATE Stock SET Quantity = Quantity - 5 WHERE ProductID = 123;
> SAVEPOINT StockUpdate;
> UPDATE Orders SET Status = 'Processed' WHERE OrderID = 456;
> ROLLBACK TO StockUpdate;
>```


>[!note] SET TRANSACTION :
> 트랜잭션의 특성을 설정합니다. 
> 격리 수준, 트랜잭션의 읽기 모드 등을 설정할 수 있습니다.
> 
>```
> SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
>```

___

### 출처(참고문헌)

- [SQL 쿼리문 보기 좋게 정렬해주는 사이트](https://zzznara2.tistory.com/663)

___

### 연결문서

- [[SQL문]]
- [[과목 2-0]]
- [[과목 2-1]]
