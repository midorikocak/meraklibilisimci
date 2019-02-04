---
ID: 517
post_title: >
  Tasarımı HTML5 ve CSS3′e dökmek (3)
  – Klasör yapısı, CSS Framework
  Seçimi
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: 'https://www.meraklibilisimci.com/tasarimi-html5-ve-css3%e2%80%b2e-dokmek-3-klasor-yapisi-css-framework-secimi/'
published: true
post_date: 2014-03-06 20:53:06
---
Tasarımcı arkadaşları psd kesmeleri için zorlayıp imajları, logoları, ikonları ve faviconları aldıktan sonra kullanmamız gereken css frameworküne karar vermemiz gerekiyor.

CSS çerçeveleri genellikle 960px genişliğinde ve bizim için ortalanmış ve sayfa bileşenleri için önceden 12'ye bölünmüş genişlikleri kullanabilmemizi sağlayan class'ları verirler. Ayrıca barındırdıkları @media-query'ler sayesinde (responsive) "tepkileşimli" yani gösterildikleri ekrana, cihaza, cihazın yatay/dikeyliğine göre bozulmadan görüntülenmelerini sağlayan hazır css sınıflarıdırlar.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/960_grid_12_col_1.png"><img class="alignnone size-large wp-image-523" alt="960_grid_12_col_1" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/960_grid_12_col_1.png?w=474" width="474" height="466" /></a>

Ayrıca yazıların boşlukların her tarayıcıda aynı görünmelerini sağlayan reset.css sınıflarını da barındırırlar. Diyelim ki ben bütün css sınıflarını genişliklerini kendim ayarlamak istiyorum ve kesinlikle tasarımıma sınıfın müdahelesini istemiyorum diyorsanız o zaman, sadece reset.css ve modernizr.js, yani html5 taglerinin, html5 desteklemeyen tarayıcılarda görünmesini sağlayan html5boilerplate öneririm.

http://html5boilerplate.com/

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-06-at-21.18.04.png"><img class="alignnone size-large wp-image-518" alt="Screen Shot 2014-03-06 at 21.18.04" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-06-at-21.18.04.png?w=474" width="474" height="395" /></a>

İnternette kullanılan bir numaralı CSS Framework'ü kullanmak istiyorum, zerre tasarım yapmak istemiyorum diyen insanlar ne kullanır derseniz, evet insanlar Twitter Bootstrap 3 kullanıyorlar.
<p style="text-align:center;"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/imgres.jpg"><img class="size-full wp-image-519 aligncenter" alt="imgres" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/imgres.jpg" width="300" height="168" /></a></p>
Fakat twitter bootstrap'in şöyle bir dezavantajı var. Tasarımı öldürüyor. Ben açıkçası base veya temaya oturtulmuş bootstrap kullanan bir site gördüğümde tasarıma önem verilmediğini düşünüyorum. Evet daha önceki HTML yazılarında twitter bootsrap 2 yi ben de kullandım ama Bootstrap artık o kadar yayıldı ki, siteniz kullanıcının aklında kalmıyor, herhangi 6000 siteden bir tanesi haline geliyor. Kaynak: <a href="http://css.dzone.com/articles/please-stop-using-twitter">http://css.dzone.com/articles/please-stop-using-twitter</a> O yüzden ben artık bootstrap kesinlikle tavsiye etmiyorum.

Peki çözüm nedir? Hayır bu etkileşim işiyle uğraşmamı kolaylaştıracak gelişmiş ancak tasarımıma da müdahele etmeyecek, tasarım css'lerini ezmeyecek bir framework'e ihtiyacım var diyorsanız, foundation öneriyorum.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2013-03-21-at-12.22.52-PM.png"><img class="alignnone size-large wp-image-520" alt="Screen-Shot-2013-03-21-at-12.22.52-PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2013-03-21-at-12.22.52-PM.png?w=474" width="474" height="340" /></a>

Öncelikle http://foundation.zurb.com adresinden foundation'u indirelim. Şimdilik "download" butonundan sonra, "download everything" butonunu seçelim

Foundation arşivini indirip, içine bir göz atalım.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-06-at-21.32.26.png"><img class="alignnone size-full wp-image-522" alt="Screen Shot 2014-03-06 at 21.32.26" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-06-at-21.32.26.png" width="250" height="235" /></a>

