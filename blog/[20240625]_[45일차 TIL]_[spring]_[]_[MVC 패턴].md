## ✔️ MVC 패턴

- `Model` / `View` / `Controller` ⇒ 유지보수가 용이하도록 각각의 역할을 나눈 코드 구성 방식

### ☑️ MVC 패턴의 구조와 흐름

1. 사용자가 요청을 보냄(예를 들어 상품 리스트 불러오기 같은)
2. 사용자의 요청을 `controller`가 받아서 `model`에 해당 요청 사항과 관련된 데이터를 요청함
3. `model`은 관련 데이터를 `controller`로 넘겨줌
4. `controller`는 `model`에게서 받은 데이터를 `view`로 전달함
5. `view`는 받은 데이터를 사용자 편의에 맞추어 UI에 예쁘게 포장해서 사용자에게 보여줌

### ☑️ MVC 각각의 역할

- `Model`: 데이터를 다루는 부분, 애플리케이션의 데이터베이스, 상수, 변수 등을 의미
- `View`: 사용자한테 보여지는 부분, 사용자 인터페이스 요소를 의미
- `Controller`: Model과 View의 중개자 역할을 하는 부분

### ☑️ MVC를 지키면서 코딩하는 방법

- `Model`은 `Controller`와 `View`에 의존하지 않아야 한다. 즉, `Model` 내부에 `Controller`와 `View`에 관련된 코드가 존재해서는 안된다.
  - `OutputView`에서 `Student`를 파라미터로 받고 있다.
  - View(`OutputView`)에는 Model(`Student`)과 관련된 코드가 존재할 수 있다.
  - 하지만 `Controller`와 관련된 코드는 존재하면 안된다.

```java
// Model

package Java240625.mvc;

public class Student {
  private String name;
  private int age;

  public Student(String name, int age) {
    this.name = name;
    this.age = age;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public int getAge() {
    return age;
  }

  public void setAge(int age) {
    this.age = age;
  }
}
```

```java
// View

package Java240625.mvc;

public class OutputView {
  public static void printProfile(Student student) {
    System.out.println("내 이름은 " + student.getName() + "입니다.");
    System.out.println("저는 " + student.getAge() + "세 " + "입니다.");
  }
}
```

- `View`는 `Model`에만 의존해야 하고, `Controller`에는 의존해서는 안된다.
- `View`가 `Model`로부터 데이터를 받을 때는, 사용자마다 다르게 보여주어야 하는 데이터에 대해서만 받아야 한다.
  - 모든 사용자에게 공통으로 보여지는 데이터(UI 레이아웃과 관련된 정보)는 `View` 자체가 가지고 있어야 하며, 사용자마다 다르게 표시되는 정보(프로필 정보, 마이페이지 데이터 등)만 `Model`을 통해서 받아야 한다.
  - `View` 자체가 가지고 있어야 하는 정보를 `View`가 외부 파라미터로 받는 등 외부 데이터에 의존하게 되면 MVC를 지키지 않은 코드 구조가 된다.
- `Controller`는 `Model`과 `View`에 의존해도 된다.

```java
package Java240625.mvc;

public class Controller {
    public static void main(String[] args){
        Student student = new Student("홍길동", 25); // Model
        OutputView.printProfile(student); // View
    }
}
```

- `View`가 `Model`로부터 데이터를 받을 때는 반드시 `Controller`를 통해서 받아야 한다.
  - 아래와 같은 예로, `Controller`를 거치지 않고 `View` 내부에서 `Model`을 직접 생성하여 사용자 화면에 보이는 구조는 MVC를 지키지 않은 코드 구조이다.

```java
// MVC의 잘못된 예시

package Java240625.mvc;

public class OutputView {
  public void printProfile() {
    Student student = new Student("홍길동", 25); // View 내부에서 Model을 직접 생성
    System.out.println("내 이름은 " + student.getName() + "입니다.");
    System.out.println("저는 " + student.getAge() + "세 " + "입니다.");
  }
}
```
