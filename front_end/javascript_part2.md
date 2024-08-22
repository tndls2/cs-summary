📍[JSON](#jsonjavascript-object-notation)  
📍[DOM](#domdocument-object-model)  
📍[비동기 프로그래밍과 Promise](#비동기-프로그래밍과-promise)  

### JSON(JavaScript Object Notation)
- `데이터 저장/전송`을 위한 간단하고 가벼운 텍스트 기반 데이터 형식  
- 자바스크립트 객체 표기법을 기반으로 함  
  but 언어에 `독립적` -> 다양한 프로그래밍 언어에서 사용 가능   
-  <u>API 응답, 데이터 시각화, 설정 파일</u> 등에서 사용됨

#### 1. 기본 구조
`이름-값` 쌍으로 이루어진 데이터 객체 표현  
데이터 객체 내부에서 데이터를 `계층적`으로 표현할 수 있게 해줌  
-> 웹 애플리케이션에서 데이터를 `직관적`으로 전달하고 처리하기 좋음
- `객체(Object)`: 중괄호 `{}`로 감싸고, 이름과 값을 콜론 `:`으로 구분
- `배열(Array)`: 대괄호 `[]`로 감싸고, 값들은 쉼표 `,`로 구분

```json
{
  "squadName": "슈퍼히어로",
  "members": [
    {
      "name": "아이언맨",
      "age": 29,
      "realName": "토니 스타크"
    },
    {
      "name": "헐크",
      "age": 39,
      "realName": "브루스 배너"
    }
  ]
}
```

#### 2. XML vs JSON
JSON은 `프로그래밍 언어 간의 데이터 교환`을 간편하게 하기 위해 개발됨  
이전에는 `XML`이 주요 데이터 교환 포맷이었으나, XML의 복잡성과 비효율성을 개선하기 위해 JSON이 등장함!

- **XML** :  계층적 구조를 명확하게 표현 가능
  ```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <root>
    <squadName>슈퍼히어로</squadName>
    <members>
      <name>아이언맨</name>
      <age>29</age>
      <realName>토니 스타크</realName>
    </members>
    <members>
      <name>헐크</name>
      <age>39</age>
      <realName>브루스 배너</realName>
    </members>
  </root>
  ```
- **JSON** : 간결한 편, 태그 없이도 데이터를 쉽게 이해 가능
  ```json
  {
    "squadName": "슈퍼히어로",
    "members": [
      {
        "name": "아이언맨",
        "age": 29,
        "realName": "토니 스타크"
      },
      {
        "name": "헐크",
        "age": 39,
        "realName": "브루스 배너"
      }
    ]
  }
  ```

#### 3. JSON 메서드
- `JSON.parse()`: JSON 문자열 -> 자바스크립트 객체로 변환
  ```javascript
  const json = '{"result":true, "count":42}';
  const obj = JSON.parse(json);
  console.log(obj); // { result: true, count: 42 }
  ```

- `JSON.stringify()`: 자바스크립트 객체 -> JSON 문자열로 변환
  ```javascript
  const obj = { result: true, count: 42 };
  const json = JSON.stringify(obj);
  console.log(json); // '{"result":true,"count":42}'
  ```

### DOM(Document Object Model)
- 웹 페이지의 구조를 트리 형태로 표현  
-> 웹페이지와 프로그래밍 언어를 연결시켜주는 역할
- DOM을 활용하면, 웹 페이지의 요소들을 `동적`으로 조작하여 다양한 기능을 구현 가능!
#### 1. DOM API
- HTML 문서의 내용을 `트리 형태`로 구조화  
  -> 자바스크립트가 HTML 문서에 접근하고 조작할 수 있도록 해주는 인터페이스   
- 각 HTML 요소는 DOM에서 `노드(node)`로 표현됨

![dom](https://www.books.weniv.co.kr/images/basecamp-javascript/chapter08/01-1.png)   

```html
<!DOCTYPE html>
<html>
  <!-- DOM API : document.head -->
  <head>
    <title>My Document</title>
  </head>
  <!-- DOM API : document.body -->
  <body>
    <h1>Hello, World!</h1>
    <p>This is a paragraph.</p>
  </body>
</html>

```

#### 2. DOM 트리에 접근하기
- `getElementById()` : 특정 ID를 가진 요소 선택
  ```javascript
  const element = document.getElementById('myId');
  console.log(element); // <div id="myId">...</div>
  ```
- `getElementsByTagName()`: 특정 태그 이름을 가진 `모든` 요소 선택

  ```javascript
  const elements = document.getElementsByTagName('p');
  console.log(elements); // HTMLCollection(2) [p, p]
  ```
- `getElementsByClassName()` : 특정 클래스를 가진 `모든` 요소 선택
  ```javascript
  const elements = document.getElementsByClassName('myClass');
  console.log(elements); // HTMLCollection(2) [div.myClass, div.myClass]

- `querySelector()` : CSS 선택자를 사용하여 `첫 번째로 일치`하는 단일 요소 선택
  ```javascript
  const element = document.querySelector('.myClass');
  console.log(element); // <div class="myClass">...</div>
  ```
- `querySelectorAll()` : CSS 선택자를 사용하여 일치하는 `모든` 요소 선택
   ```javascript
  const elements = document.querySelectorAll('.myClass');
  console.log(elements); // NodeList(2) [div.myClass, div.myClass]
  ```

#### 3. DOM 제어하기
- **이벤트 삽입** : `addEventListener` 메서드 사용
  ```html
  <button>HELLO!</button>
  <script>
    const myBtn = document.querySelector('button');
  
    myBtn.addEventListener('click', function () {
      // 버튼을 클릭할 때마다 콘솔에 'hello world' 출력
      console.log('hello world'); 
    });
  </script>
  ```

    - 이벤트 타입 : `click`
    - 리스너 함수(이벤트 핸들러 함수) : 익명 함수 -> 이벤트 발생시 실행

- **클래스 제어** : `classList` 객체 사용
  ```html
  <style>
    .blue {
      background-color: blue;
      color: white;
    }
  </style>
  <button>Make me BLUE!</button>
  <script>
    const myBtn = document.querySelector('button');
  
    myBtn.addEventListener('click', function () {
      // 버튼을 클릭할 때마다 버튼의 색상 blue로 변경
      myBtn.classList.toggle('blue'); // 클래스를 토글함
      console.log(myBtn.classList.contains('blue')); // 클래스가 있는지 확인
    });
  </script>
  ```

- **요소 제어**
   - 요소 생성/추가 : `document.createElement()`, `appendChild()`메소드 사용
      ```html
      <ul></ul>
      <button>Make me MORE!</button>
      
      <script>
        const myBtn = document.querySelector('button');
        const myUl = document.querySelector('ul');
        
        //버튼을 클릭할 때마다 리스트 아이템이 추가
        myBtn.addEventListener('click', function () {
          for (let i = 0; i < 5; i++) {
            // 리스트 생성
            const myLi = document.createElement('li');
            myLi.textContent = `Item ${myUl.children.length + 1}`;
            // 리스트에 아이템이 추가
            myUl.appendChild(myLi);
          }
        });
      </script>
      ```
    - 요소 제거 : `removeChild()` 메서드 사용
      ```html
      <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
      </ul>
      <button id="remove">Remove Last Item</button>
      
      <script>
        const removeBtn = document.getElementById('remove');
        const myUl = document.querySelector('ul');
        
        removeBtn.addEventListener('click', function () {
          if (myUl.lastElementChild) {
            // 버튼을 클릭할 때마다 리스트의 마지막 아이템 제거
            myUl.removeChild(myUl.lastElementChild);
          }
        });
      </script>
      ```

- **요소 값 제어** : DOM API를 통해 요소의 값을 가져오거나 변경 가능
  ```html
  <p></p>
  <input type="text" />
  <button>Write Something!</button>
  
  <script>
    const myBtn = document.querySelector('button');
    const myP = document.querySelector('p');
    const myInput = document.querySelector('input');
    // 입력창에 값을 입력하고 버튼을 클릭하면 그 값이 `<p>` 태그에 출력되는 코드
    myBtn.addEventListener('click', function () {
      myP.textContent = myInput.value;
    });
  
  </script>
  ```

- **속성 제어**
    - `style` 객체 사용하여  요소의 스타일 제어
      ```html
      <p>Hello World!</p>
      <button>Change Style</button>
      
      <script>
        const myP = document.querySelector('p');
        const myBtn = document.querySelector('button');
      
        myBtn.addEventListener('click', function () {
          myP.style.color = 'red';  // 텍스트 색상 -> 빨간색
          myP.style.fontWeight = 'bold'; // 텍스트 굵기 -> 굵게
        });
      </script>
      ```
    
      >**JS로 스타일링을 제어하는 이유? 🤔**  
        `동적`인 웹 페이지를 쉽게 만들 수 있기 때문 !  
        자바스크립트를 사용하면 사용자의 상호작용에 따라 실시간으로 스타일을 변경 가능함  

    - `setAttribute() 메서드`사용하여 요소의 속성 설정
      ```html
      <img src="https://via.placeholder.com/150" alt="placeholder" id="image" />
      <button>Change Image</button>
      
      <script>
        const myImg = document.getElementById('image');
        const myBtn = document.querySelector('button');
      
        myBtn.addEventListener('click', function () {
           // placeholder image : 임시로 이미지 표시하는 서비스
          myImg.setAttribute('src', 'https://via.placeholder.com/300'); // 이미지 사이즈 변경
      
          myImg.setAttribute('alt', 'new placeholder');  //이미지 설명 텍스트 변경
        });
      </script>
      ```
      
#### 4. DOM 이벤트 흐름
- `이벤트 흐름` : 브라우저에서 이벤트가 발생할 때 해당 이벤트가 DOM 요소를 통해 전파되는 방식
![이벤트 흐름](https://www.books.weniv.co.kr/images/basecamp-javascript/chapter08/03-1.png)   

- 이벤트 흐름 과정
  - `캡처링 단계 (Capturing Phase)`: 이벤트가 발생하면 브라우저는   가장 상위 요소인 `window` -> 하위 요소까지 DOM 트리를 따라 <u>내려가며</u> 이벤트 대상 탐색  
      💡 이 과정에서 만나는 모든 `캡처링 이벤트 리스너`가 실행됨
  - `버블링 단계 (Bubbling Phase)` : 이벤트 대상을 찾고 나서 다시 상위 요소로 DOM 트리를 따라 <u>올라감</u> 
  - 💡 이 과정에서 만나는 모든 `버블링 이벤트 리스너`가 실행됨 (=`이벤트 버블링`)
  
  ```html
  <!DOCTYPE html>
  <html lang="ko">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Event Flow</title>
    </head>
    <body>
      <article class="parent">
        <button class="btn" type="button">버튼</button>
      </article>
      <script>
        const parent = document.querySelector('.parent');
        const btnFirst = document.querySelector('.btn');
  
        // 캡처링 단계의 이벤트 리스너
        window.addEventListener('click', () => {
          console.log('window capture!');
        }, true);
  
        document.addEventListener('click', () => {
          console.log('document capture!');
        }, true);
  
        parent.addEventListener('click', () => {
          console.log('parent capture!');
        }, true);
  
        btnFirst.addEventListener('click', (event) => {
          console.log('btn capture!');
        });
  
        // 버블링 단계의 이벤트 리스너
        btnFirst.addEventListener('click', (event) => {
          console.log('btn bubble!');
        });
  
        parent.addEventListener('click', () => {
          console.log('parent bubble!');
        });
  
        document.addEventListener('click', () => {
          console.log('document bubble!');
        });
  
        window.addEventListener('click', () => {
          console.log('window bubble!');
        });
      </script>
    </body>
  </html>
  ```
  
  > 출력 결과:  
      1. 캡처링 단계: `window capture!` → `document capture!` → `parent capture!` → `btn capture!`  
      2. 버블링 단계: `btn bubble!` → `parent bubble!` → `document bubble!` → `window bubble!`

- `target` &`currentTarget`
  - `event.target`: 이벤트가 발생한 `진원지` 요소  
      = 사용자가 `실제로` 클릭한 버튼이나 요소
  - `event.currentTarget`: 이벤트 리스너가 `연결된` 요소  
      = 이벤트 전파 과정에서 `현재` 이벤트 리스너가 실행되고 있는 요소
    
    ```html
    <article class="parent">
      <ol>
        <li><button class="btn-first" type="button">버튼1</button></li>
        <li><button type="button">버튼2</button></li>
        <li><button type="button">버튼3</button></li>
      </ol>
    </article>
    
    <script>
      const parent = document.querySelector('.parent');
      parent.addEventListener('click', function (event) {
        console.log('Target:', event.target); // 사용자가 실제로 클릭한 버튼
        console.log('CurrentTarget:', event.currentTarget); // 이벤트 리스너가 연결된 `article.parent` 요소
      });
    </script>
    ```

- `preventDefault()` : 브라우저에서 기본적으로 제공하는 동작을 막고, 자바스크립트를 통해 원하는 동작을 수행하도록 함

  - 앵커 태그의 기본 동작 중지
    ```html
    <a href="https://www.naver.com" class="link">네이버 링크</a>
    <script>
      const link = document.querySelector('.link');
      link.addEventListener('click', (event) => {
        console.log('클릭되었습니다.');
        event.preventDefault();  // 기본 동작 중지
      });
    </script>
    ```
    - 기본 동작: 앵커 태그`<a>`를 클릭하면, 브라우저는 href 속성에 지정된 네이버 웹사이트 URL로 이동  
    - preventDefault() 사용: 네이버 웹사이트로의 이동이 막힘 & `console.log('네이버로 이동하지 않습니다.')`만 실행됨
  
  - 폼 제출의 기본 동작 중지
    ```html
    <form action="/submit" method="POST">
      <button type="submit" class="submit">제출</button>
    </form>
    <script>
      const submit = document.querySelector('.submit');
      submit.addEventListener('click', (event) => {
        console.log('폼 제출 클릭');
        event.preventDefault();  // 기본 동작 중지
      });
    </script>
    ```
    - 기본 동작: 폼의 submit 버튼을 클릭하면, 브라우저는 폼 데이터를 /submit URL로 POST 방식으로 전송하고 페이지를 새로 고침함
    - preventDefault() 사용 : 폼이 실제로 서버로 제출되지 않고, 페이지도 새로고침되지 않음 & `console.log('폼 제출이 중지되었습니다.')`만 실행됨


### 비동기 프로그래밍과 Promise
#### 1. 동기/비동기

|           | **동기 프로그래밍**                                     | **비동기 프로그래밍**                                     |
|-------------------------|-------------------------------------------------------|----------------------------------------------------------|
| **처리 방식**            | 작업이 **순차적**으로 실행 = 한 작업이 완료되기 전까지 다음 작업이 시작되지 않음 | 여러 작업이 **병렬적**으로 실행 = 한 작업이 완료되기 전에 다른 작업이 시작될 수 있음 |
| **대기 시간**       | 앞의 작업이 완료될 때까지 다음 작업은 대기             | 다른 작업이 비동기적으로 처리되며, 대기 시간 동안 다른 작업을 수행할 수 있음 |
| **프로그램 복잡도**      | 일반적으로 코드가 직관적이고 이해하기 쉬움             | **콜백**, **프로미스** 또는 `async/await`를 사용하여 복잡성이 증가할 수 있음 |
| **응답 시간**            | 모든 작업이 순서대로 실행되기 때문에 응답 시간이 길어질 수 있음 | 여러 작업을 동시에 처리할 수 있어 응답 시간이 단축될 수 있음 |
| **리소스 사용**          | 리소스가 비효율적으로 사용될 수 있음                  | 리소스를 효율적으로 사용할 수 있음 (ex. I/O 작업 동안 CPU가 유휴 상태일 필요 없음) |
| **예시**                 | 파일 읽기, 데이터베이스 조회 후 결과 반환.              | 네트워크 요청, 파일 다운로드, 이벤트 기반 작업.           |
| **장점**                 | 코드가 단순하고 유지보수가 쉬움.                       | 성능 최적화, 높은 응답 속도, 리소스 효율적 사용 가능.     |
| **단점**                 | I/O 작업에 시간이 많이 걸릴 수 있음.                    | 코드 복잡도가 증가하고 디버깅이 어려울 수 있음.           |

#### 2. Promise
js에서 `비동기 작업`을 관리하고 처리하기 위해 사용되는 객체  
성공 or 실패에 따라 실행할 함수(`콜백함수`)를 약속함  
- **Promise 상태**   
  - Pending (대기): 초기 상태로, 비동기 작업이 아직 완료되지 않은 상태  
  - Fulfilled (이행): 비동기 작업이 성공적으로 `완료`되어 결과값이 반환된 상태  
  - Rejected (거부): 비동기 작업이 실패하여 `오류`가 발생한 상태  
    `💡 pending(대기상태) -> resolve(해결) -> fulfilled(성공)`  
    `🚨 pending(대기상태) -> reject(거부) -> rejected(실패)`  

- **Promise와 사용되는 메소드**

  ```javascript
  let promise = new Promise((resolve, reject) => {
      // 비동기 작업 수행
      let success = true;
      if (success) {
          resolve("작업이 성공했습니다!");
      } else {
          reject("작업이 실패했습니다.");
      }
  });
  ```

  - `then()` : 비동기 작업이 성공적으로 완료되었을 때, 실행될 콜백 함수 지정  

    ```javascript
    promise.then(result => {
        console.log(result); // "작업이 성공했습니다!" 출력
    });
    ```  
  - `catch()` : 비동기 작업이 실패했을 때, 실행될 콜백 함수 지정

    ```javascript
    promise.catch(error => {
        console.log(error); // "작업이 실패했습니다." 출력
    });
    ``` 
  - `finally()` : 작업의 성공 여부와 상관없이, 항상 실행되는 콜백 함수 지정

    ```javascript
    promise.finally(() => {
        console.log("작업이 끝났습니다."); 
    });
    ``` 

- **Promise 장점**
  - 가독성 향상: `콜백 지옥(callback hell)`을 피하고, 코드의 가독성 높임
  - 체인 가능: `then`, `catch` 메서드를 체인으로 연결 -> 연속적인 비동기 작업을 간단하게 처리 가능
  - 에러 처리: 비동기 작업에서 발생하는 오류를 간단하게 처리 가능


#### 3. fetch와 async/await
js에서 비동기적으로 데이터를 가져오거나 서버와 통신하는 데 사용됨  
- `fetch` : 웹 브라우저에서 네트워크 요청을 수행하기 위해 사용되는 함수
  - 주로 HTTP 요청을 보냄 + 서버로부터의 응답을 받아 처리하는 데 사용
  - `Promise`를 반환함 = `then`이나 `await`로 응답을 처리할 수 있음
    
  ```javascript
  fetch('https://jsonplaceholder.typicode.com/posts/1')
    .then(response => response.json()) // 응답을 JSON으로 변환
    .then(data => console.log(data))   // 변환된 데이터를 콘솔에 출력
    .catch(error => console.error('Error:', error)); // 에러 처리
  ```

- `async/await`
  - async 함수 : 항상 Promise를 반환
  - await 키워드 : 해당 Promise가 처리될 때까지 기다리게 만듬   
    ➡️  비동기 코드가 <u>동기 코드</u>처럼 직관적으로 작동하게 됨
    
  ```javascript
  async function fetchData() {
      try {
          const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
          const data = await response.json(); // 응답을 JSON으로 변환
          console.log(data); // 변환된 데이터를 콘솔에 출력
      } catch (error) {
          console.error('Error:', error); // 에러 처리
      }
  }
  
  fetchData();
  
  ```

> **콜백 지옥(callback hell)**  
>  - js 에서 비동기 작업을 처리할 때, 중첩된 콜백 함수들로 인해 코드의 가독성이 떨어지고 유지보수가 어려워지는 현상  
> - 여러 개의 비동기 작업이 순차적으로 실행될 때 발생 🚨
> - 콜백 함수가 계속 중첩되어 코드를 오른쪽으로 깊게 밀어내기 때문에 코드가 피라미드 모양을 이룸
> ```javascript
> function firstTask(callback) {
>   setTimeout(() => {
>     console.log('첫 번째 작업 완료');
>     callback();
>   }, 1000);
> }
>     
> function secondTask(callback) {
>   setTimeout(() => {
>     console.log('두 번째 작업 완료');
>     callback();
>   }, 1000);
> }
>     
> function thirdTask(callback) {
>   setTimeout(() => {
>     console.log('세 번째 작업 완료');
>     callback();
>   }, 1000);
> }
>     
> firstTask(() => {
>   secondTask(() => {
>     thirdTask(() => {
>         console.log('모든 작업 완료');  // 중첩이 늘어남
>     });
>   });
> });
> ```
>   **💡 콜백 지옥 해결방법**  
>   1. `Promise` 사용
>   ```javascript
>   firstTask()
>     .then(secondTask)
>     .then(thirdTask)
>     .then(() => {
>       console.log('모든 작업 완료');
>     })
>     .catch(error => {
>       console.error(error);
>     });
>    ```
>   
>   2. `async/await` 사용      
>   ```javascript
>   async function runTasks() {
>     await firstTask();
>     await secondTask();
>     await thirdTask();
>     console.log('모든 작업 완료');
>   }
>       
>   runTasks().catch(error => {
>     console.error(error);
>   });
>     ```
