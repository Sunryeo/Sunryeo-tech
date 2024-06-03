## ✔️ 삼항연산자

### ☑️ If문 예제

```java
public static void main(String[] args) {
    int age = 10;
    String status;
    if (age >= 18) {
      status = "성인";
    } else {
      status = "미성년자";
    }
    System.out.println("age = " + age + "status = " + status);
  }
```

출력결과

```java
age = 10 status = 미성년자
```

### ☑️ 삼항연산자 예제

```java
public static void main(String[] args) {
	int age = 10;
	String status = (age >= 18) ? "성인" : "미성년자";
	System.out.println("age = " + age + "status = " + status);
}
```

출력결과

```java
age = 10 status = 미성년자
```

- 말 그대로 항이 3개인 연산자여서 삼항연산자
- 단순 `if-else` 문을 대체할 수 있다. 이런 경우 코드를 간결하게 작성할 수 있다는 장점이 있다.
- `if`문처럼 코드 블럭을 넣을 수 있는 것은 아니고 단순한 표현식만 넣을 수 있다.

## ✔️ 형변환

- 자바에서 숫자를 표현할 수 있는 범위는 다음과 같다.
  - `int` < `long` < `double`
  - `int` 보다 `long`이, `long` 보다 `double`이 더 큰 숫자의 범위를 표현할 수 있다.
- 작은 범위 타입의 데이터를 큰 범위 타입 데이터에 대입하는 것은 특별한 문제 없이 수행된다.

```java
public static void main(String[] args) {
        int intValue = 10;
        long longValue;
        double doubleValue;

        longValue = intValue; //int -> long
        System.out.println("longValue = " + longValue);

        doubleValue = intValue; //int -> double
        System.out.println("doubleValue = " + doubleValue);

        doubleValue = 20L; //long -> double
        System.out.println("doubleValue2 = " + doubleValue);
    }
```

출력결과

```java
longValue = 10
doubleValue = 10.0
doubleValue2 = 20.0
```

- `long → double`의 경우에도 `double`은 부동 소수점을 사용하기 때문에 더 큰 숫자 범위를 표현한다. 따라서 대입할 수 있다.

### ☑️ 자동 형변환

- 하지만 자바는 결국 같은 타입끼리만 대입이 가능하기 때문에 개념적으로는 아래와 같이 동작함

```java
intValue = 10
doubleValue = (double) intValue // 형 맞추기
```

- 이렇게 대입할 값 앞에 `(double)`을 붙여주면 형변환이 된다. 작은 범위를 큰 범위에 대입할 때는 이와 같이 자바가 자동으로 형변환 과정을 거치기 때문에 개발자가 직접 `(double)`을 써주지 않아도 된다. 이를 **자동 형변환** 또는 **묵시적 형변환**이라 한다.

### ☑️ 명시적 형변환

- 큰 범위에서 작은 범위 대입은 명시적 형변환이 필요하다.

```java
public static void main(String[] args) {
        double doubleValue = 1.5;
        int intValue = 0;

        intValue = doubleValue; //컴파일 오류 발생
        System.out.println(intValue);
    }
```

출력 결과

![](https://velog.velcdn.com/images/elma98/post/c223a92f-b2db-42f0-a469-7e469622f89d/image.png)

- `int`에 `double`을 대입할 경우 소숫점 뒷자리를 전부 절삭해버리기 때문에 자동으로 형변환 되지 않고 컴파일 오류를 발생시킨다.
- 그러나 개발자가 의도하여 강제로 형변환을 원할 경우 `(int)`를 붙여줌으로써 형변환이 가능하다.

```java
    public static void main(String[] args) {
        double doubleValue = 1.5;
        int intValue = 0;

        intValue = (int) doubleValue; ///형변환
        System.out.println(intValue);
    }
```

출력 결과

```java
1
```

- 이 경우 소숫점 뒷자리를 절삭하고 앞부분 정수만 출력되고 컴파일 오류가 발생하지 않게 된다.
- `int`형은 `double`형보다 숫자의 표현 범위가 작고 실수를 표현할 수도 없기 때문에 `int`형에 `double`형 데이터를 대입하게 되면 데이터 손실이 발생한다. 개발자가 의도하지 않은 상황에서 이러한 데이터 손실이 오류없이 작동된다면 굉장히 큰 버그를 발생시킬 수 있다. 따라서 자바는 이런 경우 컴파일 오류를 발생시킨다.

### ☑️ 형변환 과정

```java
doubleValue = 1.5
intValue = (int) doubleValue;
intValue = (int) 1.5; // doubleValue에 있는 값을 읽는다.
intValue = 1; // int로 형변환 한다. intValue에 int형인 숫자 1을 대입한다.
```

- 형변환을 한다고 해서 `doubleValue` 자체의 타입이 변경되거나 값이 변경되는 것은 아니다. 변수의 값은 대입연산자를 대입연산자 `(=)`를 사용해서 직접 대입할 때만 변경된다.

### ☑️ 형변환과 오버플로우

<aside>
❓ 형변환을 할 때 만약 작은 숫자가 표현할 수 있는 범위를 넘어서면 어떻게 될까?
</aside>

```java
   public static void main(String[] args) {
        long maxIntValue = 2147483647; //int 최고값
        long maxIntOver = 2147483648L; //int 최고값 + 1(초과)
        int intValue = 0;

        intValue = (int) maxIntValue; //형변환
        System.out.println("maxIntValue casting=" + intValue);

        intValue = (int) maxIntOver; //형변환
        System.out.println("maxIntOver casting=" + intValue);
    }
```

출력 결과

```java
maxIntValue casting=2147483647
maxIntOver casting=-2147483648
```

- `int`가 표현할 수 있는 범위를 초과할 경우 `int`가 표현할 수 있는 가장 작은 숫자로 다시 돌아가서 출력된다.
- 이렇게 시계가 한바퀴 돈 것 처럼 다시 가장 작은 수로 돌아가서 표현되는 현상을 **오버플로우**라 한다.
- 이렇게 오버플로우가 발생하면 그냥 `int` 를 `long`으로 형변환 하면 된다! 오버플로우는 일어나면 안되는 현상 즉, 버그/오류이다.
