### 날짜 : 2024-03-26 00:22

___

### 주제 : #Bootstrap #클래스 #BootstrapSpacing #공백 #Spacing #Notation

___

### Notation : 

>[!note] M / P {property}
>
>  - M : Margin
>  - P : Padding

>[!note] t, b, l , r, x, y {sides}
>
> - t : top
> - b : bottom
> - s : left (start)
> - e : right (end)
> - x : x축 -> left , right
> - y : y축 -> top , bottom

>[!note] 0, 1, 2, 3, 4, 5, auto {size}
> 
> - 0 : 0
> - 1 : 0.25rem( font-size가 16px이면, 4px) 크기
> - 2 : 0.5rem( font-size가 16px이면, 8px) 크기
> - 3 : 1rem( font-size가 16px이면, 16px) 크기
> - 4 : 1.5rem( font-size가 16px이면, 24px) 크기
> - 5 : 3rem( font-size가 16px이면, 48px) 크기
> - auto : margin의 자동으로 세팅
> 
>> `em`과 `rem`은 둘 다 CCS의 `font-size` 속성값에 비례해서 결정되는 상대 단위입니다. 
>> 예를 들어, `font-size: 16px`인 경우, 상대 단위는 브라우저에 의해서 다음과 같이 계산됩니다.
>
>> `em`과 `rem` 단위의 기준 :
>> 
>> `em`의 경우, 해당 단위가 사용되고 있는 요소의 `font-size` 속성값이 기준이 됩니다. 
>> `rem`에서 `r`은 `root`, 즉 최상위 요소를`font-size` 속성값 의미합니다. 
>> HTML에서 최상위 요소는 `<html>` 입니다. 
>> 따라서 `rem` 경우, `html` 요소의 `font-size` 속성값이 기준이 됩니다.

>[!note] n1, n2, n3, n4, n5 {size}
>
> - n : negative(음수 마진)을 의미 
> - n1 : -0.25rem( font-size가 16px이면, -4px) 크기
> - n2 : -0.5rem( font-size가 16px이면, -8px) 크기
> - n3 : -1rem( font-size가 16px이면, -16px) 크기
> - n3 : -1rem( font-size가 16px이면, -16px) 크기
> - n4 : -1.5rem( font-size가 16px이면, -24px) 크기
> - n5 : -3rem( font-size가 16px이면, -48px) 크기

### Border


```js
// 테두리 방향
.border-top, end, bottom, start 

// 테두리 색상
.border-primary, white, ...

// 테두리 두께
.border-1 ~ 6

// 테두리 둥근 모서리 형태
.rounded-top, circle, pill, ...

// 테두리 둥근 모서리 크기
.rounded-0 ~ 3
```

### Width / Height

```js
// width
.w-25 == width: 25%
-25, 50, 75, 100, auto

// height
.h-50 == height: 50%

// max-width
.mw-40 == max-width : 40%

// max-height
.mh-100 == max-height : 100%

// viewport
min-vw-100
min-vh-100
vw-100
vh-100
```

### BackGround

```js
// 배경색
.bg-primary, white, ...

// 배경 그라데이션
.bg-gradient
```

### Display

```JS
// xs크기 에서만 적용
.d-{value}
.d-inline-block
.d-grid

// 중단점 명시
.d-{breakpoint}-{value}
.d-lg-block

/* value 값 */
none : 요소를 숨김
inline : 인라인처럼 표시
inline-block : 인라인 요소처럼 표시, 블록요소처럼 너비와 높이를 설정 가능
block : 블록처럼 표시, 너비와 높이 설정 가능
grid : 그리드 레이아웃을 사용
table : 테이블 처럼 표시
table-cell : <td>,<th>처럼 테이블 셀로 표시
table-row : <tr>처럼 테이블의 행으로 표시
flex : 플렉스박스 레이아웃으로 표시
inline-flex : 플렉스박스 레이아웃으로 표시, 인라인처럼 표시
```

```js
d-print-none : 인쇄할 때 안보이게 설정
```

### Float

```JS
.float-nono, left, right, start, end, none

// 반응형
.float-sm-start, ...
```


___

### 출처(참고문헌)

- [공백(Spacing) 주기](https://minaminaworld.tistory.com/136)
- [클래스 이름 익혀보기](https://inpa.tistory.com/entry/BootStrap5-%F0%9F%93%9A-%EB%B6%80%ED%8A%B8%EC%8A%A4%ED%8A%B8%EB%9E%A9-%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%9D%B4%EB%A6%84-%EC%A0%95%EB%A6%AC#width_/_height)

___

### 연결문서

- [[0.Bootstrap]]
- [[클래스 패턴]]

