## ✔️ Thymeleaf란?

- Java 기반의 **서버 사이드 템플릿 엔진** 중 하나이다.(SSR을 위한 템플릿 엔진)
  - 서버 사이드 템플릿: 서버에서 템플릿 구성을 하는 방식으로, 데이터를 정해진 템플릿에 넣어 HTML을 그려서 클라이언트에 전달해주는 역할을 한다.
- Thymeleaf 템플릿은 유효한 HTML 구조를 가지므로 웹 브라우저에서 열어볼 수 있다.
- 다양한 표현식을 지원하여 데이터를 처리하는데 효과적이다.
- 스프링 프레임워크와의 연동을 지원하기 때문에 스프링 MVC 패턴에서 쉽게 사용할 수 있다.
- 사용자가 많은 웹페이지는 SSR로 구현하지 않는다. SSR로 구현하는 페이지는 사내 관리자 페이지 등 사용자가 한정된 웹페이지에서 주로 구현한다.

## ✔️ `@Controller`

### ‼️`@Controller` vs. `@RestController`

- `@Controller`: String return값이 해당 view를 찾아서 반환(MVC 개발)
- `@RestController`: return 값을 json으로 변환하여 반환(API 개발)

### ☑️ `@Controller`란?

- `@Controller` 는 Spring MVC에서 사용되는 어노테이션으로써 클래스가 웹 요청을 처리하는 컨트롤러 역할을 하는 어노테이션이다.
- 주요 역할:
  - 요청 매핑: `@RequestMapping`, `@Getmapping`, `@Postmapping` 등의 어노테이션을 사용하여 특정 URL에 대한 요청을 처리하는 메서드를 정의한다.
  - 데이터 준비 및 모델 생성: 컨트롤러는 서비스 계층을 호출하여 데이터를 가져오고 이를 Model 객체에 담아서 뷰에 전달하는 역할을 한다.
  - 뷰 선택 및 렌더링: 컨트롤러는 처리 결과에 따라 적절한 뷰를 선택하고, 모델 데이터를 전달한다.
  ```
  사용자 요청 -> @Controller -> 서비스 계층 호출 -> 모델 데이터 준비 -> 뷰 이름 반환 -> ViewResolver -> Thymeleaf 템플릿 -> HTML 생성 -> HTTP 응답 반환
  ```

## ✔️ Thymeleaf HTML 파일 작성하기

- 프로젝트 디렉토리 src/main/resources/templates에 `index.html` 파일을 생성한다.
- 해당 html 파일 최상단에 `<html xmlns:th="http://www.thymeleaf.org">` 를 입력한다.
- 해당 코드가 이 html 파일은 일반 html파일이 아니라 thymeleaf에 의해 제공되는 html 파일임을 명시한다.

- `Controller`파일에서 원하는 엔드포인트의 요청 처리 메서드를 만들고 String 값으로 아까 작성했던 html 파일명과 같은 값의 문자열을 리턴 해준다.(지금의 경우 index를 리턴)
- 해당 엔드포인트로 요청을 보내면 thymeleaf 엔진이 요청에 맞는 뷰를 찾아 렌더링한다.
