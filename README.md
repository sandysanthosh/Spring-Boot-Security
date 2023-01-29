# spring-basic-security

Spring Security : Basic Authentication and Authorization  using spring boot


In a Spring Boot application, you can double check that a user is authenticated by using Spring Security. One way to do this is to create a custom filter that checks if the user is authenticated and has the necessary roles or permissions to access a certain resource. You can then configure your application to use this filter for specific URLs or request types. Additionally, you can use the **SecurityContextHolder** to check if the current user is authenticated and has the necessary roles or authorities. You can also use the **@PreAuthorize** and **@PostAuthorize** annotations to check the authentication and authorization of a user before or after a method is called.


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
    
    
   #### custom filter that checks if a user is authenticated and has the necessary role to access a certain resourc:
   
   
   ```
   
   import java.io.IOException;
import javax.servlet.FilterChain;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.http.HttpServletRequest;
import org.springframework.security.core.Authentication;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.web.filter.GenericFilterBean;

public class AuthenticationFilter extends GenericFilterBean {

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain filterChain)
            throws IOException, ServletException {
        Authentication authentication = TokenAuthenticationService
                .getAuthentication((HttpServletRequest) request);
        SecurityContextHolder.getContext().setAuthentication(authentication);
        filterChain.doFilter(request, response);
    }
}



```


This filter uses the **TokenAuthenticationService** to extract the authentication information from the request and sets it in the **SecurityContextHolder**. You can then configure your application to use this filter for specific URLs or request types.


Here is an example of using the **@PreAuthorize** and **@PostAuthorize** annotations to check the authentication and authorization of a user before or after a method is called:

```
@PreAuthorize("hasRole('ROLE_ADMIN')")
@PostAuthorize("hasRole('ROLE_USER')")
public void getResource() {
    //resource logic
}

```

This code checks if the user has the role of ROLE_ADMIN before the method is executed and if the user has the role of ROLE_USER after the method is executed.

In addition to this you can also use following code to check authentication

```
@RequestMapping("/user")
public Principal user(Principal user) {
    return user;
}

```

This code returns the user details of the currently logged in user

Please note, this is only an example and you may need to adjust it to fit the specific needs of your application.


