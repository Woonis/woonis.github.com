---
title: "Study"
date: 2019-08-18 08:10:00 -0400
categories: Spring
sitemap :
  changefreq : daily
  priority : 1.0


---

# 

### Access Modifier

Java의 접근제어자는 총 4가지가 존재한다.

- Public : 같은 프로젝트 내 어느 프로젝트에서나 참조가 가능한 접근제어자.
- Protected: 상속 관계의 존재하는 클래스들만이 접근이 가능한 접근제어자.
- Package-private : 자바의 디폴트 접근제어자로써, 같은 패키지내에 존재하는 클래스 들이 접근 가능한 접근제어자.
- Private: 외부에서의 접근이 불가능하고, 현재 클래스 내에서만 접근이 가능한 접근 제어자.



### Cache

중복적인 데이터의 호출이 많은데 응답이 같거나, 데이터의 로딩의 오랜 시간이 걸리는 경우 캐시를 통해 데이터의 접근을 최소하 하여 같은 응답을 보내줄 수 있음. ex) Redis, Guava 캐시 

또한 스프링 부트에서는 어노테이션으로도 캐시를 제공하지만, 인스턴스가 여러대가 뜨는 경우 각 인스턴스 별로 캐시의 적용이나 익스파이어의 차이 갭이 발생할 수 있으므로 주의해야 한다.

### Checked vs UnChecked vs Error

- Error: 정상적인 어플리케이션에서는 발생이 불가능 한 것. 네트워크, 데이터 베이스 에러 등.
- Checked Exception: 컴파일 시에 해결해야하는 Try Catch또는 Throws를 통해. 예외의 처리를 미리 진행할 수 있는 익셉션.
- UnChecked Exception(Runtime Exception): 어플리케이션 동작중에 발생하여 동작을 멈추게하는 익셉션. NullPointerException, IndexOutOfBoudException등이 대표적이다.

### Class vs Object vs Instance

- Class : 변수와 메소드로 구성된 객체를 만들어 내기 위한 설계도.
- Object : 클래스에 선언된 모양 그대로 생성된 실체. 클래스의 인스턴스라고도 부름.
- Instance : Class를 바탕으로 구현된 구체적인 실체. 메모리의 할당된 상태. 인스턴스는 객체에 포함됨.

### Collections

Java 에서는 같은 타입의 데이터를 가지는 변수들을 한번에 저장하기 위해 Array와 Collection을 제공함.

배열의 경우에는 처음 사용시에 사이즈 정보에 대한 부분이 같이 명시되어야 하고, 해당 공간을 할당한 후 사용하지 않으면 메모리에 낭비가 발생할 수 있으므로, 동적으로 데이터의 공간을 생성하여 저장하는 Collection을 많이 사용. 

Collection Interface는 크게 Collection / Map의 큰 두가지의 자료 구조로 나눌 수 있다.

1. List : 순서가 있는 저장 공간으로 중복을 허용함. Array에 비해 인덱스를 통한 접근이 조금 느릴 수는 있음. 삭제는 리스트가 훨씬 유용하고 빠름. ex) ArrayList, Stack and so on.
2. Set : 순서가 없는 저장 공간으로 중복을 허용하지 않음. ex) HashSet, SortedSet and so on.
3. Map: Key-Value의 집합으로 이루어진 자료구조이며, 순서는 유지되지 않고 키는 중복을 허용하지 않지만 값의 경우는 중복을 허용한다. ex) HashMap, SortedMap and so on.

### CQRS(Command and Query Responsibility Segregation)

전통적인 CRUD 아키텍처에서 Application을 개발 및 운영하다보면, 자연스레 Domain Model의 복잡도가 증가함.
이로인한 유지보수 비용이 늘어나고, 처음 설계와는 다르게 변질되기도 함.

Application의 Business 정책이나 제약은 거의 C,U,D의 영향을 주고, R의 작업은 대부분 조회이므로 두 업무를 동일한 Domain Model로 처리하다보면 각 업무영역에 필요치 않은 도메인 정보들을 가지며 복잡도가 증가함.

1. DB는 분리하지 않고, Modelrhk Command Query Model만 분리함.
2. Command용과 Query용 디비를 분리하고, 이 두개의 디비를 동기화 함.
3. 이벤트 소싱을 적용한 구조. 



