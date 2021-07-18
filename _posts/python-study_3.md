---
title: 혼자 공부하는 파이썬 - 숫자
date: 2021-07-17
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 숫자의 종류
- 숫자 연산자

---

## 숫자의 종류

파이썬의 숫자에는 두 가지 종류가 있다.

- 정수(integer) : 소수점이 없는 숫자 0, 1, 3, 456 ...
- 실수(float) : 소수점이 있는 숫자 0.2, 52.74, -1.2 ...

```{.python}
>>> print(type(273))
<class 'int'>
>>> print(type(276.52))
<class 'float'>
```

---

## 숫자 연산자

### 1. 사칙 연산자 : +, -, \*, /

### 2. 정수 나누기 연산자 : //

숫자를 나누고 소수점 이하의 자릿수를 떼어 버린 후, 정수 부분만 남기는 연산자 이다.

```{.python}
>>> print("3 / 2 =", 3/2)
3 / 2 = 1.5
>>> print("3 // 2 =", 3//2)
3 // 2 = 1
```

### 3. 나머지 연산자 : %

```{.python}
>>>  print("5 % 2 =", 5%2)
5 % 2 = 1
```

### 4. 제곱 연산자 : \*\*

```{.python}
>>> print("5 ** 2 =", 5**2)
5 ** 2 = 25
>>> print("5 ** 3 =", 5**3)
5 ** 3 = 125
>>> print("5 ** 4 =", 5**4)
5 ** 4 = 625
```

### TypeError 살펴보기

```{.python}
>>> print("안녕"+1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

문자열과 숫자를 +연산자로 연결할 수 없다.  
문자열은 문자열끼리
숫자는 숫자끼리
연산이 가능하다.

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
