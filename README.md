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

# 50 Common Design Patterns in C\#

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
# Design Patterns 7-15: Full Details with Code

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

## 11. Flyweight Pattern

* **Definition:** Reduces memory usage by sharing common state among multiple objects.
* **When to Use:** Use when you need to create a large number of similar objects.
* **Similar Patterns to Learn:** Singleton, Prototype.

```csharp
public class Character
{
    public char Symbol { get; set; }
    public string Font { get; set; }
}

public class CharacterFactory
{
    private readonly Dictionary<char, Character> _characters = new();

    public Character GetCharacter(char symbol)
    {
        if (!_characters.ContainsKey(symbol))
        {
            _characters[symbol] = new Character { Symbol = symbol };
        }
        return _characters[symbol];
    }
}
```

## 12. Proxy Pattern

* **Definition:** Provides a surrogate or placeholder for another object to control access.
* **When to Use:** Use when you need to control access to an object.
* **Similar Patterns to Learn:** Decorator, Adapter.

```csharp
public interface IService
{
    void Execute();
}

public class RealService : IService
{
    public void Execute() => Console.WriteLine("Real service executed.");
}

public class ProxyService : IService
{
    private readonly RealService _realService = new();

    public void Execute()
    {
        Console.WriteLine("Proxy controlling access.");
        _realService.Execute();
    }
}
```

## 13. Chain of Responsibility Pattern

* **Definition:** Passes a request along a chain of handlers.
* **When to Use:** Use when you have multiple handlers for a request.
* **Similar Patterns to Learn:** Command, Mediator.

```csharp
public abstract class Handler
{
    protected Handler Next;

    public void SetNext(Handler next) => Next = next;
    public abstract void HandleRequest(string request);
}

public class AuthHandler : Handler
{
    public override void HandleRequest(string request)
    {
        Console.WriteLine("Authenticating request.");
        Next?.HandleRequest(request);
    }
}
```

## 14. Command Pattern

* **Definition:** Encapsulates a request as an object.
* **When to Use:** Use when you need to parameterize objects with actions.
* **Similar Patterns to Learn:** Chain of Responsibility, Mediator.

```csharp
public interface ICommand
{
    void Execute();
}

public class LightOnCommand : ICommand
{
    public void Execute() => Console.WriteLine("Light is turned on.");
}
```

## 15. Interpreter Pattern

* **Definition:** Defines a representation for a language grammar and an interpreter to evaluate it.
* **When to Use:** Use when you need to implement a language interpreter.
* **Similar Patterns to Learn:** Visitor, Command.

```csharp
public interface IExpression
{
    int Interpret();
}

public class NumberExpression : IExpression
{
    private readonly int _number;

    public NumberExpression(int number)
    {
        _number = number;
    }

    public int Interpret() => _number;
}
```
# Design Patterns 16-20: Full Details with Code

## 16. Mediator Pattern

* **Definition:** Defines an object that encapsulates how a set of objects interact.
* **When to Use:** Use when you want to centralize complex communication logic.
* **Similar Patterns to Learn:** Observer, Facade.

```csharp
public interface IMediator
{
    void SendMessage(string message, User user);
}

public class ChatMediator : IMediator
{
    private readonly List<User> _users = new();

    public void RegisterUser(User user) => _users.Add(user);

    public void SendMessage(string message, User user)
    {
        foreach (var u in _users)
        {
            if (u != user) u.ReceiveMessage(message);
        }
    }
}

public class User
{
    private readonly IMediator _mediator;
    public string Name { get; }

    public User(IMediator mediator, string name)
    {
        _mediator = mediator;
        Name = name;
    }

    public void Send(string message) => _mediator.SendMessage(message, this);
    public void ReceiveMessage(string message) => Console.WriteLine($"{Name} received: {message}");
}
```

## 17. Memento Pattern

* **Definition:** Captures and restores an object's internal state without violating encapsulation.
* **When to Use:** Use when you need to save and restore object states.
* **Similar Patterns to Learn:** Command, Prototype.

```csharp
public class Editor
{
    public string Content { get; set; }

    public EditorState Save() => new EditorState(Content);
    public void Restore(EditorState state) => Content = state.Content;
}

public class EditorState
{
    public string Content { get; }

    public EditorState(string content) => Content = content;
}

public class History
{
    private readonly Stack<EditorState> _states = new();

    public void Push(EditorState state) => _states.Push(state);
    public EditorState Pop() => _states.Pop();
}
```

## 18. Observer Pattern

* **Definition:** Defines a one-to-many dependency between objects so that when one object changes state, all dependents are notified.
* **When to Use:** Use when you need to notify multiple objects of state changes.
* **Similar Patterns to Learn:** Mediator, Event.

```csharp
public interface IObserver
{
    void Update(string message);
}

public class ConcreteObserver : IObserver
{
    public string Name { get; }

    public ConcreteObserver(string name) => Name = name;

    public void Update(string message) => Console.WriteLine($"{Name} received: {message}");
}

public class Subject
{
    private readonly List<IObserver> _observers = new();

    public void Attach(IObserver observer) => _observers.Add(observer);
    public void Notify(string message)
    {
        foreach (var observer in _observers)
            observer.Update(message);
    }
}
```

## 19. State Pattern

* **Definition:** Allows an object to change its behavior when its internal state changes.
* **When to Use:** Use when an object’s behavior depends on its state.
* **Similar Patterns to Learn:** Strategy, Command.

```csharp
public interface IState
{
    void Handle(Context context);
}

public class HappyState : IState
{
    public void Handle(Context context) => Console.WriteLine("I am happy!");
}

public class SadState : IState
{
    public void Handle(Context context) => Console.WriteLine("I am sad.");
}

public class Context
{
    private IState _state;

    public void SetState(IState state) => _state = state;
    public void Request() => _state?.Handle(this);
}
```

## 20. Strategy Pattern

* **Definition:** Defines a family of algorithms, encapsulates each one, and makes them interchangeable.
* **When to Use:** Use when you need to switch between multiple algorithms at runtime.
* **Similar Patterns to Learn:** State, Template Method.

```csharp
public interface IStrategy
{
    int Execute(int a, int b);
}

public class AdditionStrategy : IStrategy
{
    public int Execute(int a, int b) => a + b;
}

public class SubtractionStrategy : IStrategy
{
    public int Execute(int a, int b) => a - b;
}

public class Calculator
{
    private IStrategy _strategy;

    public void SetStrategy(IStrategy strategy) => _strategy = strategy;

    public int Calculate(int a, int b) => _strategy.Execute(a, b);
}
```

# Design Patterns 21-25: Full Details with Code

## 21. Template Method Pattern

* **Definition:** Defines the skeleton of an algorithm in a base class but lets subclasses override specific steps without changing the algorithm’s structure.
* **When to Use:** Use when you have an algorithm with common steps, but some steps may vary.
* **Similar Patterns to Learn:** Strategy, State.

```csharp
public abstract class DataProcessor
{
    public void ProcessData()
    {
        LoadData();
        ProcessDataInternal();
        SaveData();
    }

    protected abstract void LoadData();
    protected abstract void ProcessDataInternal();

    protected virtual void SaveData() => Console.WriteLine("Data saved.");
}

public class CsvProcessor : DataProcessor
{
    protected override void LoadData() => Console.WriteLine("CSV data loaded.");

    protected override void ProcessDataInternal() => Console.WriteLine("Processing CSV data.");
}

public class JsonProcessor : DataProcessor
{
    protected override void LoadData() => Console.WriteLine("JSON data loaded.");

    protected override void ProcessDataInternal() => Console.WriteLine("Processing JSON data.");
}
```

## 22. Visitor Pattern

* **Definition:** Allows you to add further operations to objects without modifying their classes.
* **When to Use:** Use when you need to perform different operations on objects of different classes without modifying them.
* **Similar Patterns to Learn:** Composite, Iterator.

```csharp
public interface IElement
{
    void Accept(IVisitor visitor);
}

public class Document : IElement
{
    public void Accept(IVisitor visitor) => visitor.Visit(this);
}

public class Image : IElement
{
    public void Accept(IVisitor visitor) => visitor.Visit(this);
}

public interface IVisitor
{
    void Visit(Document document);
    void Visit(Image image);
}

public class PrintVisitor : IVisitor
{
    public void Visit(Document document) => Console.WriteLine("Printing document.");
    public void Visit(Image image) => Console.WriteLine("Printing image.");
}
```

## 23. Iterator Pattern

* **Definition:** Provides a way to access the elements of a collection sequentially without exposing the underlying structure.
* **When to Use:** Use when you need to iterate over a collection without exposing its implementation.
* **Similar Patterns to Learn:** Composite, Visitor.

```csharp
public interface IIterator<T>
{
    bool HasNext();
    T Next();
}

public class ListIterator<T> : IIterator<T>
{
    private readonly List<T> _collection;
    private int _currentIndex = 0;

    public ListIterator(List<T> collection) => _collection = collection;

    public bool HasNext() => _currentIndex < _collection.Count;

    public T Next() => _collection[_currentIndex++];
}
```

## 24. Chain of Responsibility Pattern (Advanced)

* **Definition:** Passes a request along a chain of handlers where each handler decides whether to handle the request.
* **When to Use:** Use when multiple handlers may process a request, and the handler isn't predetermined.
* **Similar Patterns to Learn:** Command, Mediator.

```csharp
public abstract class AdvancedHandler
{
    protected AdvancedHandler Next;

    public void SetNext(AdvancedHandler next) => Next = next;

    public abstract void HandleRequest(string request);
}

public class LoggingHandler : AdvancedHandler
{
    public override void HandleRequest(string request)
    {
        Console.WriteLine("Logging request.");
        Next?.HandleRequest(request);
    }
}

public class AuthenticationHandler : AdvancedHandler
{
    public override void HandleRequest(string request)
    {
        Console.WriteLine("Authenticating request.");
        Next?.HandleRequest(request);
    }
}
```

## 25. Null Object Pattern

* **Definition:** Provides a default behavior for absent or null objects.
* **When to Use:** Use when you want to avoid null checks by providing a default implementation.
* **Similar Patterns to Learn:** Strategy, Singleton.

```csharp
public interface ICustomer
{
    void Purchase();
}

public class RealCustomer : ICustomer
{
    public void Purchase() => Console.WriteLine("Customer made a purchase.");
}

public class NullCustomer : ICustomer
{
    public void Purchase() => Console.WriteLine("No customer to process.");
}
```
# Design Patterns 26-30: Full Details with Code

## 26. Singleton (Thread-Safe, Lazy Initialization)

* **Definition:** Ensures a class has only one instance, with thread-safe lazy initialization.
* **When to Use:** Use when you need a single instance of a class, and it must be created only when needed.
* **Similar Patterns to Learn:** Simple Singleton, Factory Method.

```csharp
public sealed class ThreadSafeSingleton
{
    private static readonly Lazy<ThreadSafeSingleton> _instance = new Lazy<ThreadSafeSingleton>(() => new ThreadSafeSingleton());

    private ThreadSafeSingleton() { }

    public static ThreadSafeSingleton Instance => _instance.Value;
}
```

## 27. Static Factory Pattern

* **Definition:** Provides a static method to create and return instances of classes.
* **When to Use:** Use when you want to centralize object creation without exposing constructors.
* **Similar Patterns to Learn:** Factory Method, Abstract Factory.

```csharp
public class User
{
    public string Name { get; private set; }

    private User(string name)
    {
        Name = name;
    }

    public static User CreateAdmin(string name) => new User(name + " (Admin)");

    public static User CreateGuest() => new User("Guest");
}
```

## 28. Prototype Pattern (Deep Clone)