### Final vs Enum

Final의 경우는 영역에 따라 아래와 같은 역할을 하게된다.

- Class : 상속 불가. ex) String
- Method: 오버라이딩 불가.
- Field: 값의 초기화 이후 값의 변경 불가. 값의 불변을 보장하기 위해 사용.

따라서 주로 클래스 내의 값이나 프로젝트 전체내에서 상수 형식으로 선언할 수 있는 경우 final field로 선언하여 주로 사용함.

Enum은 상수의 집합을 위한 타입.

따라서 하나의 이넘타입내의 여러 연관 있는 상수의 집합을 가지고 있으며, 경우에 따라 기본적으로 제공해야하는 메소드나, 필드에 대한 추가 선언도 가능하다.



### GC(Garbage Collection)

C언어에서는 개발자가 직접 메모리에 대한 할당과 해제를 진행해야 했지만, 자바에서는 JVM을 통해 OS메모리에 접근하므로 GC가 자동으로 오래된 메모리 영역을 확보해주는 GC가 있기때문에 굳이 개발자가 신경쓸 필요가 없음.

JVM의 GC의 첫번째 타킷은 Stack에서 더 이상 도달 할 수 없는 Heap영역의 객체 Unreachable Object해당 객체.

GC의 과정을 **Mark and Sweep**라고도 부르는데, GC의 Mark는 Unreachable Object를 찾기위해 스레드를 중단하고 Stack에 있는 모든 내용을 스캔하며 Reachable Object를 마킹하는 작업을 말한다. 따라서 System.gc()를 함부로 호출하면 안됨. 이후 Sweep을 통해 더이상 참조하지 않는 객체들을 힙 영역에서 삭제한다.

- VisualVM을 통해 모니터링이 가능함.

##### 일반적인 GC

Heap영역은 크게 Young Zone과 Old Zone으로 나누게 됨.

Young Zone은 Old Zone보다 작은 메모리 영역을 가지며, Young Zone을 주기 적으로 삭제한 후 오랜 영역 참조를 가지는 메모리들을 Old Zone으로 이동시키게 됨.

따라서 전체 모든 영역을 스캔하는 것보다 더 빠르게 스캔이 가능하며, Young Zone을 한번에 비우기 때문에 연속된 여유 공간이 만들어지게 됨.

**GC가 Young Zone을 정리하는 것을 Minor GC, Old Zone을 정리하는 것을 Full FC라고 함.**

##### GC 종류

- Serial: 32bit 싱글 스레드 어플리케이션에서 사용되는 기본 GC. Minor/Full GC Single Thread 모두 All Stop.
- Parallel: 64 bit JVM이나 멀티 CPU 머신에서 사용되는 기본 GC. Minor/Full GC 모두 Multi Thread로 모두 All Stop.
- CMS Collector: Full GC의 stop-the-world를 줄이기 위함. Minor GC는 Multi Thread의 Stop이지만, Full GC는 거의 Stop-the-world가 발생하지 않음. 백그라운드의 별도의 쓰레드를 통해서 삭제될 영역을 체크하기 때문에 stop-the-world는 줄었지만, 항상 GC Thread가 별도로 동작하므로 CPU 리소스를 많이 사용하고, 메모리 파편화가 많이 발생한다.
- G1(Garbage First): 힙영역이 4GB 이상에서 동작하기 적합한 GC. CMS Collector의 메모리 파편화 이슈를 해결함. Minor GC는 Multi Thread로 정리를 하며, Old Zone을 여러개의 Region으로 나누어 관리함.



### Generic

컴파일시에 형변환의 문제점을 방지위해 사용. 클래스나 메소드에 <특정 캐릭터>를 통해 제너릭하게 받을 타입을 선언할 수 있음.

> E: 요소(Element)
> K: 키(Key)
> N: 숫자(Number)
> T: 타입(Type)
> V: 값(Value)
> S, U, V: 두번째, 세번째, 네번째에 선언된 타입

? 라는 whildcard를 통해 모든 타입에 대해 열려있도록 선언할 수도 있지만, 해당 부분을 ? extends "some class"로 선언하여 특정 클래스 하위 클래스들만이 해당 클래스에 접근이 가능하게 할 수도 있음.



