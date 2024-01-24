# 01.24.

### 절차 지향 프로그래밍 (Procedual Programming)

- 데이터 & 절차(함수)
- 함수 호출의 **흐름**이 중요
- 실제로 실행되는 내용이 무엇인가가 중요
- 데이터 재사용 X
- 하드웨어의 발전 → 문제의 복잡성 증가 → 충돌 발생
- 객체 지향 프로그래밍의 대두

### 객체 지향 프로그래밍 (Object Oriented Programming)

- 데이터와 해당 데이터를 조작하는 메서드를 **하나의 객체**로 묶어 관리
- 객체 간 상호작용과 메세지 전달이 중요

## 클래스 (class)

- 파이썬에서 객체를 생성하기 위한 설계도(blueprint)
- 객체 : 클래스에서 정의한 것을 토대로 메모리에 할당된 것
- 변수 & 메서드
- 클래스로 만든 객체 - 인스턴스 (클래스도 객체이기에 따로 정의)
- 지금까지 사용한 모든 데이터 타입은 클래스로 구현된 것
- 하나의 객체는 특정 타입의 인스턴스
- 타입(type) : 가능한 연산자와 조작
- 속성(attribute) : 가지고 있는 상태(데이터)
- 조작법(method) : 할 수 있는 조작(함수)

### 파이썬에서의 클래스 사용법

- `class`로 정의해서 사용
- 명명법 - Pascal Case(단어마다 첫글자 대문자)

```python
class Person:
    blood_color = 'red'

    def __init__(self, name):
        self.name = name

    def singing(self):
        return f"{self.name}이/가 노래합니다."
```

```python
# 인스턴스 생성
singer1 = Person('IU')

# 메서드 호출
print(singer1.singing()) # IU이/가 노래합니다.

# 속성(변수) 접근
print(singer1.name) # IU
print(singer1.blood_color) # red
```

- `__init__`
    - 생성자 함수
    - 객체의 초기화
    - 인스턴스를 생성하고 초기 변수값 결정
- 인스턴스 변수
    - `__init__`속 `self.var`형태의 변수
    - 인스턴스마다 독립적으로 가지는 변수
    - 인스턴스 생성 시마다 초기화
- 클래스 변수
    - 클래스 내부에 선언된 변수
- 인스턴스 메서드
    - 각각의 인스턴스가 호출할 수 있는 메서드
- 이름 공간 (namespace)
    - 클래스 정의 → 해당하는 이름 공간 생성
    - 인스턴스 생성 → 독립적인 이름 공간 생성
    - 탐색 순서 : 인스턴스 → 클래스
    - 이점
        1. 인스턴스간 독립적인 메모리 공간을 가짐
        2. 독립적 동작, 충돌 방지
        3. 가독성, 유지 보수성, 재사용성 증가

## 메서드

### 인스턴스 메서드

- 각 인스턴스에서 호출할 수 있는 메서드
- 인스턴스의 상태(데이터)를 조작하거나 동작을 수행
- 정의 시 처음 매개변수로 `self`를 받음
- 이유
    - 인스턴스 호출 시 `instance.method()`의 형태로 작성
    - 하지만 실제로는 `Class.method(self=instance)`가 실행
    - 표기가 다른 이유 - 객체지향적 표기

### 생성자 메서드

- `def __init__(self):`의 형태
- 생성시 자동 호출
- `self`변수 뒤 변수들이 생성 시 입력할 변수들에 해당
- 작성하지 않아도 자동으로 호출
- `self`로 작성하지 않아도 작동은 하나 권장X

```python
class MyClass(object):
    def __init__(instance, name):
        instance.name = name

my_instance = MyClass('hey')
print(my_instance.name)
```

### 클래스 메서드

- 클래스가 호출
- 클래스 변수 조작하거나 클래스 레벨의 동작 수행
- 데코레이터 `@classmethod`를 사용하여 정의, 첫 매개변수는 `cls`

```python
class Person:
    cnt = 0

    def __init__(self, name):
        self.name = name
        Person.cnt += 1

    @classmethod
    def number_of_population(cls):
        print(f"Total population is {cls.cnt}.")

person1 = Person('IU')
person2 = Person('JBJ')

Person.number_of_population() # Total population is 2.
```

### 스태틱(정적) 메서드

- 독립적으로 동작하는 메서드
- 데코레이터 `@staticmethod`를 사용하여 정의, 첫 매개변수 고정X

```python
class StringUtils:
    @staticmethod
    def reverse_string(string):
        return string[::-1]
    

    @staticmethod
    def capitalize_string(string):
        return string.capitalize()
    

text = "abcdefg"

reversed_string = StringUtils.reverse_string(text)
print(reversed_string) # gfedcba

capitalized_string = StringUtils.capitalize_string(text)
print(capitalized_string) # Abcdefg
```

### 정리

클래스가 사용할 것

- 클래스 메서드
- 스태틱 메서드

인스턴스가 사용할 것

- 인스턴스 메서드

사용 자체는 클래스, 인스턴스 모두 가능

하지만 객체 지향성을 지키기 위해 구분해서 작성

### 참고

매직 메서드

- 이름 양끝에 __를 갖는 메서드
- 특수한 동작을 위함
- ex
    - `__str__(self)`, `__len__(self)`, `__lt__(self, other)` etc…
    - `__str__(self)`는 `print`시 자동으로 실행되는 메서드
    

데코레이터

```python
def my_decorator(func):
    def wrapper():
        print('Before call')
        result = func()
        print('After call')
        return result
    return wrapper

@my_decorator
def my_function():
    print('Calling')

my_function()
# Before call
# Calling
# After call
```