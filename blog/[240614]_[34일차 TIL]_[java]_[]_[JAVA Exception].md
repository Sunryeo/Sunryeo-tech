## ✔️ 에러 vs. 예외

### ☑️ 에러란?

- 에러(Error)란 프로그램 실행 중에 발생하는 문제로, 프로그램의 비정상적인 종료를 야기한다.
- 에러는 프로그래머가 핸들링할 수 없고 예측 불가하다.
- 에러는 주로 JVM에서 발생하며, 대표적인 에러의 예로는 `OutOfMemoryError` , `StackOverflowError` 등이 있다.

### ☑️ 예외란?

- 예외(Exception)란 프로그램 실행 중에 발생하는 비정상적인 상황이다.
- 예외는 프로그래머가 예측가능하고 이를 핸들링할 수 있다.
- 예외를 처리하는 방법은 대표적으로 두 가지가 있다.
  - `try-catch` 문을 사용해 예외를 처리
  - 메서드에서 `throws` 키워드를 사용하여 해당 메서드를 호출한 곳으로 에러를 전파
- 대표적인 예외의 예로는 `NullPointerException`, `ArratyOutOfBoudsException` 등이 있다.
- 모든 예외의 최상단 부모 클래스는 `Throwable` 클래스이다.
- `Throwable` 클래스 아래 첫 번째 자식 클래스로 `Error` 와 `Exception` 으로 나뉘게 되고 `Exception` 에서 다시 `RuntimeException` 과 `IOException` 으로 나뉘게 된다.
- `RuntimeException` 은 언체크드(`unchecked`) 예외이다.
- 언체크드 예외는 주로 프로그래밍 오류에 의해 발생하고, 체크드 예외는 주로 외부 요인(파일, 네트워크 등)에 의해 발생하는 예외이다.

### ‼️ Checked Exception vs. Unchecked Exception

- `unchecked`: **컴파일 시점에서(!!)** 예외 처리를 강제하지 않음. 즉, 예외처리를 하지 않아도 컴파일 오류가 발생하지 않는다. 예외처리를 하지 않으면 런타임 익셉션으로 프로그램 실행 종료되는 것은 별개의 문제
- `checked`: 컴파일 시점에서 예외 처리를 강제한다.

### ☑️ 예외 처리 방법

1. `try-catch` 블록 사용

```java
public class Test {
  public static void main(String[] args){
    System.out.print("원하는 배열의 크기를 입력하세요: ");
    int length = sc.nextInt();
    int[] arr = new int[length];

    for (int i = 0; i < arr.length; i++) {
      arr[i] = i;
    }

    System.out.print("원하는 배열의 인덱스를 입력하세요: ");
    int idx = sc.nextInt();

    try {
      System.out.println("result: " + arr[idx]);
    } catch (ArrayIndexOutOfBoundsException e) {
      System.out.println("인덱스를 벗어났습니다.");
    } finally {
      sc.close();
    }
  }
}
```

- `try` 블록에서 시도한 코드에 예외가 터지면 `catch` 블록에서 잡아서 개발자의 의도대로 예외를 처리한다.
- `finally` 블록은 예외 발생 여부와 상관없이 마지막에 실행되어야 하는 코드를 주로 삽입한다. 주로 scanner 해제 또는 db 커넥션 풀 해제 등 자원의 해제와 관련된 행위를 실행한다.

1. `throws` 키워드로 예외 전파

```java
public class Test {
  public static void main(String[] args){
    private static int divide(int a, int b) throws ArithmeticException {
	    return a / b;
	  }

	  public static void main(String[] args){
			try {
	      divide(10, 0);
	    } catch (ArithmeticException e) {
	      System.out.println("0으로 나눌 수 없습니다.");
	    } finally {
	      System.out.println("이건 예외여부와 상관없이 항상 실행됩니다.");
	    }
	  }
  }
}
```

_실행결과_

![](https://velog.velcdn.com/images/elma98/post/bd195c3a-3614-4baa-9802-74ce9930e4d6/image.png)

- `divide` 메서드에서 전파한 예외를 메서드를 호출한 실행함수 catch 블록에서 잡아서 예외를 처리한다.

## ☑️ 커스텀 예외 만들기

- `Exception` 객체를 상속받아 예외를 커스텀 할 수 있다.
- 1로 나누면 예외가 터지도록 하는 메서드가 있다고 가정하고 아래와 같이 커스텀한 예외 객체를 핸들링 할 수 있다.

_예시_

```java
public class Division {

  public int divide(int a, int b) throws CannotDivideException {
    if (b == 1) {
      throw new CannotDivideException("1로 나눌 수 없습니다.");
    }

    return a / b;
  }
}

```

```java
public class CannotDivideException extends Exception{
    public CannotDivideException(String message) {
        super(message);
    }
}
```

```java
public class Test {
	  public static void main(String[] args){
			Division div = new Division();

	    try {
	      div.divide(10, 1);
	    } catch (ArithmeticException e) {
	      System.out.println("0으로 나눌 수 없습니다.");
	    } catch (CannotDivideException e) {
	      System.out.println(e.getMessage());
	    } finally {
	      System.out.println("이건 예외여부와 상관없이 항상 실행됩니다.");
	    }
  }
}
```

_실행결과_

![](https://velog.velcdn.com/images/elma98/post/a3346204-1ab9-4f22-ba6c-8ee8a1dcfda0/image.png)
