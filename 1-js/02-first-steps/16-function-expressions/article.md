# Function एक्सप्रेशन

Javascript में, एक function "जादुई भाषा संरचना" नहीं है, बल्कि एक विशेष प्रकार का मूल्य है।

हमने पहले जिस सिंटैक्स का उपयोग किया था, उसे *function घोषणा* कहा जाता है:

```js
function sayHi() {
  alert( "Hello" );
}
```

function बनाने के लिए एक और सिंटैक्स है जिसे *function एक्सप्रेशन* कहा जाता है।

यह इस तरह दीखता है:

```js
let sayHi = function() {
  alert( "Hello" );
};
```

यहां, function को किसी अन्य मान की तरह, स्पष्ट रूप से बनाया गया है और variable को असाइन किया गया है। कोई फर्क नहीं पड़ता कि function को कैसे परिभाषित किया गया है, यह केवल 'sayHi' variable में संग्रहीत एक मान है।

इन कोड नमूनों का अर्थ एक ही है: "एक function बनाएं और इसे variable `sayHi` में डालें"।

हम `alert` का उपयोग करके उस मूल्य को प्रिंट भी कर सकते हैं:

```js run
function sayHi() {
  alert( "Hello" );
}

*!*
alert( sayHi ); // shows the function code
*/!*
```

कृपया ध्यान दें कि अंतिम पंक्ति function नहीं चलाती है, क्योंकि `sayHi` के बाद कोई कोष्ठक नहीं है। ऐसी प्रोग्रामिंग भाषाएं हैं जहां किसी function नाम का कोई उल्लेख इसके निष्पादन का कारण बनता है, लेकिन Javascript ऐसा नहीं है।

Javascript में, एक function एक मान है, इसलिए हम इसे एक मान के रूप में व्यवहार कर सकते हैं। उपरोक्त कोड इसका स्ट्रिंग प्रतिनिधित्व दिखाता है, जो स्रोत कोड है।

निश्चित रूप से, एक function  एक विशेष मूल्य है, इस अर्थ में कि हम इसे `sayHi()` की तरह कॉल कर सकते हैं।

लेकिन यह फिर भी एक मूल्य है। इसलिए हम इसके साथ अन्य प्रकार के मूल्यों की तरह काम कर सकते हैं।

हम एक function को दूसरे variable में कॉपी कर सकते हैं:

```js run no-beautify
function sayHi() {   // (1) create
  alert( "Hello" );
}

let func = sayHi;    // (2) copy

func(); // Hello     // (3) run the copy (it works)!
sayHi(); // Hello    //     this still works too (why wouldn't it)
```

ऊपर विस्तार से यह होता है:

1. Function घोषणा `(1)` function बनाता है और इसे `sayHi` नाम के variable में डालता है।
2. लाइन `(2)` इसे variable `func` में कॉपी करती है। कृपया फिर से ध्यान दें: `sayHi` के बाद कोई कोष्ठक नहीं है। अगर वहाँ होता, तो `func = sayHi()` *कॉल का परिणाम* `sayHi()` को `func` में लिखता, न कि *function* `sayHi` को ही।
3. अब function को `sayHi()` और `func()` दोनों के रूप में कॉल किया जा सकता है।

ध्यान दें कि हम पहली पंक्ति में `sayHi` घोषित करने के लिए एक function एक्सप्रेशन का भी इस्तेमाल कर सकते थे:

```js
let sayHi = function() {
  alert( "Hello" );
};

let func = sayHi;
// ...
```

सब कुछ वैसा ही काम करेगा।


````smart header="अंत में अर्धविराम क्यों है?"
आपको आश्चर्य हो सकता है कि function एक्सप्रेशन के अंत में अर्धविराम क्यों होता है, लेकिन function डिक्लेरेशन में यह नहीं होता है:

```js
function sayHi() {
  // ...
}

let sayHi = function() {
  // ...
}*!*;*/!*
```