### Immutable Object - Integer, Character, Byte, Boolean, Long, Double, Float, Short (Wrapping Class)

변경하는 연산이 수행되면 변경하는 것처럼 보이지만 실제로는 Heap영역 안에 새로운 메모리에 새로운 객체가 할당 됨.
String 내부의 this는 Final변수임으로, 실질적으로 재 할당이 불가능함. 즉, +연산이나 replace()등의 String의 메소드가 호출되게 되면, 이는 현재 final변수로 부터 값을 읽은 후 메소드를 수행하고 새로운 객체로 값을 반환하는 형태임.



### JAVA Compile

1. Text 편집기를 통해 *.java file로 코딩.
2. javac *.java 를 통해 *.class파일(바이트 코드)로 변환.
3. JVM에서 *.class 파일로딩을 통한 프로그램 실행.

Java는 JIT(Just In Time) Compiler를 통해 이미 변환된 코드는 캐싱하는 방식을 사용하여 인터프리터의 속도를 개선하였다.
JIT란 JVM등의 가상머신이 중간 언어인 바이트 코드를 가지고 코드를 수행함으로써 플랫폼의 제약이 없이 런타임에 컴파일을 할수 있도록 하는 방식.

### JAVA Memory (Stack vs Heap)

https://yaboong.github.io/java/2018/05/26/java-memory-management/

1. Stack
   - Heap영역의 생성된 Object 타입의 데이터의 참조값이 할당.
   - Primitive Type 변수의 데이터 값이 할당.
   - 지역변수의 visibility. -> 지역변수의 호출 순서를 가지기 때문에 자신의 해당 블럭이 끝나면 함께 pop됨.
   - 각 Thread는 자신만의 Stack을 가짐. -> 즉 다른 Thread에서는 외부 Thread의 Stack에 접근이 불가함.
2. Heap
   - 긴 생명 주기를 가지는 데이터가 저장.
   - Application의 메모리 중 stack의 데이터를 제외한 부분이 저장.
   - Thread와 상관없이 단 1개의 Heap이 존재.
   - Heap영역의 오브젝트들을의 참조 값이 Stack에 저장됨. -> 파라미터 변수로 전달되었다 하더라도 종료시점에 변경 값이 반영됨.

### JAVA 8

- 람다 제공(익명 함수). 따라서 람다를 통해 익명 함수로써 메소드의 선언이 없이 처리가 가능.

- Stream API제공. Collection Type의 Stream API가 제공되면서 해당 타입의 처리가 쉬워짐. -> 대용량 처리의 경유 성능 이슈 고려.

- Joda Time 제공. 조다 타임을 통해 각 로컬 데이트 기준의 시간 처리가 간편 해짐.

  

### Join (Nested-Loop, Merge Sort, Hash)

조인이란, 두 릴레이션으로 부터 관련된 튜플들을 결합하여 하나의 튜플로 만드는 가장 대표적인 데이터 연결 방법.

1. Inner Join : A,B 테이블의 교집합을 결과로 리턴.
2. Left, Right Outer Join : 각 Left, Right 테이블을 기준으로 해당 테이블의 결과 + 중복 결과를 리턴.
3. Cross: 모든 경우의 수를 조합한 결과를 리턴.
4. Self: 자기 자신과 자기자신을 조인.

* Join 수행 방식

1. Nested-Loop : 선행테이블의 처리범위를 하나씩 액세스하면서 추출된 값으로 연결할 테이블을 조인.
   Loop를 줄이기 위해, 테이블의 로우수가 적은 테이블을 선행테이블로 하여, inner테이블의 연결고리를 결합 인덱스를 통해 최적화 해야함.
2. Sort Merge : 양쪽 테이블 처리범위를 각자 액세스 하여 정렬한 결과를 차례로 scan하면서 연결고리의 조건으로 조인.
   정렬이 되어 있지 않은 경우는 외부 정렬을 사용한 후 조인을 하며, 각 정렬되어 있는 애트리뷰트 A,B의순서에 따라 동시에 스캔하면서 조인함. 
   join의 연결고리가 '>' , '<'인 경우 Nested Join보다 유리함.
   하지만 두 집합의 크기의 차이가 큰 경우에는 비효율 적임.
