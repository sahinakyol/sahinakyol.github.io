---
layout: post
title:  "JavaScript OOP-0"
date:   16.10.2016 03.00.00
categories: [JavaScript]
tags: 
 - JavaScript
---

**Objects**

``` js
var object=new Object();
object.volume=30;
object.area=10;
object.calc()=function(){
  alert(10*30);
};
object.calc();
```
**Literals**

``` js
  var name={
    friends: ["foster","rigby"],
    getFriend: function(id) {
      return this.ogrenciler[id];
    }
  };
alert(name.getFriend(1));
```

**Arrays**

``` js
[a,b].concat([c,d]); //[a,b,c,d]

[1,2,3].every(function(num){return num <4}); //true döner her sayı 4 den küçüktür.

[1,2,3].filter(function(num){return num <= 2}); // 1,2 döner

[1,2,3].forEach(function(num){
  alert(num);
});

[1,2,3].indexOf(3); //2 döner

["127","0","0","1"].join('.'); //127.0.0.1

[1,2,3].map(function(num){return num*2}); //2 4 6 dönecek

var arr=[1,2,3].pop();
var arr=[1,2,3].pop();
alert(arr); //1 döner

var arr=[1,2,3].push(4);
var arr=[1,2,3].push(5);
alert(arr); //1 2 3 4 5 döner

```
``` js
[3,2,1].reduce(function(x,y){
  return x*y;
}); //(((3)*2)*1)=6 döner

```
``` js
[3,2,1].reduceRight(function(x,y){
  return x*y;
}); //(((1)*2)*3)=6 döner

```
``` js
[3,2,1].reverse(); //1,2,3 döner
```
```js

[1,2,3].shift(); // 2,3 döner

```
Daha bir çok fonksiyonu vardır incelenebilir.

**Fonksiyonlar**

Named Functions

```js
function a(){};
```

Unnamed Functions

```js
function(){};
```

Scope

```js
var global="global value";
function fonk(){
  var global="local value";
  alert(global);
}
fonk(); //local variable
alert(global); //global variable
```
Scope alanı olduğu için etkilenmedi değişkenler ayrıca 'var' anahtarını getirdiğimiz için.

Context anahtarları o scope daki elemana erişebilmeyi sağlıyor.

```js
this,self,

var name="a";
this.name // a
self.name // a
```

**Exception Handling**
Java'daki ile birebir aynıdır neredeyse,

```js
function fonk(a){
  if(a==5){
  throw Error("can't be 5");
}
return a;
}
```

```js
try {

} catch (e) {

} finally {

}
```
