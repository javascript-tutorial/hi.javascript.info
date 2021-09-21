# Functions

अक्सर हमें स्क्रिप्ट के कई स्थानों पर इसी तरह की क्रिया करने की आवश्यकता होती है।

उदाहरण के लिए, हमें एक अच्छा दिखने वाला संदेश दिखाना चाहिए जब कोई आगंतुक लॉग इन करता है, लॉग आउट करता है।

Functions प्रोग्राम के मुख्य "बिल्डिंग ब्लॉक्स" हैं। वे बिना दोहराव के कोड को कई बार कॉल करने की अनुमति देते हैं।

हम पहले से ही बिल्ट-इन function के उदाहरण देख चुके हैं, जैसे `alert(message)`, `prompt(message, default)` और `confirm(question)`। लेकिन हम अपने स्वयं के functions भी बना सकते हैं।

## Function घोषणा

function बनाने के लिए हम एक _function घोषणा_ का उपयोग कर सकते हैं।

यह इस तरह दिखता है:

```js
function showMessage() {
  alert( "सभी को नमस्कार!" );
}
```

`function` कीवर्ड पहले जाता है, फिर _function का नाम_ जाता है, फिर कोष्ठक के बीच _parameters_ की एक सूची (उपरोक्त उदाहरण में खाली) और अंत में function का कोड, जिसे "function बॉडी" भी कहा जाता है, घुंघराले ब्रेसिज़ के बीच।

```js
function name(parameters) {
  ...body...
}
```

हमारे नए function को इसके नाम से बुलाया जा सकता है: `showMessage()`।

उदाहरण के लिए:

```js run
function showMessage() {
  alert( 'सभी को नमस्कार!' );
}

*!*
showMessage();
showMessage();
*/!*
```

`showMessage()` कॉल करने से function के कोड को निष्पादित करता है। यहां हम संदेश को दो बार देखेंगे।

यह उदाहरण स्पष्ट रूप से function के मुख्य उद्देश्यों में से एक को प्रदर्शित करता है: कोड आवृत्ति से बचने के लिए।

यदि हमें कभी भी संदेश या उसके दिखाए जाने के तरीके को बदलने की आवश्यकता होती है, तो यह कोड को एक ही स्थान पर संशोधित करने के लिए पर्याप्त है: वह function जो इसे आउटपुट करता है।

## लोकल variables

किसी function के अंदर घोषित एक variable केवल उस function के अंदर ही दिखाई देता है।

उदाहरण के लिए:

```js run
function showMessage() {
*!*
  let message = "हैलो, मैं जावास्क्रिप्ट हूँ!"; // local variable
*/!*

  alert( message );
}

showMessage(); // हैलो, मैं जावास्क्रिप्ट हूँ!

alert( message ); // <-- Error! variable function के लिए स्थानीय है
```

## बाहरी variables

एक function बाहरी variable को भी एक्सेस कर सकता है, उदाहरण के लिए:

```js run no-beautify
let *!*userName*/!* = 'John';

function showMessage() {
  let message = 'नमस्ते, ' + *!*userName*/!*;
  alert(message);
}

showMessage(); // नमस्ते, John
```

function के पास बाहरी variable तक पूर्ण पहुंच है। यह इसे बदल भी कर सकता है।

उदाहरण के लिए:

```js run
let *!*userName*/!* = 'John';

function showMessage() {
  *!*userName*/!* = "Bob"; // (1) बाहरी variable बदल दिया

  let message = 'Hello, ' + *!*userName*/!*;
  alert(message);
}

alert( userName ); // *!*John*/!* फ़ंक्शन कॉल से पहले

showMessage();

alert( userName ); // *!*Bob*/!*, मान function द्वारा संशोधित किया गया था
```

बाहरी variable का उपयोग केवल तभी किया जाता है जब कोई लोकल न हो।

यदि function के अंदर एक ही नामित variable घोषित किया गया है तो यह _shadows_ बाहरी है। उदाहरण के लिए, नीचे दिए गए कोड में function लोकल `userName` का उपयोग करता है। बाहरी को अनदेखा किया जाता है:

