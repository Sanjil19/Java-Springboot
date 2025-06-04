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

---

### Tips to Understand the Program

- **@SpringBootApplication**  
  Marks the main class of a Spring Boot application. Combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.

- **ApplicationContext**  
  The Spring container. Manages the lifecycle and configuration of application beans.

- **@Component**  
  Tells Spring to create and manage an instance (bean) of the `Dev` class.

- **context.getBean(Dev.class)**  
  Retrieves the `Dev` bean from the Spring container.

- **Why use beans?**  
  Beans allow Spring to manage dependencies and lifecycle, making your code more modular and testable.

- **Spring Boot auto-configuration**  
  Spring Boot tries to automatically configure your application based on the dependencies you have added.

- **Project Structure**  
  Keep your classes in the same package or sub-packages of the main class to ensure they are detected by component scanning.

- **Console Output**  
  When you run the application, you should see `Working on a project` printed in the console, showing that the `Dev` bean's `build()` method was called.

> **Note:**  
> When we use `@Component`, we are telling Spring to create and manage an object (bean) of the `Dev` class.

---

### What’s Happening?

- **@SpringBootApplication:**  
  Marks the entry point and enables component scanning and auto-configuration.

- **ApplicationContext context = SpringApplication.run(...):**  
  Starts Spring Boot, creates the app context (IoC container) which holds beans.

- **@Component on Dev:**  
  Registers `Dev` as a bean (a managed object) within Spring’s container.

- **context.getBean(Dev.class):**  
  Retrieves the managed `Dev` bean from the container.

- **obj.build():**  
  Calls your method — prints "Working on a project" in the console.

---

## Why Beans?

Beans are objects managed by Spring.  
Spring handles their lifecycle, dependencies, and configuration.  
This lets you write loosely coupled, testable, and maintainable code.

---

## Extra Tips to Keep in Mind

- **Package Structure Matters**  
  Spring scans for beans in the package of your main class and its sub-packages. Keep your components inside or beneath `com.example.demo`.

- **Dependency Injection**  
  Instead of calling `context.getBean(...)`, you can use `@Autowired` to inject dependencies into classes automatically (more idiomatic in Spring).

- **Auto-configuration**  
  Spring Boot configures your app based on what it finds on the classpath. You rarely need manual setup for common things.

- **Application Properties**  
  You can customize your application using the `application.properties` or `application.yml` file in the `src/main/resources` directory.

- **Bean Scopes**  
  By default, beans are singletons (one instance per Spring container). You can change this with annotations like `@Scope("prototype")`.

- **Profiles**  
  Use `@Profile` to define beans or configurations that should only be active in certain environments (e.g., `dev`, `prod`).

- **Spring Boot DevTools**  
  Adding the DevTools dependency enables automatic restarts and live reload for a better development experience.

- **Testing**  
  Spring Boot provides testing support with annotations like `@SpringBootTest` to easily test your components.

- **Logging**  
  Spring Boot uses SLF4J with Logback by default. You can control logging levels in `application.properties`.

- **Actuator**  
  The Spring Boot Actuator module gives you production-ready features like health checks and metrics with minimal setup.

---

> **Remember:**  
> Spring Boot is designed to reduce boilerplate and make it easy to get started. Focus on writing your business logic, and let Spring handle the infrastructure!