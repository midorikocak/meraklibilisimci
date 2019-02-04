---
ID: 546
post_title: >
  Tasarımı HTML5 ve CSS3′e dökmek
  (Son) – CSS Yazma – 2
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: 'https://www.meraklibilisimci.com/tasarimi-html5-ve-css3%e2%80%b2e-dokmek-son-css-yazma-2/'
published: true
post_date: 2014-03-07 20:00:53
---
Bu yazıda CSS Kodumuzu yazmaya devam ediyoruz. Özet navigasyonu bitirdik ve detaylı navigasyonu bitirmemiz gerek. İlk iş detaylı navigasyonla başlayalım.

<img class="size-full wp-image-547 alignleft" alt="liste" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/liste.png" width="386" height="348" />

Navigasyonun şu anki durumu bu şekilde. Bunu şu şekle çevirmeliyiz:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-19.11.59.png"><img class="alignright size-full wp-image-548" alt="Screen Shot 2014-03-07 at 19.11.59" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-19.11.59.png" width="474" height="110" /></a>

Yani üst başlıklar yatay ama her üst başlığın alt menüleri dikey olacak. Bunu da
<pre><code>
#detail-navigation &gt; ul &gt; li{
    float: left;
    display: inline-block;
    margin-right: 72px;
}
</code></pre>
ile hallediyoruz. Burada "&gt;" işareti etiketin içindeki ilk child-elemente gider. Mantığı şu şekilde açıklayabiliriz:
<pre>&lt;nine&gt;
    &lt;evlat id="anne"&gt;
        &lt;evlat id="kiz"&gt;&lt;/evlat&gt;
    &lt;/evlat&gt;
&lt;/nine&gt;</pre>
Eğer "nine &gt; evlat" dersek burada sadece id'si anne olan elemanı seçeriz. ama "nine evlat" deseydik, id'si "anne" olanı ve id'si "kız" olan etiketleri seçecektik.

Bir sonraki adımımız, özet alt bilgi, yani "summary footer". Burada 3 tane liste elemanımız var. Bu liste elemanlarını dağıtmak istiyoruz. Bunun için de foundation'un block-grid özelliğinden yararlanacağız.
<pre><code>
&lt;div id="summary-footer" class="large-12 columns"&gt;
    &lt;ul class="small-block-grid-3"&gt;
        &lt;li&gt;&lt;p&gt;APPLICATION&lt;br/&gt;2014&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;REQUEST&lt;br/&gt;INFO&lt;/p&gt;&lt;/li&gt;
        &lt;li&gt;&lt;p&gt;SUBSCRIBE TO&lt;br/&gt;NEWSLETTER&lt;/p&gt;&lt;/li&gt;
    &lt;/ul&gt;
&lt;/div&gt;
</code></pre>
Burada block-grid liste elemanlarımızı istediğimiz gibi ortalayıp sağa sola yaslayıp dağıtıyor ve satır sütun belirlememize gerek kalmıyor.

Arka planları da istediğimiz gibi boyuyoruz. Sağ ve sol birbirine yapışık olduğu için arkaya beyaz bir border da attık. İstersek bunu transparan da yapabiliriz.
<pre><code>
#summary-footer li
{
    color: white;
    text-align:center;
    background-color:black;
    border-right:solid 18px white;
    border-left:solid 18px white;
    height:150px;
}

#summary-footer p
{
    padding:50px;
    background-color:black;
    font-family: 'akzidenz-grotesk_bqmedium' !important;
    font-weight:bold;
    margin: auto;
}
</code></pre>
Özet alt bilgi bölümünün son halini şu şekile getirmeyi başardık:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-21.46.50.png"><img class="alignright size-full wp-image-549" alt="Screen Shot 2014-03-07 at 21.46.50" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-21.46.50.png" width="474" height="205" /></a>

Şu anda ilk verilen tasarıma neredeyse ulaştık gibi. Sırada detay alt bilgi bölümü var. Detay alt bilgi bölümünde başlık kısmını row yani satır olarak belirledik, başlığın altında ise uzun bir künye yer alıyor. Bu künyeyi satırlara ve sütunlara bölemeyiz. Block-grid de kullanmamız mantıksız olur, sonuçta bunu Google'ın ayrı bilgi yığınları olarak indexlemesini istemiyoruz. Açıkçası, kullandığımız her elemanın, mantıksal bir açıklaması var. Sadece görsel olarak 3 kolona bölmek istiyoruz. Bunun için CSS3'ün column özelliğinden yararlanacağız. Bu özellik aynı gazetelerde olduğu gibi, başka bir elemana ihtiyaç kalmadan yazıları sütunlara bölmemizi sağlar ve ortaya çok sağlam okunabilirlik çıkar. Gazetelerde de sütunlar gözlerin uzun uzun hareketler yapmaması ve yorulmaması için varlardır.

CSS kodumuza bakarsak:
<pre><code>
#detail-footer{
    color:#58595b;
    font-size:12px !important;
    font-family: 'garamond_three_medium';
    -moz-column-count:3; /* Firefox */
    -webkit-column-count:3; /* Safari and Chrome */
    column-count:3;
    -moz-column-gap:40px; /* Firefox */
    -webkit-column-gap:40px; /* Safari and Chrome */
    column-gap:40px;
    -moz-column-rule:3px outset #fff; /* Firefox */
    -webkit-column-rule:3px outset #fff; /* Safari and Chrome */
    column-rule:3px outset #fff;
}

#copyright{
    color:#58595b;
    font-family: 'akzidenz-grotesk_bqmedium' !important;
    font-size:9px;
    margin-top:25px;
}
</code></pre>
Burada metnimizi 3 kolona ayırdık, aralarına 3px boyunda beyaz bir çizgi ve 40px boyunda boşluk koyduk.

Sonuç görüntümüz şu şekilde.<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-21.53.16.png"><img class="alignright size-full wp-image-550" alt="Screen Shot 2014-03-07 at 21.53.16" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-03-07-at-21.53.16.png" width="474" height="120" /></a>

Sonuç olarak, bize gelen bir PSD dosyasını tamamıyla HTML5 ve CSS3'e dökmüş olduk. Gelen tasarımın minimalist olması veya farklı renkler imajlar kullanması kodlama süremizi uzatabilirdi. Buraya kadar kullandığımız CSS3 özelliklerinden kullanmadığımız ama araştırıp kendi kodlarınızda kullanabilecekleriniz şunlar:
<ol>
	<li>CSS3 Box Shadow (Gölgeler)</li>
	<li>CSS3 Rounded Corners (Yuvarlak köşeler)</li>
	<li>CSS3 Gradients (Renk geçişleri)</li>
	<li> Üstüste arkaplanlar</li>
	<li>Resim dosyası kullanarak sınır çizme (border-image)</li>
	<li>2 boyutlu dönüşümler (büyütme, küçültme, döndürme, kaydırma gibi)</li>
	<li>3 boyutlu dönüşümler</li>
	<li>CSS3 Animasyonları (Flash animasyonları kadar gelişmiş animasyonları, JS ve HTML5 Canvas kullanmadan yapmanız mümkünmüş, ben denemedim :) )</li>
</ol>
Bunun gibi daha birçok CSS3 özelliğini tasarımcıdan size gelen tasarıma göre kullanmanız mümkün.

Bir sonraki seride bu tasarımı sıfırdan yazılmış bir Wordpress temasına çevirmeyi öğreneceğiz.