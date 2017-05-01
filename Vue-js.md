# VUE JS FRAMEWORK


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

## 2. 템플릿 문법

### 2-1. 보간법(Interpolation)
#### 문자열
* 데이터 바인딩의 가장 기본 형태는 “Mustache” 구문(이중 중괄호)을 사용한 텍스트 보간입니다.

```html
<span>메시지: {{ msg }}</span>
```

* Mustache 태그는 해당 데이터 객체의 msg 속성 값으로 대체됩니다. 또한 데이터 객체의 msg 속성이 변경될 때 마다 갱신됩니다.
* `v-once` 디렉티브을 사용하여 데이터 변경 시 업데이트 되지 않는 일회성 보간을 수행할 수 있지만, 같은 노드의 바인딩에도 영향을 미친다는 점을 유의해야 합니다.

```html
<span v-once>다시는 변경하지 않습니다: {{ msg }}</span>
```

### 2-2. 디렉티브(Directives)

* `v-text`
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

* `v-html`
* `v-show`
* `v-if`, `v-else`, `v-else-if`
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

* `v-for`
```html
<ul class="reset-list vue-features">
    <!-- 배열 테디어 순환 처리: feature(객체) -->
    <li v-for="(feature, index) of vue_features">
        <div v-for="value, key, index of feature">
            ({{ index }}) {{ key }}; {{ value }}
        </div>
        <hr v-if="index !== vue-features.length - 1">
    </li>
</ul>
```
* `v-bind`
* `v-model`
* `v-pre`
* `v-cloak`
* `v-once`

### 약어
* `v-on`
* `v-bind`

## 3. List Rendering (리스트 렌더링)

* `Vue.set( target, key, value )`
* `Vue.delete( target, key )`

## 4. Life Cycle(Event Hook)

## 5. Event Listener (이벤트 처리기)

* `v-on`
* `v-on:click.prevent`, `v-on:mouseover`

## 6. 계산된 속성과 감시자

### 계산된 속성 - Computed(getter, setter) 
* method와 computed 차이는 뭘까?
* computed은 함수가 아니다.
* method는 상태가 바뀔때마다 실행된다.(기존에 의존되있는 설정값을 바꾸지 않더라도.)
* computed은 상태가 변경이되어도 바뀌지 않는다.(기존에 의존되있는 설정값이 수정되지 않는 이상은.)

### 감시자 - watch
* 서버에서 응답이 올때까지 기다릴때.
* 마냥 기다리는 것은 비용낭비이니, 그럴땐 계산된 속성을 사용하자.


1. new Vue 인스턴스를 생성
2. Static 메서드 생성 (Vue.set, Vue.delete 등)
3. Life Cycle
4. Method를 등록할수 있다.
모든 속성에는 v-bind를 붙일수 있다. 동적처리를 위해서는 v-bind가 필요하다.

## 7. Component
* 기본 HTML 엘리먼트를 확장하여 재사용 가능한 코드를 캡슐화하는데
도움이 된다.

### Component 사용하기
```javascript
// 전역 컴포넌트 등록하기
Vue.component('tag-name', {
    // 옵션
    });

var app = new Vue({
    el: '#app',
    // 지역 컴포넌트 등록하기
    component: {

    }
});
```