उत्तर सीधा है:
- कोड ब्लॉक और सिंटैक्स संरचनाओं के अंत में `;` की कोई आवश्यकता नहीं है जो उनका उपयोग करते हैं जैसे `if {...}`, `के लिए { }`, `फ़ंक्शन f { }` आदि।
- स्टेटमेंट के अंदर एक function एक्सप्रेशन का उपयोग किया जाता है: `let sayHi = ...;`, मान के रूप में। यह एक कोड ब्लॉक नहीं है, बल्कि एक असाइनमेंट है। स्टेटमेंट के अंत में अर्धविराम `;` की सिफारिश की जाती है, भले ही मूल्य कुछ भी हो। तो यहां अर्धविराम function अभिव्यक्ति से संबंधित नहीं है, यह केवल स्टेटमेंट को समाप्त करता है।
````

## कॉलबैक functions

आइए function को मानों के रूप में पास करने और function एक्सप्रेशन का उपयोग करने के अधिक उदाहरण देखें।

हम तीन parameters के साथ `ask(question, yes, no)` function लिखेंगे:

`question`
: प्रश्न का पाठ

`yes`
: यदि उत्तर "हां" है तो function चलेगा

`no`
: यदि उत्तर "नहीं" है तो function चलेगा

Function को `प्रश्न` पूछना चाहिए और, उपयोगकर्ता के उत्तर के आधार पर, `yes()` या `no()` पर कॉल करना चाहिए:

```js run
*!*
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}
*/!*

function showOk() {
  alert( "You agreed." );
}

function showCancel() {
  alert( "You canceled the execution." );
}

// usage: functions showOk, showCancel are passed as arguments to ask
ask("Do you agree?", showOk, showCancel);
```

In practice, such functions are quite useful. The major difference between a real-life `ask` and the example above is that real-life functions use more complex ways to interact with the user than a simple `confirm`. In the browser, such function usually draws a nice-looking question window. But that's another story.

**The arguments `showOk` and `showCancel` of `ask` are called *callback functions* or just *callbacks*.**

The idea is that we pass a function and expect it to be "called back" later if necessary. In our case, `showOk` becomes the callback for "yes" answer, and `showCancel` for "no" answer.

We can use Function Expressions to write the same function much shorter:

```js run no-beautify
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}

*!*
ask(
  "Do you agree?",
  function() { alert("You agreed."); },
  function() { alert("You canceled the execution."); }
);
*/!*
```

Here, functions are declared right inside the `ask(...)` call. They have no name, and so are called *anonymous*. Such functions are not accessible outside of `ask` (because they are not assigned to variables), but that's just what we want here.

Such code appears in our scripts very naturally, it's in the spirit of JavaScript.

```smart header="A function is a value representing an \"action\""
Regular values like strings or numbers represent the *data*.

A function can be perceived as an *action*.

We can pass it between variables and run when we want.
```


## Function Expression vs Function Declaration

Let's formulate the key differences between Function Declarations and Expressions.

First, the syntax: how to differentiate between them in the code.

- *Function Declaration:* a function, declared as a separate statement, in the main code flow.

    ```js
    // Function Declaration
    function sum(a, b) {
      return a + b;
    }
    ```
- *Function Expression:* a function, created inside an expression or inside another syntax construct. Here, the function is created at the right side of the "assignment expression" `=`:

    ```js
    // Function Expression
    let sum = function(a, b) {
      return a + b;
    };
    ```

The more subtle difference is *when* a function is created by the JavaScript engine.

**A Function Expression is created when the execution reaches it and is usable only from that moment.**

Once the execution flow passes to the right side of the assignment `let sum = function…` -- here we go, the function is created and can be used (assigned, called, etc. ) from now on.

Function Declarations are different.

**A Function Declaration can be called earlier than it is defined.**

For example, a global Function Declaration is visible in the whole script, no matter where it is.

That's due to internal algorithms. When JavaScript prepares to run the script, it first looks for global Function Declarations in it and creates the functions. We can think of it as an "initialization stage".

