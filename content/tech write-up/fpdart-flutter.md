---
title: 'Functional Programming on Flutter using fpdart'
date: 2024-08-07T23:15:00+07:00
slug: fpdart-flutter
category: tech
summary:
description:
cover:
  image: ''
  alt: 'Implementing fpdart in Flutter'
  caption:
  relative: true
showToc: true
draft: true
ShowReadingTime: true
tags: []
---

---

### Functional Programming with Fpdart in Flutter

As I work on my budgeting app, functional programming has become essential to my Flutter development process. The fpdart package, in particular, has transformed how I handle errors and manage state. Let me share how it's helped, along with some practical examples.

#### Why Functional Programming?

FP simplifies code by making it more predictable and easier to test. By treating functions as first-class citizens and emphasizing immutability, I’ve reduced side effects and increased the reliability of my code. This approach has been crucial for maintaining consistent application state across multiple modules in my budgeting app.

#### Fpdart: A Game Changer

Fpdart, contains powerful tools like `Either` and `Option` to manage errors and nullable types effectively. Instead of cluttering my code with null checks and try-catch blocks, I now use `Either` to represent success or failure in a clean, expressive way.

Here's how I apply this in my budgeting app:

```dart
import 'package:fpdart/fpdart.dart';

// A simple use case for retrieving budget data
Future<Either<Failure, Budget>> getBudget(String userId) async {
  try {
    // Simulate an API call
    final budget = await api.fetchBudget(userId);
    return Right(budget); // Success case
  } catch (error) {
    return Left(Failure('Failed to fetch budget data')); // Failure case
  }
}
```

Using `Either`, I can cleanly separate the success (`Right`) and failure (`Left`) paths, making the function’s intent clear.

#### Handling Errors with `Either`

In a typical UI scenario, dealing with the result becomes straightforward:

```dart
void displayBudget(String userId) async {
  final result = await getBudget(userId);

  result.fold(
    (failure) => showError(failure.message), // Handle the error
    (budget) => showBudget(budget), // Handle the success
  );
}
```

The `fold` method allows me to elegantly handle both outcomes, ensuring that my UI stays responsive and the code remains easy to understand.

#### Leveraging `Option` for Nullable Values

Another powerful tool from fpdart is `Option`, which I use to handle nullable values without resorting to null checks:

```dart
Option<Budget> findBudgetById(List<Budget> budgets, String id) {
  final budget = budgets.firstWhereOrNull((b) => b.id == id);
  return Option.fromNullable(budget);
}
```

This approach encapsulates the possibility of a null value, allowing me to handle it more gracefully:

```dart
final optionBudget = findBudgetById(budgets, '123');

optionBudget.match(
  () => print('Budget not found'), // Handle the absence of a value
  (budget) => print('Found budget: $budget'), // Handle the presence of a value
);
```

---

> **Tomorrow's dawn heralds the Singularity**

---
