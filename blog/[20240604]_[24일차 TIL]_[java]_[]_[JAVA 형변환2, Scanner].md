## ✔️ 계산과 형변환

```java
public static void main(String[] args) {
    int div1 = 3 / 2;
    System.out.println("div1 = " + div1);

    double div2 = 3 / 2;
    System.out.println("div2 = " + div2);

    double div3 = 3.0 / 2;
    System.out.println("div3 = " + div3);

    double div4 = (double) 3 / 2;
    System.out.println("div4 = " + div4);

    int a = 3;
    int b = 2;
    double result = (double) a / b;
    System.out.println("result = " + result);
  }
```

출력 결과

```java
div1 = 1
div2 = 1.0
div3 = 1.5
div4 = 1.5
result = 1.5
```

- `div2`는 `double` 타입임에도 불구하고 `3 / 2`의 결과가 `1.5`가 아닌 `1.0`이 나온다. 이유는?
  - `int`와 `int`의 계산 결과를 `double` 변수에 담게 된 것이기 때문에 `1 → 1.0`으로 형변환되어 출력된다.
- 자바에서 같은 타입끼리의 계산은 같은 타입의 결과를 낸다.
  - `int + int = int`, `double + double = double`
- 서로 다른 타입의 계산은 큰 범위로 자동 형변환이 일어난다.
  - `int + long` → `long + long`, `int + double` → `double + double`

## ✔️ Scanner

<aside>
❓ 황당한 에러 대처기?!

</aside>

```java
System.out.print("실수를 입력하세요: ");
double doubleValue = scanner.nextDouble();
```

위 코드 작성 후 콘솔 출력 결과

![](https://velog.velcdn.com/images/elma98/post/ba0b0b10-cecd-4003-8760-482b7b4b645c/image.png)

이런 에러가 출력되었다..? 이 에러는 `InputMismatchException`인데, 입력받은 값의 타입이 맞지 않으면 발생하는 exception이다. 난 근데 분명 34.1을 정확히 입력했는데 왜..? 하고 stack over flow에 찾아봤더니

![](https://velog.velcdn.com/images/elma98/post/f4eed80d-cb25-4fa2-82b3-0fb4caa44268/image.png)

`,` 대신 `.` 을 소숫점으로 입력해서 그렇다고….

![](https://velog.velcdn.com/images/elma98/post/5194eb62-df1f-4003-acf3-fa5ecf3cf0bd/image.png)

`,`로 바꾸니까 정상출력된다.. 황당해서 기록해보는 에러핸들링 로그ㅋ ((o.<))

### ☑️ 예제코드

- `System.out`을 통해서 출력을 했듯이, `System.in`을 통해서 사용자의 입력을 받을 수 있다.(python의 `input` 같은 기능)
- `Scanner`라는 클래스를 활용하면 사용자의 입력을 편리하게 받을 수 있다.

```java
public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);

    System.out.print("문자열을 입력하세요: ");
    String str = scanner.nextLine(); // 입력을 String 값으로 가져온다.
    System.out.println("입력한 문자열: " + str);

    System.out.print("정수를 입력하세요: ");
    int intValue = scanner.nextInt(); // 입력받은 정수값을 가져온다.
    System.out.println("입력한 정수: " + intValue);

    System.out.print("실수를 입력하세요: ");
    double doubleValue = scanner.nextDouble(); // 입력받은 실수값을 가져온다.
    System.out.println("입력한 실수: " + doubleValue);
  }
```

- `Scanner scanner = new Scanner(System.in);`
  - `Scanner` 인스턴스를 생성해서 `System.in`을 사용하여 사용자의 입력을 편리하게 받도록 도와준다.
- `scanner.nextLine()`
  - 엔터를 입력하기 전까지의 문자를 가져온다.
- `scanner.nextInt()`
  - 입력을 `int` 형으로 가져온다.
- `scanner.nextDouble()`
  - 입력을 `double` 형으로 가져온다.
