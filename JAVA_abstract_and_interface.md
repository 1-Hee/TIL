# OOP 2

# 추상 클래스 (Abstract)
> 서로 다른 클래스 간의 공통 분모가 존재하면 공통된 것만을 구현한 부모 클래스를 상속 받아 구현하면 프로그래밍 하기 편해짐

```java

class Vehicle {
    private int curX, curY;

    public void reportPosition(){
        System.out.printf("현재 위치 : (%d, %d)\n", curX, curY);
    }

    public void addFuel(){
        System.out.println("모든 운송수단은 연료가 필요");
    }
}

class DieselSUV extends Vehicle {
    @Override
    public void addFuel(){
        System.out.printnln("주유소에서 주유!");
    }
}

class Tesla extends Vehicle {
    @override
    public void addFuel(){
        System.out.println("급속 충전!");
    }
}

```
> 이렇게 코드를 합쳐서 간결하게 만들어 버리면, 부모 클래스인 `Vehicle`의 메서드 `addFuel()`을 지워버리면 되지 않을까 생각하게 됩니다. 그러면 자식 클래스는 분명 부모 클래스의 `메서드`를 상속받아 `오버라이드` 한 것인데 그러면 상속의 이점을 누리지 못하게 됩니다. 이 때, 각각의 다른 클래스마다 `메서드`의 이름은 같으나 새로 `재정의:Overriding`할 것으로 예상되는 상황에서 부모 클래스의 메서드에 `abstract`를 추가하고 중괄호를 포함한 구현부를 지워버릴 수 있고, 이것은 상속의 이점과 서로 다르게 구현하여 사용할 수 있는 자율성의 이점을 모두 가져갈 수 있게 됩니다. 이러한 형태를 `abstract method design pattern`이라고 합니다.

```java

abstract class Vehicle {
    private int curX, curY;

    public void reportPosition(){
        System.out.printf("현재 위치 : (%d, %d)%n", curX, curY );
    }

    public abstract void addFuel();
}

```

## 추상 클래스의 특징
- `abstract` 클래스는 상속 전용의 클래스
- 클래스에 구현부가 없는 메서드가 있으므로 `객체를 생성할 수 없음.`
- 하지만 상위 클래스 타입으로써 자식을 `참조`할 수는 있다.
```java

// Vehicle v = new Vehicle(); abstract 클래스이므로 객체 생성 불가
Vehicle v = new DieselSUV(); // 가능!

```
- 부모 클래스에서 상속받은 abstract 메서드를 재정의하지 않은 경우 클래스 내부에 `abstract` 메서드가 있는 상황이므로 자식 클래스는 `abstract` 클래스로 선언되어야 함.

```java
class HorseCart extends Vehicle{}
```

- `Interface`에 있는 메서드 중 구현할 수 있는 메서드를 구현해 개발의 편의를 지원함.

-------------------------------

# Interface
## 인터페이스란?
> 서로 다른 두 시스템 장치, 소프트웨어 따위를 서로 이어주는 부분, 또는 그런 접속 장치

## 인터페이스 작성
- 최고 수준의 추상화 단계 : 일반 메서드는 모두 `abstarct` 형태
- JDK 8에서 `default method`와 `static method` 추가
- 클래스처럼 `interface` 선언 가능
- 모든 멤버 변수는 `public static final`이며 생략 가능
- 모든 메서드는 `public abstract` 이며 생략 가능

```java
public interface MyInterface{
    public static final int MEMBER1 = 10;
    int MEMBER2 = 10; // 같음
    
    public abstract void method1(int param);
    void method2(int param);
    
}

```

## 인터페이스 상속
- 클래스와 마찬가지로 인터페이스도 `extends`를 이용해 상속이 가능
- 클래스와 다른 점은 인터페이스는 다중 상속이 가능
- 헷갈릴 메서드의 `구현 자체`가 없으므로!

```java

interface Fightable{
    int fire();
}

interface Transformable{
    void changeShape(boolean isHeroMode);
}

public interface Heroable extends Fightable, Transformable {
    void upgrade();
}

```

## 인터페이스 구현과 객체 참조
- 클래스에서 `implements` 키워드를 사용해 `interface` 구현
- `implements` 한 클래스는
- 모든 `abstract` 메서드를 `override` 해서 구현하거나,
- 구현하지 않을 경우 `abstract` 클래스로 표시해야함.
- 여러 개의 `interface` 를 `implements` 가능

```java

public class IronMan implements Heroable{
    int weaponDamage = 100;

    @Override
    public int fire() {
        System.out.printf("빔 발사 %d", weaponDamage);
        return this.weaponDamage;
    }

    @Override
    public changeShape(boolean isHeroMode){
        String status = isHeroMode ? "장착" : "제거";
        System.out.printf("장갑 %s%n", status);
    }

    @Override
    public upgrade(){
        System.out.println("무기 성능 개선!");
    }    

}

```

- 다형성은 부모 `클래스` 뿐만 아니라 부모 `인터페이스`에도 적용이 됨.


## 인터페이스의 필요성
- 구현의 강제로 표준화 처리
- `abstract` 메서드를 사용함
- 인터페이스를 통한 간접적인 클래스 사용으로 손쉬운 모듈 교체 지원
- 서로 상속의 관계가 없는 클래스들에게 인터페이스를 통한 관계 부여로 다형성 확장
- 모듈 간 독립적 프로그래밍 가능 -> 개발기간 단축

## 서로 상속의 관계가 없는 클래스들에게 인터페이스를 통한 관계 부여로 다형성을 확장함.

