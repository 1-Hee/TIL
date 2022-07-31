# JAVA의 객체지향 (Object Oriented Programing)
# 1. 상속
> OOP is A, P, I, E

| 특성 | 내용 |
| ---- | ---- |
| 추상화(Abstraction) | 현실의 객체를 추상회해서 클래스를 구성한다.|
| 다형성(Polymorphism) | 하나의 객체를 여러 가지 타입으로 참조할 수 있다. |
| 상속(Inheritacnce) | 부모 클래스의 자산을 물려 받아 정의함으로 코드의 재사용이 가능하다. |
| 캡슐화, 데이터 은닉과 보호(Encapsulation) | 데이터를 외부에 직접 노출시키지 않고 메서드를 이용해 보호할 수 있다. |

- 기존 클래스의 자산(멤버)을 자식 클래스에서 재사용하기 위한 것
- `부모 생성자의 초기화 블록은 상속하지 않는다.`
- 기존 클래스의 멤버를 물려 받기 때문에 코드의 절감
- 부모의 코드를 변경하면, 모든 자식들에게도 적용 (유지 보수성 향상)
- 상속의 적용 = extends 키워드 사용

```java

public class Person {
    String name;

    void eat() {}
    void jump() {}
    
}

public class SpierMan extends Person {
    boolean isSpider;
    void fireWeb(){}
}

```

## Object 클래스
> 모든 클래스의 조상클래스 (최상위 클래스)
- 별도의 extends 선언이 없는클래스들은 extends Object가 생략된 것
- 따라서 모든 클래스에서는 Object 클래스에서 정의된 메서드가 있음.
- 상속의 관계는 is a 관계여야 함.
- Person is a Object, Spider is a Person

`생각해볼 관계`
- Person과 Employee?
- Object와 Employee?
- Employee와 SiperMan?

## 단일 상속 (Single Inheritance)
> JAVA는 단일 상속!

- 다중 상속이 허용되면, 여러 클래스의 기능을 물려받을 수 있으나 관계가 매우 복잡해짐.
- `Java`는 단일 상속만 지원함
- 대신 Interface와 포함 관계 (has a)로 단점 극복

## 포함 관계
- 상속 이외에 클래스를 재활용 하는 방법
- 2개 이상의 클래스에서 특성을 가져올 때 하나만 상속, 나머지는 멤버 변수로 처리
- 포함 관계의 UML 표현은 실선
- Spider의 코드를 수정하면 SpiderMan에도 반영되므로 유지 보수성 확보

```java
public class SpiderMan2 extends Person{
    Spider spider;
    boolean isSpider;
    
    void fireWeb() {
        if (isSpider) {
            spider.fireWeb();
        } else {
            System.out.println("Person은 거미줄 발사 불가")
        }
    }
}

```

- 상속이냐 포함이냐 그것이 문제로다.
- 어떤 클래스를 상속 받고 어떤 클래스를 포함해야 하는가?
- `상속` : is 관계가 성립하는가?
- `포함` : has 관계가 성립하는가?

--------------------------

# 2. 메서드 재정의(오버라이딩, overriding)
> 조상 클래스의 정의된 메서드를 자식 클래스에서 적합하게 수정하는 것

```java
public class Person{
    void jump(){
        System.out.println("두 다리로 힘껏 점프");
    }
}

public class Spider { 
    void jump() {
        System.out.println("키 * 1000만큼 엄청난 점프");
    }
}

// Person과 Spider 의 jump()는 각각 다른 메서드!

public class SpiderMan2 extends Person {
    Spider spider = new Spider();
    boolean isSpider;
}

```

## 메서드 오버라이딩(overriding)

```java

public class Person {
    void jump(){
        System.out.println("두 다리로 힘껏 점프");
    }
}

public class Spider {
    void jump(){
        System.out.println("키 * 1000만큼 엄청난 점프");
    }
}

// 오버라이딩 

public class SpiderMan2 extends Person{
    Spider spider = new Spider();
    boolean isSpider;

    void fireWeb(){}
    void jump(){
        if (isSpider){
            spider.jump()
        } else {
            System.out.println("두 다리로 힘껏 점프");
        }
    }
}

```
`오버라이딩의 조건`
- 메서드 이름이 같아야 한다.
- 매개 변수의 개수, 타입, 순서가 같아야 한다.
- 리턴 타입이 같아야 한다.
- 접근 제한자는 부모 보다 범위가 넓거나 같아야 한다.
- 조상보다 더 큰 예외를 던질 수 없다.

