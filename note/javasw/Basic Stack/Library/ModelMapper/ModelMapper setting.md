### 날짜 : 2024-02-16 16:02

___

### 주제 : #ModelMapper #setting

___

### 메모 : 

```groovy
dependencies {
    implementation 'org.modelmapper:modelmapper:{version}'
}
```

> ModelMapper를 사용하기 위해서는 build.gradle에 의존성을 추가해야 합니다.

```java
@Configuration
public class AppConfig {

    @Bean
    public ModelMapper modelMapper() {
        return new ModelMapper();
    }

}
```

> ModelMapper bean을 설정해주는 AppConfig 클래스를 추가로 정의합니다.

```java
@Service
public class MemberService {

    @Autowired
    private ModelMapper modelMapper;
    
	public void signUp(SignUp signUp) {

        Member member = new Member();
        modelMapper.map(signUp, member);
        
    }
}
```

> 이후에 서비스 계층에서 @Autowired로 주입받아 사용할 수 있습니다.

> modelMapper.map() 메소드를 사용할 경우 객체의 위치는 상관 없습니다.
> 즉, 아래 2가지 경우 모두 동일하게 작동합니다.
> 
> ```java
> modelMapper.map(two, one);
> modelMapper.map(one, two);
> ```
>
> 의미론적으로 보았을 때 데이터의흐름에 맞춰 호출하는 것이 좋습니다.
> 
> - 저장할 데이터를 가진 객체 -> 저장할 대상이 되는 객체
> 
> 이렇게 호출하면 코드 의도를 더욱 명확하게 표현할 수 있습니다.


___

### 출처(참고문헌)

- [공식문서](https://modelmapper.org/getting-started/)

___

### 연결문서

- [[0.ModelMapper]]

