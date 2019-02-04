---
ID: 529
post_title: >
  Tasarımı HTML5 ve CSS3′e dökmek (4)
  – Bileşenleri yerleştirmek
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: 'https://www.meraklibilisimci.com/tasarimi-html5-ve-css3%e2%80%b2e-dokmek-4-bilesenleri-yerlestirmek/'
published: true
post_date: 2014-03-06 23:55:18
---
İmajları aldık, fontları yerleştirdik, css dosyamızı düzenledik. Tasarımcıdan "lorem ipsum" metinleri, navigasyon isimlerini istedik, çoğunu verdi, bazıları için de "eeah, psd verdik ya bak ordan işte" dedi. Dikkat ederseniz hala tek satır CSS kodu yazmadık. Ona da sıra gelecek. Önce tek tek imajlarımızı, menülerimizi, bileşenlerimizi yerleştirmemiz gerekiyor. Bunu böyle yapmamızdaki amaç, CSS olmadan da bütün herşeyin düzgün göründüğünü sağlama almak.

Öncelikle imajları yerleştirelim. İmajları yerleştirirken dikkat etmemiz gereken şey her img tag'inin kendi kendini kapatıyor olması ve her birnin title yani başlık özelliğine sahip olması.
<pre><code>&lt;img src="img/logo-kucuk.png" title="logo" alt="logo" /&gt;</code></pre>
Tüm imajları bu şekilde yerleştirmemiz gerekiyor.

Daha sonra sitede gezinmeyi sağlayan navigasyonları sırasız liste şeklinde eklemeliyiz. bunları "nav" taglerinin arasına yerleştiriyoruz ki, google robotçukları bunun sitemizde gezinmeye yarayan linkleri barındıran listeler olduğunu anlasın.

Örneğin "summary-nav" dediğimiz hızlı gezinmeyi sağlayan sırasız listeyi şöyle kodlamalıyız (sıralı listede kenarda otomatik numaralar çıkar, sırasız listede ise noktalar)
<pre><code>&lt;nav id="summary-nav" class="large-12 columns"&gt;
  &lt;ul&gt;
      &lt;li&gt;APPLICATION 2014&lt;/li&gt;
      &lt;li&gt;REQUEST INFO&lt;/li&gt;
      &lt;li&gt;SUBSCRIBE TO NEWSLETTEr&lt;/li&gt;
      &lt;li&gt;SITE&lt;/li&gt;
  &lt;/ul&gt;
&lt;/nav&gt;
</code></pre>
Navigasyonları da belirtildiği gibi istediğimiz yerlere yerleştiriyoruz. Şu ana kadar elimizdeki kod şu şekilde:
<pre><code>
&lt;!DOCTYPE html&gt;
&lt;html class="no-js" lang="en"&gt;
&lt;head&gt;
&lt;meta charset="utf-8" /&gt;
&lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
&lt;title&gt;ARTINTERNATIONAL&lt;/title&gt;
&lt;link rel="stylesheet" href="css/foundation.css" /&gt;
&lt;script src="js/vendor/modernizr.js"&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;header&gt;
&lt;div class="row"&gt;
&lt;div id="main-slider" class="large-12 columns"&gt;
&lt;img src="img/main-slider.png" title="artinternational" alt="artinternational" /&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;nav id="summary-nav" class="large-12 columns"&gt;
&lt;ul&gt;
&lt;li&gt;APPLICATION 2014&lt;/li&gt;
&lt;li&gt;REQUEST INFO&lt;/li&gt;
&lt;li&gt;SUBSCRIBE TO NEWSLETTEr&lt;/li&gt;
&lt;li&gt;SITE&lt;/li&gt;
&lt;/ul&gt;
&lt;/nav&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="main-logo" class="large-2 columns"&gt;
&lt;img src="img/logo-kucuk.png" title="logo" alt="logo" /&gt;
&lt;/div&gt;
&lt;nav id="detail-navigation" class="large-10 columns"&gt;
&lt;ul&gt;
&lt;li&gt;ABOUT
&lt;ul&gt;
&lt;li&gt;About Artinternational&lt;/li&gt;
&lt;li&gt;Media&lt;/li&gt;
&lt;li&gt;Board Of Patrons&lt;/li&gt;
&lt;li&gt;Gallery Selectio Committee&lt;/li&gt;
&lt;li&gt;Partners In 2013&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;li&gt;VISITORS
&lt;ul&gt;
&lt;li&gt;Directions &amp;amp; Transportation&lt;/li&gt;
&lt;li&gt;How To Reach The Venue&lt;/li&gt;
&lt;li&gt;Map&lt;/li&gt;
&lt;li&gt;Venue&lt;/li&gt;
&lt;li&gt;Art In Istanbul&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;li&gt;EXHIBITORS
&lt;ul&gt;
&lt;li&gt;Apply For 2014&lt;/li&gt;
&lt;li&gt;2013 Participants&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;li&gt;PROGRAMME
&lt;ul&gt;
&lt;li&gt;Programme&lt;/li&gt;
&lt;li&gt;Vip Programme&lt;/li&gt;
&lt;li&gt;By The Waterside&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;li&gt;PRESS
&lt;ul&gt;
&lt;li&gt;Press&lt;/li&gt;
&lt;li&gt;Accreditation&lt;/li&gt;
&lt;li&gt;Press Coverage&lt;/li&gt;
&lt;li&gt;Contact&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;/ul&gt;

