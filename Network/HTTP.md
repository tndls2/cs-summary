📍[HTTP](#http)   
📍[HTTP 요청](http-요청request)   
📍[HTTP 응답](http-응답response)   
📍[HTTP/1.1](#http11)  
📍[HTTP 특징](#http의-특징)    
    - [🤔 상태유지와 무상태](#-상태유지와-무상태)   
    - [🤔 지속 연결(Persistent Connections)](#-지속-연결persistent-connections)

# 💡 HTTP 기본
## HTTP
Hyper Text Transfer Protocol의 약자 <br>
웹에서 정보를 주고받기 위해 사용되는 프로토콜 <br>
클라이언트-서버 모델 기반 ➡️ 클라이언트가 `요청`을 보내고 서버가 이에 대한 `응답`을 반환하는 방식으로 동작

![클라이언트-서버 구조](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FOnL4v%2FbtrpUHuLzMb%2FwQvDJYnkFoTDWpk8UAFflk%2Fimg.png)   


## HTTP 요청(Request)
클라이언트가 서버에 자원을 요청하는 행위 <br>
```http
GET /user HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
Cookie: _gid=test
User-Agent: Mozilla/5.0
```
<구조>
- **시작 라인(Start Line)**: 요청 메서드(GET, POST 등), 경로(Path), 프로토콜 버전(HTTP/1.1 등)
- **헤더(Header)**: 추가적인 정보(Host, Accept-Language, Cookie, User-Agent 등)
- **공백 라인(Empty Line)**
- **본문(Body)**: 선택적으로 데이터 포함


## HTTP 응답(Response)
서버가 클라이언트의 요청에 대해 반환하는 데이터

```http
HTTP/1.1 200 OK
Date: Wed, 01 Jun 2022 23:45:23 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2022 20:18:22 GMT
ETag: "WY63nS6c/0pdK1V6Sw02/vT6oVU="
Access-Control-Allow-Origin: *
Content-Type: text/html

<html>
    <body>...</body>
</html>
```
<구조>
- **시작 라인(Start Line)**: 프로토콜 버전(HTTP/1.1), 상태 코드(200 등), 상태 메시지(OK 등)
- **헤더(Header)**: 응답에 대한 정보(Date, Server 등)
- **공백 라인(Empty Line)**
- **본문(Body)**: 실제 응답 데이터(HTML, JSON 등)

> Content-Type : 응답값의 형태를 정의 <br>
    <종류> <br>
        - application/x-www-form-urlencoded <br>
        - multipart/form-data <br>
        - text/plain <br>
        - text/html <br>
        - image/png <br>
        - image/jpeg <br>

## HTTP/1.1
가장 표준화된 HTTP 버전  
하나의 연결로 여러 번의 요청과 응답을 처리할 수 있는 `Connection: keep-alive`기능을 제공   
➡️  매번 연결을 하지 않아도 되는 효율적인 통신

![HTTP/1.1](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTzNs5Erpi5ckwTE-9ZhdiAlPZiZJW_lTAAUg&s)   


## HTTP의 특징
1. **HTTP 메시지로 모든 데이터 전송 가능** :  HTML, JSON, 이미지, 영상 등 다양한 형태의 데이터를 전송 가능
2. **클라이언트-서버 모델**  
3. **무상태(stateless) 프로토콜**  
   - 서버가 클라이언트의 상태를 유지하지 않음
   - `상태 유지`를 위해 `토큰(JWT), 세션, 쿠키`를 사용할 수 있음
4. **비연결성(connectionless)**
   - 기본적으로 연결을 유지하지 않음
   - 효율적인 자원 사용이 가능하지만, 매 요청마다 연결을 맺어야 함
   - 이를 해결하기 위해 `지속 연결(Persistent Connections)` 사용

### 🤔 상태유지와 무상태
- **상태유지(Stateful)**: 서버가 클라이언트의 상태를 기억하고 유지함
        ![상태유지](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcoUvAI%2FbtrpVwTVWem%2FEFbrRnZi0GypNeLgbItsX0%2Fimg.png) <br>
    상태를 유지하게 되면 서버 1에 요청한 고객은 서버 1과 통신을 해야함  
(서버 2와 서버 3은 해당 클라이언트의 상태를 모름)  
🚨요청을 처리하기 위해 해당 클라이언트의 상태를 가지고 있는 서버만 사용되므로, 특정 서버에만 요청이 몰리는 경우가 발생할 수 있음  

    ![상태유지 - 서버 장애](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtQ9F2%2FbtrpPVN5qj0%2Fc3YNs7wbN23egXDtsZA6BK%2Fimg.png)   
⚠️ 서버 1에서 장애 발생 시, 서버 1에서 저장한 클라이언트의 정보는 모두 소실됨

- **무상태(Stateless)**: 서버가 클라이언트의 상태를 유지하지 않음 <br>
➡️ 클라이언트가 필요한 모든 정보를 매 요청마다 포함하여 보내야 함
        ![무상태](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FUDit3%2FbtrpU35pPpz%2FEKAkCtn2mmvbU4n9fmYkl1%2Fimg.png)   
서버는 매 요청마다 필요한 정보들을 클라이언트로부터 받기 때문에 어느 요청을 받아도 동일한 응답 제공 가능  
서버를 증설하거나 줄이거나 등의 확장성도 Statsfull방식에 비해 높음  
➡️ 하나의 서버에서 장애가 발생하더라도,  다른 서버에서 클라이언트의 요청 처리 가능


### 🤔 지속 연결(Persistent Connections)
HTTP 지속 연결을 통해 한 번 맺은 연결을 여러 요청과 응답에 재사용하여 비연결성의 단점을 극복함. 

![비연결성](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdcXDoS%2FbtrpJXznmVI%2FzzApue7U2JwlkFxviymAmk%2Fimg.png)   

한 페이지 요청시 페이지가 모두 로딩되기까지 초기에 맺어진 커넥션을 끌고감   
![지속 연결](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcaToct%2FbtrpU08RZ9b%2FpN1rkKwFW0yCxVK9stnDeK%2Fimg.png)   
페이지가 모두 그려지면 커넥션을 종료  
➡️ 매번 요청할 때 마다 커넥션을 맺어줘야하는 단점 해결
