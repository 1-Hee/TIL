# 객체지향 프로그래밍

## 객체지향 프로그래밍이란?
> `객체 지향 프로그래밍(Object Oriented Programming, OOP)`은 컴퓨터 프로그래밍의 `패러다임` 중 하나 

객체 지향 프로그래밍은 컴퓨터 프로그램을 `명령어의 목록`으로 보는 시각에서 벗어나 여러 개의 독립된 단위, 즉 `객체`들의 모임으로 파악하고자 하는 것입니다. 각각의 객체는 `메세지`를 주고 받고, 데이터를 처리할 수 있습니다.

`💡 객체는 세분화하면 정보객체와 행동 객체로 나누어 진다. 따라서 객체는 변수 + 함수 이다.`

## vs 절차지향 프로그래밍
> 데이터와 기능(메서드)를 분리하고, 추상화된 구조(인터페이스)로 제공하는 것.

![]()

### 객채지향이 필요한가? 
현실세계가 너무 복잡해져서 이것을 프로그래밍 설계에 반영하기에는 절차지향이 너무 어려워졌기 때문입니다.

![]()

## 1. 객체지향의 핵심 개념
장점 
- 클래스 단위로 모듈화 시켜 개발할 수 있으므로 많은 인원이 참여하는 대규모 소프트웨어 개발에 적합
- 필요한 부분만 수정하기 쉽기 때문에 프로그램의 유지보수가 쉬움

단점
- 설계 시 많은 노력과 시간이 필요함
    - 다양한 객체들의 상호 작용 구조를 만들기 위해 많은 시간과 노력이 필요,
- 실행 속도가 상대적으로 느림
    - 절차 지향 프로그래밍이 컴퓨터의 처리구조와 비슷해서 실행속도가 빠름.


## 2. 객체란? (컴퓨터 과학)
> 객체 또는 오브젝트(object)는 클래스에서 정의한 것을 토대로 메모리(실제 저장공간)에 할달된 것으로 프로그램에서 사용되는 데이터 또는 식별자에 의해 참조되는 공간을 의미하며, 변수, 자료구조, 함수 또는 메서드가 될 수 있다.

`💡 한줄요약 : 객체란 속성과 행동으로 구성된 모든 것`

-  클래스로 만든 객체를 인스턴스라고 합니다. 예컨데 `'Hello'`라고 하는 문자열을 하나 선언했다고 해보겠습니다. 이때 다음과 같이 표현할 수 있습니다.


```
'Hello'은 객체다(O)
'Hello'은 인스턴스다(X)
'Hello'은 클래스다(X)
'Hello'은 문자열(Str)의 인스턴스다(O)
→ 문자열이라는 Type의 하위 객체이다 
    = 'Hello'은 문자열(Str)의 인스턴스이다.
```

- 파이썬에서도 `클래스(Class)`라는 개념이 존재합니다. 이때 `클래스`를 선언한다는 것은 `클래스를 만든다 = Type을 만든다`라고 할 수 있습니다. 


- 파이썬은 모든것이 `객체(Object)`이다.
파이썬의 모든 것에는 속성과 행동이 존재합니다.

- 객체는 특정 타입의 인스턴스입니다. 비록 `클래스`를 만들지 않더라도 파이썬에서는 모든 것이 `객체` 입니다. 가령 `print('Hello Python')`에서 `'Hello Python'`은 객체이며 `문자열(Str)` 타입의 인스턴스 입니다.

-----------------------

### 객체의 특징
객체를 설명할 때, 다음의 세가지 개념이 존재합니다.

- 1) 타입 : 어떤 연산자(Operator)와 조작(Method)이 가능한가?
- 2) 속성 : 어떤 상태(데이터)를 가지는가?
- 3) 조작법(method) : 어떤 행위(함수)를 할 수 있는가?

예시를 들어보겠습니다.

`"banana".upper() `

위와 같은 코드가 있다고 했을 때 위의 세가지 개념에 대해서는 다음과 같이 설명할 수 있습니다.

1) `"banana"`는 `+`와 같은 연산(Operator)이나 `.upper() `와 같은 조작(method)이 가능하다.

2) `"banana"`는 문자열데이터를 가진다.

3) `"banana"`는 문자열 타입의 행위(함수)를 사용할 수 있다.

+extra)
- "banana"는 문자열(Str) 타입의 인스턴스 이다.
- .upper()는 행동, 함수, 메서드 이다.
- 객체(Object) = 속성(Attribute) + 기능(Method) 이다.


---------------------

### 기본 문법

클래스의 정의 `class MyClass:`

인스턴스 생성 `my_instance = MyClass()`

메서드 호출 `my_instance.my_method()`

속성 `my_instance.my_attribute`


