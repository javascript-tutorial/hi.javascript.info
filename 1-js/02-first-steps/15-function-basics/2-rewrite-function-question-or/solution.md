Using a question mark operator `'?'`:
प्रश्न चिह्न ऑपरेटर का उपयोग करते हुए `?`:

```js
function checkAge(age) {
  return (age > 18) ? true : confirm('Did parents allow you?');
}
```

Using OR `||` (the shortest variant):
OR ऑपरेटर का उपयोग करते हुए `||` (सबसे छोटा संस्करण)

```js
function checkAge(age) {
  return (age > 18) || confirm('Did parents allow you?');
}
```

Note that the parentheses around `age > 18` are not required here. They exist for better readabiltiy.
ध्यान दें कि यहां `age > 18` के आसपास के कोष्ठकों की आवश्यकता नहीं है। वे बेहतर पठनीयता के लिए मौजूद हैं।
