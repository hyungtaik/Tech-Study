# Spring Security

### 📎 보안 용어

> **접근 주체(Principal)** : 보호된 리소스에 접근하는 대상
>
> **인증(Authentication)** : 보호된 리소스에 접근한 대상에 대해 이 유저가 누구인지, 애플리케이션의 작업을 수행해도 되는 주체인지 확인하는 과정 (ex. Login한 사용자들에게만 기능 사용 등)
>
> > **[종류]**
> >
> > **1) 자격(Credential) 기반 인증**
> >
> > - 권한을 부여받는데 한 차례의 인증과정이 필요하며 대부분 아이디와 비밀번호를 입력받아 입력한 비밀번호가 저장된 비밀번호와 일치하는것을 확인한다. 
> > - 일반적으로 스프링 시큐리티에서는 **아이디를 principle, 비밀번호를 credential**. 
> >
> > **2) 이중 인증(Two-factor Authentication**
> >
> > - 한번에 2가지 방식으로 인증을 받는 것을 말한다.
> >   - 금융, 은행 웹 애플리케이션을 이용해 거래를 할 경우, 로그인과 보안 인증서를 통한 2가지 방법으로 인증을 받는다.
> >
> > **3) 물리적인 인증**
> >
> > - 지문을 인식받거나 키를 삽입하여 인증하는 것을 말한다.
>
> **권한 부여(Authorization) **
>
> > - 인가(Authorize) : 해당 리소스에 대해 접근 가능한 권한을 가지고 있는지 확인하는 과정(After Authentication, 인증 이후)
> > - 권한 : 어떠한 리소스에 대한 접근 제한, 모든 리소스는 접근 제어 권한이 걸려있다. 즉, 인가 과정에서 해당 리소스에 대한 제한된 최소한의 권한을 가졌는지 확인한다.
>
> > **[종류] **
> >
> > **1) 부여된 권한(Granted Autority)**
> >
> > - **적절한 절차로 사용자가 인증되었다면 권한을 부여**해야 한다.
> >   - 회원가입 등으로 반영구적인 권한이 부여되었다면 이 사용자의 권한을 어딘가에 저장해야 하고, 해당 사용자가 로그인 했을 때 메인 페이지로 넘어갈 수 없다면 권한 부여에 문제가 있다는 것이다.
> >
> > **2) 리소스의 권한(Intercept) **
> >
> > - 사용자의 권한만 있다고 보안이 제대로 동작하지 않는다. 보안이란 권한이 없는 자들이 원천적으로 리소스에 접근할 수 없도록 막아내는 것이기 때문이다. 그런 의미에서 **적절한 권한을 가진 사용자에게만 해당 자원에 접근할 수 있도록 자원의 외부 요청을 원천적으로 가로채는 것(Intercept)이 웹 보안**, 그 중 권한 부여의 핵심 원칙이라 할 수 있다.

****



### 1. Spring Security 란?

