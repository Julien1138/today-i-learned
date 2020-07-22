# How to not cache VueX getters
By default, VueX getters results are updated when the store is updated and then the result is cached. This way the getter's computation is done only if a change in the store occurs.

But if the result of the getter is a computation based on elements outside the store, like a date for example, it's a problem. Because the computation will be done once, at the init of the store, and never again.

On way to solve this issue is to assign a function to a getter. This way, each time the getter is called, the function is executed.
```js
const getters = {
  userIsAuthenticated: (state) => () => {
    return state.sessionTimeout != null && Date.now() < state.sessionTimeout
  },
}
```
Do not forget the parenthesis when calling this particular getter:
`store.getters.userIsAuthenticated()`
