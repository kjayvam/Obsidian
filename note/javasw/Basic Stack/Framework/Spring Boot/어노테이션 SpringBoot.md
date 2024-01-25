### 날짜 : 2024-01-16 10:43

___

### 주제 : #SpringBoot #어노테이션 #Annotation

___

### 종류 : 

>[!note] @SpringBootApplication
>
> Srping Boot를 자동으로 실행시켜주는 어노테이션으로 Bean 등록은 두 단계로 진행된다.
> 
> - @ComponentScan을 통해 Component들을 Bean으로 등록한다.
> - @EnableAutoConfiguration을 통해 미리 정의해둔 자바 설정 파일들을 Bean으로 등록한다.
> 
>> (Bean은 스프링 IoC 컨테이너에 의해 인스턴스화되어 조립되거나 관리되는 객체)

>[!note] @Configuration
>
> 1. 스프링 IoC Container에게 해당 클래스가 Bean 구성 Class임을 알려주는 어노테이션이다.  
> 2. @Bean을 해당 클래스의 메소드에 적용하면 @Autowired로 빈을 부를 수 있다.

>[!note] @EnableAutoConfiguration
>
> 1. Spring Application Context를 만들 때 자동으로 설정하는 기능을 켠다.  
> 2. classpath의 내용에 기반해서 자동 생성해 준다.  
> 만약, tomcat-embed-core.jar가 존재하면 톰캣 서버가 setting된다.

>[!note] @ComponentScan
>
> 1. @Component, @Service, @Repository, @Controller, @Configuration이 붙은 빈들을 찾아서 Context에 빈을 등록해 주는 어노테이션이다.  
> 2. @Component 어노테이션이 있는 클래스에 대하여 bean 인스턴스를 생성한다.
>
> 3. Spring에서 @Component로 다 쓰지 않고 @Repository, @Service, @Controller등을 사용하는 이유는, 예를들어 @Repository는 DAO의 메소드에서 발생할 수 있는 unchecked exception들을 스프링의 DataAccessException으로 처리할 수 있기 때문이다.
> 
> 또한 가독성에서도 해당 애노테이션을 갖는 클래스가 무엇을 하는지 단 번에 알 수 있다.

>[!note] @Component
>
> 개발자가 직접 작성한 Class를 Bean으로 등록하기 위한 어노테이션이다.  
> `@ComponentScan`선언에 의해 특정 패키지 안의 클래스들을 자동 스캔하여 @Component 어노테이션이 있는 클래스들에 대하여 Bean 인스턴스를 생성한다.
> 
> ``` java
> @Component
> public class Student {
> 	public Stdudent() {
> 	System.out.println("hello");
> 	}
> }
> 
> @Component(value="mystudent")
> public class Student {
> 	public Stdudent() {
> 	System.out.println("hello");
> 	}
> }
> ```
> 
> Component에 대한 추가 정보가 없다면 Class의 이름을 camelCase로 변경한 것이 Bean id로 사용된다.  
> 하지만, @Bean과 다르게 @Component는 name이 아닌 value를 이용해 Bean의 이름을 지정한다.

>[!note] @Bean
>
> @Bean은 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만드려할 때 사용되는 어노테이션이다.
> 
> ```java
> @Configuration
> public class ApplicationConfig {
> 	@Bean
> 	public ArrayList<String> array() {
> 	return new ArrayList<String>();
> 	}
> }
> ```
> 
> ArrayList같은 라이브러리등을 Bean으로 등록하기 위해서는 별도로 해당 라이브러리 객체를 반환하는 Method를 만들고 @Bean을 사용하면 된다.
> 위의 경우 @Bean에 아무런 값을 지정하지 않았으므로 Method 이름을 camelCase로 변경한 것이 Bean id로 등록된다.  
> 메소드가 arrayList()인 경우 arrayList가 Bean id가 된다.
> 
> ```java
> @Configuration
> public class ApplicationConfig {
> 	@Bean(name="myarray")
> 	public ArrayList<String> array() {
> 	return new ArrayList<String>();
> 	}
> }
> ```
> 
> @Bean에 name이라는 값을 이용하면 원하는 id로 Bean을 등록할 수 있다.

