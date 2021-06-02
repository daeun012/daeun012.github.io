---
title: ES6 Class의 생성자(constructor) 함수
date: 2019-04-24
tags:
  - ES6
  - JavaScript
keywords:
  - ES6
  - 생성자함수
  - constructor
  - javascript
---

## constructor

객체(인스턴스)를 생성하고 클래스 필드를 초기화하기 위한 특수한 메소드  
※ 클래스 필드 : 자바스크립트의 생성자 함수에서 this에 추가한 프로퍼티

### 1. 예문으로 이해하기

```javascript
// 클래스 선언문
class Person {
  // constructor(생성자). 이름을 바꿀 수 없다.
  constructor(name) {
    // this는 클래스가 생성할 인스턴스를 가리킨다.
    // _name은 클래스 필드이다.
    this._name = name;
  }
}

// 인스턴스 생성
const me = new Person('Lee');
console.log(me); // Person {_name: "Lee"}
cs;
```

- 클래스는 `constructor`라는 이름을 가진 특별한 메서드를 하나씩만 가질 수 있습니다. 2개 이상일 시 `SyntaxError`을 유발합니다.

- 인스턴스를 생성할 때 new 연산자와 함께 호출한 것이 바로 `constructor`이며 `constructor`의 파라미터에 전달한 값은 클래스 필드에 할당합니다.

```javascript
// 클래스 선언문
class Person {}

const me = new Person();
console.log(me); // Person {}

// 프로퍼티 동적 할당 및 초기화
me._name = 'daeun';
console.log(me); // Person {_name: "daeun"}
```

- `constructor`은 생략할 수 있습니다. 생략하면 클래스에 `constructor( ){ }`를 포함한 것과 동일하게 동작합니다.

- 따라서 인스턴스에 프로퍼티를 추가하려면 인스턴스를 생성한 이후 프로퍼티를 동적으로 추가해야 합니다.

```javascript
class Person {
  constructor(name) {
    this._name = name;
  }
}

const me = new Person('daeun');
console.log(me);
```

- `constructor`는 인스턴스의 생성과 동시에 클래스 필드의 생성과 초기화를 실행합니다.

- 따라서 클래스 필드를 초기화해야 한다면 `constructor`를 생략해서는 안됩니다.

---

#### Reference

- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes/constructor

- https://poiemaweb.com/es6-class
