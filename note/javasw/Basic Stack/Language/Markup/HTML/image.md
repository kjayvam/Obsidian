### 날짜 : 2024-01-29 10:21

___

### 주제 :  #HTML #image #images디렉토리  #CSS디렉토리 

___

### 디렉토리 : 

>[!note] css
>
> ``` html
> <head>
> 	<link href="/static/css/스타일.css" rel="stylesheet" type="text/css"/>
> </head>
> ```

>[!note] image
> 
> ``` html
> <body>
> <img src="/static/images/이미지.png">
> </body>
> ```

### 속성 :

- src : 이미지의 경로
- alt : 이미지를 표시할 수 없을 때 출력할 내용
- title : 마우스를 이미지 위에 올리면, `title` 속성 뒤에 적힌 문장이 출력됩니다.
- width : 이미지의 가로 크기
- height : 이미지의 세로 크기

### 

### 예시 : 

``` html
<img src="이미지.jpg" />
```

> 이미지가 HTML 페이지와 같은 경로에 있을 경우

``` html
<img src="images/dinosaur.jpg" />
```

> 이미지가 HTML 페이지와 같은 부스의 `images`하위 대표에 해당하는 경우에는 새롭게 삽입할 수 있습니다.

```html
<img src="https://www.example.com/images/dinosaur.jpg" />
```

> 절대 URL을 사용해서 이미지를 삽입할 수도 있습니다. (권장하지 않습니다.)

___

### 출처(참고문헌)

- [HTML의 이미지](https://developer.mozilla.org/ko/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)
- [일정한 사이즈 div 안에 이미지 넣기 (잘리면서 꽉차게, 잘리지 않고 축소)](https://multifidus.tistory.com/182)

___

### 연결문서

- [[0.HTML]]

