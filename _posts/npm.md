---
title: npm
date: 2019-06-05
tags:
  - Node.js
  - npm
keywords:
  - npm
---

- npm install --save-prod? npm install --save-dev?
- npm install 와 npm install -g의 차이

---

## npm install --save-prod? npm install --save-dev?

### 1. -P, --save-prod 플래그 사용

- 패키지를 설치하고 프로젝트의 `dependencies` 목록에 추가한다.
- 하지만 npm5부터는 이 플래그를 사용하지 않아도 dependecies에 항목을 추가할 수 있다.

### 2. -D, —save-dev 플래그 사용

- 패키지를 설치하고 프로젝트의 `devDependencies` 목록에 추가한다.

### 3. dependencies 와 devDependencies

- `dependencies` : express 패키지 처럼 실제 코드도 포함되며 앱 구동을 위해 필요한 의존성 파일들
- `devDependencies` : concurrently 패키지처럼 실제 코드에 포함되지 않으며 개발 단계에만 필요한 의존성 파일들

### 4. 굳이 사용하는 이유가 뭘까?

플래그를 사용해 dependencies 와 devDependencies 로 의존성 목록을 구분하면 “이건 개발용, 이건 실제 서비스용” 으로 구분하기 쉬워진다는 면에서 개발자들에게 필요한 기능이라고 볼 수 있다.

---

## npm install 와 npm install -g 의 차이

- `npm install (패키지명)` : 프로젝트 폴더에 패키지 설치
- `npm install -g (패키지명)` : 시스템 폴더에 패키지 설치
  (win10 기준으로는 `(사용자명)\AppData\Roaming\npm\node_modules` )
  시스템의 node_modules 폴더 경로는 `npm root -g` 를 통해 찾을 수 있다.

---

#### Reference

- https://ko.javascript.info/
