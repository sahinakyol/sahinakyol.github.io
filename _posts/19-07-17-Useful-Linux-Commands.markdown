---
layout: post
title:  "Useful Linux Commands"
date:   19.07.2017
categories: [Linux]
tags:
 - Linux
---

Some infos about linux shell scripting.Woww don't worry about language :)
Generally article is going to be english but comments or explanations are going to be Turkish.

```shell

  $ parted # Disk bölümleme için kullanırız

  $ badblocks -vs /dev/sda  # Hatalı blokları bulup tamir etmek için kullanırız

  $ cfdisk # Disk Bölümlerini gösterecektir
```
```shell

  $ ps aux  # Çalışan süreçleri görmemizi sağlar

  $ pstree  # Çalışan süreçleri ilintili görmek için

  $ top # Çalışan süreçleri ayrıntılı görmek

  $ pgrep -lu user  # Kullanıcıya ait süreçleri görmemizi sağlar

  $ killall -9 process # Süreci ve ilintili süreçleri zorlayarak durdurur

  $ xkill # Mouse ile durdurmak istediğimiz süreci tıklayarak durdurabiliriz
```
```shell

  $ passwd  # Kullanıcı parolasını değiştirebilirsiniz
  # Kullanıcı parolaları /etc/shadow dosyasında şifrelenerek saklanır
  # Yapı itibariyle hashler $Şifreleme Algoritması$Parola Değeri$Gerçek Parola değeri.
  # 1- md5, 5- SHA256, 6- SHA512 gibidir.

  $ adduser newUser # Yeni kullanıcı eklemek istersek

  $ userdel -r newUser #Dizinle beraber silecektir

  $ chfn user # Kullanıcı bilgileri değiştirilebilir

  $ chage -l user # Kullanıcı bilgileri gösterilir

  $ su otherUser  # Bir başka kullanıcı yetkisiyle çalışır

  $ chmod # Kullanıcı yetki değişikliği yapabiliriz
          # $ ls -l
          # -rw-rw-r-- 1 user user  999 Nov 10 09:05 life.c
          # Ilk yetki grubu Dosya-Dizin sahibi,
          # ikinci yetki grubu Dosya-Dizin grup sahibi,
          # üçüncü yetki grubu Dosya-Dizin farklı yetkilendirilmiş grup
  $ chmod u-x+rw myFile # Dosya'ya erişim yetkisi user yazma-okuma yapar çalıştıramaz

```
```shell

  $ cat > file
  #Bundan sonra yazacaklarınız dosyaya kaydedilecektir üstüne yazacaktır
  # >> yaparsak eğer son satıra ekleyecektir.

  $ echo {1..100} ; echo {a..z} #Ekrana basar 1'den 100'e

  $ head file # Ilk 10 eleman '-n 3' ilk 3'ü basar

  $ tail file # Son 10 eleman '-n 3' son 3'ü basar

  $ tee filenameForCreatingFile #Dosya oluşturur ve yazılanları dosyaya kaydeder.

  $ tac file  # cat'in tersi

  $ rev file # satırlar ters çevrilir ve basılır

  $ sort file # satırları sıralayarak basar

  $ nl file # satırları numaralandırarak basar

  $ paste file1 file2 # satırları yanyana basar
```
```shell

  $ grep word file  # istenilen ifadeyi arayacaktır

  $ tr a-z 1 < file # tüm küçük harfleri 1 yapar

  $ diff -y file1 file2 #dosyadaki farkları gösterecektir

  $ find path word  # dosyayı dizinde arar

  $ find / ctime 2  # 2 gün önce değişmiş dosyalar görüntülenir

  $ find / -name filename -exec rm {} \;  
  # Bulunan dosya {}'e parametre olarak gönderilir exec'den sonra çalıştırılır.

  $ find / -name filename | xargs rm -rf filename
```
```shell

  $ shred -n 5 --verbose
  # -n 5 defa uygula dosyaya rasgele bitler eklenerek kurtarılması engellenir.

  $ shred -n 5 -u -v file
  # -n 5 kez uygula -u işlem sonu sil -v göster

  $ pushd /dizin1 ; pushd /dizin2
  # bu şekilde dizinleri belileyip iki dizin arasında, pushd diyerek çalışabiliriz.
  # popd komutuyla da o dizine gider orada kalırız

  $ env # O anki ortam değişkenlerini gösterir
```
```shell

  $ pwd ; cd Desktop # iki komutu aynı anda çalıştıracaktır bunu sağlayan ';'

  $ whatis cd # Ne işe yaradığını gösterecektir

  $ apropos cd # man -k ile aynı işi yapar cd'nin geçtiği yardım sayfalarını verir.

  $ uname -a #  kernel sürümünü bize verir

  $ cal # takvim

  $ hostname #  host

  $ w # Hangi kullanıcı hangi uygulamayı çalıştırdıgını verir

  $ who #Kullanıcıyı verir

  $ uptime  # zamanı verir

  $ whereis # yardım ve kaynak dosyası verilir

  $ which echo  # dosya yolunu belirtir

  $ locate myFile # belirtilen dosyanın yolunu bulur içerisinde kelime varsa onuda bulur.
```
```shell

  $ dmidecode -t processor  # donanım özelliklerini verir

  $ cat /proc/zoneinfo  # Sanal dosya sisteminden bilgi alınabilir

  $ fdisk -l # disk bölümlerini görebiliyoruz

  $ df  # disk kullanımını gösterecektir

  $ free  # kullanılan bellek miktarını gösterecektir

  $ hdparm /dev/sdb1 # hardisk bilgisi verir

  $ modinfo usbtouchscreen  # linux kernel bilgisini verir
```
```shell

  $ history # kullanılan komutlar kaydedilir buradan ulaşılabilir

  $ traceroute google.com #tracepath google.com

  $ ifconfig -a

  $ ping www.google.com

  $ nslookup www.google.com

  $ iptables
```
```shell

  $ sudo fdisk -l

  $ sudo umount /dev/sd..

  $ mkfs.vfat -n 'MyUSB' -I /dev/sdb1 #disk formatlamayı sağlar

  $ sudo mkdir /media/myUSB

  $ sudo mount /dev/sdb1 /media/myUSB #mount etmeyi sağlar

  $ sudo dd bs=4M if=myISO.iso of=/dev/sdb1 #Kolayca bootable disk oluşturabilirsiniz

```
```shell
  $ strace  # Sistem çağırıları kontrol edilebilir
            # örnek $ strace -ls yada -myCFile.out
```
> to be continued…