### 클래스와 인스턴스
```python
class Person:
    pass

print(type(Person)) # <class 'type'>

person1 = Person() # 인스턴스 생성.

print(isinstance(person1, Person)) # person1은 Person의 인스턴스 인가요? , True

print(type(person1)) # <class '__main__.Person'>

```
### 객체를 비교하기
### `==`
- 동등한
- 변수가 참조하는 객체가 동등한 경우 True
- 두 객체가 같아 보이지만 실제로 동일한 대상을 가리키는가를 확인해주는 것은 아님.

### `is`
- 동일한
- 두 변수가 동일한 객체(id값, 주소값)을 가리키는 경우 True


```python
# '==' , 'is' 

a = [1,2,3]
b = [1,2,3]

print(a == b, a is b) # True False

a = c

print(a == c, a is c)  # True True

```

### 객체의 속성
- 특정 데이터 타입/클래스의 객체 들이 가지게 될 상태/데이터를 의미
- 클래스 변수/ 인스턴스 변수가 존재

```python
class Person:
    bloor_color = 'red' # 클래스의 변수
    
    def __init__(self, name):
        self.name = name # 인스턴수 변수


person1 = Person('지민')
print(person1.name) # 지민

```
### 인스턴스 변수

인스턴스 변수란?
- 인스턴스가 개인적으로 가지고 있는 속성
- 각 인스턴스들의 고유한 변수

- 생성자 메서드(`__init__`)에서 `self.<name>` 으로 정의
- 인스턴스가 생성된 이후 `<instance>.<name>` 으로 접근 및 할당

```python
class Person:
    # 클래스 변수가 없는 상황

    def __init__(slef, name): #여기서 선언했기 때문에
        self.name = name

john = Person('john') # 여기서 할당 해줘야 한다.
print(john.name) # john
john.name = 'John Kim'
print(john.name) # John Kim
```

### 클래스 변수
- 한 클래스의 모든 인스턴수가 공유하는 값을 의미
- 한 클래스의 인스턴스들은 같은 값을 가지게 됨.
- ex) 특정 사이트의 User 수는 클래스 변수를 사용해야함.


### 클래스 변수는 클래스 선언 시 내부에서의 정의한다
> 인스턴스 변수는 같은 클래스로부터 생성되었다고 하더라도,값을 조작하면 모두 같이 변경 됨.

```python
class Circle():
    pi = 3.14 # 클래스 변수 선언

    def __init__(self, r):
        self.r = r # 인스턴스 변수

c1  = Circle(5)
c2  = Circle(5)

# 과연 그럴지 테스트!
print(Circle.pi) # 3.14
print(c1.pi) # 3.14
print(c2.pi) # 3.14

Circle.pi = 5 # 클래스 변수를 바꿀때는 인스턴스로 접근하면 안되고, 클래스 변수 자체에서 바꿔야함.
# 지금의 코드에서는 [Circle]로 직접 접근해야함
print(Circle.pi) # 5
print(c1.pi) # 5
print(c2.pi) # 5

```

### 클래스 변수 활용(사용자 수 계산하기)
> 사용자가 몇 명인지 확인하고 싶다면?
- 인스턴스가 생성 될 때마다 클래스 변수가 늘어나도록 설정하면 됨.

```python
class Person:
    count = 0
    # 인스턴스 변수 설정
    def __init__(self, name):
        self.name = name
        Person.count += 1 #요렇게 자동으로 집계 가능!

person1 = Person('아이유')
person2 = Person('이찬혁')

print(Person.count) # 2
```

### 클래스 변수와 인스턴스 변수
> 클래스 변수를 변경할 ㄸ내 항상 클래스 변수 형식으로 변경!

```python
class Circle():
    pi = 3.14

    def __init__(self, r):
        self.r = r # 인스턴스 변수

c1 = Circle(5) # 인스턴스 변수를 바꾼 것임
c2 = Circle(1)

Circle.pi = 5
print(Circle.pi) # 5
print(c1.pi) # 5
print(c2.pi) # 5

```

------------------

### 메서드
> 특정 데이터 타입 / 클래스의 객체에 공통적으로 적용 가능한 행위(함수)

```python
class Person:

    def talk(self):
        print('안녕')

p1 = Person()
p1.talk() # 안녕

```
### 인스턴스 메서드
### 메서드의 종류
- 인스턴스 메서드 (인스턴스를 다루는 함수(인스턴스변수.. etc))
- 클래스 메서드 (클래스를 다루는 함수(클래스변수.. etc))
- 정적 메서드 (위 두가지에 해당되지 않는 독립적(?) 함수)


### 인스턴스 메서드
- 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메서드
- 클래스 내부에 정의되는 메서드의 기본
- 호출 시, 첫번째 인자로 인스턴스 자기자신(self)가 전달됨.

```python
class MyClass:
    
    def instance_method(slef, agr1, ...):

my_ins = MyClass()

```

