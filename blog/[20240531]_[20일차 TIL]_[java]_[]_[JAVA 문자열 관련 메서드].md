## ✔️ 문자열 내장 메서드

### ☑️ equals

- String 객체를 비교할 때 문자열 자체 데이터 값이 같은지 비교하는 메서드.
- `==` 로 비교하면 주소값으로 비교하기 때문에 같은 문자열이라도 다른 값으로 판단함.

  ![](https://velog.velcdn.com/images/elma98/post/026cb40a-248d-4f70-8b86-5ab7bffd04c8/image.png)

### ☑️ replaceAll & replace

- 문자열을 대체함
- `replace`: 첫번째 인자로 대체하고자 하는 문자열을 받음
- `replaceAll`: 첫번째 인자로 정규식을 넣을 수 있음. 인자로 넘겨준 정규식에 걸리는 문자열 모두를 대체함
  ![](https://velog.velcdn.com/images/elma98/post/4eac482e-eb4e-4320-b988-4d43da4e3d91/image.png)

### ☑️ substring

→ _js에 `slice` 와 유사한 기능의 메서드_

- 문자열의 인덱스에 맞추어 문자열을 자름
- 두번째 넘겨준 인자의 인덱스 바로 직전까지 자름
  ![](https://velog.velcdn.com/images/elma98/post/9218e970-06c2-48e0-8cab-17f420e9f488/image.png)

## ✔️ 문자열 포맷팅 메서드 - format

→ _python의 `format`과 유사한 기능의 메서드_

- 문자열에 특정 데이터 값을 집어 넣어 포맷팅 하는 메서드
- `%s`가 위치해 있는 순서대로 각각 포맷팅 됨
  ![](https://velog.velcdn.com/images/elma98/post/84237eb2-f794-46ed-b0fb-9b59dc2ca2ff/image.png)

## ✔️ StringBuffer vs StringBuilder

- `String` 객체는 내부 문자열을 수정할 수 없다.
- 따라서 + 연산자로 새로운 문자열을 붙일 때마다 새로운 객체가 생성되어 메모리 용량을 다수 차지하게 된다는 단점이 있다.
- 이 단점을 보완하여 나온 객체가 `StringBuffer`와 `StringBuilder`이다.
- `StringBuffer`는 내부 버퍼에 문자열을 저장하고 내부에서 추가, 수정, 삭제 작업을 자유롭게 할 수 있다.
- 멀티 스레드 환경에서 `StringBuffer`를 사용한다.(_`StringBuilder`보다 안전하기 때문_)
- 단일 스레드 환경에서 `StringBuilder`를 사용한다.(_성능이 더 좋기 때문_)
  ![](https://velog.velcdn.com/images/elma98/post/11598e46-d082-4a5e-afe2-4d2f8bf283a1/image.png)

<aside>
🌟 스레드에 대해서는 추가로 정리 예정
</aside>
