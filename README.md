# जावास्क्रिप्ट की शिक्षा

यह भंडार आधुनिक जावास्क्रिप्ट की शिक्षा की सामग्री मेज़बानी करता है जो [https://javascript.info](https://javascript.info) पर प्रकाशित है।

## अनुवाद

(अंग्रेजी वर्णानुक्रम में):

| भाषा | Github | मुख्या अनुवाद लेखक | अनूदित (%) | प्रकाशित |
|----------|--------|-------------------|-----------------|-----------|
| चीनी | https://github.com/xitu/javascript-tutorial-zh | @leviding | ![](http://translate-hook.javascript.info/stats/zh.svg?1) | https://zh.javascript.info |
| जापानी | https://github.com/KenjiI/javascript-tutorial-ja | @KenjiI | ![](http://translate-hook.javascript.info/stats/ja.svg?1) | https://ja.javascript.info |
| रोमानियाई | https://github.com/lighthousand/javascript-tutorial-ro | @lighthousand | started | - |
| रूसी | https://github.com/iliakan/javascript-tutorial-ru | @iliakan | * | https://learn.javascript.ru |
| तुर्की | https://github.com/sahinyanlik/javascript-tutorial-tr | @sahinyanlik | ![](http://translate-hook.javascript.info/stats/tr.svg?1) | - |



`*` – the previous version is published in Russian, need to backport/translate the new one from English.

If you'd like to translate it into your language, please clone the repository, change its name to `javascript-tutorial-...` (by the language) and [create an issue](https://github.com/iliakan/javascript-tutoria-en/issues/new) for me to add you to the list.

You can edit the text in any editor (markdown-like syntax). The server to run the tutorial locally and see how it looks is at <https://github.com/iliakan/javascript-tutorial-server>.  



## Structure

Every chapter, article or a task has its folder.

The folder is named like `N-url`, where `N` is a number for the sorting purposes and `url` is the URL part with title of the material.

The type of the material is defined by the file inside the folder:

  - `index.md` stands for a chapter
  - `article.md` stands for an article
  - `task.md` stands for a task (solution must be provided in `solution.md` file aswell)

Each of these files starts from the `# Main header`.
