## HTML/CSS All-in-one : 기초부터 Bootstrap, SASS, animation
<img width="1279" height="815" alt="image" src="https://github.com/user-attachments/assets/14685147-3c6c-4235-8618-7edf1e07c80e" />

위 강의에서는 표준 HTML부터 flex/grid 모던 레이아웃, Bootstrap, Sass, CSS 애니메이션 등

웹페이지 디자인과 퍼블리싱에 필요한 모든 내용을 배울 수 있다.

최근 스타트업, 대기업 등에서 적극 사용하고 있는 최신 스타일 HTML과 CSS 문법을 배워갈 수 있다.

지난 모각코 회차에서 4강까지 수강했기 때문에 5강부터 이어서 수강하고, 이에 대한 정리본을 써보도록 하겠다.

이번 회차에서는 5강부터 10강까지의 정리본을 작성해볼 것이다.

## [5강] 웹레이아웃의 기초 : div를 이용한 네모네모 박스 디자인
<img width="1293" height="874" alt="image" src="https://github.com/user-attachments/assets/e48fd0b4-bb7a-4d3a-aa6b-152d01feee44" />

### 네모 박스 디자인에 많이 사용하는 CSS 속성
<img width="1291" height="348" alt="image" src="https://github.com/user-attachments/assets/17d9fafc-06f6-4b29-b2f6-0502ad8a0cd1" />

이 때, margin은 바깥 여백

padding은 안쪽 여백

border는 테두리 (차례로 두께, 선의 종류, 색상)

border-radius는 테두리 둥글게 처리이다.

가운데 정렬도 많이 하는데 저번 회차에서 정리했듯이,

display : block; margin-left : auto; margin-right : auto 이렇게 주면 된다.

### margin과 padding을 원하는 방향에만 줄 수 있다!
<img width="1279" height="257" alt="image" src="https://github.com/user-attachments/assets/fcc106ee-db81-45f0-a73b-178e95f56a82" />

top, left, bottom, right 중 원하는 곳에만 여백을 줄 수 있다. 

(참고) margin은 음수도 가능하다. -20px 이런 식이다.

(참고) margin : 5px 6px 7px 8px; 이렇게 띄어쓰기를 이용해 작성하면

차례로 상 우 하 좌 마진을 5,6,7,8px 한번에 줄 수 있다. 

### display : block이 내장되어있는 div 박스
<img width="1277" height="206" alt="image" src="https://github.com/user-attachments/assets/70cb7e58-5286-455a-9741-86ac9b1eb0d7" />

모든 div, p, h1, li 등은 display : block 속성을 주지 않아도 기본적으로 내장되어있다. 

그래서 p태그나 div태그를 그냥 사용하면 한 행을 전부 차지하게 된다. 

이게 싫다면 display 속성을 다른 것으로 부여해주면 된다.

display : inline, inline-block, flex 등 여러가지가 있다. 

**일부 스타일은 inherit 된다.**

font-size, color, font-family, text-align 이런 속성들은

부모 태그에 쥐어주면 거기 안에 있던 태그들까지 전부 상속된다. 

=> 영어로 inherit 된다고한다. 

안에 글자들이나 태그들이 많을 경우 전부 font-size를 작성안해도 

부모태그에 한번에 작성하고 끝낼 수 있으니 편리하다. 

다 inherit되는건 아니고 글자와 관련된 스타일들이 주로 inherit 된다.  

### box-sizing : border-box
CSS에서 박스 크기 계산 방식 때문에 레이아웃 깨지는 일이 많은데, 이를 해결해주는 속성이 box-sizing이다.

```html
* {
  box-sizing: border-box;
}
```
기본값은 content-box

width/height에 padding/border가 포함되지 않는다.

border-box로 설정하면

width/height 안에 padding/border까지 포함된다.

=> 즉, 원하는 크기대로 레이아웃 제어가 쉬워진다.

따라서 실전에서는 거의 무조건 border-box를 전체 적용하는 편이다.

### margin collapsing (마진 겹침) 현상
수직 방향으로 박스를 쌓을 때 마진이 기대한 것보다 작게 보일 수 있는데, 이는 마진 겹침 현상 때문이다.

예를들어,

위 요소 margin-bottom: 30px

아래 요소 margin-top: 20px

이면 둘이 합쳐져 50px이 아니라 큰 쪽(30px)만 적용될 수 있다.

=> 해결 방법 :

중간에 padding을 주기

부모에 overflow: hidden; 또는 display: flow-root; 같은 방식 사용

### display 속성 보강 : inline / block / inline-block 차이
1) inline
   - 줄바꿈 없음
   - width/height 적용 X
   - padding은 되지만 레이아웃 제어 제한 있음
   - 대표 태그 : span , a
2) block
   - 한 줄 전부 차지
   - width/height 적용 O
   - 레이아웃 제어 쉬움
   - 대표 태그 : div , p , h1
3) inline-block
   - 줄바꿈 없음
   - width/height 적용 O
   - 버튼/배지 같은 UI 만들 때 유용

## [6강] 레이아웃 만들기 1 : 호환성 좋은 float
<img width="1281" height="735" alt="image" src="https://github.com/user-attachments/assets/cb802834-9b25-453b-864e-30b4fddef324" />

### html css로 사이트 레이아웃 만드는 법
만들고 싶은 레이아웃 디자인 위에 네모박스를 먼저 그려보고 바깥 네모부터 <div> 써서 구현하면 된다.

어려워보이는 레이아웃도 네모박스부터 그 위에 그려보고

바깥 네모부분부터 <div>로 하나하나 만들기 시작하면

그럼 무슨 레이아웃을 가져다주든 알아서 만들 수 있음

**Example 1)**

<img width="516" height="419" alt="image" src="https://github.com/user-attachments/assets/64e97925-f96f-4508-aa22-e0dc491d0770" />

▲ 예를 들어 당근마켓 상품하나 레이아웃을 구현하고 싶으면

네모박스처럼 보이는걸 전부 네모로 표시해보고

바깥 네모 부터 하나하나 <div>로 구현하라는 것이다.

물론 문자는 <p> 이미지는 <img> 이런거 쓰는게 좋음

그리고 그러려면 박스를 정렬하고 배치하는 법도 알아야한다.

### 요소를 공중에 띄워 왼쪽/오른쪽 정렬하는 float 속성
<img width="992" height="430" alt="image" src="https://github.com/user-attachments/assets/43294f5e-9b2d-47ed-901d-d07661e1211d" />

- 위의 코드는 박스 두개를 만들어 각각 왼쪽으로 정렬시킨다.

- 하지만 float를 쓰면 요소를 붕 띄우다보니 그 다음에 오는 HTML 요소들이 제자리를 찾지 못한다. 

(참고) float 속성으로 가로정렬할 땐

float 박스들을 싸매는 하나의 큰 div 박스를 만들고 폭을 지정해주는게 좋다.

그래야 모바일에서 안 흘러넘치기 때문

이건 React로 웹 개발할 때 수도없이 겪었기 때문에 빠르게 이해가 됐다.

### float를 쓰고 나면 항상 clear 속성이 필요하다.
<img width="990" height="292" alt="image" src="https://github.com/user-attachments/assets/15fd676a-c432-4300-a16a-ba01bd51124f" />

clear 속성을 사용하면 float 다음에 오는 박스들이 제자리를 찾게 된다.

float를 썼으면 까먹지 말고 항상 넣어야한다.

안 넣으면... 내 의도와는 다른 레이아웃이 뜬다고 한다.

참고로 float : none 이것도 추가해주는 게 나중에 생길 버그 예방차원에서 좋다고 한다.

