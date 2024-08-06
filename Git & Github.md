📍[Git vs Github](#git-vs-github)   
📍 [Git 작업공간](#git-작업공간)   
📍 [브랜치 병합](#브랜치-병합)   
      - [Merge](#merge)    
      - [Rebase](#rebase)  
📍 [커밋 컨벤션](#커밋-컨벤션)   

# 🖇 Git & Github
## Git vs Github
#### Git

다음과 같은 명령어로 소스 코드를 관리하는 역할  
- 소스 병합 (merge, rebase)
- 소스 리비전 관리 (reset, commit, branch)
- 소스 릴리즈 (push)
- 소스 태깅 (tag)
- 소스 변경사항 검토 (diff, log)

#### GitHub
Git을 기반으로 온라인으로 서비스하는 형태  

![git vs github](https://qph.cf2.quoracdn.net/main-qimg-6ad8361237d74cc2894a6b63005dbc28-pjlq)   


## Git 작업공간

![Git 작업공간](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FSmg3d%2FbtrQj6cd94n%2FkMihG5Jz0ktiD69uku4xBk%2Fimg.png)   

- **workspace (작업 공간)** 
    - 프로젝트의 실제 소스 코드와 파일이 저장되는 공간
    - 새로운 파일을 생성·수정하며 프로젝트 작업 진행
    
- **index(stage)**
    - 변경된 파일 중 어떤 파일이 `다음 commit에 포함`될지를 관리하는 영역
    - 작업 공간에서 변경된 파일들 중에서 commit 준비가 된 파일을 index에 추가 → index에서 commit 할 대상을 선택  

> **index(stage)이 필요한 이유 🤔**  
    1. **분리된 작업 영역**: 변경 사항을 `그룹적으로 commit`하고,  commit에 포함시킬 파일을 선택할 수 있게 해줌  
    2. **일부 변경 사항만 커밋**: 모든 변경 사항을 한 번에 commit 하지 않고, `필요한 변경 사항만 stage에 올려서` commit 가능  
    3. **레퍼런스 포인트**: stage에 있는 파일들은 현재 변경 사항을 나타내는 commit의 일부로 간주됨  
        ➡️ 변경 사항을 기록하고 버전 관리 가능
    
- **local repository(로컬 저장소)**
    - workspace(작업 공간)의 변경 내용을 commit 하여 기록할 때, commit 이력과 branch 정보를 저장하는 DB
    - 각 개발자의 `개인 컴퓨터`에 위치

- **remote repository(원격 저장소)** : 다수의 개발자가 협업하고 공유하는 `중앙 저장소`

## 브랜치 병합
![title](https://images.velog.io/images/kgh239/post/b889ec37-1ce2-4065-94a5-6aa9591f07a2/image.png)   

### merge
두 개의 브랜치를 통합하는 데 사용  
 두 브랜치의 변경 사항을 하나의 브랜치에 결합

**<Merge의 종류>**  
1. **Fast-forward Merge**  
    - 두 브랜치가 `단순한 직계 조상 관계`일 때 발생  
    - 브랜치 포인터를 앞으로 이동시키는 방식으로 병합이 이루어짐  
    - 병합 커밋이 생성되지 않으며, 커밋 이력은 `직선`으로 이어짐

    <Fast-forward Merge의 과정>  
    브랜치가 다른 브랜치의 직계 조상인지 확인  
    ➡️ 직계 조상 관계가 확인되면 브랜치 포인터를 `최신 커밋`으로 이동

2. **Non-fast-forward Merge**   
    - 브랜치들이 `직계 조상 관계가 아닐 때` 발생  
    - 병합 커밋을 생성하여 두 브랜치의 변경 사항을 결합  
    - 두 브랜치의 이력을 `트리 구조`로 유지

    <Non-fast-forward Merge의 과정>  
    두 브랜치의 공통 조상을 찾음  
    ➡️ 공통 조상부터 현재 브랜치까지의 변경 사항을 비교하여 적용  
    ➡️ `병합 커밋`을 생성하여 두 브랜치의 변경 사항 결합

![merge 종류](https://wikidocs.net/images/page/153871/05.04.01.jpg)   


> **Fast-forward와 Non-fast-forward의 차이점 💡**  
   `Fast-forward Merge`  
    - 브랜치가 직계 조상 관계일 때 발생  
    - 브랜치 포인터가 최신 커밋으로 단순히 이동하여 병합  
    - 병합 커밋 생성 ❌  
    - 커밋 이력이 **직선**으로 이어짐   
     ` Non-fast-forward Merge`  
    - 브랜치가 직계 조상 관계가 아닐 때 발생  
    - 병합 커밋이 생성되어 두 브랜치의 이력 결합
    - 커밋 이력이 **트리 구조**로 유지

### rebase

한 브랜치의 커밋 이력을 다른 브랜치의 끝으로 이동시키는 방식  
(현재 branch의 base를 `재설정`)  
더 깔끔한 커밋 히스토리를 유지 가능


> **merge vs rebase 🤔**  
    ```
    💡 merge한 코드 결과 = rebase 한 코드 결과
    ```   
 (1) **merge만 하기** (merge commit 생성)  
    - 변경 내용의 이력이 있는 그대로 모두 남기 때문에 정확하지만 이력이 `복잡`함  
    - 여러 줄기에 제각각 남아서  
 (2) **rebase로 한 줄로 만든 후에 merge 하기** (한 줄기로 만든 후 fast-forward merge)  
    - 커밋 이력이 한 줄기로 착착 보기 좋게 정리됨  
    - 다만 정확한 커밋 이력을 남겨야할 때는 부적절  
  ![merge vs rebase](https://github.com/user-attachments/assets/50bbaf8d-51ad-4e49-9d36-959efe2d4fd2)


## 커밋 컨벤션

Git을 사용할 때 커밋 메시지를 작성하는 규칙  
명확한 커밋 메시지를 통해, 어떤 기능이 추가되었고 무엇이 수정되었는지 쉽게 알 수 있음  

<장점>
- 코드 유지보수와 히스토리 관리가 수월해짐
- 팀원 간의 커뮤니케이션 원활

### 커밋 메시지 구조

일반적으로 많이 사용되는 커밋 메시지 컨벤션 중 하나는 `Udacity Style`  
구성 : `type: subject, body, footer`
각 파트는 한 줄의 공백으로 구분됩니다.  

<예시>  
```
type: subject

body

footer
```

### 커밋 메시지 타입 및 예시

| type     | subject | body (선택 사항) | footer (선택 사항) |
|----------|---------|------------------|---------------------|
| feat     | 새로운 기능 추가 | 제목은 최대 50글자를 넘기지 않음 | 이슈 트래커 ID작성 |
| fix      | 버그 수정 | 양에 구애받지 않고 최대한 상세히 작성 | "유형: #이슈 번호" 형식으로 작성. |
| docs     | 문서 수정 | 마침표 및 특수기호는 사용하지 않음 | 어떻게 변경했는지보다 무엇을 변경했는지 또는 왜 변경했는지를 설명 |
| style    | 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우 | | |
| refactor | 코드 리팩토링 | | |
| test     | 테스트 코드, 리팩토링 테스트 코드 추가 | | |
| chore    | 빌드 업무 수정, 패키지 매니저 수정, production code와 무관한 부분들 (.gitignore, build.gradle 같은) | | |
| comment  | 주석 추가 및 변경 | | |
| remove   | 파일, 폴더 삭제 | | |
| rename   | 파일, 폴더명 수정 | | |

### 예시

#### (1) feat: "로그인 기능 구현"
```
feat: "로그인 기능 구현"

로그인 시 JWT 발급

Resolves: #111
Ref: #122
Related to: #30, #50
```

#### (2) fix: Update Login Logic
```
fix: Update Login Logic
```

#### (3) chore: Update git.ignore
```
chore: Update .gitignore

database 관련 중요 정보 변경 감추기 위해 
.gitignore에 application-database.properties 추가
```
