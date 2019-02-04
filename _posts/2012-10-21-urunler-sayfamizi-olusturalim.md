---
ID: 270
post_title: Ürünler sayfamızı oluşturalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/urunler-sayfamizi-olusturalim/
published: true
post_date: 2012-10-21 06:47:19
---
Bir önceki yazıda anasayfamızı tamamlamış, bölümlerimizi oluşturmaya başlayacağımızı söylemiştik. İlk olarak ürünler bölümüyle başlayacağız.

[gallery link="file" columns="4" orderby="ID"]

Ürünler sayfamızda birden çok kategori içinde, birden fazla ürünü aynı anda görmemiz gerekiyor. Bunun için kategoriler arasında gezinmemizi sağlayan bir bağlantılar listesine ihtiyacımız var ilk olarak.
<pre><code>
&lt;div class="span3 yanliste"&gt;
    &lt;ul class="nav nav-list"&gt;
        &lt;li&gt;Kategoriler&lt;/li&gt;
        &lt;hr&gt;
        &lt;li&gt;&lt;a href="ajanda.html"&gt;Ajandalar&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="poster.html"&gt;Posterler&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="davetiye.html"&gt;Davetiyeler&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="elilani.html"&gt;El ilanları&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
&lt;/div&gt;
</code></pre>
hr etiketi gözünüze çarptıysa o etiketler arasında çizgi çekebilmemizi sağlayan etiket. Tabii listemizin güzel de görünmesini istiyoruz. Bunun için custom.css'in sonuna şöyle bir kod daha ekleyelim:
<pre><code>
.yanliste
{
    background-color: #f5f5f1;
    margin-bottom: 10px;
    padding: 14px 0;
    -moz-border-radius: 5px;
    -webkit-border-radius: 5px;
    border-radius: 5px;
}
</code></pre>
Burada yanliste class özelliğine sahip olan etiketlerin önce arkaplan rengini ayarladık. Alt taraftan 10 piksel boşluk bıraktık. Kutumuzu sağ taraftan 14 piksel sağa kaydırdık ki sayfanın kenarına yapışmasın. Son olarak da kutumuzun kenarlarını 5 piksel çağında yuvarlattık.

Bu şekilde yan listemiş şöyle bir görünüme kavuştu:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.19.29-AM.png"><img class="alignnone size-full wp-image-281" title="Screen Shot 2012-10-21 at 8.19.29 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.19.29-AM.png" height="212" width="258" /></a>

Gayet güzel ve modern.

Birden çok ürünü bir arada görmemiz gerekiyor. Bunun için önce ürünlerin ana resimlerinin küçük hallerini bir arada tutacak bir listeye ihtiyacımız var.

