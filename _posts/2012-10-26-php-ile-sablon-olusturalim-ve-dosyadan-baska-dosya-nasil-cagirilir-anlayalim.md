---
ID: 403
post_title: >
  PHP ile şablon oluşturalım ve
  dosyadan başka dosya nasıl
  çağırılır anlayalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-sablon-olusturalim-ve-dosyadan-baska-dosya-nasil-cagirilir-anlayalim/
published: true
post_date: 2012-10-26 03:13:32
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/php_include_require.png"><img class="alignnone size-medium wp-image-406" title="php_include_require" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/php_include_require.png?w=300" height="300" width="300" /></a>

Önceki yazıda dediğimiz gibi, her sayfada tekrar eden elemanları tek tek değiştirmek 10 sayfalık bir sitede eziyet gibi birşeyken, 1000 sayfalık sitede imkansız gibi birşey. Kodların sürekli tekrar edilmesini engellemek ve yeniden kullanmak, gerektiğinde tek bir dosyadan binlerce dosyayı değiştirebilmek için PHP yardımımıza koşacak.

Peki bunu nasıl yapacağız? Bunun için 5 adet dosyaya ihtiyacımız var.
<ol>
	<li>Header.php Üstbilgi bölümlerini tutacağımız bölüm. İçeriğe kadar olan bölümdeki etiketleri burada tutacağız.</li>
	<li>Footer.php Altbilgi bölümlerini tutacağımız bölüm.</li>
	<li>Sidebar.php Yanbilgi olarak tuttuğumuz, sayfa ile içerik olarak bağlantısı olmayan bilgileri tuttuğumuz bölüm.</li>
	<li>Index.php Bütün içerik ve ihtiyacımız olan sayfaları tuttuğumuz bölüm</li>
	<li>page.php</li>
</ol>
Şimdilik index.php'yi anasayfa olarak kullanabiliriz. Diğer sayfalarda da header, footer ve sidebar dosyalarını çağırabiliriz. Şu anda herhangi bir içerik yönetim sistemi veya ajax çağrısı kullanmadığımız için şimdilik bunu böyle yapalım.

Şimdi her sayfada aynı olan header dosyasını görelim:
<pre><code>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta http-equiv="content-type" content="text/html; charset=UTF-8" /&gt;
    &lt;meta name="description" content="Kızılyıldız İstanbul, Sirkeci'de faaliyet göstermekte olan tasarıma önem veren yenilikçi matbaa şirketi. Başlıca ürünlerimiz: Davetiye, Ajanda, Poster ve El ilanı"/&gt;
    &lt;meta name="keywords" content="kızılyıldız, kızıl, yıldız, matbaa, baskı, ajanda, davetiye, poster, ilan, istanbul, sirkeci"/&gt;
    &lt;title&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/title&gt;
    &lt;link href="css/bootstrap.min.css" rel="stylesheet"&gt;
    &lt;link href="css/custom.css" rel="stylesheet"&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id="sayfa" class="container"&gt;&lt;!-- Twitter Bootstrap için ekledik--&gt;
        &lt;header class="row"&gt;
            &lt;div id="marka"&gt;
                &lt;div id="logo" class="span1"&gt;
                    &lt;img src="img/logo.jpg" alt="Logo" /&gt;
                &lt;/div&gt;
                &lt;hgroup class="span3"&gt;
                    &lt;h1&gt;Kızılyıldız&lt;/h1&gt;
                    &lt;h4&gt;Matbaacılık A.Ş.&lt;/h4&gt;
                &lt;/hgroup&gt;
            &lt;/div&gt;
            &lt;div id="baglantilar" class="span8 navbar"&gt;
                &lt;nav class="navbar-inner"&gt;
                    &lt;ul class="nav"&gt;
                        &lt;li&gt;&lt;a href="index.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="urunler.html"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="duyurular.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="iletisim.html"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
                    &lt;/ul&gt;
                &lt;/nav&gt;
            &lt;/div&gt;
        &lt;/header&gt;