>[!note] @Autowired
>
> 필드, setter 메소드, 생성자에 사용하며 Type에 따라 알아서 Bean을 주입해주는 역할을 한다.  
> 객체에 대한 의존성을 주입시킨다.  
> @Autowired을 사용하면 스프링이 자동적으로 값을 할당한다.  
> Controller 클래스에서 DAO나 Service에 관한 객체들을 주입 시킬 때 많이 사용한다.  
> 
> Bean을 주입받는 방식(3가지)
> 1. @Autowired
> 2. setter
> 3. 생성자: `@AllArgsConstructor 사용`, 스프링에서는 생성자를 통한 방식을 권장한다.

>[!note] @Controller
>
> Spring MVC의 Controller로 사용되는, 클래스 선언을 단순화 시켜주는 어노테이션이다.

>[!note] @RestController
> 
> Spring에서 Controller 중 View로 응답하지 않는 Controller를 의미한다.  
> method의 반환 결과를 JSON 형태로 반환한다.
>
> `@RestController`가 적혀있는 Controller의 method는 HttpResponse로 바로 응답이 가능하다.  
> @ResponseBody 역할을 자동적으로 해주는 어노테이션이다.

>[!note] @Service
>
> Service class에서 쓰이는 어노테이션으로, `비즈니스 로직`을 수행하는 Class라는 것을 나타내는 용도이다.

>[!note] @Repository
> 
> DAO class에서 쓰이는 어노테이션이다.  
> `DB`에 접근하는 method를 가지고 있는 Class에서 쓰인다.

>[!note] @Resource
>
> @Autowired와 마찬가지로 Bean 객체를 주입해주는데 차이점은 Autowired는 타입으로, Resource는 이름으로 연결해준다.
>
> javax.annotation.Resource  
> 표준 자바(JSR-250 표준) Annotation으로, Spring Framework 2.5.* 부터 지원 가능한 Annotation이다.
>
> 어노테이션 사용으로 인해 특정 Framework에 종속적인 어플리케이션을 구성하지 않기 위해서는 @Resource를 사용할 것을 권장한다.
>
> @Resource를 사용하기 위해서는 class path 내에 jsr250-api.jar 파일을 추가해야 한다.  
> 필드, 입력 파라미터가 1개인 bean property setter method에 적용 가능하다.

>[!note] @PreConstruct, @PostConstruct
>
> 의존하는 객체를 생성한 이후 초기화 작업을 위해 객체 생성 전이나 후에 실행해야 할 method 앞에 붙여 사용한다.

>[!note] @PreDestroy
>
> 객체를 제거하기 전에 해야할 작업을 수행하기 위해 사용한다.

>[!note] @PropertySource
>
> 해당 프로퍼티 파일을 Environment로 로딩하게 해준다.
>
> 클래스에 @PropertySource("classpath:/settings.properties")라고 적고 클래스 내부에 @Resource를 Environment타입의 멤버 변수앞에 적으면 매핑된다.

>[!note] @Lazy
>
> 지연 로딩을 지원하는 어노테이션이다.  
> @Component나 @Bean 어노테이션이다 같이 쓰는데 Class가 로드될 때 스프링에서 바로 bean등록을 마치는 것이 아니라 실제로 사용될 때 로딩되게 방법이다.

>[!note] @Value
>
> propertis에서 값을 가져와 적용할 때 사용한다.
> 
> ```java
> Value("${spring.redis.host}")
> private String host;
> ```

>[!note] @RequestMapping
>
> 어떤 URL을 어떤 method가 처리할 지 매핑해주는 어노테이션이다.  
> Controller나 Controller의 메소드에 적용한다.  
> 요청을 받는 형식인 GET/POST/PUT/PATCH/DELETE를 정의하기도 한다.  
> (정의하지 않으면 자동적으로 GET으로 설정된다.)
>
> ```java
> @RequestMapping("/")
> public String index(Model model) {
> 	model.addAttribute("list", bannerService.listAll());
> 	return "index";
> }
> ```

