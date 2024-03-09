### 날짜 : 2024-01-30 13:36

___

### 주제 : #button #onClickEvent

___

### 1개만 사용 할 때 : 

``` html
<script>
    document.addEventListener('DOMContentLoaded', onClickEvent); 

    function onClickEvent() {

        let btn = document.getElementById('moveBtn');
        btn.addEventListener('click', moveFunction);

        function moveFunction() {

            location.href = '/';
        }
    }
</script>

<body>
    <button id="moveBtn">게시판 이동</button>
</body>
```

> button의 id를 이용하는 방법

``` html
<script>
    document.addEventListener('DOMContentLoaded', onClickEvent);

    function onClickEvent() {

        let listBtn = document.getElementsByName('moveBtn')[0];
        listBtn.addEventListener('click', moveFunction);

        function moveFunction() {

            location.href = '/';
        }
    }
</script>

<body>
    <button name="moveBtn">게시판 이동</button>
</body>

```

> button의 name를 이용하는 방법

### 2개를 사용 할 때 :

``` html
<script>
    document.addEventListener('DOMContentLoaded', onClickEvent);

    function onClickEvent() {

        let listBtn = document.getElementsByName('moveBtn');

		for(let i = 0; i < idBtns.length; i++) { 
			listBtn[i].addEventListener('click', moveFunction); 
		}

        function moveFunction() {

            location.href = '/';
        }
    }
</script>

<body>
    <button name="moveBtn">게시판 이동1</button>
    <button name="moveBtn">게시판 이동2</button>
</body>

```

### 차이점 :

>[!note] id와 name의 차이 = 리턴값
>
> getElementById는 단수(singular)입니다. 
> 
> - id 속성은 중복이 허용되지 않기 때문에 0개 또는 1개의 엘리먼트만 선택 가능.
> 
> getElementsByName은 복수(plural)입니다. 
> 
> - name 속성은 중복이 허용되므로, 동일한 name을 가진 여러 엘리먼트들이 존재.
> - NodeList 타입의 객체가 반환되는데, 이는 배열과 유사한 iterable 객체입니다.

___

### 출처(참고문헌)

- [DOMContentLoaded 이벤트](https://developer.mozilla.org/ko/docs/Web/API/Document/DOMContentLoaded_event)
- [addEventListener](https://ko.javascript.info/introduction-browser-events)

id, name 차이

- [getElementsByName과 getElementById 사용방법](https://blog.naver.com/ssuyastory/100168541817)
- [[javascript] getElementById()와 getElementByName()](https://jayheya.tistory.com/entry/javascript-getElementById%EC%99%80-getElementByName)
- [(JavaScript)getElementById VS getElementsByName(getElementsByTagName)](https://blog.naver.com/qbxlvnf11/220854728639)

___

### 연결문서

- [[0.JS]]

