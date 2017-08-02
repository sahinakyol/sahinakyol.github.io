---
layout: post
title:  "Docker"
date:   28.06.2017
categories: [Docker]
tags:
 - docker,container
---

**Docker Nedir**

Docker, LXC (linux container) temel alınarak geliştirilmiş açık kaynaklı bir sanallaştırma aracıdır.
Aslında sanallaştırma demek tam olarak doğru değildir bildiğimiz sanallaştırma araçlarından ziyade container,
görevi yapar.Vmware,Hyper-V,Virtualbox etc. gibi araçlar tam sanallaştırma yaparken (Yapıları itibariyle farklılıkları vardır birbirlerinden.) container'lar daha izole tüm bağımlılıklarını kendi içine toplamış en az sistem kaynağı harcayan yapılardır.Docker ile imajlar oluşturarak aynı sisteme yeni şeyler ekleyebilir,çıkarabilir ve dağıtabiliriz.
Tam olarak aynısı diyemem ama LXC ile docker gibi izole sistemler oluşturabiliriz,
fakat hardcore bir linux kullanıcısı isek bu mümkün gibi.

**Docker Kurulumu**

[Docker Installation Instructor](https://docs.docker.com/engine/installation/linux/ubuntulinux/) buradaki yönergeleri izleyerek kurabilirsiniz(16.04 Ubuntu için daha farklı bir sistem kullanıyorsanız farklı bir sistem seçmelisiniz)

```perl
  $ docker run hello-world
  # This message shows that your installation appears to be working correctly.
```
Docker komutları çalıştırırken bizden sürekli root yetkisi istemektedir,bunun için
**_sudo_** kullanmalıyız prefix olarak komutlarımızda yada alternatif bir yöntem olarak,
[docker group](https://docs.docker.com/engine/installation/linux/linux-postinstall/) oluşturabiliriz.

### Docker First Container

```perl
  $ docker run ubuntu:latest /bin/bash
  #Komut çaıştıldıktan sonra hiçbirşey olmayacaktır.
  $ docker ps -a
  #Çalışan containerları göreceksiniz
  $ docker run -i -t ubuntu:latest /bin/bash
  #Komutu çaıştırdığınızda containerin içerisinde olacaksınız
```
- **run** - Container çalıştır.
- **-t**  - Terminal.
- **-i**  - Input açık tut.
- **ubuntu:latest** - Ubuntu son sürümü kullan.
- **/bin/bash** - Bash Shell çalıştır.

Containerımızdan çıkmak istersek eğer **_Ctrl+d_** kullanmamız yeterli.
Tekrar kontrol edersek **_docker ps -a_** komutu ile;

```perl
  $ docker ps -a
  #Iki tane container göreceğiz güncel olan containerın ID'sini aşağıdaki komut ile çalıştıralım.
  $ docker diff RECENT_CONTAINER_ID
  # C /user
  # A /user/.bash_history gibi bir çıktı alacağız bunun anlamı ilk kullanılan,
  # container ile son yapılan dosya değişiklikleri farkını gösteriyor.Yani bash history oluşturmuşuz.  
```
```perl

  $ docker run -i -t ubuntu:latest /bin/bash
  #Bir şeyler yükleyebiliriz sistemimize
  user@111111c11t $ apt-get update
  user@111111c11t $ apt-get ruby
  # Ctrl+d
  $ docker ps -a #Recent Container
  $ docker diff RECENT_CONTAINER_ID
  #Bissürü bissürü dosya :)
```
Eğer istenirse commitleyebiliriz değişiklik yaptığımız containerı

```perl
  $ docker commit 111111c11t user/docker-example:0.1
  #11111111122222222222222233333333333333333444444444444
  #Uzunca bir hash başarılı hash mesejı alacaksınız.
  $ docker images
  #Imajlarımızı görebiliriz
```

### Dockerfile ile Server Oluşturma

**Default File**
Nginx configurasyon dosyası oluşturuyoruz.

```perl
  $ touch default
  $ vim default
    # server {
    #   root /var/www;
    #   index index.html index.htm;
    #   server_name localhost;
    #   location /home/user/Desktop/docker/example1 {
    #   try_files $uri $uri/ /index.html;
    #   }
    # }
```
```perl
  $ pwd
    # /home/user/Desktop/docker/example1
  $ touch Dockerfile
  $ vim Dockerfile
    # FROM ubuntu:latest
    # RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
    # RUN apt-get update
    # RUN apt-get -y install nginx
    # RUN echo "daemon off;" >> /etc/nginx/nginx.conf
    # RUN mkdir /etc/nginx/ssl
    # ADD default /etc/nginx/sites-available/default
    # EXPOSE 80
    # CMD ["nginx"]
```
- **_FROM_**  - Kurmak istediğimiz linux imajını burada belirtiriz.
- **_RUN_** - Bu komut ile çalıştırmak istediğimiz shell komutunu yazarız.
- **_ADD_** - Host makinemizden herhangi bir dosyayı container'a kopyalamamızı sağlar.
- **_EXPOSE_**  - Belirtilen porta host makineden erişebilmeyi sağlar.Birden fazla port sayısı olabilir.
- **_CMD_** - Container'da komut çalıştırmayı sağlar.

Bu şekilde de Dockerfile oluşturabilirsiniz aynı görevi yapacaktır;

```perl
  FROM ubuntu:latest
  MAINTAINER Name <me@mail.com>
  LABEL Description="...."
  RUN apt-get update\
  #Buraya kurmak istediginiz paket komutlarini yaziniz.
  VOLUME /..
```
```perl
  $ docker build -t my-nginx-container .
```
- **_'-t'_**  - tag anlamına gelmektedir imajı isimlendirmemizi sağlar.
- **_'.'_** - bulunulan dosya içerisindeki dosyaları belirtir.
- **_'build'_** - Build ediyoruz Dockerfile'ımızı.
- **_'-d'_**  - detach anlamına gelmektedir.
- **_'-v /path/to/host/dir:/path/to/container/dir:rw'_**  - rw(Read-Write) yada ro(Read-Only)

```perl
  $ docker run -p 80:80 -d my-nginx-container
  # 1111111111111111112222222222222222222333333333344444444 Succes
  # Succes gibi bir hash dönecektir.
```
```perl
  $ curl localhost/index.html
  <html>
    <head><title>403 Forbidden</title></head>
    <body bgcolor="white">
      <center><h1>403 Forbidden</h1></center>
      <hr><center>nginx/1.1.19</center>
    </body>
  </html>
```
```perl
  $ docker stop 111111c11t
  $ echo "Hola To do!" >> /home/core/share/index.html
  #Host makinede path içerisindeki index.html dosyasına yazılır
```
```perl
  $ docker run -v /home/core/share:/var/www:rw -p 80:80 -d my-nginx-container
```
```perl
  $ curl localhost
  # Hola To do!
```
```perl
  $ docker inspect CONTAINER_ID
  #Container hakkında bilgi verir.
```

### Containers Linking

```perl
  $ docker run -p 5656:5656 -name postgres -d my-postgres-image
```
```perl
  $ docker run -p 80:80 -link postgres:db -d my-application-image
```
Eğer böyle bir yapı oluşturacaksak uygulama içerisinde;
**_DB_PORT_3306_TCP_ADDR=172.17.0.0_** ve **_DB_PORT_5606_TCP_PORT=5656_** bu şekilde belirtmeliyiz.

**Docker Image to DockerHub**

Oluşturduğunuz Dockerfile öncelikle github'a push etdikten sonra;
[DockerHub](https://hub.docker.com/) 'da
Sign Up olun.

![alt text]({{ site.url | append:site.baseurl }}/images/docker/docker-1.png)

![alt text]({{ site.url | append:site.baseurl }}/images/docker/docker-2.png)

![alt text]({{ site.url | append:site.baseurl }}/images/docker/docker-3.png)

![alt text]({{ site.url | append:site.baseurl }}/images/docker/docker-4.png)

Build details'den succes olup olmadığına bakabiliriz.Daha sonra siz veya bir başkası pull edebilir image'i.

```perl
    $ docker pull sah1n/my-nginx-container
    $ sudo docker run -i -t sah1n/my-nginx-container:latest /bin/bash
```
Peki containerları silmek ve docker'ı durdurmak istersek.

```perl
  $ docker rm CONTAINER-ID
  $ docker rm --force $(docker ps -a --quiet)
  # $(docker ps -a --quiet) Burada eğer bir sürü containerımız var ise hepsini birden temizlememizi sağlar.
  $ docker rmi $(sudo docker images --quiet)
  # $(sudo docker images --quiet) Burada eğer bir sürü images var ise hepsini birden temizlememizi sağlar.
  $ service docker stop     
```
```perl
  $ docker port CONTAINER | CONTAINER_ID
  # port ve ıp vericektir
```
Eğer herhangi bir docker imajına ihtiyacımız var ise kolayca arayabiliriz.

```perl
  $ docker search rails
# rails                 Rails is an open-source web application fr...   690  [OK]       
# bluebu/rails-alpine   rails-alpine with different ruby version, ...   6    [OK]
# asux/rails            Docker base image: Rails + Puma                 5    [OK]
# bitnami/rails         Bitnami Ruby on Rails Docker Image              3    [OK]
# ...
```

#### Tips & Tricks & Notes & Exercices

```perl
  $ docker pull busybox
  $ docker images
  $ docker run busybox
  $ docker container run busybox ls -l
  # Container dosya dizin yetkilerini gösterecektir.
  $ docker run -it busybox sh
  # / # uptime
  # 00:00:00 up 0 days,  0:00,  0 users,  load average: 0.00, 0.00, 0.00
  $ docker rm $(docker ps -a --quite -f status=exited)
```
- **_-f_**  - Filter parametresi.
- Eğer bir distro seçecekseniz *alpine* kelimesini aramalısınız boyut olarak en küçük,
olan o olacaktır.
- [BusyBox](https://en.wikipedia.org/wiki/BusyBox) nedir?

> to be continued…

##### References :
+ [Getting Started with Docker](https://serversforhackers.com/getting-started-with-docker)
