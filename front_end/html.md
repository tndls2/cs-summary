📚 [HTML/CSS 베이스캠프 | 위니북스](https://www.books.weniv.co.kr/basecamp-html-css/chapter01/01-8)   

📍[HTML 기본구조](#html-기본구조)  
📍[HTML 태그 모음](#html-태그-모음)


# 📄 HTML
## HTML 기본구조

<index.html>  
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body></body>
</html>
```
> **index.html** 인 이유 🤔   
>    `index.html` : 전통적으로 웹사이트나 웹 어플리케이션의 진입점 또는 시작 페이지로 사용되는 HTML 파일을 지칭함  
>    1. `웹 서버의 기본 설정`: 대부분의 웹 서버는 특정 디렉토리에 대한 HTTP 요청을 받을 때 기본적으로 index.html 파일을 찾음 (웹 서버의 기본 구성)
>    2. `관례와 편의성`:웹 개발 커뮤니티에서 널리 받아들여진 관례 ➡️ 협업 용이
>    3. `역사적인 이유`: 초기 웹 개발 단계에서 index.html 파일을 사용하는 관례가 생김  
초기 웹 사이트들은 파일 구조가 단순했고, index.html은 디렉토리의 주요 내용을 나타내는 인덱스 역할  ➡️ 현재까지 유지됨

1. `<!DOCTYPE html>` : 해당 문서는 html Living Standard 문서 라는 의미
2. `<html lang="en">` 
    - `<html>` : HTML 문서의 모든 내용을 포함하는 **최상위 요소** ➡️ 문서의 시작과 끝 표시
    - `lang`속성 : 해당 페이지의 주 언어 설정
        (언어코드 : ko, en, zh, ja, de 등)
3. `head`
  - 기계가 식별할 수 있는 **문서 정보(메타데이터)** 를 담음
  - 검색엔진을 위한 다양한 정보들이 담기는 곳

4. `meta`
  - **메타 데이터** = 데이터에 대한 데이터, 데이터를 설명하는 데이터  
  - 검색 엔진이 페이지를 분석할 때 사용됨
    ```html
    <meta name="description" content="제주 ICT 코딩 컴퓨터학원, 연구원, 출판사" />
    ```
5. `charset` : 문자 인코딩 방식을 지정하는 속성
  - `utf-8` :  전 세계적인 언어들을 지원하는 국제적인 코드 규약   
    ➡️ 어떤 언어로 작성하더라도 웹페이지 읽기 가능

6. `body` : 웹 페이지의 실제 내용을 담는 부분

## HTML 각종 태그
HTML 문서의 구조는 `트리 형태`로 이루어져 있음  ➡️ 각 요소들은 부모-자식, 형제 관계를 가짐  
![html 속성](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter01/02-3.png)   


```html
<html>
  <head></head>
  <body>
    <section>
      <h1>
        <strong></strong>
      </h1>
      <img />
      <div>
        <p><strong></strong></p>
        <p><strong></strong></p>
        <p><strong></strong></p>
      </div>
    </section>
  </body>
</html>
```

## HTML 태그 모음

### <Contents, 목록, Forms, Table 관련 태그>
| 태그 | 내용 | 표기 |속성 |
| --- | --- | --- | --- |
| heading| 제목 | `<h1>`~ `<h6>` |  |
| anchor | 하이퍼링크 | `<a href="">` | `href`:  링크가 가리키는 대상의 주소,  `target`: 링크를 클릭했을 때의 동작 (주요 값 : `_self`, `_blank`), `download`: 링크를 클릭했을 때 URL을 다운로드하도록 요청 |
| paragraph | 문단 정의 | `<p>` | |
| strong | 텍스트 bold 강조 | `<strong>` | |
| horizon rule | 수평선 | `<hr>` | |
| line break | 개행 | `<br>` | |
| ordered list | 순서가 있는 목록 | `<ol>` | 자식으로 `<li>`태그만 사용 가능 |
| unordered list | 순서가 없는 목록 | `<ul>` | 자식으로 `<li>`태그만 사용 가능 |
| list item | 목록의 항목 | `<li>` | |
| image | 이미지 삽입 | `<img src="" alt=""/>` | 빈 요소(void element),  `src`: 경로, `alt`: 대체 텍스트, 이미젱 대한 설명 |
| division | 레이아웃 구성(여러 태그들 그룹핑) | `<div>` | CSS로 스타일을 주기 전에는 콘텐츠나 레이아웃에 영향 ❌, `class`: 그룹명 |
| span | 인라인 요소 | `<span>` | CSS로 스타일을 주기 전에는 콘텐츠나 레이아웃에 영향 ❌, `class`: 그룹명 |
| form | 폼을 구성하는 컨테이너 역할 | `<form  action="/" method="POST">` | `action`: 폼 데이터를 처리할 서버의 URL, `method`: 데이터를 서버로 전송하는 방식 |
| input | 사용자로부터 데이터 입력 받음 | `<input type="" id="" name="">` | `type`: 입력 필드의 유형을 지정(ex. text, password 등)  ,`name`: 필드의 이름 (서버 측에서 name을 통해 데이터를 식별함), `id`: 레이블(label) 요소에서 for 속성을 사용하여 id 속성과 일치시킬 수 있음|
| label | 입력 필드의 설명 제공, 연결된 입력 요소에 포커스 맞춤  | `<label for="">` | `for`: 설명하는 입력 요소의 id 지정  |
|table| 테이블 요소 | `<table>`||
|table caption| 테이블의 제목| `<caption>`||
|table header| 테이블의 헤더 셀 | `<th>`| 기본적으로 굵은 글씨와 가운데 정렬 |
|table row| 테이블의 행 | `<tr>`||
|table data| 테이블의 데이터 셀| `<td>`||



> **빈 요소(void element)** 란 ? 🤔  
  : 자식을 가질 수 없는 태그  
   스스로 닫는(self-closing) 태그라고도 불림  
  🚨 빈 요소(void element)와 `스스로 닫는 태그`는 엄밀히 말하면 다름!   
    - [MDN 문서](https://developer.mozilla.org/en-US/docs/Glossary/Void_element) 에서 HTML은 
    ```
    Self-closing tags (<tag />) do not exist in HTML.
    ```
 라고 설명함  
    - 하지만 HTML에서는 빈 요소를 **스스로 닫는 태그로 사용하는 것을 허용**  
    ➡️ 빈 요소와 스스로 닫는 태그라는 용어를 혼용해서 사용하는 경우가 있음

### <Sections 태그>
HTML 문서를 의미적으로 구분하는 태그  
CSS로 스타일을 주기 전에는 콘텐츠나 레이아웃에 영향 ❌     
![section tags](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter01/02-5.png)   

| 태그 | 내용 | 표기 | 속성 |
| --- | --- | --- | --- |
| header | 웹 페이지의 상단 (사이트의 제목, 로고, 네비게이션 등 포함) | `<header>` | |
| navigation | 다른 페이지로 이동할 수 있는 링크들을 모아 놓은 섹션 | `<nav>` |  `<ul>`,`<ol>`,`<li>`태그와 함께 사용 |
| main | 문서의 주요 콘텐츠 | `<main>` | 웹 페이지에서 한 번만 사용 가능! |
| footer | 페이지의 하단 (작성자, 저작권 정보 등) | `<footer>` |  |
| section | 특정한 섹션을 정의, 주제나 콘텐츠를 구분 | `<section>` | 제목 요소 포함 필요, 주제별로 구분 |
| article | 독립적으로 구분해 배포하거나 재사용할 수 있는 구획 | `<article>` | 제목 요소 포함 필요, 독립적인 콘텐츠를 구분 |
| aside | 문서의 주요 내용과 간접적으로 연관된 부분 (사이드바, 광고, 관련 링크, 삽화, 인용구, 작은 웹 어플리케이션 등) | `<aside>` | `<nav>`태그 사용하여 관련 링크 제공 가능 |


