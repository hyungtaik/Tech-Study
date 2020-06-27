# Java Virtual Machine (자바 가상 머신)

### 1. JVM이란?

> 시스템 메모리를 관리하면서, 자바 기반 애플리케이션을 위해 이식 가능한 실행 환경을 제공한다.
>
> **1) 자바 프로그램이 어느 기기나 OS 상에서도 실행될 수 있도록 하는 기능**
>
> **2) 프로그램 메모리를 관리하고 최적화하는 기능**
>
> - 어떤 기기 상에서 실행되고 있는 프로세스, 특히 자바 앱에 대한 리소스를 대표하고 통제하는 서버를 지칭한다.
> - 자바 애플리케이션을 클래스 로더를 통해 읽어들이고, 자바 API와 함께 실행한다.
> - Java와 OS 사이에서 중개자 역할을 수행하여 OS에 구애받지 않고 재사용을 가능하게 해준다.
>   -  Java Byte Code를 OS에 맞게 해석(기계어로 번역) 해준다. 이러한 해석과정으로 c언어와 같은 네이티브 언어에 비해 속도가 느리지만 JIT(Just In Time) 컴파일러를 구현해 극복하였다.
> - JVM이 자동으로 메모리 관리를 해준다.



#### 📎 JIT 컴파일러

> Just In Time : 그 순간.
>
> > 프로그램을 실제 실행하는 시점(그 순간)에 기계어로 번역하는 컴파일 기법 
> >
> > 같은 코드를 매번 해석하지 않고, **실행할 때 컴파일을 하면서 해당 코드를 캐싱**한다. 이후에는 바뀐 부분만 컴파일하고 나머지는 캐싱된 코드를 사용하여 인터프리터의 속도를 개선한다.



---

### 2. JVM 구조

> - Java Compiler는 자바 소스코드(.java)를 바이트 코드(.class)로 변환시켜준다.
>
> - JVM의 구조는 크게 Class Loader, Execution Engine, Garbage Collector, Runtime Data Area로 나뉜다.
>
>   

><img src="C:\Users\TAEK\AppData\Roaming\Typora\typora-user-images\image-20200628004645314.png" alt="image-20200628004645314" style="zoom:70%;" /> [ Image. JVM 구조 (ver. JDK 7) ]