## Annotation
- 사전적 의미 : `주석`
- 컴파일러, JVM, 프레임워크 등이 보는 주석
- 소스코드에 메타 데이터를 삽입하는 형태
- 소스코드에 붙여놓은 라벨
- 코드에 대한 정보 추가 
- 소스 코드의 구조 변경, 환경 설정 정보 추가 등의 작업 진행

`JDK 1.5의 기본 annotation의 예`
1. `@Deprecated`
    - 컴파일러에게 해당 메서드가 deprecated 되었다고 알려줌
2. `@Override`
    - 컴파일러에게 해당 메서드는 override한 메서드임을 알려줌
    - @Override 가 선언된 경우 반드시 super class에 선언되어 있는 메서드어야 함.
3. `@SuppressWarnings`
    - 컴파일러에게 사소한 warning의 경우 신경 쓰지 말라고 알려줌

## Object 클래스
> 가장 최상위 클래스로 모든 클래스의 조상
- Object의 멤버는 모든 클래스의 멤버

```java
// toString()은 Object의 메서드

System.out.println(person.toString()); // 주소값!

System.out.println(spiderMan.toString()); // 주소값!

```

## toString 메서드
> 객체를 문자열로 변경하는 메서드 (주소값을 반환)

```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHextString(hashCode());
}

// 정작 궁금한 것은 주소 값이 아니라 내용을 원함.

@Override
public String toString() {
    return "SpiderMan [isSpider = " + isSpider + ", name = " + name + "]";
}

```

## equals 메서드
> 두 객체가 같은 비교하는 메서드

```java
public boolean equals(Object obj){
    return (this == obj);
}
```

> 두개의 레퍼런스가 변수가 같은 객체를 가리키고 있는가?

```java

Object obj1 = new Object(); // 새로운 주소 값을 가짐
Object obj2 = new Object(); // 새로운 주소 값을 가짐
Object obj3 = obj2; // obj2 의 주소 값을 복사함 = obj2의 주소값

```
`equals 메서드`
> 우리가 비교할 것은 정말 객체의 주소 값인가?
두 객체의 내용을 비교할 수 있도록 `equals` 메서드 재정의

```java
private static void testString(){
    String s1 = new String("Hello");
    String s2 = new String("Hello");
    System.out.println((s1 == s2) + " : " + s1.equals(s2));

}

private static void testPhone() {
    Phone p1 = new Phone("01000000");
    Phone p2 = new Phone("01000000");
    System.out.println((p1 == p2) + " : " + p1.equals(p2));

}

class Phone {
    String number = "전화번호";

    public Phone(String number){
        this.number = number;
    }
}

```
- 객체의 주소 비교 : `==`
- 객체의 내용 비교 : `equals` 재정의

## hashCode
- 객체의 해쉬 코드 : 시스템에서 객체를 구별하기 위해 사용되는 정수 값
- HashSet, HashMap 등에서 객체의 동일성을 확인하기 위해 사용
- equals 메서드를 재정의 할때는 반드시 `해쉬코드`도 재정의 할 것
- 미리 작성된 String이나 Number 등에서 재정의된 `hashCode` 활용 권장

## Object의 메서드 재정의

```java
class Product {
    String sn;
    public Product(String sn){
        this.sn = sn;
    }
    
    @Override
    public boolean equals(Object obj){
        if (obj != null && obj instanceof Product){
            Product casted = (Product) obj;
            return sn.equals(casted.sn);
        }
        return false;
    }

    @Override
    public String toString(Object obj){
        return "Product [ sn = " + sn + " ]";
    }

    @Override
    public int hashCode(){
        return sn.hashCode();
    }
}

```

`super 키워드`
> this 통해 멤버에 접근했듯이 super를 통해 조상 클래스 멤버 접근

- `super` 을 이용해 조상의 메서드 호출로 조상의 코드 재사용

```java
void jump() {

    if (isSpider){
        spider.jump();
    } else {
        System.out.println("뛰기");
    }

}

void jump() {

    if (isSpider){
        spider.jump();
    } else {
        super.jump();
    }

}


```

## 변수의 Scope
> 사용된 위치에서 점점 확장해가며 처음 만난 선언부에 연결됨

