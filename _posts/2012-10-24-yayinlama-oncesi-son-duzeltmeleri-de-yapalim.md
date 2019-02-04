---
ID: 355
post_title: >
  Yayınlama öncesi son düzeltmeleri de
  yapalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/yayinlama-oncesi-son-duzeltmeleri-de-yapalim/
published: true
post_date: 2012-10-24 20:43:10
---
Aslında neredeyse her şey hazır. Yapmamız gereken bir kaç düzeltme var. Bu tarz düzeltmeler hazırlayacağınız projelerde sizin de başınıza sıkça gelecek. Bu nedenle ben de böyle bir yazı hazırlamayı uygun buldum.

Daha önce yaptığımız tasaırmla ilgili bir kaç tane göze çarpan nokta mevcut. Bazı yan listelerin simetrik görünmemesi durumu. Bir kaç tane örnek verelim. Bunlara siz de tasarımlarınızda dikkat etmelisiniz. Aslında en baştan temiz bir grid yani ızgara sistemi kullanmanızı öneririm. Kitabımızın konusu Kullanıcı Arayüzü (User Interface) tasarımı olmadığı için bu konulara girmeyeceğiz şimdilik.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ui1.png"><img class="wp-image-358 alignnone" title="ui1" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ui1.png?w=300" height="200" width="250" /></a>
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ui21.png"><img class="wp-image-357 alignnone" title="ui2" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ui21.png?w=300" height="185" width="250" /></a>

Burada gördüğümüz asimetrik farklılıkları düzenlememiz lazım. Bunun için header kısmında kullandığımız ölçeği tüm sayfalarda kullanarak işe başlayabiliriz. Header kısmında logo ve nav bölümleri için kullandığımız temel ölçü 4 birime 8 birim. Biz de diğer sayfalarımızı bu ölçüye göre ayıracağız.

Ana sayfadaki bilgiler kısmını ve footer bölümünün yapısını da biraz değiştirmemiz gerekiyor. Sayfalarda altın oranın (1/1.618) dışındaki her türlü asimetrik görüntü gözü çok yorar. Bir ipucu olarak dikkat ederseniz Twitter dahil bir çok sayfa, bölümlerini bu orana göre boyutlandırır. Siz de tasarımlarınızda bu oranı kullanabilirsiniz.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/goldenratio-640.jpeg"><img class="alignleft size-full wp-image-367" title="goldenratio-640" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/goldenratio-640.jpeg" height="396" width="628" /></a>

Biz bilgiler ve footer öğrelerimize geri dönelim. Daha önce yaptığımız bilgiler kutularında 10 piksel padding (iç boşluk) kullanmazsak yazılarımız kutunun kenarına yapışıyordu. Padding kullandığımızda da 4 birim 4 birim 4 birim boyutlandırdığımız kutulardan biri alt satıra düşüyordu. Bu yüzden kutuları 4 birim 3 birim 4 birim olarak boyutlandırmışız. Bu da güzel olmayan asimetrik bir görüntü oluşturmuş. Buna karşı yapmamız gerekn şey şu. Diyelim ki elimizde bir kutumuz var ve boyunun büyümeden içe doğru boşluklanmasını istiyoruz.
<pre><code>
&lt;div class="row"&gt;
    &lt;div id="kutu-1" class="span6"&gt;
    &lt;/div&gt;
    &lt;div id="kutu-2" class="span6"&gt;
    &lt;/div&gt;
