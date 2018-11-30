# जावास्क्रिप्ट की शिक्षा

यह भंडार (repository) आधुनिक जावास्क्रिप्ट की शिक्षा की सामग्री का मेज़बानी करता है जो [https://javascript.info](https://javascript.info) पर प्रकाशित है।

## अनुवाद

(अंग्रेजी वर्णानुक्रम में):

| भाषा | Github | मुख्या अनुवाद लेखक | अनूदित (%) | प्रकाशित |
|----------|--------|-------------------|-----------------|-----------|
| चीनी | https://github.com/xitu/javascript-tutorial-zh | @leviding | ![](http://translate-hook.javascript.info/stats/zh.svg?1) | https://zh.javascript.info |
| जापानी | https://github.com/KenjiI/javascript-tutorial-ja | @KenjiI | ![](http://translate-hook.javascript.info/stats/ja.svg?1) | https://ja.javascript.info |
| रोमानियाई | https://github.com/lighthousand/javascript-tutorial-ro | @lighthousand | started | - |
| रूसी | https://github.com/iliakan/javascript-tutorial-ru | @iliakan | * | https://learn.javascript.ru |
| तुर्की | https://github.com/sahinyanlik/javascript-tutorial-tr | @sahinyanlik | ![](http://translate-hook.javascript.info/stats/tr.svg?1) | - |



`*` – इसका का पिछला वर्जन रूसी में प्रकाशित था, नए को अंग्रेजी से अनुवाद करना है।

अगर आप इसे अपनी भाषा में अनुवाद करना चाहते हैं तो कृपया इस भंडार को क्लोन करें, इसका नाम बदलकर `javascript-tutorial-...` (भाषा के अनुसार) और [एक ईशु बनाए](https://github.com/iliakan/javascript-tutoria-en/issues/new) ताकि मैं आपको इस सूची में शामिल कर सकूं।


आप इसे किसी भी संपादक में संपादित कर सकते हैं (मार्कडाउन की तरह सिंटैक्स).
आप <https://github.com/iliakan/javascript-tutorial-server> पर जा सकते हैं ताकि आप इसे स्थानीय रूप से सरवर पर चला सकते हैं और देख सकते हैं कि यह कैसा दिखता है।

## बनावट

प्रत्येक अध्याय, लेख या कार्यों का एक फ़ोल्डर है।

फोल्डर का नाम `N-url` की तरह है, जहान `N` श्रेणीकरण के उद्देश्यों के लिए एक संख्या है और `url` एक यूआरएल भाग है जिसमें सभी सामग्रीों का नाम है।
सामग्री के प्रकार को के फ़ोल्डर अंदर फ़ाइल द्वारा परिभाषित किया जाता है:

  - `index.md` एक अध्याय है
  - `article.md` एक लेख है
  - `task.md` एक कार्य है (उपाय `solution.md` फाइल में भी प्रदान किया जाना चाहिए)

इसमें `# Main header` हर फाइल से शुरू होनी चाहिए।
