# 1. 제어문

> 프로그래밍 언어는 작성된 코드의 순서를 따릅니다. 그러나, 개발자에 의도에 따라서 때로는 흐름을 조정하거나 제어할 필요가 있는데, 이 때에 사용하는 것이 제어문입니다. 제어문은 `if`같은 `조건문`과 `while`같은 `반복문`으로 나누어 집니다. 

## 

## 1.1. 조건문

> 참, 거짓을 판단하는 `조건식`과 함께 쓰이는 `제어문`

### 

### 1.1.1. 조건문의 기본 형식

```python
# 조건문의 기본 형식
if a == True :
    print("it is True") # 조건식이 참일때,
else:
    print("it is False") # 조건식이 거짓일때,
```

### 

### 1.1.2. 복수조건문 (2개 이상의 조건이 필요할 때)

> 분기점이 2개 이상인 조건이 필요할 때에는 복수 조건문을 사용합니다.

```python
# 복수 조건문의 기본 양식

if a > 10:
    print("a > 10")

elif a > 5:
    print("a > 5")
elif a > 0 :
     print("a > 0")
else :
    print("a < 0")
```

### 

### 1.1.3. 중첩조건문 (~라면 ~인지 보고 ~한다.)

> 조건의 상하관계가 존재할 때에는 중첩 조건문을 사용합니다.

```python
# 중첩조건문의 기본양식
a = 100

if (a > 10):
    print("a > 10")
    if(a>50)
        print("a>50")
else:
    print("a <= 10")
```

> 중첩 반복문은 이론상 무한정 연장시킬 수 있으나, 너무 많이 중첩하면 중첩지옥에 빠질 수 있습니다.

### 

### 1.1.4. 조건표현식(aka 삼항연산자)

> 조건에 따라 수행할 코드가 조건별로 한 줄이하일 때 사용할 수 있는 조건문입니다.

```python
# 조건표현식의 기본양식
a = 10

value = True if a > 5 else False
print(value) # True
```

## 

## 1.2. 반복문

> 특정 조건을 만족할 때까지 같은 작업을 반복하고 싶을 때 사용하는 제어문

### 

### 1.2.1. while문

> 종료 조건이 될 때까지 반복하는 반복문

```python
# while문의 기본 양식

a = 0
while a < 5:
    print(a)
    a = a + 1 # = a += 1
print("덧셈 끝")
```

📌 [복합연산자]() 와 함께 while문을 사용하면, 종료 조건을 만드는데 유용하며 자주 씁니다.

### 

### 1.2.2. for문

> 주로 iterable(like List)과 같이 사용되며, 정해진 횟수만큼 반복하는 반복문

```python
# for문의 기본 양식
fruit = ['apple', 'banana', 'cherry', 'django', 'end']
for memeber in furit:
    print(member)
'''
apple
banana
cherry
django
end
'''
```

### 

### 딕셔너리의 순회

> 딕셔너리는 `key` 값을 기준으로 값을 탐색하는데, for문을 이용해서 딕셔너리를 순회할 수 있습니다.

```python
# for문을 이용한 딕셔너리의 탐색
Daejeon = {'jo' : 90, 'Lee' : 40, 'Kang' : 77, 'Son' : 66}

# 키 값만 탐색하고자 할 때,
Daejeon.keys()for key in Daejeon:
    print(key)

# 키 값을 기준으로 value를 탐색하고자 할 때,
for key, member in Daejeon:
    print(Daejeon[key])

# 키 값만 빠르게 확인하고 싶을 때
print(Daejeon.keys())

# value 만 빠르게 확인하고 싶을 때
print(Daejeon.values())

# key-value 쌍으로 확인하고 싶을 때
print(Daejeon.items)


# 위의 세가지 코드는 for문에 in 다음에 넣어서,
# 빠르게 배열을 만들고 순회시키는데 유용합니다.

# example
for key in Daejeon.keys():
    print(key)
```

