---
ID: 218
post_title: >
  Sayfamızın içeriğini CSS3 ile
  güzelleştirelim
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/sayfamizin-icerigini-css3-ile-guzellestirelim/
published: true
post_date: 2012-10-19 02:21:38
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5css3.png"><img class="alignnone size-medium wp-image-223" title="html5css3" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5css3.png?w=300" height="300" width="300" /></a>

Ana sayfamızı hallettik. Ama daha güzel görünmesini istiyoruz. Peki ne yapabiliriz? Örneğin Logo'nun üstte olmasını, bazı elemanların yanda, bazı elemanların gölgeli, yuvarlak köşeli olmasını da isteyebiliriz. Hatta animasyon bile hazırlayabiliriz. İşte bunun için HTML5 ile gelen CSS3 var. CSS3'ü ve özelliklerini anlamaya başlayalım. CSS yani "cascading tyle sheet" basamaklı biçim sayfası anlamına gelir.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/box_model.gif"><img class="alignnone size-full wp-image-219" title="box_model" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/box_model.gif" height="400" width="400" /></a>

HTML elemanlarının görüntüsünü düzenlememize yarar. Örneğin sayfamızda bir telefon bilgisini içeren bir kutu yaratmak istemiş olalım. Kutumuzu div etiketiyle oluşturalım ve id özelliğine de iletisimTel diyelim.
<pre> &lt;div id="iletisimTel"&gt;
    &lt;div id="tel"&gt;Tel: +90 212 444 19 17&lt;/div&gt;
    &lt;div id="fax"&gt;Fax: +90 212 444 19 05&lt;/div&gt;
&lt;/div&gt;</pre>
Şimdi adım adım kutumuzu şekillendirmeye başlayalım. CSS kodlarını istersek
<div style="background-color:white;"></div>
gibi yazabiliriz. Ama ben tavsiye etmiyorum. Sonuçta karmakarışık ve yönetilemeyen bir kodunuz olur. Bir numaralı felsefemiz bilgi ve görüntüyü birbirinden mümkün olduğunda ayrı tutmak olmalı. İkinci seçeneğimiz html sayfasının head etiketinin altında &lt;style type="text/css"&gt;&lt;/style&gt; etiketini kullanmak. Aslında bu da iyi bir yöntem değil ama şimdilik bunu kullanacağız.

Önce kutumuzu seçelim: id'si iletisimTel olan kutuyu seçmek istiyoruz. Bunun için # karakterini kullanmamız yeterli. #iletisimTel Tüm etiketleri seçmek istedeydik doğrudan div yazabilirdik.  Kendisi div olup id'si iletisimTel olan kutuyu ise div#iletisimTel şeklinde seçiyoruz. Peki birden fazla kutuyu aynı anda şekil vermek istersek ne olacaktı? Bunun için de class özelliğini kullanmamız gerekiyordu. Örneğin; &lt;div class="yesil"&gt;Yesil kutu&lt;/div&gt; &lt;div class="yesil kirmizikenar"&gt;&lt;/div&gt; dediğimizde .yesil ve .kirmizikenar ifadeleriyle etiketlerimizi seçecektik. Yine etikete özel şekil vermek isteseydik de, div.kirmizi ifadesini kullanacaktık. Örneğimize dönelim:
<pre><code>
&lt;style type="text/css"&gt;
#iletisimTel
{
    width: 250px;
    border: 1px solid black;
    background-color: silver;
    padding:10px;
}
&lt;/style&gt;
</code></pre>
Burada ilk önce elemanımızı seçtik. Daha sonra açtığımız parantezler içerisinde istediğimiz özellikleri tanımlamaya başladık.

İlk önce width özelliği ile kutumuzun genişliğini 250 piksel olarak belirledik. Daha sonra border özelliği ile kenar çizgisini siyah, kesintisiz ve 1 piksel olarak belirledik. Gördüğümüz gibi burada ingilizce renk isimlerini kullanabiliyoruz. Ama istersek #000000 şeklinde 16'lık ren kodu da kullanabilirdik. Buraada 16'lık renk kodu ile ilgili bir ipucu vermek gerekirse, ilk iki hane kırmızı miktarını belirtiyor. Sonraki iki hane yeşil ve son iki hane de mavi miktarını veriyor. İlk iki hane 16*16 yani 0'dan 255'e kadar 256 adet renk miktar değeri elde etmemize yarıyor. Bu sayede web üzerinde 16.777.216 adet renk elde edebiliyoruz. Daha fazlasını merak ediyorsanız 16'lık sayıları araştırın derim.

Backround-color özelliği ile kutumuzun arka plan rengini de belirledik. Rengin silver yani gümüş rengi olmasını belirttik. Son olarak da padding yani kutunun dışından içeriğine kadar olan mesafeyi 10 piksel olarak ayarladık. Her şey tamam olduğunda karşımıza şöyle bir görüntü çıktı:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-5.12.32-AM.png"><img class="alignnone size-full wp-image-220" title="Screen Shot 2012-10-19 at 5.12.32 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-5.12.32-AM.png" height="76" width="289" /></a>

Güzel mi? Tabii ki hayır. Bunun yerine görüntüyü biraz daha modern bir hale getirelim.
<pre><code>
&lt;style type="text/css"&gt;
#iletisimTel
{
        width: 250px;
        border: none;
        background-color: white;
        padding:10px;

        /* Yazıyı kutunun ortasına hizaladık */
        text-align:center;

        /* Kutumuza gölge verdik */
        -moz-box-shadow: 0 0 5px #888;
        -webkit-box-shadow: 0 0 5px#888;
        box-shadow: 0 0 5px #888;

        /* Yazının rengini ve font türünü seçtik */   
        color: gray;
        font:15px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
&lt;/style&gt;
</code></pre>
Örnekte gördüğümüz gibi, CSS içinde yorum yapmak PHP'ye biraz da olsa benziyor. Burada yaptığımız değişiklik ise, kutudaki kenar çizgisini yokettik, arkaplanı beyaz yaptık, yazıyı kutunun ortasına hizaladık, CSS3 ile birlikte gelen yeniliklerden gölge özelliğini kullandık, kutu içindeki yazının renk, büyüklük ve yazıtipi özelliklerini de belirledik. Son olarak görünüm şu şekilde değişti:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-5.19.09-AM.png"><img class="alignnone size-full wp-image-221" title="Screen Shot 2012-10-19 at 5.19.09 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-5.19.09-AM.png" height="70" width="287" /></a>

Nasıl? Daha güzel görünüyor değil mi? Şimdilik CSS ile ilgili yapacaklarımız bu kadar. İsterseniz siz de bu özellkleri kurcalayıp değişiklikler yapabilirsiniz. Arka planı kırmızı, yazı rengini sarı ve kocaman yapabilirsiniz mesela.

Dayanışmayla!
Meraklı Bilişimci