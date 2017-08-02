---
layout: post
title:  "S.O.L.I.D. Principles(SOLID Prensipleri)"
date:   23.09.2016
categories: [DesignPatterns]
tags:
 - Pattern
---

OOP'de uyulması gereken belli kurallar vardır.Bu kurallar olmadan geliştirilen kod ilerde çok büyük hata ve kayıplar olarak geri dönecektir.Dilden bağımsız bu kurallar SOLID kısaltmasıyla karşımıza çıkar;

    Single Responsibility Principle
    Open-Closed Principle
    Liskov's Substitution Principle
    Interface Segregation Principle
    Dependency Inversion Principle

Single Responsibility Principle

Bir sınıfın sadece tek sorumluluğu olmalıdır.Bunu açarsak, birden fazla farklı metodu içerisinde barındırmamalıdır.Örnek olarak SmartTV adında sınıfımız olsun,
    ![alt text]({{ site.url | append:site.baseurl }}/images/code/solid1.png)
    ![alt text]({{ site.url | append:site.baseurl }}/images/code/solid2.jpg)

Şekil 2'de diyagramda görülüyor ki birinci diyagrama göre sınıfın üzerindeki yük azaltılmış ve görev paylaşımı yapılmıştır buda istediğimiz şeydir.

Open-Closed Principle

Bir sınıf geliştirmeye açık ama değişime kapalı olmalıdır.Polymorphism,Inheritance,Interface gibi konuları iyi anlarsak bu prensibi uygulamak hiç zor olmayacaktır.Bu prensibi uygulamak için genel metodları interface bir sınıf üzerinden diğer sınıflara bağlamak doğru olacaktır böylelikle sınıf kontrolü yapmadan metodlara direk ulaşılır.

Liskov's Substitution Principle

Burda şöyle açıklayabiliriz ama önce prensip kuralımızı öğrenelim, türeyen sınıflar türetilen sınıfın tüm özelliklerini kullanmak zorundadır.Örnek verdiğimizde,

![alt text]({{ site.url | append:site.baseurl }}/images/code/solid3.png)

Nokia5110 sınıfı Dokunmatik methodunu kullanamayacaktı interface bi sınıf oluşturarak kuralı çiğnemenin önüne geçiyoruz.

Interface Segregation Principle

Bir arayüzü implemente alan sınıfların kullanılmayan metotları bulundurmaya zorlanmasının önlenmesidir. Mümkün olduğunca ortak özellikler arayüz halinde tasarlanmalı ve gerekirse farklı arayüzler birbirinden extend almalıdır.

Dependency Inversion Principle

Aslına bakıldığında uygulamalı açıklaması şöyle olabilir somut sınıflar arasına interface sınıflar yerleştirerek bağımlık tersine çevrilir.Yani somut sınıfta değişiklik olması engellenmiş olur.
