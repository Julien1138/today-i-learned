# Dynamically remove watcher
When dynamically creating a watcher (using the `this.$watch` method), it actually returns a function. When this function is called, it destroys the watcher.

Example:
```js
waitForPreferences() {
  if (this.tourIsDone === undefined) {
    this.unwatchPreferences = this.$watch(
      'tourIsDone',
      this.waitForPreferences,
    )
  } else {
    this.unwatchPreferences()
  }
},
```
