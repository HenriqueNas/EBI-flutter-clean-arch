# Clean Flutter Manifest (CFM)
A opined proposal of clean architecture for Flutter applications.

## Clean Architecture Overview
Clean Architecture is a _software development pattern_ that helps to create scalable, testable and maintainable applications. It was introduced by Robert C. Martin (also known as Uncle Bob) in his book, "Clean Architecture: A Craftsman's Guide to Software Structure and Design".

The key idea of Clean Architecture is to separate the application into distinct layers, each with its own responsibilities and dependencies. This approach is sometimes called the "Onion Architecture" because the layers are arranged in concentric circles, with the core domain layer at the center and the external layers on the outer rings.

_There are three main principles of Clean Architecture:_

- **Separation of concerns:** Each layer has a single responsibility, and dependencies flow inward, from the outer layers to the core.

- **Dependency inversion:** The core layer should not depend on any external layer. Instead, the external layers should depend on the core layer, making it easier to replace or update external dependencies.

- **Testability:** Each layer can be tested independently, allowing developers to catch bugs and issues early in the development cycle.


## The CFM Proposal
This project is organized using Clean Architecture principles to promote separation of concerns, independence between layers, and testability. The codebase is divided into three main layers:

- **Externals:** This layer contains infrastructure code that interacts with external systems such as databases, web services, and other external services. It defines contracts (interfaces or abstract classes) that specify how the external systems should be interacted with, and then provides implementations for those contracts.

- **Adapters:** This layer contains code that adapts the domain objects and use cases to the infrastructure code provided by the external layer. It contains controllers, models, providers, services, and sources.

- **Internals:** This layer contains domain-specific code that defines entities, use cases, and business logic. It includes entities, failures, services, and use cases
 
 
 ## Exlamples
 
- [authentication app using CFM](https://github.com/HenriqueNas/clean_arch_flutter_auth)
