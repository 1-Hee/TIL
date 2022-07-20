# 1. 제어문

> 프로그래밍 언어는 작성된 코드의 순서를 따릅니다. 그러나, 개발자에 의도에 따라서 때로는 흐름을 조정하거나 제어할 필요가 있는데, 이 때에 사용하는 것이 제어문입니다. 제어문은 `if`같은 `조건문`과 `while`같은 `반복문`으로 나누어 집니다. 

## 1.1. 조건문

> 참, 거짓을 판단하는 `조건식`과 함께 쓰이는 `제어문`

### 1.1.1. 조건문의 기본 형식

```python
# 조건문의 기본 형식
if a == True :
    print("it is True") # 조건식이 참일때,
else:
    print("it is False") # 조건식이 거짓일때,
```

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

### 1.1.4. 조건표현식(aka 삼항연산자)

> 조건에 따라 수행할 코드가 조건별로 한 줄이하일 때 사용할 수 있는 조건문입니다.

```python
# 조건표현식의 기본양식
a = 10

value = True if a > 5 else False
print(value) # True
```

## 1.2. 반복문

> 특정 조건을 만족할 때까지 같은 작업을 반복하고 싶을 때 사용하는 제어문

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

### List Comprehension(빠르게 리스트 만들기!)

> for문과 함께라면 원시 배열에서 간단하게 계산된 배열을 만들 수 있습니다.

```python
# list comprehension 기본 문법


triple = [number **3 for number in range(1,4)] # 1~3까지 세제곱한 값 배열
# [1,8,27]
```

### Dictionary Comprehension(빠르게 딕셔너리 만들기!)

> 딕셔너리도 for문과 함께라면 빠르게 처리된 배열을 만들 수 있습니다.

```python
# Dictionary Comprehension의 기본 문법
# key: value for X in iterable
# key: value for X in iterable if 조건식

dict_1 = {key: member**3 for key in range(1,4)}
# {1:1, 2:8, 3:27}
```

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

### 1.2.3. 반복문 제어

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

### pass

> 아무것도 하지 않는다는 의미의 예약어

```python
for i in range(4):
    if i == 2:
        pass
    print(i) # pass이므로 2가 정상적으로 출력!
```

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

### 1) 내장함수

> 파이썬에 기본적으로 포함되는 함수 ex) print()

### 2) 외장함수

> 파이썬이 기본적으로 없어서, import 문을 통해 도입해 사용해야하는 함수

### 3) 사용자 정의 함수

> 사용자가 직접 만든 함수

 함수의 구분은 시대에 따라서 상황에 따라서 변동성이 있으므로, 오늘의 외장함수가 얼마든지 내일의 내장함수가 될 수도 있음을 이해하고 개념만 잘 이해하면 됩니다.

### 2.2.2. 함수의 정의

> 함수를 정의하는 방법은 아래와 같습니다.

```python
def func1(parameter):
    print(parameter)
    
func1(Argument)

```

 함수는 `def`를 통해서 쉽게 만들 수 있습니다. 이러한 함수는 소괄호 안에 값을 받을 수도 있고 안받을 수도 있는데요. 값을 받고 안받고에 따라서 받으면 `Value Returnnig Fucntion`, 안받으면 `Void Function`이라고 구분짓습니다. `Void Function`은 매개변수가 없이 사용하는 함수이고, `Value Returnnig Fucntion`는 매개 변수를 받아야하는 함수입니다. 


### 2.2.3. return
 함수에서의 모든 계산이나 작업이 종료된 이후에 함수를 종료하고 값을 전달하는데 쓰는 것이 `return`입니다. `return`뒤에 값을 적으면 그 값을 반환하고, 아무것도 적지 않으면 함수를 그냥 종료하게 됩니다. 단, return은 함수 하나당 한 번만 쓸 수 있으며, 돌려줄 수 있는 값은 한 종류 입니다. 여기서 한종류라고 표현한 이유는 `return 1` 이렇게 작성하면 1이라는 숫자 하나만 돌려주게 되지만, `return [1,2,3]`을 하게 되면 2개 이상의 값을 돌려줄 수 있기 때문입니다. 
 

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
 
### 2.2.5. 정해지지 않은 여러개의 Argumets 처리
> `print()` 함수가 여러개 인자를 받을 수 있는 이유?

### 가변 인자(\*)

 `print()` 함수는 `paramter`로 애스터리스크(\*)를 사용하기 때문에 가능합니다. 함수 내의 Parameter에 \* 를 붙이면 가변인자가 됩니다. 가변인자는 값으 1개든 5개든 입력된 값에 따라서 유동적으로 크기를 조절합니다. 그래서 `print()` 함수는 여러 개의 인자를 받을 수 있습니다. 
 
 ```python
# 가변 인자와 패킹과 언패킹
# 패킹 : 여러개의 데이터를 묶어서 변수에 할당하기
numbers = (1,2,3,4,5) # 패킹

# 언패킹 : 배열의 값을 여러 변수에 할당하기
a, b, c, d, e = numbers
 
 ```

### 가변 키워드 인자(**kwargs)
> 몇 개의 키워드를 받을지 모르는 함수 정의할 때 유용

```python
def family(**kwargs):
    for key, value in kwargs.items():
        print(key, ":", value)

family(fater='아부지', mother = '어무니')
# 가변 키워드 인자를 사용하면 변수명 = 값 양식으로 값을 입력하면 되며 key값은 ''로 묶지 않습니다.
        

```

## 2.5. 함수의 범위

파이썬의 스코프 종류
Local Scope < Enclosed Scope < Global Scope < Built-in Scope

나중에 추가보충...

global, nonglobal

## 2.6. 함수의 응용

built-in, map, filter, zip, lambda, recursive function


## 2.7. 모듈
> 다양한 기능을 하나의 파일로 묶은 것.

모듈 < 패키지 < 라이브러리

패키지 = 다양한 모듈을 하나의 폴더로 묶은 것.

라이브러리 = 다양한 패키지를 하나로 묶은 것.

모듈과 패키지를 관리하는 관리자 = pip


패키지의 활용 공간 (가상환경)
모듈 사용 코드..


## 2.8. 파이썬 표준 라이브러리

pip install package
.
.
.


## 2.9. 사용자 모듈과 패키지
> 사용자가 직접 파이썬 파일로 모듈을 만들고 적용하고 싶을 때



## 2.10. 가상환경
> 파이썬 표준 라이브러리가 아닌 외부 패키지와 모듈을 사용하는 경우
