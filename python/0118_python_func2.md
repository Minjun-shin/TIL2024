# 01.18.

## 모듈

- 한 파일로 묶인 변수와 함수의 모음
- 특정한 기능을 가진 코드가 작성된 파이썬 파일
- ex) `math` `numpy` `pandas`
- 모듈 가져오기 - `import`
- `help` - 모듈 정보 가져옴

```python
import math as m

print(m.pi) # 3.141592...
print(m.sqrt(4)) # 2.0
```

- `.`은 ‘점 왼쪽 객체에서 오른쪽의 객체를 찾아라’라는 의미
- `from`은 모듈로 부터 특정 요소를 import
- `from`을 쓰면 덜 명시적
- ※ 다른 모듈에서 같은 이름의 함수 불러올 시 문제 발생(마지막 걸로 대체) - ∴ `import *` 사용 시 주의
- 패키지 : 모듈을 모아놓은 집합
- 라이브러리 : 모듈과 패키지의 집합체
    
    [파이썬 표준 라이브러리](https://docs.python.org/ko/3/library/index.html)
    
- 외부 패키지 - 설치 필요 `pip install {library}`
    
    [PyPI · The Python Package Index](https://pypi.org/)
    
    - 버전을 지정해서 받을 수 있다.
- 패키지 사용목적 - 모듈들을 효율적으로 관리하기 위함

# 제어문

- 코드의 흐름을 제어
- 조건의 따라 코드를 **실행** or **반복**

## 조건문

- 참인 경우에만 실행
- `if` / `elif` / `else`
- 복수 조건문 - 순차적으로 진행
- 주어진 코드 블록을 반복적으로 실행
- `for` / `while`

### for

- 시퀀스의 항목들을 들어있는 순서대로 반복
    
    ```python
    for variable in iterable:
        code
    ```
    
- iterable
    - 반복문에서 순회할 수 있는 객체
    - 시퀀스 뿐아니라 set, dict 포함
- tip - iterable은 복수형으로 변수명 정하기 → 반복문 속 변수를 단수형으로 하면 되기 때문
- 중첩된 반복문에서 안쪽부터 반복

### while

- 주어진 조건식이 참인 동안 코드를 반복해서 실행
    
    ```python
    while conditional expression:
        code
    ```
    
- 종료 조건은 중요하기때문에 작성할 때 잘 생각할 것

### for vs while

for

- 반복 횟수가 명확할 때
- 시퀀스 형태의 데이터를 처리할 때

while

- 반복 횟수는 명확하지 않고 종료 조건이 존재할 때
- ex) 사용자의 입력에 따라 종료

### 반복 제어

- 반복문을 끝내고 싶을 때, 일부만 실행하고 싶을 때
- `break` `continue`
- `break` : 반복문 자체를 종료
- `continue` : 다음 반복으로 넘어감
- 남용 금물

## List Comprehension

```python
[expression for variable in iterable]
[expression for variable in iterable if conditional expression]
[expression1 if conditional expression2 else expression for variable in iterable]

'''
반복문 따라 요소 생성
if문이 참일때만 요소 추가
if문이 참이면 1번 표현식, 아니면 2번 표현식
'''
```

- 명시적이지는 않음 - 남용금지

### pass

- 아무것도 수행하지 않고 넘어가는 명령어
- 사용처
    1. 임시로 코드를 완성시켜 놓을 때 ※
    2. 조건문에서 넘어갈 때
    3. 루프에서 계속 진행하기 위해서

### enumerate

- 인덱스와 요소를 같이 출력할 때