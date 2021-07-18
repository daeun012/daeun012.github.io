---
title: 혼자 공부하는 파이썬 - Python 용어 정리
date: 2021-07-16
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 키워드란?
- 식별자란?
- 주석
- 출력 : print()

---

## 키워드란?

특별한 의미가 부여된 단어  
파이썬이 만들어질 때 이미 사용하겠다고 예약해 놓은 것이다.

### 1. 왜 알아야할까?

변수나 함수의 이름을 정할 때 키워드를 사용하면 안 되기 때문에, 알아두는 것이 좋다.

### 2. 파이썬의 키워드 확인해보기

```{.python}
>>> import keyword
>>> print(keyword.kwlist)
```

다음과 같은 키워드들을 확인할 수 있다.

＊ 파이썬은 대문자와 소문자를 구분한다.

```{.python}
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

---

## 식별자란?

프로그래밍 언어에서 이름을 붙일 때 사용하는 단어

### 1. 식별자의 규칙

- 키워드를 사용하면 안된다.
- 특수 문자는 언더 바(\_)만 허용된다.
- 숫자로 시작하면 안된다.
- 공백을 포함할 수 없다.

### 2. 파이썬의 표기법 - 스네이크 케이스와 캐멀 케이스

파이썬은 대표적으로 **스네이크 케이스**와 **캐멀 케이스** 표기법을 사용한다.

#### 스네이크 케이스

단어 사이에 언더 바(\_) 기호를 붙여 표기한다.  
 ex) item_list, login_status, rotate_angle

#### 캐멀 케이스

단어들의 첫 글자를 대문자로 만들어 표기한다.  
 ex) ItemList, LoginStatus, RotateAngle

---

## 주석

```{.python}
>>> # 앞에 샵 기호를 붙여 주석 처리를 합니다.
>>> print("Hello Python!") # 문자열을 출력합니다.
```

---

## 출력 : print()

Python 에서의 출력은 print() 함수를 사용하는 것이다.

```{.python}
>>> print("Hello Python!")
Hello Python!
>>> print("Hello Python!",52,57)
Hello Python! 52 57
>>> print()

>>>
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
