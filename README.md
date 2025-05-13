# Object-Oriented Programming (OOP) Principles: A Comprehensive Guide

## Introduction

Object-Oriented Programming (OOP) is a foundational paradigm in software development. This guide will take you through the core OOP principles in C# with clear explanations, full code examples with comments, and practical best practices.

## Core OOP Principles

1. **Encapsulation**

   * **What:** Hiding internal state and requiring all interaction to be performed through an object's methods.
   * **Why:** Protects data integrity and simplifies maintenance.
   * **How:** Use access modifiers (private, public, protected, internal).

### Code Example (Encapsulation)

```csharp
public class BankAccount
{
    private decimal balance; // Private field (Encapsulated)

    public decimal GetBalance()
    {
        return balance;
    }

    public void Deposit(decimal amount)
    {
        if (amount > 0)
        {
            balance += amount;
        }
    }

    public void Withdraw(decimal amount)
    {
        if (amount > 0 && amount <= balance)
        {
            balance -= amount;
        }
    }
}
```

2. **Inheritance**

   * **What:** A mechanism to create a new class using properties and behaviors of an existing class.
   * **Why:** Promotes code reuse and hierarchical relationships.
   * **How:** Use the `: baseClass` syntax in C#.

### Code Example (Inheritance)

```csharp
public class Animal
{
    public void Eat() => Console.WriteLine("Animal is eating");
}

public class Dog : Animal
{
    public void Bark() => Console.WriteLine("Dog is barking");
}
}
```

3. **Polymorphism**

   * **What:** The ability for different classes to be treated as instances of the same type.
   * **Why:** Allows for flexible and scalable code.
   * **How:** Achieved through method overriding and interfaces.

### Code Example (Polymorphism)

```csharp
public class Animal
{
    public virtual void Speak() => Console.WriteLine("Animal makes a sound");
}

public class Cat : Animal
{
    public override void Speak() => Console.WriteLine("Cat meows");
}

public class Dog : Animal
{
    public override void Speak() => Console.WriteLine("Dog barks");
}
```

4. **Abstraction**

   * **What:** Hiding complex implementation details and exposing only necessary functionality.
   * **Why:** Simplifies interface usage and increases security.
   * **How:** Use abstract classes or interfaces.

### Code Example (Abstraction)

```csharp
public abstract class Shape
{
    public abstract double CalculateArea();
}

public class Circle : Shape
{
    private double radius;

    public Circle(double radius)
    {
        this.radius = radius;
    }

    public override double CalculateArea()
    {
        return Math.PI * radius * radius;
    }
}
```

## Watchouts, Do's and Don'ts

* **Encapsulation:** Avoid making fields public; always use properties.
* **Inheritance:** Prefer composition over inheritance if there is no "is-a" relationship.
* **Polymorphism:** Always use `override` when overriding methods.
* **Abstraction:** Keep abstract methods generic; avoid implementation logic in abstract classes.

## Summary: Questions and Answers

1. **What is Encapsulation?**

   * Encapsulation is the concept of hiding internal data and exposing only necessary methods.

2. **How does Inheritance promote code reuse?**

   * Inheritance allows a class to inherit properties and methods from another class, promoting code reuse.

3. **What is Polymorphism, and how is it achieved in C#?**

   * Polymorphism allows objects of different types to be treated as the same type, achieved using method overriding and interfaces.

4. **What is the difference between an Abstract Class and an Interface?**

   * Abstract classes can have implementations, while interfaces only define methods.

5. **How do you achieve encapsulation in C#?**

   * By using access modifiers (private, public, protected) to control access to fields and methods.

6. **When should you use Interfaces over Abstract Classes?**

   * Use interfaces for pure contracts without implementation, and abstract classes for partial implementations.

7. **What are the key differences between Inheritance and Composition?**

   * Inheritance creates an "is-a" relationship, while composition creates a "has-a" relationship.

8. **How can Polymorphism lead to flexible code?**

   * It allows methods to be called on objects of different types without knowing their specific type.

