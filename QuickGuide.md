### Spring-Boot-Security

pom.xml:
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

auth.inMemoryAuthentication().withUser("Java Techie").password("Password").roles("ADMIN");
auth.inMemoryAuthentication().withUser("Basant").password("Password2").roles("USER");

}

//Security for all API

@Override
	protected void configure(HttpSecurity http) throws Exception {
		http.csrf().disable();
		http.authorizeRequests().antMatchers("/rest/**").hasAnyRole("ADMIN").anyRequest().fullyAuthenticated().and()
				.httpBasic();
	}
@Bean
	public static NoOpPasswordEncoder passwordEncoder() {
		return (NoOpPasswordEncoder) NoOpPasswordEncoder.getInstance();
	}
}
 ```



### security.java:


```
@Configuration @EnableWebSecurity @EnableGlobalMethodSecurity(prePostEnabled=true)
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
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
	
	
} }

```


