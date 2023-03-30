# Clean Flutter Manifest (CFM)
A opined proposal of clean architecture for Flutter applications.

## Table of Contents

- [Clean Architecture Overview](#clean-architecture-overview)
- [The CFM Proposal](#the-cfm-proposal)
- [File Structure](#file-structure)
- [Good Practices](#good-practices)
    - [Test-Driven Development (TDD)](#test-driven-development-tdd)
    - [Follow SOLID Principles](#follow-solid-principles)
    - [Clean Code](#clean-code)
- [Projects Examples Using CFM](#projects-examples-using-cfm)

# Clean Architecture Overview
Clean Architecture is a _software development pattern_ that helps to create scalable, testable and maintainable applications. It was introduced by Robert C. Martin (also known as Uncle Bob) in his book, "Clean Architecture: A Craftsman's Guide to Software Structure and Design".

The key idea of Clean Architecture is to separate the application into distinct layers, each with its own responsibilities and dependencies. This approach is sometimes called the "Onion Architecture" because the layers are arranged in concentric circles, with the core domain layer at the center and the external layers on the outer rings.

_There are three main principles of Clean Architecture:_

- **Separation of concerns:** Each layer has a single responsibility, and dependencies flow inward, from the outer layers to the core.

- **Dependency inversion:** The core layer should not depend on any external layer. Instead, the external layers should depend on the core layer, making it easier to replace or update external dependencies.

- **Testability:** Each layer can be tested independently, allowing developers to catch bugs and issues early in the development cycle.


# The CFM Proposal
This project is organized using Clean Architecture principles to promote separation of concerns, independence between layers, and testability. The codebase is divided into three main layers:

- **Externals:** This layer contains infrastructure code that interacts with external systems such as databases, web services, and other external services. It defines contracts (interfaces or abstract classes) that specify how the external systems should be interacted with, and then provides implementations for those contracts.

- **Adapters:** This layer contains code that adapts the domain objects and use cases to the infrastructure code provided by the external layer. It contains controllers, models, providers, services, and sources.

- **Internals:** This layer contains domain-specific code that defines entities, use cases, and business logic. It includes entities, failures, services, and use cases

# File Structure
Here are a sample of how can you structure your project with CFM

```
clean_flutter_manifest_sample
├─ lib
│  ├─ externals
│  │  ├─ database
│  │  │  ├─ SQL
│  │  │  └─ cache
│  │  ├─ drivers
│  │  ├─ presenter
│  │  │  ├─ pages
│  │  │  ├─ utils
│  │  │  └─ widgets
│  │  ├─ sources // sources contracts implementations
│  │  └─ web
│  │     ├─ http
│  │     │  ├─ client
│  │     │  └─ middleware
│  │     ├─ socket
│  │     │  ├─ client
│  │     └─ └─ middleware
│  ├─ adapters // do not contain Flutter imports
│  │  ├─ controllers
│  │  ├─ models // every model extends a entity
│  │  ├─ providers
│  │  ├─ services // services contracts implementations
│  │  └─ sources // just contracts
│  ├─ internals // do not contain Flutter imports
│  │  ├─ entities
│  │  ├─ failures
│  │  ├─ services  // just contracts
└─ └─ └─ usecases
```

# Good Practices

Here are some good practices to keep in mind when developing a project using Clean Architecture:

### Test-Driven Development (TDD)
Test-Driven Development is a software development process that emphasizes writing automated tests before writing the actual code. TDD helps to ensure that the code is well-designed, easy to maintain, and bug-free. By writing tests first, you can ensure that your code meets the requirements and passes all the acceptance criteria.

### Follow SOLID Principles
The SOLID principles are a set of guidelines that help to create clean, maintainable, and scalable code. They are:

- **Single Responsibility Principle (SRP):** A class should have only one reason to change.

- **Open/Closed Principle (OCP):** A class should be open for extension but closed for modification.

- **Liskov Substitution Principle (LSP):** Subtypes must be substitutable for their base types.

- **Interface Segregation Principle (ISP):** A class should not be forced to implement interfaces it does not use.

- **Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules. Both should depend on abstractions.

### Clean Code
Clean Code is a set of principles and guidelines that help to create code that is easy to read, understand, and maintain. It emphasizes readability, simplicity, and clarity.

By following these principles and guidelines, you can ensure that your code is well-designed, easy to maintain, and scalable. This will make it easier to add new features, fix bugs, and update dependencies over time.

 
# Projects Examples Using CFM
 
- [authentication app using CFM](https://github.com/HenriqueNas/clean_arch_flutter_auth)
