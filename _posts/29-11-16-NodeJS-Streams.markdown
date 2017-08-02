---
layout: post
title:  "NodeJS Streams"
date:   29.11.2016 22:23
categories: [Javascript]
tags: 
 - javascript,nodejs
---

**Streams**

Akış anlamına gelen veri aktarımını yapabildiğimiz yapıdır.
_streams_ EventEmitter sınıfı gibi olay temelli çalışır.

**Read Stream**

```javascript
  var fs = require('fs'); //fs modül import edildi.
  var path = require('path'); //path modül import edildi.
  var filePath = __dirname + path.sep + "file_Path.txt"; //dosyanın_bulunduğu_dizin + / + dosya_ismi
  var readableStream = fs.createReadStream(filePath); //readableStream oluşturuldu
  var myData = ""; //String nesne oluşturuldu
  readableStream.on('data',(chunk) => { // chunk nesnesi buffer taşır
    console.log('readable:', readableStream.read()); //null döner
    myData+= chunk; //buffer aracılığıyla nesnemize atılır okunan değerler
  });

  readableStream.on('end', () => {
    console.log(myData); //sonuna gelinmişse yazılır.
  });
```
_stream_ nesnesinden okunan veri _buffer_ nesnesidir.

**Read-Write Stream**

```javascript
var fs = require('fs');
var path = require('path');
var filePathFrom = __dirname + path.sep + "file_PathFrom.txt";
var filePathTo = __dirname + path.sep + "file_PathTo.txt";

var readableStream = fs.createReadStream(filePathFrom); //okuma akışı
var writeableStream = fs.createWriteStream(filePathTo); //yazma akışı

readableStream.on('data',(chunk) => { //chunk'a alınan data write ile yazılır.
  writeableStream.write(chunk);
});
```

**Pipe**

```javascript
var fs = require('fs');
var path = require('path');
var filePathFrom = __dirname + path.sep + "file_PathFrom.txt";
var filePathTo = __dirname + path.sep + "file_PathTo.txt";

var readableStream = fs.createReadStream(filePathFrom);
var writeableStream = fs.createWriteStream(filePathTo);

readableStream.pipe(writeableStream); //yukarıdaki kod ile aynı işi yapmaktadır.Veri akışı yapılmaktadır
readableStream.pause(); //veri akışı duraklatılır.
readableStream.resume(); //veri akışı devam ettirilir.
readableStream.unpipe(); //veri akışı kesilir.
```

Genel anlamda şöyle bir yorum yapılabilir kodlar kendini anlattığı için ek bir yorum yapmıyorum,ancak daha derinlemesine irdelenebilir.Bu yazılarımı zaman içinde yetkinliğim arttıkça değiştireceğim...

to be continued...
