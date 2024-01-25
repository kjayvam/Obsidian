### 날짜 : 2024-01-16 11:40

___

### 주제 : #Lombok #Annotation #어노테이션

___

### 종류 : 

>[!note] @NoArgsConstructor
>
> 기본생성자를 자동으로 추가한다.  
> @NoArgsConstructor(access = AccessLevel.PROTECTED)  
> 기본생성자의 접근 권한을 protected로 제한할 수도 있다.
> 
> Entity Class를 프로젝트 코드상에서 기본생성자로 생성하는 것은 금지하고, JPA에서 Entity 클래스를 생성하도록 허용하기 위해 사용한다.

>[!note] @AllArgsConstructor
>
> 모든 필드 값을 파라미터로 받는 생성자를 추가한다.

>[!note] @RequiredArgsConstructor
>
> final이나 @NonNull인 필드 값만 파라미터로 받는 생성자를 추가한다.

>[!note] @Getter
>
> Class 내 모든 필드의 Getter 메소드를 자동 생성해준다.

>[!note] @Setter
>
> Class 내 모든 필드의 Setter 메소드를 자동 생성해준다.  
> Controller에서 @RequestBody로 외부에서 데이터를 받는 경우엔 기본생성자 + Set 메소드를 통해서만 값이 할당된다.  
> 그러나 Entity Class에서는 Setter를 사용하면 안되기 때문에 DTO클래스를 생성해서 DTO타입으로 받아야 한다.

>[!note] @ToString
>
> Class 내 모든 필드의 toString 메소드를 자동 생성한다.

>[!note] @EqualsAndHashCode
>
> equals와 hashCode method를 오버라이딩 해주는 어노테이션이다.
> 
> ```java
> @EqualsAndHashCode(callSuper = true)
> ```
> 
> callSuper 속성을 통해 equals와 hashCode 메소드 자동 생성 시 부모 클래스의 필드까지 감안할지 안 할지에 대해서 설정할 수 있다.  
> 즉, callSuper = true로 설정하면 부모 클래스 필드 값들도 동일한지 체크하며, callSuper = false로 설정(기본값)하면 자신 클래스의 필드 값들만 고려한다.

>[!note] @Builder
>
> 어느 필드에 어떤 값을 채워야 할지 명확하게 정하여 객체 생성 시점에 값을 채워준다.  
> 생성 시점에 값을 채워는 것은 생성자와 같지만 Builder를 사용하면 ==어느 필드에 어떤 값을==넣어야 할 지 명확하게 인지할 수 있다.
> 
> ```java
> @Builder
> public class Memer {
> 	@Id
> 	private String uderId;
> 	private String userName;
> }
> 
> //객체 생성
> Member member = Member.builder().userId(parameter.getUserId())
> 						.userName(parameter.getUserName()).build();
> ```
 
>[!note] @Data
>
> @Getter,  @Setter,  @EqualsAndHashCode,  @AllArgsConstructor을 포함한 Lombok에서 제공하는 필드와 관련된 모든 코드를 생성한다.  
> 모든 기능을 허용하기 때문에 사용하지 않는 것이 좋다.

___

### 출처(참고문헌)

- [[Spring] 어노테이션(Annotation)](https://velog.io/@rara_kim/Spring-%EC%96%B4%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98Annotation)

___

### 연결문서

- [[0.Spring Boot]]
- [[Annotation]]
