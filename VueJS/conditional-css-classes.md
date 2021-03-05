# Conditional CSS classes

VueJs provides a simple way of attributing css classes to html elements conditionally.
The syntax is :

```html
<p
  :class="{
            'class-1': condition_1,
            'class-2': condition_2,
          }"
>
  Hello !
</p>
```

Example:

```html
<div
  class="tag"
  :class="{
            'new-tag': newTag,
            'new-tag-placeholder': newTag && hovered,
          }"
></div>
```
