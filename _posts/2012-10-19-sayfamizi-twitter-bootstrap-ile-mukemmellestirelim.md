---
ID: 246
post_title: >
  Sayfamızı Twitter Bootstrap ile
  mükemmelleştirelim
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/sayfamizi-twitter-bootstrap-ile-mukemmellestirelim/
published: true
post_date: 2012-10-19 07:28:46
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/boot2.png"><img class="alignnone size-full wp-image-250" title="boot2" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/boot2.png" height="350" width="600" /></a>

Twitter Bootstrap kütüphanesini kullanmaya başlamadan önce bu kütüphanenin çalışma mantığıyla ilgili bilmemiz gereken birkaç şey var. Bu kütüphane, etiketlerin class özelliklerine eklediğimiz görevleri görüyor ve bunların görünümünü bu görevlere göre otomatik olarak değştiriyor. Biraz daha açalım.
<pre><code>&lt;div class="container"&gt;&lt;/div&gt;</code></pre>
Kütüphanemizin mantığı 960 piksel üzerine kurulu demiştik. Bootstrap bu 960 pikseli 12'ye bölerek çalışıyor. Öncelikle bu sistemi kullanabilmemiz için kök eleman belirlemeliyiz ki, hem sayfayı ortalayalım, hem boyu 960 olsun, hem de istediğimiz gibi bölebilelim. İşte bunun için yukarıdaki container sınıfına sahip olan div elemanını kullanacağız. Kök elemanını oluşturduktan sonra, her 12'ye böldüğümüz ve kutularla doldurduğumuz sıra için bir de satır elemanı oluşturmamız gerekiyor.
<pre><code>&lt;div class="container"&gt;
    &lt;div class="row"&gt;&lt;/div&gt;
&lt;/div&gt;</code></pre>
Bu satır elemanlarını da artık istediğimiz gibi kutularla doldurabiliriz.
<pre><code>&lt;div class="container"&gt;
    &lt;div class="row"&gt;
        &lt;div class="span4"&gt;4&lt;/div&gt;
        &lt;div class="span4"&gt;4&lt;/div&gt;
        &lt;div class="span4"&gt;4&lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="row"&gt;
        &lt;div class="span6"&gt;6&lt;/div&gt;
        &lt;div class="span6"&gt;6&lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;</code></pre>
Burada ilk satırı 4 birim genişliğinde iki kutuyla, ikinci satırı ise 6 birim genişliğinde iki kutuyla doldurduk.

Bu örneğimizi daha güzel göstermek için de şöyle bir biçim kullanalım:
<pre><code>
&lt;style type="text/css"&gt;
.row &gt; div
{
    background-color: #eee;
    text-align: center;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    border-radius: 3px;
    min-height: 40px;
    line-height: 40px;
    margin-top:10px;
    margin-bottom: 10px;
}
&lt;/style&gt;
</code></pre>
Biçim dosyamızı açıklamak gerekirse;
<ul>
	<li>background-color ile arkaplan rengini #eee değerine getirdik.</li>
	<li>text-align ile kutu içindeki yazıları ortaladık</li>
	<li>-webkit-border-radius, -moz-border-radius ve border-radius özelliği ile kutumuzun kenarlarını 3px çapında yuvarladık. Bu özelliğin tüm tarayıcılarda çalışması için, 3 şeklinin de kullanılması gerekiyor.</li>
	<li>min-height ile en düşün yüksekliği 40 piksele getirdik</li>
	<li>line-height ile de satır genişliğini 40 piksele ayarladık</li>
	<li>margin top ve bottom özellikleri ile de öğeler alt ve üstlerinde 10 piksellik boşluk olmasını sağladık ki birbirlerine yapışmasınlar.</li>
</ul>
Şimdi ortaya çıkan sonucu görelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-10.04.49-AM.png"><img class="alignnone size-medium wp-image-248" title="Screen Shot 2012-10-19 at 10.04.49 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-10.04.49-AM.png?w=300" height="37" width="300" /></a>

Mantığı anlamaya başladık değil mi? Bu sayede hem okunabilir, hem de derli toplu bir görünümü kolayca elde edebiliyoruz.

