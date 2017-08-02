---
layout: post
title:  "HTML5 CSS3"
date:   15.10.2016
categories: [HTML5]
tags: 
 - HTML5,CSS3
---

Eksik olduğumu düşündüğüm temel şeyler ile ilgili bitirmeyeceğim blogpost'um olacak;

``` css
    width:100%
    height:100%
```
Gibi boyutlandırmaları % cinsinden verilmeli bu responsive yapıyı bozmamızı engeller.

```css
    width: calc(100% - 10px);
```
Calc fx ile tarayıcının her boyutunda 10px boyutu sabit tutabiliriz.

``` js
    window.onload=function(){ document.getElementById("xxx").style.width="10px";}
    <img id="xxx" ... />
```
JavaScript ile de yapılabilir CSS de yapılan işlemler.

``` js
    function bisiler(){
                              var en=window.innerWidth;
                              var boy=window.outerWidth;
                              document.getElementById("xxx").style.width=en;
                            }
    window.onload=bisiler;
    window.onresize=bisiler;     
    <img id="xxx" ... />
```


```css
    user-scalable=no
```
Zoom olayını kapatabiliriz.

```css
  .{margin-top: 4px
      @media all and(max-width:400px){ margin-top:5px;}
  }

```

@media etiketi ile duruma göre tanımlama yapabiliriz.


```css
  @media handheld and (orientation:landscape);  
  @media handheld and (orientation:portrait);
  @media print(...);
```

@media etiketinin birçok farklı parametresi vardır handheld,print,screen gibi.

```css
  letter-spacing ve word spacing ile bosluklar verebiliriz.
```
SVG Iconlarını [Google Material Icons](https://design.google.com/) sitesinden indirebiliriz.
SVG'ler png,jpg formatlı dosyalara nazaran boyutu düşük dosyalardır.

Resimler bizim sitemizin yüklenmesinde yavaşlığın en büyük kısmını oluşturur.
Bundan mütevellit olabildiğince resimleri sıkıştırarak kullanmalıyız.

HTML5'da karşı cihazda 5 mb'lık depolama yapabiliriz.

``` html
      localStorage.setItem("değişken", "B");
      alert(localStorage.getItem("değişken"));
      localStorage.removeItem("değişken");
```

``` html

    <ul style="list-style-type:disc" >
      <li></li>  
    </ul>

    <ul style="list-style-type:circle" >
      <li></li>  
    </ul>

    <ul style="list-style-type:square" >
      <li></li>  
    </ul>

    <ul style="list-style-type:none" >
      <li></li>  
    </ul>

    <!--Işaretlemeler değişiklik gösteriyor.
```

``` html
  <img src="url" width="%50" height="%50" alt="description"/>

  <!--Resim eklemeyi sağlar.-->
```

```html
  <table>
    <tr>
      <th>"Something"</th>    
    </tr>

    <tr>
      <td>"Something"</td>
    </tr>  
  </table>
  <!--Text ifadeleri tablo olarak gösterir.-->
```

``` html
  <form action="xxx" method="post">
    <div>
      <label for="name">Name</label>
      <input name="name" type="text"/>
    </div>

    <div>
      <label for="password">Password</label>
      <input name="password" type="password"/>
    </div>

    <input type="submit"/>
    <button>Sign In</button>
    <input type="checkbox"/>
    <input type="radio"/>
    <select>
      <option>2017</option>
      <option>2018</option>
      <option>2019</option>
  </form>
  <!--Genel form component ve input yapısı.-->
```
```html
  <link rel="stylesheet" href="stylesheets/style.css">
  <!--Herhangi bir html dosyası içerisinde css link vermemizi sağlar.-->
```
```css
  body{
    background:black;
  }

  h1{
    color: white;
    border: 1px solid red;
  }

  body{
    background: linear-gradient(to right,black);
  }

```
to be continued...