```java
void baseCase(){

    Object[] objs = {
        new HandPhone(),
        new DigitalPhone()
    }
    for (Object obj : objs){
        if (obj instanceof HandPhone){
            HandPhone phone = (HandPhone) obj;
            phone.charge();
        } else if (obj instanceof DigitialCamera){
            DigitalCaemra camera = (DigitalCamera) obj;
            camera.charge();
        }
    }
}

void goodCase(){
    Chargeable[] objs = {
        new HandPhone(),
        new DigitalPhone()    
    }
    for (Chargeable obj : objs){
        obj.charge();
    }
}


```
## 독립적인 프로그래밍으로 개박기간 단축 됨.

```java
public interface Calculator {
    int add(int a, int b);
}

class CalculatorStub implements Calculator{
    public int add(int a, int b){
        System.out.printf("파라미터 확인 : %d , %d \n", a, b);
        return 0;
    }
}

// A팀 클라이언트를 위한 UI

class CaculatorClient{
    Calculator calcLogic = new CalculatorStub();
    public void add(){
        System.out.println("첫 번째 정수를 입력하시오 :");
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        System.out.println("두 번째 정수를 입력하시오 :");
        int b = sc.nextInt();        
        System.out.println("결과 %d+%d = %d\n", a,b,calcLogic.add(a,b));
    }
}

// B팀 계산의 로직 구현

public class CalculatorImpl implements Caculator{
    public int add(int a, int b){
        System.out.println("파라미터 확인 : %d, %d\n",a, b );
        return a+b;
    }
}

```

## default metohod
> 인터페이스에서 선언된 구현부가 있는 일반 메서드
- 메서드 선언부에 default modifier 추가 후 메서드 구현부 작성
- 접근 제한자는 `public` 으로 한정됨(생략 가능)

```java
interface DefaultMethodInterface {
    void abstractMethod();

    default void defaultMethod(){
        System.out.println("이것은 기본 메서드입니다.");
    }
    
}
```

## 필요성
- 기존의 `interface` 기반으로 동작하는 라이브러리의 `interface`에 추가해야 하는 기능이 발생
- 기존 방식으로라면, 모든 구현체들이 추가되는 메서드를 `override` 해야함.
- `default` 메서드는 `abstract`가 아니므로 반드시 구현해야할 필요는 없어짐.

## default method의 충돌
- JDK 1.7 이하의 java에서는 `interface method`에 구현부가 없으므로 충돌이 없었음
- 1.8 부터 `default method`가 생기면서 동일한 이름을 갖는 구현부가 있는 메서드가 충돌
- `method` 우선순위
- `super class의 method 우선` : super class가 구체적인 메서드를 갖는 경우 default method는 무시됨.
- `interface 간의 충돌` : 하나의 interfcae에서 default method를 제공하고 다른 interface에서도 같은 이름의 메서드(default 유무와 무관)가 있을 때 sub class는 반드시 override해서 충돌 해결.

## static method
- interface에 선언된 static method
- 일반 static 메서드와 마찬가지로 별도의 객체가 필요 없음
- 구현제 클래스 없이 바로 인터페이스 이름으로 메서드에 접근해서 사용 가능

```java
interface staticInter{
    static void staticMethod(){
        System.out.println("스태틱 메서드");
    }
}

public class Main{
    public static void main(String[] args){

        staticInter.staticMethod(); // 이렇게 사용가능!

    }
}

```

------------------------

# 제네릭 (Generic)
> 다양한 타입의 객체를 다루는 메섣, 컬렉션 클래스에서 `컴파일 시에 타입 체크`
- 미리 사용할 타입을 명시해서 형 변환을 하지 않오도 되게 함.

## 표현
- 클래스 또는 인터페이스 선언시 `<>`에 타입 파라미터 표시
```java
// example
public class Class_Name<T>{}
public class interface_Name<T>{}
// Class_Name : RawType
// Class_Name<T> : GenericType

```
> 타입 파라미터
- 특별한 의미의 알파벳 보다는 단순히 `임의의 참조형` 타입을 말함.
- `T : reference Type` 
- `E : Element` 
- `K : Key ` 
- `V : Value`

### 객체의 생성
> 변수 쪽과 생성 쪽의 타입은 반드시 같아야 함.
```java

Class_Name<String> generic = new Class_Name<String>();
Class_Name<String> generic2 = new Class_Name();
Class_Name generic = new Class_Name();

```
## 클래스의 생성
```java
class NormalBox{
    private Object some;

    public Object getSome(){
        return some;
    }

    public void setSome(Object some){
        this.some = some;
    }
}


class GenericBox<T>{
    private T Some;
    
    public T getSome(){
        return some;
    }

    public void setSome(T some){
        this.some = some;
    }
}

```

## 사용
> 컴파일 타입에 타입 `파라미터들이 대입된 타입`으로 대체!

```java

public class GenericBoxTest{
    
    public static void main(String[] args){
        GenericBox<Toy2> gBox1 = new GenericBox<>();
        
        gBox1.setSome(new Toy2());

        // gBox1.setSome(new Crocery2());

        Toy2 toy = gBox.getSome();
        // toy 사용

        GenericBox<Grocery> gBox2 = new GenericBox<>();
        gBox2.setSome(new Grocery2());
        Grocery2 grocery = gBox2.getsome();

    }

}

```

## type parameter의 제한
> 필요에 따라 구체적인 타입 제 한 필요
- 계산기 프로그램 구현 시 Number 이하의 타입 (Byte, Shor, Integer...)로만 제한
- type parameter 선언 뒤 extends와 함께 상위 타입 명시

