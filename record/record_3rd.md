# HTML/CSS 강의 요약내용
오늘은 백준 빙고내기가 아닌 코딩애플에서의 HTML/CSS 강의를 듣고 정리하는 것으로 모각코 활동을 하였다.

처음부터 HTML/CSS 강의를 듣고 싶었던 건 아니고, 그 외의 다양한 강의를 듣고 싶었지만, 

HTML/CSS 강의를 먼저 듣고 이에 대한 기본 지식이 있어야 

다른 강의를 이해하는데 쉽다고 하여, 이 강의를 먼저 듣게 되었다.

## [1강] HTML 기초와 개발환경 셋팅
- HTML은 Hypertext Markup Language의 약자
- 자료의 구조를 표현하기 위한 언어
<img width="929" height="487" alt="image" src="https://github.com/user-attachments/assets/7d2f2969-801f-47c7-a41d-3fbe6fa28d9a" />

위는 HTML 파일의 기본 템플릿이다.

```html
<head>
```
내부엔 사이트 생성에 필요한 인코딩형식,사이트제목,css나 js파일 등

```html
<body>
```
내부엔 실제 웹사이트에서 보여줄 내용 등이 있어야 한다.
    
## [2강] HTML 기본 태그로 글 작성해보기
HTML은 <태그>로 작성한다.
```HTML
<p>안녕</p> 
```
이런 식의 태그들을 열고 닫은 후 내부에 글을 넣고 그림을 넣을 수 있다.

이러한 기본 태그들을 아래에 간단하게 정리해보겠다.

### 기본 태그 목록
<img width="953" height="378" alt="image" src="https://github.com/user-attachments/assets/b750adb0-6f10-446b-8ba0-50c84d7fa6f5" />

1. 태그를 열었으면 </태그명>으로 닫아야한다.
2. 닫지 않아도 되는 <img> 같은 태그도 몇 개 존재한다.
3. 특정 태그는 안에 href=" ", src=" " 이런 속성을 집어넣어서 추가정보를 기입가능하다.
    href는 클릭시 이동할 링크를 기입가능하고 src는 파일 경로를 기입가능하다.
4. HTML은 마크업언어이기에 용도에 맞는 태그를 사용해야한다.

**이미지를 눌렀을 때 다른 곳으로 이동하게 만들고 싶다면?**
<img width="959" height="223" alt="image" src="https://github.com/user-attachments/assets/d804c3b7-48ba-4be7-b63a-a311520c6fb3" />

위처럼 태그 안에 태그를 넣는 식으로 구성하면 가능하다!

### [2강] 과제
<img width="759" height="423" alt="image" src="https://github.com/user-attachments/assets/4573ea4a-e8b5-4062-a125-79775cef3eef" />

실제로 과제를 수행한 코드이다.

코드를 실행시키면
<div>
  <img width="400" alt="image" src="https://github.com/user-attachments/assets/97365e00-bd2b-4bfa-bfed-dd78dfa3fa33" />
  <img width="400" alt="image" src="https://github.com/user-attachments/assets/8ed1900a-b32a-4495-9cd3-c4dba5f039e1" />
</div>

첫 번째 사진과 같이 뜨고, 링크임을 누르면 구글로 이동한다.

---

## Markdown과 HTML 비교

Github를 25년도부터 사용했던 나는 Github의 문법이 HTML과 유사한 것 같아, 좀 더 알아보기로 하였다.

특히,
<img width="1376" height="207" alt="image" src="https://github.com/user-attachments/assets/ec468f31-4820-4e76-bb9c-77f42449b548" />

깃허브에서 사진을 넣을 때 위와 같이 마크다운을 작성했고,
<img width="1434" height="148" alt="image" src="https://github.com/user-attachments/assets/651a8590-c4ac-492d-948e-07abc9ab2bb9" />

이와 같이 두 사진을 나란히 넣을 때도 div로 감싸 이미지를 배치하였는데

Github Markdown에서 이러한 이미지를 넣을 때 사용하는 문법이 실제로 HTML <img> 태그 자체인지 궁금하여 이를 비교해보기로 했다.

