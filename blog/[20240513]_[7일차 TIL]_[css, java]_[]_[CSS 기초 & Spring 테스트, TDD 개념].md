## ☑️ flex-item

- 자식 요소에 적용할 수 있는 `flex` 속성

### ✔️ flex-basis

- `flex-item`의 초기 크기를 설정한다.
- `width`, `height`와 다른 점은 축의 방향에 따라 달라진다는 것과 내부 콘텐츠의 길이에 따라 유연한 크기를 가진다는 것이다.
- 이 속성이 적용되어 있다면 `row`일 경우 `width` 값이, `column`일 경우 `height` 값이 무시된다.

### ✔️ flex-grow

- 아이템이 컨테이너 내부에서 할당할 수 있는 공간의 정도를 지정한다.
- 값으로 0을 주면 늘어나지 않는다.
- `flex-grow: 1` ⇒ 자식 요소들이 모두 동일한 크기의 공간을 할당 받는다.
- `flex-grow: 2 이상의 수` ⇒ 특정 하나의 자식에게만 줄 경우 해당 요소만 다른 자식요소에 비해 n배수의 여백 공간을 할당 받는다.

### ✔️ flex-shrink

- 아이템의 크기를 고정하거나 축소할 때 사용한다.
- 값으로 0을 주면 줄어들지 않는다.

<aside>
🌟 금일 강의 JavaScript 부분은 이미 아는 내용이라 다른 주제로 대체함!
</aside>

❗️해당 정리 내용은 아래 강의 내용을 바탕으로 정리되었습니다.

https://www.inflearn.com/course/자바-스프링-테스트-개발자-오답노트

## ☑️ 프로젝트에서 테스트가 왜 필요한가?

### ✔️ 잘못된 테스트 도입 상황 가정

- 어떻게든 돌아가는 코드로 이루어진 서비스가 있다.
- 이 코드는 3-4년 전에 쓰여진 코드로 당시에는 열심히 짠 코드였으나 현재는 레거시 코드가 되었다.
- 이 서비스는 그동안 큰 성장세를 보였고 유저도 계속 늘어나고 있는 상향세의 서비스이다. 따라서 앞으로 추가될 기능도 많아서 개발 인력 충원이 필요하다.
- 개발 속도 향상을 위해 개발 인력을 두 배로 충원하였다. 그러나 인력은 두 배로 늘었지만 개발 속도는 그에 비례하여 빨라지지 않았다. 약 1.2배 정도 빨라진 것 같다. 이유는 인력이 늘어나면 커뮤니케이션 비용이 발생하기 때문에 정비례하여 속도가 빨라지지 않기 때문이다.
- 하지만 아무리 정비례로 빨라지지 않는다고 하더라도 최소 1.5배는 상승해야 할 것 같은데 개발 속도가 너무 더디다, 그래서 개발자들의 생각을 들어보니
- 새로 추가된 기능이 많아 본인이 새로 작성한 코드들이 기존에 잘 돌아가던 기능에 영향을 주게 되진 않을지 걱정이 되어 배포하기가 두렵다고 한다.
- 이 때 기존에 잘 작동하던 기능들에 새로운 코드가 추가되면서 갑자기 정상작동하지 않고 버그가 발생하는 것을 `regression bug` 즉, 회귀 버그라고 한다.
- 이러한 걱정과 문제점을 해결하기 위해 테스트 코드를 추가하기로 했다.
- 하지만 프로젝트 성과 보고를 위해서는 눈에 보이는 지표로 성과를 증명해야만 한다. 그러나 테스트 코드 추가 및 테스트 자동화 만으로는 그러기엔 한계가 있다. 따라서 가시적인 성과를 내기 위해 커버리지를 50%까지 끌어올리는 것을 목표로 정한다.
- 그런데 이게 테스트 코드를 하나씩 붙이다보니 정말 간단한 기능을 추가하는데도 테스트 코드 붙이는데 시간이 더 많이 걸려서 생산성이 떨어지게 된다. 커버리지를 올려야 해서 테스트 코드를 안붙일수도 없고 붙이면 이 테스트 코드는 쓰는데 시간만 오래 걸리고 딱히 필요한 테스트 케이스도 아니게 된다.
- 그리고 테스트 코드를 붙이면 붙일수록 전에 써둔 코드들 중 리팩토링이 필요해보이는 코드들이 눈에 밟힌다. 이걸 수정해가며 테스트 코드를 쓰기엔 또 시간이 너무 많이 소요되어 그냥 지나치고 계속 테스트 코드를 써내려 간다.
- 그러다보니 전에는 잘 통과하던 케이스들이 갑자기 실패하는 일이 발생한다. 열심히 쓴 테스트 코드들의 테스트 결과가 일관되지도 않다. 그러면서 문제가 없는 코드를 디버깅하는데 시간을 낭비하게 된다.
- 어찌저찌 커버리지 50%는 달성을 했는데 이게 테스트 케이스가 너무 많아 한 번 테스트 하는데 시간이 너무 오래 걸리고 케이스들이 한 눈에 직관적으로 무엇을 테스트 하는지 잘 보이지도 않는다. 이쯤 되니 “이럴거면 테스트 코드 왜 작성했지” 하는 회의가 든다.