3. Hash : 해시 함수를 기준으로 하여 선행과 후행 테이블을 조인. 더 적은 테이블을 선행으로 하여 해시 함수를 적용한 후 후행 레코드들의 해시 함수를 적용하여 실제로 동일한 주소를 갖는 레코드들을 조인함.
   많은 메모리와 CPU가 사용되지만, 대용량 데이터를 처리하기 쉽고, 랜덤 엑세스와 정렬에 대한 부담을 해결할 수 있음. 단, 연결 조건 연산자가 '=' 인 경우에만 사용이 가능함.



### MSA(Micro Service Architecture)

- **Monolithich**

  일부 모듈의 변경사항으로 전체 어플리케이션의 개발과 운영에 영향을 줌.

  모듈별 신기술이나 특정 구조를 맞추기가 어렵고, 확장이 어려움

- **MSA**

  장 : Application을 각자 책임 명확한 작은 컴포넌트들로 나눔으로써 각 어플리케이션 별 신기술이나 구조를 적용할 수 있으며, 배포가 용이해짐. 각 Application의 통신을 위해서는 HTTP와 JSON 같은 경량 프로토콜을 사용한다.

  단 :각 어플리케이션이 분산되어 있기때문에 장애 추적, 모니터링 또는 전체 통합 테스팅이 어렵다. 또한 디펜던시가 있는 배포인 경우에는 서로의 배포 디펜던시를 가지기 때문에 까다로울 수 있다.



### OOME(Out Of Mermory Exception)

JVM의 Heap 메모리에 더이상 Object를 할당할 수 없을 때 발생.

1. Java Heap Space
   - Heap 메모리가 작음. -> -Xmx 옵션을 사용하여 메모리를 증가 시킬 수 있음.
   - 로직의 의해서 발생. -> Heap Dump를 통해 많은 메모리를 사용하고 있는 부분을 찾아 로직 수정이 필요.
2. PermGen Space
   - Permanaet : String pool, Class Method와 관련된 각종 Meta Data 저장을 위함.
   - JVM 수행 시 로딩되는 Class나 String의 수가 너무 많아 진 경우. WAS 혹은 JDK의 버그를 의심해 봐야함.

### OOP(Object Oriented Programming)

객체의 관점에서 프로그래밍을 하는 것. 어플리케이션을 구성하는 요소들을 객체로 바라보고, 객체를 유기적으로 연결하여 프로그래밍 하는 것.

1. 추상화 
   객체들의 공통된 특징을 파악해 정의해 놓은 설계의 특징.
2. 캡슐화
   정보 은닉을 위하여 외부에 노출되지 않아야 하는 속성을 노출하지 않는 특징.
3. 상속
   코드의 중복을 없애기 위해, IS-A 관계에 대해 정의하여 재사용 하는 특징.
4. 다형성
   오버라이딩을 통하여 각 하위 객체들이 하나의 상위 객체를 상속 받아도, 각자 자신의 역할에 맞게 재정의 한다는 특징.

### ORM(Object Relational Mapping)

데이터의 영속성을 위해 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑해 주는 것.

대표적인 프레임 워크로는 Hibernate가 있고, 이를 Java 표준으로 정의한 것이 JPA이다.

- 장 : 개발자가 데이터를 검색하고 업데이트하고 환경을 셋팅하기 위한 시간을 줄여주고 재사용 및 유지보수의 편리성을 증가 시켜줌.
- 단 : 설계에 신중해야 하며, 잘못된 구현의 경우 문제가 발생할 수 있고, 대용량 쿼리를 사용하기 위해서는 Store Procedure등을 사용하는 등의 별도의 튜닝이 필요한 경우가 있음.

### Overloading vs Overriding

- **Overloading** 

  함수의 메소드 명은 같지만, 파라미터의 수나 타입 다른경우.

- **Overridng (다형성)**

  상위 클래스에서 정의해둔 메소드를 하위 클래스에서 재정의 하는 경우. 함수의 리턴타입, 이름 그리고 파라미터의 수가 모두 동일.



### Process Vs Thread

- **Process**

  컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램. 메모리에서 실행되고 있는 프로그램의 독립적인 인스턴스.
독립적인 Code, Data, Stack, Heap의 영역을 OS로 부터 할당 받음
  최소 1개의 메인스레드가 있으며, 각 프로세스는 별도의 주소에서 실행되기 때문에 다른 프로세스에 접근하려면 프로세스 간의 통신이 필요함.
  
