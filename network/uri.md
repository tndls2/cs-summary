📍[URI](#url)  
📍[URL](#url)  
📍[웹 브라우저 요청 흐름](#웹-브라우저-요청-흐름)  

# 🛶 URI & 웹 브라우저 요청 흐름
## URI
Uniform Resource Identifier 의 약자 <br>
리소스를 식별하는 방법을 정의하는 개념 <br>

<종류>
- `URL`(Uniform Resource Locator): 리소스의 위치를 구체적으로 나타내는 주소
      
  ```
  http://www.example.com
  ftp://ftp.example.com/file.txt
  ```
  특정 네트워크 상에서 자원의 위치를 지정하여 해당 자원에 접근할 수 있도록 해줌

- `URN`(Uniform Resource Name): 리소스의 이름 나타냄
  ```
  urn:isbn:0451450523
  ```
  리소스의 위치와는 독립적으로 자원의 고유한 이름을 지정하여, 위치가 변경되더라도 동일한 자원을 식별 가능

  ![uri](https://images.velog.io/images/mumuni/post/21c77b70-773d-46f7-b39c-f9d5cfe27431/image.png)   

## URL

```
https://www.google.com/search?q=calendar&oq=calendar&sourceid=chrome&ie=UTF-8
```
<구성 요소> <br>
1. 프로토콜
   - `https://` : 보안이 강화된 HTTP
   - 웹 브라우저와 서버 간의 통신 방법을 정의
2. 호스트명
   - `www.google.com` : 구글의 웹 서버
   - 리소스가 위치한 서버의 이름
3. 포트 번호 
    - 기본 포트 번호가 사용됨 (https의 기본 포트 = 443).
    - URL에 명시되지 않으면 기본값 사용
4. 리소스 경로 
    - `/search` : 구글의 검색 기능에 접근하는 경로
    - 서버에서 특정 리소스의 위치
5. 쿼리 파라미터 
    - `q=calendar&oq=calendar&sourceid=chrome&ie=UTF-8`
    - 리소스에 전달되는 추가 데이터
    - ?로 시작
    - &로 구분
    - 키=값 형태의 string으로 서버에 전달


## 웹 브라우저 요청 흐름
**1. URL 입력 & DNS 조회**  
  클라이언트가 웹 브라우저에서 URL을 입력하면 입력한 DNS로 IP가 조회됨 <br>
  
  ![url 입력](https://blog.kakaocdn.net/dn/FzYIf/btrGUroTUTv/IfykRjEgCdrQlgk3W97laK/img.png)   
 <br>
 
**2. TCP/IP 연결 설정**  
  TCP 3-way Handshake 과정을 통해 클라이언트와 서버 간의 연결

**3. HTTP 요청 메시지 구성**  
-   웹 브라우저는 HTTP 요청 메시지를 생성함 <br>
-   요청 라인, 헤더, 본문 포함됨 <br>

  ![http 메시지](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fd5GiV5%2FbtrGWyOCizv%2FTy2EHNl7SYQzOue5L5mNY0%2Fimg.png)   
 
**4. 패킷 전송**  
  HTTP 요청 메시지는 TCP/IP 계층을 통해 패킷 단위로 전송됨 <br>
  
  ![http 메시지 전송 흐름](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FefPC4N%2FbtrGTZ6yvGk%2F1wDlAcnO1FlanP0QKZkd3K%2Fimg.png)   
 <br>
 
**5. 서버 응답 처리·응답**  
- 서버는 클라이언트로부터 받은 HTTP 요청 메시지를 처리함 <br>
- 요청에 따라 해당 리소스를 찾아 HTTP 응답 메시지 생성하여 전송 <br>
- 응답 메시지도 동일한 TCP/IP 계층을 통해 패킷 단위로 전송됨 <br>

  ![응답 패킷 전달](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ft2rXA%2FbtrGXf89cnU%2FYLFTanX9aHZ9aRVhLjuVn1%2Fimg.png)   

**6. 클라이언트 처리**  
- 패킷 수신 및 조립: 클라이언트 웹 브라우저는 서버로부터 받은 패킷을 재조립하여 HTTP 응답 메시지 완성
- HTML 렌더링: 웹 브라우저는 HTTP 응답 메시지의 본문(HTML, CSS, JavaScript 등)을 파싱하고 렌더링하여 사용자에게 웹 페이지를 표시 <br>

  ![응답 패킷 도착 및 웹 브라우저 렌더링](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FG19JG%2FbtrGS5zSSSw%2FqG4BIi9y8UWQM4v5Blmzf1%2Fimg.png)   
