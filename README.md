#### pom.xml:


https://docs.spring.io/spring-security/site/docs/5.0.x/reference/html/csrf.html

```

<dependencies>
        <dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-config</artifactId>
    <version>5.5.0</version>
  </dependency>
        <dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-web</artifactId>
    <version>5.5.0</version>
  </dependency>
</dependencies>

```

### WebSecurity.java:

```
@SuppressWarnings("deprecation")
@configuration
public class springsecurity extends WebSecurityConfigureAdapter{

@Override
protected void configure(AuthenticationManagerBuilder auth) throws exception {

auth.inMemoryAuthentication().withUsers("Java Techie").password("password").roles("ADMIN");
}

//Security for all API

@Override
protected void configure(HttpSecurity http) throws Exception {
		http.csrf().disable();
            http.authorizeRequests().anyRequest().fullyAuthenticated().and().httpBasic();

}

Public static NoOpPasswordEncoder passwordEncoder(){
return (NoOpPasswodEncoder) NoOpPassordEncoder.getInstance();
}
}
    
    
    ```



### security.java:

```

@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled=true)

public class WebSecurityConfig extends
		WebSecurityConfigurerAdapter {

	@Override
	protected void configure(HttpSecurity http) throws Exception {
		http
		    .csrf().csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse());
                     .logout().logoutRequestMatcher(new AntPathRequestMatcher("/logout"));
		    
		    
		http.crsf().
		.disable()
		.exceptionHandling()
		.authennticationEntryPoint(404); // check online
		.and()
		.authorizeRequests()
		.antMatchers("/")
		.permitAll()
		.and()
		.addFilterBefore(buildAdminJwtTokenAuthenticationProcessingFilter(),
		UsernamePassowrdAuthenticationFilter.class);
		
		https.headers().cacheControl();
		}
		
		
	}
}


```
