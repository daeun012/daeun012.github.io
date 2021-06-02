---
title: Babel
date: 2020-08-10
tags:
  - JavaScript
  - ES6
keywords:
  - babel
  - es6
  - javascript
---

- Babel이란?
- Babel 사용해보기

---

## Babel이란?

**Babel은 JavaScript 컴파일러이다.**
즉, 최신 사양의 자바스크립트 코드를 IE나 구형 브라우저에서도 동작하는 ES5 이하의 코드로 변환하는 트랜스파일러라고 보면 된다.

```javascript
// ES6 화살표 함수와 ES7 지수 연산자
[1, 2, 3].map((n) => n ** n);
```

Babel은 위와 같은 코드를 아래와 같이 변환한다.

```javascript
// ES5
('use strict');

[1, 2, 3].map(function (n) {
  return Math.pow(n, n);
});
```

---

## Babel 사용해보기

### 1. 사용하기 전 준비

```bash
$ npm install --save-dev @babel/core @babel/cli @babel/preset-env
```

설치가 완료되었으면 프로젝트 루트에 `.babelrc` 파일을 생성하고 아래와 같이 작성한다.

```json
// 지금 설치한 @babel/preset-env를 사용하겠다는 의미이다.
{
  "presets": ["@babel/preset-env"]
}
```

### 2. @babel/preset-env는 뭐지?

`@babel/preset-env`는 필요한 플러그인들을 프로젝트 지원 환경에 맞춰서 동적으로 결정해준다.  
즉, 함께 사용되어야하는 Babel 플러그인을 모아 둔 것이다.  
이를 **Babel 프리셋**이라고 부르며, Babel이 제공하는 공식 Babel 프리셋은 아래와 같다.

- @babel/preset-env
- @babel/preset-flow
- @babel/preset-react
- @babel/preset-typescript

### 3. npm script를 사용해 트랜스파일링 하기

```json
// package.json 파일에 build를 추가한다.
{
  "name": "es6-project",
  "version": "1.0.0",
  "scripts": {
    "build": "babel src/js -w -d dist/js"
  },
  "devDependencies": {
    "@babel/cli": "^7.7.0",
    "@babel/core": "^7.7.2",
    "@babel/preset-env": "^7.7.1"
  }
}
```

- `-w` : 타킷 폴더에 있는 모든 파일들의 변경을 감지해 자동으로 트랜스파일한다.(`--watch` 옵션의 축약형)
- `-d` : 트랜스파일링 된 결과물이 저장될 폴더를 지정한다(`--out-dir` 옵션의 축약형)

---

#### Reference

- https://poiemaweb.com/es6-babel-webpack-1
