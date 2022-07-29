
# JAVA STATEMENTS (JAVA BASIC)

## 1. 자바 기본
## 변수(Variable)란?
- 자료를 저장하기 위한 메모리의 공간으로 `타입(Type)`에 따라 크기가 다름.
- 메모리 공간에 값(value)를 할당(assign) 후 사용

## 형(形, Type) 이란?
`데이터의 종류`
> 크게 두 종류로 나눔


| 기본형(Primitive Type) | 참조형(Reference Type)|
| ---- | ---- |
| 미리 정해진 크기의 Memory Size로 표현, 변수 자체에 값 저장 | 크기가 미리 정해질 수 없는 데이터의 표현, 변수에는 실제 값을 참조할 수 있는 주소만 저장|

`기본형(Primitive Type)의 크기 `

| 구분 | Type | bit 수 | 값의 범위 |
| :----: | :----: | :----: | :---- |
| 정수형 | byte | 8 | -2^7 ~ 2^7-1 / (-128~127)|
| 정수형 | short | 16  | -2^15 ~ 2^15-1 / (-32768~32767)|
| 정수형 | int | 32 | -2^31 ~ 2^31-1 / (-2147483648~2147483647, 약 20억 정도)|
| 정수형 | long | 64  | -2^63 ~ 2^63-1 / (-9223372036854775808~9223372036854775807)|
| 실수형 | float | 32 | float f = 0.1234567890123456789f; // 0.12345679 |
| 실수형 | double | 64 | double d = 0.1234567890123456789; // 0.12345678901234568 |
| 문자형 | char | 16 | \u0000 ~ \uffff (0 ~ 2^16-1) |

-------

## 다음 코드의 실행 결과는?
```java

public class Main {
    public static void main(String[] args){
        
        int i1 = Integer.MAX_VALUE;
        int i2 = i2+1;

        System.out.println(i2);
        // 결과는 overflow로 인해 -2147483648로 바뀌어 버림.

    }
}

```

-------

## 다음 코드의 실행 결과는 (2) ?

```java

public class Main {
    public static void main(String[] args){

        float f1 = 2.0f;
        float f2 = 1.1f;
        float f3 = f1-f2;
        System.out.println(f3) // 0.9
        
        double d1 = 2.0;
        double d2 = 1.1;
        double d3 = d1 - d2;
        System.out.println(d3);

        System.out.println(((int)(d1*100) - (int)(d2*100))/100.0); // 0.9

        BigDecimal bd1 = new BigDecimal("2.0");
        BigDecimal bd2 = new BigDecimal("1.1");
        System.out.println("BigDecimal을 이용한 빼기 : " + bd1.substract(b2)); // BigDecimal을 이용한 빼기 : 0.9

    }
}

```
> 실수의 연산은 `부동 소수점` 으로 인해 완벽하게 정확하지 않다. 왜냐하면 유효 자리수를 이용해 반올림하여 계산하기 때문.


--------------

## 형변환(Type Casting) 이란?
> 변수의 타입을 다른 타입으로 변환시키는 것
ex) char <-> int

- primitive 는 primitive 끼리, reference 는 reference 끼리 형 변환 가능하다.
- boolean은 다른 기본 타입과 호환되지 않는다.
- 기본 타입과 참조형의 형 변환을 위해서 Wrapper 클래스를 사용한다.

- 형변환 방법 : 
```java
double d = 100.5;
int result = (int) d; // d = 100.5 , result = 100
```

# 기본형의 형변환의 종류
> 두 가지로 나뉩니다.

- `묵시적 형변환 (promotion)`
- `명시적 형변환`

```java
// 묵시적 형 변환 (promotion)
byte b = 10;
int i = (int) b; // 작은 사이즈인 byte -> int 이므로 묵시적 ok
int i2 = b; // 타입 캐스팅 안해도 묵시적으로 casting

// 명시적 형 변환
int j = 300;
byte b = (byte) j; // 큰사이즈에서 작은 사이즈로 변경
// 값의 손실 가능.
```
- 값의 크기, 타입의 크기가 아닌 `타입의 표현 범위`가 `커지는 방향`으로 `할당`할 경우에는 묵시적 형변환 발생

` byte > short / char > int > long > float > double `

- 명시적 형 변환은 값 손실이 발생할 수 있으므로 프로그래머 책임 하에 형변환을 진행.
- 묵지석 형 변환은 자료의 손실 걱정이 없으므로 JVM이 서비스!

