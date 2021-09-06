importance: 4

---

# Is "else" required?

# क्या "else" आवश्यक है?

The following function returns `true` if the parameter `age` is greater than `18`.
यदि `age` पैरामीटर `18` से अधिक है, तो निम्नलिखित फ़ंक्शन `true` लौटाता है।

Otherwise it asks for a confirmation and returns its result:
अन्यथा, यह एक पुष्टिकरण मांगता है और अपना परिणाम देता है:

```js
function checkAge(age) {
  if (age > 18) {
    return true;
*!*
  } else {
    // ...
    return confirm('Did parents allow you?');
  }
*/!*
}
```

Will the function work differently if `else` is removed?
यदि `else` हटा दिया जाता है तो क्या फ़ंक्शन अलग तरह से काम करेगा?

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  }
*!*
  // ...
  return confirm('Did parents allow you?');
*/!*
}
```

Is there any difference in the behavior of these two variants?
क्या इन दोनों रूपों के व्यवहार में कोई अंतर है?
