# Array intersection, difference, and union in ES6
Comparing arrays, or rather the content of arrays may not be straightforward. Here are 4 different cases.

For the following examples, we will use 2 arrays:
- `arrA = [1,3,4,5]`
- `arrB = [1,2,5,6,7]`

## Intersection
The intersection of two arrays results in an array containing the element present in both arrays.
In our example it should be `[1,5]`.
```js
let intersection = arrA.filter(x => arrB.includes(x));
```

## Difference
The difference between array A and array B results in an array containing every element from array A that are not present in array B.
In our example it should be `[3,4]`.
```js
let difference = arrA.filter(x => !arrB.includes(x));
```

## Symmetrical difference
The symmetrical difference between two arrays results in an array containing every element from array A that are not present in array B **and** every element from array B that are not present in array A.
It can be thought as the union of the two arrays minus the intersection of the two arrays.
In our example it should be `[2,3,4,6,7]`.
```js
let xor = arrA
  .filter(x => !arrB.includes(x))
  .concat(arrB.filter(x => !arrA.includes(x)));
```

## Union
The union of tho arrays results in an array containing every element that is present in array A or in array B.
In our example it should be `[1,2,3,4,5,6,7]`.
```js
let union = [...arrA, ...arrB];
```
But, the problem with the spread operator is that we will get duplicated elements. So we have to use a Set, because Sets in JavaScript contain only distinct elements:
```js
let union = [...new Set([...arrA, ...arrB)];
```