* **Definition:** Creates a copy of an existing object, including deep copy of its fields.
* **When to Use:** Use when cloning complex objects with nested references.
* **Similar Patterns to Learn:** Shallow Prototype, Builder.

```csharp
[Serializable]
public class DeepClonePrototype
{
    public string Name { get; set; }
    public List<string> Items { get; set; } = new();

    public DeepClonePrototype DeepClone()
    {
        using (var stream = new MemoryStream())
        {
            var formatter = new BinaryFormatter();
            formatter.Serialize(stream, this);
            stream.Seek(0, SeekOrigin.Begin);
            return (DeepClonePrototype)formatter.Deserialize(stream);
        }
    }
}
```

## 29. Object Pool Pattern

* **Definition:** Manages a pool of reusable objects, reducing the overhead of object creation.
* **When to Use:** Use when objects are expensive to create, but can be reused.
* **Similar Patterns to Learn:** Factory Method, Singleton.

```csharp
public class Connection
{
    public void Connect() => Console.WriteLine("Connected.");
}

public class ConnectionPool
{
    private readonly Queue<Connection> _pool = new();

    public Connection GetConnection()
    {
        return _pool.Count > 0 ? _pool.Dequeue() : new Connection();
    }

    public void ReturnConnection(Connection conn)
    {
        _pool.Enqueue(conn);
    }
}
```

## 30. Lazy Initialization Pattern

* **Definition:** Defers object creation until it is actually needed, improving performance.
* **When to Use:** Use when creating an object is resource-intensive, and it may not always be needed.
* **Similar Patterns to Learn:** Singleton, Factory Method.

```csharp
public class HeavyObject
{
    private Lazy<string> _data = new(() => LoadData());

    private static string LoadData()
    {
        Console.WriteLine("Loading heavy data...");
        return "Heavy Data Loaded";
    }

    public string GetData() => _data.Value;
}
```
# Design Patterns 31-35: Full Details with Code

## 31. Dependency Injection Pattern

* **Definition:** A technique where an object receives its dependencies from an external source rather than creating them internally.
* **When to Use:** Use when you want to promote loose coupling and make code testable.
* **Similar Patterns to Learn:** Inversion of Control, Service Locator.

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

// Usage
var service = new OrderService(new ConsoleLogger());
service.ProcessOrder();
```

## 32. Service Locator Pattern

* **Definition:** Provides a centralized point to obtain services, avoiding direct instantiation.
* **When to Use:** Use when you have a large number of services that you want to manage centrally.
* **Similar Patterns to Learn:** Dependency Injection, Factory.

```csharp
public class ServiceLocator
{
    private static readonly Dictionary<string, object> _services = new();

    public static void RegisterService<T>(T service) => _services[typeof(T).Name] = service;

    public static T GetService<T>() => (T)_services[typeof(T).Name];
}

// Usage
ServiceLocator.RegisterService<ILogger>(new ConsoleLogger());
var logger = ServiceLocator.GetService<ILogger>();
logger.Log("Service Locator Pattern.");
```

## 33. Fluent Interface Pattern

* **Definition:** Provides a fluent, method-chaining syntax for object creation or configuration.
* **When to Use:** Use when you want a readable, chained API for configuration.
* **Similar Patterns to Learn:** Builder, Factory.

```csharp
public class FluentCar
{
    private string _make;
    private string _model;

    public FluentCar SetMake(string make)
    {
        _make = make;
        return this;
    }

    public FluentCar SetModel(string model)
    {
        _model = model;
        return this;
    }

    public void Display() => Console.WriteLine($"Car: {_make} {_model}");
}

// Usage
new FluentCar().SetMake("Tesla").SetModel("Model S").Display();
```

## 34. Double-Checked Locking Pattern

* **Definition:** A technique to ensure a singleton is created only once in a multi-threaded environment.
* **When to Use:** Use when you need a thread-safe singleton with high performance.
* **Similar Patterns to Learn:** Thread-Safe Singleton, Lazy Initialization.

```csharp
public sealed class DoubleCheckedSingleton
{
    private static DoubleCheckedSingleton _instance;
    private static readonly object _lock = new object();

    private DoubleCheckedSingleton() { }

    public static DoubleCheckedSingleton Instance
    {
        get
        {
            if (_instance == null)
            {
                lock (_lock)
                {
                    if (_instance == null)
                        _instance = new DoubleCheckedSingleton();
                }
            }
            return _instance;
        }
    }
}
```

## 35. Event Aggregator Pattern

* **Definition:** Manages events and their handlers in a centralized way.
* **When to Use:** Use when you need to decouple event producers and consumers.
* **Similar Patterns to Learn:** Observer, Mediator.

```csharp
public class EventAggregator
{
    private readonly List<Action<string>> _subscribers = new();

    public void Subscribe(Action<string> subscriber) => _subscribers.Add(subscriber);

    public void Publish(string message)
    {
        foreach (var subscriber in _subscribers)
        {
            subscriber(message);
        }
    }
}

// Usage
var aggregator = new EventAggregator();
aggregator.Subscribe(msg => Console.WriteLine("Subscriber 1: " + msg));
aggregator.Subscribe(msg => Console.WriteLine("Subscriber 2: " + msg));
aggregator.Publish("Hello World");
```
# Design Patterns 36-40: Full Details with Code

## 36. Adapter Pattern (Advanced)

* **Definition:** Converts the interface of a class into another interface clients expect.
* **When to Use:** Use when you need to integrate classes with incompatible interfaces.
* **Similar Patterns to Learn:** Bridge, Proxy.

```csharp
public interface IAdvancedTarget
{
    string GetAdvancedData();
}

public class AdvancedService
{
    public string FetchData() => "Advanced Data";
}

public class AdvancedAdapter : IAdvancedTarget
{
    private readonly AdvancedService _service = new();

    public string GetAdvancedData() => _service.FetchData();
}

// Usage
IAdvancedTarget target = new AdvancedAdapter();
Console.WriteLine(target.GetAdvancedData());
```

## 37. Repository Pattern

* **Definition:** Provides an abstraction layer for data access, centralizing data management.
* **When to Use:** Use when you want to separate data access logic from business logic.
* **Similar Patterns to Learn:** DAO, Unit of Work.

```csharp
public interface IRepository<T>
{
    void Add(T item);
    IEnumerable<T> GetAll();
}

public class ProductRepository : IRepository<string>
{
    private readonly List<string> _products = new();

    public void Add(string product) => _products.Add(product);

    public IEnumerable<string> GetAll() => _products;
}

// Usage
var repo = new ProductRepository();
repo.Add("Product A");
repo.Add("Product B");
Console.WriteLine(string.Join(", ", repo.GetAll()));
```

## 38. Specification Pattern

* **Definition:** Combines business rules using logical operators (AND, OR, NOT).
* **When to Use:** Use when you need to build complex queries with reusable conditions.
* **Similar Patterns to Learn:** Composite, Strategy.

```csharp
public interface ISpecification<T>
{
    bool IsSatisfiedBy(T item);
}

public class AgeSpecification : ISpecification<int>
{
    private readonly int _minAge;

    public AgeSpecification(int minAge) => _minAge = minAge;

    public bool IsSatisfiedBy(int age) => age >= _minAge;
}

// Usage
var ageSpec = new AgeSpecification(18);
Console.WriteLine(ageSpec.IsSatisfiedBy(20)); // True
```

## 39. Unit of Work Pattern

* **Definition:** Manages a set of changes to be committed as a single transaction.
* **When to Use:** Use when you need to maintain consistency across multiple data operations.
* **Similar Patterns to Learn:** Repository, Transaction Script.

```csharp
public class UnitOfWork
{
    private readonly List<string> _operations = new();

    public void AddOperation(string operation) => _operations.Add(operation);

    public void Commit()
    {
        Console.WriteLine("Committing operations:");
        foreach (var op in _operations)
            Console.WriteLine(op);
    }
}

// Usage
var uow = new UnitOfWork();
uow.AddOperation("Insert Order");
uow.AddOperation("Update Inventory");
uow.Commit();
```

## 40. Transaction Script Pattern

* **Definition:** Encapsulates each business operation in a separate method, providing clear transaction logic.
* **When to Use:** Use when you need to maintain clear, isolated business logic for transactions.
* **Similar Patterns to Learn:** Unit of Work, Command.

```csharp
public class OrderService
{
    public void ProcessOrder()
    {
        Console.WriteLine("Starting Transaction...");
        Console.WriteLine("Processing Order...");
        Console.WriteLine("Committing Transaction...");
    }
}

// Usage
var orderService = new OrderService();
orderService.ProcessOrder();
```
# Design Patterns 41-45: Full Details with Code

## 41. Interceptor Pattern

* **Definition:** Allows behavior to be added to an object dynamically before or after its execution.
* **When to Use:** Use when you want to add pre-processing or post-processing logic to method execution.
* **Similar Patterns to Learn:** Decorator, Proxy.

```csharp
public interface IRequestHandler
{
    void Handle(string request);
}

public class ConcreteHandler : IRequestHandler
{
    public void Handle(string request) => Console.WriteLine($"Handling request: {request}");
}

public class Interceptor : IRequestHandler
{
    private readonly IRequestHandler _handler;

    public Interceptor(IRequestHandler handler) => _handler = handler;

    public void Handle(string request)
    {
        Console.WriteLine("Before handling");
        _handler.Handle(request);
        Console.WriteLine("After handling");
    }
}

// Usage
var handler = new Interceptor(new ConcreteHandler());
handler.Handle("Login Request");
```

## 42. Null Object Pattern (Advanced)

* **Definition:** Provides a default behavior for absent or null objects, avoiding null checks.
* **When to Use:** Use when you want to avoid null checks by providing a default implementation.
* **Similar Patterns to Learn:** Singleton, Strategy.

```csharp
public interface ILogger
{
    void Log(string message);
}

public class ConsoleLogger : ILogger
{
    public void Log(string message) => Console.WriteLine(message);
}

public class NullLogger : ILogger
{
    public void Log(string message) { /* Do nothing */ }
}

// Usage
ILogger logger = new NullLogger();
logger.Log("This will not be logged.");
```

## 43. Active Record Pattern

* **Definition:** Encapsulates data access logic within the entity classes themselves.
* **When to Use:** Use when you want to combine data access and business logic in one class.
* **Similar Patterns to Learn:** Repository, Unit of Work.

```csharp
public class ActiveRecord
{
    private static List<string> _data = new();

    public string Name { get; set; }

    public void Save() => _data.Add(Name);

    public static IEnumerable<string> GetAll() => _data;
}

// Usage
var record = new ActiveRecord { Name = "John" };
record.Save();
Console.WriteLine(string.Join(", ", ActiveRecord.GetAll()));
```

## 44. Role Object Pattern

* **Definition:** Attaches multiple roles (behaviors) to a single object at runtime.
* **When to Use:** Use when an object can have multiple behaviors dynamically.
* **Similar Patterns to Learn:** Strategy, State.

```csharp
public interface IRole
{
    void Execute();
}

public class AdminRole : IRole
{
    public void Execute() => Console.WriteLine("Admin Permissions.");
}

public class UserRole : IRole
{
    public void Execute() => Console.WriteLine("User Permissions.");
}

public class User
{
    private readonly List<IRole> _roles = new();

    public void AddRole(IRole role) => _roles.Add(role);

    public void PerformActions()
    {
        foreach (var role in _roles)
            role.Execute();
    }
}

// Usage
var user = new User();
user.AddRole(new AdminRole());
user.AddRole(new UserRole());
user.PerformActions();
```

## 45. Event Sourcing Pattern

* **Definition:** Stores changes to an application's state as a sequence of events.
* **When to Use:** Use when you need to keep a full history of state changes.
* **Similar Patterns to Learn:** CQRS, Observer.

```csharp
public class EventStore
{
    private readonly List<string> _events = new();