```java
class NumberBox <T extends Number>{
    public void addSomes(T... ts){
        double d = 0;
        for (T t : ts) {
            d += t.doubleValue();
        }
        System.out.println("총 합은 " + d);
    }

}
// T는 Number를 상속받아야 한다.

public class ExtendsTest{
    public static void main(String[] args){
        NumberBox<Number> numBox = new NumberBox<>();
        numBox.addSomes(1.5, 5, 4L);

        NumberBox<Integer> intBox = new NumberBox<>();
        intBox.addSomes(1,2,3);

        // NumberBox<String> strBox = new NumberBox<>();

    }
}

```
- 인터페이스로 제한할 경우도 `extends` 사용
-` 클래스와 함께 인터페이스 제약 조건`을 이용할 경우 `&`로 연결.

```java

class TypeRes<T extends Clonable>{}
class TypeRes2<T extends & Clonale & Comparable<String>>{}

```
## Generic Type 객체를 `할당 받을 때` 와일드 카드를 이용.
- `generic type`에서 구체적인 타입 대신 사용

| 표현 | 설명 |
| ---- | ---- |
| Generic type<?> | 타입에 제한이 없음(Object)|
| Generic type<? extends T> | T 또는 T를 상속받은 타입들만 사용 가능 |
| Generic type<? super T> | T 또는 T의 부모타입만 사용 가능 |


```java

public class WildTypeTest{
    public void WildCardTest(){
        PersonBox<Object> pObj = new PersonBox<>();
        PersonBox<Person> pPer = new PersonBox<>();
        PersonBox<SpiderMan> pSpi = new PersonBox<>();

        PersonBox<?> pAll = pPer;
        pAll = pSpi;
        pAll = pObj;

        PersonBox<? extends Person> pChildPer = pPer;
        pChilPer = pSpi;
        // pChilPer = pObj;

        PersonBox<? super Person> pSuperPer = pPer;
        // pSuperPer = pSpi;
        pSuperPer = pObj;
            
    }
}

class Person {}
class SpiderMan extends Person{}
class PersonBox<T> {}


```

## Generic Method
- 파라미터와 리턴타입으로 `type parameter`를 갖는 메서드
- 메서드 리턴 타입 앞에 타입 파라미터 변수 선언

` 기본 양식`
```java
[제한자] <타입파라미터, [..]> 리턴_타입 메서드_이름(파라미터){ // do something 
}
```

`example`

```java
public class TypeParameterMethodTest<T>{
    T some;
    public TypeParaMeterMethodTest(T some){
        this.some = some;
    }

    public <P> void method1(P p){
        System.out.printf("클래스 레벨의 T : %s%n", some.getClass().getSimpleName());
                System.out.printf("파라미터 레벨의 P : %s%n", p.getClass().getSimpleName());
    }

    public <P> P method2(P p){ // public이고 제네릭은 P, 리턴타입은 P, 파라미터는 P타입의 p가 들어온다.
        return p;
    }

    public static void main(String[] args){
        TypeParaMeterMethodTest<String> tpmt = new TypeParaMeterMethodTest<>("Hello"); // 객체 생성 시 T 타입 결정
        tpmt.method1(10);
        tpmt.<Long>method2(20L); // 메서드 호출 시점에 P의 타입 결정
    }
}

```

## 다음 메서드 선언을 읽어보고 사용해봅시다.

```java

public interface List<E> extends Collection<E> {
    default void sort(Comparator<? super E>){
        ...
    }

    boolean addAll(int index, Collection<? extends E> c);
}

public class Collections {
    private static <T> T get(ListIterator<? extends T> i, int index){
        ...
    }

    public static <T> void copy(List<? super T> dest, List<? extends T> src){
        ...
    }
}


```

------------------------------------


# 예외처리 , 컬렉션 프레임 워크
## 예외의 처리
## 에러와 예외
> 어떤 원인에 의해 오동작 하거나 비정상적으로 종료되는 경우
- 심각도에 따른 분류
- Error
    - 메모리 부족, stack overflow와 같이 일단 발생하면 복구할 수 없는 상황
    - 프로그램의 비 정상적인 종료를 막을 수 없음 → 디버깅 필요
- Exception
    - 읽으려는 파일이 없거나 네트워크 연결이 안 되는 등 수습될 수 있는 비교적 상태가 약한 것들
    - 프로그램 코드에 의해 수습될 수 있는 상황
- Exception Handling(예외 처리)란
- 예외 발생 시 프로그램의 비정상 종료를 막고 정상적인 실행 상태를 유지하는 것
- 예외의 감지 및 예외 발생시 동작할 코드작성이 필요
- `Checked Exception`
    - 예외에 대한 대처 코드가 없으면 컴파일이 진행되지 않음.
- `Unchecked Exception` (RuntimeException의 하위 클래스)
    - 예외에 대한 대처 코드가 없더라도 컴파일은 진행됨.


`예외의 발생`

```java

public static void main(String[] args){
    int[] intArray = { 10 };
    System.out.println(intArray[2]);
    System.out.println("프로그램 종료합니다.");
}


```
## try ~ catch 구문

```java

try {

} catch (Exception e) { // 던진 예외를 받음

    // 예외가 발생했을 때 처리할 코드
}

```

```java

public static void main(String[] args){
    int[] intArray = { 10 };
    try {
        System.out.println(intArray[2]);
    } catch (ArrayIndexOutOfBoundsException e){
        System.out.println("예외가 발생했지만 처리함 : 배열 크기 확인 필요 ");
    }
    System.out.println("프로그램 종료합니다.");
}

```

