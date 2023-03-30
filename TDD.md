# Test-Driven Development (TDD) with Clean Flutter Manifest (CFM)

Test-Driven Development (TDD) is a software development process that emphasizes writing automated tests before writing the actual code. 
TDD helps to ensure that the code is well-designed, easy to maintain, and bug-free. 
By writing tests first, you can ensure that your code meets the requirements and passes all the acceptance criteria.

## Why TDD With CFM?

TDD can be applied to any software development project, including Flutter applications built using Clean Flutter Manifest (CFM). 
Here are some benefits of applying TDD with CFM:

1. **Improved code quality:** Using CFM's Clean Architecture principles and TDD can lead to a more modular, maintainable, and testable codebase. By separating concerns into distinct layers and writing tests first, you can ensure that each component of the application works as expected and is properly isolated from other components.

2. **Reduced coupling and dependencies:** CFM's Clean Architecture principles and TDD can help to reduce coupling and dependencies between different parts of the application. By defining clear boundaries between layers and using interfaces or abstract classes to define contracts, you can make it easier to swap out implementations or upgrade dependencies without affecting the rest of the codebase.

3. **Faster iteration and development:** TDD can help to speed up the development cycle by catching bugs and issues early, before they have a chance to cause larger problems down the line. CFM's Clean Architecture principles can also make it easier to iterate quickly on specific features or functionality without affecting other parts of the application.

4. **Improved collaboration:** Using CFM's Clean Architecture principles and TDD can make it easier for developers to collaborate and work on different parts of the codebase independently. By defining clear boundaries and interfaces between layers, multiple developers can work on different components of the application at the same time without worrying about conflicts or dependencies.

Overall, combining CFM's Clean Architecture principles with TDD can lead to a more maintainable, modular, and testable codebase that is easier to iterate on and collaborate on.

## Tutorial

Here are some guidelines for applying TDD with CFM:

### Step 1: Write a simple test

First, write a test for the login feature. The test should check if the user is able to login successfully with the correct username and password. 
The test should fail initially, as the feature has not been implemented yet.

```dart

test('Login with correct username and password', () async {
  final userRepository = MockUserRepository();
  final loginUseCase = LoginUseCase(userRepository);

  when(userRepository.login('johndoe', 'password'))
      .thenAnswer((_) async => User(id: '1', name: 'John Doe'));

  final result = await loginUseCase(LoginParams(username: 'johndoe', password: 'password'));

  expect(result, Right(User(id: '1', name: 'John Doe')));
});

```

### Step 2: Write the code to pass the test
Next, write the minimum amount of code required to pass the test. In this case, you would need to implement the login method in the UserRepository class.


```dart 
abstract class UserRepository {
  Future<Either<Failure, User>> login(String username, String password);
}

class UserRepositoryImpl implements UserRepository {
  final UserLocalDataSource localDataSource;
  final UserRemoteDataSource remoteDataSource;

  UserRepositoryImpl({required this.localDataSource, required this.remoteDataSource});

  @override
  Future<Either<Failure, User>> login(String username, String password) async {
    try {
      final user = await remoteDataSource.login(username, password);
      localDataSource.cacheUser(user);
      return Right(user);
    } on ServerException {
      return Left(ServerFailure());
    } on CacheException {
      return Left(CacheFailure());
    }
  }
}

```

### Step 3: Refator

Once the test passes, you can refactor the code to improve its design, readability, and maintainability. Here are some steps you can follow:

1. Extract method: If a method is doing too many things, it may be helpful to extract part of it into a separate method. This makes the code more modular and easier to read and test.

2. Rename: A descriptive name is important for methods, classes, and variables. Renaming a method to better reflect its purpose can make the code more readable and easier to understand.

3. Reduce complexity: If a method or class is too complex, it can be difficult to understand and test. Simplifying the code by breaking it into smaller pieces can make it more manageable.

4. Replace conditional logic with polymorphism: When dealing with complex conditional logic, it can be helpful to replace it with polymorphism. This simplifies the code by reducing the number of conditions and making it easier to maintain.

5. Remove duplication: Duplication can make code difficult to maintain and can lead to bugs. Refactoring to remove duplication can make the code more readable, reduce the risk of bugs, and make it easier to maintain.

6. Use interfaces: Interfaces allow for loose coupling between classes and promote abstraction. Refactoring to use interfaces can make code more modular and easier to test.


### Step 3: Repeat

Repeat the process for each feature or functionality of your application.

By following the TDD approach, you can ensure that your code is well-designed, easy to maintain, and bug-free. It also allows you to catch bugs and issues early in the development cycle, making it easier and less expensive to fix them.


## Organizing Tests

One way to do this is to create a test directory at the root level of your project, and within that directory create subdirectories that mirror the structure of your `/lib` directory. 
For example, if you have a file at `/lib/screens/home_screen.dart`, you could create a corresponding test file at `/test/screens/home_screen_test.dart`.

Here's an example of what the directory structure might look like:

```
/my_flutter_app
  /lib
    /externals 
      /pages
        home_page.dart
        ...
    /adapters
      /models
        user_model.dart
        ...
  /test
    /externals 
      /pages
        home_page.test.dart
        ...
    /adapters
      /models
        user_model.test.dart
        ...
```

By organizing the tests in this way, you can easily locate the tests that correspond to specific files in your /lib directory. 
Additionally, this structure can make it easier to run tests selectively, as you can run tests for specific directories or files using your test runner's command line interface.

