# 01.23.

## 데이터 구조 2

- 非시퀀스 데이터 구조

### **set**

| method | 설명 |
| --- | --- |
| s.add(x) | 세트에 항목 추가, 이미 있는 경우 변화 X |
| s.clear() | 세트의 모든 항목 제거 |
| s.remove(x) | 세트에서 항목 제거, 이미 없는 경우 Key error |
| s.pop() | 세트에서 랜덤(같은 확률 아님 - 해쉬 테이블과 연관)하게 항목을 반환 및 제거 |
| s.discard(x) | 세트에서 항목 제거, 이미 없는 경우 변화 X |
| s.update(iterable) | 세트에 iterable속 요소들 추가 |
- 집합 메서드

| method | 설명 | 연산자 |
| --- | --- | --- |
| set1,difference(set2) | 차집합 | set1 - set2 |
| set1.intersection(set2) | 교집합 | set1 & set2 |
| set1.issubset(set2) | 부분집합 여부 (set1 ⊂ set2) | set1 <= set2 |
| set1.issuperset(set2) | 부분집합 여부 (set1 ⊃ set2) | set1 >= set2 |
| set1.union(set2) | 합집합 | set1 | set2 |

### dictionary

| method | 설명 |
| --- | --- |
| D.clear() | 딕셔너리의 모든 키/값 쌍을 제거 |
| D.get(k) | key값 반환 없으면 None 반환 |
| D.get(k, v) | key값 반환 없으면 v 반환 |
| D.keys() | 딕셔너리의 키를 모은 객체를 반환 |
| D.values() | 딕셔너리의 값을 모은 객체를 반환 (튜플 형태) |
| D.items() | 딕셔너리의 키/값 쌍을 모은 객체를 반환 |
| D.pop(k) | 딕셔너리에서 키를 제거하고 해당 값 반환, 없으면 error  |
| D.pop(k. v) | 딕셔너리에서 키를 제거하고 해당 값 반환, 없으면 v 반환 |
| D.setdefault(k, v=None) | 딕셔너리에서 키에 해당하는 값을 반환 <br> k가 딕셔너리의 키가 아닐 경우 값 v와 연결한 키 k를 추가하고 v를 반환 |
| D.update(other) | other 속 각 요소에 대해<br>1. 키가 딕셔너리에 있는 경우 키 값을 대체<br>2. 없는 경우 키/값 쌍을 추가 |
- .update()
    
    ```python
    person = {'name':'Alice', 'age': 30}
    
    other_person = {'name':'Jane', 'gender':'Female'}
    person.update(other_person)
    print(person) # {'name': 'Jane', 'age': 30, 'gender': 'Female'}
    
    person.update(age=50)
    print(person) # {'name': 'Jane', 'age': 50, 'gender': 'Female'}
    
    person.update(country='Korea')
    print(person) # {'name': 'Jane', 'age': 50, 'gender': 'Female', 'country': 'Korea'}
    ```
    

### Hash Table

- 해쉬 함수를 사용하여 변환한 값을 색인(index)으로 삼아 키-데이터를 저장하는 자료구조
- 데이터 검색 매우 빠름 - O(1)
- 파이썬에서는 set와 dict의 키가 해쉬 테이블을 사용
    - 이를 통해 중복을 방지
- set.pop()
    - hash 상 순서에 영향을 받음
    - 정수 값은 자체 값을 hash 값
    - 문자열의 경우 매번 다른 값을 가짐
- hashable
    - 대부분의 불변형 데이터 타입은 hashable
    - 튜플이 가변형 데이터를 참조할 경우 unhashable
    - 일관된 해쉬 값 = 불변형