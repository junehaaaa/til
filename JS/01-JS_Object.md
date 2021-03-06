# Javascript Object(객체)의 기본정의
자신의 정보를 가지고 있는 독립적인 주체.

## Property(프로퍼티)
* Property는 객체의 속성을 나타내는 접근 가능한 이름과 활용 가능한 값을 가지는 특별한 형태이다. 
* 특정 객체가 가지고 있는 정보를 품고 있기에 그 객체가 가진 정보에 직접적으로 접근할 수 있게 해주기 때문이다. 
* Property의 접근 연산자는 '.' 이다. 이 연산자를 통해 Property를 추가 할수도 있고 Property에 접근 할수도 있다.

```javascript
var apple = {}; // apple 객체를 생성.
apple.number = 1; // . 연산자를 이용하여 apple 객체의 number 프로퍼티에 생성. 1이라는 값을 할당.

var sum = apple.number + 10; // . 연산자를 이용하여 apple 객체의 number 프로퍼티에 접근하여 값을 활용할수 있다.
console.log(sum); // 11
```

> 자바스크립트에서 사용하는 변수는 값을 할당하지 않고 선언만 할경우 자바스크립트 엔진이 강제적으로 undefined를 할당한다. 하지만 프로퍼티는 값이 활당되지 않으면 존재할 필요가 없는 녀석이다. 객체의 정보를 담고 있어야할 요소가 그 어떤 정보도 할당받지 않았다면 객체로서는 이 프로퍼티는 쓸모없는 녀석이기 때문이다. 그렇기 대문에 프로퍼티를 추가하면서 값을 할당하지 않으면 syntax error다. 프로퍼티를 추가 할때 이점을 반드시 주의하여야 한다.

> 자바스크립트의 프로퍼티는 undefined나 null을 할당한다고 삭제 되지 않는다. 프로퍼티의 삭제는 delete라는 keyword를 사용해야 한다.

## Method(메서드)
객체가 가지고 있는 동작.

```javascript
var foo = {};
foo.a = 1;
foo.b = 2;
foo.sum = function() {
  console.log(foo.a+foo.b);
  };
foo.sum(); // 3
```

### 함수와 메서드가 다른점
* 메소드를 수행하기 위해서는 객체를 통해서 해당 메소드를 수행하여야 한다. 즉 그 동작을 수행하는 주체는 객체이며 그 동작을 수행하기 위해서는 객체에게 그 동작을 수행하라고 지시해야 한다.

* 함수는 그 동작을 수행하기 위해 객체에게 어떤을 동작을 수행하라고 명령하지 않아도 된다. 그이유는 함수자체가 그 동작을 정의한 함수객체이기 때문에 자기 자신을 수행하는 것이다. 함수객체라는 것에 대해서는 이후에 자세히 설명하도록 하겠다. 어찌 되었건 메소드는 객체를 움직이는 동작이며 그 동작을 수행하기 위해서 객체의 정보를 담고있는 프로퍼티를 사용할수 있다.

## Javascript 객체(Object)의 종류
* 네이티브 객체 - String, Array, Function ...
* 호스트(브라우저) 객체 - window, screen, document, location, history
* 사용자 정의 객체 - 사용자가 직접 만드는 객체 (사용자가 객체단위로 컴포넌트를 개발할수 있다.)

## Javascript 객체(Object) 생성

```javascript
/* 생성자 함수를 사용하여 객체를 생성하는 예 */
var foo = new Object(); 
foo.name='foo';
console.log(foo.name); // foo

/* JSON 방식을 사용하여 객체 리터럴 */
var foo = {
    name : 'foo'
};
console.log(foo.name); // foo
```

> 이 둘은 객체를 생성하는 방법이라는 관점에서는 동일하지만 객체의 사용이라는 방식에서는 차이가 있다. JSON 방식을 이용하면 객체리터럴이기에 단일 객체로만 활용 된다. 하지만 constructor 를 이용하면 동일한 구성을 가진 객체를 여러개 만들어 낼수 있다.