- **Thread**

  프로세스 내에서 실행되는 여러 흐름의 단위. 프로세스 내의 주소 공간이나 자원을 같은 프로세스 내의 스레드끼리 공유하면서 실행.
  프로세스로 부터 각 Stack만 할당 받고, Code, Data, Heap은 공유함.
  한 스레드가 프로세스의 자원을 변경하면, 다른 스레드에서도 그 변경 결과를 볼 수 있음.

- **Java Thread**

  일반 스레드와 차이가 없으며, JVM이 OS역할을 함. JVM에 의해 스케줄 되는 싱행 단위 코드 블럭.
  JVM이 해당 스레드를 실행하며, 현재 몇개의 스레드가 존재하고, 프로그램의 위치가 어디이며 상태는 어떤지 그리고 우선순위는 어떤지에 대한 정보들을 관리함.

- **Multi Processing and Multi Thread.**

  Multi Processing : 하나의 프로그램을 여러개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리하게 하는 것.
  장 : 여러개의 프로세스 중 하나가 문제가 발생해도 다른 프로세스는 영향이 없음.
  단 : Context Switching 과정에서 오버헤드가 발생.

  Multi Thread : 프로세스 내에서 작업의 단위를 여러 스레드의 단위로 나누어 처리하게 하는 것.
  장 : 시스템 자원 소모 감소 및 처리량 증가.
  단 : 주의 깊은 설계가 필요하고, 디버깅이 까다롭다. 또한 하나의 스레드에 영향이 생기면 전체 프로세스가 영향을 받음.

  일반적으로 프로그램을 여러개 키는 Multi Processing보다는 자원을 효율적으로 나누어 사용할 수 있고, 처리 시간이 감소하는 Multi Thread를 주로 사용.

  

### Reflection

Class의 내부 정보를 조회하고 조작할 수 있는 기법.

- Class : Object Class에 있는 getClass() 메소드를 주로 이용.
- Method : Class 클래스에 getMethod() 또는 getDeclaredMethod()를 주로 이용.
- Field: Class 클래스에 getField() 또는 getDeclaredField()를 주로 이용.

### RESTful API

REST = Representational State Transfer 

즉, 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것.

HTTP URI를 통해 자원을 명시하고, HTTP Method를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미.

- 장 : HTTP 프로토콜의 인프라를 그대로 사용하기 때문에 별도 인프라 구축이 필요 없음. 메시지가 의도하는 바를 명확하게 나타낼 수 있고, 서버와 클라이언트의 역할을 명확하게 분리한다.
- 단 : 표준이 존재하지 않고, Http Method 형태가 제한적이다. 



### Scale-up, Scale-out

- **Sacle-Up**

  수직 스케일.
  서버 자체의 성능을 증가 시키는 것. ex) 기존 서버에서 더욱 고성능 서버로 변경하는 것.
  스토리지의 확장성의 한계가 있고, 한계에 다다른 경우 새로운 시스템으로 전환하는 마이그레이션 비용이 발생.
  Ex) 제어가 힘들거나 분할 구성이 필요한 복잡한 서비스 오라클.

- ##### Scale-Out

  수평 스케일.
  기존의 서버와 같은 사양 또는 비슷한 사양의 서버 대수를 증가 시키는 방법.
  스케일 업보다는 다소 유연하지만, 병렬 구조된 서버의 데이터 동기화 및 세션 공유에 대한 고민이 필요.
  Ex) 접속 하는 세션의 수가 급속도로 증가한다면 스케일 아웃이 유리할 수도, 하지만 스케일 업의 비용이 더욱 저렴하거나 하다면 스케일 업을 하는 것도 방법일 수 있음.

### SOLID

객체지향의 5대 원칙.
**- SRP(Single Resposibility Principle) - 단일 책임 원칙**
하나의 객체는 하나의 책임을 가지도록 설계되어야 한다는 원칙.
ViewController -> ButtonEventListener의 예제.

**- OCP(Open-Closed Principle) - 개방 폐쇄 원칙**
확장에는 열려있지만 변경에는 닫혀있어야 한는 원칙. 즉, 최한의 변경으로 확장이 가능해야 함.
ButtoneEvenListener가 여러가지 타입의 버튼을 가지게 추가되는 예제.