### 

### List Comprehension(빠르게 리스트 만들기!)

> for문과 함께라면 원시 배열에서 간단하게 계산된 배열을 만들 수 있습니다.

```python
# list comprehension 기본 문법


triple = [number **3 for number in range(1,4)] # 1~3까지 세제곱한 값 배열
# [1,8,27]
```

### 

### Dictionary Comprehension(빠르게 딕셔너리 만들기!)

> 딕셔너리도 for문과 함께라면 빠르게 처리된 배열을 만들 수 있습니다.

```python
# Dictionary Comprehension의 기본 문법
# key: value for X in iterable
# key: value for X in iterable if 조건식

dict_1 = {key: member**3 for key in range(1,4)}
# {1:1, 2:8, 3:27}
```

### 

### 1.2.3. enumerate(열거형)

> 딕셔너리와 아주 궁합이 잘 맞으며, key-value로 된 값을 쉽게 분리해낼 수 있습니다.

```python
# enumerate 기본 양식

members = ['민수', '영희', '철수']

for idx, member in enumerate(members):
    print(idx, member)


# enumerate는 두번째 Argument로 시작값을 받기 때문에 
# 0부터가 아니라 1부터 맵핑할 수 있습니다.

for idx, member in enumerate(members, start=1):
    print(idx, member)


# 이렇게 써도 된다.
for idx, member in enumerate(members, 1):
    print(idx, member)
```

### 

### 1.2.3. 반복문 제어

### 

### break

> 반복문에서 조건문의 종료 조건과 상관 없이 반복문을 즉시 종료하는 예약어

```python
# break의 간단한 예시
a = 0
while a < 10 :
    a+=1
    if(a==2):
        break; # if문의 조건에 의해 while의 조건문을 만족하지 않았음에도 종료.
```

### 

### continue

> 반복문에서 조건문의 건너뛰기(skip)와 같은 기능을 하는 예약어.
> `continue`는 반복문을 `종료`하는 것이 아닌 `진행`시키는 에악어입니다.
> `진행`시킨다는 의미는 아래의 예시코드로 살펴봅시다.

```python
a = 0
while a < 10:
    a+=1
    if(a==3):
       continue

    print(a) 
```

 위 코드의 결과값은 3을 제외하고 출력합니다. 왜냐하면 반복문을 진행하다가 continue를 만나면, 곧바로 그 아래의 코드는 무시한 채 다음 코드를수행하기 때문입니다.

### 

### for-else

> 반복문을 실행한 `이후`에 실행되는 `else 문`으로, if-else와 다르게, 반복문이 `break`등으로 조기 종료되면 실행되지 않습니다. 그래서 반복문이 처음부터 끝까지 잘 실행되었는지를 판별하는데에 응용할 수 있습니다.

```python
# case1. break문으로 흐름이 이동되지 않을 때.

for char in 'apple':
    if char == 'b':
        print('b!')
        break
        print('b를 탐색!')
else:
    print('이 문자열에는 b가 없네요..') # 실행!


#case2. break문으로 흐름이 이동될 때,

for char in 'baby':
    if char == 'b':
        print('b!')
        break
        print('b를 탐색!')
else:
    print('이 문자열에는 b가 없네요..') #break문을 만나 for문이 종료되어 출력 X
```

### 

### pass

> 아무것도 하지 않는다는 의미의 예약어

```python
for i in range(4):
    if i == 2:
        pass
    print(i) # pass이므로 2가 정상적으로 출력!
```

## 

## 2.1. 함수를 왜 사용하는가?

