---
layout: post
title:  "NodeJS Events"
date:   29.11.2016
categories: [Javascript]
tags: 
 - javascript,nodejs
---

**EventEmitter Sınıfı**

NodeJS'de _events_ ile olayları gerçekleriz._events_ modülünün içerisinde _EventEmitter_ sınıfı bulunmaktadır.


_EventEmitter_ sınıfı ile yeni olay tanımlamaları yapabiliriz.

```javascript
  var events = require('events'); //events modülü import edildi
  var eventEmitter = new events.EventEmitter(); // eventEmitter objesi oluşturuldu    
```

```javascript
  var events = require('events');
  var eventEmitter = new events.EventEmitter();

  function method1(){
    console.log("Erken Kaybedenleriz")
  }
  function method2() {
    console.log("Daha görmedik tam güneşi");
  }

  console.log(eventEmitter.listenerCount("elnino")); //Burada kaçtane event tetiklendiğini görebiliriz.

  eventEmitter.on("elnino", method1); //on fonksiyonuyla method1 için bir event tanımlandı.

  eventEmitter.on("elnino", method2); //on fonksiyonuyla method2 için bir event tanımlandı.

  eventEmitter.removeListener("elnino",method2); //method2 event'i kaldırıldı

  eventEmitter.removeAllListeners("elnino"); //Tüm event'ler kaldırıldı.

  eventEmitter.emit("elnino"); //emit fonksiyonuyla olaylar tetiklenir.

```
to be continued...
