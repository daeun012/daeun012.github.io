---
title: 혼자 공부하는 파이썬 - 범위와 while 반복문
date: 2021-07-21
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 범위란?
- for 반복문 : 범위와 함께 사용하기
- while 반복문

---

## 범위란?

리스트, 딕셔너리 외에 for 반복문과 함께 많이 사용되는 자료형입니다.

### 범위 자료형 살펴보기

```python
range(A) # A는 숫자입니다 => 0부터 A-1까지의 정수로 범위를 만듭니다.
range(A,B) # A,B는 숫자입니다 =>  A부터 B-1까지의 정수로 범위를 만듭니다..
range(A,B,C) # A,B,C는 숫자입니다 => A부터 B-1까지의 정수로 범위를 만드는데, 앞뒤의 숫자가 C만큼의 차이를 가집니다.
```

```python
>>> a = range(5)
>>> a
range(0, 5)
>>> list(a) # list()함수를 사용해 범위 내부에 어떤 값이 들어 있는지 확인할 수 있습니다.
[0, 1, 2, 3, 4]
>>> list(range(5,10))
[5, 6, 7, 8, 9]
>>> list(range(0,10,2))
[0, 2, 4, 6, 8]
```

### Tpye Error 살펴보기

```python
>>> n=10
>>> a=range(0, n/2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'float' object cannot be interpreted as an integer
```

`range()` 함수의 매개변수로는 **반드시 정수**를 입력해야합니다.
`int()함수` 또는 `정수 나누기 연산자`를 사용해 다음과 같이 변경하면 에러가 발생하지 않습니다.

```python
# int() 함수 사용
>>> a = range(0, int(n/2))
>>> list(a)
[0, 1, 2, 3, 4]

# 정수 나누기 연산자 사용
>>> a = range(0, n//2)
>>> list(a)
[0, 1, 2, 3, 4]
```

---

## for 반복문 : 범위와 함께 사용하기

### for 반복문과 범위

```python
for i in range(5):
  print(i, "= 반복 변수")
print()
for i in range(5,10):
  print(i, "= 반복 변수")
print()
for i in range(0,10,2):
  print(i, "= 반복 변수")
```

▶ 실행결과

```
0 = 반복 변수
1 = 반복 변수
2 = 반복 변수
3 = 반복 변수
4 = 반복 변수

5 = 반복 변수
6 = 반복 변수
7 = 반복 변수
8 = 반복 변수
9 = 반복 변수

0 = 반복 변수
2 = 반복 변수
4 = 반복 변수
6 = 반복 변수
8 = 반복 변수
```

### 리스트와 범위를 조합해 사용하기

```python
array = [273, 32, 103, 57,52]

for i in range(len(array)):
  print("{}번째 반복 : {}".format(i, array[i]))
```

▶ 실행결과

```
0번째 반복 : 273
1번째 반복 : 32
2번째 반복 : 103
3번째 반복 : 57
4번째 반복 : 52
```

### 반대로 반복하기

#### 첫번째 방법

```python
for i in range(4, -1, -1):
  print("현재 반복 변수 : {}".format(i))
```

▶ 실행결과

```
현재 반복 변수 : 4
현재 반복 변수 : 3
현재 반복 변수 : 2
현재 반복 변수 : 1
현재 반복 변수 : 0
```

#### 두번째 방법

`reversed() `함수를 사용하는 방법

```python
for i in reversed(range(5)):
  print("현재 반복 변수 : {}".format(i))
```

▶ 실행결과

```
현재 반복 변수 : 4
현재 반복 변수 : 3
현재 반복 변수 : 2
현재 반복 변수 : 1
현재 반복 변수 : 0
```

---

## while 반복문

while 반복문의 기본적인 형태는 다음과 같습니다.
<불 표현식>이 참인 동안 문장을 계속 반복합니다.

```python
while 불 표현식:
  문장
```

### while 반복문 사용하기

```python
i = 0
while i < 5 :
  print("{}번째 반복입니다.".format(i))
  i+=1
```

▶ 실행결과

```
0번째 반복입니다.
1번째 반복입니다.
2번째 반복입니다.
3번째 반복입니다.
4번째 반복입니다.
```

### 상태를 기반으로 반복하기

```python
list_test = [1,2,1,2]
value=2

while value in list_test:
  list_test.remove(value)

print(list_test)
```

▶ 실행결과

```
[1, 1]
```

### 시간 기반으로 반복하기

시간 기반으로 반복하기 위해서는 유닉스 타임이라는 개념을 알아야 합니다.  
**유닉스 타임**이란 세계 표준시로 1970년 1월 1일 0시 0분 0초를 기준으로 몇 초가 지났는지를 정수로 나타낸 것을 말합니다.

```python
import time # 시간과 관련된 기능을 가져옵니다.

number = 0

target_tick = time.time() + 5
while time.time() < target_tick:
  number+=1

print("5초 동안 {}번 반복했습니다.".format(number))
```

▶ 실행결과

```
5초 동안 46790412번 반복했습니다.
```

### break 키워드 / continue 키워드

#### break 키워드

반복문을 벗어날 때 사용하는 키워드입니다.

```python
i = 0

while True :
  print("{}번째 반복문입니다.".format(i))
  i=i+1

  input_text = input("> 종료하시겠습니까?(y/n) : ")
  if input_text in ["Y","y"]:
    print("반복문을 종료합니다.")
    break
```

▶ 실행결과

```
0번째 반복문입니다.
> 종료하시겠습니까?(y/n) : n
1번째 반복문입니다.
> 종료하시겠습니까?(y/n) : n
2번째 반복문입니다.
> 종료하시겠습니까?(y/n) : n
3번째 반복문입니다.
> 종료하시겠습니까?(y/n) : y
반복문을 종료합니다.
```

#### continue 키워드

현재 반복을 생략하고, 다음 반복으로 넘어갈 때 사용하는 키워드 입니다.

```python
numbers = [5, 15, 6, 33, 556]

for number in numbers :
  # number가 10보다 작으면 다음 반복으로 넘어갑니다.
  if number < 10:
    continue
  print(number)
```

▶ 실행결과

```
15
33
556
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
