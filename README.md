# Silent Async Function Failures in Dart

This repository demonstrates a common error in Dart asynchronous programming: silent failures within `async` functions. The code fetches data from a remote API.  If the API request fails, an exception is caught, but without `rethrow`, the calling function wouldn't know of the failure.  The solution shows how to properly rethrow exceptions for better error handling.

## Bug
The `bug.dart` file contains the erroneous code. It fetches data, handles some errors, but doesn't properly propagate other exceptions which leads to silent failures. This example uses `http` package for making the API call, so ensure you add this package to your project (if running the example locally).

## Solution
The `bugSolution.dart` file presents a corrected version, using `rethrow` to properly propagate exceptions up the call stack. This allows the calling function to handle the error appropriately or at least detect a problem occurred.

## How to run the example:
1. Clone this repository.
2. Add the `http` dependency to your `pubspec.yaml` file and run `pub get`.
3. Run the main function in either `bug.dart` (to see the bug) or `bugSolution.dart` (to see the solution).
4. Observe the output and see how the correct propagation of exceptions makes error handling much more robust.