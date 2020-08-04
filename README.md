# 스프링 시큐리티 OAuth2.0 V2

- 페이스북, 구글 로그인 및 기본 시큐리티 연동

### 스프링 시큐리티 기본 V1 참고

- https://github.com/codingspecialist/Sringboot-Security-Basic-V1

### JPA method names 참고

![blog](https://postfiles.pstatic.net/MjAyMDA4MDRfMTU1/MDAxNTk2NTA2ODAyMTgx.Qoff6FQ1RJyGw83meuDXT5J5e-Ac1WwSJMH2wf1l1Swg.KinVePXqdUOeyDYYRp4aguwTsxF0OBQB64LNUYTJRRgg.PNG.getinthere/Screenshot_26.png?type=w773)

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
            client-id: 머시기머시기
            client-secret: 머시기머시기
            scope:
              - email
              - profile
```