## Exception 객체의 정보 활용
> Throwable의 주요 메서드

| 메서드 | 설명 |
| ---- | ---- |
| public String getMessage() | 발생된 예외에 대한 구체적인 메세지를 반환한다. |
| public Throwable getCause() | 예외의 원인이 되는 Throwable 객체 또는 null을 반환한다. |
| public void printStackTrace() | 예외가 발생된 메서드가 호출되기까지의 메서드 호출 스택을 출력한다. 디버깅의 수단으로 주로 사용된다. |

```java

int [] intArray = { 10 };
try {
    System.out.println(intArray[2]);
} catch (ArrayIndexOutOfBoundsException e){
    System.out.printf("Exception Handling : %s%n", e.getMessage());
    e.printStackTrace();
}
System.out.println("프로그램 종료합니다.");

```
## try-catch 문에서의 흐름
> try 블록에서 예외가 발생하면
- JVM이 해당 Exception 클래스의 객체 생성 후 던짐(throw)
    - throw new XXException()
- 던져진 exception 을 처리할 수 있는 catch 블록에서 받은 후 처리
- 적당한 catch 블록을 만나지 못하면 예외 처리는 실패
- 정상적으로 처리되면 try-catch 블록을 벗어나 다음 문장 진행
- try 블록에서 어떠한 예외도 발생하지 않은 경우
- catch 문을 거치지 않고 try-catch 블록의 다음 흐름 문장을 실행

```java

public static void main(String[] args){

    int num = new Random().nextInt(2);
    
    try {
        System.out.println("code 1 , num : " +num);
        int i = 1/num;
        System.out.println("code 2 - 예외 없음");
    } catch (ArithmeticException e){
        System.out.println("code 3- 예외처리 완료");
    }

    System.out.pritnln("code 4");

}

```

- num이 0일 때 출력되는 내용은?
- num이 1일 때 출력되는 내용은?


## 다충 Exception Handling
> try 블록에서 여러 종류의 예외가 발생할 경우
- 하나의 try 블록에 여러 개의 catch 블록 추가 가능
- 예외 종류별로 catch 블록 구성

```java
try{
    //exception이 발생할 만한 코드
} catch (XXException e){
    // XXException이 발생 시 처리 코드
} catch (YYException e){
    // YYException이발생 시 처리 코드
} catch (Exception e) {
    // Exception 발생 시 처리 코드
}

// 만약 예외 처리의 순서가 반대라면?

try{
    //exception이 발생할 만한 코드
} catch (Exception e) {
    // Exception 발생 시 처리 코드
} catch (YYException e){
    // YYException이발생 시 처리 코드
}  catch (XXException e){
    // XXException이 발생 시 처리 코드
}
```
- 다종 catch문 작성 순서 유의 사항
- JVM이 던진 예외는 catch문장을 찾을 때는 다형성이 적용됨
- 상위 타입의 예외가 먼저 선언되는 경우 뒤에 등장하는 catch 블록은 동작할 기회가 없음
`Unreachable catch block for Exception` 
- 상속 관계가 없는 경우는 무관
- 상속 관계에서는 작은 범위(자식)에서 큰 범위(조상) 순으로 정의

## 다중 예외 처리를 이용한 Checked Exception
## 처리하지 않으면 컴파일 불가 : Checked Exception

```java
public static void main(String[] args){
    Class.forName("abc.Def");
    new FileInputStream("Hello.java");
    DriverManager.getConnection("Hello");
    System.out.println("프로그램 정상 종료");
}

```
## 예외 처리는 가능한 구체적으로 진행

```java
public static void main(String[] args){
    try{
        Class.forName("abc.Def");
        new FileInputStream("Hello.java");
        DriverManager.getConnection("Hello");
        System.out.println("프로그램 정상 종료");        
    } catch (ClassNotFoundException e) {
        System.out.println("클래스 탐색 실패 "+e.getMessage());
    } catch (FileNotFountException e) {
        System.out.println("파일 탐색 실패 "+e.getMessage());
    } catch (SQLException e) {
        System.out.println("DB 접속 실패 "+e.getMessage());
    }
    System.out.println("프로그램 정상 종료");
}

```

## 발생하는 예외들을 하나로 처리하기
```java
try {
    // 다중 예외 발생 코드
} catch (Exception e) {
    System.out.println("예외 발생 %s%n", e.getMessage());
}

```
- 예외 상황 별 처리가 쉽지 않음
- 가급적 예외 상황 별로 처리하는 것을 권장

## 심각하지 않은 예외를 굳이 세분화 해서 처리하는 것도낭비
## '|' 를 이용해 하나의 catch 구문에서 상속관계가 없는 여러 개의 exception 처리

```java

public void exceptionHandling(){
   try{
        Class.forName("abc.Def");
        new FileInputStream("Hello.java");
        DriverManager.getConnection("Hello");
        System.out.println("프로그램 정상 종료");        
    } catch (ClassNotFoundException e | FileNotFountException e) {
        System.out.println("자원 탐색 실패 "+e.getMessage());
    } catch (SQLException e) {
        System.out.println("DB 접속 실패 "+e.getMessage());
    }
    System.out.println("프로그램 정상 종료");
}


```

## 다중 Exception Handling를 이용한 CheckedException 처리
- 계층을 이루는 예외의 처리