9. **What are access modifiers in C#?**

   * Access modifiers define the visibility of class members (public, private, protected, internal).

10. **What are the benefits of using OOP principles?**

* OOP promotes modular, maintainable, reusable, and scalable code.


# SOLID Principles and Design Patterns

## Section 1: SOLID Principles

1. **Single Responsibility Principle (SRP)**

   * **What:** A class should have only one reason to change.
   * **Why:** This promotes maintainability and avoids tightly coupled code.
   * **How:** Separate responsibilities into distinct classes.

### Code Example (SRP)

```csharp
public class Order
{
    public void PlaceOrder() => Console.WriteLine("Order Placed.");
}

public class OrderLogger
{
    public void LogOrder() => Console.WriteLine("Order Logged.");
}
```

2. **Open/Closed Principle (OCP)**

   * **What:** Software entities should be open for extension but closed for modification.
   * **Why:** This allows new features without altering existing code.
   * **How:** Use inheritance, interfaces, and polymorphism.

### Code Example (OCP)

```csharp
public interface IDiscount
{
    double ApplyDiscount(double amount);
}

public class NoDiscount : IDiscount
{
    public double ApplyDiscount(double amount) => amount;
}

public class SeasonalDiscount : IDiscount
{
    public double ApplyDiscount(double amount) => amount * 0.9;
}
```

3. **Liskov Substitution Principle (LSP)**

   * **What:** Subtypes must be substitutable for their base types.
   * **Why:** Prevents unexpected behavior.
   * **How:** Use interfaces or base classes with clear contracts.

### Code Example (LSP)

```csharp
public class Bird
{
    public virtual void Fly() => Console.WriteLine("Bird is flying");
}

public class Sparrow : Bird { }

public class Ostrich : Bird
{
    public override void Fly() => throw new NotSupportedException("Ostrich cannot fly");
}
```

4. **Interface Segregation Principle (ISP)**

   * **What:** Clients should not be forced to depend on methods they do not use.
   * **Why:** Promotes modularity and flexibility.
   * **How:** Create small, specific interfaces.

### Code Example (ISP)

```csharp
public interface IPrinter
{
    void Print();
}

public interface IScanner
{
    void Scan();
}

public class MultiFunctionPrinter : IPrinter, IScanner
{
    public void Print() => Console.WriteLine("Printing...");
    public void Scan() => Console.WriteLine("Scanning...");
}
```

5. **Dependency Inversion Principle (DIP)**

   * **What:** High-level modules should not depend on low-level modules; both should depend on abstractions.
   * **Why:** Promotes decoupled code.
   * **How:** Use dependency injection and interfaces.

### Code Example (DIP)

```csharp
public interface ILogger
{
    void Log(string message);
}

public class ConsoleLogger : ILogger
{
    public void Log(string message) => Console.WriteLine(message);
}

public class OrderService
{
    private readonly ILogger _logger;

    public OrderService(ILogger logger)
    {
        _logger = logger;
    }

    public void ProcessOrder()
    {
        _logger.Log("Order processed.");
    }
}
```

## Section 2: Design Patterns (10 Most Common)

1. Singleton
2. Factory Method
3. Abstract Factory
4. Builder
5. Prototype
6. Adapter
7. Decorator
8. Observer
9. Strategy
10. Command

## Watchouts, Do's and Don'ts

* Avoid violating SOLID principles to keep code maintainable.
* Prefer interfaces over concrete classes for dependency injection.
* Ensure design patterns solve real problems, not add unnecessary complexity.

## Summary: Questions and Answers

1. **What is the Single Responsibility Principle (SRP)?**

   * SRP means a class should only have one reason to change. It ensures that each class has one clear responsibility, making the codebase easier to maintain and extend.

2. **How does the Open/Closed Principle (OCP) support extensibility?**

   * OCP means classes should be open for extension but closed for modification. You can add new functionality without altering existing code, using polymorphism or inheritance.

3. **What is the Liskov Substitution Principle (LSP)?**

   * LSP means that objects of a derived class should be replaceable for objects of the base class without affecting program correctness.

