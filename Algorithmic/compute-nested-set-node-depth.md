# Compute nested set node's depth
FYI: [Nested set model](https://en.wikipedia.org/wiki/Nested_set_model)

To compute a node's depth, you just have to count the number of nodes encapsulating the current node.

A node is the parent of an other if `parent.left < child.left` and `parent.right > child.right`.

Here is the algorithm I used in JS to compute the depth of each node of an array of categories :
```js
.map((category, index, array) => {
  const depth = array.filter(
    (cat) => cat._lft < category._lft && cat._rgt > category._rgt,
  ).length

  return {
    ...category,
    depth: depth,
  }
}),
```