# VUE JS FRAMEWORK

## 주요특징
* 낮은 학습비용 (비교적 쉽게 느껴지는 API, HTML 기반 템플릿 문법지원)
* 고속 렌더링 속도 (React 보다 빠르다고 주장함)
* 초경량 프레임워크 
* 컴포넌트 지향 UI (페이지 단위가 아닌, 컴포넌트별 개발)
* 리엑티브 시스템 
* 데이터 바인딩

## 브라우저 지원 범위
* IE9+

## 설치
```code
<script src="https://unpkg.com/vue"></script>
```

### 1. Declaravite Rendering (선언적 렌더링)
- DOM의 문제점 : 톰을 통해 화면을 다시그리는 것은 비싸고, 지장을 준다. 상태가 변경될때에 따라 DOM을 처리하는 과정은 오류가 잦고, 지루하다.
```html
<body>
<div class="demo">
        <input type="text" class="demo__input" v-model="message">
        <p class="demo__print">사용자가 입력한 값은 <span class="demo__print-area">{{ message }}</span>입니다.</p>
        <hr>
        <pre class="demo__print-data">{{ this.$data }}</pre>
    </div>

    <!--JS Library & Framework-->
    <script src="https://unpkg.com/vue"></script>

    <script>
        new Vue({
            'el': '.demo',
            'data': data
        });
    </script>
</body>
```

### 2. Component Communication
* Props in, Events out
* 명시적으로 선언해주지 않는 이상, 자식은 부모의 능력을 상속받지 않는다.

### 3. Client-Side Routing / Vue Router
### 4. VueX
### 5. Single File Vue Components
* .vue 파일 하나에 HTML, CSS, JS 파일이 모두 들어있다. 컴포넌트 별로 .vue 파일을 관리하기 때문에 유지, 보수가 편하다.
* 하나의 문서 내에서 lang속성을 사용하면 다양한 형태의 언어 및 컴파일러를 모두 사용할수 있다.
* 스타일 영역(Scope)을 지정하여 사용할수 있다.

### 6. Virtual DOM
* Render Functions 


## Directives

### v-text
```html
<!-- v-text와 mustache 태그의 차이점 -->
<body>
    <div id="app">
       <p>Vue JS는 인기 급상승 중!! {{ comment }}</p> <!-- Vue JS는 인기 급상승 중!! Vue JS는 인기 급상승 중!! -->
       <hr>
       <p v-text="comment">Vue JS는 인기 급상승 중!!</p> <!-- Vue JS는 인기 급상승 중!! -->
    </div>

    <script>
       var vm = new Vue({
           el: '#app',
           data: {
               comment: 'Vue JS는 인기 급상승 중!!'
           }
       });
    </script>
</body>
```

### v-html
### v-show

### v-if, v-else, v-else-if
```html
<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>
```

* v-if 와 v-show의 차이점
```code
v-if / 마크업에서 삭제
v-show / display 스타일을 none으로 처리
```

### v-for
### v-on
### v-bind
### v-model
### v-pre
### v-cloak
### v-once
