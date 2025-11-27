SOLID is an acronym representing a set of five fundamental principles of object-oriented programming and design. The goal of these principles is to create software that is more **understandable, flexible, and maintainable**

## simple explanation
Think of building with **Lego blocks**:

- **SRP:** Each Lego block has a single, clear purpose (a 2x4 brick, a wheel, a window).
    
- **OCP:** You can combine these blocks in endless new ways (extend) without having to melt down and re-mold existing blocks (modify).
    
- **LSP:** A 2x2 brick can fit anywhere a 2x2 space is designed. It's perfectly substitutable.
    
- **ISP:** You have specialized pieces for different jobs, rather than one giant "do-everything" piece that forces you to have parts you don't need.
    
- **DIP:** The design of your Lego castle (the high-level plan) doesn't depend on the specific color of the bricks (the low-level detail). You can swap red bricks for blue ones without changing the design.

### S - Single Responsibility Principle (SRP)
**"A class should have one, and only one, reason to change."**
A class should have only one job or responsibility. It should not be overwhelmed with multiple tasks.

- **Bad Example:** A `Book` class that handles its own data (title, author) **and** saves itself to a database **and** prints its own format to the console.
    
- **Good Example:**
    
    - `Book` class: Only holds data and business logic related to a book (title, author, getSummary()).
        
    - `BookRepository` class: Handles all database operations (save, delete, find).
        
    - `BookPrinter` class: Handles all formatting and printing of book details.

### O - Open/Closed Principle (OCP)
**"Software entities (classes, modules, functions) should be open for extension, but closed for modification."**
You should be able to add new functionality without changing existing, working code. You **extend** behavior, not modify it.

- **Bad Example:** A `AreaCalculator` class with a single method that uses a giant `if-else` or `switch` statement to check the type of shape (circle, square) to calculate its area. To add a triangle, you must **modify** this method.
    
- **Good Example:** Define a `Shape` interface with a method `calculateArea()`. Then, have `Circle`, `Square`, and later `Triangle` classes implement this interface. The `AreaCalculator` can now work with any `Shape` without knowing its concrete type. To add a new shape, you create a new class without touching the calculator.

### L - Liskov Substitution Principle (LSP)
**"Subtypes must be substitutable for their base types."**
If class `B` is a subclass of class `A`, then you should be able to pass an object of `B` to any program that expects an object of `A` without causing errors or unexpected behavior.

- **Bad Example:** A `Square` class inheriting from a `Rectangle` class. A `Rectangle` has independent `width` and `height`. A `Square` has equal sides. If you override the setters in `Square` to force width and height to be equal, a function that expects a `Rectangle` (e.g., one that doubles its width) will break when given a `Square`.
    
- **Good Example:** Both `Rectangle` and `Square` could implement a `Shape` interface or inherit from a more general `Quadrilateral` class that doesn't make assumptions about side equality.

###  I - Interface Segregation Principle (ISP)
**"Clients should not be forced to depend on interfaces they do not use."**
Instead of one large, "fat" interface, create multiple, smaller, and more specific interfaces.

- **Bad Example:** A monolithic `Worker` interface with methods `work()`, `eat()`, and `sleep()`. A `Robot` class implementing this would be forced to implement `eat()` and `sleep()`, which make no sense.
    
- **Good Example:**
    
    - `Workable` interface: `work()`
        
    - `Feedable` interface: `eat()`
        
    - A `Human` class can implement all three. A `Robot` class only needs to implement `Workable`.

### D - Dependency Inversion Principle (DIP)
**A. High-level modules should not depend on low-level modules. Both should depend on abstractions (e.g., interfaces).**  
**B. Abstractions should not depend on details. Details (concrete implementations) should depend on abstractions.**
This principle is about decoupling. High-level policy (business logic) should not be tightly coupled to low-level implementation details (like databases, APIs, or logging frameworks).

- **Bad Example:** A `ReportService` class directly creates an instance of a `MySQLDatabase` class to save data. If you want to switch to a `PostgreSQLDatabase`, you have to change the code inside `ReportService`.
    
- **Good Example:** The `ReportService` depends on a `Database` interface (abstraction). The `MySQLDatabase` and `PostgreSQLDatabase` classes are the details that implement this interface. The `ReportService` is _injected_ with a concrete (not abstract) implementation (e.g., via a constructor), a technique known as **Dependency Injection**.


### dependency injection
 **instead of an object creating its own dependencies, they are provided to it from the outside.**