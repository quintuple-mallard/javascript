# About

The [async and await][async-await] keywords are [syntactic sugar][wiki-syntax-sugar] for promises, and allow asynchronous operations to be written in a clearer way.

## Async functions

An async function can be defined by putting the keyword `async` in front of a function definition.
Async functions return a `Promise` that performs all the actions in the function, with `return` statements being turned into `resolve` calls.

So the following async function `foo`:

```javascript
async function foo(bar) {
  console.log(`bar is ${bar}`);
  return bar ** 2;
}
```

is equivalent to a regular function using a promise:

```javascript
function foo(bar) {
  return new Promise((resolve) => {
    console.log(`bar is ${bar}`);
    resolve(bar ** 2);
  });
}
```

## Await expressions

### Error handling with await

### Top-level await

[async-await]: https://javascript.info/async-await
[wiki-syntax-sugar]: https://en.wikipedia.org/wiki/Syntactic_sugar
