---
layout: post
title:  "Ruby Basics"
date:   11.05.2017
categories: [Ruby]
tags: 
 - ruby
---

**Ruby Basics**

Ruby;
    OOP,
    Interpreted(Yorumlamalı yani çalışma anında compile edilen dildir.),
    RubyGems (Paket Yöneticisi),
    Ruby on Rails (Web Framework),
    Sinatra (Web Framework).

**IRB**

``` js
    $ irb
    > puts 'Let her go'
    > Let her go
    > ''.class
    > String
```
**Mantıksal Ifadeler**

``` js
    $ irb
    > 2 == 3 // false
    > 1 > 1 // false
    > 4 > 1 // true
    > !8 // false
    > A && B // mantıksal
    > B || A // mantıksal
```
**Metodlar**

``` js
    def metod par1 , par2
    end
```
``` js
    ala! //Çağıran nesne üzerinden işlem yapar
    pekala? //boolean dönesnesidir
    aliyülala= //Bir değişkenin değerini değiştirmek için.
```
**Naming Rules**

``` js
    class LongDay // Sınıf isimleri birer sabittir sabitler büyük harfle başlar.
    module Socket // Modul isimleri birer sabittir sabitler büyük harfle başlar.
    BETA = 999999 // sabitler büyük harfle başlar.
    viz = 11 // yerel değişkenler küçük harfle başlar.
    $golden_globe // global değişkenler $ ile başlar
    @instance // @ değişkeni ile
    @@class_var // sınıf değişkeni @@ ile başlar
```
**Loading**

``` js
    $ fileA.rb // string ifade barındıran dosya
    > "Sen Kaybolup Yiten" // string ifade
    $ fileB.rb // boş dosya
    > load "fileA.rb" // boş dosyanın içerisine yazıyoruz bu satırı
    $ ruby fileB.rb // sonra dosya çalıştırılır
    $ "Sen Kaybolup Giden" // böylece bir dosya içerisinden bir başka dosya çağrıldı
```
**Require**

``` js
    $ fileA.rb // string ifade barındıran dosya
    > "Sen Kaybolup Yiten" // string ifade
    $ fileB.rb // boş dosya
    > require "./fileA.rb" // boş dosyanın içerisine yazıyoruz bu satırı
    $ ruby fileB.rb // sonra dosya çalıştırılır
    $ "Sen Kaybolup Giden" // böylece bir dosya içerisinden bir başka dosya çağrıldı
```
**Load vs Require**

-_load_ ile birden fazla kez dosyayı yükleyebiliriz.

_require_ ile birkez yükleyebiliriz.

-_load_ dosya uzantısı gereklidir.

_require_ için gerekli değildir.

-_require_ dosyayı bulmak için bütün yoları arar.

**AutoLoad**

``` js
    $ fileA.rb
    > puts "Bir bilmece gibi"
    > class loading; end
    $ fileB.rb
    > autoload(:loading, './fileA.rb')
    loadin = loading.new
```
**RubyGems**

``` js
    $ gem install pack // belirtilen gem yüklenir
    $ gem uninstall pack // belirtilen gem kaldırılır
    $ gem list // gemler listelenir
    $ gem list -r // kullanılabilecek gemler listelenir
    $ gem install bundler // gemfile da belirtilen gemler yüklenir
```
**I-O**

``` ruby
    puts object
    print object
    p object
    gets object
    readline
    readlines
```
**Strings**

``` ruby
    "Hello" + "guys" # helloguys
    "Hello" << "guys" # helloguys
    "#{'hello'.capitalize} #{'guys'.upcase}" # Hello GUYS

    :symbol
    "exp"
    # symbol ile exp aynıdır tek farkı her çağrılmada symbol tekrar tekrar oluşturulmaz.
    # semboller değiştirilemezdir eğer değiştirilemez olmasını istiyorsak .freeze metodundan yararlanılır.
    "exp".freeze
    "exp" << " ression" #hata alırız

    "exp".to_sym # :exp
    :exp.to_s # "exp"
```
**Regexp**

