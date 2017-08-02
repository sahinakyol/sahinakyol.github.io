---
layout: post
title:  "Inheritance(Kapsülleme)"
date:   23.09.2016 01.00.00
categories: [OOP]
tags: 
 - Inheritance,JAVA
---

OOP 'de çok önemli bir yere sahip olan Kalıtım miras almak ve miras bırakmak için kullanılır.
Bunu şöyle örnekleyebiliriz anne ve babanın yetenekleri kalıtım yoluyla cocuğa aktarılır anneden gelen gözlerden ışın çıkarma babadan gelen uçma  yeteneklerine çocukları da sahip olur ama çocuklarınında ebeveynlerinden farklı olarak Süper güçlü olmak gibi bir yeteneği olabilir.

Burda bu yeteneklerin aktarılmasında Kalıtım(Inheritance) başrol oynar. Bunuda extends anahtar kelimesiyle yapar.
Bir not; bir sınıf birden fazla sınıftan türetilemez.Yani çocuğun başka ebeveynleri olamaz.

Aşağıdaki kodla daha iyi anlaşılacağı kanısındayım;

``` java
public class Ebeveyn {
private String anne;
private String baba;

public Ebeveyn(String anne, String baba) {
this.setAnne(anne);
this.setBaba(baba);
}
public String getAnne() {
return anne;
}
public String getBaba() {
return baba;
}

public void setAnne(String anne) {
this.anne = anne;
}
public void setBaba(String baba) {
this.baba = baba;
}
public String kahraman(){
return getAnne()+" "+getBaba();
}
}
```
``` java
public class Evlat extends Ebeveyn{
private String evlat;
public Evlat(String anne, String baba,String evlat) {
super(anne, baba);
this.evlat=evlat;
}
public String getEvlat() {
return evlat;
}
public void setEvlat(String evlat) {
this.evlat = evlat;
}

@Override
public String kahraman(){
return super.kahraman()+"  "+getEvlat();
}
}
```
``` java
public class anaSinif {

public static void main(String[] args) {
Evlat cocuk=new Evlat("Isın ", "Uçma ", "Güc");
System.out.println("Artık kötülüklerin karşısında daha güclü bir kahraman var : "+cocuk.kahraman());
}}

=> prints "Artık kötülüklerin karşısında daha güclü bir kahraman var : Isın Uçma Güc" to STDOUT.
```

Notlar:

-Ilk kod parçasında(Super sınıf denir bunun anlamı miras bırakan demektir) get-set kardeşler ve Constructors(Yapıcı) methodlarımız tanımlandı bunları zaten eclipse bizim için yapıyor(right click.source. ...),son olarakta yazdırma metodu tanımladık.

-Ikinci kod parcasında(Sub sınıf denir miras alan anlamına gelmektedir) super metoduyla miras aldığımız sınıfının yapıcısına erişiyoruz bildiğimiz metod çağırmaya benzemektedir.Override ediyoruz yazdırma metodunu.

-Super metod'u için aslında çok söylenebilecek birşey yoktur metod çağırmış oluyoruz.Tek istisnası vardır herzaman constructor metod içerisinde en üstte yazılmalıdır.

-Bir sınıf türetildiği sınıftaki methodu değiştirmek isterse overriding yapar,amacı eğer altsınıf üst sınıfın metodunu doğrudan kullanmak istemiyorsa kendine ait bir metod oluşturur üstten aldığı metodu değiştirerek.

-Override'ın belli kuralları vardır,öncelikle dönüş tipi, metod adı, parametre listesi aynı olmak zorundadır,erişim belirleyici üstteki metoddan daima küçük olmalıdır.
