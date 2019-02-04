---
ID: 226
post_title: >
  Profesyonel bir görünüm için CSS
  kütüphanelerini kullanalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/profesyonel-bir-gorunum-icin-css-kutuphanelerini-kullanalim/
published: true
post_date: 2012-10-19 06:24:35
---
Birçok sitede kullanılan ve birçok ihtiyaca cevap veren CSS kütüphaneleri var. Sitemizle ilgili herşeyi tek tek yazmak yerine daha önceden test edilmiş ve onaylanmış bu kütüphaneleri kullanmak verimliliğimizi artırıyor. Bu CSS kütüphaneleri hem bize kolaylık sağlıyor, hem de profesonel bir görünüm sağlıyor.

[gallery columns="4"]

Gelelim bu kütüphanelerin çalışma prensiplerine. Bu kütüphaneler genellikle sayfayı artık standart olmuş sayı olan 960 piksel boyuna getiriyor. Peki neden 960? Çünkü istendiği gibi bölünebilen bir sayı da ondan. Genellikle 24 parçaya ayrılan sayfa boyunda istendiği gibi kutu genişlikleri birbirinin üzerine çakışmayacak şekilde ayarlanabiliyor. Yazı tipleri, kutu kenarları ayarlı olduğu ve birçok tarayıcıda da test edildikleri için, sayfamız hangi tarayıcıda nasıl görünecek diye bir derdimiz de kalmıyor. Hatta öyle kütüphaneler var ki, responsive yani iphone için ayrı, android için ayrı, ipad için ayrı arayüz sağlayarak sayfamızın her platformda çalışmasını garanti ediyor.

Ben projelerimde Twitter Bootstrap kullanıyorum. Birçok web uygulamasında tercih edilen bu kütüphane twitterin kendi arayüzünde kullanılan resmi CSS kodu aslında. Twitter geliştiricileri bu kodu açık kaynaklı olarak da kullanıma açmışlar. Bu kütüphaneyi kullanabilmemiz için bir önceki derste anlattığım temel CSS bilgisini de bilmemiz yetiyor.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/bootstrap-from-twitter.jpeg"><img class="alignnone size-medium wp-image-234" title="Bootstrap-from-Twitter" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/bootstrap-from-twitter.jpeg?w=300" height="279" width="300" /></a>

Şimdi gelelim bu kütüphaneyi nasıl kullanacağımıza. Daha önce dediğimiz gibi CSS biçimlerini style etiketleri içinde kullanbiliyorduk. Ancak birden fazla sayfayı aynı biçimle yönetmek istersek bu yöntem sorun olur. Hem gereksiz kod tekrarı, hem de sunucu alanı kaybı. Üstelik kodda değişiklik yapmak istersek binlerce html dosyasını değiştirmeye çalışmak eziyet olur. Bu yüzden birden fazla dosyadan tek bir css dosyasına ulaşmak istediğimizde head etiketinin içine aynı klasörde oluşturduğumuz css dosyasının adresini şu şekilde yazmamız gerekiyor.
<pre><code>&lt;link rel="stylesheet" href="common.css" type="text/css"&gt;
</code></pre>
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-6.25.16-AM.png"><img class="alignnone size-medium wp-image-235" title="Screen Shot 2012-10-19 at 6.25.16 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-6.25.16-AM.png?w=300" height="234" width="300" /></a>

CSS kodumuzu bu şekilde çağırıyoruz. Peki Twitter Bootstrap kütüphanesini kullanmak için ne yapmamız gerekiyor? Adım adım anlatmak gerekirse:

