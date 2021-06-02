---
title: pakage.json 종속성을 최신 버전으로 업데이트하기
date: 2020-08-13
tags:
  - npm
  - Node.js
keywords:
  - update
  - npm
  - node.js
---

npm에서 dependency를 최신 버전으로 업데이트 하려면 하나씩 따로 업데이트해줘야 하는데.
그냥 한번에 업데이트 하는 방법은 없을까?

## npm-check-updates 를 이용한 업데이트

### 1. npm-check-updates 전역 설치

```bash
$ npm install -g npm-check-updates

```

### 2. npm-check-updates 실행하기

```bash
$ ncu -u

// 완료 되었으면 아래 명령어를 실행한다.

$ npm install
```

### 3. 그러나 주의하자

모든 의존성을 한번에 업데이트 하는 것은 프로젝트 관점에서 굉장히 큰 리스크를 가지고 있는 작업이다.
하지만 여러가지 보일러플레이트를 github에서 관리해야할 때에는 분명 일괄 업데이트 기능도 필요하기 마련이다.
강제로 최신버전으로 업데이트된 의존성들 사이의 호환성은 보장되지 않기 때문에 주의해서 사용하자

---

#### Reference

https://ahribori.com/article/5a7996097eaff3172844ddb9
