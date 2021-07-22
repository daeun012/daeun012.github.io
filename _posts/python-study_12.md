---
title: 혼자 공부하는 파이썬 - 함수 만들기
date: 2021-07-22
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 함수의 기본
- 가변 매개변수
- 기본 매개변수
- 키워드 매개변수

---

## 함수의 기본

함수를 생성하는 기본 형태는 다음과 같습니다.

```python
def 함수 이름():
    문장
```

### 기본적인 함수

```python
def print_3_times():
    print("안녕하세요")
    print("안녕하세요")
    print("안녕하세요")
print_3_times()

# 실행결과
안녕하세요
안녕하세요
안녕하세요
```

### 매개변수의 기본

```python
def print_3_times(value,n):
    for i in range(n):
        print(value)
print_3_times("안녕하세요",3)

# 실행결과
안녕하세요
안녕하세요
안녕하세요
```

### TypeError 살펴보기

함수를 호출할 때 매개변수를 넣지 않거나 더 많이 넣는다면 어떻게 될까?

#### 1. 매개변수를 넣지 않았을 때

```python
def print_3_times(value,n):
    for i in range(n):
        print(value)
print_3_times("안녕하세요")
```

```python
Traceback (most recent call last):
  File "c:\Users\다은\Desktop\test\format3.py", line 4, in <module>
    print_3_times("안녕하세요")
TypeError: print_3_times() missing 1 required positional argument: 'n'
```

#### 2. 매개변수를 더 넣었을 때

```python
def print_3_times(value,n):
    for i in range(n):
        print(value)
print_3_times("안녕하세요",2,13)
```

```python
Traceback (most recent call last):
  File "c:\Users\다은\Desktop\test\format3.py", line 5, in <module>
    print_3_times("안녕하세요",2,13)
TypeError: print_3_times() takes 2 positional arguments but 3 were given
```

코드를 실행하면 다음과 같이 오류를 출력합니다.  
따라서 함수를 호출할 때는 **함수를 선언할 때와 같은 개수**의 변수를 입력해야 합니다.

---

## 가변 매개변수

앞서 살펴본 함수는 함수를 선언할 때 매개변수와 함수를 호출할 때의 매개변수가 같아야 했습니다.  
하지만 우리가 자주 사용해 왔던 `print()` 함수는 매개변수를 윈하는 만큼 입력할 수 있습니다. 이와 같이 매개변수를 원하는 만큼 받을 수 있는 함수를 **가변 매개변수**라고 합니다.

### 가변 매개변수의 제약

가변 매개변수를 사용할 때는 다음과 같은 제약이 있습니다.

- 가변 매개변수 뒤에는 일반 매개변수가 올 수 없습니다.
- 가변 매개변수는 하나만 사용할 수 있습니다.

### 가변 매개변수 예제로 살펴보기

```python
def print_n_times(n, *values):
    for i in range(n):
        for value in values:
            print(value)
        print()
print_n_times(3,"안녕","즐거운","하루")
```

▶ 실행결과

```
안녕
즐거운
하루

안녕
즐거운
하루

안녕
즐거운
하루
```

---

## 기본 매개변수

print() 함수의 자동 완성 기능으로 나오는 설명입니다.

```
print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```

가장 앞에있는 value가 바로 **가변 매개변수**입니다.
앞에서 설명했다시피 가변 매개변수 뒤에는 일반 매개변수가 올 수 없다고 했습니다. 하지만 `매개변수 ="값"` 형태로 되어 있는 매개변수를 확인할 수 있습니다.  
이는 일반 매개변수가 아닌 **기본 매개변수**라고 부릅니다. 매개변수를 입력하지 않았을 경우 매개변수에 들어가는 기본값이 됩니다.

### 기본 매개변수의 제약

- 기본 매개변수 뒤에는 일반 매개변수가 올 수 없습니다.

### 기본 매개변수 예제로 살펴보기

```python
def print_n_times(value, n=2):
    for i  in range(n):
        print(value)
print_n_times("안녕하세요")
```

---

## 키워드 매개변수

매개변수 이름을 지정해서 입력하는 매개변수를 **키워드 매개변수**라고 합니다.

### 키워드 매개변수 예제로 살펴보기

#### 키워드 매개변수

```python
def print_n_times(*values, n=2):
    for i in range(n):
        for value in values:
            print(value)
        print()
print_n_times("안녕하요","즐거운","하루", n=3)

```

▶ 실행결과

```
안녕하요
즐거운
하루

안녕하요
즐거운
하루

안녕하요
즐거운
하루
```

#### 기본 매개변수 중 필요한 값만 입력하기

```python

def test(a, b=10, c=100):
    print(a+b+c)

test(10,20,30)
test(a=10, b=100, c=200)
test(c=10, a=100, b=200)
test(10, c=200)
```

▶ 실행결과

```
60
310
310
220
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