<strong>1.</strong> Önce <a href="http://twitter.github.com/bootstrap/index.html">http://twitter.github.com/bootstrap/index.html</a>adresinden kütüphaneyi indirelim.
<strong>2.</strong> bootstrap.zip dosyasını açalım ve içindeki css, js, ve img dizinlerini  index.html olarak kaydettiğimiz html sayfamızın bulunduğu dizine kopyalayalım.
<strong>3.</strong> Sitede söylendiği şekilde head etiketinin altına aşağıdaki kodları ekleyelim:
<pre><code>&lt;!-- Bootstrap --&gt;
&lt;link href="css/bootstrap.min.css" rel="stylesheet"&gt;
</code></pre>
4. Daha sonra yine sitede gösterildiği şekilde body etiketinin kapandığı &lt;/body&gt; etiketinin hemen üstüne aşağıdaki js çağırma kodlarını ekleyelim:
<pre><code>&lt;script src="http://code.jquery.com/jquery-latest.js"&gt;&lt;/script&gt;
&lt;script src="js/bootstrap.min.js"&gt;&lt;/script&gt;
</code></pre>
Burada dikkati çekmek istediğim bir nokta var. JS kodlarını bu şekilde çağırıyoruz. Yani Script etiketi ve src özelliklerini kullanarak. Ancak bir diğer dikkat etmemiz gerek nokta, js çağıran veya içeren script kodlarını sayfanın sonuna ekliyor oluşumuz. Bu tüm sayfa etiketlerinin yüklendikten sonra javasScript kodunun doğru çalışmasından emin olmamızı sağlıyor. Peki javaScript nedir diye soruyorsanız korkmayın onu da zamanı geldiğinde anlatacağım. Şimdilik bu kadarını bilmemiz yeterli.

Bütün bunları yaptıktan sonra sayfamızın kodlarının nasıl göründüğüne bir göz atalım:
<pre><code>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta http-equiv="content-type" content="text/html; charset=UTF-8" /&gt;
    &lt;meta name="description" content="Kızılyıldız İstanbul, Sirkeci'de faaliyet göstermekte olan tasarıma önem veren yenilikçi matbaa şirketi. Başlıca ürünlerimiz: Davetiye, Ajanda, Poster ve El ilanı"/&gt;
    &lt;meta name="keywords" content="kızılyıldız, kızıl, yıldız, matbaa, baskı, ajanda, davetiye, poster, ilan, istanbul, sirkeci"/&gt;
    &lt;title&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/title&gt;
    &lt;link href="css/bootstrap.min.css" rel="stylesheet"&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id="sayfa"&gt;
        &lt;header&gt;
            &lt;div id="logo"&gt;
                &lt;img src="logo.jpg" alt="Logo" /&gt;
            &lt;/div&gt;
            &lt;hgroup&gt;
                &lt;h1&gt;Kızılyıldız&lt;/h1&gt;
                &lt;h2&gt; Matbaacılık A.Ş.&lt;/h2&gt;
            &lt;/hgroup&gt;
            &lt;nav&gt;
                &lt;ul&gt;
                    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="urunler.html"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="haberler.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="iletisim.html"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/nav&gt;
        &lt;/header&gt;
        &lt;aside&gt;
            &lt;div id="iletisimTel"&gt;
                &lt;div id="tel"&gt;Tel: +90 212 444 19 17&lt;/div&gt;
                &lt;div id="fax"&gt;Fax: +90 212 444 19 05&lt;/div&gt;
            &lt;/div&gt;
        &lt;/aside&gt;
        &lt;section id="icerik"&gt;
            &lt;div id="mesaj"&gt;
                &lt;h1&gt;&lt;strong&gt;İstanbul'daki en hızlı, en kaliteli ve en uygun fiyatlı matbaayı mı arıyorsunuz?&lt;/strong&gt;&lt;/h1&gt;
                &lt;a href="urunler.html"&gt;Ürünlerimizi inceleyin&lt;/a&gt;
            &lt;/div&gt;
            &lt;div id="bilgiler"&gt;
                &lt;article id="neyapiyoruz"&gt;
                    &lt;h3&gt;Ne yapıyoruz?&lt;/h3&gt;
                    &lt;p&gt;İstanbul'dasınız, davetiye, broşür, poster veya el ilanı'na ihtiyacınız var. Hem de 3 günde. Fiyatı da biraz uygun olsun ama sonuçlar temiz mi olsun? O zaman doğru yere geldiniz.&lt;/p&gt;
                &lt;/article&gt;   
                &lt;article id="neredeyiz"&gt;
                    &lt;h3&gt;Neredeyiz?&lt;/h3&gt;
                    &lt;p&gt;İstanbul'un tarihi merkezi Sirkeci'deyiz. Ama mesafeler sorun değil. Siz bize gelemezseniz, biz size geliriz. Siparişim ayağıma gelsin diyorsanız, o da olur. &lt;/p&gt;
                &lt;/article&gt;  
                &lt;article id="farkımız"&gt;
                    &lt;h3&gt;Bizim farkımız&lt;/h3&gt;
                    &lt;p&gt;Kesin kalite garantisine ihtiyacınız varsa, ücretsiz motorsikletli kuryeyle baskı işlerim gönderilsin diyorsanız, fiyatlar uygun olsun ama fazla da gecikmesin 3 gün içinde elimde olsun istiyorsanız, aradığınız yer burası. &lt;/p&gt;
                &lt;/article&gt;  
            &lt;/div&gt;
        &lt;/section&gt;
        &lt;footer&gt;
            &lt;nav&gt;
                &lt;ul&gt;
                    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/nav&gt;
            &lt;div id="iletişim"&gt;
                &lt;div id="adres"&gt;
                    Adres:
                    Kızılyıldız Matbaacılık A.Ş.
                    Denizler Mah.
                    Eren Sok. No:68
                    Sireci, Fatih 34110
                    İstanbul TÜRKİYE
                &lt;/div&gt;
                &lt;div id="telefon"&gt;
                    Tel: +90 212 444 19 17
                    Fax: +90 212 444 19 05
                &lt;/div&gt;
            &lt;/div&gt;
            &lt;div id="copyright"&gt;Her Hakkı Saklıdır. 2012 Kızılyıldız Matbaacılık A.Ş.&lt;/div&gt;
        &lt;/footer&gt;
    &lt;/div&gt;
