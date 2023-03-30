# Clean Flutter Manifest (CFM)
A opined proposal of clean architecture for Flutter applications.

## The CFM Proposal
This project is organized using Clean Architecture principles to promote separation of concerns, independence between layers, and testability. The codebase is divided into three main layers:

- **Externals:** This layer contains infrastructure code that interacts with external systems such as databases, web services, and other external services. It defines contracts (interfaces or abstract classes) that specify how the external systems should be interacted with, and then provides implementations for those contracts.

- **Adapters:** This layer contains code that adapts the domain objects and use cases to the infrastructure code provided by the external layer. It contains controllers, models, providers, services, and sources.

- **Internals:** This layer contains domain-specific code that defines entities, use cases, and business logic. It includes entities, failures, services, and use cases
 
 
 ## Exlamples
 
- [authentication app using Clean Flutter Manifest](https://github.com/HenriqueNas/clean_arch_flutter_auth)
