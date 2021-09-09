importance: 4

---

# क्या "else" आवश्यक है?

यदि `age` parameter `18` से अधिक है, तो निम्नलिखित function `true` लौटाता है।

अन्यथा, यह एक पुष्टिकरण मांगता है और अपना परिणाम देता है:

```js
function checkAge(age) {
  if (age > 18) {
    return true;
*!*
  } else {
    // ...
    return confirm('क्या माता-पिता ने आपको अनुमति दी थी?');
  }
*/!*
}
```

यदि `else` हटा दिया जाता है तो क्या function अलग तरह से काम करेगा?

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  }
*!*
  // ...
  return confirm('क्या माता-पिता ने आपको अनुमति दी थी?');
*/!*
}
```

क्या इन दोनों रूपों के व्यवहार में कोई अंतर है?
