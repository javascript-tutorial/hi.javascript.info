
# संपत्ति के झंडे और वर्णनकर्ता

जैसा कि हम जानते हैं, वस्तुएं गुणों को संग्रहीत कर सकती हैं।

अब तक, एक संपत्ति हमारे लिए एक साधारण "की-वैल्यू" जोड़ी थी। लेकिन एक वस्तु संपत्ति वास्तव में एक अधिक लचीली और शक्तिशाली चीज है।

इस अध्याय में हम अतिरिक्त कॉन्फ़िगरेशन विकल्पों का अध्ययन करेंगे, और अगले में हम देखेंगे कि अदृश्य रूप से उन्हें गेटर/सेटर फ़ंक्शन में कैसे बदला जाए।
## संपत्ति के झंडे (Property flags)


वस्तु गुण, एक **`मान`** के अलावा, तीन विशेष विशेषताएं हैं (तथाकथित "झंडे"):
- **`writable`** --यदि `सत्य` है, तो मान बदला जा सकता है, अन्यथा यह केवल-पढ़ने के लिए है।
- **`enumerable`** -- यदि `सत्य` है, तो लूप में सूचीबद्ध है, अन्यथा सूचीबद्ध नहीं है।
- **`configurable`** -- यदि `सत्य` है, तो संपत्ति को हटाया जा सकता है और इन विशेषताओं को संशोधित किया जा सकता है, अन्यथा नहीं।

हमने उन्हें अभी तक नहीं देखा, क्योंकि आम तौर पर वे दिखाई नहीं देते हैं। जब हम एक संपत्ति "सामान्य तरीके" बनाते हैं, तो वे सभी 'सत्य' होते हैं। लेकिन हम उन्हें कभी भी बदल भी सकते हैं।

सबसे पहले, आइए देखें कि उन झंडों को कैसे प्राप्त किया जाए।
प्रक्रिया [Object.getOwnPropertyDescriptor](mdn:js/Object/getOwnPropertyDescriptor) किसी संपत्ति के बारे में *पूर्ण* जानकारी पूछने की अनुमति देता है।

वाक्य रचना है:
```js
let descriptor = Object.getOwnPropertyDescriptor(obj, propertyName);
```

`obj`
: The object to get information from.

`propertyName`
: The name of the property.

लौटाया गया मूल्य एक तथाकथित "संपत्ति विवरणक" वस्तु है: इसमें मूल्य और सभी झंडे शामिल हैं।
For instance:

```js run
let user = {
  name: "John"
};

let descriptor = Object.getOwnPropertyDescriptor(user, 'name');

alert( JSON.stringify(descriptor, null, 2 ) );
/* property descriptor:
{
  "value": "John",
  "writable": true,
  "enumerable": true,
  "configurable": true
}
*/
```

झंडे को बदलने के लिए, हम उपयोग कर सकते हैं [Object.defineProperty](mdn:js/Object/defineProperty).

वाक्य रचना है:

```js
Object.defineProperty(obj, propertyName, descriptor)
```

`obj`, `propertyName`
: The object and its property to apply the descriptor.

`descriptor`
: Property descriptor object to apply.

यदि संपत्ति मौजूद है, तो `defineProperty` इसके झंडे को अपडेट करता है। अन्यथा, यह दिए गए मूल्य और झंडे के साथ संपत्ति बनाता है; उस स्थिति में, यदि ध्वज की आपूर्ति नहीं की जाती है, तो इसे 'झूठा' मान लिया जाता है।
उदाहरण के लिए, यहां एक संपत्ति `नाम` सभी झूठे झंडों के साथ बनाई गई है:
```js run
let user = {};

*!*
Object.defineProperty(user, "name", {
  value: "John"
});
*/!*

let descriptor = Object.getOwnPropertyDescriptor(user, 'name');

alert( JSON.stringify(descriptor, null, 2 ) );
/*
{
  "value": "John",
*!*
  "writable": false,
  "enumerable": false,
  "configurable": false
*/!*
}
 */
```

इसकी तुलना ऊपर "सामान्य रूप से बनाए गए" `user.name` से करें: अब सभी फ़्लैग झूठे हैं। अगर हम यही नहीं चाहते हैं तो हम उन्हें 'डिस्क्रिप्टर' में 'सत्य' पर सेट करना बेहतर समझते हैं।
आइए अब उदाहरण के द्वारा झंडों के प्रभाव को देखें।
## गैर-लिखने योग्य (Non-writable)

Let's make `user.name` non-writable (can't be reassigned) by changing `writable` flag:

```js run
let user = {
  name: "John"
};

Object.defineProperty(user, "name", {
*!*
  writable: false
*/!*
});

*!*
user.name = "Pete"; // Error: Cannot assign to read only property 'name'
*/!*
```

Now no one can change the name of our user, unless they apply their own `defineProperty` to override ours.

```smart header="Errors appear only in strict mode"
In the non-strict mode, no errors occur when writing to non-writable properties and such. But the operation still won't succeed. Flag-violating actions are just silently ignored in non-strict.
```

Here's the same example, but the property is created from scratch:

```js run
let user = { };

Object.defineProperty(user, "name", {
*!*
  value: "John",
  // for new properties we need to explicitly list what's true
  enumerable: true,
  configurable: true
*/!*
});

alert(user.name); // John
user.name = "Pete"; // Error
```

## Non-enumerable

Now let's add a custom `toString` to `user`.

