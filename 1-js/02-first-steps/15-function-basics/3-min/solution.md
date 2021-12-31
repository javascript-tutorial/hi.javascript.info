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

प्रश्न चिह्न ऑपरेटर `'?'` के साथ एक हल:

```js
function min(a, b) {
  return a < b ? a : b;
}
```

नोट: समानता `a == b` के मामले में यह मायने नहीं रखता कि क्या लौटाया जाए।