- method 내부 → 해당 클래스 멤버 변수 → 조상 클래스 멤버 변수


```java

class Parent{
    String x = "parent";
}

class Child extends Parent {
    String x = "Child";

    void method(){
        String x = "method";
        System.out.println("x :" + x);
        System.out.println("this.x : "+this.x);
        System.out.println("this.x : "+super.x);

    }
}

public class ScopeTest {
    public class void main(String[] args){
        Child child = new Child();
        child.method();
    }
}


```

💡 생각해 볼 포인트!
- 현재 상태에서 출력 결과 예상하면?
- method의 x를 주석한다?
- child의 x를 주석하면?

-----------------------



## super 키워드
- `this()`가 해당 클래스의 다른 생성자를 호출하듯 `super()`는 조상 클래스의 생성자 호출
- 조상 클래스에 선언된 멤버들은 조상 클래스의 생성자에서 초기화가 이뤄지므로 이를 재활용
- 자식 클래스에 선언된 멤버들만 자식 클래스 생성자에서 초기화
- [💡중요] `super()`는 자식 클래스 생성자의 맨 첫 줄에서만 호출 가능
- 즉 생성자의 첫 줄에만 `this()` 또는 `super()` 가 올 수 있다.
- 명시적으로 `this()` 또는 `super()`를 호출하지 않는 경우 컴파일러 `super()` 삽입
- 결론적으로 맨 상위의 `Object`까지 객체가 다 만들어지는 구조

`생성자의 호출과 객체 생성의 단계`

```java
class Person2 {
    String name;
    
    Person2(String name){
        // super(); >> Object의 기본 생성자 호출
        this.name = name;
    }
}

public class SpiderMan3 extends Person2 {
    Spider spider = new Spdier();
    boolean isSpider;

    SpiderMan3(String name, Spider spider, boolean isSpider){
        super(name);
        this.spider = spider;
        this.isSpider = isSpider;
    }

    SpiderMan3(String name){
        this(name, new Spider(), true);
    }

    public static void main(String[] args){
        SpiderMan3 sman = new SpiderMan3("피터 파커");
    }
    
}

```

------------------------------
# 3. Package & Import
## Package
> PC의 많은 파일 관리 → 폴더를 이용
- 유사한 목적의 파일을 기준으로 작성
- 이름은 의미 있는 이름으로 계층적으로 접근

> 프로그램의 많은 클래스 → 패키지를 이용
- 패키지의 이름은 의미 있는 이름으로 만들고, .를 통해 계층적 접근
- 물리적으로는 패키지는 클래스 파일을 담고 있는 디렉토리

> package의 선언
`package packge_name;`
- 주석, 공백을 제외한 첫 번째 문장에 하나의 패키지만 선언
- 모든 클래스는 반드시 하나의 패키지에 속한다.
- 생략 시 `default package`
- `default package` 는 선언하지 않는다.

`패키지의 일반적인 naming rule`
```java
com.ssafy.hrm.common
// 회사identity.project.용도 느낌으로 작명.
```

## import
> 다른 패키지에 선언된 클래스를 사용하기 위한 키워드
- 패키지와 클래스 선언 사이에 위치
- 패키지와 달리 여러 번 선언 가능

> 선언 방법
- import 패키지명.클래스명;
- import 패키지명.*; // 하위패키지까지 모두 설치.
- import한 package의 클래스 이름이 동일하여 명확히 구분이 필요할 경우에만 구분함.
- 클래스 이름 앞에 전체 패키지 명을 입력함.
`ex) java.util.List list = new java.util.ArrayList();`
- default import package : `java.lang*;`

🏷 빠르게 `import`하는 법 `Ctrl + Shift + O`

## 일반적인 클래스의 레이아웃
```
패지키 선언부       package structure;
외부 패키지 import  import java.io.*;
class 선언부        public class ClassStructrue{
멤버변수                String name;
                        int age;
초기화 블록             {name = "andy";}
생성자                  public classStructrue(String name, int age) {
                            this.name = name
                            this.age = age
                        }
멤버 메서드             public void setName(String name){
                            this.name = name;
                        }

                        public static void main(String[] args) {
                            ClassStructure st = new ClassStructue("hong", 10);
                        }

                    }

```

----------------------


# 4. 접근제한자와 데이터 은닉과 보호

