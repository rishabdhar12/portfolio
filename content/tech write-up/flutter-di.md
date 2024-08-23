---
title: 'Implementing dependency injection in Flutter Application'
date: 2024-08-06T23:15:00+07:00
slug: flutter-di
category: tech
summary:
description:
cover:
  image: ''
  alt: 'Implementing dependency injection in Flutter Application'
  caption:
  relative: true
showToc: true
draft: false
ShowReadingTime: true
tags: []
---

---

I've been working on a Flutter budgeting application lately. Previously, I have encountered difficulties with effectively managing a variety of dependencies. Maintaining a clean and structured codebase is essential for any application that works with user data, many services, and complex financial computations. Dependency Injection (DI) is useful in this situation. Let's explore how get_it can simplify DI in Flutter.

### Why Dependency Injection Matters

> Dependency Injection is a design pattern that helps you manage dependencies in a more modular and scalable way. Instead of creating and managing instances of services manually throughout your code, DI allows you to centralize this process. This leads to better code organization, easier testing, and more maintainable applications.

### Introducing GetIt

`get_it` is a popular service locator for Dart and Flutter, making dependency management straightforward. It acts as a global registry where you can register and retrieve dependencies with ease. Its lightweight nature and flexibility make it an excellent choice for managing dependencies in a Flutter app.

### Setting Up GetIt in Your Flutter App

1. **Add GetIt to Your Project**

   Begin by adding `get_it` to your `pubspec.yaml` file:

   ```yaml
   dependencies:
     flutter:
       sdk: flutter
     get_it: ^7.7.0
   ```

2. **Create and Configure the Service Locator**

   Set up a service locator to register your dependencies. Here’s a basic setup for a budgeting app:

   ```dart
   import 'package:get_it/get_it.dart';

   final GetIt sl = GetIt.instance;

   Future<void> initializeDependencies() async {
     sl.registerLazySingleton<SomeService>(() => SomeService());
     sl.registerSingleton<AnotherService>(AnotherService());
   }
   ```

3. **Utilize Your Services**

   To access a registered service, retrieve it using the service locator:

   ```dart
   class BudgetRepository {
     final SomeService _someService = sl<SomeService>();
     final AnotherService _anotherService = sl<AnotherService>();
   }
   ```

4. **Initialize GetIt in Your App**

   Ensure you initialize `get_it` in the `main` function before running your app:

   ```dart
   Future<void> main() async {
     await initializeDependencies();
     runApp(MyApp());
   }
   ```

### Key Functions of GetIt

1. **Service Registration**

   - **`registerLazySingleton<T>(FactoryFunc<T> factory)`**: It registers a singleton that is lazily instantiated. This means the service is created only when it is first needed, and the same instance is used throughout the app. Ideal for expensive or time-consuming service creation, like network clients.

   - **`registerSingleton<T>(T instance)`**: It registers an already instantiated service as a singleton. Ideal for services that are already created or configured, like a database service.

   - **`registerFactory<T>(FactoryFunc<T> factory)`**: It registers a factory method that creates a new instance each time it’s requested. Ideal for services that should not be shared, such as view models or temporary objects.

2. **Service Retrieval**

   - **`getIt<T>()`**: It retrieves the registered service of type `T` and ensures that you’re accessing the correct instance, and if it’s not registered, you get an immediate notification of the missing dependency.

3. **Service Disposal**

   - **`unregister<T>()`**: Unregisters a service, which can be useful for cleanup operations, mainly in larger apps with many dynamic services.

---

### References

- **[Checkout the repository](https://github.com/fluttercommunity/get_it)**
- **[pub.dev](https://pub.dev/packages/get_it)**

---

> **Tomorrow's dawn heralds the Singularity**

---
