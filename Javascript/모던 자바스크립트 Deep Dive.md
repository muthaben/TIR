> 저자: 이웅모<br>
> 출판: 위키북스(2020)<br>
***
<details>
<summary>객체지향 프로그래밍 개요</summary>
<div markdown="1">
객체지향 프로그래밍은 프로그램을 명령어 또는 함수의 목록으로 보는 전통적인 명령형 프로그래밍(imperative programming)의 절차지향적 관점에서 벗어나 여러 개의 독립적 단위, 즉 <b>객체(object)의 집합으로 프로그램을 표현</b>하려는 프로그래밍 패러다임을 말한다.<br>이는 실세계의 실체(사물이나 개념)를 인식하는 철학적 사고를 프로그래밍에 접목하려는 시도에서 시작한다. <b>실체는 특징이나 성질을 나타내는 속성(attribute/property)을 가지고 있고, 이를 통해 실체를 인식하거나 구별</b>할 수 있다.<br>다양한 속성 중에서 <u>프로그래밍에 필요한 속성만 간추려 내어 표현하는 것을 추상화(abstraction)</u>라 한다.<br>객체지향 프로그래밍은 객체의 상태(state)를 나타내는 데이터와 상태 데이터를 조작할 수 있는 동작(behavior)을 하나의 논리적인 단위로 묶어 생각한다.<br><b>객체는 상태 데이터(프로퍼티)와 동작(메서드)을 하나의 논리적인 단위로 묶은 복합적인 자료구조</b>다. 각 객체는 고유의 기능을 갖는 독립적인 부품으로 볼 수 있지만 자신의 고유한 기능을 수행하면서 다른 객체와 <b>관계성(relationship)</b>을 가질 수 있다. 다른 객체와 메시지를 주고받거나 데이터를 처리할 수도 있다. 또는 다른 객체의 상태 데이터나 동작을 <b>상속</b>받아 사용하기도 한다.
<!-- <img width="500" alt="prototype" src="./image/"><br> -->
<pre>
<code>
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
</code>
</pre>
- 260 ~ 261쪽
</div>
</details>
<details>
<summary>상속과 프로토타입</summary>
<div markdown="1">
상속(inheritance)은 객체지향 프로그래밍의 핵심 개념으로 <b>어떤 객체의 프로퍼티 또는 메서드를 다른 객체가 상속받아 그대로 사용할 수 있는 것</b>을 말한다.<br> 자바스크립트는 프로토타입을 기반으로 상속을 구현하여 불필요한 중복을 제거한다. 중복을 제거하는 방법은 <b>기존의 코드를 적극적으로 재사용</b>하는 것이다.<br>
- 261 ~ 264쪽
</div>
</details>