`A function is simply a “chunk” of code that you can use over and over again, rather than writing it out multiple times.`

 프로그래밍에서 함수의 의미는 수학에서의 함수와 유의하나, 세부적으로 보면 분명 차이점은 있습니다. 수학에서의 함수는 미지수 x와 y등으로 표현되는 '식'이라면, 프로그래밍은 '식' 대신 '코드'가 대신합니다. 만약 새로운 프로그램을 만들 때마다 처음부터 기초가 되는 모든 코드를 만들어야 했다면, 개발자들은 새로운 프로그램을 만드는 데 혀를 내두를 것입니다. 자주 사용하는 코드들을 블럭화해서 재사용할 수 있도록 하는 것, 또한 그것으로 인해 크게 두가지 장점을 가질 수 있기 때문에 프로그래머는 함수를 사용합니다.



### 2.1.1. 분해(Decomposition)

 쉽게 예를 들어 보겠습니다. 파이썬에서 배열의 크기를 구하는 함수는 len()입니다. 그렇다면 len()을 직접 구현한다면 어떻게 할 수 있을까요?

```python
# 사용자 정의 len() 함수

numbers = [1,2,3]
count = 0
for i in [1,2,3]:
    count += 1
print(count)
```

 리스트를 선언하는데 사용한 1줄을 제외해도 len()이라는 함수를 구현하는 데에는 4줄이 사용되었습니다. 우리는 이미 len()이라는 함수를 알아서 한 줄에 할 수도 있는데 말이죠. 이처럼 함수는 복잡한 기능들을 기능 단위로 `분해` 해서 사용하기 편하도록 하기 위해 사용합니다.



### 2.1.2. 추상화(Abstraction)

 추상화라는 단어를 듣고서 피카소가 떠오르진 않으셨는지요? 프로그래밍에서 추상화는 `함수 안의 로직이 어떻게 구현되어 있는지 알지 못해도 사용법을 쉽게 유추할 수 있는 것`이라고 할 수 있겠습니다. `2.1.1. 분해`에서 예시를 들었던 `len()`함수를 예를 들어보죠, 프로그래밍을 모르는 사람이라도 약간의 공부만 한다면 len()은 배열의 길이를 알려주는 함수이구나 라는 것을 유추할 수 있습니다. 다른 예를 들어본다면 print() 함수도 역시 프로그래밍 언어를 배우면서 제일 먼저 쓰는 코드이지만 우리는 누구나 print()가 값을 출력하는 함수라는 것을 알고 있습니다. 이 함수가 내부에 어떤 로직을 가지고 있는지는 잘 몰라도 말이죠. 이처럼 누구나 쉽게 함수의 사용처를 유추할 수 있고, 쉽게 사용할 수 있는 특성을 추상화라고 하며 이러한 특성으로 인해 프로그래머는 모든 함수들을 백과사전처럼 외우지 않아도 됩니다. 





## 2.2. 함수의 기초

### 2.2.1. 함수의 종류

> 함수는 크게 3가지 종류로 분류할 수 있습니다.

#### 1) 내장함수

> 파이썬에 기본적으로 포함되는 함수 ex) print()

#### 2) 외장함수

> 파이썬이 기본적으로 없어서, import 문을 통해 도입해 사용해야하는 함수

#### 3) 사용자 정의 함수

> 사용자가 직접 만든 함수

 
 함수의 구분은 시대에 따라서 상황에 따라서 변동성이 있으므로, 오늘의 외장함수가 얼마든지 내일의 내장함수가 될 수도 있음을 이해하고 개념만 잘 이해하면 됩니다.

### 

### 2.2.2. 함수의 정의

> 함수를 정의하는 방법은 아래와 같습니다.

```python
def func1(parameter):
    print(parameter)

func1(Argument)
```

 함수는 `def`를 통해서 쉽게 만들 수 있습니다. 이러한 함수는 소괄호 안에 값을 받을 수도 있고 안받을 수도 있는데요. 값을 받고 안받고에 따라서 받으면 `Value Returnnig Fucntion`, 안받으면 `Void Function`이라고 구분짓습니다. `Void Function`은 매개변수가 없이 사용하는 함수이고, `Value Returnnig Fucntion`는 매개 변수를 받아야하는 함수입니다. 