&lt;section&gt;
</code></pre>
İşte her sayfada aynı olan üst bilgi kısmı. Altbilgi yani footer.php'nin kodlarını da görelim:
<pre><code>
&lt;/section&gt;
&lt;footer&gt;
    &lt;div class="row"&gt;
    &lt;nav class="span3 offset1"&gt;
        &lt;div class="kutuyazisi footerbox"&gt;
            &lt;h4&gt;Bağlantılar&lt;/h4&gt;
            &lt;ul id="altListe"&gt;
                &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/div&gt;
    &lt;/nav&gt;
    &lt;div class="span4"&gt;
        &lt;div class="kutuyazisi footerbox"&gt;
            &lt;h4&gt;Adres:&lt;/h4&gt;
            Kızılyıldız Matbaacılık A.Ş.
            Denizler Mah.
            Eren Sok. No:68
            Sireci, Fatih 34110
            İstanbul TÜRKİYE
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="span3"&gt;
        &lt;div class="kutuyazisi footerbox"&gt;
            &lt;h4&gt;Telefon&lt;/h4&gt;
            Tel: +90 212 444 19 17
            Fax: +90 212 444 19 05
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="row"&gt;
    &lt;div class="span12"&gt;
        &lt;div class="footer-floor"&gt;
            &lt;div id="copyright"&gt;Her Hakkı Saklıdır. 2012 Kızılyıldız Matbaacılık A.Ş.&lt;/div&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;/div&gt;
&lt;/footer&gt;
&lt;/div&gt;
&lt;script src="http://code.jquery.com/jquery-latest.js"&gt;&lt;/script&gt;
&lt;script src="js/bootstrap.min.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
Şimdilik her sayfada aynı olan bir sidebar kısmı kullanmıyoruz. Ama ileride kullanmak istersek lazım olabilir. Kullanmadığımız için burayı geçiyorum.

Index.php dosyamız anasayfadaki bilgileri içerecek. Aslında bundan sonra tüm diğer sayfalarda section etiketinin altına ve üstüne tek bir php kodu yazacağız.

Yazacağımız sihirli kelime include_once("header.php"). PHP'de include öntanımlı fonksiyonu başka bir dosyanın içindekileri çağırabilmemize yarıyor. İnclude_once ise bu işlemi tek bir sefer yaptığmızdan emin olmamızı sağlıyor. Aynı sayfada iki tane header yani üstbilgi çıkmasının yaratacağı çirkin görüntüyü bir düşünsenize.