### self
> 인스턴스 자기 자신
- 파이썬 인스턴스 메서드는 호출 시 첫번째 인자로 인스턴스 자신이 전달되게 설계됨.
- 매개변수 이름으로 self 를 첫번째 인자로 정의
- 다른 단어로 써도 작동하지만, 파이썬의 암묵적인 규칙

### 생성자(constructor) 메서드
- 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
- 인스턴스 변수들의 초기값을 생성
- 인스턴스 생성용 
- __init__ 메서드 자동 호출

```python
class Person:
    def __init__(self, name):
        print(f'인스턴스가 생성됨 {name}')

person1 = Person('지민') # 인스턴스가 생성됨 지민

```

### 매직메서드
- Dobule Underscore(__, aka 던더)가 있는 메서드로, 특수한 동작을 위해 만들어짐.
- 스페셜 메서드 혹은 매직 메서드라고 불림
- 특정 상황에서 자동으로 불리는 메서드

ex)
- __str__(self), __len(self)__, __repr(self)__,
- __lt__(self, other), __le__(self, other), __eq(self, other)__
- __gt__(self, other), __ge__(self, other), __ne__(self, other)


### 매직메서드의 예시
> 객체의 특수 조작 행위를 지정(함수, 연산자 등)
- `__str__` : 해당 객체의 출력 형태를 지정
    - 프린트 함수를 호출할 때, 자동으로 호출
    - 어떤 인스턴스를 출력하면 `__str__`의 return 값이 출력.

- `__gt__` : 부등호 연산자(>, greater than)


### 소멸자(destructor) 메서드
> 인스턴스 객체가 소멸(파괴)되기 직전에 호출되는 메서드

```python
class Person:

    def __del__(self):
        print('인스턴스가 사라졌습니다')

p1 = Person()
del p1 # '인스턴스가 사라졌습니다'
```

### 매직 메서드를 편집한 예시

```python
class Circle:

    def __init__(self, r):
        self.r = r

    def area(self):
        return 3.14 * self.r * self.r
    
    def __str__(self):
        return 'f[원] radius : {self.r}'
    
    def __gt__(self, other): # self가 있으므로 인스턴스 메서드
        return self.r > other.r

c1 = Circle(10)
c2 = Circle(1)

print(c1 > c2) # True , 반지름으로 비교함!

```

-----------------------


### 클래스 메서드
> 클래스가 사용할 메서드
- @classmethod 데코러이터를 사용하여 정의
- 호출 시, 첫번째 인자로 클래스(cls)가 전달됨.

### 클래스 메서드 활용
```python
class person:
    count = 0 # 클래스 변수
    def __init__(self, name): # 인스턴스 변수 설정
        self.name = name
        Person.count += 1
    
    # 인스턴스는 self
    # 클래스는 cls
    
    @classmethod
    def number_of_population(cls): # 클래스 메서드
        print(f'인구수는 {cls.count} 입니다.') 

person1 = Person('아이유')
person2 = Person('이찬혁')
print(Person.count) # 2

```

### 데코레이터
- 함수를 어떤 함수로 꾸며서 새로운 기능을 부여
- @데코레이터(함수명) 형태로 함수 위에 작성
- 순서대로 적용되기 때문에 작성 순서가 중요.

### 데코레이터 사용 예시

### 데코레이터 없이 함수 꾸미기

```python
def hello():
    print('Hello')

# 데코레이팅 함수
def add_print(original):
    def wrapper(): # 함수 내부에서 새로운 함수 선언!
        print('함수 시작')
        original()
        print('함수 끝')
    return wrapper # 함수를 리턴!

add_print(hello)()
# 함수시작
# 'Hello'
# '함수 끝'

prt_hello = addadd_print(hello)
prt_hello()
# 함수시작
# 'Hello'
# '함수 끝'

```

### 데코레이터
- 데코레이터를 활용하면 쉽게 여러 함수를 원하는데로 변경 가능!

```python
# 데코레이터 없이, 데코레이팅 함수를 사용
def add_print(original):
    def wrapper(): # 함수 내부에서 새로운 함수 선언!
        print('함수 시작')
        original()
        print('함수 끝')
    return wrapper # 함수를 리턴!

# 위 코드를 데코레이터 함수로 바로 한다면,
@add_print #add_print를 사용해서 print_hello()함수를 꾸며주도록 하는 명령어.
def print_hello():
    print("hello")

print_hello()
# "함수시작"
# "hello"
# "함수끝"

```
> 데코레이터의 차이가 헷갈린다면 바로 위 `데코레이터 없이 함수 꾸미기`으 소스 코드랑 비교해보기!



### 클래스 메서드와 인스턴스 메서드
- 클래스 메서드 -> 클래스 변수 사용
- 인스턴스 메서드 -> 인스턴스 변수 사용

