---
ID: 306
post_title: İçerik bölümlerini ekleyelim
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/icerik-bolumlerini-ekleyelim/
published: true
post_date: 2012-10-22 20:38:39
---
Geriye 3 tane bölümümüz kaldı. Daha sonra sitemiz bitiyor. Hakkımızda, Duyurular ve Kurumsal bölümlerini oluşturacağız.

[caption id="attachment_309" align="alignnone" width="300"]<a href="http://html5doctor.com/designing-a-blog-with-html5/"><img class="size-medium wp-image-309" title="http://html5doctor.com/designing-a-blog-with-html5/" alt="http://html5doctor.com/designing-a-blog-with-html5/" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5-article-outline.gif?w=300" height="300" width="300" /></a> http://html5doctor.com/designing-a-blog-with-html5/[/caption]

Hakkımızda bölümü üç ayrı yazıdan oluşacak. Şirketimiz hakkında, referanslar, tarihçe ve kalite felsefemiz. Bunları tek bir bölümde (section) ama 3 ayrı makalede oluşturacağız.

Duyurular bölümü ise bir blog gibi olacak. Tıpkı facebook veya twitter'da paylaşıldığı gibi haber formatında olacak. Devam linkine tıklandığında yazının devamı görülecek.

Kurumsal bölümü ise şirket ile ilgili bilgileri barındıracak. Yine blog gibi çalışacak. Kenarda en son makalelerin başlantılarını içeren bir bağlantı listesi olacak. Burada da şirketin finansal tabloları gibi TTK'nın emrettiği kurumsal bilgileri barındıracağız.

Şimdi hakkımızda bölümünün makaleleri ile işe başlayalım ve boş bir makale oluşturalım. Makalelerimizin yine Google tarafından tanıması için microdata kullanacağız.
<pre><code>&lt;section&gt;
    &lt;article itemscope itemtype="http://schema.org/Article"&gt;
      &lt;header&gt;
      &lt;span itemprop="name"&gt;&lt;a name="baslik"&gt;&lt;h1&gt;Başlık&lt;/h1&gt;&lt;/a&gt;&lt;/span&gt;
      &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-29" pubdate&gt;29 Ekim 2012&lt;/time&gt;&lt;/p&gt;
      &lt;/header&gt;
      &lt;p&gt;İçerik&lt;/p&gt;
    &lt;/article&gt;
&lt;/section&gt;
</code></pre>
Burada a etiketinin bir kullanımını daha görüyoruz. Href özelliği yani hedefi olmayan a etiketi, sayfamızın spesifik bölümlerine hakkimizda.html#baslik seklinde link verebilmemizi sağlar. Yani href olarak bu adresi kullandığımız bir a etiketi

Yine birden fazla makalemizi ayırmak için bir bağlantı lisesine ihtiyacımız var. Bunu da yan tarafta tutacağız.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.47.47-PM.png"><img class="alignnone size-full wp-image-313" title="Screen Shot 2012-10-22 at 10.47.47 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.47.47-PM.png" height="223" width="245" /></a>

Ürünler bölümündeki listeye benzeyecek.
<pre><code>&lt;nav class="span3 yanliste"&gt;
    &lt;ul class="nav nav-list"&gt;
        &lt;li&gt;Hakkımızda&lt;/li&gt;
        &lt;hr&gt;
        &lt;li&gt;&lt;a href="hakkimizda.html#sirketimiz"&gt;Şirketimiz&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="hakkimizda.html#referanslar&gt;Referanslarımız&lt;/a&gt;&lt;/li&gt;
&lt;/li&gt;
        &lt;li&gt;&lt;a href="hakkimizda.html#tarihce&gt;Tarihçe&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="hakkimizda.html#kalitefelsefemiz"&gt;Kalite Felsefemiz&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