&lt;/div&gt;
</code></pre>
Eğer bu haliyle kutulara padding uygularsak ikinci kutu aşağı satıra düşer. Bunun için şöyle bir yol izlememiz gerekiyor.
<pre><code>
&lt;div class="row"&gt;
    &lt;div class="span6"&gt;
        &lt;div class="bosluklu"&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="span6"&gt;
        &lt;div class="bosluklu"&gt;
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;
</code></pre>
Biçimlendirmeyi de şu şekilde yapmalıyız:
<pre><code>
.bosluklu
{
    padding: 10px;
}
</code></pre>
Bunu bu şekilde yaparsak kutularımız aşağı satıra düşmez. Burada anlamanızı istediğim bir mantık var. Twitter bootstrap kütüphanesi aslında bizim görünümle ilgisi olmayan ve bilgiyi temsil eden class veya id özelliklerimizi ayrı tutmamızı istiyor. Bu çok akıllıca ve doğru bir yaklaşım. Diğer projelerimizde de bilgiyi ve sunumu birbirinden ayrı tutma ilkesini kullanmamız lazım. Bu sayede farklı platformlarda, farklı şekillerde sunacağımız bilginin kaybını ve sunumun hasarlı olmasının da önüne geçmiş oluyoruz. Özellikle daha sonra açıklayacağımız MVC (model-view-controller) mantığında bu kavramı anlamak çok gerekli.

Şimdi kendi sayfamıza dönelim. Anasayfadaki bilgilerimiz şu şekildeydi.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-9.19.41-PM.png"><img class="size-medium wp-image-368 alignnone" title="Screen Shot 2012-10-23 at 9.19.41 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-9.19.41-PM.png?w=300" height="91" width="300" /></a>

Footer (altbilgi) kısmımız da şu şekilde:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-9.19.47-PM.png"><img class="size-medium wp-image-369 alignnone" title="Screen Shot 2012-10-23 at 9.19.47 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-9.19.47-PM.png?w=300" height="84" width="300" /></a>

Sayfamızın kodlarını biraz değiştirdik. Nereleri değiştirmişiz bunun için gtihub'a bir göz atalım. Git hakkında bilginiz yoksa, ekte yer alan "Github kullanımı" konusundaki makaleleri okumanızı tavsiye ederim. Özellikle uzun süre çalıştığımız kodlarda yaptığımız değişikliklerin kaydını tutması açısından Git mükemmel bir araç. Burada - sildiğimiz satırları, + ise eklediğimiz satırları gösteriyor. CSS dosyasında yaptığımız değişiklikleri şu şekilde verdi:
<pre><code>
 #bilgiler &gt; article
 {
-    padding: 10px;
-    border: 1px solid #e8e8e8;
     border-radius: 5px;
     -webkit-border-radius: 5px;
     -moz-border-radius: 5px;
@@ -38,22 +36,35 @@ min-height: 300px !important;
     height:242px;
 }

-#bilgiler
+.footerbox
 {
-    padding-bottom: 20px;
-    padding-top: 20px;
+    margin-top:20px;
+    margin-bottom:20px;
+    border-radius: 5px;
+    -webkit-border-radius: 5px;
+    -moz-border-radius: 5px;
+    background: #1b1b1b;
+    min-height:200px;
 }

-footer
+.kutuyazisi {
+	padding: 5px 15px
+}
+
+#bilgiler
 {
-    margin-top:20px;
+    padding-bottom: 10px;
+    padding-top: 20px;
 }

-#footer-content
+footer
 {
+    position:absolute;
+    top:900px;
+    overflow: auto;
     background: #252525;
     color: #999;
-    padding:10px;
+    margin-top:10px;
 }

 footer h4
@@ -71,11 +82,10 @@ footer a
     list-style:none;
 }

-#footer-floor {
+.footer-floor {
     color: #999;
-    background: #1b1b1b;
     padding: 10px;
-    text-align:right;
+    text-align:center;
 }
