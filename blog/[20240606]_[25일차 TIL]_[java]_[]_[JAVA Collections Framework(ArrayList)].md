## ✔️ Collections Framework의 ArrayList

- `array`는 `array`가 한 번 생성되면 그 크기를 바꿀 수 없어서 `array` 안에 들어갈 요소가 몇 개가 될 지 모를 경우에는 사용하기 굉장히 까다롭다.

```java
public static void main(String[] args){
        String[] arr = new String[2];
        arr[0] = "A";
        arr[1] = "B";
        arr[2] = "C"; // 에러 발생
}
```

- 위와 같이 `arr`을 선언하고 `arr`의 길이를 벗어나는 2번째 인덱스에 값을 할당하려고 하면 아래와 같이 `ArrayIndexOutOfBoudsException`이 발생한다. 말 그대로 `array`의 index 범위를 초과하여 발생하는 에러이다.

![](https://velog.velcdn.com/images/elma98/post/750a012b-b810-414a-9427-5b075ab9a858/image.png)

- 이렇게 배열을 사용함에 있어 불편함이 있기 때문에 Java Collections Framework이 `ArrayList`라는 클래스를 제공한다.

### ☑️ ArrayList 예제코드

```java
ArrayList<Integer> al = new ArrayList<Integer>();
al.add(1);
al.add(2);

int value1 = al.get(0);
int value2 = al.get(1);

System.out.println(value1); // 1
System.out.println(value2); // 2
```

- `ArrayList`는 `add`라는 메서드를 통해 리스트 안에 요소를 집어넣을 수 있다.
- `ArrayList`는 `get`이라는 메서드에 리스트의 인덱스를 인자로 주어 요소에 접근할 수 있다.
- 배열과는 달리 `size`라는 메서드로 리스트의 크기를 알 수 있다.

‼️ `ArrayList` 안의 요소는 모두 기본적으로 `Object` 타입으로 저장되어 있다. 따라서 리스트 요소를 `String` 타입이나 `int` 같은 기본형 타입으로 선언한 변수에 할당하면 타입 캐스팅을 따로 해주어야 한다. 이러한 번거로움을 해결하고자 `ArrayList`에는 **_제네릭 타입_**을 줄 수 있는데, 이 **_제네릭 타입_**이 요소의 타입을 기본형 타입으로 캐스팅하는 역할을 한다. 제네릭 타입에 대해서는 추후에 추가로 자세하게 정리할 예정!

```java
ArrayList al = new ArrayList(); // 제네릭 타입을 안주면
al.add(1);
al.add(2);

int value1 = al.get(0); // 여기서 에러가 발생한다.
int value2 = al.get(1); // 여기도

System.out.println(value1);
System.out.println(value2);
```

![](https://velog.velcdn.com/images/elma98/post/9f83a04e-e8d1-4d3a-ab6a-43e4811a0830/image.png)

- Provided type에 `Object`라고 써 있는 것이 보인다. 따라서 `value1`과 `value2`를 `int` 타입으로 캐스팅하기 위해서는 `ArrayList<Integer>` 이렇게 제네릭 타입을 주어야 한다.
- 제네릭 타입에는 `wrapper class`만 할당할 수 있는데, `wrapper class`는 기본형 데이터를 클래스로 감싼 타입이다. 지금은 _‘기본형 데이터를 클래스로 사용하기 위해 존재하는 클래스’_ 라는 것 정도만 인지하고 넘어가도록 하자.