    public void SaveEvent(string eventDescription) => _events.Add(eventDescription);

    public IEnumerable<string> GetEvents() => _events;
}

// Usage
var eventStore = new EventStore();
eventStore.SaveEvent("User registered.");
eventStore.SaveEvent("User logged in.");
Console.WriteLine(string.Join("\n", eventStore.GetEvents()));
```
# Design Patterns 46-50: Full Details with Code

## 46. CQRS (Command Query Responsibility Segregation)

* **Definition:** Separates read and write operations for better scalability and flexibility.
* **When to Use:** Use when you want to optimize read and write operations separately.
* **Similar Patterns to Learn:** Event Sourcing, Command.

```csharp
// Command (Write)
public class CreateOrderCommand
{
    public string ProductName { get; set; }
    public int Quantity { get; set; }
}

public class OrderHandler
{
    public void Handle(CreateOrderCommand command)
    {
        Console.WriteLine($"Order created: {command.ProductName} x {command.Quantity}");
    }
}

// Query (Read)
public class OrderQuery
{
    public string GetOrderDetails() => "Order Details: Product X, Quantity: 2";
}

// Usage
var handler = new OrderHandler();
handler.Handle(new CreateOrderCommand { ProductName = "Laptop", Quantity = 1 });

var query = new OrderQuery();
Console.WriteLine(query.GetOrderDetails());
```

## 47. Message Broker Pattern

* **Definition:** Manages communication between multiple services using messages.
* **When to Use:** Use when you want to decouple communication between services.
* **Similar Patterns to Learn:** Event Sourcing, Mediator.

```csharp
public class MessageBroker
{
    private readonly List<Action<string>> _subscribers = new();

    public void Subscribe(Action<string> subscriber) => _subscribers.Add(subscriber);

    public void Publish(string message)
    {
        foreach (var subscriber in _subscribers)
        {
            subscriber(message);
        }
    }
}

// Usage
var broker = new MessageBroker();
broker.Subscribe(msg => Console.WriteLine("Subscriber 1 received: " + msg));
broker.Publish("Hello World");
```

## 48. Observer (Advanced with Delegates)

* **Definition:** Defines a one-to-many dependency, using delegates for flexible notifications.
* **When to Use:** Use when you want a lightweight observer implementation.
* **Similar Patterns to Learn:** Mediator, Event.

```csharp
public class AdvancedPublisher
{
    public event Action<string> Notify;

    public void Publish(string message) => Notify?.Invoke(message);
}

// Usage
var publisher = new AdvancedPublisher();
publisher.Notify += msg => Console.WriteLine("Observer 1: " + msg);
publisher.Notify += msg => Console.WriteLine("Observer 2: " + msg);
publisher.Publish("Advanced Notification");
```

## 49. State Machine Pattern

* **Definition:** Manages an object’s behavior using a state machine that transitions between predefined states.
* **When to Use:** Use when an object’s behavior depends on its state.
* **Similar Patterns to Learn:** State, Strategy.

```csharp
public enum TrafficLightState { Red, Yellow, Green }

public class TrafficLight
{
    private TrafficLightState _state = TrafficLightState.Red;

    public void ChangeState()
    {
        _state = _state switch
        {
            TrafficLightState.Red => TrafficLightState.Green,
            TrafficLightState.Green => TrafficLightState.Yellow,
            _ => TrafficLightState.Red
        };

        Console.WriteLine($"Current State: {_state}");
    }
}

// Usage
var light = new TrafficLight();
light.ChangeState(); // Green
light.ChangeState(); // Yellow
light.ChangeState(); // Red
```

## 50. Hexagonal Architecture (Ports and Adapters)

* **Definition:** Promotes a clean architecture by decoupling core logic from external systems.
* **When to Use:** Use when you want a highly maintainable, testable architecture.
* **Similar Patterns to Learn:** Clean Architecture, Dependency Injection.

```csharp
// Application Core
public interface IOrderService
{
    void PlaceOrder(string product);
}

public class OrderService : IOrderService
{
    public void PlaceOrder(string product) => Console.WriteLine($"Order placed: {product}");
}

// Infrastructure (Adapter)
public class EmailNotification
{
    public void SendEmail(string message) => Console.WriteLine("Email sent: " + message);
}

// Usage
var orderService = new OrderService();
var emailNotification = new EmailNotification();

orderService.PlaceOrder("Book");
emailNotification.SendEmail("Your order for Book is confirmed.");
```
# Architecture Patterns 1-3: Full Details with Code

## 1. Layered (N-Tier) Architecture

* **Definition:** Organizes an application into logical layers, such as Presentation, Business Logic, and Data Access.
* **When to Use:** Use when you want a clear separation of concerns and easy maintainability.
* **Similar Patterns to Learn:** Clean Architecture, Hexagonal Architecture.

### Advantages:

* Clear separation of concerns.
* Easy to maintain and scale.
* Testable due to independent layers.

### Disadvantages:

* Can become tightly coupled.
* Changes in one layer may require changes in others.

### Example: Layered Architecture in C\#

```csharp
// Presentation Layer
public class ProductController
{
    private readonly ProductService _service = new ProductService();

    public void DisplayProducts()
    {
        var products = _service.GetProducts();
        Console.WriteLine(string.Join(", ", products));
    }
}

// Business Logic Layer
public class ProductService
{
    private readonly ProductRepository _repository = new ProductRepository();

    public List<string> GetProducts() => _repository.FetchProducts();
}

// Data Access Layer
public class ProductRepository
{
    public List<string> FetchProducts() => new List<string> { "Apple", "Banana", "Orange" };
}

// Usage
var controller = new ProductController();
controller.DisplayProducts();
```

## 2. Clean Architecture (Onion Architecture)

* **Definition:** Organizes code into concentric layers, ensuring that dependencies always point inward towards the core.
* **When to Use:** Use when you need a scalable, maintainable architecture that is independent of frameworks.
* **Similar Patterns to Learn:** Hexagonal Architecture, CQRS.

### Advantages:

* Highly testable due to dependency inversion.
* Independent of frameworks.
* Flexible and maintainable.

### Disadvantages:

* Initial complexity.
* Requires strict adherence to principles.

### Example: Clean Architecture in C\#

```csharp
// Core (Entities and Interfaces)
public class Product
{
    public string Name { get; set; }
}

public interface IProductService
{
    List<Product> GetAllProducts();
}

// Application Layer
public class ProductService : IProductService
{
    private readonly IProductRepository _repository;

    public ProductService(IProductRepository repository)
    {
        _repository = repository;
    }

    public List<Product> GetAllProducts() => _repository.GetProducts();
}

// Infrastructure Layer
public interface IProductRepository
{
    List<Product> GetProducts();
}

public class ProductRepository : IProductRepository
{
    public List<Product> GetProducts() => new List<Product> { new Product { Name = "Apple" } };
}

// Presentation Layer
public class ProductController
{
    private readonly IProductService _service;

    public ProductController(IProductService service)
    {
        _service = service;
    }

    public void ShowProducts()
    {
        var products = _service.GetAllProducts();
        Console.WriteLine(string.Join(", ", products.Select(p => p.Name)));
    }
}

// Usage
var repo = new ProductRepository();
var service = new ProductService(repo);
var controller = new ProductController(service);
controller.ShowProducts();
```

## 3. Hexagonal Architecture (Ports and Adapters)

* **Definition:** Emphasizes decoupling between the application core and external systems using ports (interfaces) and adapters (implementations).
* **When to Use:** Use when you want a clean, testable, and framework-independent architecture.
* **Similar Patterns to Learn:** Clean Architecture, Layered Architecture.

### Advantages:

* High testability.
* Framework independent.
* Easy to replace external components.

### Disadvantages:

* Complexity increases with large systems.
* Requires careful design.

### Example: Hexagonal Architecture in C\#

```csharp
// Core (Ports)
public interface INotificationService
{
    void Send(string message);
}

// Application Core
public class OrderService
{
    private readonly INotificationService _notificationService;

    public OrderService(INotificationService notificationService)
    {
        _notificationService = notificationService;
    }

    public void PlaceOrder(string product)
    {
        Console.WriteLine($"Order placed for {product}");
        _notificationService.Send("Order placed: " + product);
    }
}

// Adapter (Infrastructure)
public class EmailNotification : INotificationService
{
    public void Send(string message) => Console.WriteLine("Email sent: " + message);
}

// Usage
var emailService = new EmailNotification();
var orderService = new OrderService(emailService);
orderService.PlaceOrder("Laptop");
```
# Architecture Patterns 4-6: Full Details with Code

## 4. Microservices Architecture

* **Definition:** Organizes an application into a collection of small, loosely coupled services, each responsible for a specific domain.
* **When to Use:** Use when you want independent deployment, scalability, and maintainability of services.
* **Similar Patterns to Learn:** Event-Driven Architecture, CQRS.

### Advantages:

* Independent deployment.
* Scalability of individual services.
* Fault isolation.

### Disadvantages:

* Increased complexity.
* Network latency between services.

### Example: Microservices Architecture in C# (Basic Implementation)

```csharp
// Order Service (Microservice 1)
public class OrderService
{
    public void CreateOrder(string product)
    {
        Console.WriteLine($"Order created for {product}");
    }
}

// Payment Service (Microservice 2)
public class PaymentService
{
    public void ProcessPayment(string product)
    {
        Console.WriteLine($"Payment processed for {product}");
    }
}

// API Gateway (Simplified)
public class ApiGateway
{
    private readonly OrderService _orderService = new();
    private readonly PaymentService _paymentService = new();

    public void PlaceOrder(string product)
    {
        _orderService.CreateOrder(product);
        _paymentService.ProcessPayment(product);
    }
}

// Usage
var gateway = new ApiGateway();
gateway.PlaceOrder("Laptop");
```

## 5. Event-Driven Architecture

* **Definition:** Uses events to trigger and communicate between services, providing real-time processing.
* **When to Use:** Use when you want highly decoupled services that respond to events.
* **Similar Patterns to Learn:** Microservices, CQRS.

### Advantages:

* Loose coupling between components.
* Real-time processing.
* High scalability.

### Disadvantages:

* Complex debugging.
* Event consistency management.

### Example: Event-Driven Architecture in C\#

```csharp
// Event Publisher
public class EventPublisher
{
    public event Action<string> OnEvent;

    public void PublishEvent(string message) => OnEvent?.Invoke(message);
}

// Event Subscriber
public class EventSubscriber
{
    public void OnEventReceived(string message)
    {
        Console.WriteLine("Event Received: " + message);
    }
}

// Usage
var publisher = new EventPublisher();
var subscriber = new EventSubscriber();
publisher.OnEvent += subscriber.OnEventReceived;
publisher.PublishEvent("Order Placed");
```

## 6. CQRS (Command Query Responsibility Segregation)

* **Definition:** Separates read (Query) and write (Command) operations for improved scalability and performance.
* **When to Use:** Use when you want to optimize read and write operations separately.
* **Similar Patterns to Learn:** Event Sourcing, Microservices.

### Advantages:

* Optimized read and write operations.
* Clear separation of concerns.
* Scalable read models.

### Disadvantages:

* Increased complexity.
* Data consistency challenges.

### Example: CQRS in C\#

```csharp
// Command (Write)
public class CreateOrderCommand
{
    public string ProductName { get; set; }
}

public class OrderCommandHandler
{
    public void Handle(CreateOrderCommand command)
    {
        Console.WriteLine($"Order created: {command.ProductName}");
    }
}

// Query (Read)
public class OrderQuery
{
    public string GetOrderDetails() => "Order Details: Product X";
}

