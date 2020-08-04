# 스프링 시큐리티 OAuth2.0 V2

- 페이스북, 구글 로그인 및 기본 시큐리티 연동

### 스프링 시큐리티 기본 V1 참고

- https://github.com/codingspecialist/Sringboot-Security-Basic-V1

### JPA method names 참고

![blog](https://postfiles.pstatic.net/MjAyMDA4MDRfMTU1/MDAxNTk2NTA2ODAyMTgx.Qoff6FQ1RJyGw83meuDXT5J5e-Ac1WwSJMH2wf1l1Swg.KinVePXqdUOeyDYYRp4aguwTsxF0OBQB64LNUYTJRRgg.PNG.getinthere/Screenshot_26.png?type=w773)

### Naver, Google, Facebook 로그인 완료

![blog](https://postfiles.pstatic.net/MjAyMDA4MDRfMTgz/MDAxNTk2NTEzODQ3MDMz.2nBpI6CG63EZsfjYCjX08aUH6PM55JUZZltDl2bpRpwg.R9l4QGg7GzoH1xTqeRTBlehF-9lfiR1_bqZt8-5Xc2kg.PNG.getinthere/Screenshot_27.png?type=w773)

### application.yml 설정

```yml
server:
  port: 8080
  servlet:
    context-path: /
    encoding:
      charset: UTF-8
      enabled: true
      force: true

spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/security?serverTimezone=Asia/Seoul
    username: cos
    password: cos1234

  mvc:
    view:
      prefix: /templates/
      suffix: .mustache

  jpa:
    hibernate:
      ddl-auto: update #create update none
      naming:
        physical-strategy: org.hibernate.boot.model.naming.PhysicalNamingStrategyStandardImpl
    show-sql: true

  security:
    oauth2:
      client:
        registration:
          google: # /oauth2/authorization/google 이 주소를 동작하게 한다.
            client-id: 머시기
            client-secret: 머시기
            scope:
              - email
              - profile

          facebook:
            client-id: 머시기
            client-secret: 머시기
            scope:
              - email
              - public_profile

          # 네이버는 OAuth2.0 공식 지원대상이 아니라서 provider 설정이 필요하다.
          # 요청주소도 다르고, 응답 데이터도 다르기 때문이다.
          naver:
            client-id: 머시기
            client-secret: 머시기
            scope:
              - name
              - email
              - profile_image
            client-name: Naver # 클라이언트 네임은 구글 페이스북도 대문자로 시작하더라.
            authorization-grant-type: authorization_code
            redirect-uri: http://localhost:8080/login/oauth2/code/naver

        provider:
          naver:
            authorization-uri: https://nid.naver.com/oauth2.0/authorize
            token-uri: https://nid.naver.com/oauth2.0/token
            user-info-uri: https://openapi.naver.com/v1/nid/me
            user-name-attribute: response # 회원정보를 json의 response 키값으로 리턴해줌.
```