-----------------

## 다음 코드의 실행 결과는? (BP_09)

```java
// 이후 코드부터는 public class Main {} 부분을 생략함.
public static void main(String[] args){
    int i1 = Integer.MAX_VALUE;
    int i2 = i1 +1;
    System.out.println(i2); // -2147483648

    long l1 = i1 + 1;
    System.out.println(l1); // -2147483648, i1 자료형이 int였으므로 오버플로우 됨.
    
    long l2 = (long) (i1 + 1); // 연산을 먼저하므로 형변환이 나중에 이루어져서 overflow

    long l3 = (long) i1 + 1;
    System.out.println(l3);

	    int i3 = 1000000 * 1000000 / 100000; // 오버플로우 되서 이상한 숫자 나옴.
	    int i4 = 1000000 / 100000 * 100000; // 연산자 순서로 인해 나눗셈 먼저 되서 약분됨.
	    System.out.println(i3 + " : " + i4); 

}

```

----------------

## 연산자의 우선순위와 결합 방향
> 위에 쓰인 순서대로 우선순위 높음


| 연산기호 | 결합방향 |
| :---- | :----: |
| (), . |     |
| ++, --, +(부호), -(부호), ~, !, (type) | ← |
| * / % |  →  |
| +, - | → |
| <<, >>, >>> | → |
| <, >, <=, >=, instace of | → |
| ==, != | → |
| & | → |
| ^ | → |
| \| | → |
| && | → |
| \|\| | → |
| ? : | → |
| =, *=, /=, %=, +=, -=, <<=, >>=, >>>=, &=, ^=, \|= | ← | 

--------------------

## 다음 코드의 실행 결과는? (BP_11)
```java
public static void main(String[] args){
    byte b1 = 10;
    byte b2 = 20;
    byte b3 = b1+b2;
    
    int i1 = 10;
    long l1 = 20;
    int i2 = i1 + li;

    float f1 = 10.0;
    float f2 = f1 + 20.0;

}
```
- 산술 이항 연산자는 연산 전에 피 연산자의 타입을 일치시킨다.
- 피 연산자의 크기가 4byte(int) 미만이면 int 형으로 변경한 후 연산을 진행함.
- 두개의 피 연산자 중 큰 타입으로 형 변환 후 연산 진행


-----------

## 다음 코드의 실행 결과는? (BP_15)
```java
public static void main(String[] args){

    int a = 10;
    int b = 20;
    System.out.println((a > b) & (b > 0)); // false
    
    System.out.println((a += 10) > 15 | (b-=10) > 15); // true
    System.out.println("a = " + a + ", b = " + b);
    // a = 20, b = 10

    a = 10;
    b = 20;
    System.out.println((a += 10) > 15 || (b -= 10) > 15);
    System.out.println("a = " + a + ", b = " + b);
    //  a = 20, b = 20

}
```

-----------

## Java의 조건문 ( if & switch )
| if() | switch() |
| ---- | ---- |
| 논리형, boolean b; | 정수형, byte, short, char, int |
| 비교식, x >= y | Enum, Day.MONDAY |
| MethodCall, isEven() | ClassObject, Byte, Short, Character, Integer, String |
| xxxx | MethodCall, getNumber() |

## 조건문
> 주사위를 던져서 나오는 숫자에 따라 작동하는 조건문

```java
int N = 6;
int result = (int) (Math.random()*N) + 1;

if (result == 1) {

}else if (result == 2){

}else if (result == 3){

}else if (result == 4){

}else if (result == 5){

}else {
    
}

//////////////////

int N = 6;
int result = (int) (Math.random()*N) + 1;

switch(result){
    case 1:
        break;
    case 2:
        break;
    case 3:
        break;
    case 4:
        break;
    case 5:
        break;
    case 6:
        break;
    default:

}

```
---------------------
## 다음 코드의 실행 결과는 (BP_20)

```java
	public static void main(String[] args) {
		
		int month = 3;
		int day = -1;
		
		switch(month) {
			case 2:
				day = 20; break;
			case 4:
			case 6:
			case 9:
			case 11:
				day = 30 ; break;
			default:
				day = 31;
		
		}
        
        // day 값은 31이 됨.
		
	}
/// 

```

------------------

## 반복문의 구성

## for문

```java
for (int i = 0 ; i < 10 ; i++ ){
    break;
}
```

