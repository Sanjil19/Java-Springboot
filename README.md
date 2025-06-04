## Java-Springboot

### First Lesson

#### Example Code

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

@SpringBootApplication
public class Demo1Application {

    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(Demo1Application.class, args);
        Dev obj = context.getBean(Dev.class);
        obj.build();
    }
}
```

```java
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class Dev {
    public void build() {
        System.out.println("Working on a project");
    }
}
```

### Tips to Understand the Program

- **@SpringBootApplication**: This annotation marks the main class of a Spring Boot application. It combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.
- **ApplicationContext**: This is the Spring container. It manages the lifecycle and configuration of application beans.
- **@Component**: Tells Spring to create an instance (bean) of the `Dev` class and manage it.
- **context.getBean(Dev.class)**: Retrieves the `Dev` bean from the Spring container.
- **Why use beans?**: Beans allow Spring to manage dependencies and lifecycle, making your code more modular and testable.
- **Spring Boot auto-configuration**: Spring Boot tries to automatically configure your application based on the dependencies you have added.
- **Project Structure**: Keeping your classes in the same package or sub-packages of the main class ensures they are detected by component scanning.
- **Console Output**: When you run the application, you should see `Working on a project` printed in the console, showing that the `Dev` bean's `build()` method was called.

> When we use `@Component`, we are telling Spring to create and manage an object (bean) of the `Dev` class.