> - 스프링 기반의 애플리케이션 보안(인증과 권한, 인가 등)을 담당하는 스프링 하위 프레임워크이다.
> - 주로 서블릿 필터와 이들로 구성된 필터체인으로의 위임모델을 사용한다.
> - 보안과 관련해서 체계적으로 많은 옵션을 제공해주기 때문에 개발자 입장에서는 일일이 보안 관련 로직을 작성하지 않아도 된다.
> - 인증과 권한 제어에 필요한 필터의 모음이다. 필터를 기반으로 권한에 따른 접근 제어 기능, 패스워드 암호화 등 전반적인 기능을 사용하고 있어서 실무에서 많이 사용한다.
>
> #### 1) 인증관련 구조
>
> ![image-20200719182240931](C:\Users\multicampus\AppData\Roaming\Typora\typora-user-images\image-20200719182240931.png)
>
> > **[Form 기반 로그인에 대한 Flow]**
> >
> > 1. 사용자가 Form을 통해 로그인 정보를 입력하고 인증 요청을 보낸다.
> > 2. AuthenticationFilter가 HttpServletRequest에서 사용자가 보낸 아이디와 비밀번호를 인터셉트한다. Front 단에서 유효성 검사를 할 수도 있지만, 안전을 위해서 다시 한번 사용자가 보낸 아이디와 비밀번호의 유효성 검사를 해줄 수 있다. (아이디나 비밀번호가 Null일 경우) HttpServletRequest에서 꺼내온 사용자의 아이디와 비밀번호를 실질적인 인증을 담당할 AuthenticationManager 인터페이스에게 인증용 객체(UsernamePaawordAuthentication Token)로 만들어줘서 위임한다.
> > 3. AuthenticationFilter에게 인증용 객체(Token)을 전달받는다.
> > 4. 실제 인증할 AuthenticationProvider에게 Authentication객체(Token)을 다시 전달한다.
> > 5. DB에서 사용자 인증 정보를 가져올 UserDetailsService 객체에게 사용자의 아이디를 넘겨주고 DB에서 인증에 사용할 사용자 정보를 DuserDetails라는 객체로 전달받는다.
> > 6. AuthenticationProvider는 UserDetails 객체를 전달받은 이후 실제 사용자의 입력정보와 UserDetails 객체를 가지고 인증을 시도한다.
> > 7. 8. 9. 10. 인증이 완료되면 사용자 정보를 가진 Authentication 객체를 SecurityContextHolder에 담은 이후 AuthenticationSuccessHandle를 실행한다.  실패 시 AuthenticationFailuerHandler를 실행한다.
>
> #### 2) Security의 Filter
>
> ![image-20200719183646426](C:\Users\multicampus\AppData\Roaming\Typora\typora-user-images\image-20200719183646426.png)
>
> > - SecurityContextPersistenceFilter : SecurityContextRepository에서 SecurityContext를 가져오거나 저장하는 역할을 한다.
> >
> > - LogoutFilter : 설정된 로그아웃 URL로 오는 요청을 감시하며, 해당 유저를 로그아웃 처리
> > - (UsernamePassword)AuthenticationFilter : (아이디와 비밀번호를 사용하는 form 기반 인증) 설정된 로그인 URL로 오는 요청을 감시하며, 유저 인증 처리
> >   - AuthenticationManager를 통한 인증 실행
> >   - 인증 성공 시, 얻은 Authentication 객체를 SecurityContext에 저장 후 AuthenticationSuccessHandler 실행
> >   - 인증 실패 시, AuthenticationFailureHandler 실행
> >
> > - DefaultLoginPageGeneratingFilter : 인증을 위한 로그인폼 URL을 감시한다.
> > - BasicAuthenticationFilter : HTTP 기본 인증 헤더를 감시하여 처리한다.
> > - RequestCacheAwareFilter : 로그인 성공 후, 원래 요청 정보를 재구성하기 위해 사용된다.
> > - SecurityContextHolderAwareRequestFilter : HttpServletRequestWrapper를 상속한 SecurityContextHolderAwareRequestWapper 클래스로 HttpServletRequest 정보를 감싼다. SecurityContextHolderAwareRequestWrapper 클래스는 필터 체인상의 다음 필터들에게 부가정보를 제공한다.
> > - AnonymousAuthenticationFilter : 이 필터가 호출되는 시점까지 사용자 정보가 인증되지 않았다면 인증토큰에 사용자가 익명 사용자로 나타난다.
> > - SessionManagementFilter : 이 필터는 인증된 사용자와 관련된 모든 세션을 추적한다.
> > - ExceptionTranslationFilter : 이 필터는 보호된 요청을 처리하는 중에 발생할 수 있는 예외를 위임하거나 전달하는 역할을 한다.
> > - FilterSecurityInterceptor : 이 필터는 AccessDecisionManager 로 권한부여 처리를 위임함으로써 접근 제어 결정을 쉽게해준다.
>
> #### 3) Authentication
>
> - 접근 주체는 Authtentication 객체를 생성한다. 
> - 이 객체는 SecurityContext(내부 메모리)에 보관되고 사용되어진다.
>
> ```java
> public interface Authentication extends Principal, Serializable { 
>     Collection<? extends GrantedAuthority> getAuthorities(); // Authentication 저장소에 의해 인증된 사용자의 권한 목록 
>     Object getCredentials(); // 주로 비밀번호 
>     Object getDetails(); // 사용자 상세정보 
>     Object getPrincipal(); // 주로 ID 
>     boolean isAuthenticated(); //인증 여부 
>     void setAuthenticated(boolean isAuthenticated) throws IllegalArgumentException; 
> }
> ```
>
> #### 4) Authentication Manager
>
> > - 사용자의 요청을 AuthenticationFilter에서 Authentication 객체로 변환해 AuthenticationManager(Provider Manager)에게 넘겨주고, AuthenticationProvider가 실제 인증을 한 이후에 인증이 완료되면 Authentication 객체를 반환해준다.
> >   - AbstractAuthenticationProcessingFilter: 웬 기반 인증요청에서 사용되는 컴포넌트로 Post 폼 데이터를 포함하는 요청을 처리한다. 사용자의 비밀번호를 다른 필터로 전달하기 위해서 **Authentication 객체를 생성하고 일부 프로퍼리를 설정**한다.
> >   - AuthenticationManager: 인증 요청을 받고 Authentication을 채워준다.
> >   - AuthenticationProvider: 실제 인증이 일어나고 만약 인증 성공 시 Authentication 객체의 authenticated = true로 설정해준다.
> > - Spring Security는 ProvideManager라는 AuthenticationManager 인터페이스의 유일한 구현체를 제공한다.
> > - ProvideManager는 하나 또는 여러 개의 AuthenticationProvider 구현체를 사용할 수있다.
>
> #### 5) 비밀번호 인증과정
>
> > - DaoAuthenticationProvider 는 UserDetailsService 타입 오브젝트로 위임한다. UserDetailsService 는 UserDetails 구현체를 리턴하는 역할을 한다. UserDetails 인터페이스는 이전에 설명한 Authentication 인터페이스와 상당히 유사하지만 서로 다른 목적을 가진 인터페이스이므로 헷갈리면 안된다. 
> >   - Authentication : 사용자 ID, 패스워드와 인증 요청 컨텍스트에 대한 정보를 가지고 있다. 인증 이후의 사용자 상세정보와 같은 UserDetails 타입 오브젝트를 포함할 수도 있다. 
> >   - UserDetails : 이름, 이메일, 전화번호와 같은 사용자 프로필 정보를 저장하기 위한 용도로 사용한다.
>
> #### 6) 인증 예외
>
> > 인증과 관련된 모든 예외는 AuthenticationException을 상속한다. AuthenticationException은 개발자에게 상세한 디버깅 정보를 제공하기 위한 두개의 멤버 필드를 가지고 있다. 
> >
> > - authentication : 인증 요청관련 Authentication 객체를 저장하고 있다.
> > - extraInformation : 인증 예외 관련 부가 정보를 저장한다. 예를 들어 UsernameNotFoundException 예외는 인증에 실패한 유저의 id 정보를 저장하고 있다.
> >
> > ##### * 많이 발생하는 예외들
> >
> > - BadCredentialsException : 사용자 아이디가 전달되지 않았거나 인증 저장소의 사용자 id 에 해당하는 패스워드가 일치하지 않을 경우 발생한다.
> > - LockedException : 사용자 계정이 잠긴경우 발생한다.
> > - UsernameNotFoundException : 인증 저장소에서 사용자 ID를 찾을 수 없거나 사용자 ID에 부여된 권한이 없을 경우 발생한다.

