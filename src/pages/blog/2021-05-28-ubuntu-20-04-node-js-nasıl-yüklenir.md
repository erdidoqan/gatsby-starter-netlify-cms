---
templateKey: blog-post
title: Ubuntu 20.04 Node.js Nasıl Yüklenir
date: 2021-05-28T01:13:05.954Z
description: Node.js, sunucu tarafı programlama için bir JavaScript tabanlı bir
  geliştirme araçıdır. Geliştiricilerin, tarayıcı tabanlı web geliştirmeden
  zaten aşina olduğumuz bir dil olan JavaScript kullanarak ölçeklenebilir
  back-end işlevselliği oluşturmalarına olanak tanır. Node.js ve npm ubuntu
  20.04 kurulum
featuredpost: true
featuredimage: /img/nodejs-logo_hd.png
tags:
  - npm
  - node
  - nodejs
  - ubuntu
---
![Node.js ve npm ubuntu 20.04 kurulum](/img/nodejs-logo_hd.png)



Node.js ve npm ubuntu 20.04 kurulum en hızlı nasıl yapabilirsiniz. Sunucu tarafında en kolay ve hızlı kurulum yollarını aşağıda en detaylı halini sizlere paylaşacağım.

Bu kılavuzda, bir Ubuntu 20.04 sunucusuna Node.js'yi kurmanın üç farklı yolunu göstereceğiz:

* Node.js paketini Ubuntu’nun varsayılan yazılım deposundan yüklemek için `apt` kullanmak
* node.js paketinin belirli sürümlerini yüklemek için alternatif bir PPA yazılım deposuyla `apt` kullanma
* Node Version Manager olan `nvm`'yi kurmak ve onu Node.js'nin birden çok sürümünü kurmak ve yönetmek için kullanmak

## 1. Seçenek - Varsayılan Depolardan Apt ile Node.js'yi Yükleme

Ubuntu 20.04, varsayılan depolarında birden çok sistemde tutarlı bir deneyim sağlamak için kullanılabilen bir Node.js sürümü içerir. Depolardaki sürüm 10.19'dur. Bu en son sürüm olmayacak, ancak dil ile hızlı denemeler için kararlı ve yeterli olmalıdır.

Bu sürümü almak için apt paket yöneticisini kullanabilirsiniz. Önce şunu yazarak yerel paket dizininizi yenileyin:

```asp
sudo apt update
```

Ardından Node.js'yi yükleyin:

```
sudo apt install nodejs
```

Node sürümünü sorgulayarak yüklemenin başarılı olup olmadığını kontrol edin:

```
nodejs -v
```

Paketler ihtiyaçlarınızı karşılıyorsa, Node.js ile kurulum yapmak için yapmanız gereken tek şey budur. Çoğu durumda, Node.js paket yöneticisi olan npm'yi de kurmak isteyeceksiniz. Bunu, apt ile npm paketini yükleyerek yapabilirsiniz:

```
sudo apt install npm
```

Bu, Node.js ile kullanılacak modülleri ve paketleri kurmanıza olanak tanır.

Bu noktada, `apt` ve varsayılan Ubuntu yazılım havuzlarını kullanarak Node.js ve `npm`'yi başarıyla yüklediniz. Sonraki bölüm, Node.js'nin farklı sürümlerini yüklemek için alternatif bir havuzun nasıl kullanılacağını gösterecektir.

## 2. Seçenek - Bir NodeSource PPA Kullanarak Node.js'yi Apt ile Yükleme

Node.js'nin farklı bir sürümünü yüklemek için NodeSource tarafından sağlanan bir PPA'yı (kişisel paket arşivi) kullanabilirsiniz. Bu PPA'lar, resmi Ubuntu depolarından daha fazla Node.js sürümüne sahiptir. Node.js v10, v12, v13 ve v14, yazıldığı tarihte mevcuttur.

İlk olarak, paketlerine erişmek için PPA'yı kuracağız. 14.x'i tercih ettiğiniz sürüm dizesiyle (farklıysa) değiştirdiğinizden emin olarak, tercih ettiğiniz sürüm için yükleme komut dosyasını almak için ana dizininizden curl'ü kullanın.

```
cd ~
curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh

```

Mevcut sürümler hakkında daha fazla bilgi için [NodeSource](https://github.com/nodesource/distributions/blob/master/README.md) belgelerine bakın.

İndirilen komut dosyasının içeriğini `nano` (veya tercih ettiğiniz metin düzenleyiciyle) ile inceleyin:

```
nano nodesource_setup.sh
```

Komut dosyasının güvenli olduğundan emin olduğunuzda, düzenleyicinizden çıkın ve komut dosyasını `sudo` ile çalıştırın:

```
sudo bash nodesource_setup.sh
```

Paketi `-v` sürüm işaretiyle çalıştırarak yeni sürümü yüklediğinizi doğrulayın:

```
node -v
```

NodeSource nodejs paketi hem düğüm ikilisini hem de npm'yi içerir, bu nedenle npm'yi ayrı olarak kurmanıza gerek yoktur.

Bu noktada apt ve **NodeSource PPA** kullanarak Node.js ve npm'yi başarıyla yüklediniz. Sonraki bölümde, Node.js'nin birden çok sürümünü yüklemek ve yönetmek için Düğüm Sürümü Yöneticisinin nasıl kullanılacağı gösterilecektir.