그렇다면, 인스턴스 변수 클래스 변수를 모두 사용하고 싶다면? # 인스턴스 메서드를 사용해야한다!
- 클래스는 인스턴스 변수 사용 불가
- 인스턴스 메서드는 클래스 변수, 인스턴스 변수 둘다 사용 가능.

### 스태틱 메서드
> 인스턴스 변수, 클래스 변수를 전혀 다루지 않는 메서드

언제 사용?
- 속성을 다루지 않고 단지 기능(행동) 만을 하는 메서드 정의 할 때 사용

- 인스턴스 변수, 클래스 변수 아무것도 사용하지 않을 경우 사용
- @staticmetohd 데코레이터를 사용하여 정의
- 일반 함수처럼 동ㅇ작하지만, 클래스의 이름 공간(name space)에 귀속됨.
- 주로  해당 클래스로 한정하는 용도로 사용

```python
class MyClass:
    
    @staticmethod
    def static_method(arg1, ...):

MyClass.static_method(...)

```

### 스태틱 메서드 사용 예시

```python
class Person:
    count = 0 # 클래스 변수
    def __init__(self, name): # 인스턴스 변수 설정
        self.name = name
        Person.count += 1
    
    @staticmethod
    def check_rich(money): # 클래스 변수나, 인스턴스 변수를 건드리지 않음!
        return money > 1000 

person1 = Person('아이유')
person2 = Person('이찬혁')
print(Person.check_rich(100000)) # True
print(person1.check_rich(10000)) # True
# static은 클래스와 인스턴스에서 모두 접근 가능하다!

```

# 인스턴스와 클래스 간의 이름 공간(namespace)
- 클래스를 정의하면, 클래스와 해당하는 이름공간 생성
- 인스턴스를 만들면, 인스턴스 객체가 생성되고 이름 공간 생성
- 인스턴스에서 특정 속성에 접근하면, 인스턴스-클래스 순으로 탐색

```python
#  Person 정ㄹ의
class Person:
    name = 'unknown'
    
    def talk(self):
        print(self.name)

p1 = Person()
p1.talk() # unknown
# 이 때, talk() 는 함수 내부에 name이 없으므로 클래스 변수를 참조하게 됨!

# p2 인스턴스 변수 설정 전/후
p2 = Person()
p2.talk() # unknown
p2.name = 'Kim' # 클래스 변수 수정한거 아님!!!! 
p2.talk() # 'Kim' / 이때 인스턴스 변수를 가져옴!

print(Person.name) # unknown
print(p1.name) # unkown
print(p2.name) # 'Kim', 단 이때는 인스턴스 변수임!!!
```
----------------------------------------

### 메서드 정리
- 인스턴스 메서드
    - 호출한 인스턴스를 의미하는 self 매개 변수를 통해 인스턴스를 조작

- 클래스 메서드
    - 클래스를 의미하는 cls 매개 변수를 통해 클래스 조작

- 스태틱 메서드
    - 클래스 변수나 인스턴스 변수를 사용하지 않는 경우
    - 객체 상태나 클래스 상태를 수정할 수 없음.


### 예시 1
```python
class Myclass:

    def method(self): # 인스턴스 메서드
        return 'ins', self 
    
    @classmethod # 클래스 메서드!
    def classmethod(cls):
        return 'cls', cls
    
    @staticmethod
    def staticmethod():
        return 'static' # 매개변수 없음!

```

### 인스턴스 메서드를 호출한 결과

```python
obj = MyClass()
# 위에서 인스턴스 메서드의 이름을 method로 해서 아래는 인스턴스임!
print(obj.method()) # ins, 사용자 정의 클래스 주소값
print(Myclass.method(obj)) # ins, 사용자 정의 클래스 주소값

# 위 두 코드는 같은 결과 반환!
```

### 클래스 자체에서 각 메서드를 호출(인스턴스는 불가!)

```python
print(MyClass.classmethod()) # cls, 사용자 정의 클래스 주소
print(MyClass.staticmethod()) # static 

MyClass.method() # 불가! 오류 뱉음
```


### 예시 2
> 인스턴스 클래스 메서드와 스태틱 메서드 모두 접근 가능

```python
# obj 생성은 위에서 해서 생략함.

print(obj.method()) # ins, 사용자 정의 클래스 주소값

print(obj.classmethod()) # cls, 사용자 정의 클래스 주소

print(obj.staticmethod()) # static
```

---------------------

## 객체 지향의 핵심 개념 4가지


### 추상화

- 현실세계를 프로그램 설계에 반영
- 복잡한 것은 숨기고, 필요한 것만 들어내기
- 내부에 어떤 로직이 있는 지 몰라도 클래스 명이나 메서드 명으로써 기능을 유추해 쉽게 사용 가능한 것이 핵심

```python
```

### 상속

### 상속이란?
> 두 클래스 사이 부모-자식 관계를 정립하는 것.

