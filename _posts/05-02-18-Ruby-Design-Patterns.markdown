---
layout: post
title:  "Design Patterns in RUBY"
date:   05.02.2018
categories: [Ruby]
tags:
 - ruby
---

# Design Patterns in RUBY
  Tasarım kalıpları konusunda hem eksiklerimi kapatmak hem de not almak adına olabildiğince tasarım kalıplarını anlayıp buraya notlar alacağım.

## Adapter Pattern

**Sorunumuz :** iki farklı çıktı veren kaynağımız olduğunu düşünelim bunların arasına birbirinden bağımsız üçüncü bir katman koymalıyız ve bu ara katman ikisinin de dilinden anlayabilmeli bununla ilgili günlük hayattan örnekler verilebilir.Mesela tercümanlar yada ingiliz standardı prizleri kullanabilmek ayrıca ek bir aparat kullanmak gibi birsürü örnek verebiliriz.
Peki buna neden ihtiyaç duyarız;
  _Bunun nedeni aralarındaki bağımlılık sorununu çözebilmektir!_

<p align="left">
 <img src="{{ site.url | append:site.baseurl }}/images/humor/komikli1.jpg"/>
</p>

``` ruby
  class Detector
  # Binary DATA 0101010101  gibi bir değere üretmeli
  def initialize binaryData
    @binaryData = binaryData
  end
  def binaryGenerator
    rand(@binaryData).to_s(2)
  end
  end
# ------------------------------
  class Adapter
# Adapter class aldığı veriyi diğer sınıfın anlayacağı hale getiriyor.
# Binary data alınır
# Integer bir sayıya çevrilir gönderilir.
#  -------------------------
# Integer bir sayıya alınır.
# Binary data çevrilir ve gönderilir.
  def initialize(received)
    @received = received
    transform()
  end
  def transform
    if (@received.instance_of?Integer)
      puts "Binary---"
      puts @received.to_s(2)
    elsif (@received.instance_of?String)
      puts "Integer---"
      puts @received.to_i(2)
    end
  end
end

class App
  # Decimal sayılar üretmesi bekleniyor.
  def initialize(integerData)
    @integerData = integerData
  end

  def integerGenerator
    rand(@integerData)
  end
end

  app= App.new(5)
  Adapter.new(app.integerGenerator)

  bin = Detector.new(100)
  Adapter.new(bin.binaryGenerator)

```

to be continued...


Resources :
