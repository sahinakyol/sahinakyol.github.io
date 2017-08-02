---
layout: post
title:  "Encapsullation(Kapsülleme)"
date:   23.09.2016 02.00.00
categories: [OOP]
tags: 
 - Encapsullation,JAVA
---


Kapsülleme OOP(Object Oriented Programming) yani nesne yönelimli programlamanın önemli bölümlerinden biridir kapsülleme bir sınıfın kendi içerisindeki metod ve değişkenleri korumasıdır. Böylelikle diğer sınıflar kısıtlı veya hiçbir erişim sağlayamazlar. Buraya kadar standart bi açıklama oldu peki kısıtlayan veya erişimi engelleyen şeyler nedir? Bunlar erişim belirleyicidirler(access modifiers);

    public -  Herkes ulaşabilir.
    protected - Içinde bulunduğu sınıftan türetilmiş ve o sınıf ile aynı paketteki sınıflar ulaşabilir.
    private - Sadece kendi sınıfından ulaşılabilir.
    default - Tanımlanmamışsa defaulttur , içinde bulunduğu sınıftan ve paketten ulaşılabilir.

bu anahtar kelimeleri method ve nesnelerimizin başına getirerek koruma sağlayabiliriz.
Bir not; bir java dosyası içerisinde birden fazla public sınıf tanımlanamaz.

Peki private elemana farklı sınıflardan nasıl ulaşabiliriz? Bunları sağlayan getter-setter metod kardeşlerdir.Bunların sayesinde değişkeni okuyabilir yada değişken üzerinde değişiklik yapabiliriz.

Getter metoduyla okuma yaparız ve bir parametre almaz.

Setter metoduyla private üyelere değer atandığı için parametre alırlar.

Aşağıdaki kodla daha iyi anlaşılacağına inanıyorum,

``` java
public class Encapsulation {
private int x;
private int y;

public int getX() {
return x;
}
public int getY() {
return y;
}
public void setX(int x) {
this.x = x;
}
public void setY(int y) {
this.y = y;
}
public static void main(String[] args) {

Encapsulation nesne = new Encapsulation();
nesne.setX(5);
nesne.setY(6);
System.out.println(nesne.getX());
System.out.println(nesne.getY());

}
=> prints "5 , 6" to STDOUT.
```
Notlar:

-Metod isimleri get set diye başlamak zorunda değildir ama eclipse tatlılığı diyelim kolayca get-set metodunu bizim yerimize oluşturuyor.(right click.source.generate getter setters)

-This anahtar kelimesi isim karışıklığından kurtarmak için bizim yanımızdadır parametre olarak gönderilen değişkeni kullanmamıza sağlar ve tüm metodlarda kullanılabilinir buraya has değildir sadece,bir görevi daha var ama şuan söylemek kafa karıştırıcı olacaktır.

-Eğer nesne oluşturmak istemiyorsak metodlarımızı static tanımlamalıyız böylelikle nesnesiz erişebiliriz.Erişmek içinse public static int getX() {... yeterli olacaktır.