```js run
let userName = 'John';

function showMessage() {
*!*
  let userName = "Bob"; // एक local variable घोषित करें
*/!*

  let message = 'Hello, ' + userName; // *!*Bob*/!*
  alert(message);
}

// फ़ंक्शन अपना स्वयं का userName बनाएगा और उसका उपयोग करेगा
showMessage();

alert( userName ); // *!*John*/!*, अपरिवर्तित, function बाहरी variable का उपयोग नहीं करता है
```

```smart header="Global variables"
किसी function के बाहर घोषित variables, जैसे उपरोक्त कोड में बाहरी `userName`, *global* कहलाते हैं।

ग्लोबल variables किसी भी function से दिखाई देते हैं (जब तक कि लोकल द्वारा छिपा न हो)।

ग्लोबल variable के उपयोग को कम करने के लिए यह एक अच्छा अभ्यास है। आधुनिक कोड में कुछ या कोई ग्लोबल्स नहीं हैं। अधिकांश variable अपने functions में रहते हैं। हालांकि कभी-कभी, वे प्रोजेक्ट-स्तरीय डेटा संग्रहीत करने के लिए उपयोगी हो सकते हैं।
```

## Parameters

हम Parameters (जिसे _function arguments_ भी कहा जाता है) का उपयोग करके function को मनमाना डेटा पास कर सकते हैं।

नीचे दिए गए उदाहरण में, function के दो parameters हैं: `from` और `text`।

```js run
function showMessage(*!*from, text*/!*) { // arguments: from, text
  alert(from + ': ' + text);
}

*!*
showMessage('Ann', 'Hello!'); // Ann: Hello! (*)
showMessage('Ann', "What's up?"); // Ann: What's up? (**)
*/!*
```

जब function को लाइनों में कॉल किया जाता है `(*)` और `(**)`, तो दिए गए मानों को लोकल variables में कॉपी किया जाता है `from` और `text`। फिर function उनका उपयोग करता है।

यहां एक और उदाहरण दिया गया है: हमारे पास एक variable `from` है और इसे function में पास करें। कृपया ध्यान दें: function `from` को बदलता है, लेकिन परिवर्तन बाहर नहीं देखा जाता है, क्योंकि function को हमेशा मूल्य की एक प्रति प्राप्त होती है:

```js run
function showMessage(from, text) {

*!*
  from = '*' + from + '*'; // make "from" look nicer
*/!*

  alert( from + ': ' + text );
}

let from = "Ann";

showMessage(from, "Hello"); // *Ann*: Hello

// the value of "from" is the same, the function modified a local copy
alert( from ); // Ann
```

## डिफॉल्ट वैल्यूज

यदि कोई parameter प्रदान नहीं किया जाता है, तो उसका मान `undefined` हो जाता है।

उदाहरण के लिए, उपरोक्त function `showMessage(from, text)` को एक argument के साथ बुलाया जा सकता है:

```js
showMessage("Ann");
```

यह कोई एरर नहीं है। ऐसी कॉल `"*Ann*: undefined"` आउटपुट करेगी। कोई `text` नहीं है, इसलिए यह माना जाता है कि `text === undefined`।

यदि हम इस मामले में "डिफ़ॉल्ट" `text` का उपयोग करना चाहते हैं, तो हम इसे `=` के बाद उल्लिखत कर सकते हैं:

```js run
function showMessage(from, *!*text = "no text given"*/!*) {
  alert( from + ": " + text );
}

showMessage("Ann"); // Ann: no text given
```

अब यदि `text` parameter नहीं देना गया हो, तो उसे `"no text given"` मान मिलेगा।

यहां `"no text given"` एक स्ट्रिंग है, लेकिन यह एक अधिक जटिल अभिव्यक्ति हो सकती है, जिसका केवल मूल्यांकन किया जाता है और parameter गायब होने पर असाइन किया जाता है। तो, यह भी संभव है:

```js run
function showMessage(from, text = anotherFunction()) {
  // anotherFunction() only executed if no text given
  // its result becomes the value of text
}
```

```smart header="Evaluation of default parameters"
जावास्क्रिप्ट में, हर बार संबंधित parameter के बिना function को कॉल किए जाने पर एक डिफ़ॉल्ट parameter का मूल्यांकन किया जाता है।

ऊपर दिए गए उदाहरण में, `anotherFunction()` को हर बार `showMessage()` को `text` parameter के बिना कहा जाता है।
```

