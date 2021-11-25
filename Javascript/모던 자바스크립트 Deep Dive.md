> 저자: 이웅모<br>
> 출판: 위키북스(2020)<br>
***
<details>
<summary>객체지향 프로그래밍 개요</summary>
<div markdown="1">

객체지향 프로그래밍은 프로그램을 명령어 또는 함수의 목록으로 보는 전통적인 명령형 프로그래밍(imperative programming)의 절차지향적 관점에서 벗어나 여러 개의 독립적 단위, 즉 **객체(object)의 집합으로 프로그램을 표현**하려는 프로그래밍 패러다임을 말한다.  
이는 실세계의 실체(사물이나 개념)를 인식하는 철학적 사고를 프로그래밍에 접목하려는 시도에서 시작한다. **실체는 특징이나 성질을 나타내는 속성(attribute/property)을 가지고 있고, 이를 통해 실체를 인식하거나 구별**할 수 있다.  
다양한 속성 중에서 프로그래밍에 필요한 속성만 간추려 내어 표현하는 것을 **추상화(abstraction)**라 한다.  
**객체지향 프로그래밍은 객체의 상태(state)를 나타내는 데이터와 상태 데이터를 조작할 수 있는 동작(behavior)을 하나의 논리적인 단위로 묶어 생각한다.  
**객체는 상태 데이터(프로퍼티)와 동작(메서드)을 하나의 논리적인 단위로 묶은 복합적인 자료구조**다.  
각 객체는 고유의 기능을 갖는 독립적인 부품으로 볼 수 있지만 자신의 고유한 기능을 수행하면서 다른 객체와 **관계성(relationship)**을 가질 수 있다. 다른 객체와 메시지를 주고받거나 데이터를 처리할 수도 있다. 또는 다른 객체의 상태 데이터나 동작을 **상속**받아 사용하기도 한다.
```js
// 상태 데이터(이름과 주소), 동작(커밋과 운동)이 하나의 단위로 구성된 객체 person
const person = {
  name: 'John',
  addresss: 'Seoul',
  makeCommit (input) {
    return `a result of ${input}`
  },
  doPullUps (numsOfRepetition) {
    return `a result of ${numsOfRepetition}`
  }
}
```
<260 ~ 261쪽>

</div>
</details>
<details>
<summary>생성자 함수에 의한 객체 생성</summary>
<div markdown="1">

## Object 생성자 함수  
new 연산자와 함께 Object 생성자 함수를 호출하면 빈 객체를 생성하여 반환한다. 빈 객체 생성 후 프로퍼티 또는 메서드를 추가하여 객체를 완성할 수 있다.
```js
// 빈 객체 생성
const person = new Object()

// 프로퍼티 추가
person.name = 'John'
person.sayHello = function () {
  console.log(`Hi! My name is ${this.name}`)
}

console.log(person)  // {name: "John", sayHello: f}
person.sayHello()  // Hi! My name is John
```
생성자 함수(constructor)란 new 연산자와 함께 호출하여 객체(인스턴스)를 생성하는 함수를 말한다. 생성자 함수에 의해 생성된 객체를 인스턴스(instance)라 한다.  
## 생성자 함수
### 객체 리터럴에 의한 객체 생성 방식의 문제점
객체 리터럴에 의한 객체 생성 방식은 직관적이고 간편하지만 단 하나의 객체만 생성한다. 따라서 동일한 프로퍼티를 갖는 객체를 여러 개 생성해야 하는 경우 매번 같은 프로퍼티를 기술해야 하기 때문에 비효율적이다.  
객체는 프로퍼티를 통해 객체 고유의 상태(state)를 표현하고, 메서드를 통해 상태 데이터인 프로퍼티를 참조하고 조작하는 동작(behavior)을 표현한다. 따라서 **프로퍼티는 객체마다 프로퍼티 값이 다를 수 있지만 메서드는 내용이 동일한 경우가 일반적**이다.  
### 생성자 함수에 의한 객체 생성 방식의 장점
생성자 함수에 의한 객체 생성 방식은 마치 객체(인스턴스)를 생성하기 위한 탬플릿(클래스)처럼 **프로퍼티 구조가 동일한 객체 여러 개를 간편하게 생성**할 수 있다.
```js
// 생성자 함수: 일반 함수와 동일한 방식으로 정의
function Circle (radius) {
  // 생성자 함수 내부의 this는 생성자 함수가 생성할 인스턴스를 가리킨다.
  this.radius = radius
  this.getDiameter = function () {
    return 2 * this.radius
  }
}

// 인스턴스의 생성: new 연산자와 함께 호출 -> 생성자 함수로 동작
const circle1 = new Circle(5)  // 반지름이 5인 Circle 객체를 생성
const circle2 = new Circle(10) // 반지름이 10인 Circle 객체를 생성

console.log(circle1.getDiameter())  // 10
console.log(circle2.getDiameter())  // 20
```
생성자 함수는 이름 그대로 객체(인스턴스)를 생성하는 함수다.  
하지만 자바와 같은 클래스 기반 객체지향언어의 생성자와는 다르게 그 형식이 정해져 있는 것이 아니라 **일반 함수와 동일한 방법으로 생성자 함수를 정의하고 new 연산자와 함꼐 호출하면 해당 함수는 생성자 함수로 동작**한다. 만약 new 연산자와 함께 생성자 함수를 호출하지 않으면 생성자 함수가 아니라 일반 함수로 동작한다.
```js
const circle3 = Circle(15)

// 일반 함수로서 호출된 Circle은 반환문이 없으므로 암묵적으로 undefined를 반환한다.
console.log(circle3)  // undefined
```  
<234 ~ 238쪽>