## while문

```java
while ( 반복조건 ){
    실행문
    증감식
    break;
}

```

---------------

## 100번 주사위를 던진 결과의 평균 값(실수)을 출력하는 코드를 for문과 while문을 통해 구현

```java

import java.math.*;
import java.util.Random;

public class Main {

	public static void main(String[] args) {
		
		int sum = 0;
		int playtime = 100;
		double avg = 0;
		
		
		for (int i = 0 ; i < playtime ; i ++) {
			
			sum += Math.random()*6+1;			
		}
		
		avg = 1.0*sum/playtime;
		
		System.out.println(sum+":"+avg);

		int sum2 = 0;
		int playtime2 = 100;
		double avg2 = 0;
		Random rand = new Random();
		
		int i = 0;
		
		while (i < playtime2) {
			
			sum2 += rand.nextInt(6)+1;
			
			i++;
		}
		
		avg2 = 1.0*sum2/playtime2;
		
		System.out.println(sum2 + " : " +avg2);
								
	}
}

```
------------------

## for 문과 while문의 차이
| 구분 | 특징 |
| :----: | :----: |
| for | 초기값, 조건식, 증감식의 위치가 명확 |
| for | 반복의 회수가 명확한 경우 |
| for | index 의 증감 활용 |
| while | 반복의 회수가 불명확한 경우 | 
| while | index 보다는 break, continue 활용 |


--------------

## 배열
## 동일한 타입의 변수를 여러 개 사용하면...
- 변수의 수 증가
- 코드 길이 증가
- 반복문 적용 불가
- 변수의 수가 동적으로 결정될 경우 사용 불가

## 배열(Array)로 동일 타입 변수 묶어서 사용하기
- 배열이란? 동일한 타입의 데이터 0개 이상을 하나의 연속된 메모리 공간에서 관리하는 것
- 요소에 접근하는 속도가 매우 빠르다.
- 한번 생성하면 크기 변경 불가

## 배열의 생성과 초기화
- ` new int[3]; `
- ` point = new int[3]; `
- ` points`는 메모리에 있는 배열을 가리키는 reference 타입 변수

## 배열의 요소 초기화
> 배열의 생성과 동시에 저장 대상 자료형에 대한 기본 값으로 default 초기화 진행

| 자료형 | 기본값 | 비고 |
| ---- | ---- | ---- |
| boolean |  false | x |
| char |  '\u0000' | 공백문자 |
| byte, short, int |  0 | x |
| long |  0L | x |
| float |  0.0f | x |
| double |  0.0 | x |
| 참조형 변수 |  null | x |


```java

public class Main {

	public static void main(String[] args) {
		
		
		int [] points = new int[3];
		
		points[0] = 1;
		points[1] = 'A'; // 묵시적 형 변환
		// points[2] = 1.5; 	// dobule 할당 불가
		
		System.out.println(points[0]); // 1		
		System.out.println(points[1]); // 'A'를 char				
		System.out.println(points[2]); // null
		
		
		
	}

}

```

## 1~6 까지의 random 정수 5개를 저장할 배열을 만들고 값을 저장하시오.

```java

import java.math.*;
import java.util.Random;

public class Main {

	public static void main(String[] args) {
				
		// 1 ~ 6 까지의 random 정수 5개를 저장할 배열을 만들고 값을 저장하시오.
		int[] resArr = new int[3];
		Random rand = new Random();
		
		for (int i = 0; i < 3 ; i ++) {
			resArr[i] = rand.nextInt(6)+1;
			System.out.println(resArr[i]);
		}
		
		
		// 위 배열에 저장된 요소 중 짝수만 더해서 합을 출력하시오.
		int sum = 0;
				
		for (int i = 0 ; i < resArr.length ; i ++) {
			if (resArr[i]%2==0) {
				sum+=resArr[i];
			}
		}
				
	}
}

```

## char[] 를 이용해 String "SSAFY"의 각 문자를 저장하고 출력하는 코드를 작성하시오.

```java

String st = "SSAFY";

char[] chars = new char[st.length()];

chars = st.toCharArray();
for (int i = 0 ; i < chars.length ; i ++){
    System.out.println(chars[i]);
}

```

## String "1234567890"의 별자리 수를 1차원 배열에 저장하고, 배열을 순회해서 그 합을 출력하시오.

