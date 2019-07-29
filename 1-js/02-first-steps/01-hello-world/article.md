# Hello, world!

शिक्षण जो आप पढ़ रहे हैं, वह कोर जावास्क्रिप्ट के बारे में है, जो प्लेटफ़ॉर्म-स्वतंत्र है। इसके अलावा, आप Node.JS और इसका उपयोग करने वाले अन्य प्लेटफ़ॉर्म सीखेंगे।

लेकिन, हमें अपनी स्क्रिप्ट को चलाने के लिए काम करने का environment चाहिए, और, सिर्फ इसलिए कि यह पुस्तक ऑनलाइन है, ब्राउज़र एक अच्छा विकल्प है। हम ब्राउज़र-विशिष्ट commands की मात्रा रखेंगे (jase ki `alert`) यदि आप किसी अन्य environment जैसे Node.JS पर ध्यान केंद्रित करने की योजना बनाते हैं, तो न्यूनतम समय मैं उन पर समय व्यतीत न करें। दूसरी ओर, ब्राउज़र विवरण में विस्तार से बताया गया है [अगला भाग](/ui) ट्यूटोरियल का.


So first, let's see how we attach a script to a webpage. For server-side environments (like Node.js), you can execute the script with a command like `"node my.js"`.


## The "script" tag

JavaScript programs can be inserted into any part of an HTML document with the help of the `<script>` tag.

For instance:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Before the script...</p>

*!*
  <script>
    alert( 'Hello, world!' );
  </script>
*/!*

  <p>...After the script.</p>

</body>

</html>
```

```online
You can run the example by clicking the "Play" button in the right-top corner of the box above.
```

The `<script>` tag contains JavaScript code which is automatically executed when the browser processes the tag.


## Modern markup

The `<script>` tag has a few attributes that are rarely used nowadays but can still be found in old code:

The `type` attribute: <code>&lt;script <u>type</u>=...&gt;</code>
: The old HTML standard, HTML4, required a script to have a `type`. Usually it was `type="text/javascript"`. It's not required anymore. Also, the modern HTML standard totally changed the meaning of this attribute. Now, it can be used for JavaScript modules. But that's an advanced topic; we'll talk about modules in another part of the tutorial.

The `language` attribute: <code>&lt;script <u>language</u>=...&gt;</code>
: This attribute was meant to show the language of the script. This attribute no longer makes sense because JavaScript is the default language. There is no need to use it.

Comments before and after scripts.
: In really ancient books and guides, you may find comments inside `<script>` tags, like this:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    This trick isn't used in modern JavaScript. These comments hid JavaScript code from old browsers that didn't know how to process the `<script>` tag. Since browsers released in the last 15 years don't have this issue, this kind of comment can help you identify really old code.


## External scripts

If we have a lot of JavaScript code, we can put it into a separate file.

Script files are attached to HTML with the `src` attribute:

```html
<script src="/path/to/script.js"></script>
```

Here, `/path/to/script.js` is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, `src="script.js"` would mean a file `"script.js"` in the current folder.

We can give a full URL as well. For instance:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js"></script>
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

We must choose either an external `<script src="…">` or a regular `<script>` with code.

The example above can be split into two scripts to work:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Summary

- We can use a `<script>` tag to add JavaScript code to a page.
- The `type` and `language` attributes are not required.
- A script in an external file can be inserted with `<script src="path/to/script.js"></script>`.


There is much more to learn about browser scripts and their interaction with the webpage. But let's keep in mind that this part of the tutorial is devoted to the JavaScript language, so we shouldn't distract ourselves with browser-specific implementations of it. We'll be using the browser as a way to run JavaScript, which is very convenient for online reading, but only one of many.
