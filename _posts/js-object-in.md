---
title: 'in' 연산자로 객채의 프로퍼티 존재 여부 확인하기
date: 2019-10-16
tags:
  - JavaScript
  - ES6
keywords:
  - JavaScript
  - ES6
  - in
---

- 'in' 연산자 사용하기
- 'in' 연산자 응용하기 : 'for...in' 반복문

---

## 'in' 연산자 사용하기

```javascript
'key' in object;
```

※ in 왼쪽엔 반드시 프로퍼티 이름이 와야한다.

```javascript
let user = { name: 'John', age: 30 };

alert('age' in user); // user.age가 존재하므로 true 출력
alert('blabla' in user); // user.blabla 존재하지 않으므로 false 출력

let obj = {
  test: undefined,
};

alert(obj.test); // 값이 `undefined`이므로, 얼럿 창엔 undefined가 출력

alert('test' in obj); // `in`을 사용하면 프로퍼티 유무를 제대로 확인할 수 있다.(true가 출력됨).
```

---

## 'in' 연산자 응용하기 : 'for...in' 반복문

```javascript
for (key in object) {
  // 각 프로퍼티 키(key)를 이용하여 본문(body)을 실행한다.
}
```

```javascript
let user = {
  name: 'John',
  age: 30,
  isAdmin: true,
};

for (let key in user) {
  // 키
  alert(key); // name, age, isAdmin
  // 키에 해당하는 값
  alert(user[key]); // John, 30, true
}
```

---

#### Reference

- https://ko.javascript.info/object
