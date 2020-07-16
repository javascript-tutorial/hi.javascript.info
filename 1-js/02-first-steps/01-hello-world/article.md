# Hello, world! 

शिक्षण जो आप पढ़ रहे हैं, वह कोर जावास्क्रिप्ट के बारे में है, जो प्लेटफ़ॉर्म-स्वतंत्र है। इसके अलावा, आप Node.JS और इसका उपयोग करने वाले अन्य प्लेटफ़ॉर्म सीखेंगे।

लेकिन, हमें अपनी स्क्रिप्ट को चलाने के लिए काम करने का environment चाहिए, और, सिर्फ इसलिए कि यह पुस्तक ऑनलाइन है, ब्राउज़र एक अच्छा विकल्प है। हम ब्राउज़र-विशिष्ट commands की मात्रा कम रखेंगे (जैसे `alert`) ताकि, यदि आप किसी अन्य environment जैसे Node.JS पर ध्यान केंद्रित करने की योजना बनाते हैं, तब आप ब्राउज़र जावास्क्रिप्ट सीखने में समय व्यतीत नहीं करेंगे। हम ट्यूटोरियल के [अगले भाग](/ui) में ब्राउज़र जावास्क्रिप्ट पर ध्यान केंद्रित करेंगे।

तो पहले यह देखते हैं कि हम किसी स्क्रिप्ट को वेबपेज से कैसे जोड़ते हैं। सर्वर-साइड वातावरण (जैसे Node.js) के लिए, आप स्क्रिप्ट को `"node my.js"` जैसे कमांड से निष्पादित कर सकते हैं।

## "स्क्रिप्ट" टैग

जावास्क्रिप्ट प्रोग्रामों को HTML दस्तावेज़ के किसी भी भाग में `<script>` टैग की सहायता से डाला जा सकता है।

उदाहरण के लिए:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>स्क्रिप्ट से पहले...</p>

*!*
  <script>
    alert( 'Hello, world!' );
  </script>
*/!*

  <p>...स्क्रिप्ट के बाद.</p>

</body>

</html>
```

```online
आप ऊपर दिए गए बॉक्स के दाएं-कोने में "प्ले" बटन पर क्लिक करके उदाहरण चला सकते हैं।
```

`<स्क्रिप्ट>` टैग में जावास्क्रिप्ट कोड होता है जो ब्राउज़र द्वारा टैग को संसाधित (process) करने पर स्वचालित रूप से निष्पादित होता है।

## आधुनिक मार्कअप (markup)

`<स्क्रिप्ट>` टैग में कुछ attributes (विशेषताएं) हैं जो आजकल शायद ही कभी उपयोग की जाती हैं, लेकिन अभी भी पुराने कोड में पाई जा सकती हैं:

`type` attribute: <code>&lt;script <u>type</u>=...&gt;</code>
: पुराने HTML संस्करण, HTML4 में स्क्रिप्ट में एका attribute `type` की आवश्यकता होती है। `type`. आमतौर पर यह `type="text/javascript"` था. इसकी अब आवश्यकता नहीं है। साथ ही, आधुनिक HTML मानक ने इस विशेषता के अर्थ को पूरी तरह से बदल दिया है। अब, इसका उपयोग जावास्क्रिप्ट मॉड्यूल के लिए किया जा सकता है। लेकिन यह एक उन्नत विषय है, हम ट्यूटोरियल के दूसरे भाग में मॉड्यूल के बारे में बात करेंगे।

The `language` attribute: <code>&lt;script <u>language</u>=...&gt;</code>
: This attribute was meant to show the language of the script. This attribute no longer makes sense because JavaScript is the default language. There is no need to use it.

Comments before and after scripts.
: In really ancient books and guides, you may find comments inside `<script>` tags, like this:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    This trick isn't used in modern JavaScript. These comments hide JavaScript code from old browsers that didn't know how to process the `<script>` tag. Since browsers released in the last 15 years don't have this issue, this kind of comment can help you identify really old code.


## External scripts

If we have a lot of JavaScript code, we can put it into a separate file.

Script files are attached to HTML with the `src` attribute:

```html
<script src="/path/to/script.js"></script>
```

Here, `/path/to/script.js` is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, `src="script.js"` would mean a file `"script.js"` in the current folder.

We can give a full URL as well. For instance:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

To attach several scripts, use multiple tags:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files.

The benefit of a separate file is that the browser will download it and store it in its [cache](https://en.wikipedia.org/wiki/Web_cache).

Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once.

That reduces traffic and makes pages faster.
```

````warn header="If `src` is set, the script content is ignored."
A single `<script>` tag can't have both the `src` attribute and code inside.

This won't work:

```html
<script *!*src*/!*="file.js">
  alert(1); // the content is ignored, because src is set
</script>
```

हमें या तो बाहरी स्क्रिप्ट का चयन करना होगा जैसे `<script src =" ... ">` या हमें नियमित रूप से `<script>` टैग के अंदर कोड लिखना होगा।

ऊपर दिए गए उदाहरण को कार्य करने के लिए दो लिपियों में विभाजित किया जा सकता है:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## सारांश

- हम एक पृष्ठ पर जावास्क्रिप्ट कोड जोड़ने के लिए एक `<स्क्रिप्ट>` टैग का उपयोग कर सकते हैं।
- `टाइप` और` भाषा` attribute की आवश्यकता नहीं है।
- एक बाहरी फाइल में लिखी गई स्क्रिप्ट को `<script src ="path/to/script.js"> </script> के साथ डाला जा सकता है।


ब्राउज़र स्क्रिप्ट और वेबपेज के interaction (परस्पर क्रिया) के बारे में जानने के लिए बहुत कुछ है। लेकिन ध्यान रखें कि ट्यूटोरियल का यह हिस्सा जावास्क्रिप्ट भाषा के लिए समर्पित है, इसलिए हमें इसके विशिष्ट ब्राउज़र कार्यान्वयन के साथ खुद को विचलित नहीं करना चाहिए। हम जावास्क्रिप्ट को चलाने के लिए ब्राउज़र का उपयोग करेंगे, जो कई विकल्पों में से ऑनलाइन पढ़ने के लिए बहुत सुविधाजनक है।
