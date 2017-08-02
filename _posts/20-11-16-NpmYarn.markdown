---
layout: post
title:  "Yarn Kullanımı"
date:   20.11.2016
categories: [Javascript]
tags: 
 - javascript
---

**Yarn Nedir**

Facebook'un geçtiğimiz günlerde open source ettiği npm ile aynı ve senkronize çalışan paket yöneticisidir.

Aslında anlattığım herşeyi npm'le de yapabilirsiniz.Peki herşey aynı ise neden yarn'ı tercih ediyorum?

Hiç şüphesiz Yarn'ın NPM'e göre bazı üstünlükleri var;

Hız, Güvenlik, Offline Mode, Deterministic, Network Resilince...

**Offline Mode** ile eğer bir paket daha önce yüklenmişse offline olsak dahi tekrar yükleyebiliriz.

**Deterministic** bağımlılıklarımız her makine için aynı sırada yükleniyor.

**Network Resilince** herhangi bir paket hata oluşması durumunda diğer paketleri etkilemiyor.

**Multiple Registries** herhangi bir paketi npm'den kurmanız durumunda hiçbir sorun yaşanmaz.

```js
  $ yarn install paket
  $ node
  > var paket = require('paket');
  > ...
  $ yarn ls // Modüller listeleniyor
  $ yarn remove paket //paketi kaldır
  $ yarn init //yarn paket oluşturma
```

__yarn init__ komutu verdiğimizde json formatında bize bir dosya oluşturacaktır.
Içerisinde name,version,dependicies... gibi paketin bilgilerini içerir.

**JSON**

__xml__ gibi metin tabanlı dosya formatıdır.Kullanım amacı iki makine arası iletişimde ortak dil'e sahip olabilmek.

```json
{
  "name" : "leaf",
  "version" : "0.0.1",
  "dependicies" : {
    "paket" : "*"
  }
}
```
to be continued...
