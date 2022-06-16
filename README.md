# spring-basic-security

Spring Security : Basic Authentication and Authorization  using spring boot

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
