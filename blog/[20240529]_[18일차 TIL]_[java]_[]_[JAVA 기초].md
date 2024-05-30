### 💅🏻 들어가기 전 간단 기술 면접 팁

- 면접에서 cs 질문 대답할 때는 a-z를 말하려고 하기 보다 핵심만 말하려고 연습하기!
- 면접에서 자바 버전 아는거 있냐 물어보면 8, 17, 21 버전이 LTS 버전임. 이거 대답하면 됨(?)
- 8버전 변경사항은 필수, record 기능, 21버전에 가상 스레드

## ✔️ 자바의 특징

### 1. 객체 지향 언어(OOP)

- Object Oriented Programming
- 프로그램을 작성할 때 객체들을 만들어 서로 소통하도록 하는 방법

### 2. 메모리 자동 관리를 위한 가비지컬랙션(Garbage Collection)

- 프로그램이 필요로하지 않는 메모리 공간을 알아서 지워주고 확보함
- 자바, 자바스크립트, 파이썬과 같은 고수준(high-level) 언어에는 가비지 컬랙터가 존재한다.
- 메모리 할당(Allocate Memory) → 메모리 사용(Use Memory) → 메모리 해제(Release Memory)

### 3. 중요!!! JVM(Java Virtual Machine)

<aside>
🌟 기술 면접 시 질문으로 들어오면 JVM의 동작 원리까지 설명할 수 있어야 함.

</aside>

- JVM이란?: 자바 바이트코드(`.class` 파일)를 OS에 특화된 코드로 변환하여 실행하는 역할을 한다.
- 개발자가 작성한 소스 코드는 `.java`의 형태로 저장된다.
- `.java` 코드를 javac(자바 컴파일러)가 Byte code로 변환시킨다, 이 때 파일은 `.class`의 형태로 저장된다.
- `.class` 파일을 `Class Loader`가 JVM 메모리 영역 즉, `Runtime Data Area`로 로딩시킨다.
- `Runtime Data Area`는 다섯가지 영역으로 이루어져 있다.
  - `Method Area` & `Heap`: 모든 스레드가 공유하는 공간
  - `Stack` & `PC Register` & `Native Method Stack`: 스레드마다 하나씩 생성되는 공간
  - `Method Area`: JVM이 시작될 때 생성되는 공간으로 바이트코드가 이 영역에 저장된다. 클래스 정보, 변수 정보, static으로 선언한 변수가 저장된다.
  - `Heap`: 동적으로 생성된 객체가 저장되는 영역으로 GC의 대상이 되는 공간이다. `new` 키워드로 생성된 인스턴스, 배열 등이 저장된다. 이 데이터는 GC가 정리하기 전까지 이 영역에 남아있다.
  - `Stack`: 지역변수, 메서드의 매개변수, 메서드의 정보가 저장되는 영역이다. 금방 사용하고 사라지는 데이터가 저장되는 영역
  - `PC Register`: 스레드가 시작될 때 생성되며, 현재 수행중인 JVM의 명령어 주소를 저장하는 공간이다. 스레드가 어떤 부분을 어떤 명령어로 수행할 지를 저장하는 공간.
  - `Native Method Stack`: Java가 아닌 다른 언어로 작성된 코드를 위한 공간이다.
- `Runtime Data Area`에 로딩된 `.class` 파일은 `Execution Engine`에 의해 해석된다. `Execution Engine`은 로드된 바이트 코드를 실행시키는 엔진이다.
- `Native Method Interface`: JVM에 의해 실행되는 코드 중 네이티브로 실행하는 것이 있다면 해당 네이티브 코드를 호출하거나 호출될 수 있도록 만든 일종의 프레임워크
- `Native Method Libraries`: 네이티브 메소드 실행에 필요한 라이브러리

![](https://velog.velcdn.com/images/elma98/post/22481198-d26a-418d-adeb-131677badc20/image.png)

![](https://velog.velcdn.com/images/elma98/post/e3afa78f-d038-41de-82c1-7c3596518db2/image.png)

**_이미지 출처: https://www.youtube.com/watch?v=AWXPnMDZ9I0 영상 참조_**
