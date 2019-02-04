---
ID: 705
post_title: 'PHP ile içerik yönetim sistemi &#8211; 7 Temalar ve Admin paneli'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-7-temalar-ve-admin-paneli/
published: true
post_date: 2014-08-25 16:48:08
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/car-spray-painting.jpg"><img class="alignnone size-full wp-image-706" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/car-spray-painting.jpg" alt="car-spray-painting" width="438" height="332" /></a>

Görüntü sayfalarımız neredeyse bitti. Kullanıcıya göstermemiz gereken iki tip sayfa var. Kullanıcı eğer adminse, şifreyle giriş yaptıysa, yönetim yani admin paneli. Eğer giriş yapmadıysa, herkesin göreceği sayfa ve menüler. Eğer o sayfa sistemde yoksa, 404 yani sayfa bulunmadı mesajı göstermeliyiz.

Kullanıcıların göreceği sıradan sayfaların bileşenleri neler olacak? Bunları zaten HTML5 serisinde gözden geçirmiştik. Logo veya Site başlığı. Kategorilerin listesi. (Kategoriye tıklandığı zaman o kategori içerisindeki girdileri gösterecek.) Footer içinde de copyright bilgisi. Aslında daha çok bileşen eklenebilir ancak biz şimdilik bunları ekleyelim.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-25-19.20.51.png"><img class="alignnone size-large wp-image-707" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-25-19.20.51.png?w=680" alt="Ekran Resmi 2014-08-25 19.20.51" width="680" height="623" /></a>

[code language="html"]
&lt;!doctype html&gt;
&lt;html class=&quot;no-js&quot; lang=&quot;en&quot;&gt;
  &lt;head&gt;
    &lt;meta charset=&quot;utf-8&quot; /&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot; /&gt;
    &lt;title&gt;Site Başlığı&lt;/title&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;css/foundation.css&quot; /&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;css/app.css&quot; /&gt;
    &lt;script src=&quot;js/vendor/modernizr.js&quot;&gt;&lt;/script&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;header&gt;
        &lt;div class=&quot;row&quot;&gt;
            &lt;div class=&quot;large-3 large-centered columns page-title&quot;&gt;&lt;h1&gt;Site Başlığı&lt;/h1&gt;&lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;row&quot;&gt;
            &lt;div class=&quot;large-12 columns&quot;&gt;
                &lt;ul class=&quot;nav&quot;&gt;
                  &lt;li&gt;&lt;a href=&quot;/&quot;&gt;Home&lt;/a&gt;&lt;/li&gt;
                  &lt;li&gt;&lt;a href=&quot;/about/&quot;&gt;About&lt;/a&gt;&lt;/li&gt;
                  &lt;li&gt;&lt;a href=&quot;/work/&quot;&gt;Work&lt;/a&gt;&lt;/li&gt;
                  &lt;li&gt;&lt;a href=&quot;/clients/&quot;&gt;Clients&lt;/a&gt;&lt;/li&gt;
                  &lt;li&gt;&lt;a href=&quot;/contact/&quot;&gt;Contact&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/header&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-5 large-centered columns page-title&quot;&gt;
            &lt;h2&gt;Kategori Başlığı&lt;/h2&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;article&gt;
            &lt;h3&gt;Yazı Başlığı&lt;/h3&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. &lt;a href=&quot;view.php&quot;&gt;Devamını Oku&lt;/a&gt;&lt;/p&gt;&lt;/p&gt;
            &lt;small&gt;10/05/1984 23:59:59&lt;/small&gt;
        &lt;/article&gt;
        &lt;article&gt;
            &lt;h3&gt;Yazı Başlığı&lt;/h3&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. &lt;a href=&quot;view.php&quot;&gt;Devamını Oku&lt;/a&gt;&lt;/p&gt;&lt;/p&gt;
            &lt;small&gt;10/05/1984 23:59:59&lt;/small&gt;
        &lt;/article&gt;
        &lt;article&gt;
            &lt;h3&gt;Yazı Başlığı&lt;/h3&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. &lt;a href=&quot;view.php&quot;&gt;Devamını Oku&lt;/a&gt;&lt;/p&gt;&lt;/p&gt;
            &lt;small&gt;10/05/1984 23:59:59&lt;/small&gt;
        &lt;/article&gt;
        &lt;article&gt;
            &lt;h3&gt;Yazı Başlığı&lt;/h3&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. &lt;a href=&quot;view.php&quot;&gt;Devamını Oku&lt;/a&gt;&lt;/p&gt;&lt;/p&gt;
            &lt;small&gt;10/05/1984 23:59:59&lt;/small&gt;
        &lt;/article&gt;
    &lt;/div&gt;
    &lt;footer class=&quot;row genel-footer&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            COPYRIGHT 2014 meraklibilisimci.com
        &lt;/div&gt;
    &lt;/footer&gt;
    &lt;script src=&quot;js/vendor/jquery.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;js/foundation.min.js&quot;&gt;&lt;/script&gt;
    &lt;script&gt;
      $(document).foundation();
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
[/code]

Peki admin panelinde ne olacak? Üstte uzun tam sayfa bir menü, menüde meraklicms yazısı, admine girdiğimizi anlayalım diye, bir navigasyon, girdiler, kategoriler ve dosyalar diye. Her kategori için yapılacak işlemlerin gösterilebildiği açılır, kapanır menü. Tüm girdiler, yeni girdi ekle gibi. En sağa yaslı olarak kulllanıcı adının yazdığı bir isim. Ona tıklandığı zaman, profil sayfası açılır ve o profil sayfasından kendi kullanıcı adını ve şifresini değiştirebilir. Bir de yine üst menüde en sağda ayarlar diye bir link olsun ve sitemizle ilgili, site başlığı, açıklaması, copyright bilgisi gibi sabit şeyleri ordan değiştirelim.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-25-19.44.30.png"><img class="alignnone size-large wp-image-708" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-25-19.44.30.png?w=680" alt="Ekran Resmi 2014-08-25 19.44.30" width="680" height="385" /></a>

[code language="html"]
&lt;!doctype html&gt;
&lt;html class=&quot;no-js&quot; lang=&quot;en&quot;&gt;
&lt;head&gt;
    &lt;meta charset=&quot;utf-8&quot; /&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot; /&gt;
    &lt;title&gt;Merakli CMS Yönetim Paneli&lt;/title&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;css/foundation.css&quot; /&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;css/app.css&quot; /&gt;
    &lt;script src=&quot;js/vendor/modernizr.js&quot;&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
    
    &lt;nav class=&quot;top-bar&quot; data-topbar&gt;
        &lt;ul class=&quot;title-area&quot;&gt;
 
            &lt;li class=&quot;name&quot;&gt;
                &lt;h1&gt;
                    &lt;a href=&quot;#&quot;&gt;
                        Merakli CMS
                    &lt;/a&gt;
                &lt;/h1&gt;
            &lt;/li&gt;
            &lt;li class=&quot;toggle-topbar menu-icon&quot;&gt;&lt;a href=&quot;#&quot;&gt;&lt;span&gt;menu&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;
        &lt;/ul&gt;
        &lt;section class=&quot;top-bar-section&quot;&gt;
 
            &lt;ul class=&quot;center&quot;&gt;
                &lt;li class=&quot;divider&quot;&gt;&lt;/li&gt;
                &lt;li class=&quot;has-dropdown&quot;&gt;
                    &lt;a href=&quot;#&quot;&gt;Girdiler&lt;/a&gt;
                    &lt;ul class=&quot;dropdown&quot;&gt;
                        &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Tüm girdiler &amp;rarr;&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Yeni girdi&lt;/a&gt;&lt;/li&gt;
                    &lt;/ul&gt;
                &lt;/li&gt;
                &lt;li class=&quot;divider&quot;&gt;&lt;/li&gt;
                &lt;li class=&quot;has-dropdown&quot;&gt;
                    &lt;a href=&quot;#&quot;&gt;Kategoriler&lt;/a&gt;
                    &lt;ul class=&quot;dropdown&quot;&gt;
                        &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Tüm kategoriler &amp;rarr;&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Yeni kategori&lt;/a&gt;&lt;/li&gt;
                    &lt;/ul&gt;
                &lt;/li&gt;
                &lt;li class=&quot;divider&quot;&gt;&lt;/li&gt;
                &lt;li class=&quot;has-dropdown&quot;&gt;
                    &lt;a href=&quot;#&quot;&gt;Dosyalar&lt;/a&gt;
                    &lt;ul class=&quot;dropdown&quot;&gt;
                        &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Tüm dosyalar &amp;rarr;&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Yeni dosya&lt;/a&gt;&lt;/li&gt;
                    &lt;/ul&gt;
                &lt;/li&gt;
            &lt;/ul&gt;
            &lt;ul class=&quot;right&quot;&gt;
                &lt;li class=&quot;divider&quot;&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Admin&lt;/a&gt;&lt;/li&gt;
                &lt;li class=&quot;divider&quot;&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Ayarlar&lt;/a&gt;&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/section&gt;
    &lt;/nav&gt;
 
 
    &lt;div class=&quot;row admin-baslik&quot;&gt;
        &lt;div class=&quot;large-3 columns&quot;&gt;
            &lt;h3&gt;Yeni yazı ekle&lt;/h3&gt;
            &lt;p&gt;Yeni yazı eklemek için bu formu ivedilikle doldurmalısınız.&lt;/p&gt;
        &lt;/div&gt;
        &lt;div class=&quot;large-9 columns admin-icerik&quot;&gt;

&lt;form action=&quot;add.php&quot; method=&quot;post&quot;&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Başlık
        &lt;input id=&quot;title&quot; name=&quot;title&quot; type=&quot;text&quot; placeholder=&quot;Başlık&quot; /&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;İçerik
        &lt;textarea id=&quot;content&quot; name=&quot;content&quot; placeholder=&quot;İçerik&quot;&gt;&lt;/textarea&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Kategoriler
        &lt;select id=&quot;category&quot; name=&quot;category&quot;&gt;
                &lt;option value=&quot;&lt;?=$category['id']?&gt;&quot;&gt;PHP&lt;/option&gt;
        &lt;/select&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;large-12 columns&quot;&gt;
          &lt;button type=&quot;submit&quot;&gt;Submit&lt;/button&gt;
      &lt;/div&gt;
  &lt;/div&gt;
&lt;/form&gt;
        &lt;/div&gt;
 
    &lt;/div&gt;
 
 
    &lt;footer class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;hr/&gt;
            &lt;div class=&quot;row&quot;&gt;
                &lt;div class=&quot;large-6 columns&quot;&gt;
                    &lt;p&gt;&amp;copy; Copyright 2014 Meraklibilisimci.com&lt;/p&gt;
                &lt;/div&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/footer&gt;
 

    
    &lt;script src=&quot;js/vendor/jquery.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;js/foundation.min.js&quot;&gt;&lt;/script&gt;
    &lt;script&gt;
    $(document).foundation();
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
[/code]

Bu iki sayfamızı da hallettikten sonra, html sayfası olarak yazacağımız hiçbirşey kalmadı diyebiliriz. Bir sonraki aşamada, lego parçalarını birleştireceğiz, yani işin en zor ve en zevkli kısmı başlıyor.

Proje dosyalarımızın şu anki aşaması da şurda:

<a href="https://github.com/mtkocak/merakli/tree/f195b3007cf1fd032adcbca0533423fca3417f8a">https://github.com/mtkocak/merakli/tree/f195b3007cf1fd032adcbca0533423fca3417f8a</a>