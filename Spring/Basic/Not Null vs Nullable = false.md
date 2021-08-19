# @NotNull vs @Column(nullable = false)


```
@Column(nullable = false)
private String title;
```

```
@NotNull
private String title;
```

## 

> @NotNull은 DB에 쿼리를 보내기 전에 Bean 유효성 검사를 한다. 

-> 쿼리 전송 전 검사 후 null값일 경우 쿼리 자체가 전송되지 않음

> @Column(nullable = false)은 DB에서 유효성 검사를 다룬다.

-> 쿼리가 전송이 되기때문에 DB에 null값이 들어감.


스프링에서는 @NotNull 사용을 지향하고 있다.




## 참고 
https://bottom-to-top.tistory.com/14
