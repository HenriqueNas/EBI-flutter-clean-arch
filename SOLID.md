# SOLID with Clean Flutter Manifest (CFM)

SOLID is a set of design principles that aim to make software systems more maintainable, extensible, and robust. The five SOLID principles are:

**Single Responsibility Principle (SRP)**
**Open-Closed Principle (OCP)**
**Liskov Substitution Principle (LSP)**
**Interface Segregation Principle (ISP)**
**Dependency Inversion Principle (DIP)**

By following it we can create Flutter apps that are easier to test, refactor, and extend. 
SOLID also help to reduce code complexity, improve code reuse, and make our codebase more modular.

## Advanced Concepts of SOLID

SOLID principles are not only about following a set of rules but also about understanding the underlying concepts. Here are some advanced concepts of SOLID that can help you to apply SOLID principles effectively:

Cohesion and Coupling: Cohesion refers to how well the responsibilities of a module are related. High cohesion means that a module has a single responsibility and all its methods are related to that responsibility. Coupling refers to how dependent a module is on other modules. Low coupling means that a module depends only on abstractions and not on concrete implementations.

Dependency Injection (DI): DI is a technique that allows us to decouple the dependencies of a module from its implementation. By using DI, we can easily replace the implementation of a module with another implementation without changing the code that uses it.

Inversion of Control (IoC): IoC is a principle that states that the control of object creation and lifecycle should be delegated to a framework or a container. By using IoC, we can reduce the coupling between modules and make our code more modular and extensible.

SOLID Design Patterns: SOLID principles can be applied using various design patterns such as Factory Method, Abstract Factory, Builder, Decorator, Adapter, and Strategy. These patterns provide a common vocabulary and a set of best practices for applying SOLID principles.

## Example

Let's take an example of how we can apply SOLID principles with CFM in a Flutter app. Suppose we have a screen that displays a list of items. The screen has the following responsibilities:

Fetch the list of items from an API.
Parse the data into a list of domain objects.
Display the list of domain objects in a ListView widget.
To apply SOLID principles with CFM, we can create the following layers:

Presentation Layer: This layer contains the screen widget and is responsible for rendering the UI.

Domain Layer: This layer contains the domain objects and the business logic of the app.

Data Layer: This layer contains the implementation of the repositories and data sources.

To apply SRP, we can split the responsibilities of the screen into multiple classes:

ItemListScreen: This class is responsible for rendering the UI of the screen.

ItemListViewModel: This class is responsible for fetching the data from the repository, parsing the data into domain objects, and providing the list of domain objects to the screen.

ItemRepository: This class is responsible for fetching the data from the API and providing it to the ViewModel.

To apply OCP, we can use the Strategy pattern to decouple the implementation of the ItemRepository from the ViewModel. We can create an interface called ItemDataSource that defines the methods for fetching the data. Then we can create two implementations of this interface: ApiItemDataSource and CacheItemDataSource. The ItemRepository can useeither of these implementations based on the user's preference or availability of the data.

To apply LSP, we can make sure that the ApiItemDataSource and CacheItemDataSource implement the same methods defined in the ItemDataSource interface. This allows us to interchangeably use any implementation of the ItemDataSource interface without affecting the behavior of the application.

To apply ISP, we can create a separate interface for the parsing logic of the data. This allows us to use different parsing strategies without affecting the other responsibilities of the ItemListViewModel.

To apply DIP, we can use DI to inject the dependencies of the ItemListViewModel and ItemRepository. This makes it easy to replace the implementation of the dependencies without changing the code that uses them.

By applying SOLID principles with CFM, we can create a Flutter app that is easy to test, refactor, and extend. We can also reduce code complexity, improve code reuse, and make our codebase more modular.



