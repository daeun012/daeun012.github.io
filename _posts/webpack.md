---
title: Webpack
date: 2020-08-11
tags:
  - JavaScript
  - ES6
keywords:
  - webpack
  - babel
  - es6
  - javascript
---

- bundler란?
- Webpack이란?
- Babel과 Webpack 함께 사용하기

---

## bundler란?

웹 사이트를 만들다보면 js, css, img 등 수 많은 파일들이 생겨난다. 웹 사이트 로딩 시 많은 파일들이 다운되어지고, 서버와의 접속이 많아져 애플리케이션의 로딩이 느려진다.

각각의 서로 다른 패키지들이 서로 같은 이름을 가진 변수, 함수를 사용할 수 있다.
이는 예상치 못한 충돌을 발생시킨다.

이를 해결하기 위해 등장한 도구들을 `bundler`라 한다.

bundle? '묶는다' 라는 뜻이다.

### 대표적인 bundler

- webpack
- broserify
- parcel

---

## Webpack이란?

의존 관계에 있는 모듈들을 하나의 자바스크립트로 번들링하는 모듈 번들러

- 이를 사용하면 의존 모듈이 하나의 파일로 번들링되므로 별도의 모듈 로더가 필요 없다.
- 다수의 자바스크립트 파일을 하나의 파일로 번들링하므로 html 파일에서 script 태그로 다수의 자바스크립트 파일을 로드해야 하는 번거로움도 사라진다.

### Webpack 설치

```bash
# Webpack V4는 webpack-cli를 요구한다
$ npm install --save-dev webpack webpack-cli
```

---

## Babel과 Webpack 함께 사용하기

```bash
# babel-loader 설치
$ npm install --save-dev babel-loader
```

### webpack.config.js 파일 작성하기

`webpack.config.js`은 Webpack이 실행될 때 참조하는 설정 파일이다.  
프로젝트 루트에 `webpack.config.js` 파일을 생성하고 아래와 같이 작성한다.

```javascript
// Webpack이 실행될 때 참조하는 설정 파일
const path = require('path');

module.exports = {
  // entry file
  entry: './src/js/main.js',

  // 컴파일 + 번들링된 js 파일이 저장될 경로와 이름 지정
  output: {
    path: path.resolve(__dirname, 'dist/js'),
    filename: 'bundle.js',
  },

  module: {
    rules: [
      {
        test: /\.js$/,
        include: [path.resolve(__dirname, 'src/js')],
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env'],
          },
        },
      },
    ],
  },
};
```

---

#### Reference

- https://poiemaweb.com/es6-babel-webpack-2