### 

### 2.2.3. return

 함수에서의 모든 계산이나 작업이 종료된 이후에 함수를 종료하고 값을 전달하는데 쓰는 것이 `return`입니다. `return`뒤에 값을 적으면 그 값을 반환하고, 아무것도 적지 않으면 함수를 그냥 종료하게 됩니다. 단, return은 함수 하나당 한 번만 쓸 수 있으며, 돌려줄 수 있는 값은 한 종류 입니다. 여기서 한종류라고 표현한 이유는 `return 1` 이렇게 작성하면 1이라는 숫자 하나만 돌려주게 되지만, `return [1,2,3]`을 하게 되면 2개 이상의 값을 돌려줄 수 있기 때문입니다. 

### 

### 2.2.4. parameter와 argument

 함수는 선언할 때 `parameter`를 선언 할 지 안할지 정할 수 있습니다. `parameter`를 선언했다면, 후속 코드에서 함수를 사용할 때 함수에 `parameter`를 입력하면 그 입력값은 `argument`가 됩니다.

```python
# parameter와 argument

def print_input(s): #여기에서 `s`는 parameter 입니다.
    print(s)

print_input(s) # 여기에서 's'는 argument 입니다.
```

### Positional Argument

  함수의 Argument는 입력된 순서에 따라 미리 함수에 선언한 변수로 값이 할당되는데, 이것을 `Positional Argument`라고 합니다. 그러나 개발자가 함수 안의 값을 특정짓고 맵핑하고 싶을 때는 `Keyword Arguments`를 사용할 수 있습니다.

```python
def add(x, y):
    return x + y

add (1,2) # Positional Argument
add (x=1, y=2) #Keyword Arguments

add(2, y=3) # 허용, 에러 X
add(x=2, 5) # 에러발생 : 함수에 argment를 적어줄 때, 
# `keyword Argument`로 적는 순간 그 후에 값들은 모두 
# `Keyword Argument`여야 하기에 오류를 발생시킵니다.
```

### 

### 2.2.5. 정해지지 않은 여러개의 Argumets 처리

> `print()` 함수가 여러개 인자를 받을 수 있는 이유?

### 

### 가변 인자(\*)

 `print()` 함수는 `paramter`로 애스터리스크(\*)를 사용하기 때문에 가능합니다. 함수 내의 Parameter에 \* 를 붙이면 가변인자가 됩니다. 가변인자는 값으 1개든 5개든 입력된 값에 따라서 유동적으로 크기를 조절합니다. 그래서 `print()` 함수는 여러 개의 인자를 받을 수 있습니다. 

```python
# 가변 인자와 패킹과 언패킹
# 패킹 : 여러개의 데이터를 묶어서 변수에 할당하기
numbers = (1,2,3,4,5) # 패킹

# 언패킹 : 배열의 값을 여러 변수에 할당하기
a, b, c, d, e = numbers
```

### 

### 가변 키워드 인자(**kwargs)

> 몇 개의 키워드를 받을지 모르는 함수 정의할 때 유용

```python
def family(**kwargs):
    for key, value in kwargs.items():
        print(key, ":", value)

family(fater='아부지', mother = '어무니')
# 가변 키워드 인자를 사용하면 변수명 = 값 양식으로 값을 입력하면 되며 key값은 ''로 묶지 않습니다.
```

## 

## 2.5. 함수의 범위(scope)

> 함수의 범위(scope)란 함수의 life cycle의 범위이기도 하며, 어디까지 재사용이 가능한지의 기준점이 되기도 합니다.

 함수의 스코프는 `절대적인 위치`가 아니라 `상대적인 위치`입니다. 파이썬에서 함수의 스코프는 크게 4가지로 나뉘는데, 각각 `Built-in`, `Gobal`, `Enclosed` , `Local` 입니다.

#### 

#### Built-in scope

