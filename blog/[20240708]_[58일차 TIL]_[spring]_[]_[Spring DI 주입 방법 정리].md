## ☑️ DI란?

- **Dependency Injection** 즉, 의존성 주입
- 쉽게 말해 dependencies(의존성) 부품을 필요한 객체에 주입하는 것

```java
// A가 필요로 하는 부품 클래스 B
class B {}

// 부품 클래스 B를 가져다 사용하는 A
class A {
    private B b;

    public A(B b) {
      this.b = b;
  }
}
```

## ☑️ DI 방법 3가지

### ✔️ 생성자 주입

```java
@Service
public class AService {
    private final BDependency bDependency;

    @Autowired
    public AService(BDependency bDependency) {
        this.bDependency = bDependency;
    }
}
```

- 생성자에 `@Autowired` 어노테이션을 붙여 주입한다.
- 주로 생성자 주입 방식이 권장 된다.
- `final` 키워드를 사용하여 초기화하기 때문에 불변성(Immutability)을 유지할 수 있다.
- 의존하는 객체가 많아질수록 코드 복잡도가 증가한다.

### ✔️ setter 주입

```java
@Service
public class AService {
    private BDependency bDependency;

    @Autowired
    public void setBDependency(BDependency bDependency) {
        this.bDependency =byDependency;
    }
}
```

- 세터 메서드에 `@Autowired` 어노테이션을 붙여 주입한다.
- 의존성을 나중에 변경하고 싶을 때 변경할 수 있다.
- 세터 메서드를 `public`으로 노출시켜야 하기 때문에 캡슐화가 약해질 수 있다.

### ✔️ field 주입

```java
@Service
public class AService {
    @Autowired
    private BDependency bDependency;
}
```

- 클래스의 필드에 `@Autowired` 어노테이션을 붙여 주입한다.
- 코드가 간결해진다는 장점이 있다.
- 하지만 의존성이 명확하게 표현되지 않아 코드의 가독성이 떨어질 수 있다.
