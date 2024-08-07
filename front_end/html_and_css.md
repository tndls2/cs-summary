📍[HTML 기본구조](#html-기본구조)


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