</div>
</details>
<details>
<summary>상속과 프로토타입</summary>
<div markdown="1">

상속(inheritance)은 객체지향 프로그래밍의 핵심 개념으로 **어떤 객체의 프로퍼티 또는 메서드를 다른 객체가 상속받아 그대로 사용할 수 있는 것**을 말한다.  
자바스크립트는 프로토타입을 기반으로 상속을 구현하여 불필요한 중복을 제거한다. 중복을 제거하는 방법은 **기존의 코드를 적극적으로 재사용**하는 것이다.   
```js
// 생성자 함수
function Circle (radius) {
  this.radius = radius
}

// Circle 생성자 함수가 생성한 모든 인스턴스가 getArea 메서드를
// 공유해서 사용할 수 있도록 프로토타입에 추가한다
// 프로토타입은 Circle 생성자 함수의 prototype 프로퍼티에 바인딩되어 있다.
Circle.prototype.getArea = function () {
  return math.PI * this.radius ** 2
}

// 인스턴스 생성
const circle1 = new Circle(1)
const circle2 = new Circle(2)

// Circle 생성자 함수가 생성한 모든 인스턴스는 부모 객체의 역할을 하는
// 프로토타입 Circle.prototype으로부터 getArea 메서드를 상속받는다.
// 즉, Circle 생성자 함수가 생성하는 모든 인스턴스는 하나의 getArea 메서드를 공유한다.
console.log(circle1.getArea === circle2.getArea)  // true

console.log(circle1.getArea())  // 3.141592653...
console.log(circle2.getArea())  // 12.56637061...
```  
Circle 생성자 함수가 생성한 모든 인스턴스는 자신의 프로토타입, 즉 상위(부모) 객체 역할을 하는 Circle.prototype의 모든 프로퍼티와 메서드를 상속받는다.  
getArea 메서드는 단 하나만 생성되어 프로토타입인 Circle.prototype의 메서드로 할당되어 있다. 따라서 Circle 생성자 함수가 생성하는 모든 인스턴스는 getArea 메서드를 상속받아 사용할 수 있다. 즉, 자신의 상태를 나타내는 radius 프로퍼티만 개별적으로 소유하고 **내용이 동일한 메서드는 상속을 통해 공유**하여 사용하는 것이다.  
> 프로토타입은 어떤 객체의 상위(부모) 객체의 역할을 하는 객체로서 다른 객체에 공유 프로퍼티(메서드 포함)를 제공한다.   
> 프로토타입을 상속받은 하위(자식) 객체는 상위 객체의 프로퍼티를 자신의 프로퍼티처럼 자유롭게 사용할 수 있다.  

모든 객체는 [[Prototype]]이라는 내부 슬롯을 가지며, 여기에 저장되는 프로토타입은 객체 생성 방식에 의해 결정된다.  
* 객체 리터럴에 의해 생성된 객체의 프로토타입: Object.prototype  
* 생성자 함수에 의해 생성된 객체의 프로토타입: 생성자 함수의 prototype 프로퍼티에 반영되어 있는 객체  

**모든 객체는 하나의 프로토타입을 갖는다. 그리고 모든 프로토타입은 생성자 함수와 연결되어 있다.**  

<261 ~ 264쪽>
  
</div>
</details>