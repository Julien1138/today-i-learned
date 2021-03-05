# Stub an API call with an acceptable delay

VueJS (and js applications in general) have a special way of handling time : [Read this article](https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/) about tasks, microtasks, queues and schedules.

## The issue

While testing a simple click on a button, triggering the display of a loader and the fetch of data from the server, I encountered some trouble. Here is an example of a function to test:

```js
onClick() {
  this.loading = true
  naeptApi
    .fetchNaeptAsync('auth/login', {
      method: 'POST',
      body: JSON.stringify({
        email: this.email,
        password: this.password,
      }),
    })
    .then(() => {
      // Login
    })
    .catch(() => {
      // Handle error
    })
    .finally(() => {
      this.loading = false
  })
})
```

I want to stub the `fetchNaeptAsync` function, which is a promise, so I use the [SinonJS](https://sinonjs.org/releases/v9.0.2/stubs/) `stub.resolve()` function.

In the test function, after a click, we need to use `Vue.nextTick()` to wait for the DOM to be updated. Problem is, the function stubbed with SinonJS actually resolves before the view is updated. It's not visible to the naked eye, but when testing, it fails.

## The solution

We need to delay the resolving of the stubbed Promise. According to the quoted article, a `setTimeout()` with a timeout of 0 will be enough, because it will resolve at the next task loop, whereas `Vue.nextTick()` will resolve within a microtask loop. So here is how it should be done:

```js
stub.returns(
  new Promise((resolve) => {
    setTimeout(() => resolve(), 0);
  })
);
```

## Sources

- [Vue Test Utils documentation](https://vue-test-utils.vuejs.org/guides/#asynchronous-behavior-outside-of-vue)
