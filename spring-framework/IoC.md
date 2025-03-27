IoC: Inversion of Control  
=> is a fundamental design principle and one of the core concepts in the Spring Framework. In refers to the idea of inverting
the traditional control flow of an application, where instead of your code directly managing the creation and lifecycle of
objects (dependencies), this responsibility is delegated to an external entity - typically a container or framework
like Spring. In Spring, IoC is implemented through its IoC Container, which managers object creation, configuration, 
and dependency injection.

Traditional Control: In a conventional application, your code explicitly creates and manages objects. For example:
```java
public class OrderService {
    private PaymentProcessor paymentProcessor = new CreditCardProcessor(); // You control instantiation
    public void processOrder() {
        paymentProcessor.process();
    }
}
```
Here, OrderService is tightly coupled to CreditCardProcessor and controls its creation.

Inversion of Control: With IoC, you invert this responsibility. The Spring IoC Container creates and manages PaymentProcessor, 
injecting it into OrderService as needed:
```java
public class OrderService {
    private PaymentProcessor paymentProcessor; // No direct instantiation
    public OrderService(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor; // Injected by Spring
    }
    public void processOrder() {
        paymentProcessor.process();
    }
}
```
The control of object creation and wiring is "inverted" to Spring.

How IoC Works in Spring  
Spring’s IoC is implemented via its IoC Container (also called the Application Context), which:
- Reads Configuration: Spring uses configuration metadata (XML, Java annotations, or Java-based config) to understand
what beans (objects) to create and how to wire them.
- Creates Beans: Instantiates objects (called "beans" in Spring) based on this metadata.
- Manages Dependencies: Injects dependencies into beans automatically.
- Handles Lifecycle: Manages the lifecycle of beans (e.g., initialization, destruction).

Types of IoC Containers in Spring
- BeanFactory: A basic IoC container providing lazy-loaded bean creation (less commonly used).
- ApplicationContext: An advanced container (most common), extending BeanFactory with features like event propagation,
internationalization, and eager loading.

Dependency Injection (DI): The Mechanism of IoC  
IoC in Spring is primarily achieved through Dependency Injection (DI), a pattern where dependencies are provided 
to a class rather than the class creating them itself. Spring supports three types of DI:
- Constructor Injection: Dependencies are provided as constructor parameters.
```java
@Component
public class OrderService {
    private final PaymentProcessor paymentProcessor;

    @Autowired // Optional in Spring 4.3+ for single constructor
    public OrderService(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor;
    }
}
```
- Setter Injection: Dependencies are set via setter methods.
```java
@Component
public class OrderService {
    private PaymentProcessor paymentProcessor;

    @Autowired
    public void setPaymentProcessor(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor;
    }
}
```
- Field Injection: Dependencies are injected into fields directly (less common), (less recommended due to testing challenges)
```java
@Component
public class OrderService {
    @Autowired
    private PaymentProcessor paymentProcessor; // Injected directly
}
```

Configuration Methods
1. XML Configuration (Legacy)
   Define beans in an XML file:
```xml
<bean id="paymentProcessor" class="com.example.CreditCardProcessor"/>
<bean id="orderService" class="com.example.OrderService">
    <constructor-arg ref="paymentProcessor"/>
</bean>
```
Load with ClassPathXmlApplicationContext.
2. Annotation-Based Configuration (Modern)
   Use annotations like @Component, @Service, @Autowired:
```java
@Service
public class OrderService {
    private final PaymentProcessor paymentProcessor;

    @Autowired
    public OrderService(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor;
    }
}

@Component
public class CreditCardProcessor implements PaymentProcessor {
    public void process() { /* ... */ }
}
```
Enable with @ComponentScan in a configuration class.
3. Java-Based Configuration
   Use @Configuration and @Bean
```java
@Configuration
public class AppConfig {
    @Bean
    public PaymentProcessor paymentProcessor() {
        return new CreditCardProcessor();
    }

    @Bean
    public OrderService orderService(PaymentProcessor paymentProcessor) {
        return new OrderService(paymentProcessor);
    }
}
```
Load with AnnotationConfigApplicationContext.

Benefits of IoC in Spring
- Loose Coupling: Classes depend on abstractions (e.g., interfaces) rather than concrete implementations.
- Testability: Easy to swap dependencies (e.g., mock PaymentProcessor in tests).
- Flexibility: Change implementations without modifying dependent code (e.g., switch from CreditCardProcessor to PayPalProcessor).
- Centralized Management: Spring handles object lifecycle and configuration in one place.
- Reusability: Beans can be reused across the application.

Spring Boot and IoC  
Spring Boot enhances IoC with auto-configuration  
Automatically creates beans for common components (e.g., DataSource, EntityManager) based on dependencies in your pom.xml  
Example: Add spring-boot-starter-data-jpa, and Spring Boot sets up a JpaTransactionManager bean  
Use @SpringBootApplication (includes @ComponentScan) to bootstrap the IoC Container.  

Key Annotations
- @Component: Marks a class as a Spring-managed bean.
- @Autowired: Injects dependencies.
- @Qualifier: Resolves ambiguity when multiple beans of the same type exist.
- @Primary: Marks a preferred bean when multiple implementations are available.
- @Bean: Defines a bean in a @Configuration class.

IoC Container Lifecycle
- Startup: Spring scans for beans (via annotations or config) and instantiates them.
- Dependency Resolution: Injects dependencies into beans.
- Initialization: Calls @PostConstruct methods or InitializingBean hooks.
- Usage: Beans are available for the application.
- Shutdown: Calls @PreDestroy or DisposableBean hooks when the context closes.

Common Pitfalls
- Ambiguity: Multiple beans of the same type without @Qualifier or @Primary cause errors.
- Circular Dependencies: Bean A depends on B, and B depends on A—use setter injection or @Lazy to resolve.
- Manual Instantiation: Calling new bypasses IoC—always let Spring manage beans.

Summary
- IoC Definition: Control of object creation and management is inverted to Spring’s IoC Container.
- Implementation: Via Dependency Injection (constructor, setter, field).
- Purpose: Decouples components, enhances modularity, and simplifies testing.
- Spring Boot Bonus: Auto-configuration makes IoC even easier.
