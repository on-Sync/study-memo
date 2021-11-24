### 2. @Configuration

#### 2.1. 서블릿 웹보안설정은 Adapter 를 사용한다.

```java
package com.example.jwt.security;

import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@EnableWebSecurity(debug = true)
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
    
}
```

- 서블릿 보안설정은 `WebSecurityConfigurer` 인터페이스로 적용한다.
- 이 인터페이스를 구현은 보통 `WebSecurityConfigurerAdapter` 라는 Adapter 명칭의 추상화된 `base class`를 상속으로 응용한다.
- 이 기본클래스는 추상클래스지만 인터페이스의 기능은 구현되어 있다.
- 즉, 추상메소드와 추상멤버변수는 없기에 사용자는 필요한 설정만 조정하여 사용할 수 있다.

#### 2.2. 요청별 필터목록

![기본필터목록](기본필터목록.png)

- `@EnableWebSecurity(debug = true)` 에서 디버깅 설정을 해두면 Request 에 따른 Filter Chain 을 확인할 수 있다. ( `@EnableWebSecurity` 는 `@Configuration` 기능을 내포 )
- 순차적으로 필터의 적용순서된다.
- 목록내용을 확인하면 해당 Request 에서 적용된 인증, 세션, Csrf 등의 필터클래스를 점검할 수 있다.
- 이 필터들은 기본적으로 `GenericFilterBean` 추상클래스를 상속받는다.
- 이 필터들은 필요에 따라 위 추상클래스를 상속 받은 `OncePerRequestFilter` , `AbstractAuthenticationProcessingFilter` 등의 추상클래스를 사용하여 요청내 중복필터링을 방지, 인증처리를 규격화한 필터로 구현되어 있다.

#### 2.3. Request 별로 요구되는 권한 설정

```java
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests()
                .antMatchers("/", "/css/**", "/images/**","/js/**", "/h2-console/**", "/login**", "/error**").permitAll()
                .antMatchers(HttpMethod.POST, "/users").permitAll()
                .antMatchers(HttpMethod.GET, "/users").hasRole("USER")
                .anyRequest().authenticated();
    }
```

- `authorizeRequests()` 은 `AbstractRequestMatcherRegistry` 를 상속받은 `ExpressionInterceptUrlRegistry` 를 반환한다.
- 해당 Registry 는 `RequestMatcher` 로 지정된 요청 묶음별로 `List<UrlMapping>` 형태로 권한묶음과 함께 관리합니다.
- 지정가능한 권한내용은 `AuthorizedUrl` 에 분류되어 제공됩니다.
- 즉 요청방식별로 허용되는 인증권한이 요구됩니다.
