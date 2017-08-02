---
layout: post
title:  "Recursıve Functıons ın C  (C 'de Özyinelemeli Fonksiyonlar)"
date:   23.09.2016
categories: [LowLevelProgramming]
tags: 
 - Recursive
---


Recursive functions büyük problemlerin parçalanarak nasıl daha kolay çözülebileceğine yardımcı olan fonksiyon yapılarıdır.Yapı itibariyle basit ve anlaşılırlardır.Daha iyi anlaşılması açısından "Kendi Kendine Çağıran Fonksiyon" dersek daha akılda kalıcı olacaktır.

``` c
int factoriel(int x){

if(x==0)

return 1;

else

return x*factoriel(x-1);

}

```
``` c
int fibonacci(int y){

if(y==0)

return 0;

else if(y==1)

return 1;

else

return (fibonacci(y-1)+fibonacci(y-2));
```
Notlar:

-Recursive Functions her zaman performans sağlamayabilirler hafızada bazen performans kayıplarına sebep olabilirler.(Anlamayanlar için c'de heap,stack,hafıza kullanımı gibi konulara göz atabilirler)

-Gönül isterdiki github bağlantılı olmasının kodlarımın fakat hala öğrenim sürecine giremedim "tembellik aldı başını gidiyor yaa" =) (Bu not çok uzun zaman önce yazılmış :D)
