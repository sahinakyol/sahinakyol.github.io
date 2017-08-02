---
layout: post
title:  "Java Collections-HashSet"
date:   23.09.2016
categories: [OOP]
tags: 
 - collections
---


HashSet matematikteki kümelere benzeyen bir yapısı vardır.Sıralı olmayabilir ve ayrıca erişim sırası da belirsizdir.Elemanları ise eşsizdir.

``` java
public class Temp {

public static void main(String[] args)
{
HashSet<String> yapi=new HashSet<String>();

yapi.add("Güneş");
yapi.add("Ufuktan");
yapi.add("Doğar");

Iterator yineleyici=yapi.iterator();

while(yineleyici.hasNext()==true){
System.out.println(yineleyici.next());
} } }

```
Notlar:

-HashSet<String> ya... burada <String> ifadesini tanımlamasakta olur ama böyle yaparsak kümemizi daha spesifik hale getiriyoruz yani aldığı değerler string'tir diyoruz.

-Iterator nesnesi oluşturduk bu bize elemanlar arası ilerlememizi sağlar.

-hasNext ile kontrol ederiz eleman varmı yokmu boolean değer döndürürüz.

-next ile de elemanı getiririz.
