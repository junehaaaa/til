# Sass(Syntactically Awesome Style Sheets)

## 1. 프리 프로세서(Pre Processor)
Sass는 CSS 전처리기로 .css 파일 중간에 위치하는 하나의 계층이다.  
웹 브라우저는 프로세서로서 웹데이터를 다운로드 받아 해석하여 화면에 해석된 데이터를 렌더링한다.  
Sass등 CSS 확장언어를 활용할 경우 웹브라우저에서 해석되기 전에 CSS로 변경되는 과정이 필요한다.  
이를 브라우저에서 해석되기 전에 프로세싱한다고 해서 프리프로세싱한다고 부른다.

## 2. Sass 설치

### 2-1. JavaScript 개발 환경 구성
Node.js는 Back-End 개발 환경이지만, 오늘 날 Front-End 개발 환경 구축을 위해서 필수적으로 사용된다.  
Node.js의 버전은 6.5.0 이상이면 어떤 것이든 상관 없다. Node.js의 표준 패키지 관리자 NPM(Node Packages Manager)은  
Node.js에 포함되어 있기 때문에 별도로 설치할 필요가 없다.

* Node.js : Google V8 엔진을 사용하여 제작된 JavaScript 런타임
* NPM : Node.js 패키지 매니저
* NVM 사용하여 Node.js 설치/관리 (★★★★★)

#### 2-1-1. NPM 설치 및 확인

```
$ npm install node-sass # 프로젝트 로컬 설치
$ npm install node-sass --global # 컴퓨터 전역 설치
```

- `npm —version` 혹은 축약어로,  `npm -v` 명령어를 입력하여 npm이 잘 설치 되었는지 확인할 수 있다.
- `npm install -g npm@latest` 최신버전으로 업데이트 해주는 명령어로, 여기서 -g는 ‘—-global’의 약자.
- `npm install —-global` 어느위치에서나 노드사스를 설치할 수 있도록 해주는 명령어.
- `npm ls -g` 내가 설치한 노드사스가 잘 되었는지 확인 할 수 있는 명령어.
- `npm show node-sass versions` 노드사스의 버전을 쭉 출력해준다.
- `npm show node-sass@4.* version` 4버전으로 시작하는 노드사스들을 출력.
- `node-sass -—help` 참고 할수있는 옵션들을 보여준다.

## 3. CLI(Command Line Interface)

### 3-1. CLI 명령어

#### 3-1-1. 디렉토리 이동  
`cd` : change Directory의 줄임말  

문법 : `$ cd {디렉토리 경로}`  
* `cd ./`    - 현재 디렉토리 (생략 가능)  
* `cd ../`   - 상위경로로 한번 올라감  
* `cd ../../` - 상위경로로 2번 올라감  
* `cd ~/Desktop`  - 데스크탑 디렉토리로 바로 이동    

#### 3-1-2. 폴더 생성  
`mkdir` : Make Directory의 줄임말

문법 : `$ mkdir {디렉토리 이름}`
* `~/Desktop $mkdir www`  
`Desktop` 위치에서 `www`라는 이름을 가진 폴더 생성
* `~/Desktop/www $mkdir css js`  
`Desktop`의 `www`폴더 안에 `css` 와 `js` 폴더를 생성

#### 3-1-3. 디렉토리 목록출력  
`ls` : List Segments의 줄임말

문법 : `$ls {디렉토리 경로}{옵션}`  
* ~/Desktop/www $ls  
:`Desktop` 폴더안의 `www` 폴더 안의 디렉토리 `목록`을 출력

#### 3-1-4. 파일생성  
`touch` : 빈파일을 생성할 경우  
`echo` : 간단한 내용이 들어있는 파일을 생성할 경우

* `~/Desktop/www $touch index.html`  
:`Desktop`의 `www`폴더 안에 `index.html`파일 생성
* `~/Desktop/www $touch js/app.js`
:`Desktop`의 `www`의 `js`폴더안에 `app.js`파일을 생성
* `~/Desktop $echo 'var course = "FDS" ; ' > js/basic.js`    
:`Desktop`에서 `js`폴더안에 `var course = "FDS" ;`내용이 들어간 파일 생성

#### 3-1-5. 파일/(비어있지 않은)디렉토리 삭제  
`rm` : Remove 줄임말
문법 :  
`$ rm {제거할 파일/디렉토리 이름}`  
`$ rm -r js` : js폴더 내부 하위 디렉토리까지 모두 제거
`$ rm -rf www`
:`www`폴더 안의 하위 디렉토리까지 모두 제거하되, 경고를 나타내지 않음

#### 3-1-6. 디렉토리 제거
`rmdir` : Remove Directory 줄임말

문법 :  
`$ rmdir {제거할 디렉토리 이름}`
* `~/Desktop/www $rmdir js`  
:`Desktop`의 `www`폴더 안에 있는 `js`제거  

#### 3-1-7. 파일/디렉토리 이동 및 이름변경  
`mv` : Move의 줄임말  
(이미 존재하는 파일/디렉토리의 경우 이름변경이 가능)
* `~/Desktop $mv coffee.js js/coffee.js`  
:`Desktop`의 `coffee.js` 파일을 `js`폴더 안으로 이동함
* `~/Desktop $mv coffee.js milk.js`
:`Desktop`의 `coffee.js` 파일명을 `milk.js`로 변경

