## JWT 인증 구현하기

### 1. Spring Security 프로젝트

#### 1.1. dependencies

##### 필수 !

```gradle
implementation 'org.springframework.boot:spring-boot-starter-security'
```

##### 선택 ?
```gradle
implementation 'org.springframework.boot:spring-boot-starter-web'
//implementation 'org.springframework.boot:spring-boot-starter-webflux:2.6.0'
```

- spring security 는 `Filter Chain` 구조를 기반으로 보안을 제공한다.
- 필터는 WAS 형식에 따라 적용방법이 다르다.
- `servlet` 의 경우 `HttpSevletRequest` , `HttpSevletResponse` 를 사용한다.
- `webflux` 의 경우 `ServerRequest` , `ServerResponse` 를 사용한다.
- 이는 WAS 형식에 따른 동작방식의 차이에서 비롯되기에 사용할 WAS 에 따라서 의존성을 선택한다.
- 여기서는 `servlet` WAS 를 사용한 내용을 설명한다.

#### 1.2. Filter Chain

- TomcatWebServer
WebApplicationContext
UserDetailsServiceAutoConfiguration
DefaultSecurityFilterChain
- TomcatWebServer (start)


### 2. @Configuration

```java
package com.example.jwt.security;

import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@EnableWebSecurity(debug = true)
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
    
}
```
