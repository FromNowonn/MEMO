### 동료와 진행하는 스터디 도중 예외처리가 되지 않은 이유없는 403 오류가 발생했다고 연락이왔다.

### 문제를 찾기위하여 검색을 하던 도중 관련 자료를 찾아 해결하게 되었다.

### 문제는 이러하다. 

## 정상적인 토큰에서 정보를 잘 추출 했고, 인증정보(authorities)를 보면 USER라는 권한이 잘 들어가 있었다.
## 문제가 없는데 JwtFilter부분에서 걸러지는 현상이 발생했다.

![image](https://user-images.githubusercontent.com/51487025/154837194-40335ec2-f04a-45a1-8a92-7039fcc3c087.png)

## Spring Security에선 prefix인 `ROLE_` 이 있어야 작동을 한다는 것이었다.


## 이를 해결하기 위하여 Role부분을 다음과 같이 수정하였다.

![image](https://user-images.githubusercontent.com/51487025/154837274-2a1eb629-6cef-4520-84bf-16b9211ff276.png)

## 이후 토큰 생성 부분에서 다음과 같이 토큰 정보에 key값을 넣어 주었더니 모든 문제가 해결이 되었다.

![image](https://user-images.githubusercontent.com/51487025/154837286-45298ce7-5a8e-41de-aef2-777decaa12f3.png)









## 참고 
<https://ruzun88.github.io/spring/security/403-forbidden.html#filter-들여다-보기>