```java

public class HierarchyException {

    public static void main(String[] args){
        String src = "./project";

        try {
            FileInputStream input = new FileInputStream(src);
            int readData = -1;

            while ((readData = input.read()) != -1){
                System.out.println((char) readData);
            }
        } catch (FileNotFountException e){
            System.out.println(" 읽으려는 파일이 없습니다. %s%n", e.getMessage());

        } catch (IOException) {
            System.out.println("파일 읽기에 실패했습니다 : %s%n", e.getMessage());
        }
        System.out.println("파일 읽음 완료!");
    }
    
}


```

## try - catch - finally 구문을 이용한 예외 처리
> finally는 예외 발생 여부와 상관 없이 언제나 실행
- 중간에 `return을 만나는 경우`도 `finally 블록`을 먼저 수행 후 리턴 실행

```java
try{

} catch(Exception e){

} finally {

}

public static void main(String[] args){
    int num = new Random().nextInt(2);

    try {
        System.out.println("code 1, num :" + num);
        int i = 1 / num;
        System.out.println("code 2 - 예외 없음");
        return;
    } catch (ArithmeticExceptuon e){
        System.out.println("code 3 - exception handling");
    }  finally {
        System.out.println("code 4 - 언제나 실행");
    }
    System.out.println("code 5");
}

```
## finally를 이용한 자원 정리

```java

class IntallApp{
    void copy(){
        System.out.println("파일 복사");
    }
    
    void install() throws Exception {
        System.out.println("설치");
        if (Math.random() > 0.5){
            throw new Exception();
        }
    }

    void delete() {
        System.out.println("파일 삭제");
    }
}

```


```java

InstallApp app = new InstallApp();
try {
    app.copy();
    app.install();
    app.delete();
} catch (Exception e){
    app.delete();
    e.printStackTrace();
} 

InstallApp app = new InstallApp();
try {
    app.copy();
    app.install();
} catch (Exception e){
    e.printStackTrace();
} finally {
    app.delete();    
}
System.out.println("설치 종료");


```

- try 블록에서 사용한 리소스 반납
- 생성한 시스템 자원을 반납하지 않으면 장래 resource leak 발생 가능 → close 처리.

## finally에서 close를 통한 자원 반납

```java

public void useStream() {
    FileInputStream fileInput = null;
    try {
        fileInput = new FileInputStream("abc.txt");
        fileInput.read();
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if (fireInput != null){
            try {
                fileInput.close();
            } catch (IOExeption e){
                e.printStackTrace();
            }
        }
    }
}

```
- 지저분 할 수밖에 없는 finally 블록
- close 메서드 자체가 IOException 유발 가능
- FileInputStream 생성자에서 IOException 발생시 fileInput은 null 인 상황.

## try-with-resource
- JDK 1.7. 이상에서 리소스 자동 close 처리
```java
try (리소스_타입1 res1 = 초기화, 리소스_타입2 res = 초기화; ...){
    
}catch (Exception e){
    // exception handling 코드
}

```

- try 선언문에 선언된 객체들에 대해 자동 close 호출 (finally 역할)
- 단 해당 객체들이 AutoCloseable interface를 구현할 것
- 각종 I/O stream, socket, connection ...
- 해당 객체는 try 블록에서 다시 할당될 수 없음

```java

public void useStreamNewStye(){
    try (FileInputStream fileInput = new FileInputStream("abc.txt")){
        System.out.println("FileInputStream이 생성되었습니다.");
        fileInput.read();
    } catch (IOException e){
        System.out.println("파일 처리 실패");
    }
}

```

--------------------------------------

## throws 활용
## throws 키워드를 통한 처리 위임
- method에서 처리해야할 하나 이상의 예외를 호출한 곳으로 전달(처리 위임)
- 예외가 없어지는 것이 아니라 단순히 전달됨
- 예외를 전달받은 메서드는 다시 예외처리의 책임 발생

```java
void exceptionMethod() throws Exception1, Exception2{
    // 예외 발생 코드
}

void methodCaller() {
    try {
        exceptionMethod();
    } catch (Exception e){}
}

```
- 처리하려는 예외의 조상 타입으로 `throws` 처리 가능

## checked exception괴 throws

```java
public static void main(String[] args){
    CheckedThrowsTest et = new CheckedThorwsTest();
    try {
        et.method();
    } catch (ClassNotFountException e) {
        System.out.printf("exception handling : %s%n", e.getMessage());
    }
    System.out.println("프로그램 종료")
}

public void method1() throws ClassNotFoundException{
    method2();
}

public void method2() thorws ClassNotFoundException{
    Class.forName("Some Class");
}


```

- Checked Exception은 반드시 try-catch 또는 throws 필요
- 필요한 곳에서 try~catch 처리

## runtime exception 과 throws

```java

public static void main(String[] args){
    
    RuntimeThorwsTest et = new RuntimeThrowsTest();
    try{
        et.method1();
    } catch (ArimeticException e) {
        System.out.println("예외 처리 : %s%n", e.getMessage());
    }
    System.out.println("프로그램 종료");
}

public void method1() {
    method2();
}

public void method2() {
    int i = 1/0;            // ArimeticException 발생
}

```

- runtime exception은 thorws 하지 않아도 전달되지만
- 하지만 결국은 try~catch로 처리해야 함.

## 로그 분석과 예외의 추척
- Throwable의 printStackTrace는 메서드 호출 스택 정보 조회 가능
- 최초 호출 메서드에서부터 예외 발생 메서드 까지의 스택 정보 출력

