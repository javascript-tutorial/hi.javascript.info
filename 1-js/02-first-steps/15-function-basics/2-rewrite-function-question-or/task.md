importance: 4

---

# Rewrite the function using '?' or '||'

# '?' या '||' का उपयोग करके फ़ंक्शन को फिर से लिखें|

The following function returns `true` if the parameter `age` is greater than `18`.
यदि `age` पैरामीटर `18` से अधिक है, तो निम्नलिखित फ़ंक्शन `true` लौटाता है।

Otherwise it asks for a confirmation and returns its result.
अन्यथा, यह एक पुष्टिकरण मांगता है और अपना परिणाम देता है:

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  } else {
    return confirm('Did parents allow you?');
  }
}
```

Rewrite it, to perform the same, but without `if`, in a single line.
इसे फिर से लिखें, वही प्रदर्शन करने के लिए, लेकिन बिना `if` के, एक पंक्ति में।

Make two variants of `checkAge`:
'checkAge' के दो प्रकार बनाएं:

1. Using a question mark operator `?`
2. Using OR `||`
1. प्रश्न चिह्न ऑपरेटर का उपयोग करते हुए `?`
2. OR ऑपरेटर का उपयोग करते हुए `||`
