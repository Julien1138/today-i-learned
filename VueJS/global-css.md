# Add a global CSS file to a Vue-CLI project
While transforming a Laravel-Mix VueJS project into a Vue-CLI project, I could not use a webpack directive ton globally include a SCSS file as before.

The trick is to include it in the App.vue:
```html
<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="sass">
@import './style/app.scss'
</style>
```