- 클래스는 상속이 가능합니다.
- 모든 파이썬 클래스는 object 클래스를 상속받습니다.

`기본 문법`
```python
class ChildClass(ParentClass):
    pass
```

- 하위 클래스는 상위 클래스에 정의된 속성, 행동, 관계 및 제약 조건을 모두 상속 받음.
- 부모 클래스의 속성, 메서드가 자식 클래스에 상속되므로 코드 재사용성이 높아짐

### 상속-상속없이 구현하는 경우

` 학생/교수 정보를 나타내기 어려움`
```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def talk(self):
        print(f'반갑습니다. {self.name} 입니다.')

s1 =  Person('김학생', 23)
s1.talk() # 반갑습니다 김학생 입니다.

p1 = Person('박교수', 49)
p1.talk() # 반갑습니다 박교수 입니다.

s1.gpa = 4.5
p1.department = '컴퓨터 공학과'
# 불편함!
```
# 상속- 상속 없이 구현하는 경우 2

```python 
class Professor:
    def __init__(self, name, age, dep):
        self.name = name
        self.age = age
        self.dep = dep
    
    def talk(self):
        print(f'반갑습니다. {self.name} 입니다.')


class Student:
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa
    
    def talk(self):
        print(f'반갑습니다. {self.name} 입니다.')

p1 = Professor('박교수', 49, '컴퓨터공학과')

s1 = Student('김학생', 20, 3.5)

# 똑같은 내용이 중복됨!

```

## 상속 (위의 문제 해결!)
> 상속을 통한 메서드의 재활용

```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def talk(self):
        print(f'반갑습니다. {self.name} 입니다.')

class Professor(Person):
    def __init__(self, name, age, dep):
        self.name = name
        self.age = age
        self.dep = dep
    
class Student(Person):
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa


p1 = Professor('박교수', 49, '컴퓨터공학과')
s1 = Student('김학생', 20, 3.5)

```

### 상속 관련 함수와 메서드

### `ininstace(object, classinfo)`
> classinfo의 instance 이거나 subclass 인 경우 True!


```python
# 상속을 이용하지 않은 경우
class Person:
    pass

class Professor:
    pass

class Student:
    pass

p1 = Professor()
s1 = Student()

insinstance(p1, Person) # False
insinstance(p1, Professor) # True
insinstance(p1, Student) # False
insinstance(s1, Person) # False
insinstance(s1, Professor) # False
insinstance(s1, Student) # True

```

```python
# 상속을 이용한 경우

class Person:
    pass

class Professor(Person):
    pass

class Student(Person):
    pass

p1 = Professor()
s1 = Student()


insinstance(p1, Person) # True
insinstance(p1, Professor) # True
insinstance(p1, Student) # False
insinstance(s1, Person) # True
insinstance(s1, Professor) # False
insinstance(s1, Student) # True

```


### `insubclass(class, classinfo)`
- class가 classinfo의 subclass이면 True
- classinfo는 클래스 객체의 튜플일 수 있으며, classinfo의 모든 항목을 검사

```python
class Person:
    pass

class Professor(Person):
    pass

class Student(Person):
    pass

p1 = Professor()
s1 = Student()

issubclass(bool, int) # True
issubclass(float, int) # False
issubclass(Professor, Person) # True
issubclass(Professor, (Person, Student)) # True

```

### `super`
- 자식 클래스에서 부모클래스를 사용하고 싶은 경우
```python
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email

class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        #Person 클래스의 것을 사용하고 싶을 때
        super().__init__(name, age, number, email) # self는 쓸필요 없고, 이렇게 되면 부모 값을 모두 가져옴!
        self.student_id = student_id
        
```

### 상속 정리
- 파이썬의 모든 클래스는 object로부터 상속됨
- 부모 클래스는 모든 요소(속성, 메서드)가 상속됨
- super()를 통해 부모 클래스의 요소를 호출할 수 있음
- 메서드 오바리이딩을 통해 자식 클래스에서 재정의 가능함.
- 상속관계에서의 이름 공간은 인스턴스, 자식클래스, 부모 클래스 순으로 탐색

### 다중 상속
- 두 개 이상의 클래스를 상속 받는 경우
- 상속받은 모든 클래스의 요소를 활용 가능함
- 중복된 속성이나 메서드가 있는 경우 상속 순서에 의해 결정됨.


```python
class Person:
    def __init__(self, name):
        self.name = name
    
    def greeting(self):
        return f'안녕, {self.name}'

class Mom(Person):
    gene = 'XX'

    def swim(self):
        return '엄마가 수영'

class Dad(Person):
    gene = 'XY
    
    def walk(self):
        return '아빠가 걷기'

class FirstChild(Dad, Mom):
    def swim(self):
        return '첫째가 수영'
    
    def cry(self):
        return '첫째가 응애'

baby1 = FirstChild('아가')
print(baby1.cry()) # 첫째가 응애
print(baby1.swim()) # 첫째가 수영, 자식 클래스에서 정의했으므로 Mom 메서드가 아님.
print(baby1.walk()) # 아빠가 걷기
print(baby1.cry()) # XY, Dad 가먼저여서 Dad 값 상속.
    
```