## 제한자(modifier)
> 클래스, 변수, 메서드 선언부에 함께 사용되어 부가적인 의미 부여

`종류`
- 접근제한자 : public, protected, (default=package), private
- 그외 제한자
    - static : 클래스 변수 or 클래스 메서드로 한정
    - final : 요소를 더 이상 수정할 수 없게 함.
    - abstract : 추상 메서드 및 추상 클래스 작성
    - synchronized : 멀티 스레드에서의 동기화 처리

- 하나의 대상에 `여러 제한자`를 조합 가능하나, `접근 제한자`는 `하나`만 사용 가능
- `순서는 무관하다`
- 일반적으로 접근 제한자를 맨앞으로 둠.

## final
> 마지막, 더이상 바꿀 수 없음
> 확장을 못하게 막는다기보다, 실수를 안하게 돕는 것.

`final class`
- 더 이상 확장 할 수 없음 
- 상속 금지 → 오버라이드(override) 방지
- 이미 완벽한 클래스들 : String, Math 등...

`final method`
- 더이상 재정의할 수 없음
- overriding 금지

`final variable`
- 더 이상 값을 바꿀 수 없음 : 상수화


## 접근제한자(Access modifier)
> 멤버 등에 사용되며, 해당 요소를 외부에서 사용할 수 있는 지 설정

| 제한자 | 클래스 | 생성자 | 멤버 | 같은 클래스 | 같은 패키지 | 다른 패키지의 자식 클래스 | 전체 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| public | O | O | O | O | O | O | O |
| protected | X | O | O | O | O | O | X |
| package |  O | O | O | O | O | X | X |
| private | X |  O | O | O | X | X | X |


## 접근 제한자 (Access)
> method override 조건의 확인
- 부모의 제한자 범위와 같거나 넓은 범위로만 사용 가능

```java
class Parent{
    protected void method(){}
}

public class OverrideRule extends Parent{
    @Override
    void method() {}
    
    protected void method() {}

    public void method() {}
}

```

## 데이터 은닉과 보호(Encapsulation)
- 외부로 부터 쉽게 데이터가 바뀌거나 조작되는 것을 방지
- 외부에서 클래스를 통해 직접 접근 가능하게 되면 누구나 수치를 조작할 수 있음.
- 정보를 보호하기 위해 private로 접근을 막고, 공개된 메서드를 통해 접근할 통로를 마련함.
- setter / getter

```java

class UserInfo {
    private String name = 'j'
    private int account = 10000;
    public String getName(){
        return this.name;
    }

    public void setName(String name){
        if(name != null){
            this.name = name;
        } else {
            System.out.println("부적절한 name 할당 시도 무시 : " + name);
        }
    }

    // account에 대한 getter/setter는 생략
}

public class MainBoy {
    public static void main(Sting[] args){
        UserInfo us1 = new UserInfo();
        System.out.println(us1.getName())

        us1.setName(null)
        
    }
}

```

## 객체의 생성 제어와 SingleTone 디자인 패턴

`객체의 생성을 제한해야 한다면?`
> 여러 개의 객체가 필요 없는 경우

- 객체를 구별할 필요가 없는 경우 
- 수정 가능한 멤버 변수가 없고 `기능`만 있는 경우
- 이런 객체를 `stateless`한 객체라고 한다.
- 객체를 계속 생성/삭제 하는데 많은 비용이 들어서 재사용이 그냥 유리한 경우에 채택

`Singleton 디자인 패턴`
- 외부에서 생성자에 접근 금지 -> 생성자의 접근 제한자를 `private`로 설정
- 내부에서는 `private`에 접근 가능하므로 직접 객체 생성 -> 멤버 변수이므로 `private` 설정
- 객체 없이 외부에서 접근할 수 있도록 getter와 변수에 static을 추가
- 외부에선 언제나 getter를 통해서 객체를 참조하므로 하나의 객체를 재사용

`Singletone Design 연습`

```java

class SingletonClass{
    private static SingletonClass instance = new SingletonClass();
    private SingletonClass() {}

    public static SingletonClass getInstance(){ // 이 메서드로 불러서
        return instance; // 돌려주는데
    }

    public void sayHello() {
        System.out.println("Hello");
    }
}

public class SingletonTest {
    public static void main(String[] args){
        SingletonClass c1 = SingletonClass.getInstance();
        SingletonClass c2 = SingletonClass.getInstance();

        System.out.println("두객체는 같은가 : " +c1==c2); // 주소값이 둘다 같음
        c1.sayHello();

    }

}



```
--------------------------------------

