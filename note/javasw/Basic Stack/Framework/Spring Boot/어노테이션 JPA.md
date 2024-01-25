### 날짜 : 2024-01-16 11:45

___

### 주제 : #JPA #Annotation #어노테이션

___

### 종류 : 


>[!note] @Entity
>
> 실제 DB 테이블과 매핑될 Class임을 나타낸다.

>[!note] @Table
>
> Entity Class에 매핑할 테이블 정보를 알려준다.  
> 어노테이션을 생략하면 Class명을 테이블명으로 매핑한다.
> 
> ```java
> @Entity
> @Table(name = "MEMBER")
> public class Member {
> }
> ```

>[!note] @Id
>
> 해당 테이블의 PK 필드를 의미한다.

>[!note] @GeneratedValue
>
> PK의 생성 규칙을 나타낸다.  
> 가능한 Entity의 PK는 Long 타입의 Auto_increment를 추천한다.  
> 기본값은 AUTO로 MySQL의 auto_increment와 같이 자동으로 증가하는 정수형 값이 된다.
> 
>> 옵션 strategy
>> - GenerationType.AUTO = 연결할 DB를 알아서 지정
>> - GenerationType.IDENTITY = MySQL, MariaDB에서 사용
>> - GenerationType.SEQUENCE = 오라클에서 사용
>> - GenerationType.TABLE = 기본키 생성

>[!note] @Column
>
> 테이블의 컬럼을 나타내며 선언하지 않더라도 해당 Class의 필드는 모두 컬럼이 된다.  
> @Column을 생략하면 필드명을 사용해서 컬럼명과 매핑한다.
> 
> 이 어노테이션은 기본값 외에 추가로 변경이 필요한 옵션이 있을 경우 사용한다.
> 
> ```java
> @Entity
> public class Post {
> 	@Id
> 	@GeneratedValue(strategy = GenerationType.AUTO)
> 	private Long id;
> 
> 	@Column(nullable = false)
> 	private String title;
> 
> 	@Column(nullable = false)
> 	private String author;
> }
> ```

>[!note] @EnableJpaAuditing
>
> Java에서 JPA를 사용하여 Entity-DB 테이블을 매핑할 때 공통적으로 도메인들이 가지고 있는 필드나 컬럼들이 존재하는데, 대표적으로 생성일자, 수정일자, 식별자 같은 필드 및 컬럼이 있다.  
> 모든 Entity마다 해당 필드들을 넣어서 생성하는 것은 상당히 비효율적이다.
> 
> DB에서 누가, 언제하였는지 생성일, 수정일 컬럼은 대단히 중요한 데이터로, JPA에서는 `Audit`이라는 기능을 제공하고 있다.  
> Audit은 감시하다, 감사하다라는 뜻으로 Spring Data JPA에서 `시간에 대해서 자동으로 값을 넣어주는 기능`이다.
> 
> Entity를 영속성 컨텍스트에 저장하거나 조회를 수행한 후에 update를 하는 경우 매번 시간 데이터를 입력하여 주어야 하는데, audit을 이용하면 자동으로 시간을 매핑하여 데이터베이스의 테이블에 넣어준다.
> 
> ```java
> @Getter
> @MappedSuperclass
> @EntityListeners(AuditingEntityListener.class)
> public class Timestamped {
> 
> 	@CreatedDate
> 	private LocalDateTime createdAt;
> 
> 	@LastModifiedDate
> 	private LocalDateTime modifiedAt;
> }
> ```

>[!note] @MappedSuperclass
>
> JPA Entity 클래스들이 해당 클래스를 상속할 경우, createDate, modifiedDate를 컬럼으로 인식

>[!note] @EntityListeners(AuditingEntityListener.class)
>
> 해당 클래스에 Auditing 기능을 포함

>[!note] @CreatedDate
>
> Entity가 생성되어 저장될 때 시간이 자동 저장

>[!note] @LastModifiedDate
>
> 조회한 Entity의 값을 변경할 때 시간이 자동 저장

```java
@Entity
@Getter
@NoArgsConstructor
public class Post extends Timestamped{
	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	private Long id;

	@Column(nullable = false)
	private String title;

	@Column(nullable = false)
	private String author;

	@Column(nullable = false)
	private String content;

	@Column(nullable = false)
	private String password;

	public Post(PostRequestDto requestDto) {
		this.title = requestDto.getTitle();
		this.author = requestDto.getAuthor();
		this.content = requestDto.getContent();
		this.password = requestDto.getPassword();
	}

	public void update(PostRequestDto requestDto) {
		this.title = requestDto.getTitle();
		this.author = requestDto.getAuthor();
		this.content = requestDto.getContent();
		this.password = requestDto.getPassword();
	}
}
```

Post 클래스가 @MappedSuperclass가 적용된 Timestamped 클래스를 상속하기 때문에 JPA가 생성일자, 수정일자 컬럼을 인식하게 된다.  
그리고 영속성 컨텍스트에 저장 후 Timestamped 클래스의 Auditing 기능으로 인해서 트랜잭션 커밋 시점에 Hibernate가 자동으로 시간 값을 채워주는것을 확인 할 수가 있다.

> SpringBoot의 실행 클래스에 `@EnableJpaAuditing` 어노테이션을 적용해주어야 JpaAuditing 기능이 활성화 된다.

___

### 출처(참고문헌)

- [[Spring] 어노테이션(Annotation)](https://velog.io/@rara_kim/Spring-%EC%96%B4%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98Annotation)

___

### 연결문서

- [[0.Spring Boot]]
- [[Annotation]]
