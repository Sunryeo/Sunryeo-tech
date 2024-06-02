## ✔️ Java 조건문 > switch 문법

### ☑️ If문 예제 코드

```java
public class Switch1 {

  public static void main(String[] args) {
        int grade = 2;

        int coupon;
            if (grade == 1) {
                coupon = 1000;
            } else if (grade == 2) {
                coupon = 2000;
            } else if (grade == 3) {
                coupon = 3000;
            } else {
                coupon = 500;
            }
            System.out.println("발급받은 쿠폰 " + coupon);
  }
}
```

### 실행 결과

```
발급받은 쿠폰 2000
```

위 코드는 `switch`문으로 더 간결하게 작성할 수 있다.

### ☑️ switch문 예제 코드

```java
public class Switch2{
    public static void main(String[] args) {
        int grade = 2;

        int coupon;
        switch (grade) {
                case 1:
                    coupon = 1000;
                    break;
                case 2:
                    coupon = 2000;
                    break;
                case 3:
                    coupon = 3000;
                    break;
                default:
                    coupon = 500;
                }
                System.out.println("발급받은 쿠폰 " + coupon);
    }
}
```

### 실행 결과

```
발급받은 쿠폰 2000
```

위 예제처럼 `if문`과 `switch`문의 출력 결과는 동일하다.

### ☑️ swtich문의 특징

- `if`문을 좀 더 편리하게 사용할 수 있도록 하는 문법이다.
- `if`문은 비교 연산자를 사용할 수 있지만 `switch`문은 단순히 값이 같은 지만 비교할 수 있다.
- `switch`문은 조건식에 해당하는 특정값으로 실행할 코드를 선택한다.
- `break`문은 현재 실행 중인 코드를 끝내고 `switch`문을 빠져나가는 역할을 한다.
- 만약 `break`문이 없다면 실행중인 `case`문을 지나 다음 `break`를 만나기 전까지 멈추지 않고 이어서 실행된다.
- `switch`문은 사실상 사용하지 않고 `if`문만 사용해도 문제 없다. 다만 조건식이 단순한 값 비교 구문이라면 `if`문 보다 간결하게 사용할 수 있다는 장점이 있다.

### ☑ Java 14 새로운 switch문

- 기존 switch문은 if문 보다 간결한 것 같지만 생각보다 코드가 깔끔하진 않다. 이를 보완하여 새롭게 나온 switch문이 있다. Java 14 이후 버전부터 사용할 수 있다.

```java
public class Swtich3 {
    public static void main(String[] args) {
        int grade = 2;
        int coupon =
            switch (grade) {
            case 1 -> 1000;
            case 2 -> 2000;
            case 3 -> 3000;
            default -> 500;
            };
        System.out.println("발급받은 쿠폰 " + coupon);
    }
}
```

### 실행결과

```
발급받은 쿠폰 2000
```

- 기존 `switch`문과는 다르게 선택된 값을 반환하기 때문에 이를 변수에 할당할 수 있다.
