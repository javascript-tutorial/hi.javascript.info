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

फोल्डर का नाम `N-url` की तरह है, where `N` is a number for the sorting purposesउद्देश्यों and `url` is the URL part with title of the material.

The type of the material is defined by the file inside the folder:

  - `index.md` stands for a chapter
  - `article.md` stands for an article
  - `task.md` stands for a task (solution must be provided in `solution.md` file aswell)

Each of these files starts from the `# Main header`.
