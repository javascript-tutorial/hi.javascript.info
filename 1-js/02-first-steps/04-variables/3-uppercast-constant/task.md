importance: 4

---

# बड़े अक्षर का उपयोग const के लिये?

निम्नलिखित कोड की जाँच करें:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

<<<<<<< HEAD
यहां हमारे पास एक निरंतर `birthday` तिथि है और `age` की गणना `birthday` से कुछ कोड की सहायता से की जाती है (यह संक्षिप्तता के लिए प्रदान नहीं की जाती है, और क्योंकि विवरण से यहां कोई फर्क नहीं पड़ता)।
=======
Here we have a constant `birthday` for the date, and also the `age` constant.

The `age` is calculated from `birthday` using `someCode()`, which means a function call that we didn't explain yet (we will soon!), but the details don't matter here, the point is that `age` is calculated somehow based on the `birthday`.
>>>>>>> d694e895efe89922a109702085b6ca1efeffea10

क्या `birthday` के लिए बड़ा अक्षर का उपयोग करना सही होगा? `age` के लिए? या दोनों के लिए भी?

```js
<<<<<<< HEAD
const BIRTHDAY = '18.04.1982'; // बड़ा अक्षर बनाएं?

const AGE = someCode(BIRTHDAY); // बड़ा अक्षर बनाएं?
=======
const BIRTHDAY = '18.04.1982'; // make birthday uppercase?

const AGE = someCode(BIRTHDAY); // make age uppercase?
>>>>>>> d694e895efe89922a109702085b6ca1efeffea10
```