4. **How do you achieve Interface Segregation Principle (ISP)?**

   * ISP means creating small, specific interfaces instead of one large interface, ensuring that classes only implement what they need.

5. **What is Dependency Inversion Principle (DIP) and why is it important?**

   * DIP means high-level modules should not depend on low-level modules; both should depend on abstractions, promoting loose coupling and testability.

6. **What is a Design Pattern? Why do we use them?**

   * A Design Pattern is a proven solution to a recurring problem in software design. They make software scalable, maintainable, and reusable.

7. **Explain the Singleton Pattern with an example.**

   * Singleton Pattern ensures a class has only one instance and provides a global access point. Example: Database connection manager.

8. **What is the difference between Factory and Abstract Factory Patterns?**

   * Factory creates objects without specifying the exact class, while Abstract Factory creates families of related objects without specifying their concrete classes.

9. **How does the Strategy Pattern promote flexibility?**

   * Strategy Pattern defines a family of algorithms and makes them interchangeable at runtime, promoting flexible code.

10. **When should you use the Observer Pattern?**

* Use Observer Pattern when an object needs to notify multiple objects about state changes without tightly coupling them.

# Mastering 20 Common Design Patterns in C\#

## Introduction

Design Patterns are proven solutions to common problems in software design. They provide templates for writing flexible, scalable, and maintainable code. This guide covers the 20 most common design patterns in C#, with full code implementations, detailed explanations, use cases, and best practices.

## Section 1: Creational Patterns

### 1. Singleton Pattern

* **Definition:** Ensures a class has only one instance and provides a global access point.
* **When to Use:** Use when you need to ensure only one instance of a class is created, such as a database connection.
* **Similar Patterns to Learn:** Factory Method, Abstract Factory.

```csharp
public sealed class Singleton
{
    private static Singleton _instance = null;
    private static readonly object _lock = new object();

    private Singleton() { }

    public static Singleton Instance
    {
        get
        {
            lock (_lock)
            {
                if (_instance == null)
                    _instance = new Singleton();
            }
            return _instance;
        }
    }
}
```

### 2. Factory Method Pattern

* **Definition:** Provides an interface for creating objects without specifying their concrete classes.
* **When to Use:** Use when you need to delegate object creation to subclasses.
* **Similar Patterns to Learn:** Abstract Factory, Builder.

```csharp
public interface IVehicle
{
    void Drive();
}

public class Car : IVehicle
{
    public void Drive() => Console.WriteLine("Driving a car.");
}

public class Bike : IVehicle
{
    public void Drive() => Console.WriteLine("Riding a bike.");
}

public class VehicleFactory
{
    public static IVehicle CreateVehicle(string type)
    {
        return type switch
        {
            "Car" => new Car(),
            "Bike" => new Bike(),
            _ => throw new ArgumentException("Invalid vehicle type")
        };
    }
}
```

### 3. Abstract Factory Pattern

* **Definition:** Creates families of related objects without specifying their concrete classes.
* **When to Use:** Use when your system needs to work with multiple related object families.
* **Similar Patterns to Learn:** Factory Method, Prototype.

```csharp
public interface IGUIFactory
{
    IButton CreateButton();
}

public class WindowsFactory : IGUIFactory
{
    public IButton CreateButton() => new WindowsButton();
}

public class MacOSFactory : IGUIFactory
{
    public IButton CreateButton() => new MacOSButton();
}
```

### 4. Builder Pattern

* **Definition:** Separates the construction of a complex object from its representation.
* **When to Use:** Use when you need to create a complex object step by step.
* **Similar Patterns to Learn:** Factory Method, Prototype.

```csharp
public class Computer
{
    public string CPU { get; set; }
    public string RAM { get; set; }
    public string Storage { get; set; }
}

public class ComputerBuilder
{
    private Computer _computer = new Computer();

    public ComputerBuilder SetCPU(string cpu)
    {
        _computer.CPU = cpu;
        return this;
    }

    public Computer Build() => _computer;
}
```