꼭 확인해야할 정보
- 어떤 예외인가? - 예외 종류
- 예외 객체의 메세지는 무엇인가? - 예외 원인
- 어디서 발생했는가 ? - 디버깅 출발점
- 직접 작성한 코드를 디버깅 대상으로 삼을 것
- 참조하는 라이브러리는 과감히 건너뛰기!

## throws의 목적과 API 활용
- API가 제공하는 많은 메서드들은 사전에 예외가 발생할 수 있음을 선언부에 명시하고 프로그래머가 그 예외에 대처 하도록 강요함.

## 메서드 재정의와 throws
> 메서드 재정의 시 조상 클래스 메서드가 던지는 예외보다 부모 예외를 던질 수 없다.
- 부모가 치지 않은 사고를 자식이 칠수 없다.

```java

class Parent{
    void methodA() throws IOException {}
    void methodB() throws ClassNotFound {}
}

public class OverridingTest extends Parent {
    @Override
    void methodA() throws FileNotFoundException{

    }

    @Override
    void methodB() throws Exception { // 상위 Error..

    }

}

```

-------------------------------------

## 사용자 정의 예외
> API에 정의된 Exception 이외에 필요에 따라 사용자 정의 예외 클래스 작성

- 대부분 Exception 또는 RuntimeException 클래스 상속받아 작성
- Checked Exception 활용 : 명시적 예외 처리 또는 throws 필요
- 코드는 복잡해지지만 처리누락 등 오류 발생 가능성은 줄어듦
- Runtime Exception 활용 : 묵시적 예외 처리 가능
- 코드가 간결해지지만 예외 처리 누락 가능성 발생.

`사용자 정의 예외를 만들어 처리하는 장점`
- 객체의 활용 : 필요한 추가정보, 기능 활용 가능
- 코드의 재사용 : 동일한 상황에서 예외 객체 재사용 가능
- throws 메커니즘의 이용 : 중간 호출 단계에서 return 불필요


```java

public class UserExceptionTest{
    private static String[] fruits = {"사과", "오렌지", "토마토"};
    public static void main(String[] args){
        boolean result = getFruit1("사과");
        if(!result){
            System.out.println("사과는 없습니다.");
        }
        result = getFruit1("사과");
        if(!result){
            System.out.println("사과는 없습니다.");
        }
        System.out.println("창고 관리 끝");
    }

    private static boolean getFruit1(String name){
        for (int i = 0 ; i < fruits.length; i++){
            if(fruits[i] != null && fruits[i].equals(name)){
                fruits[i] = null;
                return true;
            }
        }
        return false;
    }
}

```

```java

class FruitNotFoundException extends Exception {
    public FruitNotFoundException(String name){
        super(name + "에 해당하는 과일은 없습니다");
    }
}

public class CustomExceptionTest{
    private static String[] fruits = {"사과", "오렌지", "토마토"};
    public static void main(String[] args){
        try{
            getFruit2("오렌지");
            getFruit2("오렌지");
        } catch (FruitNotFoundException e){
            e.printStackTrace();
        }
    }


    private static void getFruit2(String name) throws FruitNotFoundException{
        for (int i = 0 ; i < fruits.length ; i ++){
            if(fruits[i] != null && fruits[i].equals(name)){
                fruits[i] = null;
                return;
            }
        }
        throw new FruitNotFoundException(name);
    }

}

```

`아래 코드에 대한 여러분의 생각은?`

```java
public void method(String[] args, String name, int divisor){
    try{
        System.out.println(args[0]);
        System.out.println(name.length());
        System.out.println(1/divisor);
    } catch (Exception e){
        // 에러 발생!
    }
}

public void method2(String[] args, String name, int divisor){
    if (args != null && args.length > 1){
        System.out.println(args[0]);
    }

    if (name != null){
        System.out.println(name.length());
    }

    if (divisor != 0){
        System.out.println(1 / divisor);
    }
}


```

-------------------------------------

## List 계열

자료구조(data structure)는 컴퓨터 과학에서 효율적인 접근 및 수정을 가능케 하는 자료의 조직, 관리, 저장을 의미한다. 더 정확히 말해, 자료 구조는 데이터 값의 모임, 또 데이터 간의 관계, 그리고 데이터에 적용할 수 있는 함수나 명령을 의미한다.

`배열`
- 가장 기본적인 자료 구조
- homogenous collection : 동일한 데이터 타입만 관리 가능
- 타입이 다른 객체를 관리하기 위해서는 매번 다른 배열 필요

`Polymorphism`
- Object를 이용하면 모든 객체 참조 가능 -> Collection FrameWork
- 담을 때는 편리하지만, 빼낼 때는 Object로만 가져올 수 있음
- 런타임에 실제 객체의 타입 확인 후 사용해야 하는 번거로움
- Generic을 이용한 타입 한정
- 컴파일 타임에 저장하려는 타입 제한 → 형변환의 번거로움 제거


## `java.util 패키지`
- 다수의 데이터를 쉽게 처리하는 방법 제공 -> DB 처럼 CRUD 기능 중요
- collection framework의 핵심은 `interface`

|interface | 특징|
| ---- | ---- |
| list | 순서가 있는 데이터의 집합, 순서가 있으므로 데이터의 중복을 허용, 일렬로 줄서기, ArrayList, LinkedList |
| Set | 순서를 유지하지 않는 데이터의 집합. 순서가 없어서 같은 데이터를 구별할 수 있음 -> 중복을 허락하지 않음, ex) 알파벳이 한 종류씩 있는 주머니, HashSet, TreeSet|
| Map | key와 value의 쌍으로 데이터를 관리하는 집합, 순서는 없고 key의 중복 불가, value는 중복 가능, HashMap, TreeMap |