// Usage
var commandHandler = new OrderCommandHandler();
commandHandler.Handle(new CreateOrderCommand { ProductName = "Laptop" });

var query = new OrderQuery();
Console.WriteLine(query.GetOrderDetails());
```
# Architecture Patterns 7-9: Full Details with Code

## 7. Monolithic Architecture

* **Definition:** A single unified application where all components are tightly coupled and run as a single unit.
* **When to Use:** Use when you need a simple, fast-to-deploy application without complex service interactions.
* **Similar Patterns to Learn:** Layered Architecture, Modular Monolith.

### Advantages:

* Simple deployment.
* Easy to develop initially.
* All components run in a single process.

### Disadvantages:

* Difficult to scale independently.
* Changes in one area can affect the entire application.
* Harder to maintain with increasing complexity.

### Example: Monolithic Architecture in C\#

```csharp
// Monolithic Application
public class ProductService
{
    public void AddProduct(string product)
    {
        Console.WriteLine($"Product added: {product}");
    }

    public void ListProducts()
    {
        Console.WriteLine("Product list: Apple, Banana, Orange");
    }
}

// Usage
var service = new ProductService();
service.AddProduct("Laptop");
service.ListProducts();
```

## 8. Serverless Architecture

* **Definition:** A cloud-native architecture where applications are built using managed services (like Azure Functions, AWS Lambda) that automatically scale.
* **When to Use:** Use when you want automatic scaling, no server management, and pay-per-use pricing.
* **Similar Patterns to Learn:** Microservices, Event-Driven Architecture.

### Advantages:

* No server management.
* Automatic scaling.
* Cost-effective (pay-per-use).

### Disadvantages:

* Limited execution time (timeout).
* Cold start latency.

### Example: Serverless Architecture in C# (Azure Function)

```csharp
using Microsoft.Azure.Functions.Worker;
using Microsoft.Azure.Functions.Worker.Http;
using System.Threading.Tasks;

public static class ProductFunction
{
    [Function("ProductFunction")]
    public static async Task<HttpResponseData> Run(
        [HttpTrigger(AuthorizationLevel.Function, "get")] HttpRequestData req)
    {
        var response = req.CreateResponse();
        response.WriteString("Serverless Product List: Apple, Banana, Orange");
        return response;
    }
}
```

## 9. Service-Oriented Architecture (SOA)

* **Definition:** An architecture where an application is composed of reusable services that communicate over a network.
* **When to Use:** Use when you need to build an application with loosely coupled services that can be reused.
* **Similar Patterns to Learn:** Microservices, API Gateway.

### Advantages:

* Service reusability.
* Interoperability between services.
* Scalable and maintainable.

### Disadvantages:

* Overhead of service communication.
* Complex service orchestration.

### Example: Service-Oriented Architecture in C\#

```csharp
// Product Service
public class ProductService
{
    public string GetProduct() => "Apple";
}

// Order Service
public class OrderService
{
    private readonly ProductService _productService = new();

    public void CreateOrder()
    {
        var product = _productService.GetProduct();
        Console.WriteLine($"Order created for {product}");
    }
}

// Usage
var orderService = new OrderService();
orderService.CreateOrder();
```
# Architecture Patterns 10-12: Full Details with Code

## 10. Microkernel Architecture (Plugin-Based Architecture)

* **Definition:** Provides a core system with minimal functionality, and additional features are provided through plugins.
* **When to Use:** Use when you want a modular system with extensible features.
* **Similar Patterns to Learn:** Modular Monolith, Plugin Pattern.

### Advantages:

* Highly extensible with plugins.
* Core system remains lightweight.
* Easy to add or remove features.

### Disadvantages:

* Complex plugin management.
* Plugin conflicts can occur.

### Example: Microkernel Architecture in C\#

```csharp
// Core System
public class ApplicationCore
{
    private readonly List<IPlugin> _plugins = new();

    public void RegisterPlugin(IPlugin plugin) => _plugins.Add(plugin);

    public void Run()
    {
        Console.WriteLine("Core Application Running.");
        foreach (var plugin in _plugins)
            plugin.Execute();
    }
}

// Plugin Interface
public interface IPlugin
{
    void Execute();
}

// Example Plugins
public class LoggingPlugin : IPlugin
{
    public void Execute() => Console.WriteLine("Logging Plugin Executed.");
}

public class SecurityPlugin : IPlugin
{
    public void Execute() => Console.WriteLine("Security Plugin Executed.");
}

// Usage
var app = new ApplicationCore();
app.RegisterPlugin(new LoggingPlugin());
app.RegisterPlugin(new SecurityPlugin());
app.Run();
```

## 11. Modular Monolith Architecture

* **Definition:** A monolithic architecture with modular components that can be independently developed and maintained.
* **When to Use:** Use when you want modularity but without the complexity of microservices.
* **Similar Patterns to Learn:** Microservices, Layered Architecture.

### Advantages:

* Easy to develop and maintain.
* Strong modularity without microservices overhead.
* Single deployment unit.

### Disadvantages:

* Still has some monolithic limitations.
* Scaling requires scaling the entire application.

### Example: Modular Monolith in C\#

```csharp
// Module: Product Module
namespace ProductModule
{
    public class ProductService
    {
        public void DisplayProduct() => Console.WriteLine("Product: Apple");
    }
}

// Module: Order Module
namespace OrderModule
{
    public class OrderService
    {
        public void CreateOrder() => Console.WriteLine("Order Created");
    }
}

// Main Application
using ProductModule;
using OrderModule;

var productService = new ProductService();
productService.DisplayProduct();

var orderService = new OrderService();
orderService.CreateOrder();
```

## 12. Clean Microservices Architecture

* **Definition:** A scalable microservices architecture with clean architecture principles (separation of concerns, dependency inversion).
* **When to Use:** Use when you want scalable, independent services following clean architecture.
* **Similar Patterns to Learn:** Microservices, Clean Architecture.

### Advantages:

* Highly scalable.
* Clear separation of concerns.
* Testable services.

### Disadvantages:

* Initial complexity.
* Requires strict design discipline.

### Example: Clean Microservices Architecture in C\#

```csharp
// Product Microservice (Application Layer)
public class ProductService
{
    private readonly IProductRepository _repository;

    public ProductService(IProductRepository repository)
    {
        _repository = repository;
    }

    public string GetProduct() => _repository.GetProduct();
}

// Product Microservice (Infrastructure Layer)
public interface IProductRepository
{
    string GetProduct();
}

public class ProductRepository : IProductRepository
{
    public string GetProduct() => "Apple";
}

// API Layer
var repository = new ProductRepository();
var service = new ProductService(repository);
Console.WriteLine(service.GetProduct());
```
# Architecture Patterns 13-15: Full Details with Code

## 13. Clean Serverless Architecture

* **Definition:** Combines serverless computing with clean architecture principles, ensuring separation of concerns.
* **When to Use:** Use when you want a scalable, maintainable, and cleanly organized serverless application.
* **Similar Patterns to Learn:** Serverless, Clean Architecture.

### Advantages:

* Automatic scaling (serverless).
* Clean separation of concerns.
* Testable business logic.

### Disadvantages:

* Complexity increases with large systems.
* Cold start latency.

### Example: Clean Serverless Architecture in C# (Azure Function)

```csharp
// Core Layer (Business Logic)
public interface IProductService
{
    string GetProduct();
}

public class ProductService : IProductService
{
    public string GetProduct() => "Product: Apple";
}

// Infrastructure Layer (Azure Function)
using Microsoft.Azure.Functions.Worker;
using Microsoft.Azure.Functions.Worker.Http;
using System.Threading.Tasks;

public class ProductFunction
{
    private readonly IProductService _service = new ProductService();

    [Function("GetProduct")]
    public async Task<HttpResponseData> Run([HttpTrigger(AuthorizationLevel.Anonymous, "get")] HttpRequestData req)
    {
        var response = req.CreateResponse();
        response.WriteString(_service.GetProduct());
        return response;
    }
}
```

## 14. API Gateway Pattern

* **Definition:** Provides a single entry point for multiple backend services, centralizing API management.
* **When to Use:** Use when you want to simplify client communication with multiple backend services.
* **Similar Patterns to Learn:** Proxy, Service-Oriented Architecture.

### Advantages:

* Centralized API management.
* Load balancing and routing.
* Security (authentication, authorization).

### Disadvantages:

* Single point of failure (unless redundant).
* Adds an extra layer of complexity.

### Example: API Gateway in C\#

```csharp
// API Gateway
public class ApiGateway
{
    private readonly ProductService _productService = new();
    private readonly OrderService _orderService = new();

    public void RouteRequest(string endpoint)
    {
        if (endpoint == "/products")
            Console.WriteLine(_productService.GetProducts());
        else if (endpoint == "/orders")
            _orderService.CreateOrder();
        else
            Console.WriteLine("Invalid endpoint.");
    }
}

// Services
public class ProductService
{
    public string GetProducts() => "Product List: Apple, Banana";
}

public class OrderService
{
    public void CreateOrder() => Console.WriteLine("Order Created");
}

// Usage
var gateway = new ApiGateway();
gateway.RouteRequest("/products");
gateway.RouteRequest("/orders");
```

## 15. Backend for Frontend (BFF) Pattern

* **Definition:** Provides a dedicated backend for each frontend (e.g., mobile, web), optimizing API responses.
* **When to Use:** Use when you need to tailor API responses for different client applications.
* **Similar Patterns to Learn:** API Gateway, Microservices.

### Advantages:

* Optimized APIs for each frontend.
* Decouples frontend and backend development.
* Improved performance.

### Disadvantages:

* Increases code duplication.
* More backend services to maintain.

### Example: Backend for Frontend (BFF) in C\#

```csharp
// Mobile BFF
public class MobileBFF
{
    public string GetProductDetails()
    {
        return "Mobile Product: Apple - Compact View";
    }
}

// Web BFF
public class WebBFF
{
    public string GetProductDetails()
    {
        return "Web Product: Apple - Full View with Description";
    }
}

// Usage
var mobileBff = new MobileBFF();
Console.WriteLine(mobileBff.GetProductDetails());

var webBff = new WebBFF();
Console.WriteLine(webBff.GetProductDetails());
```
# Architecture Patterns 16-18: Full Details with Code

## 16. Saga Pattern

* **Definition:** Manages distributed transactions across multiple services using a series of local transactions and compensation actions.
* **When to Use:** Use when you need to maintain consistency across distributed services without using a distributed transaction.
* **Similar Patterns to Learn:** Event-Driven Architecture, CQRS.

### Advantages:

* Avoids distributed transactions.
* Provides fault tolerance with compensation.
* Scalable across services.

### Disadvantages:

* Complex coordination between services.
* Error handling is challenging.

### Example: Saga Pattern in C\#

```csharp
// Saga Orchestrator
public class OrderSaga
{
    public void StartSaga()
    {
        try
        {
            CreateOrder();
            ProcessPayment();
            ShipOrder();
        }
        catch (Exception)
        {
            Compensate();
        }
    }

    private void CreateOrder() => Console.WriteLine("Order Created");
    private void ProcessPayment() => Console.WriteLine("Payment Processed");
    private void ShipOrder() => Console.WriteLine("Order Shipped");

    private void Compensate() => Console.WriteLine("Compensating Transaction");
}

// Usage
var saga = new OrderSaga();
saga.StartSaga();
```

## 17. Strangler Pattern

* **Definition:** Gradually replaces an existing legacy system by building new functionality in parallel until the legacy system is completely replaced.
* **When to Use:** Use when you want to safely migrate a legacy system to a modern architecture.
* **Similar Patterns to Learn:** Modular Monolith, Microservices.

### Advantages:

* Safe, gradual migration.
* Minimal downtime.
* Continuous delivery of new features.

### Disadvantages:

* Requires maintaining two systems during migration.
* Complex routing logic.

### Example: Strangler Pattern in C\#

```csharp
// Legacy System
public class LegacyOrderSystem
{
    public void PlaceOrder() => Console.WriteLine("Order Placed in Legacy System");
}

