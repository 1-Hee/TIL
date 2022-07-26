# 파이썬의 함수들 중에 대한 심화적인 고찰

## 1. Zip

### `길이가 같은 배열을 수직으로 묶을 때`

> `Zip` 함수의 가장 기초적인 사용법으로 두 배열을 수직으로 묶어줍니다.

```python
a = [1,2,3]
b = [4,5,6]

print(list(zip(a,b))) # [(1, 4), (2, 5), (3, 6)] 

# 길이가 다른 두 배열도 묶어줍니다, 
# 단 이경우엔는 배열 e가 길이가 짧으므로 
# e의 가장 마지막 값인 인덱스 1번까지 두 쌍만 서로 짝지어 줍니다.

d = [1,2,3,4]
e = [1,2]

print(list(zip(d,e))) # [(1, 1), (2, 2)]

# 여러 개도 묶을 수 있습니다.

print(list(zip(a,b,d))) # 이경우에는 배열의 갯수만큼 짝지어지는데, 배열의 개수 n만큼 튜플로 묶어집니다.
# 마찬가지로 길이가 다르면 가장 짧은 길이까지만 짝짓습니다.

dic1 = {1:0, 2:0, 3:0}
dic2 = {2:0, 3:0, 4:0}


# zip도 묶을 수 있습니다, 단 이렇게 짝지으면 키값끼리 짝짓습니다. values()같은 메서드로 다른 값과 매칭 가능합니다.
print(list(zip(dic1,dic2)))


# zip은 iterable을 묶을 수 있기 때문에, 아래와 같이 range와도 맵핑이 가능합니다.
bf = dict(zip(range(1,4), [0]*3))
print(bf)
```

### `얕은 복사와 zip`

> `zip`은 2차원 이상의 배열을 선언할 때 발생하는 `얕은 복사` 이슈를 손쉽게 해결할 수 있습니다.

```python
matrix = [[0]*3]*3 # lite copy, 얕은 복사로 문제 발생.

mat = []
for _ in range(3):
    mat.append([0]*3) # 반복문으로 얕은 복사 문제 해결 가능.

print(mat)


# 2차 배열의 전치행렬을 만들어야 하는 경우

for r in range(3):
    for c in range(3):
        if r > c : # if문이 없으면 모든 좌표에 대해서 같은 연산을 해서 제자리 연산을 함.
            a[r][c], a[c][r] = a[c][r], a[r][c]

# 단점 : 정방형일 때만 먹힘!
```

## zip으로 손쉽게 전치행렬 만들기

> `Zip` 함수는 서로 다른 두 배열을 묶어줍니다. 이때 단순히 zip만쓰면 `zip object`를 반환하므로 `list()` 와 같이 `iterable`을 만드는 메서드와 함께 써야 변수에 저장해서 다룰 수 있습니다. 그러나 zip 객체는 그냥 `iterable`로 만들면 `tuple`을 반환하기 때문에, 값을 변경하거나 할 때에는 `map` 함수와 함께 씁니다.

```python
b = [[1,2,3,4],
     [5,6,7,8],
     [9,10,11,12]]


transposed_matrix = list(map(list, zip(*a))) # 전치 끝, this is unpacking
print(transposed_matrix)
```

for문을 이용한 `2차 배열` 전용 `deep copy` 함수

```python
def deep_copy(matrix):
    copied = []
    for i in range(len(matrix)):
        copied.append(matrix[i][:])

    return copied
```

### Scope Issue

```python
def a() :

    global x = 100 # x를 global에 선언하지 않았어도 선언이 되고 
                   # 심지어는 사용도 가능함! (global only)

    c = 10

    def b():
#        nonlocal c # 함수 b()를 호출할 때 c를 뭘 참조할 지 몰라서 
                    # 주석처리 시 오류남.

        print(id(c))
        c = 13
        print(id(c))

    b()

a()
```