---
ID: 511
post_title: >
  Tasarımı HTML5 ve CSS3′e dökmek (2)
  – Mantıksal Tasarım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: 'https://www.meraklibilisimci.com/tasarimi-html5-ve-css3%e2%80%b2e-dokmek-1-mantiksal-tasarim/'
published: true
post_date: 2014-03-06 15:13:52
---
Genellikle tasarımcılar bize tasarımlarını .psd olarak gönderirler ve bu tasarımı bizim koda dökmemiz gerekir. Öncelikle yapmamız gereken, hiçbir süsleme öğesi kulanmadan HTML5 kodu çıkarabilmek için tasarımı analiz etmek. Şimdi tasarıma göz atalım.

home.psd dosyamız şu şekilde:
<p style="text-align:center;"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ai_web-3-06.png"><img class=" wp-image-512 aligncenter" alt="AI_WEB-3-06" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ai_web-3-06.png?w=300" width="300" height="269" /></a></p>
<p style="text-align:left;">Burada tasarımcı bize yardımcı olacak bazı rehber noktaları vermiş. Fakat bizim koda dökmemiz için daha detaylı incelememiz gerekiyor. Bunun için de tasarımı analiz etmemiz lazım.</p>
<p style="text-align:center;"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ozet1.png"><img class="alignnone size-full wp-image-514" alt="ozet" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ozet1.png" width="474" height="841" /></a></p>
<p style="text-align:left;">Öncelikle tasarıma baktığımızda gördüğümüz, kullanıcının navigasyon menüleri arasında kaybolmaması hedeflenmiş, en çok kullanılan navigasyon ve altbilgi öğeleri gruplanarak özet nav ve özet footer bölümleri oluşturulmuş. Bunları nasıl kodlarız? İlk başta dediğimiz gibi bu aşamada hiçbir süsleme ve içerik öğesini dosyalarımıza eklemeyeceğiz. ihtiyacımız olan en basit HTML5 dosyasını düşünerek kodlamamızı yapalım. Daha sonra body kısmını istediğimiz framework'e taşımamız kolay.</p>

<pre><code>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;title&gt;ARTINTERNATIONAL&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
    &lt;header&gt;
        &lt;div id="main-slider"&gt;&lt;/div&gt;
        &lt;nav id="summary-nav"&gt;&lt;/nav&gt;
        &lt;div id="main-logo"&gt;&lt;/div&gt;
        &lt;nav id="detail-navigation"&gt;&lt;/nav&gt;
    &lt;/header&gt;
    &lt;div id="main-content"&gt;&lt;/div&gt;
    &lt;footer&gt;
        &lt;div id="summary-footer"&gt;&lt;/div&gt;
        &lt;div id="detail-footer"&gt;&lt;/div&gt;
        &lt;div id="copyright"&gt;
    &lt;/footer&gt;
&lt;/body&gt;

&lt;/html&gt;
</code></pre>

Minimum HTML5 dosyamızın mantıksal tasarımını bitirdik. Bu aşama gerçekten çok önemli çünkü tasarımın koda dökümünün sonraki aşamalarında bize rehber olacak. Bir sonraki yazıda cevap verebilirlik (responsiveness) için kullanacağımız CSS çerçevesini (framework) seçerek görsel öğelerin kodlanmasına başlayacağız.