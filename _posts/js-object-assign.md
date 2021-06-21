---
title: Object.assign을 이용한 객체 복사하기
date: 2019-10-18
tags:
  - JavaScript
  - ES6
keywords:
  - JavaScript
  - ES6
  - Object.assign
---

## Object.assign() 사용하기

열거할 수 있는 하나 이상의 복사하고자 하는 객체로부터 대상 객체로 속성을 복사할 때 사용한다. 대상 객체를 반환한다.

```javascript
Object.assign(dest, [src1, src2, src3...])
```

- dest : 대상 객체(목표로 하는 객체)
- src1, ...., srcN : 복사하고자 하는 객체

```javascript
let user = { name: 'John' };

let permissions1 = { canView: true };
let permissions2 = { canEdit: true };

// permissions1과 permissions2의 프로퍼티를 user로 복사한다.
Object.assign(user, permissions1, permissions2);

// now user = { name: "John", canView: true, canEdit: true }
```

목표 객체(user)에 동일한 이름을 가진 프로퍼티가 있는 경우

```javascript
let user = { name: 'John' };

Object.assign(user, { name: 'Pete' });

alert(user.name); // user = { name: "Pete" }
```

빈 배열에 복사하기

```javascript
let user = {
  name: 'John',
  age: 30,
};

let clone = Object.assign({}, user);
```

---

#### Reference

- https://ko.javascript.info/object-copy
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign
