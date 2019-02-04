---
ID: 45
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-12 Düzgün dizin
  yapısı
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-12-duzgun-dizin-yapisi/
published: true
post_date: 2017-07-19 18:40:25
---


<p>Bu yazı <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-11-bile%C5%9Fenler-composer-ve-json-87af0587d00e" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-11 Bileşenler, Composer ve JSON</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-11-bile%C5%9Fenler-composer-ve-json-87af0587d00e[/embed]
<p>Buraya kadar composer kullanarak bileşenleri nasıl yükleyip erişebileceğimizi öğrendik. Şimdi sıra geldi onu kullanmaya. Bu yazıda PHPUnit anlatacağım, ancak herşeyden önce doğru dürüst bir yazılım paketi nasıl olur kısaca ona değineceğim. Adım adım ilerleyeceğiz. Eğer yoksa hemen GitHub hesabı kurmanızı öneriyorum. Kitabımda GitHub kurulumunu, nasıl üye olunacağını anlatmıştım.</p>
<h4>Doğru Dürüst Dizin Yapısı</h4>
<p>Doğru dürüst bir projemiz olsun istiyorsak dizin yapısına dikkat etmemiz gerekiyor. İster JavaScript, ister PHP, hangi dilde yazılım üretiyorsak üretelim, her zaman söylediğim gibi, bazı iyi pratiklere dikkat etmemiz lazım.</p>
<p>Her türlü projede en az iki tane dizinimizin olması şart: src ve tests. Src dizini adı üstünde source yani kaynak kodumuzun bulunduğu dizin olup, tests ise, PHPUnit veya başka bir test aracı kullanarak yazacağımız testlerin bulunacağı dizindir.</p>
<p>Örneğin güzel bir araç olan <a href="https://github.com/thephpleague/json-guard" target="_blank">thephpleague/json-guard</a> paketinin dizin yapısına bakalım.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/07/39d26-1phge_byugzxbmkoo-9e-bw.png">

<figcaption class="wp-caption-text">Örnek paket</figcaption></figure><p>Bu paket üç dizinden oluşuyor.</p>
<ol>
<li>Docs: İsteğe bağlı olarak projemizin dokümanlarını tutabileceğimiz dizin.</li>
<li>Src: Kesinlikle ve kesinlikle kaynak kodlarımızı tutmamız gereken dizin.</li>
<li>Tests: Testlerimizi bulunduracağımız dizin.</li>
</ol>
<p>Her açık ya da kapalı kaynaklı projede olması şart olan dosyalar da var. Bunlara da tek tek bakalım. Sonu md ile biten dosyalar markdown formatındadırlar. Bu formatı daha sonra detaylıca anlatacağım. Bir de paketlerimiz tüm dünya tarafından kullanılsın istiyorsak kesinlikle yazı içeren dosyalarımızı ingilizce yazalım.</p>
<ol>
<li>README.md: Her projede olması kesin şart olan dosya, projemizi kısaca tanıttığımız yer. Yazılımımızın yüklenmesi, nasıl kullanılacağı, kodun nasıl test edileceği gibi değişik yönergeleri de içerir. İyi README.md yazmak bir sanattır. O yüzden buna da detaylıca bir yazı ile değineceğim. (gerekli)</li>
<li>LICENSE.md: Yazılımımızı hangi yazılım lisansı ile dağıttığımızı gösteren dosya. GPL olur, MIT olur ama ne olursa olsun, lisans bu dosyada durur.</li>
<li>CHANGELOG.md: Projede yaptığımız değişiklikleri belirli bir formata göre yazdığımız dosya. (isteğe bağlı)</li>
<li>CONTRIBUTING.md: Projenize katkı yapmak isteyen kişilere söylemek istediklerinizi buraya yazıyorsunuz. (isteğe bağlı)</li>
</ol>
<p>Diğer dosyalar belirli araçları yönlendiren ayar dosyaları olduğundan onları daha sonra detaylıca anlatacağım. Ama kısaca değinmek gerekirse:</p>
<ol>
<li>.gitignore: Github aracının belli dosyaları görmezden gelmesini istediğimizde doldurmamız gereken dosya.</li>
<li>.gitatrributes: Yine Github aracının belli dizin ve dosyalara bizim isteğimize göre özellikler atamasını sağlayan araç. Testlerin server’a indirilmemesini sağlıyor. (Not: Çok önemli. Asla, asla, asla testlerinizi production yani canlıda çalıştırmayın, test dosyalarını ve araçlarını canlıya almayın.)</li>
<li>composer.json: composer paket yöneticisi için paketimizi tanıtmaya yarayan json dosyası.</li>
<li>phpunit.xml.dist: PHPUnit aracını yönlendiren xml dosyası.</li>
<li>.travis.yml, .scrutinizer.yml, CI yani sürekli entegrasyon araçlarını yönlendiren dosyalardır. Çok ileri bir konu, kitabın sonunda anlatıcam.</li>
<li>.editorconfig, kullandığımız IDE yazılımının kod stilini ayarlayan dosyadır.</li>
</ol>
<p>Şimdilik bu kadar. Bir sonraki yazıda test yazmayı anlatmayı düşünüyorum.</p>