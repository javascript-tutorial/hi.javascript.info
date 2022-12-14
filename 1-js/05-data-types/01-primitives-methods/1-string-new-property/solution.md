
कोशिश करो run(दौड़ना) करने की:

```js run
let str = "Hello";

str.test = 5; // (*)

alert(str.test);
```

आपके पास `use strict` है, या नहीं इसके आधार, हो सकता है परिणाम यह हो:
1. `undefined` (no strict mode)
2. An error (strict mode).

क्यों? चलाएं फिर से देखते हैं, पंक्ति(line) `(*)` पर क्या हो रहा है :

1. जब `str` का गुणधर्म(property) पहुँचा जाता है , फिर एक "wrapper object" बनाया जाता है. 
2. strict mode में, इसमें लिखना एक त्रुटि(error) है.
3. वरना, गुणधर्म(property) के साथ कार्रवाई(operation) जारी हो जाति है, वस्तु(object) को `test` गुणधर्म(property) मिलाती है, लेकिन उसके बाद "wrapper object" गायब हो जाता है, तो अंतिम पंक्ति(line) में `str` गुणधर्म(property) का कोई निशान नहीं है.

**यह उदाहरण स्पष्ट रूप से दिखाता है कि प्राथमिक(primitives) वस्तुएं(objects) नहीं हैं.**

ये अतिरिक्त जानकारी(data) संग्रह (store) नहीं कर सकते!
