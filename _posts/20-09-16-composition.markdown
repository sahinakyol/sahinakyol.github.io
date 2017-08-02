---
layout: post
title:  "Composition in JAVA(Javada Kompozisyon)"
date:   23.09.2016
categories: [OOP]
tags: 
 - Composition,JAVA
---

Java dilinde kompozisyon kullanımı inheritance(kalıtım)'a alternatiftir.
Kalıtımın ana kuralı olan bir sınıf sadece bir sınıfı miras alabilir kuralı bazen bizi engelleyebilir.
Örnek verecek olursak farklı sınıflarda işimize yarayan bir metod varsa, kullanabilmek için kompozisyon yaparız. Aşağıdaki kodlarla daha anlaşılır hale gelecektir ;

``` java
class Splinter{
private static int x;
public void hero(){
System.out.println("Im hero");
}
}
class Schredder{
int y;
private Splinter Rafael=new Splinter();

public void power(){
System.out.println("Hello");
Rafael.hero();

}
}
public class main {

public static void main(String[] args) {
Schredder object=new Schredder();
object.power();
}
```
Notlar:

-Bir sınıfın içerisinde başka bir sınıfın nesnesini oluşturarak gerçekleştirdik.
