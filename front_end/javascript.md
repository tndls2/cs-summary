[📚 javascript 베이스캠프](https://www.books.weniv.co.kr/basecamp-javascript)    

📍[javascript 기초](#javascript)  
📍[화살표 함수](#화살표-함수)   
📍[전개구문](#전개구문-spread-syntax)  
📍[디스트럭처링](#디스트럭처링-destructuring)   
📍[Map & Set](#map--set)

## JavaScript
웹페이지에서 동작을 구현할 때 사용되는 `프로그래밍 언어`
- HTML, CSS를 프로그래밍적으로 제어 가능
- 동적인(live) 웹 지향
   - 데이터 저장 
    - 값 계산
    - 결과 반영 : `DOM API`(Document Objecct Model), `BOM API`(Browser Object Model)
    - 다른 컴퓨터와 통신 : `AJAX`
> **바닐라 자바스크립트**🍦
    : 순수 자바스크립트  

> **BOM(브라우저 객체 모델)** : JavaScript가 브라우저와 소통하기 위한 도구들을 제공하는 것 ex) `console`

### let vs const
1. `let`   
    - 변수의 가리키는 값이 `반드시 변경`되어야 하는 경우 사용

2. `const`  
    - 의도하지 않은 값의 변경을 방지 가능
    - 가독성 및  유지 보수성 ⬆️ : 다른 개발자들이 변수의 값이 변경될 가능성이 없다는 것을 빠르게 인지 가능

> tip: const로 선언하고, 문제 생기면 let으로 변경하기!

### undefined vs null
1. `undefined`
    - 변수가 값을 갖고 있지 않음 = 값이 할당되지 않음
2. `null`
    - 값이 없음 = 의도적으로 값이 없음
> **값이 비어있음을 나타내기 위해 `undefined`를 사용해도 될까? 🤔**  
    의미적으로는 부적절함! 하지만 동작상 상관없음  
     자바스크립트의 메모리를 관리해주는 프로그램인 `가비지 컬렉터`가 null과 undefined를 구분하지 않기 때문


### 템플릿 리터럴
`문자열 안에 변수를 삽입`할 수 있도록 해주는 문자열 메소드 
- 백틱(`)으로 문자열 감쌈
- `${}`안에 변수 넣음 + 연산도 가능

```javascript
let num1 = 10;
let num2 = 20;
console.log(`두 수의 합은 ${num1 + num2}입니다.`);

let num = 3;
console.log(`증감연산 : ${++num}`); // 증감연산자도 사용가능

console.log(`비교연산 : ${2 === 3}`); // 비교연산자도 사용가능 (결과값 : true / false)
```

### == vs ===
- `==` : 값만 비교
- `===` : 값 + 타입까지 비교  
-> `===`를 사용하는 것이 더 안전

```javascript
2 == '2'; // true 
2 === '2'; // false
```

### 형변환
1. 문자열 -> 숫자로 변환  
    - `parseInt` : 정수로 변환
    - `parseFloat` : 실수로 변환

    ```javascript
    parseInt('hello'); // NaN : 문자열     'hello'는 숫자로 변환 불가
    parseInt('30b'); // 30 : 문자열 '30b'에서 숫자 부분만 변환
    parseFloat('45.4'); // 45.4
    ```

2. 숫자 -> 문자 형변환
    - toString() : 진수 변환 가능
      
    ```javascript
    let num = 5;
    typeof num.toString(); // string : 숫자 5를 문자열 '5'로 변환
    (3).toString(); // '3' :숫자 3을 문자열 '3'로 변환
    (3).toString(2); // '11' : 숫자 3을 2진수로 변환하여 '11'로 표현
    ```
  > 🚨 `3.toString()`은 에러 발생   
       : 자바스크립트 엔진은 숫자 뒤의 점을 소수점으로 인식하기 때문  
      -> 소괄호로 감싸기!
### Number.isNaN()
값이 NaN인지 확인  
`isNan()`보다 더 정확하게 NaN 사용하고 판별함

```javascript
isNaN(undefined); // true : undefined는 숫자로 변환 불가
Number.isNaN(undefined); // false : undefined는 NaN이 아님
Number.isNaN(NaN); // true (NaN은 NaN)
```

### Parameter vs Argument
| 용어 | 번역 | 의미 |
| --- | --- | --- |
| Parameter | 매개변수 | 함수와 메서드에 입력 변수 이름 **(선언)** |
| Argument | 전달인자, 인자, 인수 | 함수와 메서드에 실제 입력되는 값 **(실제값)** |

### 화살표 함수
`function` 키워드 대신 `=>`로 함수 표현  
함수의 이름이 없음!  

```javascript
// 일반 함수
function add(x, y) {
  return x + y;
}

// 화살표 함수
let 더하기함수 = (x, y) => x + y;
```

### forEach()
배열의 각 요소에 대해 주어진 함수를 실행하는 메소드  
함수는 인자로 `배열 요소, 인덱스`를 받음 -> 배열의 요소를 순회하면서 해당 요소를 함수로 전달

```javascript
// 화살표 함수로 많이 표현함
const arr = ['a',  'b', 'c'];
arr.forEach((item, index) => {
  console.log(item + index);
});
```

### map()
배열의 각 요소에 대해 주어진 함수 실행  
-> `새로운 배열`로 반환하는 메소드   
배열 안에 객체에서 데이터를 뽑는 형태로도 사용  
```javascript
const ages = data.map((item) => item['name']);
```

### join()
배열의 모든 요소를 연결하여 `하나의 문자열`로 만드는 메소드
연결할 때 사용할 문자열을 인자로 받음  
```javascript
const arr = ['hello', 'world'];
console.log(arr1.join('')); // helloworld
```

### 전개구문 (Spread syntax)
배열이나 객체와 같은 데이터 구조를 `확장`할 때 사용

#### 1. 배열/객체 합치기
- 배열
   ```javascript
   const upperCase = ['A', 'B', 'C'];
   const lowerCase = ['a', 'b', 'c'];
   const upperCaseAndLowerCase = [...upperCase, ...lowerCase];
   // ['A', 'B', 'C', 'a', 'b', 'c']
   ```
- 객체
   ```javascript
   const teamA = { 'tech': 1, 'hr': 2 };
   const teamB = { 'hr': 3 };
   const teamAAndTeamB = { ...teamA, ...teamB };
   // { 'tech': 1, 'hr': 3 }
   ```
   > 🚨 **중복된 키가 있을 경우** : 뒤에 위치한 객체의 값이 우선적으로 적용  

#### 2. 배열/객체 복사

- 배열  : `얕은 복사` 방식
   ```javascript
   const upperCaseOriginal = ['A', 'B', 'C'];
   const upperCaseCpy = [...upperCaseOriginal]
   upperCaseCpy.push('D');
   //  ['A', 'B', 'C', 'D']
   ```
   > 💡 단순한 숫자나 문자열 같은 `원시 값으로만 구성된 배열`의 경우, 얕은 복사와 깊은 복사의 차이는 실제로 중요하지 않음!  
     `원시 값`은 `참조 타입`과 달리 `메모리 주소`를 공유하지 않고, `값 자체`가 복사되기 때문에!

- 객체  
`새로운 객체`가 생성되지만, 그 객체 내부의 각 프로퍼티는 원본 객체의 값이나 참조를 그대로 복사함 (`얕은 복사`)
   ```javascript
   const personOriginal = { name: 'Alice', details: { age: 25, city: 'New York' } };
   const personCopy = { ...personOriginal };
   
   // 새로운 객체가 생성됨
   console.log(personOriginal === personCopy); // false (서로 다른 객체)
   
   // 참조는 그대로 복사 (=동일한 참조를 공유함)
   personCopy.details.city = 'Los Angeles';
   console.log(personOriginal.details.city); // 'Los Angeles' (동일한 참조를 공유)
   ```

   > 💡**얕은 복사 (Shallow Copy)**  
       - 복사본을 만들 때, 원본 객체의 참조(reference)만 복사  
        - 복사된 객체는 원본 객체의 `메모리 주소를 공유`하게 됨  
       - 원본 객체와 복사본 객체가 동일한 중첩된 객체(배열, 객체)를 참조하게 됨
       - 하나의 객체에서 중첩된 객체를 변경하면 ,다른 객체에서도 해당 변경사항이 반영!  
   
   > 💡**깊은 복사 (Deep Copy)**  
       - 객체의 모든 중첩된 객체나 배열까지 `새로운 메모리 공간`에 복사하는 것
       - 복사된 객체와 원본 객체가 서로 `독립적인 메모리 공간`을 가짐
       - 복사본을 수정해도 원본에 전혀 영향 ❌

### 디스트럭처링 (Destructuring)
ES6에서 도입된 문법  
배열이나 객체의 값을 `추출`-> 변수에 `할당`  
코드가 더 간결하고 가독성이 좋아짐 👍

#### 1. 배열 디스트럭처링
- 배열의 요소 -> 변수에 할당 
- 배열의 `순서`에 따라 할당됨
   ```javascript
   const numbers = [1, 2, 3];
   const [first, second, third] = numbers;
   
   console.log(first); // 1
   console.log(second); // 2
   console.log(third); // 3
   ```
- **일부 요소만 할당하기** : 
배열에서 특정 요소만 추출

   ```javascript
   const numbers = [1, 2, 3, 4];
   const [first, , third] = numbers;
   
   console.log(first); // 1
   console.log(third); // 3
   ```
- **나머지 요소 할당하기** : 
배열의 일부 요소만 변수에 할당하고, 나머지를 별도의 배열로 받기도 가능
   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const [first, second, ...rest] = numbers;
   
   console.log(first); // 1
   console.log(second); // 2
   console.log(rest); // [3, 4, 5]
   ```

#### 2. 객체 디스트럭처링
- 객체의 프로퍼티 값 -> 변수에 할당
- 객체의 프로퍼티 이름을 그대로 사용하여 변수 생성
   ```javascript
   const person = { name: 'Alice', age: 25 };
   const { name, age } = person;
   
   console.log(name); // 'Alice'
   console.log(age); // 25
   ```

- **다른 변수 이름으로 할당하기** : 
객체 프로퍼티를 다른 이름의 변수로 할당

   ```javascript
   const person = { name: 'Alice', age: 25 };
   const { name: userName, age: userAge } = person;
   
   console.log(userName); // 'Alice'
   console.log(userAge); // 25
   ```
- **기본값 할당하기** : 프로퍼티가 없을 경우, 기본값 설정

   ```javascript
   const person = { name: 'Alice' };
   const { name, age = 30 } = person;
   
   console.log(name); // 'Alice'
   console.log(age); // 30
   ```

#### 💡 함수에서의 디스트럭처링
함수의 `인자`로 객체나 배열을 전달할 때도 디스트럭처링을 사용 가능
```javascript
function greet({ name, age }) {
  console.log(`Hello, my name is ${name} and I am ${age} years old.`);
}
```

### Map & Set
ES6에서 도입된 문법  
#### 1. Map
- `키-값 쌍`을 저장하는 구조
- 객체와 유사하지만 더 유연함
- `키(Key)`: 어떤 데이터 타입(문자열, 숫자, 객체 등)도 가능함  
- 복잡한 데이터 구조에서 객체를 키로 사용하는 경우 유용함! (ex. 캐싱, 구성 설정 저장 등)

- **Map에 값 추가하기** : `set` 메서드 사용하여 키-값 쌍 추가  
  ```javascript
  let m = new Map();
  m.set('key1', 'value1');
  m.set(42, 'value2');
  m.set(true, 'value3');
  ```

- **Map에서 값 가져오기** :`get` 메서드 사용하여 특정 키에 대응하는 값 가져옴
  ```javascript
  m.get('key1'); // 'value1'
  m.get(42); // 'value2'
  ```

- **Map에 값이 있는지 확인하기** : `has` 메서드 사용하여 특정 키가 있는지 확인
  ```javascript
  m.has('key1'); // true
  ```

-  **Map에서 값 제거하기** : `delete` 메서드 사용하여 특정 키-값 쌍 제거  
  ```javascript
    m.delete('key1'); // true
   ```


- **Map의 크기 확인하기** : `size` 속성 사용하여 Map에 저장된 키-값 쌍의 개수 확인
  ```javascript
  m.size; // 2
  ```

- **Map의 모든 데이터 삭제하기** : `clear` 메서드 사용하여 Map의 모든 데이터를 삭제합니다.
  ```javascript
  m.clear();
  m.size; // 0
  ```

- **Map의 키와 값에 접근하기** : `keys()`와 `values()` 메서드 사용하여 키/값 접근
  ```javascript
  console.log([...m.keys()]); // ['key1', 42]
  console.log([...m.values()]); // ['value1', 'value2']
  ```

- **배열과 Map의 변환**
  ```javascript
  let arr = [[1, 'one'], [2, 'two']];
  let mapFromArr = new Map(arr);
  console.log([...mapFromArr]); // [[1, 'one'], [2, 'two']]
  ```

> **Map vs Object** 🤔  
    - 키의 타입: Object는 키로 문자열이나 심볼만 사용할 수 있지만, Map은 `모든 데이터 타입`을 키로 사용 가능  
    - 성능: 많은 데이터의 추가, 제거 작업에서 Map이 Object보다 더 나은 성능

#### 2. Set
중복되지 않는 `유일한` 값들의 집합  
값의 순서는 삽입된 순서를 따름  

- **배열과 Set의 변환 & Set을 이용한 중복 제거**
  ```javascript
  let arr = ['apple', 'banana', 'orange', 'banana'];
  let uniqueSet = new Set(arr);
  let uniqueArr = [...uniqueSet]; // 중복된 값이 제거된 배열로 바뀜
  // ['apple', 'banana', 'orange']
  ```

- **Set의 교집합, 합집합, 차집합**
  ```javascript
  let setA = new Set(['apple', 'banana']);
  let setB = new Set(['banana', 'orange']);
  
  // 교집합
  let intersection = new Set([...setA].filter(x => setB.has(x)));
  
  // 합집합
  let union = new Set([...setA, ...setB]);
  
  // 차집합
  let difference = new Set([...setA].filter(x => !setB.has(x)));
  ```