// Modern System
public class ModernOrderSystem
{
    public void PlaceOrder() => Console.WriteLine("Order Placed in Modern System");
}

// Router (Strangler Switch)
public class OrderRouter
{
    private readonly LegacyOrderSystem _legacy = new();
    private readonly ModernOrderSystem _modern = new();

    public void PlaceOrder(bool useModern)
    {
        if (useModern)
            _modern.PlaceOrder();
        else
            _legacy.PlaceOrder();
    }
}

// Usage
var router = new OrderRouter();
router.PlaceOrder(useModern: true);
```

## 18. Reactive Microservices Architecture

* **Definition:** Builds microservices that respond to events in real-time using reactive principles (responsive, resilient, elastic, message-driven).
* **When to Use:** Use when you need scalable, high-performance, and fault-tolerant services.
* **Similar Patterns to Learn:** Event-Driven Architecture, Microservices.

### Advantages:

* High scalability and responsiveness.
* Fault-tolerant with event-driven communication.

### Disadvantages:

* Debugging can be complex.
* Requires careful design for consistency.

### Example: Reactive Microservices in C\#

```csharp
// Reactive Event Publisher
public class ReactiveEventPublisher
{
    public event Action<string> OnEvent;

    public void Publish(string message) => OnEvent?.Invoke(message);
}

// Reactive Event Subscriber
public class ReactiveSubscriber
{
    public void OnEventReceived(string message)
    {
        Console.WriteLine("Reactive Event Received: " + message);
    }
}

// Usage
var publisher = new ReactiveEventPublisher();
var subscriber = new ReactiveSubscriber();
publisher.OnEvent += subscriber.OnEventReceived;
publisher.Publish("Order Placed");
```
# Mastering Dependency Injection (DI) in ASP.NET Core

## Introduction

Dependency Injection (DI) is a design pattern that enables loose coupling between components in an application. In ASP.NET Core, DI is a first-class citizen and is natively supported by the framework.

### What is Dependency Injection?

Dependency Injection is a technique where an object’s dependencies are provided externally, rather than the object creating them itself.

* **Why Use DI?**: It improves code maintainability, testability, and scalability.
* **How DI Works in ASP.NET Core?**: ASP.NET Core uses a built-in DI container that supports three main lifetimes: Transient, Scoped, and Singleton.

## Core Concepts

### 1. Types of Dependency Injection

* **Constructor Injection (Most Common)**: Dependencies are provided via the constructor.

  ```csharp
  public class NotificationService
  {
      private readonly IMessageService _messageService;

      public NotificationService(IMessageService messageService)
      {
          _messageService = messageService;
      }

      public void Notify(string message)
      {
          Console.WriteLine(_messageService.SendMessage(message));
      }
  }
  ```

* **Property Injection (Setter Injection)**: Dependencies are set via properties.

  ```csharp
  public class NotificationService
  {
      public IMessageService MessageService { get; set; }

      public void Notify(string message)
      {
          Console.WriteLine(MessageService?.SendMessage(message));
      }
  }
  ```

* **Method Injection**: Dependencies are passed as method parameters.

  ```csharp
  public class NotificationService
  {
      public void Notify(IMessageService messageService, string message)
      {
          Console.WriteLine(messageService.SendMessage(message));
      }
  }
  ```

### 2. DI Lifetime Scopes (In-Depth)

* **Transient**: A new instance is created each time the service is requested.

  ```csharp
  builder.Services.AddTransient<ITransientService, TransientService>();
  ```

* **Scoped**: A new instance is created once per request (HTTP request in a web app).

  ```csharp
  builder.Services.AddScoped<IScopedService, ScopedService>();
  ```

* **Singleton**: A single instance is created for the lifetime of the application.

  ```csharp
  builder.Services.AddSingleton<ISingletonService, SingletonService>();
  ```

## Advanced DI Techniques

* Using Factory Pattern with DI
* Implementing Scoped Services with Async Context
* DI in Middleware
* Conditional DI (based on environment)

## Watchouts

* Avoid injecting too many dependencies (Constructor Over-Injection).
* Use appropriate lifetime for services (Singleton for stateless services).
* Be careful with Scoped services in Singleton.
* Circular Dependencies should be avoided.
* Avoid using static services with DI.

## Summary

### Question and Answer Mastery

1. **What is Dependency Injection (DI)?**

   * DI is a design pattern where dependencies are injected into a class rather than the class creating them.

2. **Why should you use DI in ASP.NET Core?**

   * It promotes loose coupling, enhances testability, and improves maintainability.

3. **What are the three main service lifetimes in DI?**

   * Transient, Scoped, and Singleton.

4. **How do you register a service in DI in ASP.NET Core?**

   * Using `builder.Services.AddTransient`, `AddScoped`, or `AddSingleton` methods in Program.cs.

5. **What is Constructor Injection?**

   * Dependency is provided through the constructor of the class.

6. **What is Scoped Service?**

   * A service instance is created once per HTTP request.

7. **How does Singleton differ from Transient?**

   * Singleton creates a single instance for the application's lifetime, while Transient creates a new instance on every request.

8. **How do you resolve services manually?**

   * Using `IServiceProvider.GetRequiredService<T>()`.

9. **What is the risk of injecting Scoped services in Singleton?**

   * Scoped service instances may become singletons when injected into a Singleton, leading to unexpected behavior.

10. **How can you use DI in Middleware?**

* By injecting services via the constructor of the Middleware class.


# Mastering Middleware and Filters in ASP.NET Core

## Introduction

Middleware and Filters are two powerful concepts in ASP.NET Core that control how HTTP requests and responses flow through an application.

### What is Middleware?

Middleware is software that is assembled into an application pipeline to handle HTTP requests and responses. Each middleware component decides:

* Whether to pass the request to the next middleware.
* Whether to process the request and response.

### Why Use Middleware?

* Centralized request/response handling.
* Logging, Authentication, Exception Handling, CORS, and more.

### How Middleware Works?

* Middleware is added in `Program.cs` using `app.UseMiddleware<>()` or `app.Use()` methods.
* Order matters – Middleware is processed in the sequence it is added.
* Each middleware can decide to terminate the pipeline or pass the request to the next.

### Middleware vs Filters (Clear Comparison)

* **Middleware**: Affects the entire request pipeline, including static files, authentication, etc.
* **Filters**: Specific to MVC (Controller) actions, executing around action methods.

## Types of Middleware

1. Built-in Middleware (Exception Handling, Static Files, Routing, CORS).
2. Custom Middleware (User-defined logic).
3. Conditional Middleware (Environment-specific).

## Creating Custom Middleware (Step-by-Step)

### Step 1: Create a Custom Middleware Class

```csharp
public class RequestLoggingMiddleware
{
    private readonly RequestDelegate _next;

    public RequestLoggingMiddleware(RequestDelegate next)
    {
        _next = next;
    }

    public async Task InvokeAsync(HttpContext context)
    {
        Console.WriteLine($"Request: {context.Request.Method} {context.Request.Path}");
        await _next(context);
    }
}
```

### Step 2: Register Middleware in Pipeline

```csharp
app.UseMiddleware<RequestLoggingMiddleware>();
```

### Step 3: Test the Middleware

* Any HTTP request will now be logged.

### Advanced Custom Middleware with Dependency Injection

```csharp
public class HeaderInjectionMiddleware
{
    private readonly RequestDelegate _next;
    private readonly ILogger<HeaderInjectionMiddleware> _logger;

    public HeaderInjectionMiddleware(RequestDelegate next, ILogger<HeaderInjectionMiddleware> logger)
    {
        _next = next;
        _logger = logger;
    }

    public async Task InvokeAsync(HttpContext context)
    {
        context.Response.OnStarting(() => {
            context.Response.Headers["X-Custom-Header"] = "Middleware Added Header";
            _logger.LogInformation("Custom Header Added");
            return Task.CompletedTask;
        });

        await _next(context);
    }
}
```

### Registering the Advanced Middleware

```csharp
app.UseMiddleware<HeaderInjectionMiddleware>();
```

## Middleware Ordering Explained (Critical Concept)

* Order of middleware registration in `Program.cs` directly affects execution.
* Example:

```csharp
app.UseRouting(); // Routing Middleware
app.UseAuthentication(); // Authentication Middleware
app.UseAuthorization(); // Authorization Middleware
app.UseEndpoints(endpoints => endpoints.MapControllers());
```

## Deep Dive into Filters

Filters are used to execute code before or after specific stages of request processing in MVC controllers.

### Types of Filters (In-Depth)

1. **Authorization Filters** - Validate user authentication and authorization.
2. **Resource Filters** - Execute before or after the entire request pipeline.
3. **Action Filters** - Execute code before or after an action method.
4. **Exception Filters** - Handle exceptions globally or locally.
5. **Result Filters** - Execute code before or after the action result.

### Implementing a Custom Action Filter

```csharp
public class CustomActionFilter : IActionFilter
{
    public void OnActionExecuting(ActionExecutingContext context)
    {
        Console.WriteLine("Action Executing");
    }

