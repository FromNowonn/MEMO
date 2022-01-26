# JPA(Java Persistence API)

> Java ORM 기술에 대한 표준 명세 ㅡ> Java에서 제공하는 API(Not Spring!!!)
> 즉, ORM을 사용하기 위해 Java에서 제공하는 API방식 인터페이스라는 점!

## ORM? JDBC?

ORM은 DB테이블을 객체로 매핑하는 방식 -> SQL을 자동으로 생성함.

JDBC는 SQL문으로 직접 DB를 조작하는 방식 -> SQL을 명시 해 주어야 함.

## JPA의 구조는?

Spring ㅡ> Hibernate ㅡ> JPA 이다.

단계적으로 보자면,

primarykey -> JPA -> sql -> JDBC API -> DB -> Mapping 순서라 생각하면 될것이다.

## Why JPA?

복잡한 sql문을 일일이 만들지 않고 hibernate framework를 사용하여 간단한 메소드로 CRUD구현이 가능하다.

`JPA가 SQL을 처리해주기 때문에 유지보수성도 향사되며 객체를 통한 쿼리를 사용하기 때문에 객체 지향적인 개발이 가능하다.`