# 5. 다형성(Polymrphism)
> 하나의 객체가 많은 타입을 가질 수 있는 것
`정의` : 상속 관계에 있을 때 조상 클래스에 속하는, 조상 클래스 타입인 자식클래스 여러 개를 레퍼런스 할 수 있다.

- onlyOne은 SpiderMan 타입인가?
    - SpiderMan 타입으로 onlyOne을 참조할 수 있는가?

- onlyOne은 Person 타입인가?
    - Person 타입으로 onlyOne을 참조할 수 있는가?

- onlyOne은 Object 타입인가?
    - Object 타입으로 onlyOne을 참조할 수 있는가?

- onlyOne은 Venom 타입인가?
    - Venom 타입으로 onlyOne을 참조할 수 있는가?


```java

SpiderMan onlyOne = new SpiderMan();

SpiderMan sman = onlyOne;

Person person = onlyOne;

Object obj = onlyOne;

Venom venom = onlyOne;

```

## 다형성의 활용
## case1. 다른 타입의 객체를 다루는 배열
- 배열의 특징 : 같은 타입의 데이터를 묵음으로 다룸
- 다형성으로 다른 타입의 데이터 (Person, SpiderMan)를 하나의 배열로 관리
- Object는 모든 클래스의 조상
    - object 배열은 어떤 타입의 객체라도 다 저장 가능
- 자바의 자료 구조를 간단하게 처리 가능
    - 이와 같은 특성을 이용해 Collection API가 등장

```java

public ArrayList(int initialCapacity){
    
    if (initialCapacity>0){
        thie.elementData = new Object[initialCapacity];
    } else if (initialCapacitiy == 0){
        this.elementData = EMPTY_ELEMENTDATA;
    } else{
        throw new IllegalArgumentException("Illegal Capacity : " + initialCapacity);
    }
}

```

`💡 기본형은 담을 수 있을까?`

```java

class someclass{

}

someclass s1 = new someclass();

Object [] obj = new Object[3];
obj[0] = "Hello";
obj[1] = s1;
obj[2] = 1; // 된다.
// 원칙적으로는 '1' 자체는 primitive여서 담을 수 없다.
// 그러나 자바에서는 autoboxing으로 인해 primitve도 저장을 한다!

```
> 실제로 `obj` 배열에 담긴 Type을 `getClass().getName()`으로 출력해보면 `java.lang.Integer`라고 하는 `reference`형 으로 캐스팅 된 것을 확인 가능!


## case2. System.out.println()
> 출력에 사용되는 `System.out.println()`의 실제 구조는 다음과 같다

```java

public void println(Object x){
    String s = String.valueOf(x);
    synchronized (this){
        print(s);
        newLine();
    }
}

```
- 조상을 파라미터로 처리한다면 객체의 타입에 따라 메서드를 만들 필요가 없다.
- API에서 파라미터로 Object를 받는다는 것은 모든 객체를 처리한다는 뜻과 동의어
- 물론 필요하다면 `하위 클래스`에서 `오버라이딩`이 가능하고 필요함.

## 다형성의 활용
- 메모리에 있는 것과 사용할 수 있는 것의 차이
- 메모리에 있더라도 참조하는 변수의 타입에 따라 접근할 수 있는 내용이 제한됨.

## 참조형 객체의 형 변환
> 작은 집(child)에서 큰집(super)로 >> 묵시적 캐스팅

```java
byte b= 10;
int i = b; // 묵지석 캐스팅

```

- 자손타입의 객체를 조상 타입으로 참조함. 형변환 생략 가능.
    - 원래 데이터를 손실 없이 담을 수 있으므로 가능

> 큰집(super)에서 작은 집으로(child)으로 >> 명시적 캐스팅
```java
int i =  10;
byte b = (byte) i; // 형변환 생략 불가함!
```
- 조상 타입을 자손 타입으로 참조 : 형 변환 생략 불가

## 참조형 객체의 형 변환
> 무늬만 SpiderMan인 Person

```java
Person p1 = new Person();
SpiderMan sman = (SpiderMan) p1; // 형변환 된거 같지만 데이터 손실..!!!
samn.fireWeb();
// Exception 발생!
```
- 실제 메모리에 올라간 객체에는 `fireWeb()` 메소드가 없음