    public void OnActionExecuted(ActionExecutedContext context)
    {
        Console.WriteLine("Action Executed");
    }
}
```

### Applying Filter Globally

```csharp
builder.Services.AddControllers(options =>
{
    options.Filters.Add<CustomActionFilter>();
});
```

## Advanced Middleware and Filters Techniques

* Exception Handling Middleware with Custom Response
* Conditional Middleware (Using Environment Checks)
* Using Dependency Injection in Middleware
* Applying Filters Globally (Global Filters)
* Combining Middleware and Filters for Secure APIs

## Watchouts

* Middleware order is critical (Pipeline Sequence).
* Filters do not apply to non-MVC requests (like Web API).
* Avoid long-running tasks in Middleware.
* Be aware of filter conflicts (Authorization vs Action Filters).
* Avoid circular dependencies in Middleware.

## Summary

### Question and Answer Mastery

1. **What is Middleware in ASP.NET Core?**

   * Middleware is a software component that processes HTTP requests and responses.

2. **How do you create Custom Middleware?**

   * By creating a class with an `InvokeAsync` method and registering it using `app.UseMiddleware<>`.

3. **What is the difference between Use, Run, and Map in Middleware?**

   * `Use`: Continues to next middleware.
   * `Run`: Terminates the pipeline.
   * `Map`: Conditionally branches the pipeline.

4. **What are Filters?**

   * Filters are components that run before or after specific stages of the request pipeline in controllers.

5. **What are the types of Filters?**

   * Authorization, Resource, Action, Exception, Result.

6. **How do you apply a Filter to a Controller?**

   * Using `[ServiceFilter]`, `[TypeFilter]`, or `[Authorize]`.

7. **How do you create a Custom Action Filter?**

   * By implementing `IActionFilter` and registering it.

8. **How do Middleware and Filters differ?**

   * Middleware is for the entire HTTP request pipeline, while Filters are for MVC actions.

9. **What is the significance of Middleware order?**

   * The order determines how requests are processed.

10. **How do you inject services in Middleware?**

* Using the constructor of the Middleware class with DI.

# Mastering Memory Management in ASP.NET Core

## Introduction

Memory management is a critical concept for any .NET developer, especially when building high-performance web applications with ASP.NET Core. Understanding how memory is allocated, managed, and freed is essential for writing efficient and scalable code.

### Why Memory Management is Important?

* Prevents memory leaks.
* Enhances application performance.
* Reduces unnecessary resource consumption.

## Core Concepts

### 1. Garbage Collection (GC)

* **What is Garbage Collection?**

  * Garbage Collection (GC) is an automatic memory management system in .NET.
  * It automatically frees memory that is no longer in use, preventing memory leaks.

* **GC Generations (Detailed):**

  * **Generation 0:** Short-lived objects. (e.g., local variables, temporary data)
  * **Generation 1:** Medium-lived objects. (e.g., cached data)
  * **Generation 2:** Long-lived objects. (e.g., static objects, global instances)

* **GC Modes (Advanced):**

  * **Workstation (Default for desktops):** Optimized for client applications.
  * **Server (Optimized for high-performance servers):** Multi-threaded collection.
  * **Background GC:** Runs concurrently with application code.

### 2. IDisposable and Using Statement

* **What is IDisposable?**

  * An interface that allows manual resource cleanup, especially for unmanaged resources.

* **Using Statement Explained:**

  ```csharp
  using (var stream = new FileStream("example.txt", FileMode.Open))
  {
      // File is automatically disposed of at the end of the block
  }
  ```

  * Using statement ensures that the resource is properly disposed even if an exception occurs.

* **Implementing IDisposable with Dispose Pattern:**

  ```csharp
  public class ResourceHolder : IDisposable
  {
      private bool _disposed = false;

      public void UseResource()
      {
          if (_disposed) throw new ObjectDisposedException("ResourceHolder");
          Console.WriteLine("Using Resource");
      }

      public void Dispose()
      {
          Dispose(true);
          GC.SuppressFinalize(this);
      }

      protected virtual void Dispose(bool disposing)
      {
          if (_disposed) return;

          if (disposing)
          {
              // Release managed resources
              Console.WriteLine("Disposing managed resources");
          }

          // Release unmanaged resources
          Console.WriteLine("Disposing unmanaged resources");
          _disposed = true;
      }

      ~ResourceHolder()
      {
          Dispose(false);
      }
  }
  ```

### 3. Value Types vs Reference Types (Deep Dive)

* **Value Types:**

  * Stored in the stack.
  * Examples: `int`, `double`, `struct`, `bool`.
  * Memory is allocated immediately and destroyed once the method ends.

* **Reference Types:**

  * Stored in the heap.
  * Examples: `class`, `interface`, `array`, `string`.
  * Memory is managed by Garbage Collector.

### 4. Stack vs Heap Memory (In-Depth)

* **Stack Memory:**

  * Fast access (Last-In, First-Out - LIFO).
  * Stores value types and method call data.

* **Heap Memory:**

  * Slower but allows dynamic memory allocation.
  * Stores reference types and long-lived objects.

## Advanced Memory Management Techniques

### 1. Handling Large Object Heap (LOH)

* Objects larger than 85,000 bytes are stored in LOH.
* LOH is not compacted by default, which can cause memory fragmentation.
* Use `GCSettings.LargeObjectHeapCompactionMode` for manual compaction.

### 2. Avoiding Memory Leaks

* Always dispose of IDisposable objects.
* Use `WeakReference<T>` for cache without preventing GC.
* Avoid static event handlers (they prevent GC).

### 3. Understanding Finalization

* Finalizers (`~ClassName`) are called by GC before object destruction.
* Avoid long-running tasks in finalizers.

### 4. Advanced Tips

* Use `ArrayPool<T>` for reusable large arrays.
* Use `GC.Collect()` only for testing, not in production.
* Prefer `Span<T>` and `Memory<T>` for low-level optimizations.

## Watchouts

* Avoid memory leaks by disposing of resources properly.
* Be careful with large object allocations (LOH).
* Avoid circular references in managed objects.
* Do not call `GC.Collect()` in production.
* Understand the difference between Stack and Heap allocations.

## Summary

### Question and Answer Mastery

1. **What is Garbage Collection (GC) in .NET?**

   * GC is an automatic memory management system that reclaims unused objects.

2. **What are the GC generations?**

   * Generation 0 (short-lived), Generation 1 (medium-lived), Generation 2 (long-lived).

3. **What is the difference between stack and heap?**

   * Stack is for value types and method calls (LIFO), while Heap is for reference types and long-lived objects.

4. **What is IDisposable, and why is it important?**

   * IDisposable is an interface for manual resource cleanup, avoiding memory leaks.

5. **How does the `using` statement help with memory management?**

   * It ensures IDisposable objects are automatically disposed of when out of scope.

6. **What are Value Types and Reference Types?**

   * Value Types are stored in the stack, Reference Types are stored in the heap.

7. **How does the Dispose Pattern work?**

   * It provides a safe way to release both managed and unmanaged resources.

8. **What is the Large Object Heap (LOH)?**

   * A special heap for objects larger than 85,000 bytes.

9. **How do you prevent memory leaks in ASP.NET Core?**

   * Dispose of unmanaged resources, avoid static event handlers, use `WeakReference`.

10. **What is the difference between a weak reference and a strong reference?**

* A weak reference allows GC to collect the object even if it is referenced.


# Mastering ASP.NET Core Internals for Senior Developers

## Introduction

ASP.NET Core is a powerful, high-performance, open-source framework for building modern, cloud-based, and cross-platform web applications. Understanding its internals is essential for senior developers who want to write optimized, scalable, and secure applications.

## Core Concepts

### 1. ASP.NET Core Request Processing Pipeline

* **What is the Request Pipeline?**

  * It is a series of middleware components that process HTTP requests and responses.
  * Each request goes through this pipeline, and each middleware can either process the request or pass it to the next.

* **How does it work? (Detailed Flow)**

  1. HTTP Request received by the Kestrel Server.
  2. Middleware processes the request in order (Exception Handling, Static Files, Routing).
  3. Routing Middleware identifies the matching route.
  4. MVC Middleware (Controller) processes the request.
  5. HTTP Response is sent back to the client.

### Request Pipeline Diagram

```plaintext
Client → Kestrel → Middleware 1 → Middleware 2 → Routing → Controller → Middleware 3 → Response
```

### 2. Hosting Model

* **Kestrel Web Server (Built-in)**

  * High-performance, cross-platform web server.
  * Can run as a standalone server or behind a reverse proxy (e.g., IIS, Nginx).

* **In-Process vs Out-of-Process Hosting (Detailed)**

  * **In-Process:** Runs directly inside IIS worker process (w3wp.exe).
  * **Out-of-Process:** Kestrel runs independently, with IIS as a reverse proxy.

### 3. Dependency Injection (DI) System

* **Built-in DI Container**

  * Supports Transient, Scoped, and Singleton lifetimes.

* **How DI Works Internally? (Advanced)**

  * Services are registered in the DI container.
  * DI resolves services using Constructor Injection.
  * The lifetime of each service is determined by its registration type (Transient, Scoped, Singleton).

### 4. Middleware Architecture

* Middleware are components that intercept HTTP requests.
* **Order Matters:** The order in which middleware is registered determines the flow.
* Example:

  ```csharp
  app.UseRouting();
  app.UseAuthentication();
  app.UseAuthorization();
  app.UseEndpoints(endpoints => endpoints.MapControllers());
  ```

### 5. Configuration System (In-Depth)

* **Multi-Source Configuration:** Supports JSON, XML, Environment Variables, Command Line, Azure Key Vault.
* **Configuration Providers:** Hierarchical key-value system (appsettings.json, appsettings.Development.json).
* **Accessing Configuration Values:**

  ```csharp
  var configValue = builder.Configuration["MySetting:SubSetting"];
  ```

### 6. Hosting and Startup

* **Program.cs and Startup.cs (ASP.NET Core 3.1 and below)**

  * Program.cs: Configures WebHost.
  * Startup.cs: Configures Services and Middleware.

* **Unified Hosting Model (ASP.NET Core 6 and above)**

  * Single Program.cs with WebApplicationBuilder.

  ```csharp
  var builder = WebApplication.CreateBuilder(args);
  var app = builder.Build();
  app.Run();
  ```

### 7. Logging System (Detailed)

* **Integrated Logging Providers:** Console, Debug, EventSource, Application Insights.
* **Structured Logging with Serilog:**

  ```csharp
  builder.Logging.ClearProviders();
  builder.Logging.AddSerilog(new LoggerConfiguration().WriteTo.Console().CreateLogger());
  ```
* **Log Levels:** Trace, Debug, Information, Warning, Error, Critical.

### 8. Exception Handling

* **Global Exception Handling Middleware:**

  ```csharp
  app.UseExceptionHandler(errorApp =>
  {
      errorApp.Run(async context =>
      {
          context.Response.ContentType = "application/json";
          await context.Response.WriteAsync("{"Error":"An unexpected error occurred"}");
      });
  });
  ```

## Advanced Internals

* **Application Lifecycle:** How ASP.NET Core initializes and handles requests.
* **Threading and Async Programming:** Handling asynchronous requests efficiently.
* **Performance Optimization:** Response Caching, Compression, Connection Pooling.
* **Security Mechanisms:** Authentication, Authorization, CORS, Data Protection.
* **Advanced Configuration:** Environment-Specific Configuration, Secret Management, Azure Key Vault.
* **WebHostBuilder and GenericHostBuilder:** Understanding the hosting model.

## Watchouts

* Misconfiguring the middleware order can break the application.
* Be cautious with Singleton services that rely on Scoped services.
* Avoid tight coupling in DI (prefer interface-based injections).
* Always test configurations in production-like environments.

## Summary

### Question and Answer Mastery

1. **What is the ASP.NET Core request processing pipeline?**

   * It is a series of middleware components that handle HTTP requests and responses in a specific order.

2. **What is Kestrel, and how does it differ from IIS?**

   * Kestrel is a cross-platform web server for ASP.NET Core, while IIS is a Windows-only web server that can proxy requests to Kestrel.

3. **How does Dependency Injection (DI) work internally?**

   * DI is managed by a built-in container that resolves services based on their registration (Transient, Scoped, Singleton).

4. **What are the different DI lifetimes?**

   * Transient (per request), Scoped (per HTTP request), Singleton (one instance for the app).

5. **What is the difference between In-Process and Out-of-Process Hosting?**

   * In-Process runs directly in IIS, while Out-of-Process uses Kestrel with IIS as a reverse proxy.

6. **What is the role of Program.cs and Startup.cs?**

   * Program.cs configures the host, Startup.cs configures services and middleware (pre-ASP.NET Core 6).

7. **How do you set up global exception handling?**

   * Using `app.UseExceptionHandler` with a custom handler in `Program.cs`.

8. **What is the purpose of the Configuration System?**

   * To provide hierarchical, multi-source configuration for the application.

9. **How does the Logging System work?**

   * Integrated with multiple providers (Console, Serilog, Application Insights), supports structured logging.

10. **What are best practices for Middleware configuration?**

* Use correct order, avoid long-running tasks, and secure sensitive endpoints.

# Mastering Configuration and Logging in ASP.NET Core

## Introduction

Configuration and Logging are two critical aspects of any ASP.NET Core application. They ensure that applications can be easily configured for different environments and that errors can be diagnosed efficiently.

## Configuration in ASP.NET Core

### 1. What is Configuration?

* Configuration is how application settings are defined, accessed, and managed.
* ASP.NET Core supports hierarchical configuration using key-value pairs.
* It allows for flexibility across different environments (Development, Staging, Production).

### 2. Configuration Sources (Comprehensive)

* **JSON Files:** appsettings.json, appsettings.Development.json.
* **Environment Variables:** OS-level configuration values.
* **Command-Line Arguments:** Configuration values passed during app startup.
* **User Secrets:** Secure storage for sensitive values (Development only).
* **Azure Key Vault:** Securely store and manage application secrets in Azure.
* **In-Memory Collection:** Useful for testing configurations.
* **INI Files and XML Files:** Alternative configuration formats.

### 3. Configuring Application Settings

* Example: appsettings.json

```json
{
  "AppSettings": {
    "SiteTitle": "My ASP.NET Core App",
    "MaxUserCount": 100,
    "ConnectionStrings": {
      "DefaultConnection": "Server=myServer;Database=myDB;User Id=myUser;Password=myPass;"
    }
  }
}
```

* Accessing Configuration Values

```csharp
var builder = WebApplication.CreateBuilder(args);
var siteTitle = builder.Configuration["AppSettings:SiteTitle"];
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");
Console.WriteLine($"Site Title: {siteTitle}");
```

### 4. Environment-Specific Configuration

* Supports separate configurations for different environments (Development, Staging, Production).
* Automatically loads the correct appsettings file based on environment.
* Example: appsettings.Development.json

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Debug",
      "Microsoft": "Information"
    }
  }
}
```