### वैकल्पिक डिफ़ॉल्ट parameters

कभी-कभी function घोषणा में parameter के लिए डिफ़ॉल्ट मान सेट करना समझ में आता है, लेकिन बाद के चरण में, इसके निष्पादन के दौरान भी सेट किया जाता है।

छोड़े गए पैरामीटर की जांच करने के लिए, हम इसकी तुलना `undefined` से कर सकते हैं:

```js run
function showMessage(text) {
*!*
  if (text === undefined) {
    text = 'खाली संदेश';
  }
*/!*

  alert(text);
}

showMessage(); // खाली संदेश
```

...या हम `||` ऑपरेटर का उपयोग कर सकते हैं:

```js
// यदि टेक्स्ट पैरामीटर छोड़ा गया है या "" पारित किया गया है, तो इसे 'खाली' पर सेट करें
function showMessage(text) {
  text = text || 'empty';
  ...
}
```

आधुनिक जावास्क्रिप्ट इंजन [nullish coalescing operator](info:nullish-coalescing-operator) `??` को सपोर्ट करती है| यह तब बेहतर होता है जब `0` जैसे झूठे मूल्यों को नियमित माना जाता है:

```js run
// यदि कोई "count" पैरामीटर नहीं है, तो "unknown" दिखाएं
function showCount(count) {
  alert(count ?? "unknown");
}

showCount(0); // 0
showCount(null); // unknown
showCount(); // unknown
```

## एक मान लौटाना

एक function परिणाम के रूप में एक मान वापस कॉलिंग कोड में वापस कर सकता है।

सबसे सरल उदाहरण एक ऐसा function होगा जो दो मानों का योग करता है:

```js run no-beautify
function sum(a, b) {
  *!*return*/!* a + b;
}

let result = sum(1, 2);
alert( result ); // 3
```

निर्देश `return` function के किसी भी स्थान पर हो सकता है। जब निष्पादन उस तक पहुंच जाता है, तो function बंद हो जाता है, और मान कॉलिंग कोड पर वापस आ जाता है (उपरोक्त `result` को सौंपा गया)

एक function में `return` की कई घटनाएं हो सकती हैं। उदाहरण के लिए:

```js run
function checkAge(age) {
  if (age >= 18) {
*!*
    return true;
*/!*
  } else {
*!*
    return confirm('क्या आपके पास अपने माता-पिता से अनुमति है?');
*/!*
  }
}

let age = prompt('आपकी उम्र क्या है?', 18);

if ( checkAge(age) ) {
  alert( 'प्रवेश करने की अनुमति है' );
} else {
  alert( 'पहुंच अस्वीकृत' );
}
```

बिना मूल्य के `return` का उपयोग करना संभव है। यह function को तुरंत बाहर निकलने का कारण बनता है।

उदाहरण के लिए:

```js
function showMovie(age) {
  if ( !checkAge(age) ) {
*!*
    return;
*/!*
  }

  alert( "आपको फिल्म दिखा रहा है" ); // (*)
  // ...
}
```

ऊपर दिए गए कोड में, अगर ` checkAge(age)` `false` लौटाता है, तो `showMovie` `alert` पर आगे नहीं बढ़ेगा।

````smart header="A function with an empty `return`or without it returns`undefined`" If a function does not return a value, it is the same as if it returns `undefined`:

```js run
function doNothing() {
  /* खाली */
}

alert( doNothing() === undefined ); // true
```

एक खाली `return` भी `return undefined` जैसा ही है:

```js run
function doNothing() {
  return;
}

alert( doNothing() === undefined ); // true
```
````

````warn header="Never add a newline between `return` and the value"
`return` में एक लंबी अभिव्यक्ति के लिए, इसे एक अलग लाइन पर रखना आकर्षक हो सकता है, जैसे:

```js
return
 (some + long + expression + or + whatever * f(a) + f(b))
```
यह काम नहीं करता है, क्योंकि `return` के बाद जावास्क्रिप्ट सेमीकोलन लगा देता है । यह उसी तरह काम करेगा:

```js
return*!*;*/!*
 (some + long + expression + or + whatever * f(a) + f(b))
```

तो, यह प्रभावी रूप से एक खाली रिटर्न बन जाता है।

