---
title: 혼자 공부하는 파이썬 - 함수의 활용
date: 2021-07-23
tags:
  - Python
keywords:
  - python
  - 혼자공부하는파이썬
  - 재귀 함수
---

- 재귀 함수
- 재귀 함수의 문제

---

## 재귀 함수

### 반복문으로 팩토리얼 구하기

```python
def factorial(n):
    output =1
    for i in range(1, n+1):
        output*=1
    return output
print("1! :", factorial(1))
print("2! :", factorial(2))
print("3! :", factorial(3))
print("4! :", factorial(4))
```

▶ 실행결과

```
1! : 1
2! : 2
3! : 6
4! : 24
```

### 재귀 함수로 팩토리얼 구하기

**재귀**란 '자기 자신을 호출하는 것'을 의미합니다.

```python
def factorial(n):
    if n ==0:
        return 1
    else :
        return n*factorial(n-1)
print("1! :", factorial(1))
print("2! :", factorial(2))
print("3! :", factorial(3))
print("4! :", factorial(4))
```

▶ 실행결과

```
1! : 1
2! : 2
3! : 6
4! : 24
```

---

## 재귀 함수의 문제

재귀 함수는 상황에 따라서 같은 것을 기하급수적으로 많이 반복한다는 문제가 있습니다. 재귀 함수로 인해 발생하는 문제를 알아보고 이후 문제를 해결할 수 있는 **메모화**라는 기술을 알아보려합니다.

### 재귀 함수로 피보나치 수열 구현하기

**피보나치 수열**은 '토끼는 어떠한 속도로 번식하는가'와 같은 연구에 사용되는 수열 입니다. 다음과 같은 규칙을 가지고 있습니다.

- 처음에는 토끼가 한 쌍만 존재합니다.
- 두 달 이상 된 토끼는 번식할 수 있습니다.
- 번식한 또끼는 매달 새끼를 한 쌍씩 낳습니다.
- 토끼는 죽지 않는다고 가정합니다.

이와 같은 규칙으로 한 달이 지날 때마다 달라지는 토끼 쌍의 수를 적어보면 '1쌍, 1쌍, 2쌍, 3쌍, 5쌍, 8쌍, 13쌍 ....'이 됩니다.  
규칙을 나타내보면 이와 다음과 같습니다.

- 1번째 수열 =1
- 2번째 수열 =1
- n번째 수열 = (n-1)번째 수열 + (n-2) 번째 수열

이를 코드로 구현해 보면 다음과 같습니다.

```python
def fibonacci(n):
    if n ==1:
        return 1
    if n ==2:
        return 1
    else :
        return fibonacci(n-1) + fibonacci(n-2)
print("fibonacci(1):", fibonacci(1))
print("fibonacci(2):", fibonacci(2))
print("fibonacci(3):", fibonacci(3))
print("fibonacci(4):", fibonacci(4))
print("fibonacci(35):", fibonacci(35))
```

▶ 실행결과

```
fibonacci(1): 1
fibonacci(2): 1
fibonacci(3): 2
fibonacci(4): 3
fibonacci(35): 9227465
```

fibonacci(35)를 입력해서 35번째 피보나치 수를 구하면, 시간이 좀 오래 걸리는 걸 확인 할 수 있습니다.  
왜 오래 걸리는지 코드를 변경해 문제를 확인해 보려합니다.

```python
counter = 0
def fibonacci(n):
    print('fibonacci({})를 구합니다.'.format(n))
    global counter
    counter+=1
    if n ==1:
        return 1
    if n ==2:
        return 1
    else :
        return fibonacci(n-1) + fibonacci(n-2)

fibonacci(10)
print("---")
print("fibonacci(10) 계산에 활용된 덧셈 횟수는 109번입니다.")

```

▶ 실행결과

```
fibonacci(10)를 구합니다.
fibonacci(9)를 구합니다.
... 생략 ...
fibonacci(1)를 구합니다.
fibonacci(2)를 구합니다.
---
fibonacci(10) 계산에 활용된 덧셈 횟수는 109번입니다.
```

코드를 실행해보면 같은 것을 여러 번 연산한다는 것을 확인할 수 있습니다.

#### UnboundLocalError 살펴보기

위의 코드를 보면 `global counter`라고 되어 있는 부분이 있습니다.
왜 이런 코드를 사용해야하는지 살펴보겠습니다.

```python
counter = 0
def fibonacci(n):
    print('fibonacci({})를 구합니다.'.format(n))
    # global counter  이 부분을 지워보겠습니다.
    counter+=1
    if n ==1:
        return 1
    if n ==2:
        return 1
    else :
        return fibonacci(n-1) + fibonacci(n-2)

fibonacci(10)
print("---")
print("fibonacci(10) 계산에 활용된 덧셈 횟수는 109번입니다.")
```

▶ 실행결과

```python
Traceback (most recent call last):
  File "c:\Users\다은\Desktop\test\format3.py", line 13, in <module>
    fibonacci(10)
  File "c:\Users\다은\Desktop\test\format3.py", line 5, in fibonacci
    counter+=1
UnboundLocalError: local variable 'counter' referenced before assignment
```

실행결과를 보면 `UnboundLocalError`를 확인할 수 있습니다.  
파이썬은 함수 내부에서 함수 외부에 있는 변수를 참조하지 못합니다.  
그래서 함수 내부에서 함수 외부에 있는 변수라는 것을 알리기 위해 `global 변수 이름` 이라는 구문을 사용한 것 입니다.

### 메모화

현재 재귀함수로 구현한 피보나치 수열의 문제는 같은 값을 구하는 연산을 반복하고 있기 때문에 발생하는 것 입니다.  
따라서 같은 값을 한 번만 계산하도록 코드를 수정해 문제를 해결해 보려 합니다.

```python
counter = 0
dictionary ={
    1:1,
    2:1
}
def fibonacci(n):
    if n in dictionary:
        return dictionary[n]
    else :
        output = fibonacci(n-1) + fibonacci(n-2)
        dictionary[n] = output
        return output

print("fibonacci(1):", fibonacci(1))
print("fibonacci(2):", fibonacci(2))
print("fibonacci(3):", fibonacci(3))
print("fibonacci(4):", fibonacci(4))
print("fibonacci(35):", fibonacci(35))
```

`fibonacci(35)`를 실행했을 때 아까와는 다르게 값이 바로 나오는 것을 확인할 수 있습니다!  
코드를 살펴보면 딕셔너리를 사용해 한 번 계산한 값을 저장합니다. 이를 **메모화**한다고 표현합니다.  
딕셔너리에 값이 메모되 있으면 처리를 수행하지 않고 곧바로 메모된 값을 돌려주면서 코드의 속도를 빠르게 만드는 것입니다.

---

#### Reference

- [혼자 공부하는 파이썬](https://www.hanbit.co.kr/store/books/look.php?p_code=B2587075793)
