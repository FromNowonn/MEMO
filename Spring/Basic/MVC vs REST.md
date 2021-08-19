# Spring MVC vs RESTful API

>Model + View + Controller

## MVC 패턴

스프링 프레임워크는 기본적으로 MVC 패턴을 지원합니다.

MVC 패턴이란 `Model`, `View`, `Controller` 세 부분으로 구분하여 개발하는 패턴을 말하는데

`Model`은 데이터를,

`View`는 데이터들의 입출력을,

`Controller`는 model에 대한 처리와 view 반환을 담당하는 구조이다.

MCV패턴은 구조가 간단하기 때문에 생산성을 증가시키는 장점이 있지만, 규모가 커질수록 유지보수가 어려워진다.

## RESTful API

Rest API는 http 프로토콜 위에서 Client가 Server를 호출해서 데이터를 받는 방식을 사용하기 쉽게 정리한 표준화된 방식을 의미함.

(html문서가 아닌 다른 데이터도 조회,수정,삭제가 가능하도록 표준화한 방식)

>즉, Controller + ResponseBody = RestController라 정의할 수 있다.

### 그렇다면, 왜 Rest방식을 사용하는가?

MVC 패턴에서 데이터를 받아서 화면에 노출 시키는 기능은 `View` 이다. 

이 때, Controller 방식은 뷰를 계속해서 리턴 시키는 방식을 사용한다.

하지만, Rest방식은 Json 혹은 XML형식으로 데이터만 전송하게 되므로, 

HTML + CSS + JavaScript 방식의 Controller 보다 생산성과 의존성이 증가한다.
