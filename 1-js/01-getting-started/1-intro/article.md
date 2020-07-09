# जावास्क्रिप्ट की परिचय

चलिए हम देखते हैं कि जावास्क्रिप् इतना खास क्यों है, हम इस से क्या प्राप्त कर सकते हैं औरा कौन से अन्य टेक्नोलॉजी इसके साथ अच्छे से काम करते हैं।

## जावास्क्रिप्ट क्या है?

*जावास्क्रिप्ट* को पहली बार *वेब पेजेस चलाने* के लिए बनाया गया था।

इस भाषा में प्रोग्राम को *स्क्रिप्ट्स* कहा जाता है। उन्हें एचटीएमएल के अंदर में ही लिखा जा सकता है और वो पेज लोड होते ही अपने आप एक्सेक्यूट (निष्पादित) हो जाता है।

स्क्रिप्ट्स को एक प्लेन टेक्स्ट के रूप में लिखा तथा एक्सेक्यूट (निष्पादित) किया जाता है. उन्हें चलाने के लिए एक विशेष तैयारी या संकलन की आवश्यकता नहीं है।

इस पहलू में, जावास्क्रिप्ट, [जावा](https://en.wikipedia.org/wiki/Java_(programming_language)) नामक एक अन्य भाषा से बहुत अलग है।

```smart header="Why is it called <u>Java</u>Script?"
जब जावास्क्रिप्ट बनाया गया था, तो शुरू में इसका दूसरा नाम था: "LiveScript"। लेकिन उस समय जावा बहुत लोकप्रिय था, इसलिए यह निर्णय लिया गया कि जावा के "छोटे भाई" के रूप में प्रस्तुत करने से एक नई भाषा की स्थिति में मदद मिलेगी।

लेकिन जैसे यह विकसित हुआ, जावास्क्रिप्ट अपने स्वयं के विनिर्देशन के साथ एक पूरी तरह से स्वतंत्र भाषा बन गई इसे कहा जाता है [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), और अब इसका जावा से कोई संबंध नहीं है।
```

आज, जावास्क्रिप्ट को न केवल ब्राउज़र में निष्पादित किया जा सकता है, लेकिन सर्वर पर भी, या वास्तव में किसी भी डिवाइस पर, जिसमें एक विशेष कार्यक्रम है जिसे [जावास्क्रिप्ट इंजन](https://en.wikipedia.org/wiki/JavaScript_engine) कहा जाता है।

ब्राउज़र में एक एकीकृत इंजन होता है जिसे कभी-कभी "जावास्क्रिप्ट वर्चुअल मशीन" कहा जाता है।

अलग-अलग इंजनों के अलग-अलग "कोडनेम" होते हैं। उदाहरण के लिए:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- क्रोम (Chrome) और ओपेरा (Opera) में।
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- फ़ायरफ़ॉक्स (Firefox) में।
- ...IE के विभिन्न संस्करणों के लिए "ट्राइडेंट" (Trident) और "चक्र" (Chakra) जैसे अन्य कोडनेम हैं, माइक्रोसॉफ्ट एज के लिए "चक्रकोर" (ChakraCore), "नाइट्रो" (Nitro) और सफारी के लिए "स्क्विरफेलिश" (SquirrelFish) आदि।

उपरोक्त शब्द याद रखने के लिए अच्छे हैं क्योंकि इनका उपयोग इंटरनेट पर डेवलपर लेखों में किया जाता है। हम भी उनका उपयोग करेंगे। उदाहरण के लिए, यदि "एक सुविधा X V8 द्वारा समर्थित है", तो यह शायद क्रोम और ओपेरा में काम करता है।

```smart header="How do engines work?"

इंजन जटिल हैं। लेकिन मूल बातें आसान हैं।

1. इंजन (एम्बेडेड अगर यह एक ब्राउज़र है) स्क्रिप्ट पढ़ता है (parse)।
2. फिर यह मशीन भाषा के लिए स्क्रिप्ट ("संकलन") को परिवर्तित करता है (compile)।
3. और फिर मशीन कोड चलता है, (बहुत तेज)।

इंजन प्रक्रिया के प्रत्येक चरण में अनुकूलन (Optimisation) लागू करता है। यह संकलित (complied) स्क्रिप्ट को भी देखता है, इसके माध्यम से बहने वाले डेटा का विश्लेषण करता है, और आगे उस ज्ञान के आधार पर मशीन कोड का आगे अनुकूलन करता है।
```

## एक ब्राउज़र में जावास्क्रिप्ट क्या कर सकता है?

आधुनिक जावास्क्रिप्ट एक "सुरक्षित" प्रोग्रामिंग भाषा है। यह मेमोरी या सीपीयू तक निम्न-स्तरीय पहुंच प्रदान नहीं करता है, क्योंकि यह शुरू में उन ब्राउज़रों के लिए बनाया गया था जिन्हें इसकी आवश्यकता नहीं है।

जावास्क्रिप्ट की क्षमताएं बहुत हद तक उस वातावरण पर निर्भर करती हैं, जिसमें वह चल रहा है. उदाहरण के लिए, [Node.js] (https://wikipedia.org/wiki/Node.js) ऐसे कार्यों का समर्थन करता है जो जावास्क्रिप्ट को मनमाने ढंग से फाइल पढ़ने / लिखने, नेटवर्क अनुरोध करने, आदि की अनुमति देता है।

In-browser JavaScript can do everything related to webpage manipulation, interaction with the user, and the webserver.

For instance, in-browser JavaScript is able to:

- Add new HTML to the page, change the existing content, modify styles.
- React to user actions, run on mouse clicks, pointer movements, key presses.
- Send requests over the network to remote servers, download and upload files (so-called [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) and [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologies).
- Get and set cookies, ask questions to the visitor, show messages.
- Remember the data on the client-side ("local storage").

## What CAN'T in-browser JavaScript do?

JavaScript's abilities in the browser are limited for the sake of the user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.

Examples of such restrictions include:

- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.

    Modern browsers allow it to work with files, but the access is limited and only provided if the user does certain actions, like "dropping" a file into a browser window or selecting it via an `<input>` tag.

    There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must agree for data exchange and contain a special JavaScript code that handles it. We'll cover that in the tutorial.

    This limitation is, again, for the user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's a safety limitation.

![](limitations.svg)

Such limits do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow plugin/extensions which may ask for extended permissions.

## What makes JavaScript unique?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Support by all major browsers and enabled by default.
```
JavaScript is the only browser technology that combines these three things.

That's what makes JavaScript unique. That's why it's the most widespread tool for creating browser interfaces.

That said, JavaScript also allows to create servers, mobile applications, etc.

## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and auto-converting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.

There are more. Of course, even if we use one of transpiled languages, we should also know JavaScript to really understand what we're doing.

## सारांश

- जावास्क्रिप्ट को शुरुआत में केवल ब्राउज़र-भाषा के रूप में बनाया गया था, लेकिन अब इसे कई अन्य वातावरणों में भी उपयोग किया जाता है।
- आज, जावास्क्रिप्ट HTML / CSS के साथ पूर्ण एकीकरण के साथ सबसे व्यापक रूप से अपनाया जाने वाला एक अद्वितीय ब्राउज़र-भाषा है।
- कई भाषाएं हैं जो जावास्क्रिप्ट में "transpiled" (किसी अन्य भाषा में अनुवाद करने की प्रक्रिया) होती हैं और कुछ विशेषताएं प्रदान करती हैं।जावास्क्रिप्ट पर महारत हासिल करने के बाद, कम से कम संक्षेप में उन पर एक नज़र डालने की सलाह दी जाती है।
