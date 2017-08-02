---
layout: post
title:  "Law of Demeter"
date:   07.05.2017
categories: [DesignPatterns]
tags: 
 - Pattern
---

**'Law of demeter'** yada diğer adıyla _'en az bilgi prensibi'_ object oriented programming'in
temel prensiplerinden biridir.

Yapısı temelde nesnelerin sadece ilgili olduğu sınıf veya metodlarla konuşmasını hedefler. **_"don't talk with strangers"_**

Ruby'de araştırma ihtiyacı hissetmediğim ama Java'da fazlasıyla karşıma çıkan
loose ve tight coupling yapılarından *'Law of demeter' loose coupling sağlar.*

**Tight Coupling in JAVA**

```java

class CustomerRepository {

  private readonly Database database; //Database Sınıfından nesne oluşturulmuş

  public CustomerRepository(Database database){
    this.database = database; //Constructor 'database' nesnesini alıyor
  }

  public void Add(string CustomerName){
    database.AddRow("Customer", CustomerName);
    // Add metodu database nesnesi ile çağırılan AddRow metoduna aldığı string'i gönderiyor
    // tight coupling burada oluyor.
  }
}

class Database {
  public void AddRow(string Table, string Value){
  }
}

```
**Loose Coupling in JAVA**

```java

class CustomerRepository{

  private readonly IDatabase database; // IDatabase sınıfından nesne oluşturulmuş

  public CustomerRepository(IDatabase database){ //Constructor 'database' nesnesini alıyor
  this.database = database;
  }

public void Add(string CustomerName){
  database.AddRow("Customer", CustomerName);
  // Add metodu database nesnesi ile --interface üzerinden çağırılan
  // --AddRow metoduna aldığı string'i gönderiyor loose coupling burada oluyor.
 }
}


interface IDatabase{
  void AddRow(string Table, string Value);
 //Javada loose coupling yapmak için interface kullanırız böylece doğrudan Database sınıfı ile iletişime geçtik
  }


class Database : IDatabase{ //IDatabase interface'i implemente edildi
public void AddRow(string Table, string Value)
  {

    }
}

```
**Tight Coupling in RUBY**

```ruby

class Paperboy
  def collect_money(customer, amount) #collect_money sınıfı customer ve amount nesnesi alıyor
    if customer.wallet.cash > amount
      # => Eğer customer sınıfının wallet metodundaki cash nesnesi amount'dan yüksek ise 
      # => withdraw metoduna miktarı gönder.
      # => customer.wallet.withdraw(amount)
    else
      # collect_later
    end
  end
end
#Burada tight coupling yapılmıştır Javadakine benzer bir yapı görülebilir
```
**Loose Coupling in RUBY**

```ruby

class Customer
  def pay_amount(amount)
    @wallet.withdraw!(amount)
    # wallet sınıfının wallet nesnesi üzerinden withdraw metoduna amount nesnesi gönderiliyor.
    # burada dikkat edilirse araya taşıyıcı bir sınıf koyuluyor.
    # Ruby'de interface kavramı yoktur onun yerine bu tarz bir yapı ile sağlanır.
  end
end

class Wallet
  def withdraw!(amount)
    return false if @balance < amount
    # Eğer balance objesinin değerinden yüksek ise amount değeri false dön ve balance'dan amount kadar azalt aksi takdirde true dönecektir.
    @balance -= amount
    true
  end
end

```
```ruby

class Paperboy
  def collect_money(customer, amount)
    if customer.pay_amount(amount)
      #customer sınıfının pay_amount metodu çağırılıyor eğer true ise thanks basacaktır.
      puts 'Thanks!'
    else
      # collect_later
    end
  end
end
```
References :

[The Law of Demeter](http://nithinbekal.com/posts/demeter/)

[What is the difference between loose coupling and tight coupling in the object oriented paradigm?](https://stackoverflow.com/questions/2832017/what-is-the-difference-between-loose-coupling-and-tight-coupling-in-the-object-o)
