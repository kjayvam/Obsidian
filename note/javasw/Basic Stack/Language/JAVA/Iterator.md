### 주제 : #Iterator #이터레이터 #반복자

___

### Iterator란? : 

> iterator는 반복의 기술 용어기 때문에 반복자라고 한다
> 계산 같은 컴퓨터의 작업 처리 절차를 반복한다는 뜻 같다.
> **ArrayList, HashSet과 같은 컬렉션을 반복하는 데 사용할 수 있는 객체**다. 

### 사용하는 이유 : 

> List에는 인덱스가 있지만 Set은 순서가 없는(unordered) 컬렉션이기 때문에 인덱스가 없다...(중략)...iterator는 for-each 반복문이 할 수 없는 일을 할 수 있다. 
>> 예를 들어 iterator가 지원하는 경우 반복하는 동안 요소를 제거할 수 있다...(중략)...
> 
> 리스트는 또한 양방향으로 반복할 수 있는 iterator를 제공한다. 
> for-each 반복문은 처음부터 끝까지만 반복된다...(중략)...인덱스를 사용해 요소에 접근하는 것은 배열로 지원되는 컬렉션에서 약간 더 효율적이다.  
> 그러나 ArrayList 대신 LinkedList를 사용하면 list.get(i)에 액세스할 때마다 연결된 리스트가 i번째 요소까지 모든 요소를 반복해야 하기 때문에 성능이 나빠질 것이다. 
> iterator(따라서 for-each 루프)에는 이 문제가 없다. 컬렉션 자체에 iterator 구현이 있기 때문에 항상 주어진 컬렉션의 요소를 반복하는 가장 좋은 방법을 사용한다

### Iterator의 장점  : 

> 1. 컬렉션에서 요소를 제어하는 기능  
> 2. next() 및 previous()를 써서 앞뒤로 이동하는 기능  
> 3. hasNext()를 써서 더 많은 요소가 있는지 확인하는 기능

### Iterator VS for-each  

>[!note] Iterator
>
> ``` java
> ArrayList<String> 변수1 = new ArrayList<>();
> Iterator<String> 변수2 = 변수1.iterator();
> 
> while ( 변수2.hasNext()) {
> 	String 변수3 = 변수2.next();
> 	print(변수3);
> }
>```



>[!note] for-each
>``` java
> ArrayList<String> 변수1 = new ArrayList<>();
> 
> for ( String 변수3 : 변수1 ){
> 	print(변수3)
> }
>```

### 사용 예제 : 

``` java
public static void main(String[] args) { 
	// 컬렉션 생성 
	ArrayList<String> cars = new ArrayList<>(); 
	
	cars.add("벤츠"); 
	cars.add("람보르기니"); 
	cars.add("롤스로이스"); 
	cars.add("페라리"); 
	
	// iterator 획득 
	Iterator<String> iterator = cars.iterator(); 
	
	// while문을 사용한 경우 
	while(iterator.hasNext()) { 
		String str = iterator.next(); 
		System.out.println(str); 
	} 
		
	// for-each문을 사용한 경우 
	for (String str : cars) { 
		System.out.println(str); 
	} 
}
```

``` java
// 출력 결과 :
벤츠 
람보르기니 
롤스로이스 
페라리
```

### set 사용 예제 : 

``` java
public static void main(String[] args) { 
	// 컬렉션 생성 
	Set<String> cars = new HashSet<>(); 
	
	cars.add("벤츠"); 
	cars.add("람보르기니"); 
	cars.add("롤스로이스"); 
	cars.add("페라리"); 
	
	// iterator 획득
	Iterator<String> iterator = cars.iterator(); 
	
	// while문을 사용한 경우 
	while(iterator.hasNext()) { 
		System.out.println("cars : " + iterator.next()); 
	} 
	
	// for-each문을 사용한 경우 
	for (String car : cars) { 
		System.out.println("cars : " + car); 
	} 
}
```

``` java
// 출력 결과 :
cars : 벤츠 
cars : 람보르기니 
cars : 롤스로이스 
cars : 페라리
// Set을 사용했기 때문에 출력 시 넣은 순서와 상관없이 값이 출력되는 걸 볼 수 있다.
```

### 값을 수정하는 예제 :

``` java
public static void main(String[] args) { 
	// 컬렉션 생성 
	ArrayList<String> list = new ArrayList<>(); 
	
	list.add("A");
	list.add("B"); 
	list.add("C"); 
	list.add("D"); 
	list.add("E"); 
	list.add("F"); 
	System.out.println("while문 지나기 전 리스트에 들어있던 값 : " + list); 

	// iterator 획득
	ListIterator<String> listIterator = list.listIterator(); 
	
	// 리스트에 들어있는 값에 각각 '+' 붙이기 
	while(listIterator.hasNext()) { 
		Object element = listIterator.next(); 
		listIterator.set(element + "+"); 
	} 
	System.out.println("while문 지난 후 수정된 결과 : " + list); 
	
	// 리스트에 들어있는 값을 역순으로 표시 
	System.out.print("역순 출력 결과 : "); 
	while(listIterator.hasPrevious()) { 
		Object element = listIterator.previous(); 
		System.out.print(element + " "); 
	} 
	System.out.println(); 
}
```

``` java
// 출력 결과 :
while문 지나기 전 리스트에 들어있던 값 : [A, B, C, D, E, F] 
while문 지난 후 수정된 결과 : [A+, B+, C+, D+, E+, F+] 
역순 출력 결과 : F+ E+ D+ C+ B+ A+
```

___

### 출처(참고문헌)

- [iterator란?](https://onlyfor-me-blog.tistory.com/319)

___

### 연결문서

- [[0.자바란]]