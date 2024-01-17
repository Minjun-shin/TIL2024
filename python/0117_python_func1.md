# 01.17.

## 함수

- 재사용 가능한 코드 묶음
- 중복 방지, 재사용
- 가독성 & 유지 보수성 UP
- 내장 함수(built-in func)
    - 기본적으로 제공되는 함수 - import 불필요
    - ex) `print` `abs`
- 함수 호출 : 함수의 이름을 사용하여 코드 블럭을 실행하는 것
- 함수 구조
    - parameter - INPUT
    - func body - 코드 블럭
    - Docstring - guide (Optional)
    - return value - OUTPUT (if you need it)
- 함수 정의 - `def` 사용
    
    ```python
    def func_name(parameter):
        '''
    	func info
    	'''
    	#func body
    	parameter += 1
    	
    	# OUTPUT
    	return parameter
    ```
    
- 주의 - `return` 이후 줄은 작동하지 않음
- 함수 호출 - 호출 시 함수 이름과 필요한 인자(argument) 전달
    - `()` 필요
    - parameter ≠ argument
    - 거의 비슷하게 보이고 혼용하여 사용하는 경우가 많음
    - parameter는 정의할 때, argument는 호출할 때
- 인자의 종류
    - 위치 인자 (Positional) - 인자 위치에 따라 전달되는 인자, 호출 시
        
        ```python
        def greeting(name, age):
        	print(f'안녕하세요, {name}님! {age}살이시군요.')
        
        greeting('Alice', 25) # 안녕하세요, Alice님! 25살이시군요.
        greeting('Bella') # Error : missing 1 positional argument 'age'
        greeting('Alice', 25, 'Bella') # Error : 2 positional argument but 3 were given
        ```
        
    - 기본 인자 값 (Default) - 인자에 기본 값 할당
        - 전달하지 않을 경우 기본 값 사용
        
        ```python
        def greeting(name, age=30):
        		print(f'안녕하세요, {name}님! {age}살이시군요.')
        
        greeting('Alice', 25) # 안녕하세요, Alice님! 25살이시군요.
        greeting('Bella') # 안녕하세요, Bella님! 30살이시군요.
        ```
        
    - 키워드 인자 (keyward) - **호출 시** 사용
        - 순서는 중요하지 않음
        - 키워드 인자는 위치 인자 뒤에 위치해야 함
        
        ```python
        def greeting(name, age):
        	print(f'안녕하세요, {name}님! {age}살이시군요.')
        
        greeting('Alice', 25) # 안녕하세요, Alice님! 25살이시군요.
        greeting(25, 'Alice') # 안녕하세요, 25님! Alice살이시군요.
        greeting(age=25, name='Alice') # 안녕하세요, Alice님! 25살이시군요.
        greeting(age=25, 'Alice') # Error
        ```
        
    - 임의의 인자 목록 (Arbitrary Argument List)
        - 정해지지 않은 개수의 인자 (0개 이상) ex) `print`
        - 정의 시 인자 앞에 `*`
        - args는 튜플로 처리됨
        
        ```python
        def calculate_sum(*args):
        	print(args)
        	total = sum(args)
        	print(f'합계 : {total}')
        
        calculate_sum(1, 2, 3)
        # (1, 2, 3)
        # 합계 : 6
        ```
        
    - 임의의 키워드 인자 목록 (Arbitrary Keyward Argument List)
        - 정해지지 않은 개수의 키워드 인자 (0개 이상)
        - 정의 시 인자 앞에 `**`
        - kwargs는 딕셔너리로 처리됨
        
        ```python
        def print_info(**kwargs):
        	print(kwargs)
        
        print_info(name='Alice', age=30) # {'name':'Alice, 'age':30}
        ```
        
    - 인자 순서
        
        ```python
        def func(arg1, arg2=None, *args, **kwargs):
        	pass
        ```
        

### 함수의 Scope

- 함수의 공간
    - Local - 함수 내 scope
    - Global - 모든 코드가 참조할 수 있는 scope
- 변수가 어느 scope에 있는지 주의 - 변수의 수명주기와 관련
- 수명 주기(Life-Cycle)
    - built-in - 파이썬이 실행된 이후 계속 유지
    - global - 모듈이 호출된 이후 또는 인터프리터가 끝날 때까지 유지
    - local - 함수가 호출된 이후부터 종료될 때까지 유지
- 이름 검색 규칙
    - Local → Enclosed → Global → Built-in
- `global` - 전역 변수로 선언하기 위함
    - 변수 접근 전에 사용해야 함
    - 매개변수에 사용 X
    - Not recommended

### 재귀함수

- 함수 내에서 자기자신을 호출하는 함수
- ex) factorial
    
    ```python
    def factorial(n):
    	if n == 1: # base case
    		return 1
    	return n * factorial(n-1)
    
    print(factorial(5)) # 5! = 120
    ```
    
- 1개 이상의 베이스 케이스 존재, 수렴하도록 작성
- recursion error 주의

### 유용한 내장 함수

- map
    - `map(func, iterable)`
    - iterable한 데이터 구조의 모든 요소에 함수를 적용하여 map object로 return
- zip
    - `zip(*iterable)`
    - 임의의 iterable들을 모아 튜플을 원소로 하는 zip object  return

### Lambda Function

- 익명 함수
- `lambda parameter : expression`
- 예시
    
    ```python
    add_nums = lambda x, y : x + y
    
    print(add_nums(1, 3)) # 1 + 3 = 4
    ```
    
- 간단한 연산이나 함수를 표현할 때 사용
- 함수를 **매개변수**로 사용할 때 사용 - ***중요***

### Packing & Unpacking

- Packing : 여러 개의 값을 하나의 변수에 할당
- 예) 가변 인자
    - `a, *b, c = [1, 2, 3, 4, 5]` → `a = 1`, `b = [2, 3, 4]`, `c = 5`
- Unpacking : packing된 변수의 값을 개별적인 변수들에 할당하는 것
- `a, b, c = (1, 2, 3)`
- `*` 는 리스트의 요소를 Unpacking
- `**` 는 딕셔너리의 요소를 Unpacking