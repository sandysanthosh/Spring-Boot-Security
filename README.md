# spring-basic-security

Spring Security : Basic Authentication and Authorization  using spring boot


In a Spring Boot application, you can double check that a user is authenticated by using Spring Security. One way to do this is to create a custom filter that checks if the user is authenticated and has the necessary roles or permissions to access a certain resource. You can then configure your application to use this filter for specific URLs or request types. Additionally, you can use the SecurityContextHolder to check if the current user is authenticated and has the necessary roles or authorities. You can also use the @PreAuthorize and @PostAuthorize annotations to check the authentication and authorization of a user before or after a method is called.


Dependency:

```
DevTools
Secutiry 
Web
```

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
