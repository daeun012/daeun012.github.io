---
title: 혼자 공부하는 파이썬 - 리스트와 반복문
date: 2021-07-20
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 리스트란?
- 리스트 연산자 : 연결(+), 반복(\*), len()
- 리스트에 요소 추가하기 : append(), insert(), extend()
- 리스트에 요소 제거하기 : del, pop(), remove(), clear()
- 리스트 내부에 있는지 확인하기 : in/not in 연산자
- for 반복문 : 리스트와 함께 사용하기

---

## 리스트란?

파이썬에서 리스트의 의미는 **여러가지 자료를 저장할 수 있는 자료**입니다.

### 리스트 선언하기

리스트는 대괄호[ ] 내부에 여러 종류의 자료를 넣어 선언합니다.
이때 대괄호[ ] 내부에 넣는 자료를 `요소(element)`라고 부릅니다.

```python
>>> list_a  = [273, 32, "문자열", True, False]  # 리스트는 여러 자료형으로 구성할 수 있습니다.
>>> print(list_a)
[273, 32, '문자열', True, False]
```

### 특정 요소에 접근하고 변경하기

list_a[0] <- 대괄호[ ] 안에 들어간 숫자를 `인덱스`라고 부릅니다.

```python
>>> list_a  = [273, 32, "문자열", True, False]
>>> list_a[0]
273
>>> list_a[1]
32
>>> list_a[2]
'문자열'
>>> list_a[1:3] # 1번째 글자부터 3번째 글자를 선택하는 것이 아니라 그 앞에 숫자, 2번째 글자까지 선택합니다.
[32, '문자열']
>>> list_a[0] = "변경" # 다음과 같이 요소를 변경할 수 있습니다.
>>> list_a
['변경', 32, '문자열', True, False]
```

위와 같은 일반적인 사용법 외에도 다양한 방법들을 살펴보려합니다.

#### 대괄호 안에 음수를 넣어 뒤에서부터 요소를 선택할 수 있습니다.

```python
>>> list_a  = [273, 32, "문자열", True, False]
>>> list_a[-1]
False
>>> list_a[-2]
True
>>> list_a[-3]
'문자열'
```

#### 리스트 접근 연산자를 이중으로 사용할 수 있습니다.

```python
>>> list_a  = [273, 32, "문자열", True, False]
>>> list_a[2]
'문자열'
>>> list_a[2][1] # 문자열에서 1번째를 가져와 출력합니다.
'자'
```

#### 리스트 안에 리스트를 사용할 수 있습니다.

```python
>>> list_a =[[1,2,3],[5,6,7],[8,9,10]]
>>> list_a[1]
[5, 6, 7]
>>> list_a[1][1]
6
```

### 리스트에서의 IndexError 살펴보기

리스트의 길이를 넘는 인덱스로 요소에 접근하려고 할 때 발생합니다.

```python
>>> list_a =[1,2,3,4]
>>> list_a[5]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

---

## 리스트 연산자 : 연결(+), 반복(\*), len()

#### 리스트 연산자

```python
list_a = [1,2,3]
list_b = [5,6,7]

print("#리스트")
print("list_a = ", list_a)
print("list_b = ", list_b)
print()

print("# 리스트 기본 연산자")
print("list_a + list_b = ", list_a + list_b)
print("list_a * 3 = ", list_a * 3)
print()

print("# 길이 구하기")
print("len(list_a) = ", len(list_a))
```

▶ 실행결과

```
#리스트
list_a =  [1, 2, 3]
list_b =  [5, 6, 7]

# 리스트 기본 연산자
list_a + list_b =  [1, 2, 3, 5, 6, 7]
list_a * 3 =  [1, 2, 3, 1, 2, 3, 1, 2, 3]

# 길이 구하기
len(list_a) =  3
```

---

## 리스트에 요소 추가하기 : append(), insert(), extend()

리스트에 요소를 추가할 때 대표적인 두 가지 방법이 있습니다.

```
리스트명.append(요소)
리스트명.insert(인덱스, 요소)
```

### 리스트에 요소 추가하기

```python
list_a = [1,2,3]
list_b = [5,6,7]