&lt;/nav&gt;
</code></pre>
Şimdi içeriklerimizi yazıp yazımıza dahil edelim.
<pre><code>&lt;section&gt;
    &lt;article itemscope itemtype="http://schema.org/Article"&gt;
        &lt;header&gt;
            &lt;span itemprop="name"&gt;&lt;a name="sirketimiz"&gt;&lt;h1&gt;Şirketimiz&lt;/h1&gt;&lt;/a&gt;&lt;/span&gt;
            &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-29" pubdate&gt;29 Ekim 2012&lt;/time&gt;&lt;/p&gt;
        &lt;/header&gt;
        &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. İstanbul, Sirkeci de faaliyet göstermekte olan baskı şirketidir. Başlıca faaliyet alanları, davetiye, broşür, el ilanı ve poster üretimi olan firma, aynı zamanda müşterilerine özel baskı çözümleri de sunmaktadır. Hali hazırda kendi ajanda ürünlerini Radikal Ajanda  markasıyla pazarlayan şirket, aynı zamanda poster işleri yapan görsel sanatçılara da baskı işleri ile sponsor olmakta ve sanata ve santçıya destek olmaktadır. Şirket ayrıca üniversitelerin sanat ve görsel tasarım bölümleri ile birlikte tasarım yarışmaları yapmış ve birlikte projeler geliştirmiştir.&lt;/p&gt;
    &lt;/article&gt;
    &lt;article itemscope itemtype="http://schema.org/Article"&gt;
        &lt;header&gt;
            &lt;span itemprop="name"&gt;&lt;a name="referanslar"&gt;&lt;h1&gt;Referanslarımız&lt;/h1&gt;&lt;/a&gt;&lt;/span&gt;
            &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-15" pubdate&gt;15 Ekim 2012&lt;/time&gt;&lt;/p&gt;
        &lt;/header&gt;
        &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. olarak referanslarımızdan bazıları;
            &lt;ul&gt;
                &lt;li&gt;Açık Kaynak Maden Suları&lt;/li&gt;
                &lt;li&gt;Uranyum Yazılım&lt;/li&gt;
                &lt;li&gt;Yolgösteren Stratejik Danışmanlık&lt;/li&gt;
                &lt;li&gt;Özgür Yazılım Çöpçatanlık Hizmetleri&lt;/li&gt;
                &lt;li&gt;Atolye Atolyesi Sanat Galerisi&lt;/li&gt;
                &lt;li&gt;Sınırsız Çay Felsefe Klübü&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/p&gt;
    &lt;/article&gt;
    &lt;article itemscope itemtype="http://schema.org/Article"&gt;
        &lt;header&gt;
            &lt;span itemprop="name"&gt;&lt;a name="tarihce"&gt;&lt;h1&gt;Tarihçe&lt;/h1&gt;&lt;/a&gt;&lt;/span&gt;
            &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-14" pubdate&gt;14 Ekim 2012&lt;/time&gt;&lt;/p&gt;
        &lt;/header&gt;
        &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. 14 Mart 1971 yılında, İstanbul'da matbaacılıkta yeni teknolojilerin kullanımına yer açmak ve baskı hizmetlerine devrimci bir soluk getirmek amacıyla kurulmuştur. Bugüne kadar birçok sanat etkinliğinin hem sponsoru hem de düzenleyicisi olan şirket, görsel tasarım alanında birçok faaliyetlerde de buşunmuştur. Bugüne kadar birçok ödül alan firmamızın aldığı ödüllerden bazıları şunlardır:
            &lt;ul&gt;
                &lt;li&gt;1974 Balkan Matbaa Ödülleri Avrupa 3. sü&lt;/li&gt;
                &lt;li&gt;1982 Mimar Sinan Üniversitesi En İyi Baskı Ödülü&lt;/li&gt;
                &lt;li&gt;1994 Avrupa Güzel Sanatlar Derneği, Sanata Desten Ödülü&lt;/li&gt;
                &lt;li&gt;1998 Kırtasiyeciler Odası, En yenilikçi Matbaa Ödülü&lt;/li&gt;
                &lt;li&gt;2005 Görsel Sanatlar Derneği, Sanatın Dostu Ödülü&lt;/li&gt;
                &lt;li&gt;2011 Kalite Derneği, Kalite Özel Ödülü&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/p&gt;
    &lt;/article&gt;
    &lt;article itemscope itemtype="http://schema.org/Article"&gt;
        &lt;header&gt;
            &lt;span itemprop="name"&gt;&lt;a name="kalitefelsefemiz"&gt;&lt;h1&gt;Kalite Felsefemiz&lt;/h1&gt;&lt;/a&gt;&lt;/span&gt;
            &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-08" pubdate&gt;8 Ekim 2012&lt;/time&gt;&lt;/p&gt;
        &lt;/header&gt;
        &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. olarak biz, kalitenin ve tasarımın sadece bir süs veya iyi bir pr çalışması değil, şirketimizi var eden temel kavram olduklarına inanıyoruz. Alelade veya sıradan ürünler geliştirmek yerine, firmamız her ürününde sanatçı ve tasarımcı desteği almaya azami gayret göstermekte olup, inovasyon odaklı çalışarak kendi farkını ortaya koymakta ve her zaman tecrübesini yeni sanatçılarla ve tasarımcılarla paylaşmaya özen göstermektedir.&lt;/p&gt;
    &lt;/article&gt;