`Built-in scopes are one of the widest scopes that cover all the reserved keywords. These are easy to call anywhere in the program prior to using them, without the need to define them.`

 먼저 `Built-in` 스코프는 파이썬 함수에서 선언되지 않은 변수를 탐색해야할 경우 파이썬이 `Local`에서부터 변수를 탐색해 나가다가 마지막까지 찾지 못하면 탐색하는 가장 넓은 범위의 스코프입니다. 

![0721s1](https://github.com/1-Hee/TIL/blob/master/source/0721s1.PNG?raw=true)

> `Built-in` 스코프의 종류

#### 

#### Global scope

> 함수나 반복문 외부에서 선언된 변수

```python
# example

a = 10 # Global scope
def test():
    a = 10 # Local scope
```

> 파이썬 파일에서 함수와 반복문 안에 쓰이지 않은 대부분의 변수는 전역변수입니다.

#### 

#### Enclosed scope

> 2개 이상의 중첩함수에서만 존재하는 outer 함수에 선언된 변수

```python
# example

def outer_func():
    a = 10 # Enclosed scope
    def innter_func():
        a = 10 # Local
```

#### 

#### Local scope

> 함수나 반복문 내부에서 선언된 변수

```python
# example

def test():
    a = 10 # Local scope


while True:
    b = 10 # Local scope
```

### 

### 2.5.1. Scope의 확장

#### Global scope

> global scope인 변수를 사용하거나, local과 global scope의 변수 이름이 같아 구분이 필요할 때 사용합니다.

```python
# example

a= 10

def test():
    global a
    a = 11
    print(a) # 10    
```

#### 

#### nonlocal

> global을 제외하고 가장 가까운 scope의 변수를 선택하도록 할 때

```python
# example

a= 10

def test():
    nonlocal a
    x = 10
    print(a) # 10    
```



## 2.6. 함수의 응용

### 2.6.1. map

> 순회 가능한 데이터구조(iterable)의 모든 요소에 대한 형변환을 하고 map object로 반환하는 함수

*map object != 리스트, 튜플, 딕셔너리 등*

map 함수는 결과값을 `map object`로 반환하기 때문에 배열 등에 응용하려면 list()와 같은 함수를 사용해야합니다.

```python
# example
st = '12345'

lst1 = list(map(int, st)) # [1,2,3,4,5]
```

### 

### 2.6.2. filter

> 순회 가능한 데이터 구조의 모든 요소에 함수처리를 하고 그 결과가 True인 것을 filter object로 반환하는 함수

```python
# example
def odd(n):
    return n % 2
numbers = [1,2,3]
result = filter(odd, numbers) # 이렇게만 하면 filter object!
lst = list(result) # [1,3]
```

### 

### 2.6.3. zip

> 복수의 iterable을 모아 튜플을 원소로 하는 zip object를 반환

```python
#example 
girls = ['jelly', 'melly']
boys = ['justin', 'meric']
pair = zip(girls, boys) # 여기까지하면 zip object
lst = list(pair) # [('jelly', 'justin'), ('melly', 'meric')] # 1대일 대응 튜플!
```

### 

### 2.6.3. lambda

> 표현식을 계산한 결과값을 반환하는 함, 이름이 없는 함수여서 익명함수

return 문을 가질수 없고, 간편조건문 외 조건문이나 반복문을 사용할 수 없습니다.
**def를 사용할 수 없는 곳에서도 사용 가능** 합니다.

```python
#example 
#lambda를 사용하지 않고 구현할 때,
def triangle_area(b, h):
    return 0.5 * b * h
print(triangle_area(5, 6)) # 15.0

#lambda 사용 시
triangle area = lambda b, h : 0,5 * b * h
print(triangle_area(5,6)) # 15.0
```

### 

### 2.6.4. 재귀함수(recursive function)

> 자기 자신을 호출하는 함수

- 점화식 같은 곳에서 로직을 표한하기 쉬운 경우에 사용합니다. 
- 변수의 사용이 줄어들어 코드의 가독성이 높아집니다.
- 1개 이상의 base case(종료 상황)이 존재하고, 수렴하도록 작성합니다.

```python
# example
# 팩토리얼
def factorial(n):
    if n == 0 or n==1
        return 1
    else:
        n * factorial(n-1)

print(factorial(4)) # 24
```



📌 재귀 함수 주의 사항

- 재귀함수는 base case에 도달할 때까지 함수를 호출합니다.
- 메모리 스텍이 넘치게 되면 stack overflow로 인해 프로그램이 동작하지 않습니다.
- 파이썬에서는 최대 재귀 깊이(maximum recursion depth) 가 1000번으로 이를 넘어서면 Error!
  
  

## 2.7. 모듈, 패키지, 라이브러리

> 다양한 기능을 하나의 파일로 묶은 것.

### 

### 2.7.1. 모듈 vs 패키지 vs 라이브러리

각각 기능을 묶은 것이라는 점에서 공통점을 가지나 규모의 측면에서는 다음과 같습니다.

`모듈 < 패키지 < 라이브러리`

- 모듈 = 다양한 기능들을 하나의 파일로 묶은 것. # (파이썬 파일 단위 .py)

- 패키지 = 다양한 모듈을 하나의 폴더로 묶은 것. # 모듈 묶음

- 라이브러리 = 다양한 패키지를 하나로 묶은 것. # 패키지 묶음

- 모듈과 패키지를 관리하는 관리자이자 명령여 → pip(== PyPI(Python Package Index))

### 

### 2.7.2. 모듈, 패키지, 라이브러리를 불러오는 방법

```python
import module
from module import (var, function, class) # from module import class 요런식!
from module import * # 전부다 도입!

from package import module
form package.module import var/function/Class 
# from package.module import Class 요런식!
```



💡 사용자가 직접 파일을 만들고 py로 저장한 다음에 폴더에 담으면 그것으로도 모듈로 사용 가능합니다.
` test 폴더 안에 tools라는 파일명으로 저장한 py 파일을 모듈로 쓰는 경우`

```python
from test import tools
```

### 

### 2.7.3. 파이썬 패키지 관리자 명령어

- 패키지의 설치
  
  - pip install Package
  - pip install Package = 1.0.5
  - pip install 'Package >= 1.0.4'

- 패키지 삭제
  
  - pip uninstall package

- 패키지 전체 목록 확인
  
  - pip list

- 특정 패키지에 대한 정보 확인
  
  - pip show package

- 현재 작업 환경에 설치된 패키지 정보를 저장
  
  - pip freeze > requirements.txt

- requirements.txt 등에 저장된 패키지 정보를 기준으로 새 작업환경에 설치하는 방법
  
  - pip install -r requirements.txt
  
  

## 2.8. 가상환경

> 파이썬 표준 라이브러리가 아닌 외부 패키지와 모듈을 사용하는 경우

 개발자가 프로젝트를 진행할 때마다 프로그램을 버전을 달리해서 새로 깔고 지우기를 반복한다면 여간 번거로운 일이 아닐 수 없을 것입니다. 또한, 그럴 수 밖에 없다면 개발자는 복수의 프로젝트에 참여하지 못할 것이기 때문에 인력의 낭비이기도 합니다. 그래서 파이썬에서는 가상환경을 제공하여 서로 독립적인 환경에서 개발할 수 있습니다.





- `파이썬에서 가상환경을 만드는 명령어 with git bash`

```python
python -m venv venv
# 여기서 첫번째 venv는 가상환경을 만드는 명령어, 두번재 venv는 폴더명입니다.
```

## 

- `파이썬에서 가상환경을 활성화/비활성화 시키는 방법(토글키처럼 온오프)`
  
  ```python
  source venv/Scripts/activate
  ```
