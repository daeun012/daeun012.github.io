---
title: React LifeCycle(리액트 생명주기)
date: 2019-05-30
tags:
  - React
keywords:
  - react
  - 리액트생명주기
  - componentlifecycle
---

- 컴포넌트 초기 생성(Mount)
- 컴포넌트 업데이트
- 컴포넌트 제거(마운트 해제)

---

## 컴포넌트 초기 생성(Mount)

컴포넌트가 브라우저에 나타나기 전, 후에 호출되는 API  
아래의 순서대로 호출 된다.

- `constructor()`
- `static getDerivedStateFromProps()`
- `render()`
- `componentDidMount()`

### 1. constructor( )

컴포넌트 생성자 함수, 컴포넌트가 새로 만들어질 때마다 이 함수가 호출된다.

### 2. static getDerivedStateFromProps( )

```javascript
static getDerivedStateFromProps(prosp,state) {
  // 여기서는 setState 를 하는 것이 아니라
  // 특정 props 가 바뀔 때 설정하고 설정하고 싶은 state 값을 리턴하는  형태로 사용된다.
  /*
  if (props.value !== state.value) {
    return { value: props.value };
  }
  return null; // null 을 리턴하면 따로 업데이트 할 것은 없다라는 의미
  */
}
```

최초 마운트 시와 업데이트 시 모두에서 render 메서드를 호출하기 직전에 호출된다.

- 부모 컴포넌트가 다시 렌더링을 발생 시켰을 때에만 실행된다.
- 해당 컴포넌트 내에서 지역적인 `setState()`가 발생한 경우에는 실행되지 않는다.

### 3. componentDidMount( )

컴포넌트가 마운트된 직후, 즉 컴포넌트가 화면에 나타나게 됐을 때 호출된다. 외부에서 데이터를 불러오기 위해, 네트워크 요청을 보내기 적절한 위치이다.

- 외부 라이브러리 연동 : D3,
- 컴포넌트에서 필요한 데이터 요청 : Ajax, GraphQL, etc
- DOM에 관련된 작업 : 스크롤 설정, 크기 읽어오기 등

---

## 컴포넌트 업데이트

props 또는 state가 변경되어 컴포넌트가 다시 렌더링될 때, 아래의 순서대로 호출된다.

- `static getDerivedStateFromProps()`
- `shouldComponentUpdate()`
- `render()`
- `getSnapshotBeforeUpdate()`
- `componentDidUpdate()`

### 1. shouldComponentUpdate( )

```javascript
shouldComponentUpdate(nextProps, nextState) {
  // return false 하면 render()를 발생시키지 않는다.
  // return this.props.checked !== nextProps.checked
  return true;
}
```

이 메서드는 오직 성능 최적화만을 위한 것이다.

- `this.props`와 `nextProps`, 그리고 `this.state`와 `nextState`를 비교해 사용한다.

### 2. getSnapshotBeforeUpdate( )

```javascript
getSnapshotBeforeUpdate(prevProps, prevState);
```

가장 마지막으로 렌더링된 결과가 DOM 등에 반영되었을 때에 호출된다. 이 생명주기 메서드가 반환하는 값은 `componentDidUpdate()`에 인자로 전달된다.

### 3. componentDidUpdate( )

```javascript
componentDidUpdate(prevProps, prevState, snapshot);
```

이 메서드는 갱신이 일어난 직후에 호출된다.

- 이전과 현재의 props를 비교해 네트워크 요청을 보내는 작업이 대부분 이 메서드에서 이루어진다.

```javascript
componentDidUpdate(prevProps) {
  // 전형적인 사용 사례 (props 비교)
  if (this.props.userID !== prevProps.userID) {
    this.fetchData(this.props.userID);
  }
}
```

---

## 컴포넌트 제거(마운트 해제)

- `componentWillUnmount()`

### 1. componentWillUnmount( )

```javascript
componentWillUnmount() {
  // 이벤트, setTimeout, 외부 라이브러리 인스턴스 제거
}
```

컴포넌트가 마운트 해제되어 제거되기 직전에 호출된다.

- `componentDidMount()` 내에서 생성된 구독 해제

---

#### Reference

- https://velopert.com/1130
- https://ko.reactjs.org/