And after all Function Declarations are processed, the code is executed. So it has access to these functions.

For example, this works:

```js run refresh untrusted
*!*
sayHi("John"); // Hello, John
*/!*

function sayHi(name) {
  alert( `Hello, ${name}` );
}
```

The Function Declaration `sayHi` is created when JavaScript is preparing to start the script and is visible everywhere in it.

...If it were a Function Expression, then it wouldn't work:

```js run refresh untrusted
*!*
sayHi("John"); // error!
*/!*

let sayHi = function(name) {  // (*) no magic any more
  alert( `Hello, ${name}` );
};
```

Function Expressions are created when the execution reaches them. That would happen only in the line `(*)`. Too late.

Another special feature of Function Declarations is their block scope.

**In strict mode, when a Function Declaration is within a code block, it's visible everywhere inside that block. But not outside of it.**

For instance, let's imagine that we need to declare a function `welcome()` depending on the `age` variable that we get during runtime. And then we plan to use it some time later.

If we use Function Declaration, it won't work as intended:

```js run
let age = prompt("What is your age?", 18);

// conditionally declare a function
if (age < 18) {

  function welcome() {
    alert("Hello!");
  }

} else {

  function welcome() {
    alert("Greetings!");
  }

}

// ...use it later
*!*
welcome(); // Error: welcome is not defined
*/!*
```

That's because a Function Declaration is only visible inside the code block in which it resides.

Here's another example:

```js run
let age = 16; // take 16 as an example

if (age < 18) {
*!*
  welcome();               // \   (runs)
*/!*
                           //  |
  function welcome() {     //  |  
    alert("Hello!");       //  |  Function Declaration is available
  }                        //  |  everywhere in the block where it's declared
                           //  |
*!*
  welcome();               // /   (runs)
*/!*

} else {

  function welcome() {    
    alert("Greetings!");
  }
}

// Here we're out of curly braces,
// so we can not see Function Declarations made inside of them.

*!*
welcome(); // Error: welcome is not defined
*/!*
```

What can we do to make `welcome` visible outside of `if`?

The correct approach would be to use a Function Expression and assign `welcome` to the variable that is declared outside of `if` and has the proper visibility.

This code works as intended:

```js run
let age = prompt("What is your age?", 18);

let welcome;

if (age < 18) {

  welcome = function() {
    alert("Hello!");
  };

} else {

  welcome = function() {
    alert("Greetings!");
  };

}

*!*
welcome(); // ok now
*/!*
```

Or we could simplify it even further using a question mark operator `?`:

```js run
let age = prompt("What is your age?", 18);

let welcome = (age < 18) ?
  function() { alert("Hello!"); } :
  function() { alert("Greetings!"); };

*!*
welcome(); // ok now
*/!*
```


```smart header="When to choose Function Declaration versus Function Expression?"
As a rule of thumb, when we need to declare a function, the first to consider is Function Declaration syntax. It gives more freedom in how to organize our code, because we can call such functions before they are declared.

That's also better for readability, as it's easier to look up `function f(…) {…}` in the code than `let f = function(…) {…};`. Function Declarations are more "eye-catching".

...But if a Function Declaration does not suit us for some reason, or we need a conditional declaration (we've just seen an example), then Function Expression should be used.
```

## Summary

- Functions are values. They can be assigned, copied or declared in any place of the code.
- If the function is declared as a separate statement in the main code flow, that's called a "Function Declaration".
- If the function is created as a part of an expression, it's called a "Function Expression".
- Function Declarations are processed before the code block is executed. They are visible everywhere in the block.
- Function Expressions are created when the execution flow reaches them.

In most cases when we need to declare a function, a Function Declaration is preferable, because it is visible prior to the declaration itself. That gives us more flexibility in code organization, and is usually more readable.

So we should use a Function Expression only when a Function Declaration is not fit for the task. We've seen a couple of examples of that in this chapter, and will see more in the future.
