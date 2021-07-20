---
title: 혼자 공부하는 파이썬 - 딕셔너리와 반복문
date: 2021-07-21
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 딕셔너리란?
- 딕셔너리에 값 추가/제거 하기
- 딕셔너리 내부에 키가 있는지 확인하기 : in 키워드, get()
- for 반복문 : 딕셔너리와 함께 사용하기

---

## 딕셔너리란?

**리스트**가 '인덱스를 기반'으로 값을 저장하는 것이라면,  
**딕셔너리**는 '키를 기반으'로 값을 저장하는 것이라고 할 수 있습니다.

### 딕셔너리 선언하기

딕셔너리는 중괄호{ }로 선언하며, '키:값' 형태를 쉼표로 연결해 만듭니다.

```python
>>> dict_a ={
... "name" : "김다은",
... "age" : 25
... }

# 딕셔너리 내부의 값에 여러 자료를 넣을 수 있습니다.
>>> dict_b = {
... "student" : ["김말숙", "김철수", "이승한"],
... "dept" : ["경영학과", "전자공학과", "물리학과"]
... }
```

### 딕셔너리 요소에 접근하기

```python
>>> dict_a ={
... "name" : "김다은",
... "age" : 25
... }
>>> dict_a
{'name': '김다은', 'age': 25}
>>> dict_a["name"]
'김다은'
>>> dict_a["age"]
25

>>> dict_b = {
... "student" : ["김말숙", "김철수", "이승한"],
... "dept" : ["경영학과", "전자공학과", "물리학과"]
... }
>>> dict_b
{'student': ['김말숙', '김철수', '이승한'], 'dept': ['경영학과', '전자공학과', '물리학과']}
```

### 딕셔너리의 문자열 키와 관련된 실수 살펴보기

```python
>>> dict_key = {
... name : "건조 망고",
... type : "당절임"
... }
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
NameError: name 'name' is not defined
```

name이라는 이름이 정의되지 않았다는 오류입니다.  
파이썬은 딕셔너리의 키에 단순한 식별자를 입력하면 변수로 인식합니다.  
이러한 오류를 피하기 위해.  
키를 문자열로 사용 할 때는 반드시 따옴표를 붙여주어야 합니다.

```python
dict_key = {
... 'name' : '건조망고',
... 'type' : '당절임'
... }
```

---

## 딕셔너리에 값 추가/제거 하기

### 딕셔너리에 요소 추가하기

```python
dictionary = {}

print("요소 추가 이전 :", dictionary)

dictionary["name"] = "새로운 이름"
dictionary["haed"] = "새로운 머리"
dictionary["body"] = "새로운 몸"

print("요소 추가 이후 :", dictionary)
```

▶ 실행결과

```
요소 추가 이전 : {}
요소 추가 이후 : {'name': '새로운 이름', 'haed': '새로운 머리', 'body': '새로운 몸'}
```

### 딕셔너리에 요소 제거하기

```python
dictionary = {
  "name" : "건조 망고",
  "type" : "당절임"
}

print("요소 추가 이전 :", dictionary)

del dictionary["name"]

print("요소 추가 이후 :", dictionary)
```

▶ 실행결과

```
요소 추가 이전 : {'name': '건조 망고', 'type': '당절임'}
요소 추가 이후 : {'type': '당절임'}
```

### KeyError 예외 살펴보기

리스트의 길이를 넘는 인덱스에 접근하면 `IndexError`가 발생했습니다.  
딕셔너리도 존재하지 않는 키에 접근하면 `KeyError`가 발생합니다

```python
>>> dictionary = {}
>>> dictionary["name"]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'name'
```

---

## 딕셔너리 내부에 키가 있는지 확인하기 : in 키워드, get()

### in 키워드

```python
dictionary = {
  "name" : "건조 망고",
  "type" : "당절임",
  "ingredient" : ["망고", "설탕", "치자황색소"],
  "origin" : "필리핀"
}

key = input(">접근하고자 하는 키:")

if key in dictionary :
  print(dictionary[key])
else :
  print("존재하지 않는 키에 접근하고 있습니다.")


```

▶ 실행결과

```
>접근하고자 하는 키:name
건조 망고

>접근하고자 하는 키:gg
존재하지 않는 키에 접근하고 있습니다.
```

### get() 함수

```python
dictionary = {
  "name" : "건조 망고",
  "type" : "당절임",
  "ingredient" : ["망고", "설탕", "치자황색소"],
  "origin" : "필리핀"
}

value = dictionary.get("존재하지 않는 키")
print ("값:", value)

if value == None:
  print("존재하지 않는 키에 접근했었습니다.")
```

▶ 실행결과

```
값: None
존재하지 않는 키에 접근했었습니다.
```

---

## for 반복문 : 딕셔너리와 함께 사용하기

```python
for 키 변수 in 딕셔너리:
    코드
```

```python
dictionary = {
  "name" : "건조 망고",
  "type" : "당절임",
  "ingredient" : ["망고", "설탕", "치자황색소"],
  "origin" : "필리핀"
}

for key in dictionary :
  print(key,":",dictionary[key] )
```

▶ 실행결과

```
name : 건조 망고
type : 당절임
ingredient : ['망고', '설탕', '치자황색소']
origin : 필리핀
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