## `Collection 기능`

| 분류 | Collection |
| ---- | ---- |
| 추가 | add(E, e) |
| 추가 | addAll(Collection <? extends E> c) |
| 조회 | contains(Object o) |
| 조회 | containsAll(Collection<?> c) |
| 조회 | equals() |
| 조회 | isEmpty() |
| 조회 | iterator() |
| 조회 | size() |
| 삭제 | clear() |
| 삭제 | removeAll(Collection<?> c) |
| 삭제 | retainAll(Collection<?> c) |
| 기타 | toArray() |

## Collection vs List 메서드 비교

| 분류 | Collection | List |
| ---- | ---- | ---- |
| 추가 | add(E, e) | add(int index, E element) |
| 추가 | addAll(Collection <? extends E> c) | addAll(int index, Collection<? extends E> c) |
| 조회 | contains(Object o) | get(int index) |
| 조회 | containsAll(Collection<?> c) | indexOf(Object o) |
| 조회 | equals() | lastIndexOf(Object o) |
| 조회 | isEmpty() | listIterator() |
| 조회 | iterator() | x |
| 조회 | size() | x |
| 삭제 | clear() | remove(int index) |
| 삭제 | removeAll(Collection<?> c) | x |
| 삭제 | retainAll(Collection<?> c) | x |
| 수정 | x | set(int index, E element) |
| 기타 | toArray() | subList(int fromindex, int toIndex) |


## 주요 메서드

```java
List<String> friends = new ArrayList<>();

public void createTest() {
    freinds.add("홍길동");
    freinds.add("홍길동"); // 동일 데이터 추가
    freinds.add("장길산");
    freinds.add("임꺽정");
    freinds.add(0, "이몽룡"); // 끼워 넣기
    System.out.println("추가 후 내용 출력 : " friends);
}

```

## `ArrayList 소스 코드 분석`

```java
// 생성자, constructor
public ArrayList(int initialCapcity) {
    if (initialCapacity>0){
        this.elementData = new Object[initialCapacity];
    } else if (initialCapacity == 0){
        this.elementData = EMPTY_ELEMENTDATA;
    } else {
        throw new IllegalArgumentException("Illegal Capacity " + initialCapacity);
    }
}

public ArrayList() {
    this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA; // {}
}

// add >> ensureCapacityInternal >> ensureExplicitCapacity >> grow

private void grow(int minCapcity){
    // overflow - conscious code
    int oldCapacity = elementData.length;
    int newCapacity = oldCapacity + (oldCapacity >> 1);
    if(newCapacity - minCapacity < 0){
        newCapacity = minCapacity;
    }
    if(newCapactiy - MAX_ARRAY_SIZE > 0){
        newCapacity = hugeCapacity(minCapacity);
    }
    elementData = Arrays.copyOf(elementData, newCapacity);
}


```


## `배열과 ArrayList`
## 배열의 장점
- 가장 기본적인 형태의 자료 구조로 간단하며 사용이 쉬움
- 접근 속도가 빠름

## 배열의 단점
- 크기를 변경할 수 없어 추가 데이터를 위해 새로운 배열을 만들고 복사해야 함
- 비 순차적 데이터의 추가, 삭제에 많은 시간이 걸림.
- 배열을 사용하는 ArrayList도 태생적으로 배열의 장-단점을 그대로 물려받음.

## LinkedList
> 각 요소를 Node로 정의하고, Node는 다음 요소의 참조 값과 데이터로 구 성
- 각 요소가 다음 요소의 링크 정보를 가지며, 연속적으로 구성될 필요가 없다.

## LinkedList와 ArrayList의 비교

| 구분 | 순차적 데이터 100만 건 | 비순차적 데이터 10만건 | 조회 10만건 |
| ---- | ---- | ---- | ---- |
| ArrayList | 빠름 | 느림 |  빠름 |
| LinkedList | 느림 | 빠름 | 느림 |

`결론`
- 특정 클래스가 좋고 나쁨이 아니라 용도에 따라 적합하게 사용해야 함.
- 소량의 데이터를 가지고 할 경우에는 큰 차이 없음
- 정적인 데이터 활용, 단순한 데이터 조회용 : ArrayList
- 동적인 데이터 추가, 삭제가 많은 작업 : LinkedList

## 자료 삭제시 주의사항
## `Index를 이용한 for문`

```java
List<Integer> nums = new ArrayList<>();
Random rand = new Random();

for (int i = 0; i < 10 ; i +=){
    nums.add(rand.nextInt(20));
}
System.out.println("전체 :" + nums);

for (int i = 0 ; i < nums.size ; i ++){
    if(nums.get(i)%2 == 0){
        nums.remove(i);
        i--;
    }
}
System.out.println("짝수 삭제 후 : " + nums);


```

- 요소가 삭제되면 size가 줄기 때문에 index 차감 필요
- 거꾸로 접근하면 해결 가능

```java
for (int i = nums.size()-1; i>=0 ; i--){
    if(nums.get(i)%2 ==1){
        nums.remove(i);
    }
}

```
## `for-each 문은 중간에 삭제하면 오류남!!`
--------------------------------------

## Set 계열
## Set Interface
## `특징`
- 순서 없이 주머니에 구슬(데이터)을 넣는 형태
- 순서가 없으므로 데이터를 구별할 index가 없어 데이터의 중복이 허용되지 않음. (효율적인 중복데이터 삭제 수단)


## Set API의 활용