## Javascript 객체(Object) 참고사항

* 자바스크립트에서 생성하는 모든 객체는 Object 객체에서 파생되어 나온 객체. 
* 이들은 암묵적으로 Array 객체를 상속함.

### Obejct 객체

* Object 객체는 Built-in 객체로서 최상위레벨의 객체((Top-Level-Object).
* 즉 모든 객체는 이 Object 객체에서 파생되어 나온 확장형태임.
* Object 객체라는 최상위 객체를 껍대기로 파생되는 객체들은 Object 객체가 가지고 있는 기본적인 구성요소를 상속받게 된다.(사실 자바스크립트의 모든 객체가 자유롭게 확장될수 있는 이유도 Object 객체가 가진 특별한 구성요소 때문이다.)
* Object 객체가 가진 특별한 구성요소들이란 바로 constructor, prototype 이라는 프로퍼티와 hasOwnProperty(), toString(), isPrototypeOf()라는 메소드들이다. 

### Obejct의 배열 상속

* 자바스크립트의 객체는 곧 배열이다.
* JSON의 표현방식은 [] 라는 Array 표현의 다른 방식일 뿐이다. 실제로 객체의 프로퍼티 생성이나 참조에서 . 연산자가 아닌 []를 사용 할수도 있다.

```javascript
var foo = {name:'foo'};
console.log(foo['name']); // foo
```

### Class와 객체의 차이점

Class는 분류에 대한 개념이지 실체가 아니다. 반면, 객체는 실체이다.
과일이라는 분류는 Class이며, 사과는 과일의 실체인 객체이다. 생성자 함수는 객체 생성 시 호출되어 객체의 초기화를 담당한다.

```javascript
function Fruit() {
  // 과일이라는 Class
}

var apple = new Fruit();
// new Fruit(); 이라는 생성자 함수를 이용해서 Fruit의 특징을 가진 apple 이라는 객체 생성

Fruit.prototype
// Class의 prototype 프로퍼티에 멤버를 추가하면 해당 Class에 의해 생성된 객체는 해당 멤버를 공통적으로 갖게 된다.
```

Class와 객체를 구분하는 간편한 방법 중 하나는 해당 Class나 객체를 대상으로 질문을 해보는 것이다. 생물인 경우 '나이가 어떻게 되는지', 무생물의 경우 '제조일자가 어떻게 되는지' 질문해보는 것이다. 사람의 나이는 정의할 수 없다. 그러므로 Class이다. 반면 옆집 철수의 나이는 정의할 수 있다. 그러므로 객체이다. 과일의 경우 생산일이 없지만, 사과는 생산일이 있다.

객체는 유일무이하게 존재하는 실체이기 때문에 속성에 값을 가지고 있고,
클래스는 개념이면서 분류 체계일 뿐이므로 속성에 값을 가질 수 없다.

- 미키마우스의 꼬리는? 1개
- 제리의 꼬리는? 1개
- 쥐의 꼬리는? 1개

쥐는 클래스인데 꼬리의 개수에 답을 가지고 있다.
메모리 상의 모든 쥐의 객체가 같은 꼬리 개수를 갖는데, 이를 따로 정의할 필요가 있을까?
같은 클래스의 모든 객체가 같은 값을 가지고 있다면 그 값은 클래스에 저장하면 어떨까? 이 경우 prototype에 해당 속성을 정의하면 된다. 즉, 추상화된 Class에 이미 정해진 프로퍼티나 메서드는 prototype을 사용해 정의하면 된다.

```javascript
쥐.prototype.꼬리개수 = 1;
쥐.prototype.울다 = function () { return "찍찍"; };

var 제리 = new 쥐();
var 미키 = new 쥐();
제리.꼬리개수; // 1
미키.꼬리개수; // 1
제리.울다(); // 찍찍
미키.울다(); // 찍찍
```