---
layout: post
title:  "Java Generıcs"
date:   23.09.2016 00.00.00
categories: [OOP]
tags: 
 - Generics,JAVA
---
Java'da 5.0 ile gelen daha güvenilir ve kolay yapısıyla gönülleri fethetmiş bir özelliktir.
Öncelikle güvenilir olmasını açıklamak istersek bazen list yapılarında veya class'larda farklı tipli nesne gönderme ihtiyacımız olabilir. Sabit bir tip belirlediğimiz için bunu yapmak çok zordur.Burada imdadımıza generic types yetişir.Kolaylığı ise cast işlemlerini azaltmamızı sağlar.

``` java
class saitama<T> {
public T nesne;

public T getNesne() {
return nesne;
}

public void setNesne(T nesne) {
this.nesne = nesne;
}

}
public class Genos {

public static void main(String[] args) {

saitama<Integer> one=new saitama<Integer>();
one.setNesne(89);
System.out.println(one.getNesne());
//-------------------------------
saitama<String> two=new saitama<String>();
two.setNesne("I wanna be HERO for protecting you but you'll never know");
System.out.println(two.getNesne());
}

}
```

``` java

class saitama<K,V> {

TreeMap<K, V> nesne=new TreeMap<K, V>();

public TreeMap<K, V> getNesne() {
return nesne;
}

public void setNesne(K key,V value) {

this.nesne.put(key, value);
}

}
public class Genos {

public static void main(String[] args) {

saitama<String,Integer> one=new saitama<String,Integer>();
one.setNesne("I don't wanna be a part of your parade", 2015);
System.out.println(one.getNesne());
}
}
```
