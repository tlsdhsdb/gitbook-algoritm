# 함수와 람다 표현식

## 함수

* 함수\(Function\)란 특정한 작업을 하나의 단위로 묶어 놓은 것을 의미
* 함수를 사용하면 불필요한 소스코드의 반복을 줄일 수 있음

#### 함수의 종류

* **내장 함수:** 파이썬이 기본적으로 제공하는 함수
* **사용자 정의 함수:** 개발자가 직접 정의하여 사용할 수 있는 함수

#### 함수 정의하기

* 프로그램에는 똑같은 코드가 반복적으로 사용되어야 할 때가 많음
* **함수를 사용하면 소스코드의 길이를 줄일 수 있음**
  * **매개변수:** 함수 내부에서 사용할 변수
  * **반환 값:** 함수에서 처리 된 결과를 반환

```text
def 함수명(매개변수):
    실행할 소스코드
    return 반환 값
```

#### 더하기 함수 예시

더하기 함수 예시 1\)

```text
def add(a, b):
    return a + b

print(add(3, 7))
```

실행 결과

```text
10
```

**더하기 함수 예시 2\)**

```text
def add(a, b):
    print('함수의 결과:', a + b)

add(3, 7)
```

실행 결과

```text
함수의 결과: 10
```

#### 파라미터 지정하기

* **파라미터의 변수를 직접 지정**할 수 있음
  * 이 경우 매개변수의 순서가 달라도 상관이 없음

```text
def add(a, b):
    print('함수의 결과:', a + b)

add(b = 3, a = 7)
```

실행 결과

```text
함수의 결과ㅣ 10
```

#### global 키워드

* `global` 키워드로 변수를 지정하면 해당 함수에서는 지역 변수를 만들지 않고 **함수 바깥에 선언된 변수를 바로 참조**하게 됨

```text
a = 0

def func():
    global a
    a += 1

for i in range(10):
    func()

print(a)
```

실행 결과

```text
10
```

#### 여러 개의 반환 값

* 파이썬에서 함수는 여러 개의 반환 값을 가질 수 있음

```text
def operator(a, b):
    add_var = a + b
    subtract_var = a - b
    multiply_var = a * b
    divide_var = a / b
    return add_var, subtract_var, multiply_var, divide_var

a, b, c, d = operator(7, 3)
print(a, b, c, d)
```

실행 결과

```text
10 4 21 2.3333333333333335
```

## 람다 표현식

* 람다 표현식을 이용하면 함수를 간단하게 작성할 수 있음
  * 특정한 기능을 수행하는 함수를 한 줄에 작성할 수 있다는 점이 특징임

```text
def add(a, b):
    return a + b

# 일반적인 add() 메서드 사용
print(add(3, 7))

# 람다 표현식으로 구현한 add() 메서드
print((lambda a, b: a + b)(3, 7))
```

실행 결과

```text
10
10
```

#### 람다 표현식 예시: 내장 함수에서 자주 사용되는 람다 함수

```text
array = [('홍길동', 50), ('이순신', 32), ('아무개', 74)]

def my_key(x):
    return x[1]

print(sorted(array, key=my_key))
print(sorted(array, key=lambda x: x[1]))
```

실행 결과

```text
[('이순신', 32), ('홍길동', 50), ('아무개', 74)]
[('이순신', 32), ('홍길동', 50), ('아무개', 74)]
```

#### 람다 표현식 예시: 여러 개의 리스트에 적용

```text
list1 = [1, 2, 3, 4, 5]
list2 = [6, 7, 8, 9, 10]

result = map(lambda a, b: a + b, list1, list2)

print(list(result))
```

실행 결과

```text
[7, 9, 11, 13, 15]
```

