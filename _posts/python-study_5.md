---
title: 혼자 공부하는 파이썬 - 숫자와 문자열의 다양한 함수
date: 2021-07-19
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 문자열의 format() 함수
- 대소문자 바꾸기 : upper()와 lower()
- 문자열 양옆의 공백 제거하기 : strip()
- 문자열의 구성 파악하기 : isOO()
- 문자열 찾기 : find()와 rfind()
- 문자열과 in 연산자
- 문자열 자르기 : split()

---

## 문자열의 format() 함수

`format()`함수는 문자열이 가지고 있는 함수 입니다.
다음과 같이 사용할 수 있습니다.

```
"{}".format(52)
"{} {} {}".format(52, 20)
"{} {} {} {} {}".format(30, 20 ,10 , 15 ,16)
```

이러한 형태로 앞쪽에 있는 문자열의 {} 기호가 `format()` 함수 괄호 안에 있는 매개 변수로 차례로 대치되면서 문자열이 되는 것 입니다.

#### 1. format() 함수로 숫자를 문자열로 변환하기

```python
a = "{}".format(10)
print(a) # 10
print(type(a)) # <class 'str'>
```

#### 2. format() 함수의 다양한 형태

```python
a = "{} 만원".format(10)
b = "오늘은 {}월 {}일 입니다".format(7,19)
c = "{} {} {}".format(3000, 4000, 5000)
d = "{} {} {}".format(1, "문자열", True)

print(a) # 10 만원
print(b) # 오늘은 7월 19일 입니다
print(c) # 3000 4000 5000
print(d) # 1 문자열 True
```

### 정수 출력의 다양한 형태

#### 1. 정수를 특정 칸에 출력하기

```python
# 정수
output_a = "{:d}".format(52) # {:d}는 int 자료형의 정수를 출력하겠다고 직접적으로 지정하는 것이다. 매개변수로 정수만 올 수 있다.

# 특정 칸에 출력하기
output_b = "{:5d}".format(52) # 5칸을 잡고 뒤에서 부터 52를 채운다.
output_c = "{:10d}".format(-52)

# 빈칸을 0으로 채우기
output_d = "{:05d}".format(52) # 5칸을 잡고 뒤에서부터 52라는 숫자를 넣은 후 앞의 빈 곳을 0으로 채운다.
output_e = "{:05d}".format(-52) # 부호가 있을 때는 맨 앞자리를 부호로 채우고 나머지 빈 곳을 0으로 채운다.

print('# 기본')
print(output_a)

print('# 특정 칸에 출력하기')
print(output_b)
print(output_c)

print('# 빈칸을 0으로 채우기')
print(output_d)
print(output_e)
```

실행 결과

```
# 기본
52
# 특정 칸에 출력하기
   52
       -52
# 빈칸을 0으로 채우기
00052
-0052
```

#### 2. 기호 붙여 출력하기

```python
output_a = "{:+d}".format(52)
output_b = "{:+d}".format(-52)
output_c = "{: d}".format(-52)
output_d = "{: d}".format(52)

print(output_a)
print(output_b)
print(output_c)
print(output_d)
```

실행 결과

```
+52
-52
-52
 52
```

#### 3. 조합해보기

```python
output_a = "{:+5d}".format(52)
output_b = "{:+5d}".format(-52)
output_c = "{:=+5d}".format(52)
output_d = "{:=+5d}".format(-52)
output_e = "{:+05d}".format(52)
output_f = "{:+05d}".format(-52)

print(output_a)
print(output_b)
print(output_c)
print(output_d)
print(output_e)
print(output_f)
```

실행 결과

```
  +52
  -52
+  52
-  52
+0052
-0052
```

### 부동 소수점 출력의 다양한 형태

#### 1. float 자료형의 기본

```python
output_a = "{:f}".format(52.273) # {:f}는 float 자료형을 출력하겠다고 직접적으로 지정하는 것이다. 매개변수로 float 자료형만 올 수 있다.
output_b = "{:15f}".format(52.273)
output_c = "{:+15f}".format(52.273)
output_d = "{:+015f}".format(52.273)

print(output_a)
print(output_b)
print(output_c)
print(output_d)
```

실행 결과

```
52.273000
      52.273000
     +52.273000
+0000052.273000#### 1. float 자료형의 기본
```

#### 2. 소수점 아래 자릿수 지정하기

