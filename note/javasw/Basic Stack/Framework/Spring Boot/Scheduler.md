### 날짜 : 2024-01-16 12:29

___

### 주제 : #Scheduler #스케쥴러

___

### 설명 : 

> 스프링 스케쥴러는 일정 주기마다 특정 작업을 수행하기 위해서 사용된다.  
> 개발자가 하나하나 신경쓰지 않더라도 Scheduler의 기능을 이용하면 원하는 기능을 수행할 수 있게된다.

### 실행주기를 설정하는 방법 : 

- fixedDelay : 이전 수행이 종료된 지점을 기준으로 일정시간이 경과했을 때 다음을 수행
- fixedRate : 이전 수행이 시작된 지점을 기준으로 일정시간이 경과했을 때 다음을 수행

위의 두 가지 방법은 이전에 수행했던 수행시점을 기준으로 일정시간 후에 다음 수행을 시작한다.  

`fixedRate`의 경우 작업에 소요되는 수행 시간이 fixedRate에서 지정된 시간보다 길어지면 두 수행이 겹쳐서 발생할 가능성이 있기 때문에 fixedRate을 사용하여 스케쥴링을 할 때에는 주의가 필요하다.

### Cron 표현식

| 필드 | 허용되는 값 | 허용되는 특수문자 |
|---|---|---|
| 초 | 0-59 | * , - |
| 분 | 0-59 | * , - |
| 시 | 0-59 | * , - |
| 일 | 1-31 | * , - ? L W |
| 월 | 1-12 or JAN-DEC | * , - |
| 요일 | 0-6 or SUN-SAT | * , - ? L # |
| 년도 | 1970-2099 | * , - |

- 스케쥴링 시간은 정규 표현식을 사용하여 표현하는 규칙
- 초 / 분 / 시 / 일 / 월 / 요일 / 년도(생략가능)
- `0 5 * * * *` : 매시 5분마다 작업을 수행
- `0 0/10 * * * *`10분에 한번씩 작업을 수행
- 콤마(,)  
	특정 여러 시간 지정  
    ex) MON, WED, FRI     ->     월요일, 수요일, 금요일
    
- \-  
    범위(기간) 지정  
    ex) 2000–2010     ->     2000 년에서 2010 년 사이의 매년
    
- L  
    지정할 수 있는 범위의 마지막 값(날짜와 요일에만 사용)  
    ex) 요일 필드에 5L     ->     해당 월의 마지막 금요일
    
- W  
    일 필드에서 허용. 주어진 요일에 가장 가까운 평일(월-금)을 지정  
    ex) 15W     ->     15일이 토요일이라면 금요일날 실행
    
- 요일 필드에서 허용. 뒤에 1-5사이의 숫자가 와야함  
    ex) 5  #  3     ->     매월 세번째 금요일
    
- ?  
    조건 없음(날짜와 요일에만 사용)
    
- /  
    시작 시간과 반복 간격  
    ex) *  /  5     ->     5분마다 실행
    
- \*  
    모든 수
    
### 예시

- 0  0  14   *   *   *             : 매일 오후 2시
- 0  0  0  1   *   *                : 매달 1일 0시
- 0  5  1  ?  7  MON-WEB : 매년 7월 월-수 1시 5분

### 스케줄링 사용하기

> 스프링에서 스케줄링을 사용하기 위해서는 Main 클래스에 `@EnableScheduling` 어노테이션을 붙여줘야 한다.

```java
@SpringBootApplication
@EnableScheduling
public class Application {
	
    public static void main(String[] args) {
    	SpringApplication.run(Application.class, args);
    }
}
```

> 5초마다 현재 시간을 출력하는 코드를 작성해 보면 아래와 같다.

```java
@Component
public class TestScheduler {

	@Scheduled(cron = "0/5 * * * * *")
	public void test() {
		System.out.println("now: " + LocalDateTime.now());
	}
}
```

> 코드를 작성하고 실행을 누르면 아래와 같이 5초마다 현재시각이 출력되는 것을 볼 수 있다.

![](https://velog.velcdn.com/images/rara_kim/post/9195ffdb-effa-4a64-bb0b-ff0d304bc0aa/image.png)

___

### 출처(참고문헌)

- [Scheduler](https://velog.io/@rara_kim/Spring-Scheduler)

___

### 연결문서

- [[0.Spring Boot]]

