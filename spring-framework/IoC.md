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