### 5. Secret Management

* User Secrets for local development (secure sensitive information).

  ```bash
  dotnet user-secrets init
  dotnet user-secrets set "AppSettings:ApiKey" "my-secret-key"
  ```
* Azure Key Vault for production (secure secrets storage).

  * Securely access secrets without hardcoding them.

### 6. Strongly Typed Configuration (Advanced)

* Bind configuration values directly to a class.

```csharp
builder.Services.Configure<AppSettings>(builder.Configuration.GetSection("AppSettings"));

public class AppSettings
{
    public string SiteTitle { get; set; }
    public int MaxUserCount { get; set; }
}
```

* Accessing Strongly Typed Configuration

```csharp
public class HomeController : Controller
{
    private readonly AppSettings _appSettings;

    public HomeController(IOptions<AppSettings> options)
    {
        _appSettings = options.Value;
    }

    public IActionResult Index()
    {
        ViewData["Title"] = _appSettings.SiteTitle;
        return View();
    }
}
```

## Logging in ASP.NET Core

### 1. What is Logging?

* Logging is the process of recording information about the application’s execution.
* Helps with debugging, monitoring, and auditing.

### 2. Built-in Logging Providers

* Console
* Debug
* EventSource
* Application Insights (Azure)
* File Logging (using Serilog)

### 3. Configuring Logging (Detailed)

* Example Configuration in appsettings.json

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning"
    }
  }
}
```

### 4. Customizing Logging

* Use ILogger<T> for type-based logging.

```csharp
public class HomeController : Controller
{
    private readonly ILogger<HomeController> _logger;

    public HomeController(ILogger<HomeController> logger)
    {
        _logger = logger;
    }

    public IActionResult Index()
    {
        _logger.LogInformation("Home page accessed.");
        return View();
    }
}
```

### 5. Structured Logging with Serilog (Advanced)

* Serilog is a popular logging library for ASP.NET Core.
* Supports structured logging (JSON format).

```csharp
using Serilog;

builder.Logging.ClearProviders();
builder.Logging.AddSerilog(new LoggerConfiguration()
    .WriteTo.Console()
    .WriteTo.File("logs/log.txt", rollingInterval: RollingInterval.Day)
    .CreateLogger());
