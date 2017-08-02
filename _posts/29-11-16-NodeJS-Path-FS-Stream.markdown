---
layout: post
title:  "NodeJS Path,Fs ve IO Işlemleri"
date:   29.11.2016 20:37
categories: [Javascript]
tags: 
 - javascript,nodejs
---

**Path Modülü**

_Path_ modülü sayesinde herhangi bir sistemin dosyalama sisteminden bağımsız,
dosya yolu istemi yapılabilir.

```javascript
  var path = require('path'); //path modülü import edildi.
  var file = "./Desktop/abdalJS/file_Path.txt" // dosya yolu belirtildi.

  var fileName = path.basename(file); //dosya ismi yazdırılır.

  var fileExtension = path.extname(file); //dosya uzantısı yazdırılır.

  var dirname = path.dirname(file); // dosya konumu belirtilir

  var filePathParse = path.parse('/home/user/dir/file_Path.txt'); //dosya yolunun tüm bilgilerini yazdırır.

  console.log(fileName);
  console.log(fileExtension);
  console.log(dirname);
  console.log(filePathParse);
```
**FS Modülü ve IO Işlemleri**

_fs_ modülü ile dosya sistemi işlemleri senkron ve asenkron yapılabilir.

**Dosya Okuma**

```javascript
    var fs = require('fs'); //fs modülü import edildi.
    var file = "./Desktop/abdalJS/file_Path.txt" // dosya yolu belirtildi.

    fs.readFile(file, (err, data) => { //dosya okuma
    if (err) throw err;
    console.log(data.toString());
  });
```
**Dosya Açma**

```javascript
    var fs = require('fs'); //fs modülü import edildi.
    var file = "./Desktop/abdalJS/file_Path.txt" // dosya yolu belirtildi.

    fs.open(file, 'r', (err, fd) => { //dosya açma işlemi 'r' parametresi ile açılıyor
    if (err) {
      if (err.code === "ENOENT") {
        console.error('Dosya bulunamadı!');
        return;
      } else {
        throw err;
      }
    }
    readMyData(fd);
  });
```
**Dosya Yazma**

```javascript
    var fs = require('fs'); //fs modülü import edildi.
    var file = "./Desktop/abdalJS/file_Path.txt" // dosya yolu belirtildi.    

    fs.writeFile(file, 'Şifa istemem balından.', (err) => { //Dosya'ya yazıldı.
      if (err) throw err;
        console.log('Başarılı!');
      });
```
**Dosya Kapatma**

```javascript
    var fs = require('fs'); //fs modülü import edildi.
    var file = "./Desktop/abdalJS/file_Path.txt" // dosya yolu belirtildi.

    fs.close(fd,(err) => { //dosya kapatma işlemi
      if (err) {
        return console.error(err);
      } else {
        console.log("Dosya Kapatıldı!");
      }
    });
```














to be continued...
