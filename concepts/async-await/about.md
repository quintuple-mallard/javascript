# About

The [async and await][async-await] keywords are [syntactic sugar][wiki-syntax-sugar] for promises, and allow asynchronous operations to be written in a clearer way.

## Async functions

An async function can be defined by putting the keyword `async` in front of a function definition.
Async functions return a `Promise` that performs all the actions in the function, with `return` statements being turned into `resolve` calls.

So the following async function `foo`:

```javascript
async function foo(bar) {
  console.log(`bar = ${bar}`);
  return bar;
}
```

is equivalent to a regular function using a promise:

```javascript
function foo(bar) {
  return new Promise((resolve) => {
    console.log(`bar = ${bar}`);
    resolve(bar);
  });
}
```

## Await expressions

The await keyword is syntactic sugar for a `.then` call.
For example, this simple API call with a promise

```javascript
function getDog() {
  return fetch('https://www.example.com/api').then((response) =>
    response.json(),
  );
}
```

can be rewritten to use await as follows:

```javascript
async function getDog() {
  const data = await fetch('https://www.example.com/api');
  return data.json();
}
```

Await can only be used in async functions and the global scope of modules.

### Error handling with await

Unlike promises, await does not have any built in error handling functionality.
Instead, a try / catch block should be used.

```javascript
async function getDog() {
  try {
    const data = await fetch('https://www.example.com/api');
  } catch {
    throw new Error('Data not available');
  }
  return data.json();
}
```

### Top-level await

In JavaScript modules, you can use an await statement at the [top level][top-await].

```javascript
const data = fetch("https://www.example.com/api").then((response) => response.json());

export default await data;
```
<!-- prettier-ignore-start -->
~~~~exercism/note

While most browsers now support a top-level await statement, Safari has only partial support.

~~~~
<!-- prettier-ignore-end -->

[async-await]: https://javascript.info/async-await
[wiki-syntax-sugar]: https://en.wikipedia.org/wiki/Syntactic_sugar
[top-await]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await#top_level_await
