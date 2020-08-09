# कोड संरचना

पहली चीज जो हम अध्ययन करेंगे, वह है कोड की नींव की ईंटें (building blocks)।

## उक्ति (Statements) [#उक्ति]

उक्ति कार्य करने वाले वाक्य रचना और आदेश हैं।

हमने पहले ही एक उक्ति देखा है, `alert('हेलो विश्व!')`, "हेलो विश्व" जो संदेश दिखाता है।

हम अपने कोड में जितने चाहें उतने उक्ति दे सकते हैं। उक्ति अर्धविराम से अलग किए जा सकते हैं।

उदाहरण के लिए, यहां हमने "हेलो विश्व!" को दो अलर्ट में विभाजित किया है:

```js run no-beautify
alert('हेलो!'); alert('विश्व');
```

आमतौर पर कोड को अधिक पठनीय बनाने के लिए अलग-अलग लाइनों पर उक्ति लिखे जाते हैं:

```js run no-beautify
alert('हेलो');
alert('विश्व');
```

## अर्धविराम [#अर्धविराम]

लाइन ब्रेक मौजूद होने पर अधिकांश मामलों में अर्धविराम छोड़ा जा सकता है।

यह कोड काम करेगा:

```js run no-beautify
alert('हेलो')
alert('विश्व')
```

यहाँ, जावास्क्रिप्ट लाइन ब्रेक (एक पंक्ति का अंत) को "निहित" अर्धविराम के रूप में मानता है। इसे [automatic semicolon insertion](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) कहा जाता है। 

**ज्यादातर मामलों में, एक नई पंक्ति का अर्थ अर्धविराम है। लेकिन "ज्यादातर मामलों में" का अर्थ "हमेशा" नहीं होता है!**

There are cases when a newline does not mean a semicolon. For example:

```js run no-beautify
alert(3 +
1
+ 2);
```

The code outputs `6` because JavaScript does not insert semicolons here. It is intuitively obvious that if the line ends with a plus `"+"`, then it is an "incomplete expression", so the semicolon is not required. And in this case that works as intended.

**But there are situations where JavaScript "fails" to assume a semicolon where it is really needed.**

Errors which occur in such cases are quite hard to find and fix.

````smart header="An example of an error"
If you're curious to see a concrete example of such an error, check this code out:

```js run
[1, 2].forEach(alert)
```

No need to think about the meaning of the brackets `[]` and `forEach` yet. We'll study them later. For now, just remember the result of the code: it shows `1` then `2`.

Now, let's add an `alert` before the code and *not* finish it with a semicolon:

```js run no-beautify
alert("There will be an error")

[1, 2].forEach(alert)
```

Now if we run the code, only the first `alert` is shown and then we have an error!

But everything is fine again if we add a semicolon after `alert`:
```js run
alert("All fine now");

[1, 2].forEach(alert)  
```

Now we have the "All fine now" message followed by `1` and `2`.


The error in the no-semicolon variant occurs because JavaScript does not assume a semicolon before square brackets `[...]`.

So, because the semicolon is not auto-inserted, the code in the first example is treated as a single statement. Here's how the engine sees it:

```js run no-beautify
alert("There will be an error")[1, 2].forEach(alert)
```

But it should be two separate statements, not one. Such a merging in this case is just wrong, hence the error. This can happen in other situations.
````

We recommend putting semicolons between statements even if they are separated by newlines. This rule is widely adopted by the community. Let's note once again -- *it is possible* to leave out semicolons most of the time. But it's safer -- especially for a beginner -- to use them.

## Comments [#code-comments]

As time goes on, programs become more and more complex. It becomes necessary to add *comments* which describe what the code does and why.

Comments can be put into any place of a script. They don't affect its execution because the engine simply ignores them.

**One-line comments start with two forward slash characters `//`.**

The rest of the line is a comment. It may occupy a full line of its own or follow a statement.

Like here:
```js run
// This comment occupies a line of its own
alert('Hello');

alert('World'); // This comment follows the statement
```

**Multiline comments start with a forward slash and an asterisk <code>/&#42;</code> and end with an asterisk and a forward slash <code>&#42;/</code>.**

Like this:

```js run
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

The content of comments is ignored, so if we put code inside <code>/&#42; ... &#42;/</code>, it won't execute.

Sometimes it can be handy to temporarily disable a part of code:

```js run
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl` and `key:Option` instead of `key:Shift`.
```

````warn header="Nested comments are not supported!"
There may not be `/*...*/` inside another `/*...*/`.

Such code will die with an error:

```js run no-beautify
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
````

Please, don't hesitate to comment your code.

Comments increase the overall code footprint, but that's not a problem at all. There are many tools which minify code before publishing to a production server. They remove comments, so they don't appear in the working scripts. Therefore, comments do not have negative effects on production at all.

Later in the tutorial there will be a chapter <info:code-quality> that also explains how to write better comments.
