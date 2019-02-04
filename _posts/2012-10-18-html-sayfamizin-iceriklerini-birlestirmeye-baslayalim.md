---
ID: 208
post_title: >
  HTML sayfamızın içeriklerini
  birleştirmeye başlayalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/html-sayfamizin-iceriklerini-birlestirmeye-baslayalim/
published: true
post_date: 2012-10-18 18:10:13
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5_logo_5121.png"><img class="alignnone size-medium wp-image-214" title="HTML5_Logo_512" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5_logo_512.png?w=300" height="300" width="300" /></a>

Şimdi elimizde tüm içeriklerimiz var ve artık sıra geldi bunları sayfamızda birleştirmeye. Önce elimizdeki sayfamıza bakalım ve içeriklerimizi yerleştirelim.
<pre><code>&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta http-equiv="content-type" content="text/html; charset=UTF-8" /&gt;
    &lt;meta name="description" content="Kızılyıldız İstanbul, Sirkeci'de faaliyet göstermekte olan tasarıma önem veren yenilikçi matbaa şirketi. Başlıca ürünlerimiz: Davetiye, Ajanda, Poster ve El ilanı"/&gt;
    &lt;meta name="keywords" content="kızılyıldız, kızıl, yıldız, matbaa, baskı, ajanda, davetiye, poster, ilan, istanbul, sirkeci"/&gt;
    &lt;title&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div id="sayfa"&gt;
        &lt;div name="ustbilgi"&gt;
            &lt;div name="logo"&gt;&lt;/div&gt;
            &lt;h1&gt;Kızılyıldız&lt;/h1&gt;
            &lt;h2&gt;Matbaacılık A.Ş.&lt;/h2&gt;
            &lt;div name="baglantilar"&gt;
                &lt;ul&gt;
                    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="urunler.html"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="haberler.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="iletisim.html"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/div&gt;
        &lt;/div&gt;
        &lt;div name="iletişim"&gt;
            &lt;div name="telefon"&gt;
                Tel: +90 212 444 19 17
                Fax: +90 212 444 19 05
            &lt;/div&gt;
        &lt;/div&gt;
        &lt;div name="icerik"&gt;
            &lt;div name="mesaj"&gt;
                &lt;h1&gt;&lt;strong&gt;İstanbul'daki en hızlı, en kaliteli ve en uygun fiyatlı matbaayı mı arıyorsunuz?&lt;/strong&gt;&lt;/h1&gt;
                &lt;a href="urunler.html"&gt;Ürünlerimizi inceleyin&lt;/a&gt;
            &lt;/div&gt;
            &lt;div name="bilgiler"&gt;
                &lt;div name="neyapiyoruz"&gt;
                    &lt;h3&gt;Ne yapıyoruz?&lt;/h3&gt;
                    &lt;p&gt;İstanbul'dasınız, davetiye, broşür, poster veya el ilanı'na ihtiyacınız var. Hem de 3 günde. Fiyatı da biraz uygun olsun ama sonuçlar temiz mi olsun? O zaman doğru yere geldiniz.&lt;/p&gt;
                &lt;/div&gt;   
                &lt;div name="neredeyiz"&gt;
                    &lt;h3&gt;Neredeyiz?&lt;/h3&gt;
                    &lt;p&gt;İstanbul'un tarihi merkezi Sirkeci'deyiz. Ama mesafeler sorun değil. Siz bize gelemezseniz, biz size geliriz. Siparişim ayağıma gelsin diyorsanız, o da olur. &lt;/p&gt;
                &lt;/div&gt;  
                &lt;div name="farkımız"&gt;
                    &lt;h3&gt;Bizim farkımız&lt;/h3&gt;
                    &lt;p&gt;Kesin kalite garantisine ihtiyacınız varsa, ücretsiz motorsikletli kuryeyle baskı işlerim gönderilsin diyorsanız, fiyatlar uygun olsun ama fazla da gecikmesin 3 gün içinde elimde olsun istiyorsanız, aradığınız yer burası. &lt;/p&gt;
                &lt;/div&gt;  
            &lt;/div&gt;
        &lt;/div&gt;
        &lt;div name="altbilgi"&gt;
            &lt;div name="altbaglantılar"&gt;
                &lt;ul&gt;
                    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/div&gt;
            &lt;div name="iletişim"&gt;
                &lt;div name="adres"&gt;
                    Adres:
                    Kızılyıldız Matbaacılık A.Ş.
                    Denizler Mah.
                    Eren Sok. No:68
                    Sireci, Fatih 34110
                    İstanbul TÜRKİYE
                &lt;/div&gt;
                &lt;div name="telefon"&gt;
                    Tel: +90 212 444 19 17
                    Fax: +90 212 444 19 05
                &lt;/div&gt;
            &lt;/div&gt;
            &lt;div name="copyright"&gt;Her Hakkı Saklıdır. 2012 Kızılyıldız Matbaacılık A.Ş.&lt;/div&gt;
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
Bitti mi? Hayır. Etiketlerimizi tamamladık ama sayfamızı <strong>HTML5</strong>'e uygun hale getirmemiz gerekiyor. HTML5 ile gelen yeni ve çok yararlı etiketler var. Sayfamızı bu halde bıraksak belki HTML4 olarak uyumlu olur ve çalışır ama, HTML5'in getirdiği yeniliklerden yararlanmak istiyorsak, bir kaç iyileştirme yapmamız lazım. Şimdi gelelim HTML5 ile gelen yeni etiketlerin başlıcalarına:
<ul>
	<li><strong>Section:</strong> Sayfa içinde farklı bölümleri oluşturmamıza yarıyor. Div gibi değil. Farkı şu, örneğin bir sayfa içinde 3 ayrı konu ile ilgili bölüm hazırladınız. Yelken, Kayak ve Sörf gibi. Görüntüleme ile ilgili bölümlerde ise div kullanmak gerekiyor.</li>
	<li><strong>Article:</strong> Makale etiketi. Örneğin blog sayfanız var, yazılarınızı makale etiketi içerisine yazabilirsiniz. Ya da duyuru haberlerinizi article etiketi içinde tutmalısınız.</li>
	<li><strong>Nav: </strong>Bağlantı listelerimizi artık navbar içinde tutmamız gerekiyor ki hem tarayıcılar hem de arama motorları sayfamızı iyi anlasın ve yorumlasınlar.</li>
	<li><strong>Aside: </strong>İlk olarak sadece article içinde yan bilgi vermeye izin veren bir etiketti. Ancak daha sonra itirazlar üzerine, yanpanel olarak da kullanılmasına izin verecek şekilde değiştirildi. Sayfanızda yan bilgileri, reklamları burada tutabilirsiniz. Biz de iletişim bilgimizi burada tutacağız.</li>
	<li><strong>Header: </strong>Artık logo, navbar, başlık gibi bilgileri tuttuğumuz bir etiketimiz var. Üstbilgilerimiz de burada yer alacak.</li>
	<li><strong>Footer: </strong>Yine üst bilgi gibi, altbilgiler için de yeni bir etiketimiz mevcut.</li>
	<li><strong>Hgroup: </strong>Biraz ayrıntı gibi görünebilir ama h1 h2 gibi birlikte yeralan başlıkları da bu etiket içinde tutmamızda yarar var.</li>
