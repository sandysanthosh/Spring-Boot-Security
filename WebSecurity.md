### Application.properties:

```

server.port=8080
security.basic.enabled=true
spring.security.user.name=admin
spring.security.user.password=admin


```



### SecurityApplication:


```

package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.reactive.EnableWebFluxSecurity;

@EnableWebSecurity
@Configuration
@SpringBootApplication
public class SecurityApplication {

	public static void main(String[] args) {
		SpringApplication.run(SecurityApplication.class, args);
	}

}


```



### RestController:

```

package com.example.Controller;

import org.springframework.web.bind.annotation.RequestMapping;

@org.springframework.web.bind.annotation.RestController
public class RestController {
	
	@RequestMapping("/hello")
	public void hello() {
		System.out.println("First Check");
	}

}
```
