# Function

* 독립적으로 분리된 로직으로서 프로그램 수준에서 미리 정의되어 있거나 사용자정의에 의해 만들어진 실행단위를 일컫는 말이다. 
* 자바스크립트의 function은 Fisrt-Class-Object 로서 변수나 데이터 구조 안에 담을 수 있으며 인자로 전달할 수 있고 반환 값으로도 사용할 수 있으며, 런타임에 생성할 수도 있다. 생성자 함수, 함수의 인자, 함수의 반환 값, 객체의 멤버, 배열의 원소로서 다양하게 사용된다.

> #### 일급객체(First-Class Object)의 특징 
> * 변수, 데이터 구조 안에 담을 수 있다.
> * 인자(Parameter, Argument)로 전달할 수 있다.
> * 반환 값(Return Value)으로 사용할 수 있다.
> * 런타임(실행) 중에 생성할 수 있다.
> * 할당에 사용된 이름과 관계 없이 고유하게 식별할 수 있다.

```javascript
// 변수에 함수를 할당할 수 있다.
var fn = function () { ... };

fn();

// 함수의 인자로 함수가 전달될 수 있다.
function fn(callback) {
    callback();
}

fn( function() { ... } );

// 함수의 반환 값으로 함수를 내보낼 수 있다. (객체도 가능)
function fn() {
    return function() { ... };
}

fn()();

// 객체의 속성으로 함수를 설정할 수 있다. (메소드)
var obj = {
    "fn": function() { ... }
};

obj.fn();

// 배열의 원소(Item)로 함수를 메모리할 수 있다.
var arr = [];
arr[0] = function() {...};

arr[0]();
```

#### 생성자 함수

```javascript
function Person() {} // 생성자 함수
var jiwoo = new Person(); // 생성된 객체
var heechan = new Person(); // 생성된 객체
```

#### callback 함수

- callback 함수는 보통 동기(async) 처리에 사용한다.
- 특정 이벤트 종료 시점에 callback 함수를 통해 이벤트를 실행할 수 있다.

```javascript
function(el, callback) {
  // some codes...
  // 해당 함수가 결과값을 리턴하기 바로 전에 callback 함수를 호출한다.
  // 예 : 특정 이벤트가 종료되는 시점에 이벤트를 실행 할 수 있다.
  if(callback && typeof callback === 'function') {
    callback();
  }
  return el;
}
```

```javascript
// callback 함수의 jQuery 사용 예시

$('.off-canvas-menu-button').on('click', function(){
  $(this).parent().animate({
    'transform' : 'translateX(100px)'
  }, 400, 'ease-out-back', function() {
    console.log('finished animation.');
  })
});
// function() {
//    console.log('finished animation.');
// 이 부분은 모든 애니메이션이 끝나면 실행되는 callback 함수이다.
```

## 함수선언(Function Declarations)이란?
* 함수선언은 `Function Statement` 라고도 하며 말그대로 함수 문장이란 뜻이다. 이는 곧 실행가능한 코드블럭이 아니며 함수의 정의를 나타내는 문장으로 해석되며 따라서 코드해석에 따른 수행결과가 존재하지 않는다는 것을 의미한다.

* 함수 선언문이 `Statement` 라고 하는 말은 정의에서 밝힌것 처럼 코드블럭 자체는 실행가능 코드가 아니라는 것이다. 즉 해당 코드블럭을 콘솔에서 실행하여도 어떠한 결과도 `return` 되지 않는다. 그러한 이유로 함수선언문을 Class와 동일한 개념으로 이해해도 무방하다.

```javascript
//Function Declarations
function foo() {
    console.log('hello');
}
```

## 함수표현(Function Expressions)이란?
* 함수표현은 `Function Literal` 이다. 이는 실행 가능한 코드로 해석 되어지거나 변수나 데이터구조에 할당되어지고 있음을 의미한다. 즉, 해당 코드블럭이 실행코드로서 해석되어지며 동시에 코드실행에 따른 결과값을 가지거나 특정 변수에 할당된 값으로 존재한다.

```javascript
// anonymous function expression
var foo = function() {
    console.log('hello');
};

// named function expression
var foo = function foo() {
    console.log('hello');
};

// self invoking function expression
(function foo() {
    console.log('hello');
})();
```

> 위 코드에서 named function expression는 매우 특이하다. foo 라는 변수에 이름있는 함수를 할당하고 있다. 흔히 알고 있는 함수리터럴과는 좀 거리가 있다. 하지만 이 named function expression에는 한가지 특징이 있다. 바로 해당 함수의 이름은 함수밖에서는 사용할수 없다는 것이다.

```javascript
var foo = function A() {
    A(); // 실행가능 
}

A(); //  Syntax Error
```

* 이처럼 함수표현은 함수리터럴로 특정변수에 할당되거나 즉시 실행가능한 코드 블럭으로서 존재하는 함수를 의미하는 것이다. 함수표현이 실행코드로서 해석되기 위해서는 ()를 이용하여 함수를 감싸 주어야 한다. 이를 자기호출함수(self invoking function)라고도 한다. 자기호출함수는 재귀함수와는 다른 개념이다. 재귀함수는 함수 안에서 자신을 호출하는 형식이지만 자기호출함수는 해석과 동시에 실행되는 코드블럭을 말한다.

* 이들 함수선언과 함수표현은 함수호출 방법에서는 큰 차이가 없다. 하지만 호이스팅(hoisting) 관점에서는 큰 차이를 보이게 된다.

## 호이스팅(Hoisting) 

* 인터프린터가 자바스크립트 코드를 해석함에 있어서 Global 영역의 선언된 코드블럭을 최상의 Scope로 끌어올리는 것을 호이스팅이라 한다.

* 호이스팅에서 중요한 부분은 statement는 호이스팅 되지만 할당은 호이스팅 되지 않는 다는 것이다. 즉, `{}` 안의 내용은 포함하지만 `=` 연산자를 사용한 값은 호이스팅 되지 않는다.

```javascript
// 함수선언에서의 호이스팅
foo();
function foo() {
    console.log('hello');
};
> hello
```
```javascript
// 함수표현에서의 호이스팅
foo();
var foo = function() {
    console.log('hello');
};
> Syntax Error 
```
> 위 코드에서 알수 있듯이 함수선언은 `foo();` 라는 실행코드를 해석하기 이전에 `foo` 함수에 대한 선언을 호이스팅하여 global 객체에 등록시키기 때문에 오류 없이 수행된다. 하지만 함수표현은 변수에 함수리터럴을 할당하는 구조이기 때문에 Hoisting 되지 않으며 `Syntax Error` 를 발생시킨다.

## Scope

## Scope Chain

## Arguments

## Constructor