print("# 리스트 뒤에 요소 추가하기")
list_a.append(4)
list_a.append(5)
print(list_a)
print()

print("# 리스트 중간에 요소 추가하기")
list_a.insert(1,10)
print(list_a)
```

▶ 실행결과

```
# 리스트 뒤에 요소 추가하기
[1, 2, 3, 4, 5]

# 리스트 중간에 요소 추가하기
[1, 10, 2, 3, 4, 5]
```

### 리스트에 한번에 여러 요소 추가하기

`extend()` 함수를 사용해 한번에 여러 요소를 추가할 수 있습니다.

```pyhon
>>> list_a = [1,2,3]
>>> list_a.extend([4,5,6])
>>> print(list_a)
[1, 2, 3, 4, 5, 6]
```

---

## 리스트에 요소 제거하기 : del, pop(), remove(), clear()

### 인덱스로 제거하기 : del, pop()

```
del 리스트명[인덱스]

리스트명.pop(인덱스)
```

#### 리스트 요소를 인덱스 기반으로 제거하기

```python
list_a = [1,2,3,4,5,6]

print("# 리스트 요소 하나 제거하기")
del list_a[1]
print("del list_a[1] = ", list_a)
list_a.pop(2)
print("list_a.pop(2) = ", list_a)
list_a.pop()
print("list_a.pop() = ", list_a) # pop() 함수의 매개변수에 아무 것도 입력하지 않으면 자동으로 -1이 들어가 마지막 요소를 제거합니다.
```

▶ 실행결과

```
# 리스트 요소 하나 제거하기
del list_a[1] =  [1, 3, 4, 5, 6]
list_a.pop(2) =  [1, 3, 5, 6]
list_a.pop() =  [1, 3, 5]
```

#### 리스트 요소를 한꺼번에 제거하기

`del 키워드`를 사용해 범위를 지정하여 리스트의 요소를 한꺼번에 제거할 수도 있습니다.

```pyhton
>>> list_a = [1,2,3,4,5,6,7,8]
>>> del list_a[3:6]
>>> list_a
[1, 2, 3, 7, 8]

```

범위의 한쪽을 입력하지 않은면 지정한 위치를 기준으로 한쪽을 전부 제거할 수 있습니다.

```pyhon
>>> list_a = [1,2,3,4,5,6,7,8]
>>> del list_a[:3]
>>> list_a
[4, 5, 6, 7, 8]
```

```pyhon
>>> list_a = [1,2,3,4,5,6,7,8]
>>> del list_a[3:]
>>> list_a
[1, 2, 3]
```

### 값으로 제거하기 : remove()

```
리스트.remove(값)
```

```pyhon
>>> list_a = [1,2,1,2]
>>> list_a.remove(2)
>>> list_a
[1, 1, 2]
```

`remove()` 함수로 지정한 값이 리스트 내부에 여러개 있어도 가장 먼저 발견되는 하나만 제거됩니다.

### 모두 제거하기 : clear()

리스트 내부의 요소를 모두 제거할 때는 `clear()` 함수를 사용합니다.

```
리스트.clear()
```

```pyhon
>>> list_a = [0,1,2,3,4,5,6]
>>> list_a.clear()
>>> list_a
[]
```

---

## 리스트 내부에 있는지 확인하기 : in/not in 연산자

```
값 in 리스트
```

#### in 연산자

```python
>>> list_a = [274, 5, 103, 6, 7]
>>> 273 in list_a
False
>>> 5 in list_a
True
>>> 1 in list_a
```

#### not in 연산자

```python
>>> list_a = [274, 5, 103, 6, 7]
>>> 1 not in list_a
True
>>> 5 not in list_a
False
>>> 273 not in list_a
True
```

---

## for 반복문 : 리스트와 함께 사용하기

for 반복문의 기본 형태는 다음과 같습니다.

```python
for 반복자 in 반복할 수 있는 것 :
  코드
```

```python
array = [274, 56, 15, 47]
for element in array :
    print(element)
```

▶ 실행결과

```
274
56
15
47
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