</ul>
Bir diğer değişiklik ise artık <strong>div</strong> etiketlerinde name kullanamıyoruz. Bunun yerine id kullanacağız. id özelliğinde dikkat edilmesi gerekn ise bir id'de kullandığımız kelimeyi başka birinde kullanamıyoruz. Kelime eşsiz olmak zorunda.

Şimdi bu kurallara göre sayfamızı HTML5 ile uyumlu hale getirelim ve teknolojiyi yakalayalım:
<pre><code>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta http-equiv="content-type" content="text/html; charset=UTF-8" /&gt;
    &lt;meta name="description" content="Kızılyıldız İstanbul, Sirkeci'de faaliyet göstermekte olan tasarıma önem veren yenilikçi matbaa şirketi. Başlıca ürünlerimiz: Davetiye, Ajanda, Poster ve El ilanı"/&gt;
    &lt;meta name="keywords" content="kızılyıldız, kızıl, yıldız, matbaa, baskı, ajanda, davetiye, poster, ilan, istanbul, sirkeci"/&gt;
    &lt;title&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/title&gt;
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
                Tel: +90 212 444 19 17
                Fax: +90 212 444 19 05
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
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
Sonucumuzu görelim. Üstkısım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-18-at-9.04.48-PM.png"><img class="size-full wp-image-210 alignnone" title="Screen Shot 2012-10-18 at 9.04.48 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-18-at-9.04.48-PM.png" height="377" width="393" /></a>

İçerik:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-18-at-9.04.57-PM.png"><img class="size-full wp-image-211 alignnone" title="Screen Shot 2012-10-18 at 9.04.57 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-18-at-9.04.57-PM.png" height="502" width="393" /></a>

Alt kısım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-18-at-9.05.05-PM.png"><img class="alignnone size-full wp-image-212" title="Screen Shot 2012-10-18 at 9.05.05 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-18-at-9.05.05-PM.png" height="156" width="375" /></a>

İşte elimizde modern, tüm bilgileri içeren ve her tarayıcıda kolayca açılabilecek bir internet sayfası var. Bir sonraki yazıda bölümlerimizi oluşturmaya başlayacağız ve ufak ufak sayfamızın tasarımını değiştirmeye başlayacağız. Bunun için kullanacağımız araç ise tabii ki HTML5 ile beraber gelen CSS3.

Dayanışmayla,
Meraklı Bilişimci