Düzenli ifadeler /... / arasına yazılır.

``` ruby
    /@/ =~ "user@user.com" # 4
```
**Ranges**

``` ruby
    1..100 # start .. end
    1...100 # start .. end-1
    (1..100).to_a # [1,2,...,99,100]
    ("a".."z").to_a # ["a","b",...,"y","z"]
    (1..10).step(3) {|i| puts i} #1 4 7 10
```
**Arrays**

``` ruby
    dizi = Array.new
    dizi = ["xx", 33, true, [1,2,3]]
    dizi.first # "xx"
    dizi.last # [1,2,3]
    dizi[-2] # true
    dizi1 = [1,2,3]
    dizi2 = [1,2,3]
    dizi1 + dizi2 # [1,2,3,1,2,3]
```
**Hash**

```ruby
    birdman = { key: 'value' , key1: 'value1'} #keyler semboldür
    'key'.eql? 'key1' # false
    birdman.keys # [:ad , :soyad]
    birdman.values # ["value", "value1"]

    def name(params={}) #method içinde kullanımı
      "#{params[:ad]} #{params[:soyad]}"
    end
    name ad:"birds" soyad:"die" # "birds die"

    birdman.each do |key , value|
      puts "#{key}: #{value}" # key: value key: value1
    end
```
**Conditions**

``` ruby
    if Conditions
      ...
    end

    if Conditions then
      ...
    end

    if Conditions
      ...
    elsif Conditions
      ...
    end

    unless Conditions
      ...
    end

    Conditions ? true_works : false_works

    case value
    when String then "String Değer"
    when Integer then "Integer Değer"
    end

    while Conditions
      ...
    end

    until Conditions
      ...      
    end

    loop do
      ...
    end
```
**Exception Handling**

``` ruby
  begin
    number = 1/0
  rescue
    puts "hata"
  ensure
    puts "hata oluştu"
  end

  number = 1
  begin
    fail "hata" if number >3
  end
```
**Blocks,proc,Lambda**

``` ruby
  topla = -> a,b{a + b} # -> lambda işaretçisi
  topla.call(5 , 6) # 11

  def topla(a,b) a+b end
  topla.to_proc # metod bloğa dönüştü

  def hes(s1,s2, islem)
        islem.call(s1,s2)
  end
  top=hes(2,3, lambda {|a,b| a+b})
  puts top
```
_proc_ ile _lambda_ neredeyse aynıdır. lambda proc'tan türetilmiştir.

**Class**

``` ruby
  class Animals
    def initialize(fırtına) # Constructor metod
      puts "Bir fırtına tuttu bizi"
      @fırtına = fırtına
    end
  end

  monkey = Animals.new('etkilenmez')
  horse = Animals.new('etkilenmez')
  birds = Animals.new('etkilenir')

  class Maden
    attr_accessor :jeo
    #get-set metodlarını ortadan kaldırır 'attr_reader' , 'attr_writer' olabilir.
    def initialize
      jeo = "";
    end

    def self.metods #self sınıfa ait olduğunu belirtir.
      puts "luluby"
    end
  end

  altın = Maden.new
  altın.jeo = "Çok değersizdir bu yüzden savaş bile çıkarır..."
  puts altın.jeo

  # @@var değişekini sınıf değişenidir.  
```
**Inheritance**

``` ruby
  class A
  end
  class B < A
  end

  #super metodu da vardır
  #sınıf değişeknleride(@@var) kalıtım youluyla aktarılır en son sınıftaki değerini alır.
  #bunu engellemek için @var kullanılmalı
```
**Modules**

Moduller namespace'lere benzetilebilir.

``` ruby
  module Mod
    PI=3.14
    def self.method puts "minna" end
  end
  Mod.method
  Mod::PI
```
``` ruby
  module Blink
    def blinkio "eyes" end
  end

  class face
    include blink #include yerine prepend veya extend kelimesi getirilebilir
  end

  face.new.blinkio # eyes

```
**File IO**

