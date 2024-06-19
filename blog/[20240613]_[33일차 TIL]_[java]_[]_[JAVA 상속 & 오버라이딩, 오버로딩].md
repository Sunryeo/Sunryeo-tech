## ✔️ 상속(Inheritance)

### ☑️ 상속이란?

- 자바에서 상속이란, 부모 클래스로부터 자식클래스가 필드, 메서드 등을 물려받아 자식클래스에서 사용할 수 있게 하는 것을 의미한다.
- 상속은 클래스의 재사용을 용이하게 하기 때문에 코드의 중복을 줄여준다는 장점이 있다.

### ☑️ 부모 생성자 호출

- 자식 클래스를 생성할 때는 부모 생성자가 먼저 호출된다.
- 부모 생성자는 자식 생성자의 맨 첫 줄에서 호출된다.

_예시_

```java
// 부모 클래스

public class Animal {
  protected String kind;

  public Animal(String kind) {
	  this.kind = kind;
  }
}
```

```java
// 자식 클래스

public class Cat extends Animal {

  public Cat(String kind) {
    super(kind);
  }
}
```

- `super()` 는 상위 클래스를 의미한다.
- 부모 생성자에 필요한 필드가 있다면 자식 클래스의 생성자도 이를 상속받아 `super`로 받아주어야 한다.

## ✔️ Overloading & Overriding

### ☑️ overloading

- 이름과 리턴 타입이 같고 매개변수가 다른 메서드

_예시_

```java
public String run() {
	return "달리는 중";
}

// 매개변수만 다른 두 함수

public String run(String engine) {
  return engine + "으로 달리는 중";
}
```

### ☑️ overriding

- 부모 클래스에게서 상속받은 메서드를 재정의하는 것, 추상클래스의 추상메서드나 인터페이스의 메서드를 구현하는 것도 오버라이딩이다.
- `@Override` 어노테이션을 같이 사용해야 한다.

예시

```java
public abstract class Animal {
  public abstract void sound(); // 추상메서드
}
```

```java
public class Cat extends Animal {
  @Override
  public void sound() {
    System.out.println("miumiu");
  }
}
```