실제로, GitHub에서 사용하는 Markdown 문법은 HTML로 변환된다.

### 제목

| Markdown | HTML | 
|----------|------|
| `# 제목` | `<h1>제목</h1>` |
| `## 제목` | `<h2>제목</h2>` |
| `### 제목` | `<h3>제목</h3>` |

### 텍스트 스타일

| Markdown | HTML | 결과 |
|----------|------|------|
| `**굵게**` | `<strong>굵게</strong>` | **굵게** |
| `*기울임*` | `<em>기울임</em>` | *기울임* |

### 링크

| Markdown | HTML |
|----------|------|
| `[텍스트](url)` | `<a href="url">텍스트</a>` |

### 이미지

| Markdown | HTML |
|----------|------|
| `![설명](url)` | `<img src="url" alt="설명">` |

### 리스트

**순서 없는 리스트:**

| Markdown | HTML |
|----------|------|
| `- 항목` | `<ul><li>항목</li></ul>` |

**순서 있는 리스트:**

| Markdown | HTML |
|----------|------|
| `1. 항목` | `<ol><li>항목</li></ol>` |

### Markdown에서 HTML 직접 사용

Markdown 파일(.md) 안에서 HTML을 바로 사용할 수 있다.
```markdown
# 마크다운 제목

일반 텍스트이다.

<div align="center">
  <img src="image.jpg" width="500">
</div>

다시 마크다운이다.
```

이렇게 두 문법을 섞어서 사용 가능하다!

정리하자면, Markdown은 HTML의 간편버전이라고 볼 수 있다.

자꾸 ``` 표시를 사용하지 않으면 내용을 감싸던 태그가 사라지고 안의 내용만 표시되길래 당황하였는데 이러한 이유로 그랬던 것이었다.

### 왜 HTML 문법을 사용했을까?
정말 많은 것들이 있는데 왜 HTML을 Markdown이 이용했는지 궁금하여 추가로 역사적(?) 배경을 찾아보았다
1. 웹 문서라서
   Markdown은 웹에 표시할 문서를 만드는 언어이다.
   결국 브라우저에서 보여주려면 HTML로 변환되어야 한다.
   Python이나 C는 프로그래밍 언어라서, HTML과 같은 문서 표시 언어를 사용해야한다.
2. 언어적 역할 비교
   <img width="948" height="420" alt="image" src="https://github.com/user-attachments/assets/657b36e0-6ca1-439c-abd4-a2ac51272c58" />
3. 우선 HTML은 너무 복잡하기 때문에 이를 Markdown으로 간단하게 표현
   그러나, 결국 브라우저에 보여줄 때는 HTML로 변환한다!
   곧, Markdown은 처음부터 HTML을 대체하려던 게 아니라 HTML을 보완하려고 만들어진 것으로 HTML을 쉽게 쓰는 도구라고 볼 수 있다. 다만 웹은 HTML이 필수다보니, 기초가 HTML로 시작된 것이다.

## [3강] 기본적인 웹페이지 스타일링
거의 모든 태그는 style="스타일값;" 이라는 속성을 열 수 있다.
여러개 사용시 뒤로 쭉 스타일값을 나열해주면 되지만 세미콜론을 까먹으면 안 된다.

## [4강] CSS 파일 만들고 첨부하는 법
클래스 selector는 .클래스명{ } 이렇게 적을 수 있고 모든
class="클래스명"을 가진 요소에 스타일을 적용가능하다.

아이디 selector는 #아이디명 { } 이렇게 적을 수 있고 모든
id="아이디명" 속성을 가진 요소에 스타일을 적용가능하다.

태그 selector는 p { 스타일~~ } 이렇게 적을 수 있고 모든
<p> 태그에 스타일을 적용가능하다.

``` md    
# 셀렉터의 우선순위
(점수가 높을수록 더 우선 적용됨)

style="" (1000점)
#id (100점)
.class (10점)
p (1점)
```