&lt;/section&gt;</code></pre>
Bu sayfamız için içeriklerimiz tamam. Şimdi sayfamızın nasıl göründüğüne bir bakalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.48.39-PM.png"><img class="alignnone size-full wp-image-314" title="Screen Shot 2012-10-22 at 10.48.39 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.48.39-PM.png" height="405" width="628" /></a>

Ancak biz yazıların ayrı ayrı, tab halinde görünmesini istiyoruz. Bunu yapmamıza Twitter Bootstrap kütüphanesi izin veriyor. Dokümanlara baktığımızda karşılaştığımız <a href="http://twitter.github.com/bootstrap/components.html">tabbable özelliği</a> işimizi görecektir:
<pre><code>
&lt;div class="tabbable"&gt; &lt;!-- Only required for left/right tabs --&gt;
  &lt;ul class="nav nav-tabs"&gt;
    &lt;li class="active"&gt;&lt;a href="#tab1" data-toggle="tab"&gt;Section 1&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#tab2" data-toggle="tab"&gt;Section 2&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;
  &lt;div class="tab-content"&gt;
    &lt;div class="tab-pane active" id="tab1"&gt;
      &lt;p&gt;I'm in Section 1.&lt;/p&gt;
    &lt;/div&gt;
    &lt;div class="tab-pane" id="tab2"&gt;
      &lt;p&gt;Howdy, I'm in Section 2.&lt;/p&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;
</code></pre>
Biz de sayfamızı bu hale getirelim. Çok sık kullandığım bir araç da W3C Checker. Yani eğer yazdığınız html kodunda bir hata varsa bunu otomatik olarak kontrol ediyor. Textmate programında mevcut:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-11.13.43-PM.png"><img class="alignnone size-full wp-image-316" title="Screen Shot 2012-10-22 at 11.13.43 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-11.13.43-PM.png" height="243" width="628" /></a>

