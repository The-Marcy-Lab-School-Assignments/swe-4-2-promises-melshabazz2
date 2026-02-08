# Short Response Questions

## Question 1: Promise States

What are the three states of a Promise? For each state, explain what it represents and which Promise method (`.then()` or `.catch()`) is used to handle it.

**Your Answer:**
- The first state of a `promise` is `pending`. It represents the current status of the `promise`, the asychronous code has begun and is in progress but has not been completed yet. The `pending` state isn't handled by a method, it is an attribute that exist in the cycle of a `promise`
- The second state of a `promise` is `resolved` also known as `fulfilled`, `resolved` represents the successful completion of the `promise`. It is handled by the `.then()` method which is used to execute a callback that receieves the resulting value. 
- The third state of a `promise` is `rejected`, this state usually occurs when an asynchronous operation fails, it proivdes a reason for the failure, usually an `error object`. `rejected` is handled using the `.catch()` method or by using the `try...catch` block to prevent the error from crashing the application.



## Question 2: Callback Hell vs. Promise Chaining

Explain why deeply nested callbacks (callback hell) are problematic, and describe how Promise chaining with `.then()` solves this problem.

**Your Answer:**

- `nested callbacks` are problematic because:
    - They create a pyramid structure that is hard to read. 
    - You have to manually handle every single error level, unlike promises that allow you to handle all errors with one method.

- Promise chaining improves readability. Instead of nesting functions inside of others, `.then()` returns a new promise which creates the next link in the chain. Each `.then()` represents a sequence.
- Error handling: As mentioned before, instead of handling an error on every level you can attach a `.catch()`at the bottom for when an error occurs(`rejects`) and that stops all the remaining `.then()` blocks from executing and skips to the `.catch()` in order to assess the error.

## Question 3: Error Handling with `.catch()`

If you have a chain of three `.then()` calls followed by a single `.catch()`, and the second `.then()` throws an error, what happens? Why is this behavior useful?

**Your Answer:**
- First what happens is that promise enters the `reject` state and that second `.then()`holds on to the error until it reaches the `.catch()`.
- Javascript will skip the third `.then()` and go to the `.catch()` which receives the error as an argument.
- This behavior (also known as `error propogation`) is useful because:
    - It prevents "failure", it makes no sense for the code to continue to run if the second `.then()` fails. It prevents your code from running with missing data or invalid data.
    - You dont have to write an error for every level, if any `.then()` fails, the code will stop from executing and skip to the single `.catch()` which provides you with an error object for the level that error occured in. It also allows debugging to be alot easier by providing a trace back to that level in which the error occured.