&lt;script src="http://code.jquery.com/jquery-latest.js"&gt;&lt;/script&gt;
&lt;script src="js/bootstrap.min.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
Sayfamızın son görüntüsü de şu şekilde:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-6.45.52-AM.png"><img class="alignnone size-full wp-image-236" title="Screen Shot 2012-10-19 at 6.45.52 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-6.45.52-AM.png" height="587" width="360" /></a>

Gördüğümüz gibi fontlar, bağlantılar daha bir güzel ve modern görünüyor. Bu da Twitter Bootstrap kütüphanesi sayesinde oldu.

Eğer Google Chrome veya Firefox kullanıyorsanız, herhangi bir yazının üzerine sağ tıkladığınızda öğeyi incele bağlantısına tıklarsanız, geliştirici araçlarına ulaşırsınız. Bu aracı kullanmayı web geliştirme öğrenmek isteyen birinin kesinlikle bilmesi gerekiyor. Görsel öğrenin arkasındaki kodu alenen görebilmemizi sağlıyor.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-9.20.49-AM.png"><img class="alignnone size-full wp-image-237" title="Screen Shot 2012-10-19 at 9.20.49 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-9.20.49-AM.png" height="337" width="392" /></a>

İşte bunu açtığımızda Twitter Bootstrap'ın yaptığı işleri görebiliriz. Burada da h1, h2 ve diğer etiketleri düzenleyen css kodlarını görüyoruz.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-9.22.02-AM.png"><img class="alignnone size-full wp-image-238" title="Screen Shot 2012-10-19 at 9.22.02 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-9.22.02-AM.png" height="288" width="308" /></a>

Şimdi siz de css dizini içindeki bootstrap.css dosyasını açın, kurcalayın ve nasıl çalıştığını görün. Bir sonraki yazıda kütüphaneyi kullanarak sayfamızı tamamlayacağız.

Dayanışmayla!
Meraklı Bilişimci