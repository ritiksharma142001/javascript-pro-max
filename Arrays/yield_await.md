**What is yield Used For in JavaScript?**

The `yield` keyword is used inside generator functions (`function*`) to pause the function execution and return a value. Later, when you call `.next()`, the function resumes from where it stopped.

### Simple Example: Pausing Execution
```js
function* myGenerator() {
  yield "Hello";
  yield "World";
}

const gen = myGenerator();

console.log(gen.next().value); // "Hello"
console.log(gen.next().value); // "World"
console.log(gen.next().value); // undefined
```

#### 🔹 How it Works?
1️⃣ The generator function `myGenerator` has two `yield` statements.
2️⃣ Calling `gen.next()` returns the first value ("Hello") and pauses.
3️⃣ Calling `gen.next()` again resumes from the second `yield` ("World").
4️⃣ Once all `yield` statements are used, `gen.next()` returns `undefined`.

### Why Use `yield`?
✅ **Efficient Iteration** → It pauses execution instead of running all at once.
✅ **Async Generators** → Works with `await` to handle asynchronous data smoothly.

### Example: Using `yield` in an Async Generator
```js
async function* numberGenerator() {
  yield new Promise((resolve) => setTimeout(() => resolve(1), 500));
  yield new Promise((resolve) => setTimeout(() => resolve(2), 500));
  yield new Promise((resolve) => setTimeout(() => resolve(3), 500));
}

const genAsync = numberGenerator();

genAsync.next().then(console.log); // { value: Promise, done: false }
genAsync.next().then(console.log); // { value: Promise, done: false }
genAsync.next().then(console.log); // { value: Promise, done: false }
```
🔹 Here, `yield` returns a Promise, and `Array.fromAsync()` can collect these values.

---

## Why Use `yield` If `await` Exists?
Both `yield` and `await` help with pausing execution, but they work differently:

| Feature            | `yield` (Generators)  | `await` (Async/Await)  |
|-------------------|----------------------|------------------------|
| Used in          | `function*` (Generator function) | `async function` |
| Execution        | Pauses function execution and returns control to the caller | Pauses only the current function, but doesn't return control to the caller |
| Works With       | `yield` pauses execution until `.next()` is called | `await` pauses execution until the Promise resolves |
| Use Case         | Iterators, streaming data, and handling large datasets efficiently | Handling asynchronous operations like API calls |

### Example 1: `await` - Waiting for a Promise
```js
async function fetchData() {
  console.log("Fetching data...");
  let result = await new Promise((resolve) => setTimeout(() => resolve("Data received!"), 2000));
  console.log(result);
}

fetchData();
console.log("I won't wait for fetchData()");
```
🔹 **Output:**
```
Fetching data...
I won't wait for fetchData()
(Data received! appears after 2 seconds)
```
✅ `await` lets execution continue while waiting for a Promise to resolve.

### Example 2: `yield` - Pausing Execution
```js
function* generatorExample() {
  yield "Step 1";
  yield "Step 2";
  yield "Step 3";
}

const gen = generatorExample();

console.log(gen.next().value); // "Step 1"
console.log(gen.next().value); // "Step 2"
console.log(gen.next().value); // "Step 3"
console.log(gen.next().value); // undefined
```
🔹 Here, `yield` pauses execution until `.next()` is called.

### 🔹 When to Use What?
✅ Use `await` when waiting for asynchronous operations like API calls.
✅ Use `yield` when working with iterators, lazy loading, or streaming data efficiently.

---

## `yield` with `setTimeout`
Sure! Here's an example where `yield` is used with `setTimeout` to simulate pausing execution and resuming after a delay.

### 🔹 `yield` with `setTimeout` in a Generator Function
```js
function* delayedMessages() {
  console.log("Step 1: Start");

  yield new Promise(resolve => setTimeout(() => {
    console.log("Step 2: After 2 seconds...");
    resolve();
  }, 2000));

  yield new Promise(resolve => setTimeout(() => {
    console.log("Step 3: After 3 more seconds...");
    resolve();
  }, 3000));

  console.log("Step 4: Done!");
}

const generator = delayedMessages();

generator.next().value.then(() => generator.next().value.then(() => generator.next()));
```

### 🔹 What Happens Here?
1️⃣ **Step 1:** The function starts running.
2️⃣ **Step 2:** The first `yield` pauses execution for 2 seconds using `setTimeout`.
3️⃣ **Step 3:** After 2 seconds, the second `yield` pauses execution for 3 more seconds.
4️⃣ **Step 4:** Finally, after 5 seconds total, execution completes.

### 🔹 Output in Console
```
Step 1: Start
(Waits 2 seconds...)
Step 2: After 2 seconds...
(Waits 3 more seconds...)
Step 3: After 3 more seconds...
Step 4: Done!
```
✅ `yield` pauses execution, and `.next()` resumes it after the timeout!

