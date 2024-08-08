📚 [HTML/CSS 베이스캠프 | 위니북스](https://www.books.weniv.co.kr/basecamp-html-css/chapter01/01-8)   

📍[CSS](#css)  
📍[CSS 적용방식](#css-적용-방식)  
📍[선택자](#선택자)  
📍[단위](#단위)  
📍[가상 클래스 & 가상 요소](#가상-클래스--가상-요소) 



# 💄 CSS
## CSS
Cascading Style Sheets의 약자  
HTML의 스타일, 레이아웃 등을 꾸미는 역할  
> Cascading(연속화)란? 🤔  
    '폭포'라는 의미   
    CSS에서 스타일이 적용될 때는, `우선순위`를 가지고 적용됨   
    우선순위가 적용되는 과정이 마치 폭포처럼 위에서 아래로 떨어지는 모양 !
  ![cascading](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter03/01-1.png)   

### CSS의 목표
1. `구조와 스타일의 분리` : HTML 문서는 콘텐츠와 구조를 정의하고, CSS는 스타일과 레이아웃을 정의함  
➡️ 문서의 구조적 의미가 명확해지고, 스타일을 변경할 때 HTML 코드를 수정할 필요가 없음
2. `일관된 디자인 유지` : CSS를 사용하면 여러 페이지에 동일한 스타일 적용 가능  
➡️ 웹사이트 전체에서 일관된 디자인 유지에 도움이 됨
3. `재사용성 및 효율성 향상` : 스타일 시트를 한 번 작성하면 여러 문서에서 재사용 가능  
➡️ 개발 시간을 단축시킴 + 코드의 중복 줄임


## CSS 적용 방식

각 방식은 용도와 장단점이 다르므로 상황에 따라 적절한 방식을 선택하여 사용하여야 함

#### 1. 인라인 방식
HTML 태그 내 `style` 속성을 통해 스타일을 직접 지정하는 방식  

```html
<p style="color: yellow; background-color: black;">Hello world</p>
```
- 장점: 
  - 빠르고 간편하게 특정 요소에 스타일을 적용할 수 있음
  - 소규모 테스트나 특수 목적에 유용

- 단점: 
  - 코드의 가독성이 떨어짐
  - 스타일이 길어질 경우 복잡도가 급격히 상승함
  - 가상 클래스와 가상 요소(:hover, ::before, ::after) 스타일 적용 불가
  - 재사용성이 떨어짐

#### 2. 내부 스타일
HTML 파일 내 `<style>` 태그를 사용하여 스타일을 정의하는 방식  

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>내부 스타일</title>
    <style>
        p {
            color: yellow;
            background-color: black;
        }
    </style>
</head>
<body>
    <p>Hello world</p>
</body>
</html>
```

- 장점: 
  - 인라인 방식보다 코드의 재사용성과 가독성 향상  
  - 한 파일 내에서 스타일을 관리할 수 있어 편리

- 단점: 
  - HTML 파일이 길어질수록 복잡도가 증가하여 효율성이 떨어짐
  - 대규모 프로젝트에서는 유지보수 어려움

#### 3. 외부 스타일
HTML 파일에서 `<link>` 태그를 사용해 외부 CSS 파일을 연결하는 방식  
HTML 파일과 분리하여 관리 가능

**<index.html>**
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>외부 스타일</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <p>Hello world</p>
</body>
</html>
```

**<style.css>**
```css
p {
    color: yellow;
    background-color: black;
}
```

- 장점: 
  - HTML과 CSS를 분리하여 코드의 가독성과 효율성, 유지보수성이 높아짐
  - 여러 HTML 파일에서 동일한 CSS 파일을 참조할 수 있어 스타일의 일관성 유지 가능
  - 대규모 프로젝트에 적합

- 단점: 
  - 외부 파일을 불러오기 때문에 로딩 속도가 약간 느려질 수 있음
  - CSS 파일이 많아질 경우 관리가 어려울 수 있음

    
### 선택자
#### 1. 전체 선택자(`*`)
HTML 문서 내의 모든 요소 선택  
reset.css에서 많이 사용됨  
> reset.css는 전체 선택자를 통해 브라우저마다 다르게 기본 설정된 스타일 초기화 -> 일관된 디자인 

```css
* {
  margin: 0;
  padding: 0;
}
```
💡 큰 프로젝트에서는 <u>특정 요소에만 스타일을 적용</u>하는 것이 성능상 효율적임

#### 2. 타입 선택자 (`tag`)
특정 HTML 태그를 선택  
특정 태그 <u>전체</u>에 스타일을 적용
```css
h1 {
  color: blue;
}
p {
  font-size: 32px;
  font-weight: bold;
}

```

#### 3. 아이디 선택자 (`#`)
특정 요소 선택  + 한 번만 사용 가능
```html
<header id="header">hello</header>
```
```css
#header {
  color: blue;
}
````

> `id` : HTML 문서 내에서 **한 번만 사용** 될 수 있는 고유한 식별자   
JavaScript와 함께 동적인 웹 페이지를 만들 때 사용  
해시 링크와 결합하여 `특정 위치로 바로 이동`할 수 있게 해줌  
ex) `#`: 프래그먼트 식별자(Fragment Identifier)
     ```   https://docs.python.org/3/tutorial/controlflow.html#defining-functions
    ```  
id="defining-functions"를 가진 요소로 스크롤  
  
#### 4. 클래스 선택자 (`.`)
특정 요소 선택 + 여러 번 사용 가능
 ```html
<h1 class="fc-red">hello wolrd</h1>
```
```css
.fc-red {
  color: red;
}
```

> 하나의 요소에 여러 개의 클래스 적용 가능!   
    ```
    <p class="text-large text-bold fc-red">Styled text</p>
    ```

#### 5. 특성 선택자 (`[]`)
특정 속성을 가진 요소 선택  
-> 속성 기준으로 스타일 지정
```html
<button type="button" class="btn">button</button>
<button type="submit" class="btn">submit</button>

```
```css
[type='button'] {
  border: 0;
  cursor: pointer;
}
```

#### 6. 그룹 선택자 (`,`)
여러 개의 선택자 선택 -> 중복 감소
```css
h1,
h2,
h3 {
  color: blue;
}
```

#### 7. 복합 선택자
<예시용 html 일부>
```html
<!-- ... -->
<section>
  <div>
    <p>lorem ipsum dolor sit amet</p>
  </div>
  <p>lorem ipsum dolor sit amet</p>
  <p>lorem ipsum dolor sit amet</p>
</section>
<p>lorem ipsum dolor sit amet</p>
<p>lorem ipsum dolor sit amet</p>
<p>lorem ipsum dolor sit amet</p>
```
  ![복합 선택자](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter03/03-1.png)   

#### 7-(1) 자손 선택자 (` `)
특정 요소의 `모든 하위 요소` 선택
```css
section p {
  font-weight: bold;
}
```
![자손 선택자](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter03/03-2.png)  

#### 9. 자식 선택자 (`>`)
특정 요소의 직계 자식 요소만 선택  

```css
section > p {
  color: royalblue;
}
```
![자식 선택자](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter03/03-3.png)  

#### 10. 일반 형제 선택자 (`~`)
`뒤에 나오는 형제만` 선택  
```css
section ~ p {
  text-decoration: underline;
}
```
![일반 형제 선택자](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter03/03-4.png)   

#### 11. 인접 형제 선택자 (`+`)
 `바로 뒤에 인접한 형제만` 선택
```css
section + p {
  background: yellow;
}
```
![인접 형제 선택자](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter03/03-5.png)  

### 단위 
#### 절대 길이 단위 
디바이스별로 다른 위치, 크기로 보이는 문제가 발생 🚨
- `px` (cm, mm, in, pc, pt ….)   

#### 상대 길이 단위 
- `%` : 부모 요소의 크기 기준
   ```css 
  .parent {
    width: 300px;
    background-color: #e0e0e0;
    padding: 10px;
  }
   .child {
    width: 50%; /*부모의 50% 너비*/
    background-color: #b0b0b0;
    padding: 10px;
  }
  ```
- `vm`, `vh`: 뷰포트(브라우저 창의 크기) 기준
  ```css
  .viewport-box {
    width: 50vw; /*뷰포트의 50% 너비*/
    height: 30vh; /*뷰포트의  30% 높이*/
    background-color: #d0d0d0;
    border: 1px solid #000;
    padding: 10px;
  }
  ```

- `em` : 부모 요소로부터 상속받은 요소의 글자 크기를 기준으로 하는 배수 단위
- `rem` : root em, 최상위 요소(`<html>`)의 글자 크기를 기준으로 하는 배수 단위
  ```css
  html {
    font-size: 16px;
  }
  .parent {
    font-size: 20px;
  }
  .em-child {
    font-size: 1.5em; /*부모의 20px * 1.5 = 30px*/
  }
  .rem-child {
    font-size: 1.5rem; /*루트의 16px * 1.5 = 24px*/
  }
  ```


### 가상 클래스 & 가상 요소
#### 1. 가상 클래스 선택자(Pseudo-class selectors)
요소의 특정 상태 선택 가능  
`:` 사용하여 표현

- 동적 가상 클래스 : `사용자의 동작`에 따라 변화하는 상태 선택
  ```css
  .hover-button {
    padding: 10px 20px;
    background-color: #3498db;
    color: white;
    border: none;
    transition: background-color 0.3s;
  }   
  .hover-button:hover { /*마우스  포인터가 요소 위에 올라간 경우*/
    background-color: #2980b9; /*배경색 변경*/
  }
  ```

- 구조적 가상 클래스 : 문서 구조 내에서 `요소의 위치`에 따라 선택
  ```css
  li:first-child { /*형제 요소 그룹 중 첫 번째 요소*/
    color: #e74c3c;
  }
   
  li:last-child { /*형제 요소 그룹 중 마지막 요소*/
    color: #2ecc71;
  }
  li:nth-child(even) { /*짝수 번째 항목 선택*/
    background-color: #f1f1f1;
  }
  ```

#### 2. 가상 요소(Pseudo-elements)
가상의 요소를 만드는 것  
선택한 요소의 특정 부분에 스타일 적용  
`::` 사용하여 표현
```css
.quote::before {
  content: "💙"; /*해당 요소의 앞에 내용 추가*/
  color: #3498db;
  font-size: 1.2em;
  margin-right: 5px;
}
 
.quote::after {
  content: "🦊"; /*해당 요소의 뒤에 내용 추가*/
  color: #3498db;
  font-size: 1.2em;
  margin-left: 5px;
}
```