``` ruby
  File.open('hello', 'w') do |myFile|
    myFile.print "File IO!"
  end
```

``` ruby
  (5..10).inject{|number1 , number2| number1 + number2 }
  #Sayıların toplamını verecektir = 45

  array = [1,2,3,4,5,7,6,8].sort #sort metodu sıralayacaktır
    double = array.map do |indis| #map metodu each metodu gibi davranıyor
    indis * 2
  end
  puts double # 2,4,6,8,10,12,14,16
```

``` ruby

  variable = "nobody"
  changed = variable.upcase!
  puts changed # = NOBODY
  puts variable # = NOBODY
  #Eğer '!' kullanmazsak
  # changed = NOBODY
  # variable = nobody
  # metod isimlerinin sonunda kuallandığımız ! bize kalıcı değişiklik olacağını belirtir ve sağlar

```

``` ruby
  # What the pack? =)
  #Stringleri formatlayarak saklayabiliriz

  "Neşet Ertaş".unpack("C C C C C C C C C C C")
    # [78, 101, 197, 159, 101, 116, 32, 69, 114, 116, 97]
  [78, 101, 197, 159, 101, 116, 32, 69, 114, 116, 97].pack("C C C C C C C C C C C")
    # "Ne\xC5\x9Fet Erta" türkçe karakterler desteklenmediği için
  "Neşet Ertaş".unpack("C C")
    # [78, 101] stringin istenilen kadarı alınabilir
  [78, 101].pack("C")
    # N
  "Neşet Ertaş".unpack("C*")
    # [78, 101, 197, 159, 101, 116, 32, 69, 114, 116, 97] yine aynınısını verir
  "Neşet Ertaş".unpack("C2")
    # [78, 101] ilk iki karakteri aldı
  "Neşet Ertaş".unpack("B*")

    # C => char Range: 0 to 255
    # I => int Range: -2147483648 to 2147483647
    # S => short Range: 0 to 65535
    # L => long Range: 0 to 4294967296
    # Q => long long Range: 0 to 18446744073709551616
    # J => pointer width
    # U => UTF-8 Characters
    # d|D => Float
    # B => Bit
    # H => Hex
    # u => UU-Encoding Unix-to-Unix Encoding.
    # M => Quoted-Printable / MIME Encoding (RFC2045)
    # m => Base64 Encoding (RFC 2045)
    # m0 => Base64 Encoding (RFC 4648)
    # p => Pointer to Null-Terminated String
    "ℜ".unpack1("U") # 8476
    # 2.4 ile gelmiş yeni pack methodu

    "Neşet Ertaş".unpack("U*")
      # [78, 101, 351, 101, 116, 32, 69, 114, 116, 97, 351]

    "78, 101, 351, 101, 116, 32, 69, 114, 116, 97, 351".unpack("B*")
      # ["00110111001110000010110000100000001100010011000000
      # 11000100101100001000000011001100110101001100010010110
      # 00010000000110001001100000011000100101100001000000011
      # 00010011000100110110001011000010000000110011001100100
      # 01011000010000000110110001110010010110000100000001100
      # 01001100010011010000101100001000000011000100110001001
      # 10110001011000010000000111001001101110010110000100000
      # 001100110011010100110001"]

    ["0011011100111000001011000010000000110001001100000011000
      1001011000010000000110011001101010011000100101100001000
      0000110001001100000011000100101100001000000011000100110
      0010011011000101100001000000011001100110010001011000010
      0000001101100011100100101100001000000011000100110001001
      1010000101100001000000011000100110001001101100010110000
      1000000011100100110111001011000010000000110011001101010
      0110001"].pack("B*")
      # "78, 101, 351, 101, 116, 32, 69, 114, 116, 97, 351"

    [78, 101, 351, 101, 116, 32, 69, 114, 116, 97, 351].pack("U*")
      # "Neşet Ertaş"
```

to be continued...


Resources :

 [Idiosyncratic Ruby](http://idiosyncratic-ruby.com)
