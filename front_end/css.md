📚 [HTML/CSS 베이스캠프 | 위니북스](https://www.books.weniv.co.kr/basecamp-html-css/chapter01/01-8)   

📍[CSS](#css)  
📍[CSS 적용방식](#css-적용-방식)  


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