&lt;/nav&gt;
&lt;/div&gt;
&lt;/header&gt;

&lt;div class="row"&gt;
&lt;div id="main-content" class="large-12 columns"&gt;
&lt;h2&gt;ISTANBUL’S LEADING INTERNATIONAL ART FAIR&lt;/h2&gt;&lt;br/&gt;
&lt;p&gt;HALIÇ CONGRESS CENTER&lt;/p&gt;
&lt;p&gt;&lt;img src="img/AI_WEB-3-07.jpg" title="artinternational" alt="artinternational" /&gt;ArtInternational launched in September 2013 at the Haliç Congress Centre in Istanbul to strong acclaim. Bringing together leading international and local galleries, this leading modern and contemporary art fair in Istanbul offers unrivalled access to exciting new art from Turkey, Europe, the US, the Middle East and beyond. Drawing on its unique geographic location as a gateway between ‘East’ and ‘West’, the fair is fast becoming a cultural bridge across the global art world. In addition to the participation of leading and emerging galleries, the fair provides a programme of exhibitions, events and forums, enabling visitors to experience the rich cultural history of Istanbul alongside the flourishing local contemporary art scene developing today.
&lt;/p&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;footer&gt;
&lt;div class="row"&gt;
&lt;div id="summary-footer" class="large-12 columns"&gt;
&lt;ul&gt;
&lt;li&gt;APPLICATION 2014&lt;/li&gt;
&lt;li&gt;REQUEST INFO&lt;/li&gt;
&lt;li&gt;SUBSCRIBE TO NEWSLETTER&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="footer-title" class="large-2 columns"&gt;&lt;h2&gt;ARTINTERNATIONAL&lt;/h2&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="detail-footer" class="large-9 columns"&gt;
&lt;h3&gt;INTERTEKS&lt;/h3&gt;
&lt;p&gt;6, Mim Kemal Öke Cad.&lt;br/&gt;
34367 Nisantası, Istanbul&lt;/p&gt;

&lt;h3&gt;FAIR DIRECTOR:&lt;/h3&gt;
&lt;p&gt;Dyala Nusseibeh&lt;br/&gt;
dyala@artinternational14.com&lt;/p&gt;

&lt;h3&gt;ARTISTIC DIRECTOR:&lt;/h3&gt;
&lt;p&gt;Stephane Ackermann&lt;br/&gt;
Stephane.Ackermann@montex.co.uk&lt;/p&gt;

&lt;h3&gt;HEAD OF VIP RELATIONS &amp;amp; PROGRAMMING:&lt;/h3&gt;
&lt;p&gt;Isabella Icoz&lt;br/&gt;
isabella@artinternational14.com&lt;/p&gt;

&lt;h3&gt;GENERAL ENQUIRIES:&lt;/h3&gt;
&lt;p&gt;info@artinternational14.com&lt;/p&gt;

&lt;h3&gt;GALLERY APPLICATIONS:&lt;/h3&gt;
&lt;p&gt;applications@artinternational14.com&lt;/p&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;div class="row"&gt;
&lt;div id="copyright" class="large-4 large-centered columns"&gt;COPYRIGHT &amp;copy; 2013 ARTINTERNATIONAL. ALL RIGHTS RESERVED&lt;/div&gt;
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
Şu anda ekrana baktığımızda hala tasarımdan çok uzağız ama yaklaştık.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-01.48.17.png"><img class="alignnone size-large wp-image-530" alt="Screen Shot 2014-03-07 at 01.48.17" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-01.48.17.png?w=474" width="474" height="520" /></a>

Tüm bileşenlerimizi siteye yerleştirdik. Şimdi sıra geldi CSS'imizi yazmaya. Burada garanti ettiğimiz olay, google robotçuklarının kodu düzgün bir şekilde okuyabilmesi. Ayrıca kod hatalarımızı W3C sitesinde de kontrol ettirebiliriz. W3C sitesinin validate syntax, yani kodu doğrula aracı bulunuyor.

http://validator.w3.org/

Bu adresten, URL yani site adresi girerek, dosya yükleyerek veya doğrudan giriş yaparak HTML5 kodumuzu kontrol ettirebiliriz. (Eski HTML versiyonlarını da otomatik olarak algılayacaktır.)

Sonuç eğer şu şekildeyse, bir sonraki aşamaya yani CSS yazma aşamasına geçebiliriz:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-01.51.27.png"><img class="alignnone size-large wp-image-531" alt="Screen Shot 2014-03-07 at 01.51.27" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-01.51.27.png?w=474" width="474" height="397" /></a>

&nbsp;

Peki CSS'i nasıl yazacağız? O da bir sonraki yazıda...