# Creating an array of promises for Promise.all()

When we want to pass a promise that only resolves once a number of other promises have all resolved successfully, we can use `Promise.all()`.

`Promise.all()` takes an array of promises and returns a single promise. This promise will only resolve once all the promises in the array of promises it receives have been resolved. If any of those promises are rejected, the promise returned by `Promise.all()` will also be rejected.

We can use Array.map() to create an array of promises from any other array. We do this by passing a callback function to the array's `map` method, which receives a single element from the array and returns a new promise.

The following example shows a simplified version of this:

```js
const values = [true, false, true, true];
Promise.all(
  values.map(function (value) {
    if (value === true) {
      return Promise.resolve();
    } else {
      return Promise.reject();
    }
  })
)
  .then(function () {
    console.log("Everything is true");
  })
  .catch(function () {
    console.log("Not everithing is true");
  });
```

This code will take the values array and create a new array containing four promises. Three of those promises will resolve successfully, but one will reject. This will cause the entire promise returned by `Promise.all()` to be rejected, triggering the code in the `catch` block to execute.

## References

- [Building Progressive Web Apps](https://www.oreilly.com/library/view/building-progressive-web/9781491961643)