```python
output_a = "{:15.3f}".format(52.273) #{.3f} : 소수점 아래 3번째 자릿수까지 보여준다.
output_b = "{:15.2f}".format(52.273)
output_c = "{:15.1f}".format(52.273)

print(output_a)
print(output_b)
print(output_c)
```

실행 결과

```
         52.273
          52.27
           52.3
```

자동으로 반올림이 일어나는 것을 확인 할 수 있습니다.

#### 3. 의미 없는 소수점 제거하기

```python
output_a = 52.0
output_b = "{:g}".format(ouput_a) # 의미 없는 0을 제거 하고 싶을 땐 {:g}를 사용한다.

print(output_a)
print(output_b)
```

실행 결과

```
52.0
52
```

### IndexError 살펴보기

{} 기호의 개수가 `format()` 함수의 매개변수 개수보다 많으면 `IndexError 예외`가 발생합니다.

```python
>>> "{} {}".format(1, 2, 3, 4) # {} 보다 매개변수 개수가 많을 때는 예외가 발생하지 않습니다. {} 개수만큼 적용되고 나머지 매개변수는 버려집니다.
'1 2'
>>> "{} {} {}".format(1, 2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: Replacement index 2 out of range for positional args tuple
```

---

## 대소문자 바꾸기 : upper()와 lower()

- `upper()` : 문자열의 알파벳을 대문자로 만든다.
- `lower()` : 문자열의 알파벳을 소문자로 만든다.

```python
>>> a = "Hello Python Programming...!"
>>> a.upper()
'HELLO PYTHON PROGRAMMING...!'
```

```python
>>> a = "Hello Python Programming...!"
>>> a.lower()
'hello python programming...!'
```

---

## 문자열 양옆의 공백 제거하기 : strip()

- `strip()` : 문자열 양옆의 공백을 제거한다.
- `rstrip()` : 문자열 오른쪽 공백을 제거한다.
- `lstrip()` : 문자열 왼쪽 공백을 제거한다.

```python
>>> input_a = """
...              안녕하세요
... 문자열의 함수를 알아봅시다.
... """
>>> print(input_a)

             안녕하세요
문자열의 함수를 알아봅시다.

>>> print(input_a.strip())
안녕하세요
문자열의 함수를 알아봅시다.
```

---

## 문자열의 구성 파악하기 : isOO()

문자열이 소문자로만 구성되어 있는지, 알파벳 또는 숫자로만 구성되어 있는지 등을 확인할 때는 is로 시작하는 이름의 함수를 사용합니다.

- `isalnum()` : 문자열이 알파벳 또는 숫자로만 구성되어 있는지 확인합니다.
- `isalpha()` : 문자열이 알파벳으로만 구성되어 있는지 확인합니다.
- `isdentifier()` : 문자열이 식별자로 사용할 수 있는 것인지 확인합니다.
- `isdecimal()` : 문자열이 정수 형태인지 확인합니다.
- `isdigit()` : 문자열이 숫자로 인식될 수 있는 것인지 확인합니다.
- `isspace()` : 문자열이 공백으로만 구성되어 있는지 확인합니다.
- `islower()` : 문자열이 소문자로만 구성되어 있는지 확인합니다.
- `isupper()` : 문자열이 대문자로만 구성되어 있는지 확인합니다.

```python
>>> print("TrainA10".isalnum())
True
>>> print("10".isalnum())
True
>>> print("TrainA10".isdigit())
False
```

True 또는 False를 출력합니다.

---

## 문자열 찾기 : find()와 rfind()

- `find()` : 왼쪽부터 찾아서 처음 등장하는 위치를 찾습니다.
- `rfind()` : 오른쪽부터 찾아서 처음 등장하는 위치를 찾습니다.

```python
>>> output_a = "안녕안녕하세요".find("안녕")
>>> print(output_a)
0

>>> output_b = "안녕안녕하세요".rfind("안녕")
>>> print(output_b)
2
```

```
0  1  2  3  4  5  6
안 녕 안 녕 하 세 요
```

처음 "안녕"은 0번째에 있는 것이고,  
두 번째 "안녕"은 2번째부터 등장해 저러한 결과가 나옵니다.

---

## 문자열 자르기 : split()

```python
>>> a = "10 20 30 40 50".split(" ")
>>> print(a)
['10', '20', '30', '40', '50']
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