```

### 6. Log Levels Explained (Advanced)

* Trace: Most detailed logs.
* Debug: Development-level logs.
* Information: General information.
* Warning: Unexpected situations, but not errors.
* Error: Error conditions.
* Critical: Severe errors that cause termination.

## Watchouts

* Avoid logging sensitive information (e.g., passwords, API keys).
* Set appropriate log levels in production (Warning or higher).
* Use structured logging for better log analysis (JSON format).
* Manage log file sizes with rolling file logging.

## Summary

### Question and Answer Mastery

1. **What is Configuration in ASP.NET Core?**

   * It is how application settings are managed and accessed from various sources.

2. **What are the common Configuration Sources?**

   * JSON Files, Environment Variables, Command-Line, User Secrets, Azure Key Vault.

3. **How do you access configuration values in code?**

   * Using `builder.Configuration["Key"]` or `GetSection()`.

4. **What is Environment-Specific Configuration?**

   * Different settings for Development, Staging, Production environments.

5. **How do you securely store secrets in ASP.NET Core?**

   * Using User Secrets for development and Azure Key Vault for production.

6. **What is Logging, and why is it important?**

   * Logging records application events for debugging, monitoring, and auditing.

7. **What are the built-in Logging Providers?**

   * Console, Debug, EventSource, Application Insights, Serilog (custom).

8. **How do you configure Logging Levels?**

   * In appsettings.json or programmatically (Debug, Information, Error).

9. **What is Structured Logging, and why is it useful?**

   * It provides logs in JSON format, making them easy to parse and analyze.

10. **How do you prevent logging sensitive information?**

* Avoid logging credentials, use logging filters, and secure secrets in Azure Key Vault.

# Mastering Security and Identity in ASP.NET Core

## Introduction

Security and Identity are fundamental to building secure and scalable ASP.NET Core applications. This guide covers authentication, authorization, identity management, JWT, OAuth 2.0, OpenID Connect, and best practices for secure API development.

## Core Concepts

### 1. Authentication vs Authorization

* **Authentication:** Verifies the identity of a user.

  * Examples: Login with username and password, OAuth login with Google.
* **Authorization:** Determines what authenticated users can access.

  * Examples: Admin access, User read-only access.

### 2. Authentication Mechanisms (Detailed)

* **Cookie Authentication:** Uses cookies to track user sessions (stateful).
* **JWT Authentication (JSON Web Tokens):** Secure, stateless authentication for APIs.
* **OAuth 2.0 and OpenID Connect:** Secure authentication using external providers (Google, Facebook).

### 3. ASP.NET Core Identity (Comprehensive)

* **What is Identity?**

  * A complete user management system for ASP.NET Core.
  * Supports user registration, login, password management, two-factor authentication, email confirmation.

* **Configuring Identity in ASP.NET Core**

```csharp
builder.Services.AddIdentity<IdentityUser, IdentityRole>(options =>
{
    options.Password.RequireDigit = true;
    options.Password.RequiredLength = 8;
    options.SignIn.RequireConfirmedEmail = true;
})
.AddEntityFrameworkStores<ApplicationDbContext>()
.AddDefaultTokenProviders();
```

### 4. Secure Password Storage

* Passwords are hashed using secure hashing algorithms (PBKDF2, BCrypt).
* Example: Configuring password strength in Identity

```csharp
builder.Services.Configure<IdentityOptions>(options =>
{
    options.Password.RequireDigit = true;
    options.Password.RequiredLength = 8;
    options.Password.RequireUppercase = true;
    options.Password.RequireNonAlphanumeric = true;
});
```

### 5. Role-Based Authorization (Granular)

* Roles are assigned to users to control access.
* Example: Admin Role

```csharp
[Authorize(Roles = "Admin")]
public class AdminController : Controller
{
    public IActionResult Dashboard()
    {
        return View();
    }
}
```

* Dynamically Adding Roles

```csharp
var roleManager = app.Services.GetRequiredService<RoleManager<IdentityRole>>();
await roleManager.CreateAsync(new IdentityRole("Admin"));
```

### 6. Policy-Based Authorization (Advanced)

* Fine-grained control over authorization.
* Example: Creating a custom policy

```csharp
builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("RequireAdmin", policy => policy.RequireRole("Admin"));
    options.AddPolicy("AgeRequirement", policy => policy.RequireClaim("Age", "18"));
});
```

* Applying Policy in Controller

```csharp
[Authorize(Policy = "RequireAdmin")]
public class SecureController : Controller
{
    public IActionResult SecureArea()
    {
        return View();
    }
}
```

### 7. JWT Authentication (JSON Web Tokens) (Detailed)

* Secure, stateless authentication using JWT.
* Configuring JWT in Startup

```csharp
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
.AddJwtBearer(options =>
{
    options.TokenValidationParameters = new TokenValidationParameters
    {
        ValidateIssuer = true,
        ValidateAudience = true,
        ValidateLifetime = true,
        ValidIssuer = "https://yourdomain.com",
        ValidAudience = "https://yourdomain.com",
        IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes("YourSecretKey"))
    };
});
```

* Generating JWT Token

```csharp
public string GenerateJwtToken(string username)
{
    var claims = new[]
    {
        new Claim(JwtRegisteredClaimNames.Sub, username),
        new Claim(JwtRegisteredClaimNames.Jti, Guid.NewGuid().ToString())
    };

    var key = new SymmetricSecurityKey(Encoding.UTF8.GetBytes("YourSecretKey"));
    var creds = new SigningCredentials(key, SecurityAlgorithms.HmacSha256);

    var token = new JwtSecurityToken(
        issuer: "https://yourdomain.com",
        audience: "https://yourdomain.com",
        claims: claims,
        expires: DateTime.Now.AddHours(1),
        signingCredentials: creds
    );

    return new JwtSecurityTokenHandler().WriteToken(token);
}
```

### 8. Advanced Security Techniques

* Custom Claims and Policies.
* Two-Factor Authentication (2FA) with Email or SMS.
* Secure Cookies with `HttpOnly`, `Secure`, `SameSite=Strict`.
* Rate Limiting to prevent API abuse.
* Secure Headers (HSTS, Content Security Policy).
* Enforcing HTTPS with `app.UseHttpsRedirection()`.

## Watchouts

* Avoid weak password policies.
* Do not store user passwords in plain text.
* Always use HTTPS in production.
* Secure API keys in Azure Key Vault.
* Monitor authentication logs for suspicious activity.

## Summary

### Question and Answer Mastery

1. **What is the difference between Authentication and Authorization?**

   * Authentication verifies identity, Authorization determines access.

2. **How does ASP.NET Core Identity manage users?**

   * Through user registration, login, password management, roles, and claims.

3. **How do you configure password strength in Identity?**

   * Using `IdentityOptions.Password` configuration.

4. **What is JWT, and why is it used for authentication?**

   * JSON Web Token is a secure, stateless authentication mechanism.

5. **How do you enforce HTTPS in an ASP.NET Core application?**

   * Using `app.UseHttpsRedirection()`.

6. **What are Roles, and how do they work in Authorization?**

   * Roles are used to group users with similar permissions.

7. **What is Policy-Based Authorization?**

   * Fine-grained control of user access based on custom policies.

8. **How do you secure APIs using JWT?**

   * Using JWT Bearer Authentication with token validation.

9. **What are Secure Cookies, and how do you configure them?**

   * Cookies with `HttpOnly`, `Secure`, `SameSite` attributes.

10. **What are best practices for secure password storage?**

* Use hashed passwords, secure hashing algorithms (PBKDF2, BCrypt).


# Mastering OWASP and Its Implementations in ASP.NET Core

## Introduction

OWASP (Open Web Application Security Project) is an organization that provides best practices and guidelines for securing web applications. This guide will cover the OWASP Top 10 vulnerabilities, how they apply to ASP.NET Core applications, and how to mitigate them with full code examples and best practices.

## OWASP Top 10 Vulnerabilities (Detailed)

### 1. Injection (SQL Injection, Command Injection)

* **What is Injection?**

  * Injection attacks occur when untrusted data is inserted into a command or query.
  * Common Types: SQL Injection, Command Injection, LDAP Injection.

* **How to Prevent Injection in ASP.NET Core**

  * Use Parameterized Queries with Entity Framework (EF Core)

  ```csharp
  var user = await dbContext.Users.FirstOrDefaultAsync(u => u.Username == username);
  ```

  * Use Stored Procedures for database operations.
  * Avoid dynamic SQL queries.

* **Example of a Secure SQL Query:**

  ```csharp
  var query = "SELECT * FROM Users WHERE Username = @username";
  using var command = new SqlCommand(query, connection);
  command.Parameters.AddWithValue("@username", username);
  var reader = await command.ExecuteReaderAsync();
  ```

### 2. Broken Authentication

* **What is Broken Authentication?**

  * Authentication mechanisms are improperly implemented, allowing unauthorized access.

* **How to Prevent Broken Authentication**

  * Enforce strong password policies in ASP.NET Core Identity.

  ```csharp
  builder.Services.Configure<IdentityOptions>(options =>
  {
      options.Password.RequireDigit = true;
      options.Password.RequiredLength = 8;
      options.SignIn.RequireConfirmedEmail = true;
  });
  ```

  * Use HTTPS for secure transmission.
  * Implement Two-Factor Authentication (2FA).

### 3. Sensitive Data Exposure

* **What is Sensitive Data Exposure?**

  * Sensitive data is not properly protected (e.g., passwords, API keys).

* **How to Protect Sensitive Data**

  * Enforce HTTPS with HSTS (HTTP Strict Transport Security).

  ```csharp
  app.UseHsts();
  app.UseHttpsRedirection();
  ```

  * Use Azure Key Vault for secure secret management.
  * Encrypt sensitive data using Data Protection API.

### 4. XML External Entities (XXE)

* **What is XXE?**

  * An attack where malicious XML can access external resources.

* **How to Prevent XXE in ASP.NET Core**

  * Disable DTD processing in XML parsers.

  ```csharp
  var xmlReaderSettings = new XmlReaderSettings
  {
      DtdProcessing = DtdProcessing.Prohibit
  };
  ``
  ```

### 5. Broken Access Control

* **What is Broken Access Control?**

  * Users can access unauthorized resources.

* **How to Prevent Broken Access Control**

  * Use Role-Based Authorization.

  ```csharp
  [Authorize(Roles = "Admin")]
  ```

  * Implement Policy-Based Authorization for fine-grained control.

### 6. Security Misconfiguration

* **What is Security Misconfiguration?**

  * Application is not securely configured (e.g., debugging enabled in production).

* **How to Prevent Security Misconfiguration**

  * Use environment-specific configuration (appsettings.Production.json).
  * Ensure HTTPS is enabled in production.
  * Disable stack traces in production.

### 7. Cross-Site Scripting (XSS)

* **What is XSS?**

  * Malicious scripts are injected into a trusted website.

* **How to Prevent XSS in ASP.NET Core**

  * Use Razor Encoding by default.

  ```html
  <p>@Html.Encode(Model.UserInput)</p>
  ```

  * Implement Content Security Policy (CSP).

  ```csharp
  app.UseCsp(options => options
      .ScriptSources(s => s.Self())
      .StyleSources(s => s.Self()));
  ```

### 8. Insecure Deserialization

* **What is Insecure Deserialization?**

  * Deserialization of untrusted data, leading to remote code execution.

* **How to Prevent Insecure Deserialization**

  * Avoid deserializing untrusted data.
  * Use known object types for JSON deserialization.

  ```csharp
  var user = JsonConvert.DeserializeObject<User>(jsonInput);
  ```

### 9. Using Components with Known Vulnerabilities

* **What is the Risk?**

  * Using outdated NuGet packages or libraries with known security flaws.

* **How to Secure Components**

  * Regularly update NuGet packages.
  * Use `dotnet list package --outdated` to identify outdated packages.

### 10. Insufficient Logging and Monitoring

* **What is the Risk?**

  * Failure to detect security breaches due to poor logging.

* **How to Enhance Logging and Monitoring**

  * Use ILogger for structured logging.

  ```csharp
  _logger.LogInformation("User Login Attempted");
  ```

  * Use Serilog for centralized, structured logging.

## Advanced Security Practices

* Implementing Rate Limiting with ASP.NET Core.
* Using Secure Cookies with HttpOnly, Secure, and SameSite attributes.
* Securing APIs with API Keys and OAuth2.
* Using Content Security Policy (CSP) for XSS protection.
* Automating Security Scans (e.g., OWASP ZAP).

## Watchouts

* Avoid exposing sensitive data in configuration files.
* Ensure HTTPS is enabled in production.
* Regularly update NuGet packages to avoid vulnerabilities.
* Avoid storing passwords in plain text.
* Monitor authentication logs for suspicious activity.

## Summary

### Question and Answer Mastery

1. **What is OWASP?**

   * The Open Web Application Security Project, a non-profit that provides security best practices.

2. **What are the OWASP Top 10 vulnerabilities?**

   * Injection, Broken Authentication, Sensitive Data Exposure, XXE, Broken Access Control, Security Misconfiguration, XSS, Insecure Deserialization, Using Components with Known Vulnerabilities, Insufficient Logging and Monitoring.

3. **How do you prevent SQL Injection in ASP.NET Core?**

   * Use Parameterized Queries or Stored Procedures.

4. **How do you enforce strong password policies?**

   * Use ASP.NET Core Identity with configured password options.

5. **What is HSTS, and why is it important?**

   * HTTP Strict Transport Security, enforces HTTPS connections.

6. **How do you prevent Cross-Site Scripting (XSS) in ASP.NET Core?**

   * Use Razor Encoding, Content Security Policy (CSP).

7. **What is Policy-Based Authorization?**

   * Fine-grained control of user access with custom policies.

8. **How do you secure APIs using JWT?**

   * Use JWT Bearer Authentication with secure token validation.

9. **What is XXE, and how do you prevent it?**

   * XML External Entities, prevent by disabling DTD processing.

10. **How do you implement secure logging and monitoring?**

* Use structured logging with ILogger or Serilog, and monitor logs for suspicious activities.
# Mastering OWASP and Its Implementations in ASP.NET Core

## Introduction

OWASP (Open Web Application Security Project) is an organization that provides best practices and guidelines for securing web applications. This guide will cover the OWASP Top 20 vulnerabilities (including the next 10 beyond the traditional top 10), how they apply to ASP.NET Core applications, and how to mitigate them with full code examples and best practices.

## OWASP Next 10 Vulnerabilities (Advanced)

### 11. Cross-Site Request Forgery (CSRF)

* **What is CSRF?**

  * An attack where a malicious website tricks a user into performing an action on another site where they are authenticated.

* **How to Prevent CSRF in ASP.NET Core**

  * Use Anti-Forgery Tokens (`@Html.AntiForgeryToken()` in forms).

  ```csharp
  [ValidateAntiForgeryToken]
  public IActionResult SubmitForm()
  {
      // Form Submission
  }
  ```

  * Enable CSRF Protection Globally

  ```csharp
  app.UseAntiforgery();
  ```

### 12. Security Misconfiguration (Advanced)

* **What is Advanced Security Misconfiguration?**

  * Misconfigured HTTP Headers (e.g., Content Security Policy, Strict-Transport-Security).

* **How to Secure Configuration:**

  * Enforce HTTPS and HSTS

  ```csharp
  app.UseHsts();
  app.UseHttpsRedirection();
  ```

  * Use Secure Headers Middleware (NWebSec).

### 13. Insecure Object References

* **What is Insecure Object References?**

  * Direct access to objects without authorization checks (e.g., /users/1/edit).

* **How to Prevent:**

  * Use GUIDs instead of sequential IDs for sensitive objects.
  * Implement Role-Based and Policy-Based Authorization.

### 14. HTTP Parameter Pollution

* **What is HTTP Parameter Pollution?**

  * Multiple values for a single parameter can lead to unexpected behavior.

* **How to Prevent:**

  * Use model binding with strong types in ASP.NET Core.

  ```csharp
  public IActionResult Search(string query)
  {
      if (string.IsNullOrEmpty(query))
      {
          return BadRequest("Query cannot be empty.");
      }
  }
  ```

### 15. Server-Side Request Forgery (SSRF)

* **What is SSRF?**

  * An attack where the server makes HTTP requests to an internal system at an attacker’s request.

* **How to Prevent SSRF:**

  * Restrict outgoing HTTP requests to trusted domains.
  * Use HttpClientFactory with strict configurations.

### 16. Remote Code Execution (RCE)

* **What is RCE?**

  * Allows an attacker to run arbitrary code on the server.

* **How to Prevent:**

  * Do not execute untrusted code (e.g., Shell commands).
  * Avoid deserializing untrusted data.

### 17. Mass Assignment

* **What is Mass Assignment?**

  * When properties of a model can be set by user input without restriction.

* **How to Prevent:**

  * Use ViewModels or DTOs instead of directly binding user input to models.

  ```csharp
  public class UserDto
  {
      public string Username { get; set; }
      public string Email { get; set; }
  }
  ```

### 18. Cross-Origin Resource Sharing (CORS) Misconfiguration

* **What is CORS Misconfiguration?**

  * Incorrectly allowing all origins to access APIs.

* **How to Secure CORS:**

  ```csharp
  builder.Services.AddCors(options =>
  {
      options.AddPolicy("SecurePolicy",
          builder => builder.WithOrigins("https://trusted-domain.com")
                            .AllowAnyMethod()
                            .AllowAnyHeader());
  });

  app.UseCors("SecurePolicy");
  ```

### 19. Cache Poisoning

* **What is Cache Poisoning?**

  * Manipulating cached responses to deliver malicious content to users.

* **How to Prevent:**

  * Use secure cache headers.

  ```csharp
  app.Use(async (context, next) =>
  {
      context.Response.Headers["Cache-Control"] = "no-store";
      await next.Invoke();
  });
  ```

### 20. Insecure HTTP Methods

* **What is the Risk?**

  * Allowing unsafe HTTP methods (e.g., TRACE, DELETE).

* **How to Secure HTTP Methods:**

  ```csharp
  app.UseEndpoints(endpoints =>
  {
      endpoints.MapControllers().WithMetadata(new HttpMethodMetadata(new[] { "GET", "POST" }));
  });
  ```

## Advanced Security Practices

* Implementing Rate Limiting with ASP.NET Core.
* Using Secure Cookies with HttpOnly, Secure, and SameSite attributes.
* Securing APIs with API Keys and OAuth2.
* Using Content Security Policy (CSP) for XSS protection.
* Automating Security Scans (e.g., OWASP ZAP).

## Summary

### Question and Answer Mastery

1. **What is Cross-Site Request Forgery (CSRF)?**

   * CSRF is an attack where a malicious website tricks a user into performing an action on another site where they are authenticated.

2. **How do you prevent CSRF in ASP.NET Core?**

   * Use Anti-Forgery Tokens with `@Html.AntiForgeryToken()` and `[ValidateAntiForgeryToken]`.

3. **What is SSRF, and how do you prevent it?**

   * SSRF (Server-Side Request Forgery) tricks a server into making requests to unintended destinations. Prevent it by restricting outgoing HTTP requests.

4. **How do you prevent Insecure Object References?**

   * Use GUIDs instead of sequential IDs, and implement Role-Based Authorization.

5. **What is Remote Code Execution (RCE), and how do you avoid it?**

   * RCE allows an attacker to run arbitrary code on the server. Avoid it by not executing untrusted code or deserializing untrusted data.

6. **What is CORS Misconfiguration, and how do you secure it?**

   * Incorrectly allowing all origins to access APIs. Secure by restricting origins using `builder.Services.AddCors`.

7. **How do you prevent Cache Poisoning?**

   * Use secure cache headers (`Cache-Control: no-store`).

8. **What is Mass Assignment, and how do you prevent it?**

   * Automatically binding user input to model properties. Prevent with DTOs or ViewModels.

9. **What is HTTP Parameter Pollution, and how do you secure it?**

   * Multiple values for a single parameter causing unexpected behavior. Use strong model binding.

10. **What are the best practices for securing HTTP methods?**

* Restrict allowed HTTP methods using `MapControllers()` with specified methods (GET, POST).