### ✔️ 그럼 무엇이 잘못되었을까?

- 레거시 코드에 테스트를 붙이는 것은 TDD가 아니다.
- 레거시 코드에 테스트를 붙이려면 코드 개선이 필요하다.
  - 테스트의 목적에는 회귀 버그 방지를 위해서도 있지만 설계를 유연하게 가져가기 위함도 있다.
  - 기존의 설계보다 더 유연한 확장이 가능하고 테스트를 쉽게 할 수 있도록 설계를 진화시켜야 한다.
  - 테스트를 고민하면 설계가 개선되고, 설계를 고민하면 테스트가 쉬워진다 → 선순환
  - 이를 가능하게 하기 위해서는 테스트 진행과 동시에 코드 개선도 함께 이루어져야 한다.
- 커버리지에 집착하면 안된다.
  - 테스트를 진행하다 보면 테스트를 굳이 할 필요 없는 기능들이 존재한다.
  - 테스트를 추가했을 때 얻을 수 있는 효용성을 따지는 것이 목적이 아닌 커버리지 자체가 목적이 되어서는 안된다.
- 따라서 커버리지를 올리기 위한 mock 프레임워크 사용법만 고민하는 것이 아닌, 왜 테스트를 해야 하고, 어떻게 테스트 해야 하는지 고민했어야 한다.

### ✔️ 결론

- TDD를 논하기 전에 프로젝트는 우선 테스트가 가능한 구조로 변경 되어야 한다.

<aside>
🔓 간단 회고
지금까지 실무 개발 업무를 포함한 나의 개발 전반의 경험상 테스트를 추가한 프로젝트를 경험한 적은 없다. 하지만 지난 실무에서의 프로젝트 경험을 바탕으로 테스트 코드가 개발 생산성을 크게 높여주고 QA 단계에서 더 체계적이고 결정적인 테스트가 가능하도록 만들어준다는 것을 크게 느꼈다. 하지만 테스트 도입이 단지 테스트 코드 추가를 위해서 이루어지면 안된다는 점까지 멀리 보지는 못했다. 자칫하면 보여주기식, 남기기식 코드조각 따위로 전락할 수도 있기 때문에 설계의 유연성과 함께 가져가야 한다는 포인트는 이 주제를 관통하는 가장 중요한 포인트이다. 아직 나는 설계의 확장성, 유연성을 고려하고 큰 그림을 그리기에는 너무 주니어이지만 앞으로 시니어가 되는 과정에서 좋은 코드를 짜는 개발자가 되기 위해서는 이 부분을 괄시해서는 안된다는 점을 배웠다. 오늘은 대단히 실용적이고 유용한 개발지식을 공부한 것은 아니지만 가장 중요한 것을 배웠다!

</aside>
