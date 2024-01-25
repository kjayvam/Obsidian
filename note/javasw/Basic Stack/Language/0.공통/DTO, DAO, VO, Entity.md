### 날짜 : 2024-01-16 12:03

___

### 주제 : #DTO #DAO #VO #Entity

___

### 요약 설명 : 

- DAO : Database에 접근하는 역할을 하는 객체.
- DTO : 데이터를 전달하기 위한 객체
- VO : 값 자체를 표현하는 객체.
- Entity : 실제 DB 테이블과 매핑이 되는 클래스.

|  |**DTO**|**VO**|**Entity**|
|---|---|---|---|
|**정의**|Layer간의 데이터 전송용 객체|값을 표현하는 객체|DB 테이블에 대해 매핑하는 객체|
|**상태 변경 여부**|가변 혹은 불변|불변|가변 혹은 불변|
|**로직 여부**|getter() / setter()메소드에 대한 로직만 포함한다.|setter() 메소드 이외의 메소드를 가진다.|로직을 포함할 수 있다.|

### DAO : 

>[!note] DAO = Data Access Object
> 
> - Database에 접근하는 역할을 하는 객체.
> - 프로젝트의 서비스 모델에 해당하는 부분과 데이터베이스를 연결하는 역할
> - 데이터의 CRUD 작업을 시행하는 클래스. 
> - 즉, 데이터에 대한 CRUD 기능을 전담하는 오브젝트

>[!note] 사용하는 이유
> 
> - 효율적인 커넥션 관리와 보안성.
> - DAO는 비즈니스 로직을 분리하여 도메인 로직으로부터 DB와 관련한 메커니즘을 숨기기 위해 사용.

> 예제

``` java
public class TestDao {
public void add(TestDto dto) throws ClassNotFoundException, SQLException {
	private static final String DRIVER = "com.mysql.jdbc.Driver";
    private static final String URL = "jdbc:mysql://localhost:3306/dao_Db";
    private static final String USER = "root";
    private static final String PASSWORD = "1234";   
		
		String sql = "SELECT * FROM vouchers";

        try {
            con = DriverManager.getConnection(URL, USER, PASSWORD);
            stmt = con.createStatement();
            res = stmt.executeQuery(sql);
            while (res.next()) {
                System.out.println(res.getString("id") + " ");
                System.out.println(res.getString("value") + " ");
            }
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }

    preparedStatement.setString(1, dto.getName());
    preparedStatement.setInt(2, dto.getValue());
    preparedStatement.setString(3, dto.getData());
    preparedStatement.executeUpdate();
    preparedStatement.close();

    connection.close();
	}
}
```

### DTO : 

>[!note] DTO = Data Transfer Object (≒ Value Object)
> 
> - 데이터를 전달하기 위한 객체
> - 로직을 가지지 않는 순수한 데이터 객체(getter & setter 만 가진 클래스).
> - 여러 레이어(Layer)간 데이터를 주고 받을 때 사용할 수 있고 주로 View와 Controller 사이에서 활용.
> - getter / setter 메소드를 포함한다. 하지만, 이외의 다른 비즈니스 로직은 포함하지 않는다.
> - 어떻게 구현하느냐에 따라 가변 객체로 활용할 수도 있고 **불변 객체로 활용할 수도 있다.
> - 데이터 전달 만을 위한 객체라는 게 핵심 정의이다. 그렇기 때문에 완전히 데이터 전달 용도로만 사용하는게 목적이라면, getter/setter만 필요하지, 이외의 비즈니스 로직은 굳이 있을 필요가 없다.
> 
> 계층(Controller, View) 간 데이터 교환을 위한 Java beans  
> 위 MVC 중 Model 쪽에 속하여 MVC 흐름 속에서 데이터가 교환될 수 있도록 하는 객체
> 
> Controller는 View - Model의 데이터를 주고 받을 때 별도의 DTO 를 주로 사용,  
> 도메인 객체를 View에 직접 전달할 수 있지만,
> 
> - 민감한 도메인 비즈니스 기능이 노출될 수 있으며
> - Model과 View 사이에 의존성이 생기기 때문
> 
> (물론 소규모 프로젝트의 경우 DTO 사용이 불필요할 수 있음)