### 다중상속의 arg 입력 순서가 다를 때


```python

class Person:
    def __init__(self, name):
        self.name = name
    
    def greeting(self):
        return f'안녕, {self.name}'

class Mom(Person):
    gene = 'XX'

    def swim(self):
        return '엄마가 수영'

class Dad(Person):
    gene = 'XY
    
    def walk(self):
        return '아빠가 걷기'

class SecondChild(Mom, Dad):
    def walk(self):
        return '둘째가 걷기'
    
    def cry(self):
        return '둘째가 응애'

baby2 = SecondChild('아가')
print(baby2.cry()) # 둘째가 응애
print(baby2.walk()) # 둘째가 걷기, 자식 클래스에서 정의했으므로 Dad 메서드가 아님.
print(baby1.swim()) # 엄마가 수영 
print(baby1.cry()) # XX, Mom이 먼저여서 Mom 값 상속.

```

### 상속 관련 함수와 메서드
> mro 메서드 (Method Resolution Order)
- 해상 인스턴스의 클래스가 어떤 부모의 클래스를 가지는지 확인하는 메서드
- 기존의 인스턴스 -> 클래스 순으로 이름 공간을 탐색하는 과정에서 상속 관계에 있으면 인스턴스 -> 자식클래스 -> 부모 클래스로 확장.

```python
print(FristChild.mro())
'''
[<class '__main__.FirstChild'>, <class '__main__.Dad'>, <class '__main__.Mom'>, <class '__main__.Person'>, <class 'object'>]
'''

print(SecondChild.mro())
'''
[<class '__main__.SecondChild'>, <class '__main__.Mom'>, <class '__main__.Dad'>, <class '__main__.Person'>, <class 'object'>]
'''
```

---------------

## 다형성
> 다형성(Polymorphism) 이란?
- 여러 모양을 뜻하는 그리스어
- 동일한 메서드가 클래스에 따라 다르게 행동할 수 있음을 의미
- 즉, 서로 다른 클래스에 속해 있는 객체들이 동일한 메세지에 대해 `다른 방식으로 응답`할 수 있음.

### 메서드 오버라이딩
>  상속받은 메서드를 재정의
- 클래스 상속 시 부모 클래스에서 정의한 메서드를 자식 클래스에서 변경
- 부모 클래스의 메서드 이름과 기본 기능은 그대로 사용하나, 특정 기능을 바꾸고 싶을 때 사용.

```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def talk(self):
        print(f'반갑습니다. {self.name} 입니다.')

# 자식 클래스 - Professor

class Professor(Person):
    def talk(self):
        print(f'{self.name}일세')

# 자식 클래스 - Student
class Student(Person):
    def talk(self):
        super().talk() # 부모의 것도 실행하고
        print(f'저는 학생입니다') # 이 부분도 실행!
        
p1 = Professor('김교수')
p1.talk() # 김교수일세

s1 = Student('이학생')
s1.talk()
# 반갑습니다. 이학생입니다.
# 저는 학생입니다.

```

```
# 파이썬은 오버라이딩만 있다!
# 파이썬에는 오버로딩이 없다 : 가변인자가 있어서
```

-----------

## 캡슐화
- 객체의 일부 구현 내용에 대해 외부로부터의 직접적인 액세스를 차단
    - ex) 주민등록번호
- 파이썬에서는 암묵적으로 존재하나, 언어적으로는 존재하지 않음.


### 접근제어자 종류
- Public Access Modifier
- Protected Access Modifier
- Private Access Modifier

### Public Member
- 언더바 없이 시작하는 메서드나 속성
- 어디서나 호출이 가능, 하위 클래스 override 허용
- 일반적으로 작성되는 메서드와 속성의 대다수를 차지

```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age

# Person 클래스의 인스턴스인 p1은 이름과 나이 모두 접근 가능하고 이 경우 변수는 Public임!
p1 = Person('김싸피', 30)
print(p1.name) # 김싸피
print(p1.age) # 30

```

### Protected Member
- 언더바 1개로 시작하는 메서드나 속성
- 암묵적 규칙에 의해 부모 클래스 내부와 자식클래스에서만 호출 가능
- 하위 클래스 override 허용


```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def get_age(self):
        return self._age # 요기서 제한!

## 인스턴스를 만들고 get_age 메서드를 활용하여 호출 가능
p1 = Person('김싸피', 30)
print(p1.get_age()) # 30

# _age에 직접 접근하여도 확인이 가능합니다.
# 파이썬에서는 암묵적으로 활용될 뿐입니다.

print(p1._age) # 30

```

