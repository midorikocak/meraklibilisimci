---
ID: 194
post_title: >
  Sayfamıza içeriklerimizi eklemeye
  başlayalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/sayfamiza-iceriklerimizi-eklemeye-baslayalim/
published: true
post_date: 2012-10-17 17:44:02
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/logo.jpg"><img class="alignnone size-thumbnail wp-image-196" title="logo" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/logo.jpg?w=150" height="142" width="150" /></a>

Öncelikle elimizde logo.jpg adında bir logomuz var. Logomuzu nasıl ekleyeceğiz? Sayfalarda resimleri eklemek için kullandığımız etiket &lt;img&gt; etiketi. Burada da &lt;img src="logo.jpg" alt="Logo"&gt; olarak kullanacağız. Bu etikette genişlik ve yüksekliğini de ayarlayabiliriz ama şimdilik gerek yok. Peki alt özelliği nedir? Alt yani alternatif, eğer resim yüklenmezse yerinde görünmesini istediğimiz yazıdır, önlem olarak bunu hep kullanmamız gerekiyor.

Sitemizin başlığını seçelim. Başlıklarda h1 kullanıyorduk hatırlarsanız.

Devam edelim. Bölümlerimiz arasında gezinmemiz için bağlantı listesine ihtiyacımız var demiştik. Linklerimiz burada olacak. Peki HTML Sayfasında bağlantılar nasıl tutuluyor? Nasıl bir link yaratıyoruz? Bunun için de kullandığımız etiket &lt;a&gt; örneğin sayfamızdan link vermek istediğimizi düşünelim. Şöyle yapacağız:

&lt;a href="http://www.meraklibilsimci.com"&gt;Meraklı Bilişimci&lt;/a&gt;

Şimdi de bölümlerimize geri dönelim ve liste hazırlamaya başlayalım:
<pre><code>
&lt;ul&gt;
    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="urunler.html"&gt;Ürünlerimiz&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="haberler.html"&gt;Duyurular&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="iletisim.html"&gt;İletişim&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
</code></pre>
İpucu: Burada ul, unordered yani numarasız liste anlamına geliyor. Numaralı olmasını isteseydik ol etiketini kullanmamız gerekiyordu.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-17-at-8.37.30-PM.png"><img class="size-full wp-image-199 alignnone" title="Screen Shot 2012-10-17 at 8.37.30 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-17-at-8.37.30-PM.png" height="124" width="132" /></a>

Linklerimiz de hazır. Başka neye ihtiyacımız vardı? İletişim bilgilerimizin her yerden ulaşılır olmasını istiyorduk. Bunu da şu şekilde yapalım:
<pre><code>&lt;div name="iletişim"&gt;
    &lt;div name="telefon"&gt;
        Tel: +90 212 444 19 17
        Fax: +90 212 444 19 05
    &lt;/div&gt;
&lt;/div&gt;
</code></pre>
İletişim bilgilerimiz de hazır.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-17-at-8.40.00-PM.png"><img class="alignnone size-full wp-image-200" title="Screen Shot 2012-10-17 at 8.40.00 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-17-at-8.40.00-PM.png" height="21" width="335" /></a>

Ana sayfada 3 tane bölümümüz olsun. Sayfamızı yaparken ziyaretçimizin gözüyle bakmamız gerekiyor. Ben genellikle misyon, vizyon gibi küçük şirketler için anlamsız kurumsal bıdı bıdılara karşıyım. Sonuçta baskı yaptırmak istiyorum, bunu hızlı ve uygun bir fiyata yaptırmak istiyorum ve kaliteli bir sonuç istiyorum. İlk 10 saniyede bunlara ulaşamazsam giderim. İşte böyle acımasız internet kullanıcısı, her şey hızlı ve sizin o şirin intro videonuzu izlemeye vakti yok.
<pre><code>&lt;div name="icerik"&gt;
    &lt;div name="mesaj"&gt;
        &lt;h1&gt;&lt;strong&gt;İstanbul'daki en hızlı, en kaliteli ve en uygun fiyatlı matbaayı mı arıyorsunuz?&lt;/strong&gt;&lt;/h1&gt;
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
</code></pre>
İçeriklerimizi ve kısa bilgilerimizi de hallettik.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-17-at-8.37.48-pm1.png"><img class=" wp-image-202 alignnone" style="border:1px solid gray;" title="Screen Shot 2012-10-17 at 8.37.48 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-17-at-8.37.48-pm1.png?w=239" height="300" width="239" /></a>

Geldik alt bilgiye. Alt bilgide de navigasyona ve birkaç kısa bilgiye ihtiyacımız var. Örneğin gizlilik bildirimi, copyright, sıkça sorulan sorular, bu sayfayı kim yaptı veya başka göz önünde olmasını o kadar çok istemediğimiz bilgiler burada olmalı. Şimdilik gizlilik bildirimine ihtiyacımız yok ama bunun yerine adres bilgilerimizi ve bağlantı listemizden bir kısmını buraya ekleyebiliriz.
<pre><code>&lt;div name="altbilgi"&gt;
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
</code></pre>
Ana sayfamızdaki tüm bilgileri halettik.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-17-at-8.38.07-PM.png"><img class="size-full wp-image-203 alignnone" style="border:1px solid gray;" title="Screen Shot 2012-10-17 at 8.38.07 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-17-at-8.38.07-PM.png" height="159" width="382" /></a>

Bir sonraki yazıda da bunları birleştireceğiz.

Dayanışmayla!
Meraklı Bilişimci