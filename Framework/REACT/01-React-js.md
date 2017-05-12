# React.js

## 특징

### JUST THE UI
> React.js는 UI 컴포넌트를 만들기 위한 라이브러리이다. 컴포넌트 지향 프레임워크는 여러 가지가 있지만 React.js는 정말 UI 컴포넌트만 지원한다. 비록 지원하는 범위는 작지만, 애플리케이션을 만드는 방법을 크게 바꿀 수 있다는 점이 특이하다. 또한, 이해 비용이 적어 도입하기 쉬우며 Backbone.js의 뷰 부분을 React.js로 구현하거나 Angular.js의 directives를 React.js를 사용해 구현하는 등 여러 환경과 조합해 사용할 수 있다.

### VIRTUAL DOM
> React.js는 자바스크립트 내에 DOM Tree와 같은 구조체를 VIRTUAL DOM으로 갖고 있다. 다시 그릴 때는 그 구조체의 전후 상태를 비교하여 변경이 필요한 최소한의 요소만 실제 DOM에 반영한다. 따라서 무작위로 다시 그려도 변경에 필요한 최소한의 DOM만 갱신되기 때문에 빠르게 처리할 수 있다.

### DATA FLOW
> React.js는 단방향 데이터 흐름을 지향한다. 따라서 Angular.js의 양방향 데이터 바인딩을 사용할 때처럼 작성할 코드의 양이 확연히 줄거나 하지는 않는다. 그렇지만, 애플리케이션의 데이터를 관리하는 모델 컴포넌트가 있고 그 데이터를 UI 컴포넌트에 전달하는 단순한 데이터 흐름으로 이해하고 관리하기 쉬운 애플리케이션을 만들 수 있다.

## JSX
React.js는 JSX 문법을 사용하여 템플릿을 작성한다. JSX 문법은 XML 문법과 유사하다.

### 특징
* JSX는 컴파일링 되면서 최적화 되므로, 빠르다.
* Type-safe (어떠한 연산도 정의되지 않은 결과를 내놓지 않는것, 즉 예측 불가능한 결과를 나타내지 않는 것. 컴파일링 과정에서 에러를 감지 할 수 있다.
* HTML에 익숙하다면, JSX를 사용하여 더 쉽고 빠르게 템플릿을 작성 할 수 있다.


```javascript
class App extends React.Component {
  render() // render() 메소드에서는 컴포넌트에 렌더링 될 데이타를 정의.
    {
      return (
        <h1>Hello World</h1>
      );
    }
}
```

> JSX에서 보이는 div, a 등과 같은 HTML 태그는 사실 HTML 태그가 아니라 모두 React.js의 컴포넌트다. 기본 HTML 태그를 React.js에서 미리 컴포넌트로 작성해 제공할 뿐이다. JSX로 작성되는 모든 요소는 React.js 컴포넌트로 보면 된다.

## React.js의 구조
```
project
├── package.json         
├── public            # 서버 public path
│   └── index.html    # 메인 페이지
├── src               # React.js 프로젝트 루트
│   ├── components    # 컴포넌트 폴더
│   │   └── App.js    # App 컴포넌트
│   └── index.js      # Webpack Entry point
└── webpack.config.js # Webpack 설정파일
```

## React.js의 컴포넌트

React.js에서는 기본적으로 컴포넌트를 만들고 조합하여 애플리케이션을 만든다.

### render

* 컴포넌트는 React.createClass()에 render 메서드를 가진 리터럴 객체를 전달해 작성할 수 있다.
* render()는 컴포넌트를 하나만 반환해야 합니다. 아래 처럼 복수의 컴포넌트를 반환할 수 없다.

```javascript
// NO
render() {
   return (
     <div>title</div>
     <div>contents</div>
   );
}

// OK
render() {
  return (
    <div>
      <div>title</div>
      <div>contents</div>
    </div>
  );
}
```

### Props - 컴포넌트 간의 상호작용

  * 컴포넌트 내부에 Immutable Data를 설정할때 사용
  * render() 메소드 내부 안에 { this.props.propsName } 형식으로 사용
  * 컴포넌트를 사용 할 때, < > 괄호 안에 propsName="value" 를 넣어 값을 설정  

```javascript
import React from 'react';

class Header extends React.Component {
	render() {
		return(
			<h1>{ this.props.title }</h1> // App.Header안에 title을 참조
		);
	}
}

class App extends React.Component {
	render() {
    return(
        <div>
        	<Header title={ this.props.headerTitle } /> {/* Props 객체 참조 */}
        	<Content title={ this.props.contentTitle }
        			     body={ this.props.contentBody } />
        </div>
    );
  }
}

// Props 객체설정
App.defaultProps = { 
    headerTitle: 'Default header',
    contentTitle: 'Default contentTitle',
    contentBody: 'Default contentBody'
};
```

### Props Types

* Type 검증(Validate)하기

### State - 컴포넌트를 동적으로 갱신

* 유저의 액션이나 Ajax 요청 등으로 값이 동적으로 변화하는 경우는 State를 사용한다. 
* 특정 this.state.xxx을 갱신할 때는 this.state를 사용해 갱신하는 것이 아니라 반드시 this.setState를 사용해 갱신한다.

```javascript
class Counter extends React.Component {
  
  constructor(props) {
    super(props);
    this.state = {
       count: 2
    };
  }
  
  onClick() {
    this.setState({
      count: this.state.count + 1
    });
  }
  
  render() {
    return (
      <div>
        <div>count:{this.state.count}</div>
        <button onClick={this.onClick.bind(this)}>click!</button>
      </div>
    );
  }
}
```

* state의 초기 값을 설정 할 때는 constructor(생성자) 메소드에서 this.state= { } 를 통하여 설정한다.
* state를 렌더링 할 때는 { this.state.stateName } 을 사용한다.
* state를 업데이트 할 때는 this.setState() 메소드를 사용. ES6 class에선 auto binding이 되지 않으므로, setState 메소드를 사용 하게 될 메소드를 bind 해주어야 한다. (bind 하지 않으면 React Component 가 가지고있는 멤버 함수 및 객체에 접근 할 수 없다.)
