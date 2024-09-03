---
title: 'Functional Programming in Flutter using fpdart'
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
draft: false
ShowReadingTime: true
tags: [
    'Flutter',
    'FunctionalProgramming',
    'Fpdart',
    'FlutterDevelopment',
    'ErrorHandling',
    'ImmutableState',
    'OptionType',
    'EitherType',
    'CleanCode',
    'BudgetingApp',
    'FlutterTips',
]
---

---

As I build my budgeting app, functional programming has become a key part of my development. The fpdart package has really helped me manage errors and state in a more organized way. Let me show you how it’s made a difference with some practical examples.

---

### Why Functional Programming?

> Functional programming makes code easier to manage and test by focusing on pure functions and immutability (not changing data). 
---
## How Fpdart Helps

Fpdart offers tools like `Either` and `Option` that simplify error handling and dealing with nullable values. Instead of using lots of null checks, I use `Either` to handle success and failure in a cleaner way.

Here’s how I use `Either` in my budgeting app:

```dart
import 'package:fpdart/fpdart.dart';

// Get budget data
Future<Either<Failure, Budget>> getBudget(String userId) async {
    try {
        final budget = await api.fetchBudget(userId); // API call
        return Right(budget); // Success
    } catch (error) {
        return Left(Failure('Failed to fetch budget data')); // Failure
    }
}
```


### Handling Errors with `Either`

Handling results in the UI:

```dart
void displayBudget(String userId) async {
    final result = await getBudget(userId);

    result.fold(
            (failure) => showError(failure.message), // Show error message
            (budget) => showBudget(budget), // Display budget
            );
        }
```

With `Either`, I can separate successful results (`Right`) from errors (`Left`), making my code easier to understand.

The `fold` method helps me deal with both success and failure in a clean way, keeping the code neat and the UI responsive.

### Using `Option` for Nullable Values

Fpdart’s `Option` helps manage nullable values without constant null checks. This way, I can handle the presence or absence of values more smoothly.

```dart
Option<Budget> findBudgetById(List<Budget> budgets, String id) {
    final budget = budgets.firstWhereOrNull((b) => b.id == id);
    return Option.fromNullable(budget);
}
```

Instead of checking if `budget` is null, I can handle it like this:

```dart
final optionBudget = findBudgetById(budgets, '123');

optionBudget.match(
        () => print('Budget not found'), // Handle missing budget
        (budget) => print('Found budget: $budget'), // Handle found budget
    );
```

---

- **[fpdart (pub.dev)](https://pub.dev/packages/fpdart)**
- **[fpdart (Github)](https://github.com/SandroMaglione/fpdart)**


---

> **Tomorrow's dawn heralds the Singularity**

---