<hr>



### 2. 접근 권한 부여

> - 자동으로 설정된 Spring Security  필터 체인의 마지막 서블릿 필터는 FilterSecurityInterceptor이다. 이 필터는 해당 요청의 수락 여부를 결정한다. FilterSecurityInterceptor가 실행되는 시점에는 이미 사용자가 인증되어 있을 것이므로 유효한 사용자인지도 알 수 있다.
> - Authentication 인터페이스에 List<GrantedAuthority> getAuthorities() 라는 메소드는 사용자 아이디에 대한 권한 목록을 리턴한다. 권한 처리 시에 이 메소드가 제공하는 권한 정보를 참조해서 해당 요청의 승인 여부를 결정하게 된다.
> - Access Decision Manager 라는 컴포넌트가 인증 확인을 처리한다. AccessDecisionManager 인터페이스는 인증 확인을 위해 두가지 메소드를 제공한다.
>   - supports : AccessDecisionManager 구현체는 현재 요청을 지원하는지의 여부를 판단하는 두개의 메소드를 제공한다. 하나는 java.lang.Class 타입을 파라미터로 받고 다른 하나는 ConfigAttribute 타입을 파라미터로 받는다.
>   - decide : 이 메소드는 요청 컨텍스트와 보안 설정을 참조하여 접근 승인여부를 결정한다. 이 메소드에는 리턴값이 없지만 접근 거부를 의미하는 예외를 던져 요청이 거부되었음을 알려준다.

