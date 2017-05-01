---
layout: article
title: BEM - Block, Element, Modifier
comments: true
author: 김현우
tags: BEM BEM사용법 개발방법론
---

### 1. BEM이란?

블럭(Block), 요소(Element), 변경자(Modifier)를 축약하여 부르는 이름. 

> BEM — Block Element Modifier is a methodology that helps you to create reusable components and code sharing in front-end development

    - 러시아의 Yandex라는 기업에서 탄생
    - Easy : BEM을 적용하기 위해선, 그냥 단순히 BEM의 네이밍 규칙을 따르면 된다.
    - Modular : 독립적인 블럭과 CSS 선택자는 코드의 재사용성과 모듈화를 가능케 한다.
    - Flexible : 사용자의 입맛에 맞게 재구성하여 사용할 수 있다.

BEM은 코딩 스타일이 아니라, **개발 및 설계 방법론** 이다. 객체를 코드로 표현하는 방법과 일련의 패턴을 의미하며, 프로그래밍 방법에 관한 보편적 지식이다.

#### 1-1. BEM의 목표

1. 빠른 개발 속도
    - 병렬적으로 개발을 진행(모듈화)하여 웹 사이트의 첫 버전을 신속하게 공개(프로토타입)
2. 효율적인 유지 보수
    - 오랜기간 동안 효율적으로 유지보수 할 수 있는 구조와 커뮤니케이션 방법 확립
3. 팀의 확장성
    - 급격한 학습 곡선 없이 새로운 멤버를 할당할 수 있는 환경 조성
4. 코드의 재사용
    - UI의 일관성을 유지하고 재사용성을 높이기 위해 문맥적인 의존 없는 모듈 개발

---

#### 2. 개발 방법론(methodology)

1. 단계적 개발(직렬)
2. 동시적 개발(병렬)

##### 2-1. 단계적 개발 방법론

일반적인 개발 프로세스로 디자이너와 개발자 간 각자의 영역에서 작업하며 서로 간섭하는 일이 없어야 한다. 하지만 디자인은 늘 수정 가능성이 열려 있을 뿐 아니라, 새롭게 추가되는 페이지, 요소 등이 있으므로 불규칙적으로 변하는 요구사항에 하나 하나 대응하는 것은 쉽지 않다.

> 디자이너가 페이지 시안을 제공하면, 이어서 마크업/스타일링/스크립팅을 하게 된다. 이 방법의 문제는 작업이 진행 중인 상황에서도 디자인 시안이 변경되는 경우가 잦아 개발을 뒤엎어야 하는 경우가 발생할 수 있다는 점이다.

##### 2-2. 동시적 개발 방법론

문제의 범위를 작게 나눠 디자인/개발을 최대한 병렬적으로 진행한다. 문제의 범위를 작게 나누는 이유는 변경 사항에 기민하게 대처 처리가 가능하기 때문이다. 단, 이 방법은 사전에 협업자와 긴밀한 커뮤니케이션으로 팀원 간의 조직력을 요구한다.

> 디자이너는 제작하고자 하는 페이지의 전체적인 컨셉(와이어프레임, 레이아웃, 컬러 시스템, 컴포넌트 등)을 먼저 설계(Design)하여 UI Kit을 제작한 후 개발자에게 제공한다. 그리고 개발자는 UI Kit을 토대로 레이아웃, 컬러 시스템, 컴포넌트를 모듈(부품) 단위로 작게 나눠 프로토타입 및 프레임워크를 개발한다. 이 시간에 디자이너는 자신이 만든 UI Kit을 토대로 페이지를 제작하여 개발자에게 제공하면, 개발자는 제작된 프레임워크를 활용하여 페이지를 제작한다.

---

### 3. 적용

##### BEM은 동시적 개발 방법론에 속한다. 우선 **하나로 일치된 도메인(Unified Data Domain)**을 가져야 한다.

서로 간섭없이 개발하는게 아니라 Block의 이름을 함께 짓고, 이해관계자가 공통적인 용어를 사용해야 한다. 이를 `Unified Data Domain`이라고 한다. 각 영역에 이름을 붙이고 함께 사용하면 커뮤니케이션 비용을 낮출 수 있다. **변경이 필요한 영역을 정확하게 알려줄 수 있고 각 영역을 조합해 새로운 영역을 만들어 낼 때도 몇 마디 대화 만으로 의사를 전달할 수 있다**.

##### Block

애플리케이션의 컴포넌트(부품)로써 독립된 영역을 지칭한다. Block은 Context에 의존적이지 않은 독립된 객체 또는 높은 수준으로 추상화 한 컴포넌트이다. 하위에 요소만 포함할 수도 있고, 또 다른 블럭을 포함할 수도 있다.

##### Element

Block을 구성하는 작은 단위를 의미한다. Element는 특정 기능을 담당한다. Block과는 달리 Context에 의존적이며 요소가 속한 Context 내에서만 의미를 갖는다.

##### Modifier

블럭 또는 요소의 스타일이나 동작을 표현할 경우 사용한다. (상태 디자인, State Design)

숨겨놓은 요소를 출력하거나 특정 버튼에 커서를 올렸을 때, 배경색을 변경하는 등 블럭이나 요소의 상태를 표현한다. 기존과 비슷하지만 스타일이나 동작이 조금 다른 블럭이나 요소를 만들고 싶은 경우에 사용한다.