>[!note] @CookieValue
>
> 쿠키 값을 파라미터로 전달 받을 수 있는 방법으로, 해당 쿠키가 존재하지 않으면 500에러를 발생시킨다.
>
> ```java
> public String view(@CookieValue(value="auth") String auth) {
> 	.....
> }
> ```

>[!note] @CrossOrigin
>
> CORS 보안상의 문제로 브라우저에서 리소스를 현재 origin에서 다른 곳으로의 AJAX요청을 방지하기 위해 사용한다.  
> @RequestMapping이 있는 곳에 사용하면 해당 요청은 타 도메인에서 온 ajax요청을 처리한다.

>[!note] @ModelAttribute
>
> view에서 전달해주는 파라미터를 Class(VO/DTO)의 멤버 변수로 binding 해주는 어노테이션이다.  
> `<input name="id" />` 처럼 어떤 태그의 name값이 해당 Class의 멤버 변수명과 일치하고 setmethod명도 일치해야한다.

>[!note] @GetMapping
>
> @RequestMapping(Method=RequestMethod.GET)과 같은 역할을 한다.  
> 이 외에도 @PostMapping,@PutMapping, @DeleteMapping 등의 어노테이션도 있다.

>[!note] @SessionAttributes
>
> Session에 데이터를 넣을 때 사용하는 어노테이션이다.  
> @SessionAttributes("name")이라고 하면 Model에 key값이 "name"으로 있는 값은 자동으로 세션에도 저장되게 한다.

>[!note] @Valid
>
> 유효성 검증이 필요한 객체임을 지정한다.

>[!note] @InitBinder
>
>@Valid 어노테이션으로 유효성 검증이 필요하다고 한 객체를 가져오기전에 수행해야할 method를 지정한다.

>[!note] @RequestAttribute
>
> Request에 설정되어 있는 속성 값을 가져올 수 있다.

>[!note] @RequestBody
>
> 요청이 온 데이터를 바로 Class나 model로 매핑하기 위한 어노테이션이다.  
> POST나 PUT, PATCH로 요청을 받을때 Request로 넘어온 body 값들을 자바 타입으로 파싱해준다.
> 
> HTTP POST 요청에 대해 request body에 있는 request message에서 값을 얻어와 매핑한다.  
> RequestData를 바로 Model이나 클래스로 매핑한다.
> 
> 이를테면 JSON 이나 XML같은 데이터를 적절한 messageConverter로 읽을 때 사용하거나 POJO 형태의 데이터 전체로 받는 경우에 사용한다.
> 
> ```java
> @PostMapping("/api/posts")   
> public PostResponseDto createPost(@RequestBody PostRequestDto requestDto) {
> 	return postService.createPost(requestDto);
> }
> ```

>[!note] @RequestHeader
>
> Request의 header값을 가져올 수 있으며, 메소드의 파라미터에 사용한다.

>[!note] @RequestParam
>
> `@PathVariable`과 유사하다.  
> Request의 파라미터에서 가져오는 것이다. method의 파라미터에 사용한다.  
> `?name=rara`와 같은 쿼리 파라미터를 파싱해준다.
> 
> HTTP GET 요청에 대해 매칭되는 request 파라미터 값이 자동으로 들어간다.  
> URL뒤에 붙는 파라미터 값을 가져올 때 사용한다.  
> `http://localhost:8080/home?user_id=rara.log`
> 
> ```java
> @GetMapping("/account")
> public List<AccountInfo> getAccountByUserId ( @RequestParam("user_id") Long userId) {
> 	return accountService.getAccountByUserId(userId)
> 		.stream().map(AccountDto -> AccountInfo.builder()
> 			.accountNumber(AccountDto.getAccountNumber())
> 			.balance(AccountDto.getBalance())
> 			.build()).collect(Collectors.toList());
> }
> ```

