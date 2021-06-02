---
title: async-await
date: 2019-06-02
tags:
  - JavaScript
  - ES6
keywords:
  - async-await
  - async
  - 비동기
---

- async
- await
- async-await : 에러 핸들링하기
- async/await 과 promise.then/catch 비슷한데 뭘 쓰지?

---

## async

`async`는 function 앞에 위치한다.

```javascript
async function f() {
  return 1;
}

f().then(alert); // 1
```

- function 앞에 `async`를 붙이면 해당 함수는 항상 프라미스를 반환한다.

---

## await

```javascript
// await는 async 함수 안에서만 동작한다.
async function f() {
  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve('완료!'), 1000);
  });

  let result = await promise; // 프라미스가 이행될 때까지 기다림

  alert(result); // "완료!"
}

f();
```

- 프라미스가 처리될 때까지 함수 실행을 기다리게 한다.
- 프라미스가 처리되면 그결과와 함께 실행이 재게 된다.
- 프라미스가 처리되길 기다리는 동안에 엔진은 다른 일(다른 스크립트를 실행, 이벤트 처리 등)을 할 수 있다.

---

## async & await : 에러 핸들링하기

```javascript
async function f() {
  await Promise.reject(new Error('에러 발생!'));
}

// throw문을 사용해 위와 동일한 코드를 작성할 수 있다.
async function f() {
  throw new Error('에러 발생!');
}

// 또는 try catch문을 사용해 잡을 수 있다.
async function f() {
  try {
    let response = await fetch('http://유효하지-않은-url');
    let user = await response.json();
  } catch (err) {
    // fetch와 response.json에서 발행한 에러 모두를 여기서 잡습니다.
    alert(err);
  }
}

f();
```

---

## async/await 과 promise.then/catch 비슷한데 뭘 쓰지?

비슷하다. 둘 중 편한 것을 쓰면 된다.

하지만 여러 개의 프라미스가 모두 처리되길 기다려야 하는 상황이라면...

```javascript
// 프라미스 처리 결과가 담긴 배열을 기다립니다.
let results = await Promise.all([
  fetch(url1),
  fetch(url2),
  ...
]);
```

실패한 프라미스에서 발생한 에러는 보통 에러와 마찬가지로 Promise.all로 전파된다. 에러 때문에 생긴 예외는 try...catch로 감싸 잡을 수 있다.

---

#### Reference

- https://ko.javascript.info/