</code></pre>
Yaptığımız işlemlere şimdi sırayla bakalım:
<ol>
	<li>Bilgiler içindeki article etiketlerinden boşluğu kaldırmışız</li>
	<li>footerbox adında yeni bir etiket oluşturmuşuz. Onun da alt ve üstündeki boşlukları kaldırmışız.</li>
	<li>Yukarıda belirttiğimiz gibi kutuyazısı adında bir içerik sınıfı oluşturmuşuz ve kutuları onunla tanımlamışız.</li>
	<li>bilgiler id'sine sahip etiketlerden de boşlukları kaldırmışız.</li>
	<li>Footer etiketlerimizin yerini position: absolute; özelliği ile sabitlemişiz. Bu yeni bir özellik. Position özelliği bize öğelerimizin yerini belirli koşullara göre belirlememizi sağlayan bir araç. Bunun diğer özelliklerini ve kullanımlarını araştırmayı size bırakıyorum.</li>
	<li>Footer etiketimizin üstünde sınır boşluğu olarak 10 piksel belirlemişiz. Sayfalarımızda öğeler arasındaki boşlukların sabit olmasına özen göstermemiz, profesyonel bir görüntü elde etmemiz açısından çok önemli. Biz sayfamızda öğeler arasındaki boşlukları 20 px olarak belirlemişiz. Peki neden burada 10px kullandık? Çünkü css koduna göz atarsanız üst taraftaki bilgiler öğesinin alt kısmında da 10 piksellik boşluk bıraktığımızı görürsünüz. Bu iki öğe arasına gelecek hayali sınır çizgisinin de simetrik olmasını sağlıyor.</li>
	<li>En alttaki her hakkı saklıdır bilgilerini içeren footer-floor etiketinin arka plan renklerini değiştirmişiz. Aslında footer içinde yer alan kutuları koyu gri, footer'in kendisini de gri yaptık. Siz de kendiniz istediğiniz gibi bir renk paleti kullanabilirsiniz.</li>
</ol>
Aslında ben tasarım olarak sadelikten yanayım. Bu konuda Micrsoft tarafından sunulan Metro UI tasarım yaklaşımını da araştırmanızı tavsiye ederim. Burada öğelerin kullanımını açıkladığımızdan biz o şekilde sade bir tasarım dili kullanamıyoruz. Ancak projelerinizde sadeliğe önem vermeniz hem erişilebilirlik hem de performans açısından çok düzgün bir yaklaşım olacaktır.

HTML kodumuzda yaptığımız değişikliklere de göz atalım ve yaptığımız iyileştirmeleri tek tek açıklayalım:
<pre><code>@@ -15,7 +15,7 @@
                 &lt;div id="logo" class="span1"&gt;
                     &lt;img src="img/logo.jpg" alt="Logo" /&gt;
                 &lt;/div&gt;
-                &lt;hgroup class="span2"&gt;
+                &lt;hgroup class="span3"&gt;
                     &lt;h1&gt;Kızılyıldız&lt;/h1&gt;
                     &lt;h4&gt;Matbaacılık A.Ş.&lt;/h4&gt;
                 &lt;/hgroup&gt;
@@ -23,10 +23,10 @@
             &lt;div id="baglantilar" class="span8 navbar"&gt;
                 &lt;nav class="navbar-inner"&gt;
                     &lt;ul class="nav"&gt;
-                        &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
+                        &lt;li&gt;&lt;a href="index.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                         &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                         &lt;li&gt;&lt;a href="urunler.html"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
-                        &lt;li&gt;&lt;a href="haberler.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
+                        &lt;li&gt;&lt;a href="duyurular.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
                         &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                         &lt;li&gt;&lt;a href="iletisim.html"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
                     &lt;/ul&gt;
@@ -49,52 +49,62 @@
             &lt;/div&gt;
             &lt;div id="bilgiler" class="row"&gt;
                 &lt;article id="neyapiyoruz" class="span4"&gt;