>[!note] @RequestPart
>
> Request로 온 MultipartFile을 바인딩해준다.
> 
> ```java
> @RequestPart("file") MultipartFile file
> ```

>[!note] @ResponseBody
>
> HttpMessageConverter를 이용하여 JSON(or xml)으로 요청에 응답할 수 있게 해주는 어노테이션이다.  
> view가 아닌 `JSON 형식의 값을 응답할 때` 사용하는 어노테이션으로, 문자열을 리턴하면 그 값이 http response header가 아닌 response body에 들어간다.
> 
> 이미 @RestController 어노테이션이 붙어 있다면, 쓸 필요가 없다.  
> 허나 그렇지 않은 단순 컨트롤러라면, HttpResponse로 응답 할 수 있게 해준다.
> 
> 만약 객체를 return하는 경우 JACKSON 라이브러리에 의해 문자열로 변환되어 전송된다.  
> context에 설정된 viewResolver를 무시한다고 보면된다.

>[!note] @PathVariable
>
> method 파라미터 앞에 사용하면서 해당 URL에서 `{특정값}`을 변수로 받아올 수 있다.  
> HTTP 요청에 대해 매핑되는 request parameter 값이 자동으로 binding 된다.  
> URI에서 각 구분자에 들어오는 값을 처리해야 할 때 사용한다.
> 
> REST API에서 값을 호출할 때 주로 많이 사용한다.  
> `http://localhost:8080/api/posts/1`
> 
> ```java
> @GetMapping("/api/posts/{id}")   
> public PostResponseDto getPost(@PathVariable Long id) {
> 	return postService.getPost(id);
> }
> ```

>[!note] @ExceptionHandler(ExceptionClassName.class)
>
> 해당 클래스의 예외(Exception)를 캐치해서 처리한다.

>[!note] @ControllerAdvice
>
> Class위에 ControllerAdvice를 붙이고 어떤 예외를 잡아낼 것인지는 각 메소드 상단에 `@ExceptionHandler(예외클래스명.class)` 를 붙여서 사용한다.
> 
> ```java
> @ControllerAdvice
> public class CustomExceptionHandler {
> 
> 	@ExceptionHandler(AbstractException.class)
> 	protected ResponseEntity<ErrorResponse>handleCustomException(AbstractException e) {
> 		ErrorResponse errorResponse = ErrorResponse.builder()
> 													.code(e.getStatusCode())
> 													.message(e.getMessage())
> 													.build();
> 	return new ResponseEntity<>(errorResponse, HttpStatus.resolve(e.getStatusCode()));
> 	}
> }
> ```

>[!note] @RestControllerAdvice
>
> @RestControllerAdvice  =  @ControllerAdvice + @ResponseBody

>[!note] @ResponseStatus
>
> 사용자에게 원하는 Response code와 reason을 return 해주는 어노테이션이다.  
> 예외처리 함수 앞에 사용한다.
> 
> ```java
> @ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR)
> @ExceptionHandler(Exception.class)
> public Exception handleAllException() {
> 	System.out.println("error from GlobalExceptionHandler");
> 	return new Exception();
> }
> ```

>[!note] @Transactional
>
> DB 트랜잭션을 설정하고 싶은 method에 어노테이션을 적용하면 method 내부에서 일어나는 DB 로직이 전부 성공하게되거나 DB 접근중 하나라도 실패하면, 다시 롤백할 수 있게 해주는 어노테이션이다.
> 
> ```java
> @Transactional(readOnly=true)  -> 읽기 전용임
> 
> @Transactional(rollbackFor=Exception.class)  -> 해당 Exception이 발생하면 롤백한다.
> 
> @Transactional(noRollbackFor=Exception.class)  -> 해당 Exception이 발생해도 커밋한다.
> 
> @Transactional(timeout=10)  ->  10초 안에 완료되지 않으면 롤백한다.
> ```
> 
> 모든 처리가 정상적으로 됐을때만 DB에 커밋하며 그렇지 않은 경우엔 커밋하지 않는다.  
> 비즈니스 로직과 트랜잭션 관리는 주로 `Service`에서 관리한다.  
> 따라서 일반적으로 DB 데이터를 등록/수정/삭제 하는 Service 메소드는 @Transactional를 필수적으로 가져간다.