Ama siz de <a href="http://validator.w3.org/">http://validator.w3.org/</a>adresine giderek kendi kodunuzu otomatik olarak kontrol ettirebilirsiniz.  Eğer yemyeşil This document was successfully checked as HTML5! mesajını gördüyseniz ne mutlu size, hata bulduysa tek tek düzeltmemiz gerekiyor.
<pre><code>
&lt;section class="tabbable tabs-left"&gt;
    &lt;ul class="nav nav-tabs"&gt;
        &lt;li class="active"&gt;&lt;a href="#sirketimiz" data-toggle="tab"&gt;Şirketimiz&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="#referanslar" data-toggle="tab"&gt;Referanslar&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="#tarihce" data-toggle="tab"&gt;Tarihçe&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="#kalitefelsefemiz" data-toggle="tab"&gt;Kalite Felsefemiz&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
    &lt;div class="tab-content"&gt;
        &lt;article class="tab-pane active" id="sirketimiz" itemscope itemtype="http://schema.org/Article"&gt;
            &lt;header&gt;
                &lt;h3&gt;&lt;span itemprop="name"&gt;Şirketimiz&lt;/span&gt;&lt;/h3&gt;
                &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-29"&gt;29 Ekim 2012&lt;/time&gt;&lt;/p&gt;
            &lt;/header&gt;
            &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. İstanbul, Sirkeci de faaliyet göstermekte olan baskı şirketidir. Başlıca faaliyet alanları, davetiye, broşür, el ilanı ve poster üretimi olan firma, aynı zamanda müşterilerine özel baskı çözümleri de sunmaktadır. Hali hazırda kendi ajanda ürünlerini Radikal Ajanda  markasıyla pazarlayan şirket, aynı zamanda poster işleri yapan görsel sanatçılara da baskı işleri ile sponsor olmakta ve sanata ve santçıya destek olmaktadır. Şirket ayrıca üniversitelerin sanat ve görsel tasarım bölümleri ile birlikte tasarım yarışmaları yapmış ve birlikte projeler geliştirmiştir.&lt;/p&gt;
        &lt;/article&gt;
        &lt;article class="tab-pane" id="referanslar" itemscope itemtype="http://schema.org/Article"&gt;
            &lt;header&gt;
                &lt;h3&gt;&lt;span itemprop="name"&gt;Referanslarımız&lt;/span&gt;&lt;/h3&gt;
                &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-15"&gt;15 Ekim 2012&lt;/time&gt;&lt;/p&gt;
            &lt;/header&gt;
            &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. olarak referanslarımızdan bazıları;&lt;/p&gt;
                &lt;ul&gt;
                    &lt;li&gt;Açık Kaynak Maden Suları&lt;/li&gt;
                    &lt;li&gt;Uranyum Yazılım&lt;/li&gt;
                    &lt;li&gt;Yolgösteren Stratejik Danışmanlık&lt;/li&gt;
                    &lt;li&gt;Özgür Yazılım Çöpçatanlık Hizmetleri&lt;/li&gt;
                    &lt;li&gt;Atolye Atolyesi Sanat Galerisi&lt;/li&gt;
                    &lt;li&gt;Sınırsız Çay Felsefe Klübü&lt;/li&gt;     
                &lt;/ul&gt;
        &lt;/article&gt;
        &lt;article class="tab-pane" id="tarihce" itemscope itemtype="http://schema.org/Article"&gt;
            &lt;header&gt;
                &lt;h3&gt;&lt;span itemprop="name"&gt;Tarihçe&lt;/span&gt;&lt;/h3&gt;
                &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-14"&gt;14 Ekim 2012&lt;/time&gt;&lt;/p&gt;
            &lt;/header&gt;
            &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. 14 Mart 1971 yılında, İstanbul'da matbaacılıkta yeni teknolojilerin kullanımına yer açmak ve baskı hizmetlerine devrimci bir soluk getirmek amacıyla kurulmuştur. Bugüne kadar birçok sanat etkinliğinin hem sponsoru hem de düzenleyicisi olan şirket, görsel tasarım alanında birçok faaliyetlerde de buşunmuştur. Bugüne kadar birçok ödül alan firmamızın aldığı ödüllerden bazıları şunlardır:&lt;/p&gt;
                &lt;ul&gt;
                    &lt;li&gt;1974 Balkan Matbaa Ödülleri Avrupa 3. sü&lt;/li&gt;
                    &lt;li&gt;1982 Mimar Sinan Üniversitesi En İyi Baskı Ödülü&lt;/li&gt;
                    &lt;li&gt;1994 Avrupa Güzel Sanatlar Derneği, Sanata Desten Ödülü&lt;/li&gt;
                    &lt;li&gt;1998 Kırtasiyeciler Odası, En yenilikçi Matbaa Ödülü&lt;/li&gt;
                    &lt;li&gt;2005 Görsel Sanatlar Derneği, Sanatın Dostu Ödülü&lt;/li&gt;
                    &lt;li&gt;2011 Kalite Derneği, Kalite Özel Ödülü&lt;/li&gt;     
                &lt;/ul&gt;
        &lt;/article&gt;
        &lt;article class="tab-pane" id="kalitefelsefemiz" itemscope itemtype="http://schema.org/Article"&gt;
            &lt;header&gt;
                &lt;h3&gt;&lt;span itemprop="name"&gt;Kalite Felsefemiz&lt;/span&gt;&lt;/h3&gt;
                &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-08"&gt;8 Ekim 2012&lt;/time&gt;&lt;/p&gt;
            &lt;/header&gt;
            &lt;p&gt;Kızılyıdız Matbaacılık A.Ş. olarak biz, kalitenin ve tasarımın sadece bir süs veya iyi bir pr çalışması değil, şirketimizi var eden temel kavram olduklarına inanıyoruz. Alelade veya sıradan ürünler geliştirmek yerine, firmamız her ürününde sanatçı ve tasarımcı desteği almaya azami gayret göstermekte olup, inovasyon odaklı çalışarak kendi farkını ortaya koymakta ve her zaman tecrübesini yeni sanatçılarla ve tasarımcılarla paylaşmaya özen göstermektedir.&lt;/p&gt;
        &lt;/article&gt;
    &lt;/div&gt;
&lt;/section&gt;
</code></pre>
Sol tab navigasyonunu sol tarafta kullandığımız için yanlisteye de gerek kalmadı. Yanlistenin oldu 3 birimlik kutuyu silelim ve sectionun boyunu 8 birimden 12 birime çıkaralım. Sayfamızın son hali şöyle olmalı:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-11.37.09-PM.png"><img class="alignnone size-full wp-image-317" title="Screen Shot 2012-10-22 at 11.37.09 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-11.37.09-PM.png" height="345" width="628" /></a>

Hakkımızda bölümünü bitirdik. Bir sonraki yazıda da duyurular ve kurumsal bölümlerini yapacağız.

Dayanışmayla!
Meraklı Bilişimci