## 객체지향 개요
* 소프트웨어 객체는 현실 세계의 객체를 필드와 메서드로 모델링한 것
* 소프트웨어 객체는 상태를 필드(Field)로 정의하고, 동작을 메서드(Method)로 정의
* 필드는 객체 내부에 선언된 변수를 의미하고, 메서드는 객체 내부에 정의된 동작을 의미함

### 절차지향
* 일련의 동작을 순서에 맞추어 단계적으로 실행하도록 명령어를 나열
* 데이터를 정의하는 방법보다는 명령어의 순서와 흐름에 중점

### 객체지향
* 현실 세계를 객체 단위로 프로그래밍하며, 객체는 필드(데이터)와 메서드(코드)를 하나로 묶어 표현
* 프로그램을 유연하고 변경이 용이하게 만들기 때문에 대규모 소프트웨어 개발에 많이 사용
* 소프트웨어 개발과 보수를 간편하게 하며 직관적인 코드 분석이 가능

### 객체지향 주요개념
* 캡슐화(정보은닉)
  * 필드와 메서드를 하나의 캡슐처럼 포장해 세부 내용을 외부에서 알 수 없도록 감추는 것
* 상속
  * 상위 객체를 상속받은 하위 객체가 상위 객체의 메서드와 필드를 사용하는 것
* 다형성
  * 대입되는 객체에 따라서 메서드를 다르게 동작하도록 구현하는 기술
  * 실행 도중 동일한 이름의 다양한 구현체 중에서 메서드를 선택 가능

---

## 객체지향프로그래밍 언어 -Java

### Java의 목적
* Write Once Run Anywhere(한 번 작성되면 어디서든지 실행되어야함)
* Java는 platform independent하게 동작
* Super Computer부터 Smart Card까지 한 번 작성된 코드는 코드의 수정이 없이, 코드의 재컴파일없이 실행가능

### Java언어의 개발 목적
* Program개발을 쉽게 하였다.
* Compile환경이 아니라, Interpreted환경이다.
* 한 개의 이상의 thread를 사용할 수 있다.
* 동적으로 program을 변화시킬 수 있다.
* Code 자체적으로 security를 보장할 수 있다.

### Java Virtual Machine
* JVM은 System마다, 그리고, 운영체제마다 다름
* Java Application에서는 JDK안에서 실행
* Applet의 경우에는 browser안에 JVM(*.jar가 그 역할을 한다.)이 있어서 java Code를 실행
* Java compiler는 Source Code를 JVM에 대한 machine code instruction으로 변환하면, JVM으로 구현된 development tool에 의해서 interpreted됨

### Garbage Collection
* Java는 프로그래머에게 메모리를 release(최적화)하게 하는 책임을 지우지 않음
* Garbage Collector는 Java Program의 life cycle 동안 자동적으로 동작해서 de-allocate메모리에 필요와 메모리의 부족을 제거

### Process의 개념
* 프로그램 - 저장장치에 저장되어 있는 정적인 상태
* 프로세스 - 실행을 위해 메모리에 올라온 동적인 상태
* 프로그램이 프로세스가 된다는 것은 운영체제로부터 프로세스 제어 블록을 얻는다는 뜻
* 프로세스가 종료된다는 것은 해당 프로세스 제어 블록이 폐기된다는 뜻

### Thread의 개념
* 프로세스에서 실행 제어만 분리한 실행 단위(프로세스 시행부)
* 프로세서를 사용하는 기본 단위이며, 명령어를 독립적으로 실행할 수 있는 하나의 제어 흐름
* 같은 그룹의 스레드는 코드, 주소 공간, 운영체제의 자원(파일 신호)등을 공유

#### 멀티태스킹 : 운영체제가 CPU에 작업을 줄 때 시간을 잘게 나누어 배분하는 기법
#### 멀티프로세싱 : CPU를 여러 개 사용하여 여러 개의 Thread를 동시에 처리하는 작업 환경
#### CPU 멀티 Thread : 하드웨어적인 방법으로 하나의 CPU에서 여러 Thread를 동시에 처리하는 병령 처리 기법
#### 멀티 Thread : 운영체제가 소프트웨어적으로 프로세스를 작은 단위의 Thread로 분할하여 운영하는 기법

### 병행성(concurrency)문제
* 두개 이상의 Thread가 어떤 객체에 있는 하나의 데이터에 접근하게 되는 경우
* 서로 다른 두 스택에서 실행되는 메소드가 객체에 있는 동일한 객체에 대한 getter 또는 setter메소드를 호출하게 되는 경우
* Thread는 자신이 잠시 중단된 적이(interrupt)있다는 것을 기억할 수가 없음

### Thread에서의 동기화
* 다중 Thread환경에서 한번에 하나의 쓰레드만이 공유 데이터를 접근할 수 있도록 제어하는 것
* 여러 Thread가 동시에 실행되는 다중 Thread에서 데이터를 공유하기 위해서는 어떤 Thread가 다른 Thread의 상태와 행동 등을 고려





