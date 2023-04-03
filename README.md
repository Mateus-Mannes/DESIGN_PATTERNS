# STRATEGY

The Strategy Design Pattern is a behavioral design pattern that allows you to define a family of algorithms, encapsulate each one, and make them interchangeable. This pattern enables the algorithms to vary independently from the clients that use them, promoting loose coupling and flexibility in code.

```mermaid
classDiagram
    class Context {
        +setStrategy(Strategy)
        +executeStrategy()
    }
    class Strategy {
        +execute()
    }
    class ConcreteStrategyA {
        +execute()
    }
    class ConcreteStrategyB {
        +execute()
    }
    Context "1" *-- "1" Strategy
    Strategy <|-- ConcreteStrategyA
    Strategy <|-- ConcreteStrategyB

```

# CHAIN OF RESPONSABILITY

The Chain of Responsibility Design Pattern is a behavioral design pattern that allows you to decouple the sender of a request from its receivers by giving multiple objects a chance to handle the request. The pattern establishes a chain of objects (handlers) that can process the request. The request is passed along the chain until one of the handlers processes it, or the end of the chain is reached.

``` mermaid
classDiagram
    class Client
    class Handler {
        +Handler Next
        +handleRequest(Request)
    }
    class ConcreteHandlerA {
        +handleRequest(Request)
    }
    class ConcreteHandlerB {
        +handleRequest(Request)
    }
    Client --> Handler
    Handler <|-- ConcreteHandlerA
    Handler <|-- ConcreteHandlerB
```

# TEMPLATE METHOD

The Template Method Design Pattern is a behavioral design pattern that defines the skeleton of an algorithm in an operation, deferring some steps to subclasses. The pattern allows subclasses to redefine certain steps of an algorithm without changing the overall structure and sequence of the algorithm.


```mermaid
classDiagram
    class Client
    class AbstractClass {
        +templateMethod()
        +primitiveOperation1()
        +primitiveOperation2()
    }
    class ConcreteClassA {
        +primitiveOperation1()
        +primitiveOperation2()
    }
    class ConcreteClassB {
        +primitiveOperation1()
        +primitiveOperation2()
    }
    Client --> AbstractClass
    AbstractClass <|-- ConcreteClassA
    AbstractClass <|-- ConcreteClassB

```

# DECORATOR

The Decorator Design Pattern is a structural design pattern that allows you to add new functionality to an existing object without altering its structure. This pattern involves a set of decorator classes that are used to wrap concrete components. Decorator classes mirror the type of the components they are decorating but add or override behavior.

```mermaid

classDiagram
    class Client
    class Component {
        +operation()
    }
    class ConcreteComponent {
        +operation()
    }
    class Decorator {
        -component: Component
        +operation()
    }
    class ConcreteDecoratorA {
        +operation()
        +addedBehavior()
    }
    class ConcreteDecoratorB {
        +operation()
    }
    Client --> Component
    Component <|-- ConcreteComponent
    Component <|-- Decorator
    Decorator o-- Component
    Decorator <|-- ConcreteDecoratorA
    Decorator <|-- ConcreteDecoratorB


```

# STATE

The State Design Pattern is a behavioral design pattern that allows an object to change its behavior when its internal state changes. The pattern encapsulates state-specific behavior into separate classes and delegates the state-related tasks to the corresponding objects.

```mermaid
classDiagram
    class Client
    class Context {
        +request()
        +changeState(State)
        -state: State
    }
    class State {
        +handle(Context)
    }
    class ConcreteStateA {
        +handle(Context)
    }
    class ConcreteStateB {
        +handle(Context)
    }
    Client --> Context
    Context o-- State
    State <|-- ConcreteStateA
    State <|-- ConcreteStateB

```


# BUILDER

The Builder Design Pattern is a creational design pattern that separates the construction of a complex object from its representation. It allows the same construction process to create different representations of the object. This pattern is particularly useful when you need to create complex objects with many parts or configurations.

```mermaid
classDiagram
    class Client
    class Director {
        +construct()
        +setBuilder(Builder)
    }
    class Builder {
        +buildPartA()
        +buildPartB()
        +getResult(): Product
    }
    class ConcreteBuilderA {
        +buildPartA()
        +buildPartB()
        +getResult(): Product
    }
    class ConcreteBuilderB {
        +buildPartA()
        +buildPartB()
        +getResult(): Product
    }
    class Product {
        -partA: String
        -partB: String
    }
    Client --> Director
    Director --> Builder
    Builder <|-- ConcreteBuilderA
    Builder <|-- ConcreteBuilderB

```

# OBSERVER

The Observer Design Pattern is a behavioral design pattern that defines a one-to-many dependency between objects so that when one object (the Subject) changes its state, all its dependents (the Observers) are notified and updated automatically. This pattern promotes loose coupling between the Subject and the Observers.

```mermaid
classDiagram
    class Client
    class Subject {
        +attach(Observer)
        +detach(Observer)
        +notify()
    }
    class ConcreteSubject {
        +getState(): State
        +setState(State)
        -state: State
    }
    class Observer {
        +update()
    }
    class ConcreteObserverA {
        +update()
        -subject: ConcreteSubject
    }
    class ConcreteObserverB {
        +update()
        -subject: ConcreteSubject
    }
    Client --> Subject
    Client --> Observer
    Subject <|-- ConcreteSubject
    Observer <|-- ConcreteObserverA
    Observer <|-- ConcreteObserverB
    ConcreteSubject "1" o-- "*" Observer: observers
```

# FACTORY METHOD

The Factory Method Design Pattern is a creational design pattern that provides an interface (or abstract class) for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. This pattern promotes loose coupling between the creator and the concrete products.

```mermaid
classDiagram
    class Client
    class Creator {
        +factoryMethod(): Product
    }
    class ConcreteCreatorA {
        +factoryMethod(): Product
    }
    class ConcreteCreatorB {
        +factoryMethod(): Product
    }
    class Product {
        +operation()
    }
    class ConcreteProductA {
        +operation()
    }
    class ConcreteProductB {
        +operation()
    }
    Client --> Creator
    Creator <|-- ConcreteCreatorA
    Creator <|-- ConcreteCreatorB
    Creator ..> Product
    Product <|-- ConcreteProductA
    Product <|-- ConcreteProductB
```