Örneğin index.php'nin son haline bakalım.
<pre><code>
&lt;?php
include_once("header.php");
?&gt;
&lt;div id="anaResim"&gt;&lt;img src="img/anaResim.jpg" alt="Ana Resim"/&gt;&lt;/div&gt;
&lt;div id="mesaj"&gt;
    &lt;div class="row"&gt;
        &lt;div class="span12"&gt;
            &lt;h1&gt;&lt;strong&gt;İstanbul'daki en hızlı, en kaliteli ve en uygun fiyatlı matbaayı mı arıyorsunuz?&lt;/strong&gt;&lt;/h1&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="row"&gt;
        &lt;div id="inceleyin" class="span4 offset8"&gt;
            &lt;a class="btn btn-primary btn-large"  href="urunler.html"&gt;Ürünlerimizi inceleyin&lt;/a&gt;
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;
&lt;div id="bilgiler" class="row"&gt;
    &lt;article id="neyapiyoruz" class="span4"&gt;
        &lt;div class="kutuyazisi"&gt;
            &lt;h3&gt;Ne yapıyoruz?&lt;/h3&gt;
            &lt;p&gt;İstanbul'dasınız, davetiye, broşür, poster veya el ilanı'na ihtiyacınız var. Hem de 3 günde. Fiyatı da biraz uygun olsun ama sonuçlar temiz mi olsun? O zaman doğru yere geldiniz.&lt;/p&gt;
        &lt;/div&gt;
    &lt;/article&gt;   
    &lt;article id="neredeyiz" class="span4"&gt;
        &lt;div class="kutuyazisi"&gt;
            &lt;h3&gt;Neredeyiz?&lt;/h3&gt;
            &lt;p&gt;İstanbul'un tarihi merkezi Sirkeci'deyiz. Ama mesafeler sorun değil. Siz bize gelemezseniz, biz size geliriz. Siparişim ayağıma gelsin diyorsanız, o da olur. &lt;/p&gt;
        &lt;/div&gt;
    &lt;/article&gt;  
    &lt;article id="farkımız" class="span4"&gt;
        &lt;div class="kutuyazisi"&gt;
            &lt;h3&gt;Bizim farkımız&lt;/h3&gt;
            &lt;p&gt;Kesin kalite garantisine ihtiyacınız varsa, ücretsiz motorsikletli kuryeyle baskı işlerim gönderilsin diyorsanız, fiyatlar uygun olsun ama fazla da gecikmesin 3 gün içinde elimde olsun istiyorsanız, aradığınız yer burası. &lt;/p&gt;
        &lt;/div&gt;
    &lt;/article&gt;  
&lt;/div&gt;
&lt;?php
include_once("footer.php");
?&gt;
</code></pre>
Yeni dosyamızı oluşturduk. Şimdi bu <a href="http://127.0.0.1/phpEgitimi2.1/index.php">http://127.0.0.1/phpEgitimi2.1/index.php</a> adresinden çağırırsanız tam olarak karşınıza şu sayfanın gelmesi lazım.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.44.15-PM.png"><img class="alignnone size-full wp-image-398" title="Screen Shot 2012-10-25 at 4.44.15 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.44.15-PM.png" height="389" width="628" /></a>

Sayfa bu haliyle eksiksiz karşınıza geldiyse, tebrikler. İlk PHP websitesi şablonunuzu oluşturdunuz. Artık üstteki bir linki değiştirmek için tekrar tekrar sayfalarca html dosyasını düzeltmenize gerek yok.

Şimdi bir işlem daha yapabiliriz. index.php ve diğer sayfalarda bu include işlemini tekrarlamak yerine, index.php ye göndereceğimiz bir değişkenle bu işi çözebiliriz. Örneğiin: http://127.0.0.1/phpEgitim2.1/index.php?sayfa=anaSayfa gibi bir ifadeyle tekbir defada tüm sayfaları çağırabiliriz.

Şimdi tekrar index.php kodumuza bakalım
<pre><code>
&lt;?php
include_once("header.php");
if(isset($_GET["sayfa"]))
{
    $sayfa = $_GET["sayfa"].".php";
}
else
{
    $sayfa = "anasayfa.php";
}
include($sayfa);
include_once("footer.php");
?&gt;
</code></pre>
Burada ilk önce header.php'yi çağırdık. Eğer url vasıtasıyla sayfa adlı değişken sayfamıza geldiyse çağır dedik. Eğer yoksa doğrudan anasayfaya yönlendir dedik.

Mesela olmayan bir sayfayı açmaya çalışırsak ne olur?

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-26-at-5.13.20-AM.png"><img class="alignnone size-full wp-image-405" title="Screen Shot 2012-10-26 at 5.13.20 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-26-at-5.13.20-AM.png" height="314" width="628" /></a>

Bu sayfada hata mesajı aldık. Çünkü php yorumlayıcısı o sayfayı sunucuda bulamadı. Ancak sayfayı aşağı kaydırdığımızda footeri görebiliriz. Bu include fonksiyonu kullanmamızdan kaynaklanıyor. İnclude dosyayı bulamasa bile hata verir ama kodu okumaya devam eder. Eğer require veya require_once fonksiyonunu kullanmış olsaydık, sayfa hata verecekti ve çalışmayı durduracaktı. Dolayısıyla biz de footer'i göremeyecektik, çünkü geri kalan komutlar çalıştırılmayacaktı.

