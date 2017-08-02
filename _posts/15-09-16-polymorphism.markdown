---
layout: post
title:  "Polymorphism(Çok Biçimlilik)"
date:   23.09.2016 03.00.00
categories: [OOP]
tags: 
 - Polymorphism
---


Polymorphism OOP'de önemli konulardan biridir.Açıklamak istediğimizde tanım vermekten ziyade kod üzerinde anlatmak anlaşılmasını kolaylaştıracaktır;

``` java
class Hareket {

public void move(){
System.out.println("Hareket Sinifi ");
}
}
class Balik extends Hareket{

@Override
public void move() {
System.out.println("Balık Yüzer");

}
}
class Aslan extends Hareket{

@Override
public void move() {
System.out.println("Aslan koşar");
}
}
class Kartal extends Hareket{

@Override
public void move() {
System.out.println("Kartal Uçar");
}
}
class poli{

public static void polican(Hareket hayvan) {
hayvan.move();
}

public static void main(String[] args) {
Hareket nesne1=new Hareket();
Balik nesne2=new Balik();
Aslan nesne3=new Aslan();
Kartal nesne4=new Kartal();

polican(nesne1);
polican(nesne2);
polican(nesne3);
polican(nesne4);

}}
```

Notlar:

-Burada polican metoduna kadar herşey normaldir ancak dikkat edilmesi gereken husus polican metodunun "Hareket tipinde nesne alıp move() methodunu çağırmasıdır "

-Ee ne var bunda diyebilirsiniz ama nesnelerimizi polican metoduna gönderdiğimizde hangi sınıfın move metodu çağrılacaktır?Burada öncelik türeyen sınıfın metodu olacaktır.

-Polican methodunda hayvan değişkenin birden fazla nesneye bağlanabildiğini görürüz, bu özellik polimorfizm 'dir.

-Bir kavram daha ortaya çıkacaktır "Late Binding" geç bağlama anlamına gelir polymorphism'in kalbidir.Geç bağlama,parametre olarak nesne gönderdik ve bu çağrılan metodların hangi nesne üzerinden çalıştıralacağını java belirler.Çalışma zamanında belirlenir.

-Burada kısa tutmaya çalıştım aslında daha komplike bir konudur farklı kavram ve konularla ilintilidir.(instanceof,getclass,upcasting,downcasting,geç ve erken bağlama,kalıtım,overrriding)