```java
public class SetTest {
    set<Object> hset = new HashSet<Object>();
    private void addMethod(){
        hset.add(new Integer(1));
        hset.add("Hello");
        hset.add("Hello"); // 동ㅇ리한 데이터 추가 확인
        hset.add(1); // 기본형은 wrapper를 통해 추가
        System.out.println("데이터 추가 결과" + hset);
    }

    private void retireveMethod(){
        System.out.println("데이터 개수 : " + hset.size());

        for (Object sboj : hset){
            System.out.println("데이터 조회 : " + sobj);
        }
    }

    private void removeMethod(){
        hset.remove("Hello");
        System.out.println("데이터 삭제 결과 : " + hset);
    }

    public static void main(String[] args){
        SetTest test = new setTest();
        test.addmethod();
        test.retireveMethod();
        test.removeMethod();
    }
}

```
## 동일한 데이터의 기준

`SmartPhone도 Set에 삽입해보기`

```java
class SmartPhnoe{
    String number;
    public SmartPhone(String number){
        this.number = number;
    }

    public String toString(){
        return "전화 번호 : " + number;
    }
}

```

- 동일한 데이터의 기준은 객체의 equals()가 true를 리턴하고 hashCode() 값이 같을 것.

```java
public boolean equals(Object obj){
    boolean result = false;
    if (obj != null && obj instanceof SamePhone){
        SamePhone param = (SamePhone) obj;
        result = (this.number.equals(params.number));
    }
    return result;
}

public int hashCode(){
    return number.hashCode();
}

```


--------------------------------------

## Map 계열
- Key와 Value를 하나의 Entry로 묶어서 데이터 관리
- Key : Object 형태로 데이터 중복 X
- Value : object 형태로 데이터 중복 OK

## `Map interface 메서드`

| 분류 | Map |
| 추가 | put(K key, value) |
| 추가 | putAll(Map<? extends K, ? extends V> m) |
| 조회 | contiansKey(Object key) |
| 조회 | containsValue(Object value) |
| 조회 | entrySet() |
| 조회 | keySet() |
| 조회 | get(Object key) |
| 조회 | values() |
| 조회 | size() |
| 조회 | isEmpty() |
| 삭제 | clear() |
| 삭제 | remove(Object key) |
| 수정 | put(K key, V value) |
| 수정 | putAll(Map<? extends K, ? extends V> m) |


## Map interface의 주요 메서드

```java

Map<String, String> hMap = new HashMap<>();

private void addMethod() {
    System.out.println("추가 성공 ? : " + hMap.put("andy", "1234"));
    System.out.println("추가 성공 ? : " + hMap.put("andy", "1234"));

    hMap.put("kate", "9999");

    hMap.putIfAbsent("kate", "1245");

    hMap.put("henry", "4567");

    System.out.println("추가 결과 " + hMap);


}

```

## 정렬
- 요소의 특정 기준에 대한 내림차 순 또는 오름차 순으로 배치
- 순서를 가지는 `Collection`들만 정렬 가능
- `List 계열`, `SortedSet`, `SortedMap` 가능
- Collections의 sort()를 통하 정렬
` sort(List<T> list)`
- 객체가 Comparable을 구현하고 있는 경우 내부 알고리즘으로 정렬


## 정렬
> SmartPhone의 정렬 처리
```java
public void sortPhone(){
    List<SmartPhone> phones = Arrays.asList(new SmartPhone("010"), new SmartPhnoe("011"), new SmartPhnoe("000"));
    Collection.sort(phones);
}

@SuppressWarning("unchecked")
public static <T extends Comparable<? super T>> void sort(List<T> List){}


// 언제나 정렬 가능한 요소들

public final class String implements java.io.Serializable, Comparable<String>, CharSequence { ... }
public final class Integer extends Number implements Comparable<Integer> {...}


```

## 정렬 
```java
// Comparable interface

public interface Comparable<T>{
    public int comparTo(T o);
}

// SmartPhone 정렬 처리

public class SmartPhone implements Comparable<SmartPhone> {
    String number;

    @Override
    public int compaerTo(SmartPhone o){
        return this.number.compareTo(o.number);
    }
}

public void sortPhone(){
    List<SmartPhone> phones = Arrays.asList(new SmartPhone("010"), new SmartPhone("011"), new SmartPhone("000"));
    Collection.sort(phones);
    System.out.println(phones);
}


```

## Comparator의 활용
- 객체가 Comparable을 구현하고 있지 않거나 사용자 정의 알고리즘으로 정렬하려 하는 경우
- String을 알파벳 순이 아닌 글자 수 별로 정렬하려면?
- sort(List<t> list, Comparator<? super T> c)

```java

public interface Comparator<T> {
    int compare(T o1, T o2);
}

public class StringLengthComparator implements Comparator<String> {
    @Override
    public int compare(String o1, String o2){
        int len1 = o1.length();
        int len2 = o2.length();
        return Integer.compaer(len1, len2);

    }
}

public void stringLengthSort(){
    Collections.sort(names, new StringLengthCompartor());
    System.out.println(names); 
}

```
- 1회성 객체 사용 시 anonymous inner class 사용
- 클래스 정의, 객체 생성을 한번에 처리

```java

Collections.sort(names, new StringLengthComparator());

Collections.sort(names, new Comparator<String>{
    @override
    public int compare(String o1, String o2){
        return Integer.compare(o1.length(), o2.length());
    }

    
});


```

## 람다 표현식 사용
```java

Collections.sort(names, (o1, o2) -> {
    return Integer.compare(o1.length(), o2.length());
});

```






--------------------------------------