Önceki yazıda indirdiğimiz font dosyalarını, fonts adı altında bir klasör oluşturup içine atalım. Daha sonra stylesheet.css'i de CSS klasörünün içine atalım. Bu dosyadaki "url('dosyaadi')" şeklinde olan satırları da "url('../fonts/dosyaadi')" şekline getirelim.

Gördüğümüz gibi arşivimizde karmaşık dosyalar vs. yok. index.html dosyasının içinde de foundation sınıfı ile yapabileceğimiz örnekler gösterilmiş. bu dosya şimdilik bi kenarda dursun. dosyanın adını example.html olarak değiştirelim. Siz kendiniz dosyanın içeriğine bakarak inceleyebilirsiniz, ancak burada foundation detaylarına girmeyeceğim.

Şimdi anasayfa tasarımı ile 12 sütun mantığını nasıl oturtabiliriz, bir bakalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/grid.png"><img class="alignnone size-large wp-image-524" alt="grid" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/grid.png?w=474" width="474" height="841" /></a>

Şimdi tasarımcının gönderdiği, daha önce mantıksal olarak böldüğümüz tasarımı, görsel olarak grid'e yani 12 sütunlu ızgaraya oturtuyoruz. Gördüğümüz gibi tasarımda 8 adet satır var, ve bunların herbirini ayrı ayrı bölmemiz gerekiyor.
<pre><code>
&lt;!doctype html&gt;
&lt;html class="no-js" lang="en"&gt;
&lt;head&gt;
&lt;meta charset="utf-8" /&gt;
&lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
&lt;title&gt;ARTINTERNATIONAL&lt;/title&gt;
&lt;link rel="stylesheet" href="css/foundation.css" /&gt;
&lt;link rel="stylesheet" href="css/stylesheet.css" /&gt;&lt;!-- CSS dosyamızı buraya ekledik --&gt;
&lt;script src="js/vendor/modernizr.js"&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;header&gt;
&lt;div class="row"&gt;
&lt;div id="main-slider" class="large-12 columns"&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;nav id="summary-nav" class="large-12 columns"&gt;&lt;/nav&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div class="large-12 columns"&gt;
&lt;nav id="summary-nav"&gt;&lt;/nav&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="main-logo" class="large-2 columns"&gt;&lt;/div&gt;
&lt;nav id="detail-navigation" class="large-10 columns"&gt;&lt;/nav&gt;
&lt;/div&gt;
&lt;/header&gt;

&lt;div class="row"&gt;
&lt;div id="main-content" class="large-12 columns"&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;footer&gt;
&lt;div class="row"&gt;
&lt;div id="summary-footer" class="large-12 columns"&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="detail-footer" class="large-12 columns"&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="copyright" class="large-4 large-centered columns"&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;/footer&gt;

&lt;script src="js/vendor/jquery.js"&gt;&lt;/script&gt;
&lt;script src="js/foundation.min.js"&gt;&lt;/script&gt;
&lt;script&gt;
$(document).foundation();
&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
Şu anda ilk çerçeve dosyamızı oluşturmuş olduk. Izgara(Grid) ve foundation mantığını sanırım anlamış oldunuz.<strong> Bir sonraki yazıda</strong>, logo, ikon, favicon gibi elemanları yerleştireceğiz. Bu dosyayı "index.html" olarak klasörümüzün içine kaydedelim.

Burada div tag'lerine genişlik vermek için kullandığımız large-12 veya large-10 gibi sınıflar, 3 ana tipten oluşuyor, large, medium ve small. Örneğin large-4 large-4 large-4 gibi 3 tane blok oluşturduğumuzda, bu blokarın büyük ekranlar için kesinlikle yanyana görüntülenmesini istiyoruz. Ama medium ve small ekran genişlikleri için bunu önemsemiyoruz. Eğer cep telefonu gibi küçük ekranları da illaki bölmemiz gerekiyorsa, herbirinin yanına smal-3 ve medium-3 sınıflarını da eklememiz gerekecekti. Ancak tepkileşimliliği, yani cep telefonunda, ipad'de sitenin bozulmamasını istiyorsak, bu blokların dar ekranlarda alt alta görüntülenmelerine de izin vermemiz gerekiyor.

Foundation ile ilgili daha detaylı bilgiler için:
http://foundation.zurb.com/docs/components/grid.html

Kaynakça:
http://www.sitepoint.com/best-web-designing-frameworks-2014/