यदि हम चाहते हैं कि लौटाए गए एक्सप्रेशन को कई लाइनों में लपेटा जाए, तो हमें इसे उसी लाइन से शुरू करना चाहिए जैसे `return`। या कम से कम उद्घाटन कोष्ठक इस प्रकार रखें:

```js
return (
  some + long + expression
  + or +
  whatever * f(a) + f(b)
  )
```
और यह वैसे ही काम करेगा जैसा हम उम्मीद करते हैं।
````

## एक function का नामकरण [#function-naming]

Functions क्रिया हैं। तो उनका नाम आमतौर पर एक क्रिया है। यह संक्षिप्त होना चाहिए, यथासंभव सटीक होना चाहिए और यह वर्णन करना चाहिए कि function क्या करता है, ताकि कोड पढ़ने वाले व्यक्ति को यह संकेत मिल सके कि function क्या करता है।

क्रिया को अस्पष्ट रूप से वर्णित करने वाले मौखिक उपसर्ग के साथ function प्रारंभ करना एक व्यापक प्रथा है। उपसर्गों के अर्थ पर टीम के भीतर एक समझौता होना चाहिए।

उदाहरण के लिए, `"show"` से शुरू होने वाले फ़ंक्शन आमतौर पर कुछ दिखाते हैं।

Function की शुरुआत...

- `"get…"` -- एक मूल्य वापस करें,
- `"calc…"` -- कुछ गणना करो,
- `"create…"` -- कुछ बनाये,
- `"check…"` -- कुछ जांचें और एक बूलियन लौटाएं, आदि।

ऐसे नामों के उदाहरण:

```js no-beautify
showMessage(..)     // एक संदेश दिखाता है
getAge(..)          // उम्र लौटाता है (इसे किसी तरह प्राप्त करता है)
calcSum(..)         // एक योग की गणना करता है और परिणाम देता है
createForm(..)      // एक फॉर्म बनाता है (और आमतौर पर इसे वापस करता है)
checkPermission(..) // अनुमति की जाँच करता है, सही/गलत लौटाता है
```

उपसर्गों के साथ, function नाम पर एक नज़र यह समझ देती है कि यह किस प्रकार का कार्य करता है और यह किस प्रकार का मूल्य देता है।

```smart header="One function -- one action"
एक function को ठीक वही करना चाहिए जो उसके नाम से सुझाया गया है, और नहीं।

दो स्वतंत्र क्रियाएं आम तौर पर दो functions की सेवा करती हैं, भले ही उन्हें आम तौर पर एक साथ बुलाया जाता है (उस स्थिति में हम एक तीसरा function बना सकते हैं जो उन दोनों को कॉल करता है)।

इस नियम को तोड़ने के कुछ उदाहरण:

- `getAge` -- बुरा होगा अगर यह उम्र के साथ एक `alert` दिखाता है (सिर्फ लेना चाहिए )।
- `createForm` -- खराब होगा यदि यह डॉक्यूमेंट को संशोधित करता है, इसमें एक फॉर्म जोड़ता है (केवल इसे बनाना और वापस करना चाहिए)।
- `checkPermission` -- खराब होगा यदि यह `access granted/denied` संदेश प्रदर्शित करता है (केवल जांच करना चाहिए और परिणाम वापस करना चाहिए)।

ये उदाहरण उपसर्गों के सामान्य अर्थ ग्रहण करते हैं। आप और आपकी टीम अन्य अर्थों पर सहमत होने के लिए स्वतंत्र हैं, लेकिन आमतौर पर, वे बहुत भिन्न नहीं होते हैं। किसी भी मामले में, आपको इस बात की पक्की समझ होनी चाहिए कि उपसर्ग का क्या अर्थ है, उपसर्ग का function क्या कर सकता है और क्या नहीं। सभी समान-उपसर्ग फ़ंक्शन को नियमों का पालन करना चाहिए। और टीम को ज्ञान साझा करना चाहिए।
```

```smart header="Ultrashort function names"
*अक्सर* उपयोग किए जाने वाले फ़ंक्शंस में कभी-कभी अल्ट्रा-शॉर्ट नाम होते हैं।

उदाहरण के लिए, [jQuery](http://jquery.com) फ्रेमवर्क `$` के साथ एक function को परिभाषित करता है। The [Lodash](http://lodash.com/) library का मुख्य function `_` है।

ये अपवाद हैं। आम तौर पर functions नाम संक्षिप्त और वर्णनात्मक होने चाहिए।
```