Kategori sayfasında görünecek her bir ürün için ihtiyacımız olan bilgilere bir göz atalım.
<ol>
	<li>Her ürünün küçük bir resmi</li>
	<li>Ürünün adı</li>
	<li>Ürünün fiyatı</li>
	<li>Ürünle ilgili ek bilgi (Opsiyonel, bu gittigidiyor'da teslim günü olmuş, sahibinden de ise indirim miktarı olmuş. Şimdilik buna gerek yok.)</li>
</ol>
Her ürün satırında 4 tane ürün göstermek en iyisi. Her ürünün küçük resmi 170'e 135 piksel boyunda olsun. Şimdi kodumuzu yazmaya başlayalım.
<pre><code>
&lt;a class="urun-resmi" href="kahveajanda.html" class="baslik" title="Kahverengi Klasik Ajanda"&gt;
    &lt;img src="img/kahveajanda.jpg" alt="Kahverengi Klasik Ajanda" /&gt;
&lt;/a&gt;
&lt;div class="urun-detay"&gt;
    &lt;div class="urun-baslik"&gt;
        &lt;a href="kahveajanda.html" class="baslik" title="Kahverengi Klasik Ajanda"&gt;Kahverengi Klasik Ajanda&lt;/a&gt;
    &lt;/div&gt;
    &lt;div class="urun-fiyati"&gt;
        &lt;span class="fiyat"&gt;16.50&lt;/span&gt; 
        &lt;span class="doviz-kodu"&gt;TL&lt;/span&gt;
    &lt;/div&gt;
&lt;/div&gt;</code></pre>
Tek bir ürün için kodumuz bu şekilde.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.10.41-AM.png"><img title="Screen Shot 2012-10-21 at 8.10.41 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.10.41-AM.png" height="184" width="204" /></a>

Ama birden fazla ürünümüz olacak, hatta bir sayfada yüzlerce ürün bile göstermemiz gerekebilir. Bunları peki nasıl sıralarsak daha iyi olur? Bu konuda uygulanan tekniklerden bir tanesi bunları teker teker bir listenin elemanı haline getirmek.
<pre><code>
&lt;ul class="urun-listesi"&gt;
    &lt;li class="urun"&gt;Ürün 1&lt;/li&gt;
    &lt;li class="urun"&gt;Ürün 2&lt;/li&gt;
    &lt;li class="urun"&gt;Ü<span style="line-height:19px;">rün 3</span></code><code>&lt;/li&gt;
    &lt;li class="urun"&gt;Ürün 4&lt;/li&gt;
    &lt;li class="urun"&gt;Ürün 5&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.09.34-AM.png"><img class="alignnone size-full wp-image-277" title="Screen Shot 2012-10-21 at 8.09.34 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.09.34-AM.png" height="108" width="88" /></a>

Yukarıdaki ürünleri bu listenin elemanları olarak yerleştireceğiz. Yapalım:
<pre><code>
&lt;h5&gt;Ajandalar&lt;/h5&gt;
&lt;ul class="urunlistesi"&gt;
    &lt;li class="urun"&gt;
        &lt;a class="urun-resmi" href="kahveajanda.html" class="baslik" title="Kahverengi Klasik Ajanda"&gt;
            &lt;img src="img/kahveajanda.jpg" alt="Kahverengi Klasik Ajanda" /&gt;
        &lt;/a&gt;
        &lt;div class="urun-detay"&gt;
            &lt;div class="urun-baslik"&gt;
                &lt;a href="kahveajanda.html" class="baslik" title="Kahverengi Klasik Ajanda"&gt;Kahverengi Klasik Ajanda&lt;/a&gt;
            &lt;/div&gt;
            &lt;div class="urun-fiyati"&gt;
                &lt;span class="fiyat"&gt;16.50&lt;/span&gt; 
                &lt;span class="doviz-kodu"&gt;TL&lt;/span&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/li&gt;
    &lt;li class="urun"&gt;
        &lt;a class="urun-resmi" href="siyahajanda.html" class="baslik" title="Siyah Modern Ajanda"&gt;
            &lt;img src="img/siyahajanda.jpg" alt="Siyah Modern Ajanda" /&gt;
        &lt;/a&gt;
        &lt;div class="urun-detay"&gt;
            &lt;div class="urun-baslik"&gt;
                &lt;a href="siyahajanda.html" class="baslik" title="Siyah Modern Ajanda"&gt;Siyah Modern Ajanda&lt;/a&gt;
            &lt;/div&gt;
            &lt;div class="urun-fiyati"&gt;
                &lt;span class="fiyat"&gt;15&lt;/span&gt; 
                &lt;span class="doviz-kodu"&gt;TL&lt;/span&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/li&gt;
    &lt;li class="urun"&gt;
        &lt;a class="urun-resmi" href="deriajanda.html" class="baslik" title="Deri Lüks Ajanda"&gt;
            &lt;img src="img/deriajanda.jpg" alt="Deri Lüks Ajanda" /&gt;
        &lt;/a&gt;
        &lt;div class="urun-detay"&gt;
            &lt;div class="urun-baslik"&gt;
                &lt;a href="deriajanda.html" class="baslik" title="Deri Lüks Ajanda"&gt;Deri Lüks Ajanda&lt;/a&gt;
            &lt;/div&gt;
            &lt;div class="urun-fiyati"&gt;
                &lt;span class="fiyat"&gt;19&lt;/span&gt; 
                &lt;span class="doviz-kodu"&gt;TL&lt;/span&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/li&gt;
    &lt;li class="urun"&gt;
        &lt;a class="urun-resmi" href="kalemliajanda.html" class="baslik" title="Kalemli Çok Amaçlı Ajanda"&gt;
            &lt;img src="img/kalemliajanda.jpg" alt="Kalemli Çok Amaçlı Ajanda" /&gt;
        &lt;/a&gt;
        &lt;div class="urun-detay"&gt;
            &lt;div class="urun-baslik"&gt;
                &lt;a href="kalemliajanda.html" class="baslik" title="Kalemli Çok Amaçlı Ajanda"&gt;Kalemli Çok Amaçlı Ajanda&lt;/a&gt;
            &lt;/div&gt;
            &lt;div class="urun-fiyati"&gt;
                &lt;span class="fiyat"&gt;21.50&lt;/span&gt; 
                &lt;span class="doviz-kodu"&gt;TL&lt;/span&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/li&gt;
    &lt;li class="urun"&gt;
        &lt;a class="urun-resmi" href="ozelajanda.html" class="baslik" title="Özel Baskı Promosyon Ajanda"&gt;
            &lt;img src="ozelajanda.jpg" alt="Özel Baskı Promosyon Ajanda" /&gt;
        &lt;/a&gt;
        &lt;div class="urun-detay"&gt;
            &lt;div class="urun-baslik"&gt;
                &lt;a href="ozelajanda.html" class="baslik" title="Özel Baskı Promosyon Ajanda"&gt;Özel Baskı Promosyon Ajanda&lt;/a&gt;
            &lt;/div&gt;
            &lt;div class="urun-fiyati"&gt;
                &lt;span class="fiyat"&gt;35.50&lt;/span&gt; 
                &lt;span class="doviz-kodu"&gt;TL&lt;/span&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/li&gt;
&lt;/ul&gt;
</code></pre>
Son olarak görünümüz şu şekilde:
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.15.34-AM.png"><img title="Screen Shot 2012-10-21 at 8.15.34 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-8.15.34-AM.png" height="578" width="222" /></a>

Eksik olan ne? Eksiği yok fazlası var aslında. Önce kenardaki noktalardan kurtulmamız lazım. Bunun için custom.css'e gidelim ve yazmaya başlayalım.
<pre><code>
.urunlistesi {
    list-style-type: none !important;
    font-family: "Arial","Helvetica",sans-serif !important;
    font-size: 12px !important;
}
</code></pre>
list-style-type: none ile listenin kenarlarındaki noktalardan kurtulduk. Peki bu !important da neyin nesi? Örneğin elinizde aynı etiketi etkileyen ve çakışan iki özellik var. Siz özelliğin başka bir yerde çakışabileceğini düşünüyorsanız, !important; ile özelliğinizi en önemli özellik haline getiriyorsunuz.

Font-family ve size ile yazı tipi ve boyutlarını da ayarladık. Devam edelim:
<pre><code>
.urun-listesi .urun {
    float: left;
    width: 145px;
    padding: 6px;
    background-color: #fff;
    border: 1px solid #ececec;
    margin: 0 8px 14px 0;
    position: relative;
    list-style-type:none !important;
}
</code></pre>
Burada tanımladığımız bütün özellikleri biliyoruz aslında. float left ile kutuyu sola yaslayacağımızı, width ile genişliğini, padding ile etrafındaki boşluğu, background-color ile arkaplan rengini, margin ile kenar boşluklarını ayarladık. Burada kullandığımız 4 adet sayı, top, right, bottom, left, yani üst, sağ, alt ve sol kenar boşluklarını tek bir satırdan ayarlamamızı sağlıyor.

Position: relative özelliği ise normalde olması gereken yere göreceli olarak konumlandırma yapmamıza yarar. Yine list-style-type ile liste özelliğini önlem olarak burada da yoketmişiz.
<pre><code>
.urun-baslik {
    margin-bottom: 0;
    line-height: 15px;
    text-align: left;
}
</code></pre>
Ürün başlığı için alt boşluğu 0, satır boyunu 15 piksel yapmış ve yazıları sola hizalamışız.
<pre><code>
.urun-baslik a {
    display: block;
    color: #666;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
</code></pre>
Burada yeni birkaç özellikle karşılaşıyoruz. Display block ile elemanımızı satır içinde değil, kendi başına görüntülenmesini sağladık. Ne de olsa resim kutusu olarak kullanacağız ve sağında solunda orasında burasında yazı vs. istemeyiz değil mi? color ile yazı rengini ayaladık. White-space nowrap özelliği ile kutu içindeki yazının alt satıra kaymaması gerektiğini belirttik. Owerflow özelliği ile taşan metnin gizlenmesi gerektiğini söyledik. En güzel özelliğimiz ise text-overflow. Buna verdiğimiz ellipsis değeriyle taşan yazılardan sonra üç nokta gelmesini sağladık.
<pre><code>
.urun-fiyat {
    padding-top:6px;
    color: #78c042;
    line-height: 14px;
    text-align: right;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: clip;
}
</code></pre>
Ürün fiyatını şekilldenrimek için de yukarıda belirttiğimiz özelliklerin aynısından yararlandık. Burada tek farklı olan, text-align ile metini sağa hizalandırmış ve text-overflow özelliğini de taşan kısmı kesecek şekilde ayarlamış olmamız. Bu özellikle ilgili <a href="https://developer.mozilla.org/en-US/docs/CSS/text-overflow">mozilla geliştirici sitesinde</a> de örnekler mevcut.

Son duruma bakalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-9.44.49-AM.png"><img class="alignnone size-full wp-image-285" title="Screen Shot 2012-10-21 at 9.44.49 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-21-at-9.44.49-AM.png" height="409" width="628" /></a>

Ürünler sayfamızı tamamladık. Peki tek bir ürünü incelemek ve sipariş vermek istediğimizde ne olacak? O da bir sonraki yazıya.

Dayanışmayla!
Meraklı Bilişimci