# 🍪 Spring에서 쿠키 사용해보기

## 사용자의 방문 횟수를 브라우저에 쿠키로 저장하고 보여주기
- @CookieValue Annotation 활용
``` JAVA
@CookieValue(value = "visitCount", defaultValue = "0", required = true) String cookieValue

```
<br>

- 쿠키 생성
``` JAVA
Cookie visitCountCookie = new Cookie("visitCount", cookieValue);
```
<br>

- 쿠키 유효기간 설정
``` JAVA
visitCountCookie.setMaxAge(2 * 60 * 60 * 24 * 365);   //  2years
//                         2                              2seconds
//                         2 * 60                         2minutes
//                         2 * 60 * 60                    2hours
//                         2 * 60 * 60 * 24               2days
//                        -1                              until browser is open
```
<br>

- 현재 경로 이하에 모두 쿠키 적용
``` JAVA
visitCountCookie.setPath("/");
```
<br>

- 클라이언트에게 보낼 응답에 쿠키 포함
``` JAVA
response.addCookie(visitCountCookie);
```
<br>