```java

String org = "1234567890";

char[] my_char = new char[org.length()];

int sum = 0;

for (int i = 0 ; i < org.length; i ++){
    sum += my_char[i] - '0';
}

System.out.println(sum);
// int <-> char 간에는 형변환이 저유자재로!

```

## 기본문제6 다음은 배열의 다양한 생성 코드이다. 잘못된 것은?

```java

public class Main {

	public static void main(String[] args) {
		
		int[] ints = new int[3];
		ints[2] = 10;
		
		char[] chars = {'S','S', 'S','S','S'};
		
		boolean [] bools;
		// bools = {true,false, false};; // 배열의 크기는 선언과 동시에 결정해야함.
		
		
	}


```

## for-each Array
- 가독성이 개선된 반복문, 배열과 Collection에서 사용
- index 대신 직접 요소에 접근하는 변수 제공

```java

public class Main {

	public static void main(String[] args) {
		

		int intArr [] = new int [3]; // 값을 안담아주면 null인데
		
		for (int x : intArr) {// 이렇게 for문 순회하면 0을 출력.
			System.out.println(x);
		}
		
		
	}

}


```

## Array is Immutable
> 배열은 최초 메머리 할당 이후 변경할 수 없음.

```java

int [] nums = {1,2,3};

nums = new int[] {1,2,3,4} // 이거 안됨.

nums[1] = 100;
// 개별 요소에 대한 값 변경은 가능하나, 요소를 새로 추가하거나 삭제할 수는 없음.

```

## api로 제공하는 배열복사
- `System.arrayCopy`
- `Arrays.copyOf`


## 배열에서 새로운 요소를 추가하는 방법.

```java

int [] scores = {90, 80, 100};

scores[3] = 95; // index Error
scores = new int [] {90, 80, 100, 95}; // 불가
scores = {90, 80, 100, 95}

// 이 위 코드들은 확장하는 방법도 아니고 다 오류남

int[] scores = Arrays.copyOf(intArr, 5); // 배열 확장!
		
for (int i = 0 ; i < scores.length; i ++) {
	System.out.println(scores[i]);
}

```


## 기본문제 11
## 평균구하기, 평균차이가 가장 큰 값, 가장 작은 값

```java

```

## 기본문제 20
```java
```

-------------------------

# 객체지향 프로그래밍
## 객체지향 프로그래밍이란? - Object Oriented Programming

### 객체란?
> 주제가 아닌것, 주체가 활용하는 것.

### 객체지향 프로그래밍
- 주변에 많은 것들을 객체화 해서 프로그래밍 하는 것
- 객체 지향은 객체를 많이 만드는 것을 추천한다? (X)
 
## 객체지향 프로그래밍의 장점
- 블록형태의 모듈화된 프로그래밍
- 신뢰성 높은 프로그래밍이 가능하다.
- 추가, 수정, 삭제가 용이하다.
- 재사용성이 높다


## 자바의 클래스 정의

```java

public class Person{
    String name;
    int age;
    boolean isHungry;

    void eat(){
        System.out.println("냠냠");
        isHungry = False;
    }

    void work() {
        System.out.println("열일");
        isHungry = True;        
    }
}


```

## 인스턴스 멤버 변수의 특징
> `static` 없이 클래스 외부에 선언되는 변수는 인스턴스 변수

- 클래스 영역에 선언한다
- 객체가 만들어 질 때, 객체 별로 생성된다.
- 변수 타입 별로 default로 초기화 한다.
- 변수에 접근은 객체 생성(메모리에 올린 후) 객체이름으로 접근

- `중요` : Garbage Collector에 의해 객체가 없어질 때 없어지며, 프로그래머가 명시적으로 소멸 불가.


## 클래스 멤버 변수 특징
- 클래스 영역에 선언되며  `static` 키워드가 붙음
- 클래스 영역에 클래스 로딩시 메모리에 등록
- 개별 객체 생성 무관, 모든 객체가 공유
- 타입별로 default로 초기화함.
- 객체 생성과 무관하게 클래스 이름으로 접근
- 소멸시점 : 프로그램 종료 시


------------------------

## 메서드의 정의와 필요성
메서드란?
- 현실의 객체가 하는 동작을 프로그래밍화 한 것
- 어떤 작업을 수행하는 명령문의 집합
- 반복적으로 사용되느 코드 중복 방지
- 코드의 양을 줄일 수 있고 유지 보수가 용이함.