> - **ClassLoader** : RunTime 시점에 클래스를 로딩하게 해주며 클래스의 인스턴스를 생성하면 클래스 로더를 통해 메모리에 로드하게 된다. 즉 자바 애플리케이션이 실행중일때, 클래스 파일들을 엮어서 JVM이 OS로부터 할당받은 메모리 영역인 Runtime Data Areas로 적재하는 역할을 한다.
>
>   - class area(Method area) : 메모리로 읽어온 클래스의 정보를 기억하는 곳.
>   - heap : 클래스의 객체를 생성하여 기억하는 곳.
>   - stack : 메소드 수행 시마다 프레임이 할당되어 메소드 수행에 필요한 변수나 중간 결과 값을 임시 기억하는 곳. 메소드 종료               시 할당 메모리 자동 제거
>   - 
>
> - **Runtime Data Area** : JVM이 프로그램을 수행하기 위해 OS로부터 별도로 할당받은 메모리 공간을 말하며, 크게 5가지 영역으로 나눌 수 있다. 이 중에서 쓰레드가 생성되었을 때 기준으로 Heap과 Method 영역은 모든 쓰레드가 공유해서 사용하고, 스택 영역과 PC 레지스터, Native method stack은 각각의 쓰레드마다 생성되고 공유되지 않는다.
>
>   <img src="C:\Users\TAEK\AppData\Roaming\Typora\typora-user-images\image-20200628005150723.png" alt="image-20200628005150723" style="zoom:50%;" />[ Image. Runtime Data Area 구조]
>
>   | 영역                       | 설명                                                         |
>   | -------------------------- | ------------------------------------------------------------ |
>   | PC Register                | 프로그램의 실행은 CPU에서 명령어를 수행하는 과정으로 이뤄지는데 이때 **명령을 수행하는 동안 필요한 정보저장**을 레지스터라고 하는 CPU내의 기억장치를 사용한다.<br/>Java의 PC Register는 CPU 내의 기억장치와 다르게 Register - Base가 아닌 **Stack - Base**로 동작한다. PC Register는 각 Thread별로 하나씩 존재하며, 현재 수행중인 JVM 명령의 주소를 가지게 된다.  즉, **현재 Thread가 실행되는 부분의 주소와 명령을 저장하고 있는 영역**이다. |
>   | Java Virtual Machine Stack | Thread의 수행정보를 Frame을 통해서 저장하게 된다. Java Virtual Machine Stack은 Thread가 시작될 때 생성되며, 각 Thread 별로 생성되기 때문에 다른 Thread가 접근할 수 없다. <br>Method가 호출되면 Method와 정보는 Stack에 쌓이고, 호출이 종료될 때 Stack Point에서 제거된다. **Method 정보로 매개변수,지역변수, 임시변수 그리고 Method 호출한 주소 등을 저장**하고 종료시 메모리공간에서 사라진다. |
>   | Native Method Stack        | Java 외의 언어로 작성된 Native 코드들을 위한 Stack, 즉 JNI(Java Native Interface)를 통해 호출되는 C/C++ 등의 코드를 수행하기 위한 Stack이다.<br/>이러한 Native Method를 위해 Native Method Stack이라는 메모리 공간을 갖는다. Application에서 Native Method를 호출하게 되면 Native Method Stack에 새로운 Stack Frame을 생성하여 push한다. 이는 JNI를 이용하여 JVM 내부에 영향을 주지 않기 위함이다. **실제 실행할 수 있는 기계어로 작성된 프로그램을 실행시키는 영역이다.** |
>   | Method Area                | 모든 Thread가 공유하는 메모리 영역이다. JVM이 시작될 때 생성되고, JVM이 읽은 각각의 클래스, 인터페이스, 메소드, 필드, Static 변수 등의 바이트 코드 등을 보관한다. |
>   | Heap Area                  | 프로그램 상에서 **런타임시 동적으로 할당하여 사용하는 영역**으로  New명령어를 통해 생성한 인스턴스와 배열 등의 참조형 변수정보가 저장되는 공간이다. 메소드 영역에 로드된 클래스만 생성이 가능하고 Garbage Collector가 참조되지 않는 메모리를 확인하고 제거하는 영역이다.<br/>힙 영역은 **효율적으로 GC가 일어나게 하기 위해 5개의 영역(eden, survivor1, survivor2, old, permanent)으로 나뉜다.** JDK7까지는 permanent영역이 heap에 존재했지만 JDK8부터는 permanent 영역은 사라지고 일부가 "meta space 영역"으로 변경되었다.(위의 그림 JDK7 기준) meta space 영역은 Native stack 영역에 포함되었다. JDK8 기준으로 permanent영역이 삭제되어 heap 영역에서 사용할 수 있는 메모리가 늘어났고, permanent영역을 삭제하기 위해 존재했던 여러 복잡한 코드들이 삭제 되어 permanent영역을 스캔 하기 위해 소모되었던 시간이 감소되어 GC 성능이 향상 되었다. |
>
>   ​                  
>
> - **Execution Engine** :  로드된 클래스의 바이트코드를 실행하는 Runtime 모듈이다. 클래스로더를 통해 JVM 내의 Runtime Data Area에 배치된 바이트 코드는 Execution Engine에 의해 실행되며, 실행 엔진은 자바 바이트 코드를 명령어 단위로 읽어서 실행한다. 최초의 JVM이 나왔을 당시는 인터프리터 방식으로 한 줄씩 해석하여 실행하였기 때문에 속도가 느리다는 단점이 있었지만 JIT 컴파일러 방식을 통해 이를 보완하였다. JIT는 바이트코드를 어셈블러 같은 Native Code로 바꿔서 실행이 빠르지만 변환하는데 비용이 발생한다. 이와 같은 이유로 JVM은 모든 코드를 JIT 컴파일러방식으로 실행하지 않고, 인터프리터 방식을 사용하다 일정한 기준이 넘어가면 JIT 컴파일러 방식으로 실행한다.
>
>   
>
> - **Garbage Collectior** : Heap 메모리 영역에 생성된 객체들 중에 참조되지 않는 객체들을 탐색 후 제거하는 역할을 한다. 
>
>   - GC가 역할을 하는 시간은 정확히 언제인지 알 수 없다. (참조가 없어지자마자 해제되는 것을 보장하지 않으므로)
>
>   - GC가 수행하는 쓰레드가 아닌 다른 모든 쓰레드가 일시정지된다.
>
>   - Full GC가 일어나서 수 초간 모든 쓰레드가 정지한다면 장애로 이어지는 치명적인 문제가 생길 수 있다. 
>
>   - GC는 Minor GC와 Major GC로 나뉜다.
>
>     1) **Minor GC : New 영역에서 일어나는 GC**
>
>     - 최초에 객체가 생성되면 Eden영역에 생성된다.
>
>     - Eden영역에 객체가 가득차게 되면 첫 번째 CG가 일어난다.
>
>     - survivor1 영역에 Eden영역의 메모리를 그대로 복사된다. 그리고 survivor1 영역을 제외한 다른 영역의 객체를 제거한다.
>
>     - Eden영역도 가득차고 survivor1영역도 가득차게된다면, Eden영역에 생성된 객체와 survivor1영역에 생성된 객체 중에 참조되고 있는 객체가 있는지 검사한다.
>
>     - 참조 되고있지 않은 객체는 내버려두고 참조되고 있는 객체만 survivor2영역에 복사한다.
>
>     - survivor2영역을 제외한 다른 영역의 객체들을 제거한다.
>
>     - 위의 과정중에 일정 횟수이상 참조되고 있는 객체들을 survivor2에서 Old영역으로 이동시킨다.
>
>       \- 위 과정을 계속 반복, survivor2영역까지 꽉차기 전에 계속해서 Old로 비움
>
>     2) **Major GC(Full GC) : Old 영역에서 메모리 회수가 일어나는 GC**
>
>     - Old 영역에 있는 모든 객체들을 검사하며 참조되고 있는지 확인한다.
>
>     - 참조되지 않은 객체들을 모아 한 번에 제거한다.
>
>       \- Minor GC보다 시간이 훨씬 많이 걸리고 실행중에 GC를 제외한 모든 쓰레드가 중지한다. **( Stop - the - Wold)**
>
>        -> 이것이 종료될 때 까지 다른 모든 쓰레드가 멈추기 때문에 성능에 영향을 끼칠 수 밖에 없다.
>
>       
>
>     📎 Major GC(Full GC)가 일어나면, Old영역에 있는 참조가 없는 객체들을 표시하고 그 해당 객체들을 모두 제거하게 된다.
>
>     그러면서 Heap 메모리 영역에 중간중간 제거되고 빈 메모리 공간이 생기는데 이 부분을 없애기 위해 재구성을 하게 된다. (디스크 조각모음처럼 조각난 메모리를 정리함)
>
>     따라서 메모리를 옮기고 있는데 다른 쓰레드가 메모리를 사용해버리면 안되기 때문에 모든 쓰레드가 정지하게 되는 것이다.
>
>   