**- LSP(Liskov Substitution Principle) - 리스코프 치환의 원칙** (계약에 의한 원칙)
하위 클래스로의 변환이 자유로워야 하며, 상위 클래스의 객체에서 제공하는 메소드는 하위 클래스 객체에서 항상 같은 동작을 해야한다.
Rectangle -> Sqaure 를 직사각형에서 제공하는 SetHeigh()등의 메소드에 위배될 수 있음.

**- ISP(Interface Segregation Principle) - 인터페이스 분리의 원칙**
클라이언트는 자기가 디펜던시를 가지는 인터페이스에만 의존을 해야함.
Component -> Button, Modal의 경우 Modal의 변경이 생기면 Button도 변경해야함.

**- DIP(Dependency Inversin Principle) - 의존 역전 원칙**
고수준의 모듈의 저수준의 모듈을 의존하는 것이 아닌, 저수준의 모듈이 고수준의 모듈을 의존해야함.
그래야 확장에 유연한 구조가 되며, 단일 책임을 지킬 수 있음.

### Spring AOP

관점 지향 프로그래밍.

어떤 로직을 핵심적인 관점, 부가적인 관점으로 나누어보고 프로그래밍을 하겠다는 것.

각 클래스 별로 흩어진 로직을 Aspect로 모듈화 하고, 비즈니스 로직에서는 분리하겠다는 것.

ex) @transactional, logging을 위한 것을 추가하고자 할 때.

### Spring Filter vs Interceptor

Filter : Request가 들어온 후 DispatcherServlet으로 요청이 전달되기 전에 호출되는 것. 요청과 응답을 가로채는 것.

Interceptor :  DispatcherServlet으로 요청을 받은 후 컨트롤러의 전달 전에 호출되는 것. 요청의 작업 전후를 가로채는 것.

### Spring IOC, DI, DL

##### IOC (Inversion of Control)

제어의 역전이라 부르며, 컨테이너가 등장하면서 객체의 생성 및 관리의 역할이 컨테이너로 위임된 것을 의미함.

##### DL (Dependeny Lookup)

의존 대상을 검색을 통해 반환 받는 방식.  ex) (Bean Factory )factory.getBean(id), ApplicationContext

##### DI (Dependency Injection)

- Setter : 클래스 사이의 의존 관를 연결하기 위해 Setter메소드를 사용. 객체를 생성한 후 Set을 호출하지 않으면 디펜던시가  null로 되어있는 상태로 nullPointer가 발생할 수 있지만, 생성자를 통해 주입받아야 할 객체가 너무 많을 때 유용.
- Constructor : (가장 추천) 클래스 사이의 의존 관계를 연결시키기 위하여 constructor를 사용. 컴포넌트로 항상 의존성을 전달. 생성을 하면서 의존을 모두 주입받음으로써, 의존 관계가 명확해짐. 즉 SRP를 지키기 쉬워짐.
- Method : 어떤 메소드의 실행을 다른 메소드로 대체하거나 메소드의 리턴형을 추상 클래스로 지정 후 필요에 따라 추상클래스의 구현체를 리턴하도록 구현.
- Variable : @Autowried

##### @Autowired 

@Component가 붙은 클래스들 중 빈을 찾아서 인젝션 해줌. 인젝션 할 수 있는 클래스형은 반드시 하나여야함.
여러개의 클래스 타입으로 상속 구현 클래스가 발생했다면 ? @Primary를 부여하거나 @Qulifier를 사용.

##### @Component

@Controller : 스프링 MVC용.
@Service : 서비스용. @Component와 동일.
@Repository: 데이터 엑세스를 위한용.
@Configuration: 설정용.

### Spfing MVC