- 조상을 무작정 자손으로 바꿀 수는 없다.
- `instanceof 연산자`
- 실제 메모리에 있는 객체가 특정 클래스 타입인지 `boolean`으로 리턴

💻 `instanceof` 예시

```java

Person p1 = new Person();

if (p1 instanceof SpiderMan){
    SpiderMan sm = (SpiderMan) p1;
}

```

## 참조 변수의 레벨에 따른 객체의 멤버 연결
- 상속 관계에서 객체의 `멤버 변수가 중복` 될 때
- `참조 변수`의 `타입`에 따라 연결이 달라짐. 💡 (이름 기준 x)
- 상속 관계에서 객체의 메서드가 중복될 때(메서드가 `override` 되었을 때)
- 무조건 자식 클래스의 메서드가 호출됨 -> virtual method invocation
- 최대한 메모리에 생성된 실제 객체에 최적화 된 메서드가 동작

## 예시 1) 객체가 출력되는 과정
```java
// System.out.println(Object obj)
SuperClass superclass = newe SubClass();
System.out.println(superclass);

// PrintStream의 print 메서드
public void print(Object obj){
    write(String.valueOf(obj));
}

// String의 valueOf
public static String valueOf(Object obj){
    return (obj==null) ? "null" : obj.toString();
}

// Object의 toString()
public String toString(){
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}


```

## 예시 2) 상속관계에서...

```java
class UserInfo {
    String name = "홍길동";

    @Override
    public String toString(){
        return "이름 : " + this.name;
    }
}

class MemberInfo extends UserInfo {
    String grade = "정회원";

    @Override // 다형성
    public String toString(){
        return super.toString() +", 등급" + grade;
    }
}

public class PrintObject {
    public static void main(String[] args){

        Object member = new MemberInfo();
        System.out.println("객체 정보 : " + member);

    }
}

```

 Java 에서 어떤 클래스 간의 관계를 형성할 때 상속을 통해서 부모-자식 간의 관계를 형성할 수 있다. 이 때 자바에서는 상위 클래스의 메서드에 대한 `Overriding`이 가능한데, 이때 오버라이딩 즉, 재정의가 안되면 결국에는 모든 메서드는 Object로 향할 수 밖에 없을 것이다. 그러나, 객체지향 프로그래밍의 특성중 하나인 `다형성`으로 인해서, 우리는 이미 상위 클래스에서 정의된 메서드라고 할지라도, 자식 클래스에서 개발자가 원하는 데로 편집하고 재활용 할 수 있다. 이것이 다형성의 본질이자, 객체 지향 프로그래밍의 특성이다.



💡 다음 중 가장 적합한 메서드 구성은 무엇일까?

```java
public void userJump1(Object obj){
    int (obj instanceof Person){
        Person casted = (Person) obj;   // # (1)
        casted jump();
    }
}

public void userJump2(Person person){
    person.jump();                       // # (2)
}

public void userJump3(SpiderMan spiderMan){
    spiderMan.jump();                    // # (3)
}

Object obj = new Object();
Person p1 = new Person();
SpiderMan sp1 = new SpiderMan();

AppropriateParameter ap = new AppropriateParameter();

// 호출은 가능하나 실제로 점프가 불가
ap.userJump1(obj);
ap.userJump1(Person);
ap.userJump1(sman);

// ap.userJump1(obj);
ap.userJump1(Person);
ap.userJump1(sman);


// ap.userJump1(obj);
// ap.userJump1(Person);
ap.userJump1(sman);

```

`(1)` : 모든 케이스를 담을 수 있지만, 사실 다 받았어야 하는가?

`(2)` : Object만 못받으므로 조건문이 필요 없어짐

`(3)` : Object, Person 둘다 못받으므로 Person을 못받아서 아쉬워 짐.


- 용도에 따른 가장 적합한 메서드 구성은?
- 상위로 올라갈수록 활용도도 높아짐 (다양한 경우에서 사용 가능)
- 하지만 코드의 복잡성도 함께 증가 (고려할 요인이 많아짐)
- Java API 처럼 공통 기능인 경우 Object를 파라미터로 쓰는게 맞겠지만,
- 많은 경우에서 `Object`를 남용하기 보다는 비즈니스 로직상 `최상위 객체`를 사용을 권장한다. `like Person`

