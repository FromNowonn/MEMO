## Nginx

여기서 Nginx를 설치하는 이유는 `reverse-proxy`를 통해 `리다이렉트`를 하기 위함. 

즉, 포트번호를 자동으로 잡아주기 위함이다.

reverse-proxy란 외부의 요청을 받아 뒷단 서버로 요청을 전달하는 행위를 말하는데

이런 리버스 프록시 서버(Nginx)는 요청을 전달하고, 실제 요청에 대한 처리는 뒷단의 웹 서버들이 처리.

### Nginx 설치
EC2에 Nginx를 설치.
```
sudo yum install nginx
```
Nginx 실행.
```
sudo service nginx start
```

nginx 설정파일을 열어 현재 실행중인 프로젝트에 `reverse-proxy` 설정

```
sudo vi /etc/nginx/nginx.conf
```

`server` 내의 `location /` 부분에 아래 내용을 추가.

    server {
        listen       80;
        listen       [::]:80;
        server_name  내 도메인

        location /{
                proxy_pass http://localhost:8080;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $http_host;
        }


nginx 재시작 후 접속하면 포트번호 없이 접속 가능

## 출처
https://jojoldu.tistory.com/267?category=635883
