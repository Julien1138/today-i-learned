# Easy lifecycle debugger
A mixin to copy paste in the main.js file of the projects to see the lifecycle events called by vue for each component :

```js
Vue.mixin({
  created() {
    console.log('[created] ' + this.$options.name)
  },
  destroyed() {
    console.log('[destroyed] ' + this.$options.name)
  },
})
```

Any vue hook can be used.
