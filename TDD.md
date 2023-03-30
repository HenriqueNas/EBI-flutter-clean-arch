# Test-Driven Development (TDD) with Clean Flutter Manifest (CFM)

Test-Driven Development (TDD) is a software development process that emphasizes writing automated tests before writing the actual code. 
TDD helps to ensure that the code is well-designed, easy to maintain, and bug-free. 
By writing tests first, you can ensure that your code meets the requirements and passes all the acceptance criteria.

## Why TDD?

There are several benefits of using TDD:

1. Better quality code: By writing tests first, you ensure that your code is well-designed and follows the requirements.

2. Early bug detection: By writing tests first, you can detect bugs early in the development cycle, which is cheaper and easier to fix than later stages.

3. Improved maintainability: By having automated tests, you can refactor your code with confidence, knowing that you have tests in place to ensure that everything still works.

4. Increased productivity: TDD forces you to think through the requirements before writing code, which can save you time in the long run.


## TDD With CFM

TDD can be applied to any software development project, including Flutter applications built using Clean Flutter Manifest (CFM). Here are some guidelines for applying TDD with CFM:

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

Once the test passes, you can refactor the code to improve its design, readability, and maintainability.


### Step 3: Repeat

Repeat the process for each feature or functionality of your application.

By following the TDD approach, you can ensure that your code is well-designed, easy to maintain, and bug-free. It also allows you to catch bugs and issues early in the development cycle, making it easier and less expensive to fix them.