### Private Member
- 언더바 2개로 시작하는 메서드나 속성
- 본 클래스 내부에서만 사용이 가능
- 하위 클래스 상속 및 호출 불가능(오류)
- 외부 호출 불가능(오류)

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def get_age(self):
        return self.__age # 요기서 제한!    

# 인스턴스를 만들고, get_age 메서드를 활용하여 호출할 수 있습니다.

p1 = Person('김싸피', 30)
print(p1.get_age()) # 30

# __age에 직접 접근이 불가합니다.
print(p1.__age) # 오류!

```

### getter 메서드와 setter 메서드
> private로 인해 변수를 가져 와서 직접적으로 수정하는 것을 막음으로 인해 값을 확인하거나 변경하는 것이 제한되는데 이것을 해결하기 위한 대안 방법!

- 변수에 접근할 수 있는 메서드를 별도로 생성
- getter 메서드 : 변수의 값을 읽는 메서드
    - @property 데코레이터 사용
- setter 메서드 : 변수의 값을 성격의 메서드
    - @변수.setter 사용

```python
class Person:
    def __init__(self, age):
        self.age = age

    @property # 이게 없이 아래 코드 처럼 호출하면 에러!
    def age(self):
        return self._age
    
    @age.setter
    def age(self, new_age):
        if new_age <= 19:
            raise ValueError('Too Young For SSAFY')
        
        self._age = new_age

p1 = Person(20)
print(p1.age) # 20 

p1.age = 33 # getter 가 있기 때문에 되는 것임!
print(p1.age) # 33 
    