> - 인증과정에서 발생할 수 있는 예상 가능한 에러를 처리하는 AuthenticationException 과 하위 클래스를 사용했던 것처럼 특정 타입의 예외 클래스들을 사용하면 권한처리를 하는 애플리케이션의 동작을 좀 더 세밀하게 제어할 수 있다. 
> - AccessDecisionManager 는 표준 스프링 빈 바인딩과 레퍼런스로 완벽히 설정할 수 있다.디폴트 AccessDecisionManager 구현체는 AccessDecisionVoter 와 Vote 취합기반 접근 승인 방식을 제공한다.
> - Voter 는 권한처리 과정에서 다음 중 하나 또는 전체를 평가한다.
>   - 보호된 리소스에 대한 요청 컨텍스트 (URL 을 접근하는 IP 주소)
>   - 사용자가 입력한 비밀번호
>   - 접근하려는 리소스
>   - 시스템에 설정된 파라미터와 리소스

> - AccessDecisionManager 는 요청된 리소스에 대한 access attribute 설정을 voter에게 전달하는 역할도 하므로 voter는 웹 URL 관련 access attribute 설정 정보를 가지게 된다. 
> - Voter는 사용할 수 있는 정보를 사용해서 사용자의 리소스에 대한 접근 허가 여부를 판단한다. 보터는 접근 허가 여부에 대해서 세 가지 중 한 가지로 결정하는데, 각 결정은 AccessDecisionVoter 인터페이스에 다음과 같이 상수로 정의되어 있다.
>   - **Grant(ACCESS_GRANTED)** : Voter 가 리소스에 대한 접근 권한을 허가하도록 권장한다.
>   - **Deny(ACCESS_DENIED)** : Voter 가 리소스에 대한 접근 권한을 거부하도록 권장한다.
>   - **Abstain(ACCESS_ABSTAIN)** : Voter 는 리소스에 대한 접근권한 결정을 보류한다. 이 결정 보류는 다음과 같은 경우에 발생할 수 있다.
>     - voter 가 접근권한 판단에 필요한 결정적인 정보를 가지고 있지 않은 경우
>     - Voter 가 해당 타입의 요청에 대해 결정을 내릴 수 없는 경우

<hr>



### 3. Access

> - hasRole(Role) : 해당 Role 을 갖고있는 사용자 허용
> - hasAnyRole(Role1, Role2, ...) : 해당 Role 중에 1개이상 갖고있는 사용자 허용
> - anonymous : 익명 사용자 허용
> - authenticated : 인증된 사용자 허용
> - permitAll : 모든 사용자 허용
> - denyAll : 모든 사용자 차단

<hr>



### 4. Spring Security 관련 Annotation

> - @Secured : 각 요청경로에 따른 권한 설정은 위의 xml에서도 할 수 있지만, 메소드레벨에서 @Secured 를 통해서도 할 수 있다.  EnableGlobalMethodSecurity(securedEnabled=true) 를 추가하면 된다.
>   - @Secured("ROLE_ADMIN") , @Secured({"ROLE_ADMIN","ROLE_USER"})
>   - 비인가자 접근 시 AccessDeniedException 던짐
> - @PreAuthorize : 위와 비슷하지만 spEL 을 사용할 수 있다. @EnableGlobalMethodSecurity(prePostEnabled=true)를 설정한다.
>   - @PreAuthorize("hasRole('ADMIN')")
> - @PostAuthorize : 위와 동일
> - @AuthenticationPrincipal : 컨트롤러단에서 세션의 정보들에 접근하고 싶을 때 파라미터에 선언해준다.
>   - \- public ModelAndView userInfo(@AuthenticationPrincipal User user)
>   - \- 이거 안쓰고 확인하려면 (User) SecurityContextHolder.getContext().getAuthentication().getPrincipal(); 이런식으로 써야한다.
>   - \- 4.x 부터는 org.springframework.security.core.annotation.AuthenticationPrincipal 을 import 해야한다.
>   - \- mvc:annotation-driven.mvc:argument-resolvers 에 bean 으로 org.springframework.security.web.method.annotation.AuthenticationPrincipalArgumentResolver 를 등록한다.

<hr>

[참고 URL]

- https://coding-start.tistory.com/153 [코딩스타트]

- [http://springmvc.egloos.com/category/Spring%20Security](http://springmvc.egloos.com/category/Spring Security)
- https://www.holaxprogramming.com/2017/10/09/java-jvm-performance/