-                    &lt;h3&gt;Ne yapıyoruz?&lt;/h3&gt;
-                    &lt;p&gt;İstanbul'dasınız, davetiye, broşür, poster veya el ilanı'na ihtiyacınız var. Hem de 3 günde. Fiyatı da biraz uygun olsun ama sonuçlar temiz mi olsun? O zaman doğru yere geldiniz.&lt;/p&gt;
+                    &lt;div class="kutuyazisi"&gt;
+                        &lt;h3&gt;Ne yapıyoruz?&lt;/h3&gt;
+                        &lt;p&gt;İstanbul'dasınız, davetiye, broşür, poster veya el ilanı'na ihtiyacınız var. Hem de 3 günde. Fiyatı da biraz uygun olsun ama sonuçlar temiz mi olsun? O zaman doğru yere geldiniz.&lt;/p&gt;
+                    &lt;/div&gt;
                 &lt;/article&gt;   
-                &lt;article id="neredeyiz" class="span3"&gt;
-                    &lt;h3&gt;Neredeyiz?&lt;/h3&gt;
-                    &lt;p&gt;İstanbul'un tarihi merkezi Sirkeci'deyiz. Ama mesafeler sorun değil. Siz bize gelemezseniz, biz size geliriz. Siparişim ayağıma gelsin diyorsanız, o da olur. &lt;/p&gt;
+                &lt;article id="neredeyiz" class="span4"&gt;
+                    &lt;div class="kutuyazisi"&gt;
+                        &lt;h3&gt;Neredeyiz?&lt;/h3&gt;
+                        &lt;p&gt;İstanbul'un tarihi merkezi Sirkeci'deyiz. Ama mesafeler sorun değil. Siz bize gelemezseniz, biz size geliriz. Siparişim ayağıma gelsin diyorsanız, o da olur. &lt;/p&gt;
+                    &lt;/div&gt;
                 &lt;/article&gt;  
                 &lt;article id="farkımız" class="span4"&gt;
-                    &lt;h3&gt;Bizim farkımız&lt;/h3&gt;
-                    &lt;p&gt;Kesin kalite garantisine ihtiyacınız varsa, ücretsiz motorsikletli kuryeyle baskı işlerim gönderilsin diyorsanız, fiyatlar uygun olsun ama fazla da gecikmesin 3 gün içinde elimde olsun istiyorsanız, aradığınız yer burası. &lt;/p&gt;
+                    &lt;div class="kutuyazisi"&gt;
+                        &lt;h3&gt;Bizim farkımız&lt;/h3&gt;
+                        &lt;p&gt;Kesin kalite garantisine ihtiyacınız varsa, ücretsiz motorsikletli kuryeyle baskı işlerim gönderilsin diyorsanız, fiyatlar uygun olsun ama fazla da gecikmesin 3 gün içinde elimde olsun istiyorsanız, aradığınız yer burası. &lt;/p&gt;
+                    &lt;/div&gt;
                 &lt;/article&gt;  
             &lt;/div&gt;
         &lt;/section&gt;
         &lt;footer&gt;
