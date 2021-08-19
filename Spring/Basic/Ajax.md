# 스프링 AJAX 통신


## ajax란?

asynchronous Javascript and XML의 줄임말로 자바스크립트를 이용하여 비동기 식으로 서버와 통신 기법. 

비동기통신이기 때문에 서버에 요청이 가더라도 반응형 애플리케이션 같은 효과를 줄 수 있다.

>ajax 통신을 하기 위해서는 jQuery 라이브러리를 이용해야한다.

```mustache
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
```

## 기본 예제
- 클라이언트 (javascript)
```javascript
    var data = {
         title : $('#title').val(),
         author: $('#author').val(),
         contents: $('#content').val()
        };

        $.ajax({
            type: 'POST',
            url: '/api/v1/board',
            dataType: 'json',
            contentType:'application/json; charset=utf-8',
            data: JSON.stringify(data)
        }).done(function (){
            alert('작성 완료');
            window.location.href='/';
        }).fail(function (error){
            alert(JSON.stringify(error));
        });

```
- 서버 (Spring)
```java
@PostMapping("/api/board")
    public Long save(@RequestBody RegistrationDto registrationDto){
        return boardService.save(registrationDto);
    }

} 
```
- 뷰 (mustache)

```mustache
<body>
   <button type="button" class="btn btn-primary" id="btn-registration">등록</button>
</body>
```
## 참고

스프링 부트와 AWS로 혼자 구현하는 웹 서비스 - 이동욱

https://jojoldu.tistory.com/463
