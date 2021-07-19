---
title: 혼자 공부하는 파이썬 - if~else와 elif 구문
date: 2021-07-19
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- if~else 조건문 사용하기
- elif 구문
- False로 변환되는 값
- pass 키워드

---

## if~else 조건문 사용하기

if~else 조건문의 구조는 다음과 같습니다.

```
if 조건 :
    조건이 참일 때 실행할 문장
else :
    조건이 거짓일 때 실행할 문장
```

#### if~else 조건문으로 짝수와 홀수 구분하기

```python
number = input("정수 입력>")
number = int(number)

if number % 2 == 0 :
  print("짝수입니다")
else :
  print("홀수입니다.")
```

---

## elif 구문

조건이 세 개 이상일 때 사용하는 구문입니다.  
elif 구문의 구조는 다음과 같습니다.

```
if 조건A :
    조건A가 참일 때 실행할 문장
elif 조건B :
    조건B가 참일 때 실행할 문장
elif 조건C :
    조건C가 참일 때 실행할 문장
...
else :
    모든 조건이 거짓일 때 문장
```

#### 계절구하기

```python
import datetime

now = datetime.datetime.now()

if 3 <= now.month <= 5 :
  print("이번 달은 {}월로 봄입니다!".format(now.month))
elif 6 <= now.month <= 8 :
  print("이번 달은 {}월로 여름입니다!".format(now.month))
elif 9 <= now.month <= 11 :
  print("이번 달은 {}월로 가을입니다!".format(now.month))
else :
  print("이번 달은 {}월로 겨울입니다!".format(now.month))
```

---

## False로 변환되는 값

if 조건문의 매개변수에 불이 아닌 다른 값이 올 때는 자동으로 이를 불로 변환해 처리합니다.
예제를 통해 이를 살펴보겠습니다.

#### False로 변환되는 값

```python
if 0 :
    print("0은 True로 변환됩니다.")
else :
    print("0은 False로 변환됩니다.")

if "" :
    print("빈 문자열은 True로 변환됩니다.")
else :
    print("빈 문자열은 False로 변환됩니다.")
```

실행결과
```
0은 False로 변환됩니다.
빈 문자열은 False로 변환됩니다.
```

---

## pass 키워드

#### 나중에 구현하려고 비워둔 구문

```python
number = input("정수 입력>")
number = int(number)

if number > 0 :
  # 양수일 때 : 아직 미구현 상태
else :
  # 음수일 때 : 아직 미구현 상태
```

실행결과
```
IndentationError: expected an indented block
```

오류가 발생합니다. 그렇기 때문에 if 구문 사이에는 어떤 내용이라도 넣어 줘야 합니다.  
그래서 파이썬은 이를 해결하기 위해 `pass`라는 키워드를 제공합니다.

#### pass 키워드를 사용한 미구현 부분 입력

```python
number = input("정수 입력>")
number = int(number)

if number > 0 :
  # 양수일 때 : 아직 미구현 상태
  pass
else :
  # 음수일 때 : 아직 미구현 상태
  pass
```

코드를 살펴보던 도중 `pass` 키워드를 만나면  
"진짜로 아무것도 안함" 또는 "곧 개발하겠음"이라는 의미로 생각하면 됩니다.

## raise NotImplementedError

`pass` 키워드를 입력해 놨어도 내일이면 잊어버리는 경우가 많습니다.
그래서 `raise` 키워드와 미구현 상태를 표현하는 `NotImplementedError`을 조합해  
`raise NotImplementedError`를 사용하면 "아직 구현하지 않은 부분이에요!"라는 오류를 강제로 발생시킬 수 있습니다.

```python
number = input("정수 입력>")
number = int(number)

if number > 0 :
  # 양수일 때 : 아직 미구현 상태
  raise NotImplementedError
else :
  # 음수일 때 : 아직 미구현 상태
  raise NotImplementedError
```

실행결과
```
Traceback (most recent call last):
  File "c:\Users\다은\Desktop\test\format3.py", line 6, in <module>
    raise NotImplementedError
NotImplementedError
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