-            &lt;div id="footer-content"&gt;
-                &lt;div class="row"&gt;
-                    &lt;nav class="span2 offset3"&gt;
-                        &lt;h4&gt;Bağlantılar&lt;/h4&gt;
-                        &lt;ul id="altListe"&gt;
-                            &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
-                            &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
-                            &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
-                        &lt;/ul&gt;
-                    &lt;/nav&gt;
-                    &lt;div id="iletişim"&gt;
-                        &lt;div id="adres" class="span2"&gt;
-                            &lt;h4&gt;Adres:&lt;/h4&gt;
-                            Kızılyıldız Matbaacılık A.Ş.
-                            Denizler Mah.
-                            Eren Sok. No:68
-                            Sireci, Fatih 34110
-                            İstanbul TÜRKİYE
-                        &lt;/div&gt;
-                        &lt;div id="telefon" class="span2"&gt;
-                            &lt;h4&gt;Telefon&lt;/h4&gt;
-                            Tel: +90 212 444 19 17
-                            Fax: +90 212 444 19 05
-                        &lt;/div&gt;
-                    &lt;/div&gt;
+            &lt;div class="row"&gt;
+            &lt;nav class="span3 offset1"&gt;
+                &lt;div class="kutuyazisi footerbox"&gt;
+                    &lt;h4&gt;Bağlantılar&lt;/h4&gt;
+                    &lt;ul id="altListe"&gt;
+                        &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
+                        &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
+                        &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
+                    &lt;/ul&gt;
+                &lt;/div&gt;
+            &lt;/nav&gt;
+            &lt;div class="span4"&gt;
+                &lt;div class="kutuyazisi footerbox"&gt;
+                    &lt;h4&gt;Adres:&lt;/h4&gt;
+                    Kızılyıldız Matbaacılık A.Ş.
+                    Denizler Mah.
+                    Eren Sok. No:68
+                    Sireci, Fatih 34110
+                    İstanbul TÜRKİYE
+                &lt;/div&gt;
+            &lt;/div&gt;
+            &lt;div class="span3"&gt;
+                &lt;div class="kutuyazisi footerbox"&gt;
+                    &lt;h4&gt;Telefon&lt;/h4&gt;
+                    Tel: +90 212 444 19 17
+                    Fax: +90 212 444 19 05
+                &lt;/div&gt;
+            &lt;/div&gt;
+            &lt;/div&gt;
+            &lt;div class="row"&gt;
+            &lt;div class="span12"&gt;
+                &lt;div class="footer-floor"&gt;
+                    &lt;div id="copyright"&gt;Her Hakkı Saklıdır. 2012 Kızılyıldız Matbaacılık A.Ş.&lt;/div&gt;
                 &lt;/div&gt;
             &lt;/div&gt;
-            &lt;div id="footer-floor"&gt;
-
-                &lt;div id="copyright"&gt;Her Hakkı Saklıdır. 2012 Kızılyıldız Matbaacılık A.Ş.&lt;/div&gt;
             &lt;/div&gt;
-
         &lt;/footer&gt;
     &lt;/div&gt;
     &lt;script src="http://code.jquery.com/jquery-latest.js"&gt;&lt;/script&gt;</code></pre>
<ol>
	<li>İlk iş olarak alt satıra düşme sorununu çözdüğümüzden header bölümünü tekrar toplam 12 birime yükselttik.</li>
	<li>Bağlantı listelerindeki eski dosya isimlerini düzelttik.</li>
	<li>Bilgiler bölümündeki kutularımızı taşmayı önlemek için kutuyazısı sınıfındaki div etiketlerinin içine taşıdık. Böylelikle kutularımızın her birinin boyunu 4 birim olarak eşitledik.</li>
	<li>Yine footer alt bilgi kısmındaki kutuları da kutuyazısı sınıfındaki div etiketlerinin içine taşıdık. Boylarını simetrik görüntü için 3 birim 4 birim 3  birim olarak belirledik. Aslında her birini 4 birim olarak belirleyebilirdik ancak kutlar arasında büyük boşluklar istemediğimiz için böyle birşey yapmadık. Çünkü görsel boşluklar birbiriyle bağlantılı öğelerin anlamsal olarak da birbirlerinden uzaklaşmalarına sebep olurlar.</li>
</ol>
Ana sayfada yaptığımız değişiklikler bu şekilde. Diğer sayfalarda da header ve footer kısımlarını tek tek düzeltmemiz gerekiyor.

Footer ve icerik kısmının son ve güzel halini görelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-10.13.45-AM.png"><img class="alignleft size-full wp-image-383" title="Screen Shot 2012-10-24 at 10.13.45 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-10.13.45-AM.png" height="361" width="628" /></a>

