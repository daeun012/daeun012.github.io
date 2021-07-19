---
title: 혼자 공부하는 파이썬 - 불 자료형과 if 조건문
date: 2021-07-19
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 불 연산하기 : 논리 연산자
- if 조건문 사용하기
- 날짜/시간 활용하기
- 컴퓨터의 조건 - if 조건문으로 짝수와 홀수 구분해보기

---

## 불 연산하기 : 논리 연산자

python에는 논리 연산자를 not, and, or 로 나타냅니다.

### not 연산자

`not 연산자`는 피연산자가 하나인 `단항 연산자` 입니다.

```python
>>> print(not True)
False
>>> print(not False)
True
>>>
```

#### not 연산자 조합하기

```python
>>> x = 10
>>> under_20 = x < 20
>>> print(under_20)
True
>>> print(not under_20)
False
>>>
```

### and 연산자와 or 연산자

```python
>>> print (True and True)
True
>>> print (True and False)
False
>>> print (False and False)
False
>>> print (True or True)
True
>>> print (True or False)
True
>>> print (False or False)
False
```

---

## if 조건문 사용하기

if 조건문의 구조는 다음과 같습니다.

```
if 조건 :  -> if 조건문 뒤에는 반드시 클론(:)을 붙여주어야 한다.
    문장
    문장
```

#### 조건문의 기본 사용

```python
number = input("정수 입력>")
number = int(number)

if number > 0:
    print("양수입니다.")

if number < 0:
    print("음수입니다.")

if number == 0 :
    print("0입니다.")
```

▶ 실행결과

```
정수 입력>273
양수입니다.

```

```

정수 입력>0
0입니다.

```

```

정수 입력>-52
음수입니다.

```

---

## 날짜/시간 활용하기

#### 날짜/시간 출력하기

```python
import datetime # 날짜/시간과 관련된 기능 가져옵니다.

now = datetime.datetime.now() # 현재 날짜/시간을 구합니다.

print(now.year, "년") # 2021 년
print(now.month, "월") # 7 월
print(now.day, "일") # 19 일
print(now.hour, "시") # 13 시
print(now.minute, "분") # 41 분
print(now.second, "초") # 39 초
```

#### 날짜/시간 한 줄로 출력하기

```python
import datetime # 날짜/시간과 관련된 기능 가져옵니다.

now = datetime.datetime.now()

print("{}년 {}월 {}일 {}시 {}분 {}초".format(
  now.year,
  now.month,
  now.day,
  now.hour,
  now.minute,
  now.second
  ))
```

▶ 실행결과

```
2021년 7월 19일 13시 44분 52초
```

#### 오전과 오후를 구분하는 프로그램

```python
import datetime

now = datetime.datetime.now()

if now.hour < 12 :
  print("현재 시각은 {}시로 오전입니다!".format(now.hour))
if now.hour >= 12 :
  print("현재 시각은 {}시로 오후입니다!".format(now.hour))
```

▶ 실행결과

```
현재 시각은 13시로 오후입니다!

```

#### 계절을 구분하는 프로그램

```python
import datetime

now = datetime.datetime.now()

if 3 <= now.month <= 5 :
  print("이번 달은 {}월로 봄입니다!".format(now.month))
if 6 <= now.month <= 8 :
  print("이번 달은 {}월로 여름입니다!".format(now.month))
if 9 <= now.month <= 11 :
  print("이번 달은 {}월로 가을입니다!".format(now.month))
if now.month == 12 or 1 <= now.month <= 2 :
  print("이번 달은 {}월로 겨울입니다!".format(now.month))
```

▶ 실행결과

```
이번 달은 7월로 여름입니다!'
```

---

## 컴퓨터의 조건 - if 조건문으로 짝수와 홀수 구분해보기

#### 끝자리로 짝수와 홀수 구분

```python
number = input("정수 입력>")
last_character = number[-1]
last_character = int(last_character)

if last_character == 0 \
    or last_character == 2 \
    or last_character == 4 \
    or last_character == 6 \
    or last_character == 8 :
    print("짝수입니다")

if last_character == 1 \
    or last_character == 3 \
    or last_character == 5 \
    or last_character == 7 \
    or last_character == 9 :
    print("짝수입니다")
```

파이썬에서 줄이 너무 길어질 때는 \ 기호를 입력하고 줄바꿈해서 코드를 입력합니다.

#### in 문자열 연산자를 활용해 짝수와 홀수 구분

```python
number = input("정수 입력>")
last_character = number[-1]

if last_character in "02468":
    print("짝수입니다.")
if last_character in "13579":
    print("홀수입니다.")
```

#### 나머지 연산자를 활용해서 짝수와 홀수 구분

```python
number = input("정수 입력>")
number = int(number)

if number % 2 == 0 :
    print("짝수입니다.")
if number % 2 == 1 :
    print("홀수입니다.")
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
