# HTML(HyperText Markup Language)

## 1. 웹은 무엇인가?
* Tim Berners-Lee에 의해 창시.<br>
* WWW(World Wide Web)은 Internet의 서비스중 하나이다. 웹이라고 불러도 무리가 없다.<br>

## 2. 웹을 이루는 기술들
* HTML5 - 콘텐츠의 구조를 바라보아야 한다.
* CSS3 - 스타일링
* JS - 동적인 구현을 가능하게 해줌

### 2-1. 웹표준과 접근성
* 웹표준 / 방법론 : 표준'기술' (참고서적: 제프리 젤드만의 웹표준가이드)
* 웹접근성 / 목표치 : 웹의 힘에는 보편성에 있다.(누구에게나 접근이 가능한.)

#### 2-1-1. 환경에 대한 이해
* 다양한 Flatform
* Cross Browsing
* SEO(Search Engine Optimization) - 검색 엔진 최적화
* 저사양 또는 저속회선

 웹접근성은 더이상 선택이 아니라 필수다.<br>
 웹표준 / HTML 4.01, XHTML 1.0, HTML5

## 3. 마크업
* 그룹핑(구조설계) : 논리적인 순서가 중요.
* 시맨틱 마크업 : 컴퓨터가 이해하기 쉽도록 마크업해야함. http://www.w3schools.com/tags/default.asp 참조.
* 네이밍 : 의미가 이해되도록 정하는것이 중요.
* 유효성검사 : 문법적 요소를 체크해야함.

### 3-1. 요소 설명 <br>
* head에서는 meta 태그가 가장먼저 선언되어야한다.<br>

```html
<!DOCTYPE html> // DTD가 웹표준을 참고한다.
<html lang="ko"> // 이 html의 문서는 한국어로 되어있다.
<head>
  <meta charset="UTF-8"> // 8비트로 표현되는 모든 언어를 표현한다.
  <title>Document</title> // 타이틀의 콘텐츠는 SEO 관점에서 굉장히 중요하다.
  <link rel="stylesheet" href=""> // CSS를 링크한다.
</head> // 브라우저상에는 표현되지 않지만 html의 중요한 정보들을 담고 있다.
<body> // 브라우저상에 시각적으로 표현되는 부분

</body>
</html>
```

### 3-2. 아웃라인 알고리즘
* 암묵적 아웃라인 - 헤딩의 숫자만 가지고 판단한다.
* 명시적 아웃라인 - section, article, nav
* [아웃라인 알고리즘 참조](https://developer.mozilla.org/ko/docs/Web/HTML/HTML5_%EB%AC%B8%EC%84%9C%EC%9D%98_%EC%84%B9%EC%85%98%EA%B3%BC_%EC%9C%A4%EA%B3%BD)

### 3-3. 태그
* http://www.w3schools.com/tags/default.asp 참조.
* <div> - 중립적 의미를 가질때 주로 사용함. 시멘틱 코드의 관점에서 div를 남용하면. 별고민 없는 html 문서가 됨.
* `<ul>` - unorder line / `<ol>` - order line
그룹핑은 연관성있는 것끼리 묶어내야함. 디자인 요소로 묶어내면 안됨.
* `<dl>`
* `<time>`


### 3-4. 블록 요소와 인라인 요소

```html
# 블록 요소
<div>, <p>, <h1~h6>, <ol>, <ul>, <li>, <dl>, <dt>, <dd>

# 인라인 요소
<a>, <img>, <span>, <strong>, <em>, <button>
```

#### 3-4-1. 블록 요소 특징
* `<width>`, `<height>` 값을 적용할 수 있다.
* 인접한 형제 요소들로부터 줄 바꿈(내림)이 된다.
* 수직 `<margin>`과 수직 `<padding>`을 적용할 수 있다.
* `<vertical-align>` 속성을 적용할 수 없다.

#### 3-4-2. 인라인 요소 특징
* 인라인은 블록안에 속한다.
* 인라인 요소에는 `<width>`와 `<height>` 속성을 적용할수 없다.
* 인접한 `<inline>` 형제 요소들과 동일한 행에 배치된다.
* 수직 `<margin>`과 수직 `<padding>`을 적용할 수 없다.
* `<vertical-align>` 속성을 적용할 수 있다.
* `<position>`을 적용하면 `<block>` 요소로 변경된다.
* `<float>`를 적용하면 `<block>` 요소로 변경된다.
* 인라인 요소에는 공백문자가 표현된다.