Almamız gereken bir güvenlik önlemi var. Sonuçta dışarıdan bir değişkenin, dosya sistemimize erişmesini sağlıyoruz. Tüm sunucu yapımızın (../../..) karakterleri kullanılarak bir üst klasördeki dosyaların veya dizinlerin açığa çıkmasını istemiyorsak, sayfa değişkeninin içindeki . ve / karakterlerini yoketmemiz lazım. Bunun için PHP'nin realpath() fonksiyonunu kullanmalıyız. realpath($sayfa) ifadesi ../../dizin gibi bir girdiden /dizin çıktısını her şartta üreterek bizi üst dizinler konusunda endişelenme derdinden de kurtaracak.

Hatta en doğrusu biz content adında bir klasör oluşturarak içerik dosyalarımızı oradan çağıralım. Bunları yaptığımızda index.php dosyamızın son hali şu şekilde olmalı:

<pre><code>
&lt;?php
include_once("header.php");
if(isset($_GET["sayfa"]))
{
    $sayfa = preg_replace('/[^a-zA-Z0-9_\.\-&amp;=]/', '', $_GET["sayfa"]);
    //realpath ile üst dizinlere girişi önleyelim
    $sayfa = realpath("content/".$sayfa.".php");
    //preg_replace ile a-ZA-Z0-9_.-&amp;= karakterleri harici herşeyi yokedelim.
}
else
{
    $sayfa = "content/anasayfa.php";
}
include($sayfa);
include_once("footer.php");
?&gt;
</code></pre>

$sayfa = preg_replace('/[^a-ZA-Z0-9_\.\-&amp;=]/', '', $sayfa); Koduna dikkat ettiniz mi? Bu tarz güvenlik olaylarında biraz paranoyak olmakta yarar var. Sonuçta kodumuza veri alıyoruz ve dosya sisteminde kullanıyoruz. Biz de bir dosya adında olamayacak tırnak işareti gibi güvenlik açıklarına yolaçabilecek tüm karakterleri aradık ve temizledik. Bu da bize ekstra güvenlik sağladı. preg_replace fonksiyonu ile ilgili ek bilgi vermek gerekirse, bu verdiğimiz kurallı ifade (regex)'e göre arayıp değiştirme yapmaya yarıyor. Kurallı ifade ne diyecek olursanız o da ayrı bir kitap konusu. Merak ederseniz araştırmayı size bırakıyorum. Ama kısaca belli koşullara göre arama yapmamızı sağlayan ifadeler diyelim. Şimdilik bu kadarını bilsek yeterli. İleride başka yerlerde lazım olduğunda daha çok detaya gireriz.

Son olarak yapmamız gereken birşey var. Header.php içindeki linkleri yeni hallerine göre yani index.php?sayfa=icerik olarak değiştirelim.

<pre><code>&lt;div id="baglantilar" class="span8 navbar"&gt;
    &lt;nav class="navbar-inner"&gt;
        &lt;ul class="nav"&gt;
            &lt;li&gt;&lt;a href="?sayfa=anasayfa"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="?sayfa=hakkimizda"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="?sayfa=urunler"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="?sayfa=duyurular"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="?sayfa=kurumsal"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="?sayfa=iletisim"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
        &lt;/ul&gt;
    &lt;/nav&gt;
&lt;/div&gt;</code></pre>

İşte şimdi elimizde temiz ve güvenli bir içerik yönetim sistemine doğru evrimleşecek bir yazılım var.

Şimdilik bu kadar. Sonraki yazıda form ile veri girişi konusuna geri döneceğiz.

Dayanışmayla!
Meraklı Bilişimci