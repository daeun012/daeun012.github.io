---
title: 혼자 공부하는 파이썬 - 문자열, 리스트, 딕셔너리와 관련된 기본 함수
date: 2021-07-21
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
---

- 리스트에 적용할 수 있는 기본 함수 : min(), max(), sum()
- reversed() 함수로 리스트 뒤집기
- enumerate() 함수와 반복문 조합하기
- 딕셔너리의 items() 함수와 반복문 조합하기
- 리스트 내포

---

## 리스트에 적용할 수 있는 기본 함수 : min(), max(), sum()

- `min()` : 리스트 내부에서 최솟값을 찾습니다.
- `max()` : 리스트 내부에서 최댓값을 찾습니다.
- `sum()` : 리스트 내부에서 값을 모두 더합니다.

#### 예제로 살펴보기

```python
>>> numbers = [103, 45, 765, 65, 233]
>>> min(numbers)
45
>>> max(numbers)
765
>>> sum(numbers)
1211

# min() 함수와 max() 함수는 리스트를 사용하지 않고도 최솟값과 최댓값을 구할 수 있습니다.
>>> max(1,2,3,432,44,56,77)
432
>>> min(999,35,21,432,44,57,88)
21
```

---

## reversed() 함수로 리스트 뒤집기

리스트에서 요소의 순서를 뒤집고 싶을 때는 `reversed()` 함수를 사용합니다.

```python
list_a = [1,2,3,4,5]
list_reversed = reversed(list_a)

print("# reversed() 함수")
print("reversed(list_a): ", list_reversed)
print("list(reversed(list_a)): ", list(list_reversed))
print()

print("# reversed() 함수와 반복문")
for i in reversed([1,2,3,4,5]):
  print(i)
```

▶ 실행결과

```
# reversed() 함수
reversed(list_a):  <list_reverseiterator object at 0x0000027D495C5FD0>
list(reversed(list_a)):  [5, 4, 3, 2, 1]

# reversed() 함수와 반복문
5
4
3
2
1
```

### 확장 슬라이싱

리스트를 뒤집을 수 있는 또 다른 방법으로 `확장 슬라이싱`이 있습니다.

```python
>>> numbers = [1,2,3,4,5]
>>> numbers[::-1]
[5, 4, 3, 2, 1]

# 문자열에도 적용할 수 있습니다.
>>> "안녕하세요"[::-1]
'요세하녕안'
```

---

## enumerate() 함수와 반복문 조합하기

다음과 같은 리스트로 다음과 같은 결과를 출력하고 싶다면 어떻게 해야 할까요?

```python
list_a = ["A","B","C"]

# 원하는 출력결과
0 번째 요소는 A입니다.
1 번째 요소는 B입니다.
2 번째 요소는 C입니다.
```

제가 지금까지 배운 방법들로 조합해 보면 다음과 같이 작성할 수 있습니다.

```python
# 방법 1
list_a = ["A","B","C"]

i=0
for item in list_a :
  print("{} 번째 요소는 {}입니다.".format(i, item))
  i+=1

# 방법 2
list_a = ["A","B","C"]

for i in range(len(list_a)) :
  print("{} 번째 요소는 {}입니다.".format(i, list_a[i]))

```

이러한 코드를 더 쉽게 작성할 수 있도록 파이썬은 `enumerate()` 함수를 제공합니다.

#### enumerate() 함수와 리스트

```python
list_a = ["A","B","C"]

print("# 단순 출력")
print(list_a)
print()

print("# enumerate() 함수 적용 출력")
print(enumerate(list_a))
print()

print("# list() 함수로 변환해서 출력")
print(list(enumerate(list_a)))
print()

print("# 반복문과 조합하기")
for i, value in enumerate(list_a):
  print("{} 번째 요소는 {}입니다.".format(i,value))
```

▶ 실행결과

```
# 단순 출력
['A', 'B', 'C']

# enumerate() 함수 적용 출력
<enumerate object at 0x0000016DDB3993C0>

# list() 함수로 변환해서 출력
[(0, 'A'), (1, 'B'), (2, 'C')]

# 반복문과 조합하기
0 번째 요소는 A입니다.
1 번째 요소는 B입니다.
2 번째 요소는 C입니다.
```

---

## 딕셔너리의 items() 함수와 반복문 조합하기

`enumerate()` 함수와 반복문을 조합해 리스트의 인덱스 값을 쉽게 구할 수 있어던 것 처럼.  
딕셔너리는 `items()` 함수를 사용해 키 값을 쉽게 구할 수 있습니다.

```python
dictionary_a = {"키A": "값A","키B": "값B","키C": "값C"}

print("# 딕셔너리의 items() 함수")
print("items():", dictionary_a.items())
print()

print("# 딕셔너리의 items() 함수와 반복문 조합하기")
for key, element in dictionary_a.items():
  print("dictionary[{}] = {}".format(key, element))
```

▶ 실행결과

```
# 딕셔너리의 items() 함수
items(): dict_items([('키A', '값A'), ('키B', '값B'), ('키C', '값C')])

# 딕셔너리의 items() 함수와 반복문 조합하기
dictionary[키A] = 값A
dictionary[키B] = 값B
dictionary[키C] = 값C
```

---

## 리스트 내포

프로그램을 만들 때는 반복문을 사용해 리스트를 재조합하는 경우가 많습니다.  
우선 반복문을 사용해 리스트를 재조합하는 코드를 살펴봅시다.

```python
array = []

for i in range(0,20,2):
  array.append(i*i)

print(array)
```

▶ 실행결과

```
[0, 4, 16, 36, 64, 100, 144, 196, 256, 324]
```

이를 좀 더 쉽게 작성할 수 있는 방법이 있습니다.

```python
array = [i*i for i in range(0,20,2)]

print(array)
```

▶ 실행결과

```
[0, 4, 16, 36, 64, 100, 144, 196, 256, 324]
```

"range(0,20,2)의 요소를 i라고 할때 i\*i로 리스트를 재조합해 주세요" 라는 코드입니다. 이러한 구문을 **리스트 내포**라고 부릅니다.

리스트 내포는 다음과 같은 형태로 사용합니다.

```python
리스트 이름 = [표현식 for 반복자 in 반복할 수 있는 ㅍ것]
```

if 구문을 포함하여 사용할 수도 있습니다.

```pyhton
array = ["사과", "자두", "초콜릿", "바나나"]

output = [fruit for fruit in array if fruit !="초콜릿"]

print(output)
```

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