---

### 4. Naming Guide

#### 4-1. MindBEMding

BEM 방법론을 기반으로 한 Naming Guide

BEM은 클래스 명명 규칙을 강제하지 않는다. 많은 사람이 오해하고 있는 호불호가 극명하게 갈리는 명명법은 BEM 방법론을 기반으로 한 MindBEMding 명명법이다.

> The naming techniques covered in this post are not the original BEM ones, but are improved versions that I much prefer. Whatever the actual notation used, they are all based on the same BEM principles.

```scss
.block {} // .block 영역 : represents the higher level of an abstraction or component.
.block__element {} // .block을 지원하는 자식 요소 represents a descendent of .block that helps form .block as a whole.
.block--modifier {} // .block의 상태를 나타내는 변환자 represents a different state or version of .block.
```

하나의 하이픈이나 언더스코어 대신 두 개를 사용하는 이유는 block의 네이밍에 하이픈이나 언더스코어가 포함 될 수 있기 때문이다.

```scss
.site-search {} /* Block */
.site-search__field {} /* Element */
.site-search--full {} /* Modifier */
```

BEM이 의도하고자 하는 바는 네이밍 자체로 해당 마크업 요소가 어떤 일을 하는지 명확하게 알리기 위함이다. 그리고 해당 요소가 어떤 Context에 속하고, 해당 block 안에서 어떤 element의 상태변화를 의미하는지 쉽게 구분하기 위함이다.

```scss
.person {} // 사람
.person__hand {} // 사람에 속하는 손
.person--female {} // 사람의 종류인 여성
.person--female__hand {} // 사람의 종류인 여성의 손
.person__hand--left {} // 사람에 속하는 손 중에 왼쪽 손
```

아래 코드와 비교해보면 어떤 Naming 규칙이 Context와 Element, Variation의 관계를 분명하게 나타내는지 알 수 있다.

```scss
.person {}
.hand {}
.female {}
.female-hand {}
.left-hand {}
```

Context와 Element, Variation의 관계를 명확하게 알기 어렵고, 서로의 연결이 끊겨있다.

> We tie concrete links to other elements of our code through naming alone. Powerful stuff.

##### examples

```html
<form class="site-search  site-search--full">
    <input type="text" class="site-search__field">
    <input type="Submit" value ="Search" class="site-search__button">
</form>
```

```html
<div class="media">
    <img src="logo.png" alt="Foo Corp logo" class="media__img--rev">
    <div class="media__body">
        <h3 class="alpha">Welcome to Foo Corp</h3>
        <p class="lede">Foo Corp is the best, seriously!</p>
    </div>
</div>
```

##### Uuuugly!

흔히 이러한 Naming Guide에 반대하는 사람들은 코드가 못생겨진다고 말한다. 하지만 보기에 이상해도 분명한 목적을 가지고 있다면, 충분히 고려해볼만 하다.

> BEM may look a little funny – and it might require more typing (most text editors have autocomplete, and gzip will negate any differences in filesize) – but it is so powerful.

##### MindBEMding을 올바르게 사용하기

> When you are using BEM, though, it is important to remember that you don’t need to use it for everything. Take for example:

```scss
.caps { text-transform: uppercase; }
```

> This CSS would never fall into any BEM category, it’s merely a standalone rule.

```scss
.header {}
.header__logo {}
```

> This is unnecessary. The trick with BEM is knowing when something falls into a relevant category. Just because something happens to live inside a block it doesn’t always mean is is actually a BEM element.  In the case of our site logo it lives in the .header purely coincidentally; it could just as easily be in our sidebar or footer. An element’s scope can start in any context, so you need to make sure you only apply BEM as far as you need to.

```scss
.site-logo {}
```

> Everything is potentially open to moving into BEM territory, though. Taking our .site-logo example again, imagine that we want to have a festive version of the logo for our Christmassy site design. We could have:

```scss
.site-logo--xmas {}
```
> We can quickly build variations of things by using the -- modifier notation. :+1:

#### modified BEM

Naming 할 때 중요한 것은 일관성이다. 일관성을 위해서 BEM과 같은 방법론을 사용할 것을 권한다. 

> 18F generally recommends using a modified BEM methodology outlined in the next subsection. However, you might want to use standard BEM when:
>
>   - You need a naming scheme that general CSS developers will already be familiar with or an existing naming scheme hasn’t been consistent enough.
>   - When you want to use JavaScript to modify the BEM class names dynamically.

##### BEM 사용 예

```scss
// block
.inset {
  margin-left: 15%;

  // element
  .inset__content {
    padding: 3em;
  }
}

// modifier
.inset--sm {
  margin-left: 10%;

  .inset__content {
    padding: 1em;
  }
}

// modifier
.inset--lg {
  margin-left: 20%;
}
```

---

> #### 참고 문헌
> 1. **[github.com/yamoo9](https://github.com/yamoo9/FDS/blob/3rd_FDS/REFERENCES/BEM.md)** : BEM Summary
> 2. **[http://getbem.com/](http://getbem.com/)** : BEM 공식 사이트
> 3. **[MindBEMding](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)** : getting your head ’round BEM syntax
> 4. **[Modified BEM](https://pages.18f.gov/frontend/#suggested-custom-methodology)** : 18F generally recommends using a modified BEM methodology
