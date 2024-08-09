📍[📦 Box Model](#-box-model)  
  - [CSS Box Model](#css-box-model)  
  - [display 속성](#display-속성)  
  - [CSS 초기화](#css-초기화)

📍[🛒 요소 배치](#-요소-배치)  
  - [요소의 배치](#요소의-배치)  
  - [정렬된 배치](#정렬된-배치)  

## 📦 Box Model
### CSS Box Model
웹 레이아웃의 기초  
모든 HTML 요소는 하나의 `박스`로 취급   

**<박스의 구성>**
- 요소(element): 텍스트, 사진 등 보여줄 대상
- 패딩(padding): 요소 주변 영역 감쌈
- 테두리(border): 요소, 패딩을 감싸는 테두리
- 마진(margin): 테두리 밖의 영역 감쌈
    ![box](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter05/01-1.png)   


### display 속성
![display](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter05/02-1.png)   
- `block`
  -  블록 레벨 요소로 만듬 
  -  전후 줄 바꿈 o
  - width, height, margin, padding 속성 모두 사용 가능
- `inline`
  - 인라인 요소로 만듬
  - 요소 전후 줄 바꿈 x  
      -> 텍스트 흐림에 따라 배치
  - width, height 속성 사용불가!
  - margin 속성도 좌우만 적용됨
  
- `inline-block` : 인라인 요소와 블록 요소의 특성을 결합  
     -> `인라인`처럼 텍스트 흐름에 따라 배치  
     -> `블록`처럼 width, height, margin, padding 모두 사용 가능

- `flex`: 가로, 세로 축을 이용해 요소들 1차원 배치  
    -> 자식 요소들의 크기와 순서를 유연하게 조절 가능
    ![flex](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter05/flex_002.png)   

  ```css
  .flex-container {  /*부모 컨테이너*/
    display: flex;  /*flew 설정*/
    /*아이템들이 서로 떨어져서 균등하게 배치되도록 설정*/
    justify-content: space-between;
  }
  .flex-item { /*자식 컨테이너*/
    background-color: #c0c0c0;
    border: 1px solid #333;
    padding: 10px;
  }
  ```

- `grid`: 격자 형태의 2차원적 레이아웃 모델 제공
    ![grid](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter05/grid_002.png)   
    ```css
  .grid-container {  /*부모 컨테이너*/
    display: grid; /*grid 설정*/
  /*두 개의 열을 만들고, 각 열이 전체 그리드 너비의 절반(1fr)씩 차지하도록 설정*/
    grid-template-columns: repeat(2, 1fr);
    gap: 10px; /*아이템 사이 간격 설정*/
  }
  .grid-item { /*자식 컨테이너*/
    background-color: #b0b0b0;
    border: 1px solid #333;
    padding: 20px;
    text-align: center;
  }
    ```


### CSS 초기화
 각 브라우저가 HTML 요소에 대해 기본적으로 제공하는 스타일 존재함!  
브라우저마다 조금씩 다르기 때문에, 동일한 HTML이 `브라우저별로 다르게 렌더링` 되며 디자인의 일관성 떨어짐   
-> 일관된 디자인을 구현하기 위해 `reset.css` 파일 사용 
> CSS 속성들을 초기화하는 방법 = **reset.css** 사용

> **크로스 브라우징(Cross Browsing)** 이란?🤔  
    - 다양한 디바이스와 브라우저를 사용하는 다양한 사용자가 거의 비슷한 사용자 경험을 할 수 있도록 하는 기술  
     - 어느 한쪽에 최적화되어 치우치지 않도록 공통 요소를 사용하여 웹페이지를 제작하는 기법  
     - 사용자가 방문했을 때 정보로서의 소외감을 느끼지 않도록 하는 방법론적 가이드  



## 🛒 요소 배치
###  요소의 배치
#### 1. Position 속성
  - `static` (default값): html를 작성한 순으로 정상적인 흐름(normal flow)에 따라 위치  
  - `relative` : 상대적인 위치  
    -> 다른 요소들과의 관계를 유지하면서 위치 조정할 때 사용
  - `absolute` : 절대적인 위치  
    -> 가장 가까운 조상 요소 중 position 속성이 `static이 아닌 값을 가진 요소`를 기준으로 위치 잡음

#### 2. 3차원 공간에서 배치
`z-index` 속성 사용 !   
- 요소의 `쌓임 순서(stacking order)`를 결정
- 어떤 요소가 다른 요소 위에 나타날지를 제어  

**<z-index 특성>**  
- position이 `static`이 아닌 요소의 z축 결정 
- `z-index 값이 더 큰 요소`가 값이 작은 요소의 위를 덮음
- `부모`가 z-index를 높여 자식 앞으로 나올 수 없음!  
    but `자식`이 z-index를 낮춰 부모 뒤로 가는 건 가능

  ```html
  <div class="container">
    <div class="box red">Red Box</div>
    <div class="box green">Green Box</div>
    <div class="box blue">Blue Box</div>
  </div>
  ```
  ```css
  .box {
    position: absolute;
    width: 100px;
    height: 100px;
    border: 2px solid black;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .red {
    background-color: rgba(255,0,0,0.8);
    /*절대적인 위치 설정*/
    top: 40px;
    left: 40px;
    z-index: 3; /*맨 위에 위치*/
  }
  .green {
    background-color: rgba(0,255,0,0.8);
    /*절대적인 위치 설정*/
    top: 80px;
    left: 80px;
    z-index: 2; /*중간에 위치*/
  }
  .blue {
    background-color: rgba(0,0,255,0.8);
    /*절대적인 위치 설정*/
    top: 120px;
    left: 120px;
    z-index: 1; /*맨 아래에 위치*/
  }
  ```
#### 2. 쌓임 맥락(Stacking Context)
요소의 3차원 개념화를 위한 가상의 개념   
쌓임 맥락 내에서 자식 요소들의  `쌓임 순서` 결정  
- 요소에 position 속성이 <u>없는</u> 경우 : 만들어진 순서대로의 z-index 순서를 가짐  & 부모의 z-index 값은 `auto`
  - `가장 나중에 만들어진 요소`가 `가장 높은 z-index`가짐  
  -  부모의 position 속성이 <u>있는</u> 자식이 나타난 경우 : 부모의 z-index에 종속 ❌, 자신만의 `독립적인 stacking-context`를 가짐
- 부모의 z-index 값이 auto가 <u>아닌</u> 정수값인(0-n) 경우
  - 부모의 독자적인 stacking-context가 생성
  - 자식의 stacking-context는 부모의 stacking-context에  `종속적`

```html
<div class="box back">
  <div class="box red">
    <div class="box green"></div>
  </div>
  <div class="box blue"></div>
</div>
 
<div class="box back">
  <!--부모 red의 index값 = auto-->
  <div class="box red">
    <!--자식 green의 index는 부모에 종속X -->
    <!-- green이 전체 box들 중 맨 위에 위치하게 됨 -->
    <div class="box green" style="z-index: 100"></div>
  </div>
  <div class="box blue"></div>
</div>
 
<div class="box back">
   <!--부모 red의 index값 = 정수값 -->
  <div class="box red" style="z-index: 0">
    <!--자식 green의 index는 부모에 종속 O -->
    <!-- green은 부모의 자식 box들 중 맨 위에 위치하게 됨 -->
    <!-- 전체 box들 중 맨 위 X -->
    <div class="box green" style="z-index: 100">  </div>
    </div>
    <div class="box blue"></div>
  </div>
  ```
### 정렬된 배치
#### 1. flex
1차원 레이아웃 담당  
부모 요소를 `display: flex`로 설정하면, 자식 요소들이 **flex item** 됨  
->  flexbox 레이아웃을 사용할 수 있음  
✔️ 부모 요소 =  `flex-container` 
✔️ 자식 요소=` flex-item`

**<flexbox 속성>**  

| **속성**              | **값**                                              | **설명**                                                                                      |
|-----------------------|-----------------------------------------------------|-----------------------------------------------------------------------------------------------|
| **`flex-direction`**  | `row`                                               | 주 축이 행 방향, 왼쪽 -> 오른쪽으로 정렬 (default)                                          |
|                       | `row-reverse`                                       | 주 축이 행 방향, 오른쪽 -> 왼쪽으로 정렬                                                    |
|                       | `column`                                            | 주 축이 열 방향, 위 -> 아래로 정렬                                                          |
|                       | `column-reverse`                                    | 주 축이 열 방향, 아래 -> 위로 정렬                                                          |
| **`justify-content`** | `flex-start`                                        | 주 축의 시작점에 아이템 정렬                                                               |
|                       | `flex-end`                                          | 주 축의 끝점에 아이템 정렬                                                                 |
|                       | `center`                                            | 주 축의 중앙에 아이템 정렬                                                                 |
|                       | `space-between`                                     | 아이템 사이에 동일한 간격을 설정, 시작과 끝은 여백 없음                                      |
|                       | `space-around`                                      | 아이템 주변에 동일한 간격을 설정, 시작과 끝에도 반간격 적용                                 |
|                       | `space-evenly`                                      | 아이템 주변과 시작, 끝 모두 동일한 간격 설정                                               |
| **`align-items`**     | `stretch`                                           | 교차 축을 채우기 위해 아이템을 늘림 (deafult)                                                 |
|                       | `flex-start`                                        | 교차 축의 시작점에 아이템 정렬                                                             |
|                       | `flex-end`                                          | 교차 축의 끝점에 아이템 정렬                                                               |
|                       | `center`                                            | 교차 축의 중앙에 아이템을 정렬                                                               |
|                       | `baseline`                                          | 아이템을 텍스트의 기준선에 맞춰 정렬                                                         |
| **`gap`**             | `gap: [크기]`                                       | 아이템 사이의 간격을 설정. 모든 방향에 동일한 간격 적용.                                     |
|                       | `gap: [행 간격] [열 간격]`                         | 행과 열의 간격을 각각 설정                                                                    |
| **`flex-wrap`**       | `nowrap`                                            | 한 줄에 모든 아이템을 배치 (default).                                                         |
|                       | `wrap`                                              | 가능한 영역 내에서 아이템을 여러 행으로 나누어 배치                                          |
|                       | `wrap-reverse`                                      | 가능한 영역 내에서 아이템을 여러 행으로 나누어 배치하되, 역순으로 정렬                     |

![flex](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter07/01-1.png)   


#### 2. grid  
2차원 레이아웃 담당  
행과 열을 동시에 제어할 수 있어 복잡한 레이아웃 설정 가능  

**<명칭>**  
- `grid container` : 그리드의 가장 바깥 영역
- `grid cell` : 그리드의 한 칸 (개념적인 정의)
- `grid track` : 그리드의 행(row) or 열(column)
- `grid item` : 그리드 컨테이너의 자식 요소들
- `grid line` : 그리드 셀을 구분하는 선
- `grid number` : 그리드 라인의 각 번호
- `grid gap` : 그리드 셀 사이의 간격(gutter)
- `grid area` : 그리드 셀의 집합

  ![grid](https://www.books.weniv.co.kr/images/basecamp-html-css/chapter07/02-1.png)   

**<grid 속성>**  

| **속성**                      | **값**                                                      | **설명**                                                                                 |
|-------------------------------|-------------------------------------------------------------|------------------------------------------------------------------------------------------|
| **`grid-template-columns`**    | `[크기] [크기] ...`                                         | 열 방향 그리드 트랙의 크기를 설정 ex)`100px 1fr 100px`.                          |
|                               | `repeat([횟수], [크기])`                                   | 열 방향의 그리드 트랙을 간단히 반복해서 설정 ex) `repeat(2, 1fr 2fr)`           |
| **`grid-template-rows`**       | `[크기] [크기] ...`                                         | 행 방향 그리드 트랙의 크기 설정 ex) `100px 2fr`                               |
|                               | `repeat([횟수], [크기])`                                   | 행 방향의 그리드 트랙을 간단히 반복해서 설정 ex) `repeat(2, 1fr 2fr)`           |
| **`fr` 단위**                 | `[숫자]fr`                                                  | 그리드 컨테이너의 공간을 분할하는 유연한 길이 단위 ex) `1fr 2fr 1fr` (1:2:1 비율) |
| **`gap`**                      | `[크기]`                                                    | 셀과 셀 사이의 간격을 설정 -> 모든 방향에 동일한 간격 적용          |
|                               | `[행 간격] [열 간격]`                                      | 행과 열의 간격 각각 설정 ex)`10px 20px`                                      |
| **`justify-items`**            | `start` \| `end` \| `center` \| `stretch`                  | 수평(행) 방향으로 그리드 항목 정렬                                            |
| **`align-items`**              | `start` \| `end` \| `center` \| `stretch`                  | 수직(열) 방향으로 그리드 항목 정렬                                             |
| **`grid-area`**                | `[row-start] / [column-start] / [row-end] / [column-end]`  | 그리드 항목의 위치와 크기 설정 ex)`1 / 1 / 2 / 4`                             |
|                               | `[row-start] / [column-start] / [row-span] / [column-span]`| 그리드 항목이 차지할 행과 열의 범위 설정 ex) `1 / 1 / span 2 / span 3`       |
| **`span` 키워드**              | `span [숫자]`                                               | 여러 행 또는 열을 차지하도록 그리드 항목 병합. ex)`grid-column: span 3`        |