Normally, a built-in `toString` for objects is non-enumerable, it does not show up in `for..in`. But if we add a `toString` of our own, then by default it shows up in `for..in`, like this:

```js run
let user = {
  name: "John",
  toString() {
    return this.name;
  }
};

// By default, both our properties are listed:
for (let key in user) alert(key); // name, toString
```

If we don't like it, then we can set `enumerable:false`. Then it won't appear in a `for..in` loop, just like the built-in one:

```js run
let user = {
  name: "John",
  toString() {
    return this.name;
  }
};

Object.defineProperty(user, "toString", {
*!*
  enumerable: false
*/!*
});

*!*
// Now our toString disappears:
*/!*
for (let key in user) alert(key); // name
```

Non-enumerable properties are also excluded from `Object.keys`:

```js
alert(Object.keys(user)); // name
```

## Non-configurable

The non-configurable flag (`configurable:false`) is sometimes preset for built-in objects and properties.

A non-configurable property can not be deleted.

For instance, `Math.PI` is non-writable, non-enumerable and non-configurable:

```js run
let descriptor = Object.getOwnPropertyDescriptor(Math, 'PI');

alert( JSON.stringify(descriptor, null, 2 ) );
/*
{
  "value": 3.141592653589793,
  "writable": false,
  "enumerable": false,
  "configurable": false
}
*/
```
So, a programmer is unable to change the value of `Math.PI` or overwrite it.

```js run
Math.PI = 3; // Error

// delete Math.PI won't work either
```

Making a property non-configurable is a one-way road. We cannot change it back with `defineProperty`.

To be precise, non-configurability imposes several restrictions on `defineProperty`:
1. Can't change `configurable` flag.
2. Can't change `enumerable` flag.
3. Can't change `writable: false` to `true` (the other way round works).
4. Can't change `get/set` for an accessor property (but can assign them if absent).

**The idea of "configurable: false" is to prevent changes of property flags and its deletion, while allowing to change its value.**

Here `user.name` is non-configurable, but we can still change it (as it's writable):

```js run
let user = {
  name: "John"
};

Object.defineProperty(user, "name", {
  configurable: false
});

user.name = "Pete"; // works fine
delete user.name; // Error
```

And here we make `user.name` a "forever sealed" constant:

```js run
let user = {
  name: "John"
};

Object.defineProperty(user, "name", {
  writable: false,
  configurable: false
});

// won't be able to change user.name or its flags
// all this won't work:
user.name = "Pete";
delete user.name;
Object.defineProperty(user, "name", { value: "Pete" });
```


## Object.defineProperties

There's a method [Object.defineProperties(obj, descriptors)](mdn:js/Object/defineProperties) that allows to define many properties at once.

The syntax is:

```js
Object.defineProperties(obj, {
  prop1: descriptor1,
  prop2: descriptor2
  // ...
});
```

For instance:

```js
Object.defineProperties(user, {
  name: { value: "John", writable: false },
  surname: { value: "Smith", writable: false },
  // ...
});
```

So, we can set many properties at once.

## Object.getOwnPropertyDescriptors

To get all property descriptors at once, we can use the method [Object.getOwnPropertyDescriptors(obj)](mdn:js/Object/getOwnPropertyDescriptors).

Together with `Object.defineProperties` it can be used as a "flags-aware" way of cloning an object:

```js
let clone = Object.defineProperties({}, Object.getOwnPropertyDescriptors(obj));
```

Normally when we clone an object, we use an assignment to copy properties, like this:

```js
for (let key in user) {
  clone[key] = user[key]
}
```

...लेकिन वह झंडे की नकल नहीं करता है। इसलिए यदि हम एक "बेहतर" क्लोन चाहते हैं तो `Object.defineProperties` को प्राथमिकता दी जाती है।

एक और अंतर यह है कि `for..in` प्रतीकात्मक गुणों को अनदेखा करता है, लेकिन `ऑब्जेक्ट.getOwnPropertyDescriptors` प्रतीकात्मक वाले सहित सभी * संपत्ति वर्णनकर्ता देता है।

## किसी वस्तु को विश्व स्तर पर सील करना

संपत्ति विवरणक व्यक्तिगत गुणों के स्तर पर काम करते हैं।

ऐसी विधियाँ भी हैं जो *संपूर्ण* वस्तु तक पहुँच को सीमित करती हैं:

[Object.preventExtensions(obj)](mdn:js/Object/preventExtensions)
: Forbids the addition of new properties to the object.

[Object.seal(obj)](mdn:js/Object/seal)
: Forbids adding/removing of properties. Sets `configurable: false` for all existing properties.

[Object.freeze(obj)](mdn:js/Object/freeze)
: Forbids adding/removing/changing of properties. Sets `configurable: false, writable: false` for all existing properties.

और उनके लिए परीक्षण भी हैं:
[Object.isExtensible(obj)](mdn:js/Object/isExtensible)
: Returns `false` if adding properties is forbidden, otherwise `true`.

[Object.isSealed(obj)](mdn:js/Object/isSealed)
: Returns `true` if adding/removing properties is forbidden, and all existing properties have `configurable: false`.

[Object.isFrozen(obj)](mdn:js/Object/isFrozen)
: Returns `true` if adding/removing/changing properties is forbidden, and all current properties are `configurable: false, writable: false`.

व्यवहार में इन विधियों का उपयोग शायद ही कभी किया जाता है।
