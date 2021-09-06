A solution using `if`:
`if` का उपयोग करके एक हल:

```js
function min(a, b) {
  if (a < b) {
    return a;
  } else {
    return b;
  }
}
```

A solution with a question mark operator `'?'`:
प्रश्न चिह्न ऑपरेटर `'?'` के साथ एक हल:

```js
function min(a, b) {
  return a < b ? a : b;
}
```

P.S. In the case of an equality `a == b` it does not matter what to return.
नोट: समानता `a == b` के मामले में यह मायने नहीं रखता कि क्या लौटाया जाए।
