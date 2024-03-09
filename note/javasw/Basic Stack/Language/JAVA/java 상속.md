### 주제 : #다형성 #상속 #예약어

___

### abstract : 

> 상위클래스에서 사용됩니다.
> 상위클래스를 인스턴스 생성하지 못합니다.
> 하위클래스만 사용이 가능합니다.

#### abstract 예시 :
	
// 상위클래스

``` java
abstract class Parent {
	abstract void doSomething(); // 추상 메소드
}

```

// 하위클래스

``` java
class Child extends Parent {
    @Override
    void doSomething() {
        // 추상 메소드 구현
    }
}
```

// 메인

``` java
public class Main {
    public static void main(String[] args) {
        // Parent parent = new Parent(); // 이 부분은 오류를 발생시킵니다.
        Child child = new Child(); // 하위 클래스로는 객체 생성 가능
    }
}
```

### extends : 

> 상위클래스에 있는 맴버에 접근이 가능합니다.
> 'super.맴버(메소드)'을 통해 상위 클래스의 맴버(메소드)에 접근이 가능하다.
> '@override'를 통해 재정의된 메소드를 표시합니다.

#### extends 예시 : 

// 상위클래스

``` java
class Parent {
    int num = 10;

    void display() {
        System.out.println("Parent class method");
    }
}
```

// 하위클래스

``` java
class Child extends Parent {
    int num = 20;

    void display() {
        super.display(); // 부모 클래스의 display() 메소드 호출
        System.out.println("Child class method");
    }

    void accessFields() {
        System.out.println("Child num: " + num);          // 자식 클래스의 num
        System.out.println("Parent num: " + super.num);   // 부모 클래스의 num
    }
}
```

// 메인

``` java
public class Main {
    public static void main(String[] args) {
        Child child = new Child();
        child.display();       // 메소드 오버라이딩을 통한 부모 메소드 호출
        child.accessFields();  // 부모 클래스와 자식 클래스의 멤버 접근
    }
}
```

// 출력

``` java
Parent class method
Child class method
Child num: 20
Parent num: 10
```




___

### 출처(참고문헌)

- [추상클래스](http://www.tcpschool.com/java/java_polymorphism_abstract)

___

### 연결문서

- [[0.자바]]
- [[다형성]]
- [[예약어]]