#### 3-1-8. `&&` 명령어 사용  
`명령어 사이에 &&을 넣으면 차례대로 실행`
문법 : `$ mkdir {디렉토리 이름} && cd {디렉토리 이름}`
* `~/Desktop $ mkdir images && cd images`  
: `Desktop`위치에 `images`폴더를 만들고 `images` 폴더로 이동함

### 3-2. VIM
`vi` 입력 후, 뒤에 바로 원하는 파일의 경로를 적어주면 텍스트 편집기와 같은 창이 보여진다.

```
vi css/style.css
```
예를들어, 이렇게 입력하면 css 폴더에있는 style.css의 내용을 직접 입력하거나 수정할 수 있는 창이 보여진다.  
내용을 바로 입력하는것은 불가능하고, `i`키를 눌러서 insert 가능하게 한 후, 원하는 내용을 입력하거나 수정할 수 있다.  
입력이 다 끝난 후에는, `esc`키를 누르고 `:wq`를 입력해야 저장을 하고 빠져나올 수 있으며, `:q!`를 입력하면 저장하지 않은 채로 나올 수 있다.

## 4. CLI을 이용한 CSS 컴파일링

```css
# 적용전
html {
  font-size: 10px;
  }
body {
  font-size: 1.4rem;
  color: #000;
  background: #fff;
  }

  body *,
  body *::before,
  body *::after {
    content: '';
    box-sizing: border-box;
  }
```

### 4-1. expanded  
코드를 선택자마다 여러 줄로 출력

```
# 입력예시
node-sass lecture.scss lecture.css --output-style expanded
```


```css
# 결과
html {
  font-size: 10px;
}

body {
  font-size: 1.4rem;
  color: #000;
  background: #fff;
}

body *,
body *::before,
body *::after {
  content: '';
  box-sizing: border-box;
}
```

### 4-2. compressed  
코드를 모두 압축하여 출력(사람이 볼게 아냐..)

```
# 입력예시
node-sass lecture.scss lecture.css --output-style compressed
```

```css
# 결과
html{font-size:10px}body{font-size:1.4rem;color:#000;background:#fff}body *,body*::before,body *::after{content:'';box-sizing:border-box}
```

### 4-3. compact
코드를 선택자마다 한 줄로 출력
```
# 입력예시
node-sass lecture.scss lecture.css --output-style compact
```


```css
# 결과
html { font-size: 10px; }

body { font-size: 1.4rem; color: #000; background: #fff; }

body *, body *::before, body *::after { content: ''; box-sizing: border-box; }
```

### 4-4. nested
코드를 선택자마다 여러 줄로 출력하되, 선언 구문의 끝이 마지막 속성 뒤에 위치(기본 값)
```
# 입력예시
node-sass lecture.scss lecture.css --output-style nested
```


```css
# 결과
html {
  font-size: 10px; }

body {
  font-size: 1.4rem;
  color: #000;
  background: #fff; }

body *,
body *::before,
body *::after {
  content: '';
  box-sizing: border-box; }
  ```

## 5. Sass 문법

### 5-1. SCSS

```css
# 예시
# 변수를 선언하여 연산할수 있다.

$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```


### 5-2. Sass
```sass
# 예시
# 변수를 선언하여 연산할수 있다.
# 들여쓰기 문법을 사용한다.(세미콜론과 중괄호를 사용하지 않는다.)

$font-stack:    Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

## 6. CSS Sourcemap
CSS SourceMap을 구성하는게 중요하다. 하나의 CSS 파일에 모두 넣는게 아니라,  
공통된 부분을 분리하여 모듈로 관리해야 한다.

### 6-1. Sourcemap 설정 방법 (크롬 브라우져 이용하기)

* CSS SourceMap을 구성하는게 중요하다. 하나의 CSS 파일에 모두 때려 넣는게 아니라,  
공통된 부분을 분리하여 모듈로 관리할 때 유용하다.

* 크롬브라우저는 기본적으로 Sass의 소스맵을 제공하기 때문에, 다음과 같이 세팅해주면 좋다.

#### 크롬 실험 기능 설정 하기

1. 크롬에서 `chrome://flags/` 을 주소창에 입력하고, 개발자 도구 실험 항목을 찾아,  
 `사용`으로 설정을 켜준다.
2. 개발자도구 창 켜기 : 오른쪽마우스 클릭 후 검사버튼 누르거나,  
 `F12`버튼 누르거나, 맥의 경우는 `command + option + i`로 개발자도구를 열 수 있다.
3. 닫기창 옆에있는 햄버거메뉴를 누르면 나오는 `Setting`버튼을 누르거나, `f1`버튼을 누르면  
 Preference 창이 나오는데, 탭을 `Experiments`로 바꾸어서, 다음과 같은 접근성 항목과,  
  LIVE SASS 항목 등 에 체크해준다. `Accessibility`, `Inspection`, `Allow custom UI themes`, `Live SASS`


#### TIP
* 프론트엔드 개발자에 요구되는 것 : 디자이너와의 커뮤니케이션, 백엔드에 대한 기본 지식
* 프로젝트의 완성보다 커밋 히스토리가 중요 : 어떤 부분을 맡았고 어떤 고민에 의해서  
 도출된 프로젝트인지 기록을 남길것.