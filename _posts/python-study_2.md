---
title: 혼자 공부하는 파이썬 - 자료형과 문자열
date: 2021-07-16
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 자료형 확인하기
- 문자열 연산자
- 문자열의 길이 구하기

---

## 자료형 확인하기

파이썬에서 자료의 형식을 확인할 때는 `type()` 함수를 사용한다.

```python
>>> print(type("안녕하세요"))
<class 'str'>
>>> print(type(2763))
<class 'int'>
```

---

## 문자열 연산자

프로그래밍 언어에서 이름을 붙일 때 사용하는 단어

### 1. 문자열 연결 연산자 : +

두 문자열을 연결해 새로운 문자열을 만든다

```python
>>> print("안녕" +"하세요")
안녕하세요
>>> print("안녕하세요" +"!")
안녕하세요!
```

문자열과 숫자의 연결은 불가능하다.

```python
>>> print("안녕" + 1)
```

### 2. 문자열 반복 연산자 : \*

문자열을 숫자와 \* 연산자로 연결하면 문자열을 반복할 수 있다.

```python
>>> print("안녕" *3)
안녕안녕안녕
```

### 3. 문자열 선택 연산자(인덱싱) : []

문자열 내부의 문자 하나를 선택하는 연산자이다.

```python
>>> print("안녕하세요"[0])
안
>>> print("안녕하세요"[1])
녕
>>> print("안녕하세요"[2])
하
>>> print("안녕하세요"[3])
세
>>> print("안녕하세요"[-1])
요
>>> print("안녕하세요"[-2])
세
```

### 4. 문자열 범위 선택 연산자(슬라이싱) : [:]

문자열의 특정 범위를 선택할 때 사용하는 연산자

```python
>>> print("안녕하세요"[1:4])
녕하세
>>> print("안녕하세요"[0:2])
안녕
>>> print("안녕하세요"[1:3])
녕하
>>> print("안녕하세요"[1:])
녕하세요
>>> print("안녕하세요"[:3])
안녕하
```

---

## 문자열의 길이 구하기

문자열의 길이를 구할 때는 `len()` 함수를 사용한다.

```python
>>> print(len("Hello Python!"))
13
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)