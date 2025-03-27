Object-Oriented Programming (OOP) in Java is built around four main characteristics (or principles) that enable modular, 
reusable, and maintainable code. These are Encapsulation, Inheritance, Polymorphism, and Abstraction. 
Here’s a breakdown of each:

1. Encapsulation
- Definition: Encapsulation is the bundling of data (attributes) and methods (behavior) into a single unit (a class), 
while restricting direct access to some of an object’s components. 
It’s often achieved using access modifiers (e.g., private, public) and getter/setter methods.
- Purpose: Protects the internal state of an object from unintended interference and misuse, promoting data integrity and security.
- How in Java: Use private fields with public methods to control access.
- Example:
```java
public class Person {
    private String name; // Private field
    private int age;

    // Public getters and setters
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        if (age >= 0) { // Validation
            this.age = age;
        }
    }
}
```
Here, name and age are encapsulated, and access is controlled via methods.

2. Inheritance
- Definition: Inheritance allows a class (subclass/child) to inherit properties and methods from another class (superclass/parent),
promoting code reuse and establishing a hierarchical relationship.
- Purpose: Reduces redundancy by letting subclasses share common functionality while adding or overriding specific behavior.
- How in Java: Use the extends keyword. Java supports single inheritance for classes (one superclass), 
but multiple inheritance via interfaces.
- Example:
```java
public class Animal {
    public void eat() {
        System.out.println("This animal eats food.");
    }
}

public class Dog extends Animal {
    public void bark() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Inherited from Animal
        dog.bark(); // Defined in Dog
    }
}
```
Dog inherits eat() from Animal and adds its own bark() method.

3. Polymorphism
- Definition: Polymorphism allows objects of different classes to be treated as objects of a common superclass or interface. 
It means "many forms" and is achieved through method overriding (runtime polymorphism) or method overloading 
(compile-time polymorphism).
- Purpose: Enables flexibility and extensibility by allowing a single interface to represent different underlying forms (data types).
- How in Java:
   - Overriding: Subclass provides a specific implementation of a superclass method (using @Override).
   - Overloading: Multiple methods with the same name but different parameters in the same class.
- Example (Overriding)
```java
public class Animal {
    public void sound() {
        System.out.println("Some generic sound");
    }
}

public class Cat extends Animal {
    @Override
    public void sound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Cat(); // Polymorphism
        myAnimal.sound(); // Outputs "Meow"
    }
}
```
- Example (Overloading)
```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    public double add(double a, double b) {
        return a + b;
    }
}
```

4. Abstraction
- Definition: Abstraction is the process of hiding complex implementation details and exposing only 
the essential features of an object. It’s achieved using abstract classes or interfaces.
- Purpose: Simplifies interaction with objects by focusing on "what" they do rather than "how" they do it, reducing complexity.
- How in Java: Use the abstract keyword for abstract classes or interface for fully abstract types. Subclasses or implementing classes provide concrete implementations.
- Example (Interface):
```java
public interface Vehicle {
    void start(); // Abstract method
    void stop();
}

public class Car implements Vehicle {
    public void start() {
        System.out.println("Car starts with a key.");
    }
    public void stop() {
        System.out.println("Car stops with brakes.");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle myCar = new Car();
        myCar.start(); // Outputs "Car starts with a key."
        myCar.stop();  // Outputs "Car stops with brakes."
    }
}
```
Vehicle defines the contract; Car provides the implementation.

Summary (Principle - Key Concept - Java Mechanism - Benefit)  
Encapsulation - Data hiding and bundling - private, getters/setters - Security, control  
Inheritance - Reusing code from a parent class - extends - Code reuse, hierarchy  
Polymorphism - Multiple forms of a method/object - Overriding, overloading - Flexibility, extensibility  
Abstraction - Hiding details, showing essentials - abstract, interface - Simplicity, modularity  