### 5. Prototype Pattern

* **Definition:** Creates objects by copying an existing object (clone).
* **When to Use:** Use when object creation is expensive or complex.
* **Similar Patterns to Learn:** Builder, Abstract Factory.

```csharp
public class Shape
{
    public string Color { get; set; }

    public Shape Clone()
    {
        return (Shape)this.MemberwiseClone();
    }
}
```

## Section 2: Structural Patterns

### 6. Adapter Pattern

* **Definition:** Converts the interface of a class into another interface clients expect.
* **When to Use:** Use when you need to integrate classes with incompatible interfaces.
* **Similar Patterns to Learn:** Bridge, Proxy.

```csharp
public interface ITarget
{
    void Request();
}

public class Adaptee
{
    public void SpecificRequest() => Console.WriteLine("Specific Request");
}

public class Adapter : ITarget
{
    private readonly Adaptee _adaptee = new Adaptee();

    public void Request()
    {
        _adaptee.SpecificRequest();
    }
}
```
## 7. Bridge Pattern

* **Definition:** Separates an abstraction from its implementation so that they can vary independently.
* **When to Use:** Use when you want to decouple abstraction and implementation.
* **Similar Patterns to Learn:** Adapter, Composite.

```csharp
public interface IRenderer
{
    void RenderShape(string shape);
}

public class VectorRenderer : IRenderer
{
    public void RenderShape(string shape) => Console.WriteLine($"Drawing {shape} with vectors");
}

public class RasterRenderer : IRenderer
{
    public void RenderShape(string shape) => Console.WriteLine($"Drawing {shape} with pixels");
}

public class Shape
{
    protected IRenderer renderer;

    public Shape(IRenderer renderer)
    {
        this.renderer = renderer;
    }
}

public class Circle : Shape
{
    public Circle(IRenderer renderer) : base(renderer) { }

    public void Draw() => renderer.RenderShape("Circle");
}
```

## 8. Composite Pattern

* **Definition:** Composes objects into tree structures to represent part-whole hierarchies.
* **When to Use:** Use when you need to work with tree-like structures.
* **Similar Patterns to Learn:** Decorator, Flyweight.

```csharp
public interface IComponent
{
    void Display();
}

public class Leaf : IComponent
{
    public void Display() => Console.WriteLine("Leaf");
}

public class Composite : IComponent
{
    private readonly List<IComponent> _children = new List<IComponent>();

    public void Add(IComponent component) => _children.Add(component);

    public void Display()
    {
        Console.WriteLine("Composite");
        foreach (var child in _children) child.Display();
    }
}
```

## 9. Decorator Pattern

* **Definition:** Adds responsibilities to an object dynamically.
* **When to Use:** Use when you need to add features to an object without modifying its class.
* **Similar Patterns to Learn:** Proxy, Composite.

```csharp
public interface ICoffee
{
    string GetDescription();
}

public class BasicCoffee : ICoffee
{
    public string GetDescription() => "Basic Coffee";
}

public class MilkDecorator : ICoffee
{
    private readonly ICoffee _coffee;

    public MilkDecorator(ICoffee coffee)
    {
        _coffee = coffee;
    }

    public string GetDescription() => _coffee.GetDescription() + ", Milk";
}
```

## 10. Facade Pattern

* **Definition:** Provides a unified interface to a set of interfaces in a subsystem.
* **When to Use:** Use when you want to simplify complex subsystems.
* **Similar Patterns to Learn:** Mediator, Adapter.

```csharp
public class SubsystemA
{
    public void OperationA() => Console.WriteLine("Subsystem A operation");
}

public class SubsystemB
{
    public void OperationB() => Console.WriteLine("Subsystem B operation");
}

public class Facade
{
    private readonly SubsystemA _subsystemA = new SubsystemA();
    private readonly SubsystemB _subsystemB = new SubsystemB();

    public void PerformOperations()
    {
        _subsystemA.OperationA();
        _subsystemB.OperationB();
    }
}
```