p1.age = 19 # 가능한 이유 :
# 바로 age가 바뀌는게 아니라 내부로 들어가 new_age로 바꿈, 캡슐화(숨김!)
print(p1.age) # ValueError : Too Young For SSAFY!
```

------------------------

# 에러와 예외 처리

## 버그란?
- 최초의 버그는 1945년 프로그래밍 언어의 일종인 코볼 발명자 그레이스 호퍼가 발견
- 역사상 최초의 컴퓨터 버그는 Mark II 라는 컴퓨터 회로에 벌렝니 나방이 들어가 합선을 일으켜 비정상 적으로 동작
- 이 때부터 소프트웨어에서 발생하는 문제를 버그라고 부름

## 디버깅의 정의
- 잘못된 프로그램을 수정하는 것을 디버깅 de(없애다) + bugging(버그)
- 에러 메세지가 발생하는 경우
    - 해당하는 위치를 찾아 메세지를 해결
- 로직 에러가 발생하는 경우
    - 명시적인 에러 메세지 없이 예상과 다른 결과가 나온 경우

` " 코드의 상태를 신중하게 출력해가며 심시숙고하는 것보다 훌륭한 디버깅 도구는 없습니다"`

### 디버깅의 방법?
- print() 함수 활용
    - 특정함수의 결과, 반복, 조건 등을 나눠서 생각!
- 개발환경에서 제공하는 기능 활용
- Python tutor 활용
- 뇌컴파일, 눈 디버깅

## 문법 에러(Syntax Error)
- `SystaxError`가 발생하면, 파이썬 프로그램은 실행되지 않음
- 파일이름, 줄번호 ^ 문자 등을 통해 파이썬이 코드를 읽어 나갈 때 (parser) 문제가 발생한 위치를 표 현
- 줄에서 에러가 감지된 가장 앞의 위치를 가리키는 캐럿(caret) 기호(^)를 표시

### `invalid syntax : 문법 오류`
```python  
while # SyntaxEorr : invalid syntax
```

### `assign to literal : 잘못된 할당`
```python  
5 = 3 # SyntaxError : cannot assign to literal
```

### `EOL : 괄호 안닫은 경우`
```python  
print('hello
```

### `EOF : 함수 괄호 안 닫은 경우`
```python  
print(
```

## 예외(Exception)
- 실행 도중 예상치 못한 상황을 맞이하면, 프로그램 실행을 멈춤
    - 문장이나 표현식이 문법적으로 올바르더라도 발생하는 에러
- 실행 중에 감지되는 에러들을 예외(Exception)라고 부름
- 예외는 에러 타입(type)으로 나타나고, 타입이 메세지의 일부로 출력됨.
- 모든 내장 예외는 Exception Class를 상속받아 이뤄짐
- 사용자 정의 예외를 만들어 관리할 수 있음.


## 예외의 종류

### 1. ZeroDivisionError ( 0으로 나눔 )
> 0으로 나누고자 할 때 발생
- ` 10 / 0`

### 2. NameError (정의하지 않음)
> namespace 상에 이름이 없는 경우
- ` print(name_error)`

### 3. TypeError
> 타입이 불일치 하는 경우
- ` 1+ '1'`
- ` round('3.5`
- `divmod() # 인자가 꼭 필요한데 안넣어서 오류!`
```python
import random
random.sample() # 인자가 필요한데 넣어서 오류!
```
- `divmod(1,2,3) # 너무 많은 인자!`
```python
import random
random.sample(range(3), 1, 2) # Too much!
```
```python
import random
random.sample(1, 2) 
# 첫번째는 시퀀스를 넣어야 하는데 안넣어서 오류!
```
 
### 4. ValueError
- ` int('3.5') # 문법적으론 맞는데, 실수는 지원 안해서!`
- `range(3).index(6) # .index()는 없으면 에러 발생!`

### 5. IndexError
```python
empty_list = []
empty_list[2] # IndexError 
```

### 6. KeyError (dictionary)
```python
song = {'IU' : '좋은날'}
song['BTS'] # KeyError
```

### 7. ModuleNotFoundError
`import ssafy # ModuleNotFountError`

### 8. ImportError
```python
from random import samp
# 이름을 잘못 입력해서 오류 발생!
```

### 9. KeyboardInterrrupt - 임의로 프로그램 종료
```python
while True:
    continue

# Ctrl + C 눌렀을 때    
```

### 10. IndentationError - depth가 틀림1
```python
for i in range(3):
print(i)
```

## 예외 처리
- try문(statement) / except절(clause)을 이용하여 예외 처리를 할 수 있음
- try 문
    - 오류가 발생할 가능성이 있는 코드를 실행
    - 예외가 발생되지 않으면 except 없이 실행 종료
- except문
    - 예외가 발생하면, except 절이 실행
    - 예외 상황을 처리한느 코드를 받아서 적절한 조치를 취함.

### ` try문의 작성 방법`

```python
try:
    # try 명령문
except 예외그룹 -1 as 변수 -1:
    # 예외처리 명령문1
except 예외그룹 -2 as 변수 -2:
    # 예외처리 명령문 2
finally:
    # finally 명령문

```

### 예외 처리 예시

```python
try:
    num = input('숫자 입력 : ')
    
except:
    print('숫자가 아닙니다.')

```

```python

try:
    num = input('숫자 입력 : ')
    
except ValueError:
    print('숫자가 아닙니다.')


```

### 에러 메세지 처리 (as)
> as 키워드를 활용하여 원본 에러 메세지를 사용할 수 있음
- 예외를 다른 이름에 대입
`[][1] # IndexError : list index out of range  `

```python

try:
    empty_list = []
    print(empty_list[-1])
except IndexError as err:
    print(f'{err}, 오류가 발생했습니다.')

'''
list index out of range, 오류가 발생했습니다.
'''

```
### 복수의 예외 처리 실습
> 100을 사용자가 입력한 값을 나누고 출력하는 코드를 작성해보시오.
- 먼저, 발생 가능한 에러가 무엇인지 예상해보시오.

```python
num = input('100으로 나눌 값을 입력하시오 : ')
print(100/int(num)) 
# 예상 가능한 에러
# ZeroDivisionError
# TypeError
```

`100을 사용자가 입력한 정수로 나누고 출력하는 코드를 작성해보시오`

```python
try:
    num = input('100으로 나눌 값을 입력하시오 : ')
    100/int(num)

except (ValueError, ZeroDivisionError):
    print('제대로 입력해줘')

```

```python

try:
    num = input('100으로 나눌 값을 입력하시오 : ')
    print(100/int(num))
except ValueError:
    print('숫자를 넣어주세요')
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
except:
    print('에러는 모르지만 에러가 발생하였습니다.')

# 순차적으로 수행되므로 가장 작은 범주부터 예외처리!    

```

### 예외 처리 종합
- try : 코드를 실행함
- except : try 문에서 예외가 발생 시 실행함
- else : try 문에서 예외가 발생하지 않으면 실행함.
- finally : 예외 발생 여부와 관계 없이 항상 실행함.

### 예외 처리 종합 예시
- 파일을 열고 읽는 코드를 작성하는 경우
```
파일 열기 시도

    파일이 없는 경우 => '해당 파일이 없습니다' 출력.

    파일 있는 경우 => 파일 내용을 출력

해당 파일 읽기 작업 종료 메세지 출력
```

```python
try:
    f = open('noofile.txt')
except FileNotFoundError:
    print('해당 파일이 없습니다.') 
else:
    print('파일을 읽기 시작합니다.')
    print(f.read())
    print('파일을 모두 읽었습니다')
    f.close()   
finally:
    print('파일 읽기를 종료합니다.')

# 파일이 없는 경우
# '해당 파일이 없습니다'
# '파일 읽기를 종료합니다.'  

#  파일이 존재하는 경우
# '파일을 읽기 시작합니다'
# 파일내용
# '파일을 모두 읽었습니다.'
# '파일 읽기를 종료합니다.'

```

---------------------------------------