## Functions == Comments

Functions छोटे होने चाहिए और ठीक एक काम करना चाहिए। अगर वह चीज बड़ी है, तो शायद यह function को कुछ छोटे functions में विभाजित करना बेहतर है। कभी-कभी इस नियम का पालन करना इतना आसान नहीं हो सकता है, लेकिन यह निश्चित रूप से एक अच्छी बात है।

एक अलग function न केवल परीक्षण और डीबग करना आसान है - इसका अस्तित्व एक महान comment है!

उदाहरण के लिए, नीचे दिए गए दो कार्यों `showPrimes(n)` की तुलना करें। हर एक `n` तक [अभाज्य संख्याएँ](https://en.wikipedia.org/wiki/Prime_number) आउटपुट करता है।

पहला संस्करण एक लेबल का उपयोग करता है:

```js
function showPrimes(n) {
  nextPrime: for (let i = 2; i < n; i++) {
    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }

    alert( i ); // एक अभाज्य संख्या
  }
}
```

दूसरा संस्करण अभाज्यता के परीक्षण के लिए एक अतिरिक्त function `isPrime(n)` का उपयोग करता है:

```js
function showPrimes(n) {

  for (let i = 2; i < n; i++) {
    *!*if (!isPrime(i)) continue;*/!*

    alert(i);  // एक अभाज्य संख्या
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if ( n % i == 0) return false;
  }
  return true;
}
```

दूसरा संस्करण समझना आसान है, है ना? कोड पीस के बजाय हम क्रिया का एक नाम देखते हैं (`isPrime`)। कभी-कभी लोग ऐसे कोड को _self-describing_ कहते हैं।

इसलिए, function बनाए जा सकते हैं, भले ही हम उनका पुन: उपयोग करने का इरादा न रखते हों। वे कोड की संरचना करते हैं और इसे पठनीय बनाते हैं।

## सारांश

एक function घोषणा इस तरह दिखती है:

```js
function name(parameters, delimited, by, comma) {
  /* code */
}
```

- किसी function को दिए गए मान parameters के रूप में उसके local variables में कॉपी किए जाते हैं।
- एक function बाहरी variables का इस्तेमाल कर सकता है। लेकिन यह केवल अंदर से बाहर काम करता है। function के बाहर का कोड इसके स्थानीय variables नहीं देखता है।
- एक function एक मान वापस कर सकता है। यदि ऐसा नहीं होता है, तो इसका परिणाम `undefined` होता है।

कोड को साफ और समझने में आसान बनाने के लिए, function में मुख्य रूप से local variables और parameter का उपयोग करने की अनुशंसा की जाती है, outer variables नहीं।

ऐसे function को समझना हमेशा आसान होता है जो पैरामीटर प्राप्त करता है, उनके साथ काम करता है, और किसी ऐसे फ़ंक्शन की तुलना में परिणाम देता है जिसमें कोई पैरामीटर नहीं होता है, लेकिन बाहरी variables को साइड-इफेक्ट के रूप में संशोधित करता है।

Function नामकरण:

- एक नाम स्पष्ट रूप से वर्णन करना चाहिए कि function क्या करता है। जब हम कोड में एक function कॉल देखते हैं, तो एक अच्छा नाम हमें तुरंत समझा देता है कि यह क्या करता है और क्या वापस लौटता है।
- एक function एक क्रिया है, इसलिए function नाम आमतौर पर मौखिक होते हैं।
- कई प्रसिद्ध function प्रीफ़िक्स मौजूद हैं जैसे `create…`, `show…`, `get…`, `check…` और इसी तरह। function क्या करता है यह संकेत देने के लिए उनका उपयोग करें।

Function स्क्रिप्ट के मुख्य निर्माण खंड हैं। अब हमने मूल बातें शामिल कर ली हैं, इसलिए हम वास्तव में उन्हें बनाना और उनका उपयोग करना शुरू कर सकते हैं। लेकिन यह सिर्फ रास्ते की शुरुआत है। हम कई बार उनके पास वापस जायेंगे, उन्नत सुविधाओं में और अधिक गहराई से इनको जानेंगे।