### 3. JVM 실행 과정

> 1. 프로그램이 실행되면, JVM은 OS로부터 이 프로그램이 필요로하는 메모리를 할당받고, JVM은 이 메모리를 용도에 따라 여러 영역으로 나누어 관리한다.
> 2. 자바 컴파일러(JAVAC)가 자바 소스코드를 읽고, 자바 바이트코드(.class)로 변환시킨다.
> 3. 변경된 class 파일들을 클래스 로더를 통해 JVM 메모리 영역으로 로딩한다.
> 4. 로딩된 class파일들은 Execution engine을 통해 해석된다.
> 5. 해석된 바이트 코드는 메모리 영역에 배치되어 실질적인 수행이 이루어지고, 이러한 실행 과정 속 JVM은 필요에 따라 쓰레드 동기화나 가비지 컬렉션 같은 메모리 관리 작업을 수행한다.





[참고 URL]

- [ https://starplatina.tistory.com/entry/JDK8%EC%97%90%EC%84%A0-PermGen%EC%9D%B4-%EC%99%84%EC%A0%84%ED%9E%88-%EC%82%AC%EB%9D%BC%EC%A7%80%EA%B3%A0-Metaspace%EA%B0%80-%EC%9D%B4%EB%A5%BC-%EB%8C%80%EC%8B%A0-%ED%95%A8](https://starplatina.tistory.com/entry/JDK8에선-PermGen이-완전히-사라지고-Metaspace가-이를-대신-함)

- https://aljjabaegi.tistory.com/387
- https://www.holaxprogramming.com/2017/10/09/java-jvm-performance/