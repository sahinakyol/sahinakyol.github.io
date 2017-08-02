---
layout: post
title:  "Java Database Connectıvıty(JDBC) wıth Crud Operations (JDBC ile Veritabanı Işlemleri)"
date:   23.09.2016
categories: [OOP]
tags:
 - Collections,JAVA
---

JDBC(Java Database Connectivity) java uyugulamamızla veritabanımızı bağlamımızı sağlayan bir Java Api'sidir.

Veritabanını tanımlamak istediğimizde çok büyük  kısmı SQL(dilden veya teknolojiden bağımsız standart veritabanı dilidir.) komutlarını kullanır.Veritabanları verileri saklarken belli bir veri modeli kullanır.Bunlar;

    -Hierarchical
    -Network
    -OOP
    -Relational
    -Entity -Relation Model

Bunlar içerisinde en çok kullanılanı Relational(ilişkisel) modeldir.

    Burada bir not  eklemeliyim ;
    Bu noktadan önceki yazılarımla sonraki yazılarım arası uzun bir zaman geçmiş devam edip etmekte tereddüte düşsemde sonradan yazmaya karar verdim yazılarımı olabildiğince kısa yazmaya çalışıyorum aslına bakıldığında bazı konular kitap yazılacak düzeyde genişler ama olabildiğince basitleştirmeye önemli gördüğüm noktaları yazmaya çalışıyorum belirtmek istedim.

Veritabanı işlemlerinde bir veritabanı aracına ihtiyaç duyarız bunlar(mysql,postgresql,oracle...)bizim veritabanı oluşturmamızı düzenleme ve saklamamızı sağlarlar.

Örneğimi [postgresql](https://www.postgresql.org/) üzerinden yapacağım ;

[Kurulum için buradaki yönergeleri kullanabilirsiniz(Ubuntu)](https://help.ubuntu.com/community/PostgreSQL)

yada

[Video(Ubuntu)](https://www.youtube.com/watch?v=QTCsjVGlPBM)

Kurulumdan sonra kullandığımız ide için connector indirmemiz gerekli

[Postgresql connector](https://jdbc.postgresql.org/download.html)

Connector'ümüzü eclipse ortamına harici kütüphane olarak tanıtıyoruz

  ![alt text]({{ site.url | append:site.baseurl }}/images/code/jdbc1.png)

Burada "HibernateExample" adlı dosyasının üzerine sağ tıklayıp properties seçeneğini seçiyoruz.

  ![alt text]({{ site.url | append:site.baseurl }}/images/code/jdbc2.png)

Burası gelmiyorsa arama bölümünde Build path yazarak getirebilirsiniz.

  ![alt text]({{ site.url | append:site.baseurl }}/images/code/jdbc3.png)

"Add external JARs.." butonuna tıklayın indirdiğimiz connector'ü seçin daha sonra hepsini tamam diyerek kapatın.

Buradan örnek demoyu inceleyebilirsiniz.

[JDBC Example](https://github.com/MrBlueSkyy/JdbcExample)