> 
> Request와 Response용 DTO는 View를 위한 클래스로, 자주 변경이 필요한 클래스이다.  
> Entity 클래스와 DTO 클래스를 분리하는 이유는 View Layer와 DB Layer를 철저하게 분리하기 위해서다.
> 
> 테이블과 매핑되는 Entity 클래스가 변경되면 여러 클래스에 영향을 끼치게 되는 반면 View와 통신하는 DTO 클래스(Request/Response 클래스)는 자주 변경되므로 분리해야 한다.

![](https://velog.velcdn.com/images%2Fgeesuee%2Fpost%2F1c2190b5-d40b-4ce8-b4a2-7ffe7d8f0a9d%2FMVC%20DTO.png)

> 예제

```java
[가변 객체로써의 DTO]

// 가변 객체 DTO
// 기본생성자로 생성 후 값을 유동적으로 변경 
public class DtoEx {
    private String name;
    private int age;

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

[불변 객체로써의 DTO]

// 불변 객체 DTO
// 생성시 지정했던 값이 변하지 않고 getter() 메소드만 사용 가능
public class DtoEx {
    private final String name;
    private final int age;

    public DtoEx(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```

- 가변 객체로써 DTO를 만들 때는 setter() 메소드를 이용하여 구현할 수 있다.
- 불변 객체로써 DTO를 만들 때는 생성자를 이용해서 구현시 getter() 메소드만 구현할 수 있다.
- 이렇게 구현함으로써 데이터를 전달하는 과정에서 데이터의 불변성을 보장합니다.

### VO :

>[!note] VO = Value Object
>
> - 값 자체를 표현하는 객체.
> - DTO와 유사하지만 DTO는 setter를 가지고 있어 값이 변할 수 있다.
> - VO는 getter() 메소드를 포함해서, 이외의 비즈니스 로직도 포함할 수 있다.
> - 사용하는 도중에 변경 불가하여 setter() 메소드는 가지지 않아. 오로지, 읽기 기능만 가능하다.(read-Only)
> - VO는 두 객체의 모든 필드 값들이 동일하면 두 객체는 같다! 가 핵심 정의이다. 그렇기 때문에 완전히 값 자체 표현 용도로만 사용하는 게 목적이라면, 두 객체의 모든 필드 값들이 모두 같으면 같은 객체이도록 만드는 것(equals() 와 hashCode()의 오버라이딩)이 중요하지, 메소드는 어떤 메소드가 있든 말든 상관 없다.

> 예제

``` java
// VO예제
// 값을 표현만 하기 때문에 setter()메소드는 사용하지 않는다.
public class VoEx {
    static class Money{
        private final int value;

        Money(int value) {
            this.value = value;
        }

        public int getValue() {
            return value;
        }
				
	// 사용자 생성 메소드이지만 setter형태의 메소드가 아니므로 무관함
        public String printMoney(){
            return this.value + "원";
        }
					
	// 두 객체의 모든 필드 값들이 모두 같으면 같은 객체이도록 만들기 위한 오버라이딩
		@Override
        public int hashCode() {
            return Objects.hash(value);
        }

        @Override
        public boolean equals(Object obj) {
            if(this == obj)
                return true;
            if(obj == null || getClass() != obj.getClass())
                return false;
            Money money = (Money) obj;
            if(value == money.value)
                return true;
            else
                return false;
        }
    }
}
```

### Entity

>[!note] Entity = Value Object
>
> - 실제 DB 테이블과 매핑이 되는 클래스.
> - 데이터를 전달하는 클래스로 사용하면 안된다.
> - Entity를 기준으로 테이블이 형성되고, 칼럼이 변경되곤 한다.
> - Entity는 비즈니스 로직을 포함할 수도, setter() 메소드를 포함할 수도 있습니다.

> 예제

``` java
public class EntityEx {
    private final Long id;
    private final String name;
    private final int value;

    public EntityEx(Long id, String name, int value) {
        this.id = id;
        this.name = name;
        this.value = value;
    }
}
```

___

### 출처(참고문헌)

- [MVC와 DTO](https://velog.io/@geesuee/JAVA-%EC%9E%90%EB%B0%94-MVC%EC%99%80-DTO)
- [DAO, DTO, VO, Entity 간단하고 쉽게 이해하기](https://ccomccomhan.tistory.com/35)
- [DTO(VO), DAO , Entity에 대해서 알아보자!](https://today-retrospect.tistory.com/142)

___

### 연결문서

- [[0.자바란]]
- [[MVC패턴]]