1. 클라이언트가 서버에 요청을 하면 스프링에서 제공하는 DispatcherServlet라는 클래스가 요청을 가로챔.
2. DispatcherServlet은 어떤 컨트롤러에게 요청을 위임할지 HandlerMappding을 통해 판단.
3. 매핑된 컨트롤러가 있다면 @RequestMapping을 통하여 처리 메소드를 수행.
4. 컨트롤러는 Service를 주입받아 서비스 내 처리메소드를 수행.
5. Service는 비즈니스 로직을 주로 수행하며, 디비 접근이 필요한 경우 Dao를 주입받아 디비 처리는 위임.
6. Dao는 ORM을 통해 디비작업을 수행한 후 서비스에게 결과를 리턴
7. 모든 로직을 끝낸 서비스는 컨트롤러에게 결과를 리턴
8. 컨트롤러는 Model객체에 결과의 응답페이지를 어떻게 보여줄지의 정보를 담아서 DispatcherServlet에게 전달.
9. ViewResolver는 해당 View를 찾아 DispatcherSevlet에게 전달.
10. DispatcherServlet은 응답할 View에 렌더를 지시하고 View는 응답 로직을 처리.
11. DispatcherServlet이 클라이언트에게 렌더링된 View를 응답.

### Static 

메모리 사용에 이점. 데이터 공유의 개념.

method : 클래스 객체를 생성하지 않고, 클래스 명으로 접근이 가능한 메소드를 생성함.

variable : 클래스의 객체들이 공유하는 변수로 생성됨.

### String, String Buffer, StringBuilder

String은 문자열을 저장하기 위한 자바의 타입으로써 유일하게 new 생성자를 통하지 않고 객체를 생성하는 Reference Type.
String은 자바에서 기본연산 중 "+"연산을 제공함.
하지만 스트링 객체의 "+" 연산을 사용하게 되면, 해당 기존 객체의 재사용성이 떨어지게 됨.
따라서 String Buffer와 String Builder가 생김.
두 클래스 모두 문자열을 다루기 때문에 CharSequence를 구현하고, 문자열의 더하기 연산을 위한 목적은 같지만, String Buffer는 Thread Safe하고 String Builder는 Thread Safe하지 않음.
그러므로 여러 쓰레드에서 한 변수의 접근을 통하여 값의 연산을 하는 경우에는 StringBuilder가 아닌 StringBuffer를 사용하는 것이 좋음.

### Sync vs Async And Blocking vs Non-Blocking

- Sync vs Async (순서)

  Sync는 작업의 순서를 보장. Ex) A, B, C 순서로 호출 했다면, A, B, C 순서로 작업이 완료.
  ASync는 작업의 순서를 보장하지 않음. Ex) A, B, C 순서로 호출했어도, 호출의 순서대로 완료되지 않을 수 있음.
  Java에서 Sync처리는 CompletableFuture로 처리함.

- Blocking vs Non-Blocking(통지)

  Blocking은 작업이 끝날때 까지 대기하다가 즉석에서 완료 통지를 받음.
  Non-Blocking은 작업의 완료를 나중에 통지 받음.



### TDD(Test Driven Development)

테스트를 먼저 만들고 테스트를 통과하기 위해 실제 코딩을 하는 것.
장 : 결함이 줄어들고, 코드복잡도가 떨어짐.
단 : 개발 시간이 증가하고, 적응하는 것에 시간이 걸림.

### Thread

Java에서는 Thread Class를 상속하거나 Runnable 클래스를 구현함으로써 구현 가능.

- Runnable : 스레드가 실행되기 위한 준비 단계.
- Running: CPU를 점유하여 실행하고 있는 상태.
- Dead : 스레드 실행 완료 상태.
- Blocked: CPU 점유를 상실한 상태

Object Locking : Shared Resource에 접근하기 위하여 각 스레드가 Lock을 획득 하기 위해 대기하게 되면서 시간이 길어지면 Hang이 걸린 것 처럼 보임.



### == vs equals

Java 에서 == 는 stack에 저장된 주소 값 또는 값을 비교하는 연산자이며, equals는 실제 객체의 값이 동일한지를 비교한다.
따라서 stack에 주소 값이 저장되지 않고 실제 값이 저장되는 prmitive type의 변수들에 대해서는 실 ==와 각 타입의 Wrapping class를 통해 equals로 값을 비교해도 값의 비교를 확인할 수 있다. 하지만 new 생성자를 통해 Reference 타입의 객체를 생성하는 경우에는 stack에 주소 값이 저장되고 실제 각 객체의 값의 디테일은 Heap에 저장되므로 클래스별 equals 메소드 오버라이딩을 통해 각 객체의 밸류가 정말 동일한지 확인할 수 있는 구현이 필요하다.