Burada vermek istediğim bir ek bilgi var. PHP gibi server tabanlı teknolojilerin ortaya çıkmasının büyük sebeplerinden bir tanesi de bu binlerce sayfadan oluşan HTML sayfalarında tekrar eden yapısal öğelerin yeniden kullanılmasına include özelliği ile olanak vermesi. Yani düşünün elinizde 100 sayfalık bir site var sadece bir bağlantı listesindeki etiketi değiştirmek istediğinizde 100 defa aynı işlemi yapmanız gerekiyordu. Halbuki tek bir şablon dosyasını header.php ve footer.php şeklinde çağırırsanız bir işlemde tüm sayfaların düzgün görünmesini sağlayabiliyorsunuz. İşte sunucu tabanlı teknolojilerin bir faydası daha. Sadece etkileşimlilik değil aynı zamanda verimlilik de sağlıyor.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-10.15.14-PM.png"><img class="size-full wp-image-370 alignnone" title="Screen Shot 2012-10-24 at 10.15.14 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-10.15.14-PM.png" height="399" width="526" /></a>

Çok fazla yapmamız gereken bir şey kalmadı gibi.
<ol>
	<li>Yanliste içeren sayfalarımızı 4'e 8 birim boyuna getireceğiz.</li>
	<li>Bazılarından row etiketli sınıfları kaldıracağız.</li>
	<li>Footer'ın 900lük top özelliğini kaldırmamız gerekiyor. Uzun sayfalarda footer içeriğin üstüne binebilir. Bunun yerine icerik sınıfındaki section etiketimizin min-height özelliğini 790 piksel yapalım. Bu altbilginin çok yukarıda olduğu kısa sayfalar gösterilmesinin önüne geçecektir.</li>
	<li>Bağlantı listesi yerine nav-tabs özelliği olan sayfalarımızı da aynı 4 ve 8 birim ölçüsüne uygun hale getirmemiz gerekiyor. Bunun için css doyasına .nav-tabs sınıflı etiket özelliği olarak min-height: 280px !important; ekledik.</li>
</ol>
Kodlarımızın son hali için <a href="https://github.com/mtkocak/html5css3egitim">https://github.com/mtkocak/html5css3egitim</a> adresine bakabilirsiniz. (Kitapta kodların tamamı burada yazacak.)

Sayfalarımızın son hallerine de bakalım:

1. Kurumsal Bölümü

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-11.35.26-PM.png"><img class="alignleft size-full wp-image-374" title="Screen Shot 2012-10-24 at 11.35.26 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-11.35.26-PM.png" height="294" width="628" /></a>

2. Ürünler Bölümü:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-11.35.19-PM.png"><img class="alignleft size-full wp-image-375" title="Screen Shot 2012-10-24 at 11.35.19 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-11.35.19-PM.png" height="314" width="628" /></a>

3. İletişim Bölümü:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-11.35.13-PM.png"><img class="alignleft size-full wp-image-376" title="Screen Shot 2012-10-24 at 11.35.13 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-24-at-11.35.13-PM.png" height="297" width="628" /></a>

Gördüğümüz gibi sayfalarımız birbiriyle gayet uyumlu. Uyuma bu kadar çok önem vermemizin bir diğer sebebi de, sayfalar arası geçiş olduğu zaman gözün fazla değişikliğe maruz kalmaması. Yani kullanıcının yeni bilgileri algılaması için geçecek süreyi bir de yeni sayfa yapılarını anlamasına uğraşarak harcamasını istemiyoruz. Sonuçta elimizde çok kısıtlı (en fazla 18 saniye) bir algı ve dikkat süresi var. Bunu da iyi kullanmamız gerekiyor.

Websitemiz bitti. Hayırlı olsun. Eğer buraya kadar eksiksiz bir şekilde örnekleri yaptıysanız, artık internet sitesi yapmayı öğrendiniz demektir. Önemli bir konu ise öğrenecek şeylerin hiçbir zaman bitmediği. Her zaman yeni şeyler öğrenmeye azimli ve hevesli olmak bu işte başarılı olmanın anahtarıdır. Eğer bu ilkeyi korursanız ve öğrenmeyi, kendinizi geliştirmeyi severseniz, mesleğiniz de size bunun karşılığını verecektir. Bir sonraki yazıda FTP kullanarak yayınlamayı anlatacağım.

Dayanışmayla!
Meraklı Bilişimci