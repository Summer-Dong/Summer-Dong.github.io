---
layout: post
title: Converting between HTML string and HTML DOM
date: 2020-05-20 19:20:23 +0900
category: javascript
---
Context: You got a HTML string and need to do parsing with the P tags, then return the parsed HTML string.
```js
const parser = new DOMParser()
const doc = parser.parseFromString(value, 'text/html')
const elementArray = [...doc.getElementsByTagName('p')]
elementArray.forEach((c, i) => {
    doc.getElementsByTagName('p')[i].innerHTML = doc
        .getElementsByTagName('p')
        [i].innerHTML.replace(/\n/g, '<br />')
})
value = new XMLSerializer().serializeToString(doc)
```
