# The modern mode, "use strict"

लंबे समय तक, जावास्क्रिप्ट संगतता मुद्दों के बिना विकसित हुआ। भाषा में नई सुविधाएँ जोड़ी गईं जबकि पुरानी कार्यक्षमता नहीं बदली।

मौजूदा कोड को कभी नहीं तोड़ने का इसका लाभ था। लेकिन नकारात्मक पक्ष यह था कि जावास्क्रिप्ट के रचनाकारों द्वारा की गई कोई भी गलती या अपूर्ण निर्णय हमेशा के लिए भाषा में फंस गया।

2009 तक ऐसा ही था जब ECMAScript 5 (ES5) दिखाई दिया। इसने भाषा में नई सुविधाएँ जोड़ीं और कुछ मौजूदा को संशोधित किया। पुराने कोड को काम करने के लिए, ऐसे अधिकांश संशोधन डिफ़ॉल्ट रूप से बंद होते हैं। आपको उन्हें एक विशेष निर्देश के साथ स्पष्ट रूप से सक्षम करने की आवश्यकता है: `"use strict"`.

## "use strict"


निर्देश एक स्ट्रिंग की तरह दिखता है: `"use strict"` या `'use strict'`. जब यह एक स्क्रिप्ट के शीर्ष पर स्थित होता है, तो पूरी स्क्रिप्ट "आधुनिक" तरीके से काम करती है।


उदाहरण के लिए:

```js
"use strict";

// this code works the modern way
...
```


बहुत जल्द हम फंक्शन (कमांड को ग्रुप करने का एक तरीका) सीखने जा रहे हैं, तो आइए पहले से ध्यान दें कि किसी फंक्शन की शुरुआत में `"use सख्त"` लगाया जा सकता है। ऐसा करने से केवल उस फंक्शन में स्ट्रिक्ट मोड सक्षम होता है। लेकिन आमतौर पर लोग इसका इस्तेमाल पूरी स्क्रिप्ट के लिए करते हैं।

````warn header="Ensure that \"use strict\" is at the top"
Please make sure that `"use strict"` is at the top of your scripts, otherwise strict mode may not be enabled.

Strict mode isn't enabled here:

```js no-strict
alert("some code");
// "use strict" below is ignored--it must be at the top

"use strict";

// strict mode is not activated
```

Only comments may appear above `"use strict"`.
````

```warn header="There's no way to cancel `use strict`"
There is no directive like `"no use strict"` that reverts the engine to old behavior.

Once we enter strict mode, there's no going back.
```

## Browser console

When you use a [developer console](info:devtools) to run code, please note that it doesn't `use strict` by default.

Sometimes, when `use strict` makes a difference, you'll get incorrect results.

So, how to actually `use strict` in the console?

First, you can try to press `key:Shift+Enter` to input multiple lines, and put `use strict` on top, like this:

```js
'use strict'; <Shift+Enter for a newline>
//  ...your code
<Enter to run>
```

यह फ़ायरफ़ॉक्स और क्रोम जैसे अधिकांश ब्राउज़रों में काम करता है।

यदि ऐसा नहीं होता है, उदा। पुराने ब्राउज़र में, 'सख्त उपयोग' सुनिश्चित करने के लिए एक बदसूरत, लेकिन विश्वसनीय तरीका है। इसे इस तरह के रैपर के अंदर रखें:

```js
(function() {
  'use strict';

  // ...your code here...
})()
```

## क्या हमें "strict" का उपयोग करना चाहिए?

सवाल स्पष्ट लग सकता है, लेकिन ऐसा नहीं है।

कोई स्क्रिप्ट शुरू करने की सिफारिश कर सकता है `"use strict"`... लेकिन आप जानते हैं कि क्या अच्छा है?

आधुनिक जावास्क्रिप्ट "कक्षाओं" और "मॉड्यूल" का समर्थन करता है - उन्नत भाषा संरचनाएं (हम निश्चित रूप से उन्हें प्राप्त करेंगे), जो सक्षम करें `use strict` खुद ब खुद। इसलिए हमें जोड़ने की आवश्यकता नहीं है `"use strict"` निर्देश, यदि हम उनका उपयोग करते हैं।


**तो अब के लिए `"use strict";` आपकी स्क्रिप्ट के शीर्ष पर एक स्वागत योग्य अतिथि है। बाद में, जब आपका कोड सभी कक्षाओं और मॉड्यूल में होता है, तो आप इसे छोड़ सकते हैं।**


अभी तक, हमें इसके बारे में पता चल गया है `use strict` सामान्य रूप में।

अगले अध्यायों में, जैसा कि हम भाषा की विशेषताओं को सीखते हैं, हम सख्त और पुराने तरीकों के बीच अंतर देखेंगे। सौभाग्य से, बहुत सारे नहीं हैं और वे वास्तव में हमारे जीवन को बेहतर बनाते हैं।

इस ट्यूटोरियल में सभी उदाहरण सख्त मोड मानते हैं जब तक कि (बहुत ही कम) अन्यथा निर्दिष्ट न हो।
