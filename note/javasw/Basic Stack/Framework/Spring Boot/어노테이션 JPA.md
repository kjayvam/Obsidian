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

>[!note] @JoinColumn (name="user_id")
>
> 엔티티 간의 관계를 매핑할 때 사용
> 외래키 매핑에 사용

>[!note] @ManyToOne
>
> - 다대일(N:1) 관계를 매핑할 때 사용
> - Foreign Key가 있는 쪽에 추가
> - 예) 포스트 엔티티에서 사용자 엔티티를 참조할 때

>[!note] @OneToOne
>
> - 일대일(1:1) 관계를 매핑할 때 사용
> - 주 테이블이나 대상 테이블 둘 중 하나에 FK를 두고 매핑 가능
> - 주로 주 테이블에 FK를 두는 것이 편리
> - 예) 사용자 엔티티에서 보안정보 엔티티를 1:1로 연관 지을 때 사용

>[!note] @Query
> 
> @Query를 사용하면 리포지토리 인터페이스에 직접 JPQL이나 네이티브 SQL을 정의할 수 있습니다. 
> 즉, 커스텀한 쿼리를 작성할 수 있다는 장점이 있습니다.
> 
> ```java
> public interface UserRepository extends JpaRepository<User, Long> {
> 	// JPQL을 활용한 커스텀 쿼리 예제
> 	@Query("SELECT u FROM User u WHERE u.name = ?1 AND u.age > ?2") 
> 	List<User> findUsers(String name, int age);
> 	// 네이티브 SQL을 활용한 예제
> 	@Query(value = "SELECT * FROM USER WHERE AGE > ?1", nativeQuery = true)
> 	 List<User> findUsersByNativeSql(int age); 
>}
> ```
> 바인딩 변수 : 메소드 파라미터의 값을 동적으로 하여 쿼리에 주입하는 변수
> 
>> 인덱스 바인딩
>
>?1, ?2는 바인딩 변수(binding variable)를 의미 
> 
> 예제
> 
> ```java
> @Query("SELECT u FROM User u WHERE u.name = ?1 AND u.age > ?2")
> List<User> findUsers(String name, int age); 
> // 메서드 호출
>List<User> users = userRepository.findUsers("홍길동", 20);
> ```
> 
> 실행
> 
> ```java
> SELECT * FROM User u WHERE u.name = '홍길동' AND u.age > 20
> ```
> 
> 바인딩 변수 사용의 장점은
> 1. SQL 인젝션 공격을 방지할 수 있다
> 2. 가독성이 높아진다
> 
>> 이름 바인딩
>
> :이름 바인딩 변수(binding variable)를 의미
> 
> 예제
> 
> ```java
> @Query("SELECT u FROM User u WHERE u.name = :name AND u.age > :age")
> List<User> findUsers(@Param("name") String name, @Param("age") int age);
> ```
> 
> `@Param` 사용하여 JPQL의 바인딩 변수 이름과 메서드 파라미터 이름을 매핑합니다.
> 이름 바인딩의 장점은 이름으로 표현되어 가독성이 높고, 코드 변경에 더욱 강건하다는 점입니다.
> 그래서 보통 이름 바인딩 방식을 선호합니다. 제시해주신 코드도 문제 없이 동작할 것입니다.

>[!note] @Modifying
>
> @Query을 사용할 때 insert, delete, update(select 제외) 쿼리를 사용할 때 반드시 사용해야 함


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
@Data
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
