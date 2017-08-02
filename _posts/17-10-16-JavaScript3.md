---
layout: post
title:  "JavaScript OOP-1"
date:   17.10.2016 17.00.00
categories: [JavaScript]
tags: 
 - JavaScript
---

**Prototypes**

 Javascriptte fonksiyonlar sınıf gibi davranabilirler.
 Fonksiyonlarımız aynı zamanda constructor'dır.

``` js
function container(){
  alert('Class');
  return "Function";
}
var fonk=container();
alert(fonk);

var cls=new container();
alert(cls);

```

``` js
var user=function(name,surname,age){
  this.name=name;
  this.surname=surname;
  this.age=age;
}
user.name // Isim değeri dönecektir.
```

**Monkey Patching**

Herhangi bir prototype'ı manipule etmemizi sağlar.

``` js
function info(name,surname,age){
  this.name=name;
  this.surname=surname;
  this.age=age;
}

info.prototype.first(){
  alert("Whatever");
}

info.prototype.first=function(){
  alert("staff");
}
var object=new info();
info.first(); //staff
```
**Instance of**

Türetidiği nesneyi belirtir.Aşağıda hem 'Car' hem de 'Object' nesnelerinden true dönüyor.

``` js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
var mycar = new Car("Honda", "Accord", 1998);
var a = mycar instanceof Car;    // returns true
var b = mycar instanceof Object; // returns true
```
**NameSpaces**

```js
var nameSpace = {
  age:100,

  name: function(){
    alert("Garona");
    this.age++;
  },

  Surname: function(){
    alert("Wolfram");
    this.age++;
  }
}
nameSpace.name(); //Garona
nameSpace.age; //101
```
Bu kodları hızlıca denemek isterseniz benim kullandığım [Mozilla Developer Edition](https://www.mozilla.org/tr/firefox/developer/) önce kurunuz(siz farklı bir browser da kullanabilirsiniz) daha sonra 'F12' tuşuna basın ve console sekmesinden denemeye başlayabilirsiniz.
