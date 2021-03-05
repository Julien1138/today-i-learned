# Add v-model capability to a custom component

`v-model` replace the use of both `:value` and `@input`.

Example for a color-picker :

```js
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  }

  methods: {
    onClick(color) {
      this.$emit("input", color);
    },
  },
};
```

And how to use it :

```html
<color-picker v-model="myColor"></color-picker>
```

## References

- [VueJS documentation](https://vuejs.org/v2/guide/components.html#Using-v-model-on-Components)
- [VueJS documentation (going further)](https://vuejs.org/v2/guide/components-custom-events.html#Customizing-Component-v-model)