>[!note] @Cacheable
>
> method 앞에 지정하면 해당 method를 처음 호출하면 캐시에 적재하고, 그 다음부터는 동일한 method 호출이 있을 때 캐시에서 결과를 가져와서 return하므로 method 호출 횟수를 줄여주는 어노테이션이다.  
> 주의할 점은 ==입력이 같으면 항상 출력이 같은 method==에 적용해야한다.
> 
> 그런데 또 항상 같은 값만 뱉어주는 메서드에 적용하려면 조금 아쉬울 수 있다.  
> 따라서 메서드 호출에 사용되는 자원이 많고 자주 변경되지 않을 때 사용하고 나중에 수정되면 캐시를 없애는 방법을 선택할 수 있다.
> 
> ```java
> @Cacheable(key = "#companyName", value = CacheKey.KEY_FINANCE)
> ```

>[!note] @CachePut
>
> `캐시를 업데이트` 하기 위해서 method를 항상 실행하게 강제하는 어노테이션이다.  
> 해당 어노테이션이 있으면 항상 method 호출을 하기 때문에 @Cacheable과 같이 사용해서는 안된다.

>[!note] @CacheEvict
> 
> 캐시에서 데이터를 제거하는 트리거로 동작하는 method에 붙이는 어노테이션이다.
> 
> 캐시된 데이터는 언제가는 지워져야한다.  
> 그러지 않으면 결과값이 변경이 일어났는데도 기존의 데이터(캐시된 데이터)를 불러와서 오류가 발생할 수 있다.
> 
> 물론 캐시 설정에서 캐시 만료시간을 줄 수도 있다.
> 
> ```java
> @CacheEvict(value="cacheKey"), @CacheEvict(value="cacheKey", allEntries=true)
> ```

>[!note] @CacheConfig
>
> 클래스 레벨에서 공통의 캐시 설정을 공유하는 기능이다.

>[!note] @Scheduled
> 
> 정해진 시간에 method를 실행하게 하는 기능이다.
> 
> ```java
> @Transactional
> @Scheduled(cron = "0 0 1 * * *")
> public void weatherDateScheduling() {
> 	diaryServiceImpl.saveWeatherDate();
> }
> ```

>[!note] @PageableDefault
> 
> Pageable 인터페이스를 반환하는 메소드에서 사용합니다.
> 메소드에서 기본 페이지 사이즈, 정렬 조건 등을 지정할 수 있습니다.
> 
> ``` java
> @Repository
> public interface MemberRepository extends JpaRepository<Member, Long> {
>   @PageableDefault(page = 0, size=10, sort="id", direction=Sort.Direction.DESC)
>  Page<Member> findAll(Pageable pageable);
> }
> // 예) 시작 페이지 = 1페이지, 사이즈가 10개, 정렬기준 = id, 정렬 = 내림차순
> ```


### @Controller와 @RestController의 차이점

>[!note] @Controller
>
> API와 view를 동시에 사용하는 경우에 사용한다.  
> 대신 API 서비스로 사용하는 경우는 @ResponseBody를 사용하여 객체를 반환한다.  
> `view` return이 주목적이다.

>[!note] @RestController
>
> view가 필요없는 API만 지원하는 서비스에서 사용한다.  
> @RequestMapping 메서드가 기본적으로 @ResponseBody 의미를 가정한다.  
> `data` return이 주목적이다.

> 즉,  @RestController  =  @Controller  +  @ResponseBody
___

### 출처(참고문헌)

- [[Spring] 어노테이션(Annotation)](https://velog.io/@rara_kim/Spring-%EC%96%B4%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98Annotation)

___

### 연결문서

- [[0.Spring Boot]]
- [[Annotation]]