Geçici stili ve kutularımızı silelim ve gelelim web sayfamıza. Sayfa id'sine sahip olan kök div'imiz zaten elimizde mevcuttu. Buna class olarak container ekleyelim.
<pre><code>&lt;div id="sayfa" class="container"&gt;&lt;!-- Twitter Bootstrap için ekledik--&gt;</code></pre>
Bunun altındaki header etiketimize de row özelliği verelim. İçindeki logo ve şirket ismi kutucuklarına marka diyelim, bağlantı listemizi de bağlantılar adındaki bir kutunun içine alalım. Logo'yu içinde tutan kutumuzun boyu 1 birim, şirket adını içinde tutan kutunun boyu ise 2 birim olsun:
<pre><code>
        &lt;div id="marka"&gt;
            &lt;div id="logo" class="span1"&gt;
                &lt;img src="logo.jpg" alt="Logo" /&gt;
            &lt;/div&gt;
            &lt;hgroup class="span2"&gt;
                &lt;h1&gt;Kızılyıldız&lt;/h1&gt;
                &lt;h4&gt;Matbaacılık A.Ş.&lt;/h4&gt;
            &lt;/hgroup&gt;
        &lt;/div&gt;
</code></pre>
Daha sonra bağlantı listemizi de baglantilar adında bir kutunun içine yerleştirelim. Bu kutunun da boyu 8 birim olsun. 12 birimin tamamını kullanmadığımıza dikkat ettiniz mi? Eğer taşma olursa, alt satıra düşmeyi engellemek için yaptık bunu. Bağlantı listemizi yatay ve Bootrap görünümüne getirebilmek için ilk kutuya navbar, onun içindeki nav etiketine de navbar-inner, daha içerideki numarasız ul liste etiketine de nav nac class'larını verelim. Bootstrap'te böyle tanımlanmış çünkü.
<pre><code>
&lt;div id="baglantilar" class="span8 navbar"&gt;
            &lt;nav class="navbar-inner"&gt;
                &lt;ul class="nav"&gt;
                    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="urunler.html"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="haberler.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="iletisim.html"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/nav&gt;
        &lt;/div&gt;
</code></pre>
Headeri kapatalım ve devam edelim. Karşımıza şöyle bir görüntü gelecek:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-10.18.06-AM.png"><img title="Screen Shot 2012-10-19 at 10.18.06 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-10.18.06-AM.png" height="67" width="628" /></a>

O da ne? Herşey tavana yapışmış vaziyette. Hatta birbirlerine değenler var. Peki ne yapacağız. İşte bunun için temel CSS bilgimizi konuşturmamız gerekiyor.

Bootstrap.min.css dosyasını eklediğimiz &lt;link rel=""&gt; etiketini hatırladınız mı? İşte onun altına &lt;link href="css/custom.css" rel="stylesheet"&gt; etiketini ekleyelim. Yeni bir dosya yaratacağız. Adını da custom.css koyacağız. Kendi css özelliklerimizi buraya yazacağız ki, twitter bootstrap kütüphanesini bozmayalım ve elimizde de temiz bir css dosyası olsun. Css dizini altında herhangi bir text editör veya ide vasıtasıyla custom.css dosyasını oluşturalım.

İlk isteğimiz yapışanları ayıklamak. Dosyanın içine sırayla aşağıdaki kodları yazalım.
<pre><code>
#marka
{
    float:left;
}

#baglantilar
{
    float:right;
    margin:20px;
}

#logo
{
    margin:10px;
}

header
{
    margin-bottom:10px;
}
</code></pre>
Burada ne yaptık? Sırayla açıklayalım.
<ol>
	<li>Marka adındaki logo ve şirket ismini içeren kutumuzu sola yasladık.</li>
	<li>Baglantılar adındaki kutumuzu ise sağa yasladık. Her tarafından 20 piksel boyunda mesafe bıraktık.</li>
	<li>logo adındaki kutumuz için de her yönden 10 piksel mesafe bıraktık ki yapışmasın.</li>
	<li>Tüm header etiketimiz için de alt tarafa 10 piksellik boşluk verdik.</li>
</ol>
Şimdi dosyaya tekrar bakalım. Karşımıza şöyle bir sonuç çıkmalı:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-10.26.36-AM.png"><img class="alignnone size-full wp-image-252" title="Screen Shot 2012-10-19 at 10.26.36 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-10.26.36-AM.png" height="54" width="628" /></a>

Şimdi elimizde çok daha güzel, okunaklı ve profesyonel bir üst kısım var. Sonraki yazıda kalan bölümleri de düzenleyeceğiz.

Dayanışmayla!
Meraklı Bilişmci