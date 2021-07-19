---
title: 혼자 공부하는 파이썬 - 변수와 입력
date: 2021-07-18
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 변수 선언과 할당
- 복합 대입 연산자
- 사용자 입력 : input()
- 문자열을 숫자로 바꾸기
- 숫자를 문자열로 바꾸기

---

## 변수 선언과 할당

파이썬은 변수의 자료형에 대해 미리 선언해 주지 않아도 된다.  
`pi = 3.14 ` 이렇게 간단하게 변수를 만들 수 있다!

```python
>>> pi = 3.1415926
>>> pi+2
5.1415926
```

---

## 복합 대입 연산자

+= : 숫자 덧셈 후 대입  
-= : 숫자 뺄셈 후 대입  
\*= : 숫자 곱셈 후 대입  
/= : 숫자 나눗셈 후 대입  
%= : 수자의 나머지를 구한 후 대입  
\*\*= : 숫자 제곱 후 대입

```python
>>> number = 100
>>> number += 10
>>> number += 20
>>> print('number:', number)
number: 130
```

숫자 뿐만 아니라 문자열에도 사용할 수 있다.

```python
>>> string = "안녕하세요"
>>> string += "!"
>>> string += "!"
>>> print('string:', string)
string: 안녕하세요!!
```

---

## 사용자 입력 : input()

#### 1. `input()` 함수로 사용자로부터의 입력을 받아 낼 수 있다.

```python
>>> input("인사말을 입력하세요 >>")
인사말을 입력하세요 >> 안녕하세요!
' 안녕하세요!'
```

#### 2. 사용자가 입력한 내용은 `input()` 함수의 결과로 나온다.

이 값은 다른 변수에 대입해 사용 할 수 있다.

```python
>>> string = input("인사말을 입력하세요 >>")
인사말을 입력하세요 >> 안녕하세요!!!!!!!
>>> print(string)
 안녕하세요!!!!!!!
```

#### 3. `input()` 함수의 결과의 자료형은 무조건 str! 문자열이다.

```python
>>> string = input("인사말을 입력하세요 >>")
인사말을 입력하세요 >> 안녕하세요!!!!!!!
>>> print(string)
 안녕하세요!!!!!!!
>>> print(type(string))
<class 'str'>


>>> number = input("숫자를 입력하세요 >>")
숫자를 입력하세요 >>123456
>>> print(number)
123456
>>> print(tpye(number))
<class 'str'>
```

---

## 문자열을 숫자로 바꾸기

input() 함수의 입력 자료형은 항상 문자열이기 때문에 입력받은 문자열을 수자로 변환해야 숫자 연산에 활용할 수 있다.
이를 **캐스트(cast)** 라고 부른다.

- int() : 문자열을 int 자료형으로 변환
- float() : 문자열을 float 자료형으로 변환

```python
string_a=input("입력A> ")
int_a=int(string_a)

string_b=input("입력B> ")
int_b=int(string_b)

print("문자열 자료:", string_a+string_b)
print("숫자 자료:", int_a+int_b)
```

▶ 실행결과
```python
입력A> 273
입력B> 52
문자열 자료: 27352
숫자 자료: 325
```

### ValueError 살펴보기

자료형을 변환할 때 **변환할 수 없는 것**을 변환하려 하면 `ValueError` 예외가 발생한다.  
이러한 예외가 발생하는 경우는 두 가지가 있다.

#### 1. 숫자가 아닌 것을 숫자로 변환하려 할 때

```python
int("안녕하세요")
float("반갑습니다")
```

이와 같은 오류를 볼 수 있다.

```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '안녕하세요'
```

#### 2. 소수점이 있는 숫자 형식의 문자열을 int() 함수로 변환하려고 할 때

```python
int("3.145")
```

이와 같은 오류를 볼 수 있다.

```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '3.145'
```

---

## 숫자를 문자열로 바꾸기

`str()` 함수를 사용해 숫자를 문자열로 변환할 수 있다.

```python
output_a = str(52)
output_b = str(52.273)
print(type(output_a), output_a)
print(type(output_b), output_b)
```

▶ 실행결과
```python
<class 'str'> 52
<class 'str'> 52.273
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
