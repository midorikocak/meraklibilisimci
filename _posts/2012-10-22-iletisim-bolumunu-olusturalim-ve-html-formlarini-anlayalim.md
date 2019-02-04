---
ID: 289
post_title: >
  İletişim bölümünü oluşturalım ve
  HTML formlarını anlayalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/iletisim-bolumunu-olusturalim-ve-html-formlarini-anlayalim/
published: true
post_date: 2012-10-22 07:22:04
---
Tek ürün gösteren veya sipariş vermeyi sağlayan sayfayı yapmadan önce, saitemizin belki de en önemli bölümü olan iletişim bölümümüzü yapmamız gerekiyor.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-12.24.28-AM.png"><img class="alignnone size-medium wp-image-290" title="Screen Shot 2012-10-22 at 12.24.28 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-12.24.28-AM.png?w=292" height="300" width="292" /></a>

İletişim bölümü sitemizin en önemli bölümüdür. Genellikle firmaların internet sitelerine giren insanlar sadece bu bölüm için sayfayı açarlar. Aradıkları şey genellikle telefon numarası, adres, e-posta veya daha da önemlisi mesajlarını direk yollayabilecekleri bir iletişim formudur.

[gallery link="file" columns="4" orderby="ID"]

Bu bölümü oluşturmak için ihtiyacımız olan bilgiler neler?
<ol>
	<li>Adres</li>
	<li>Telefon</li>
	<li>E-posta adresleri</li>
	<li>İletişim Formu</li>
</ol>
İletişim formunda ihtiyacımız olan nedir?
<ul>
	<li>Gönderen kişinin adı, soyadı</li>
	<li>Geri dönüş yapmak için e-posta adresi</li>
	<li>Gönderilecek mesaj</li>
</ul>
İletişim ile ilgili bilgileri vereceğiz. Burada çok önemli bir noktaya geldik. Meta etiketleri bölümünde belirttiğimiz anahtar kelimeler Google veya diğer arama motorları tarafından o kadar da dikkate alınmıyor. Şaşırdınız değil mi? Maalesef öyle. Meta description yani açıklama dikkate alınıyor, ama anahtar kelimelere ne kadar önem addedildiği meçhul. Google kullanmadığını söylüyor, ya da çok suistimal edildiği için böyle bilinmesini istiyor.

Peki biz internet sitemizdeki bilgiyi olduğu gibi Google'a nasıl anlatacağız? İnsan olmadığı, bir makine olduğu için anlamakta zorlanacaktır. Örneğin, neyin adres, neyin firma ismi,neyin yorum olduğunu bilemeycektir.

İşte tam da bunun için yeni bir şey icad edilmiş adı da microdata. Biz iletişim sayfamızdaki adresi bu şekilde ekleyeceğiz. Google da bunun adres olduğunu şıp diye anlayacak. Yazalım;
<pre><code>
&lt;div itemscope itemtype="http://schema.org/LocalBusiness"&gt;
  &lt;span itemprop="name"&gt;&lt;h3&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/h3&gt;&lt;/span&gt;
&lt;h4&gt;İletişim Bilgileri:&lt;/h4&gt;
  &lt;div itemprop="address" itemscope itemtype="http://schema.org/PostalAddress"&gt;
    &lt;h5&gt;Adres:&lt;/h5&gt;
      &lt;p&gt;&lt;span itemprop="streetAddress"&gt; Denizler Mah. Eren Sok. No:68&lt;/span&gt;&lt;br/&gt;
      &lt;span itemprop="addressLocality"&gt;Sireci, Fatih&lt;/span&gt;
      &lt;span itemprop="postalCode"&gt;34110&lt;/span&gt;&lt;br/&gt;
      &lt;span itemprop="addressCountry"&gt;İstanbul, TÜRKİYE&lt;/span&gt;&lt;/p&gt;
  &lt;/div&gt;
    &lt;strong&gt;Tel:&lt;/strong&gt;&lt;span itemprop="telephone"&gt;+90 212 444 19 17&lt;/span&gt;&lt;br/&gt;
    &lt;strong&gt;Fax:&lt;/strong&gt;&lt;span itemprop="faxNumber"&gt;+90 212 444 19 05&lt;/span&gt;&lt;br/&gt;
    &lt;strong&gt;E-mail:&lt;/strong&gt; &lt;span itemprop="email"&gt;iletisim(at)kizilyildizbaski.com.tr&lt;/span&gt;
&lt;/div&gt;
</code></pre>
Burayı çok fazla açıklamaya gerek yok sanırım. Metin içinde verdiğimiz bilgileri, <a href="http://www.schema.org">schema.org</a>'da bulunan bilgi kalıpları içine yerleştirmekle işe başlıyoruz. Daha fazla bilgi için <a href="http://www.schema.org">schema.org</a>'u incelemenizi tavsiye ederim.

Adres bilgisi şu şekilde görünmeli:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-9.11.08-AM.png"><img class="alignnone size-full wp-image-292" title="Screen Shot 2012-10-22 at 9.11.08 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-9.11.08-AM.png" height="251" width="332" /></a>

İşte şu anda bizim görüp anladığımız bilgiyi Google'da anlayacak ve sayfalarında bu bilgiye de yer verecek. Bu ekstra bilgi üstelik bizim sayfamızın arama sonuçlarında daha yukarılarda yeralmasını da sağlayacak.

Sıra geldi formumuzu tasarlamaya. Bunun için ilk iş olarak form etiketiyle işe başlıyoruz.
<pre><code>
&lt;form action="iletisim.html" method="post"&gt;
    &lt;fieldset&gt;
        &lt;legend&gt;Gönderen Bilgisi&lt;/legend&gt;
        &lt;label for=""&gt;Adı Soyadı:&lt;/label&gt;
        &lt;input type="text" id="adSoyad" name="adSoyad" placeholder="Adınız Soyadınız" /&gt;
        &lt;label for=""&gt;E-posta Adresi:&lt;/label&gt;
        &lt;input type="email" id="ePosta" name="ePosta" placeholder="E-posta adresiniz"/&gt;
        &lt;label for=""&gt;Mesaj:&lt;/label&gt;
        &lt;textarea id="formmesaj" name="formmesaj"&gt;Mesajınız&lt;/textarea&gt;&lt;br /&gt;
        &lt;input type="submit" value="Gönder" /&gt;
    &lt;/fieldset&gt;
&lt;/form&gt;
</code></pre>
Formda yaptığımız işlere kısaca bir göz atmakta yarar var:
<ul>
	<li>İlk önce action özelliği ile formumuzun hedefini belirledik. Şu anda değil ama Php'de sunucu tarafında veri işlerken buna ihtiyacımız olacak. Verilerin URL'de ?gonderen=Mutlu+Kocak şeklinde gözükmesini istemediğimiz için de gönderim şeklini post olarak belirledik.</li>
	<li>fieldset ile yeni formumuzun etrafını çizdik, başlık olarak legend etiketini kullandık, buna şimdilik gönderen bilgileri dedik.</li>
	<li>input etiketlerini kullandık. Placeholder özellikleriyle tıklandığı anda yokolan ipucu bilgilerini girdik</li>
	<li>type="email" özelliği ile tarayıcının, girilen bilginin eposta olup olmadığını kontrol etmesini sağladık.</li>
	<li>textarea girdisiyle birden çok satır içerebilen bir form alanı yarattık.</li>
	<li>Submit girdisiyle form gönderme butonunu yarattık ve üzerindeki yazıyı value özelliği ile "Gönder" yaptık.</li>
</ul>
Şimdi sonucu görelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.10.05-AM.png"><img class="alignnone size-full wp-image-300" title="Screen Shot 2012-10-22 at 10.10.05 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.10.05-AM.png" height="327" width="338" /></a>

Tüm bu yaptıklarımızı sayfamızın içine yerleştirelim. Twitter bootstrap kütüphanesi ile daha önce yaptığımız gibi sayfamızı 3 birim e 8 birimlik iki bölüme ayıralım. Birinci kısımda bölüm başlığı, diğer kısımda ise bölüm içeriği olsun. Belki daha sonra bu kısımları section etiketi ile yeniden düzenleyebiliriz.

Kodumuzun son hali şöyle. Yer kaplamaması açısından sadece içerik section etiketinin içeriğini yazıyorum.
<pre><code>
&lt;section id="icerik" class="container"&gt;
    &lt;div id="row"&gt;
        &lt;div class="span3"&gt;&lt;h3&gt;İletişim Bilgileri:&lt;/h3&gt;&lt;/div&gt;
        &lt;div class="span8"&gt;
            &lt;div itemscope itemtype="http://schema.org/LocalBusiness"&gt;
                &lt;span itemprop="name"&gt;&lt;h4&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/h4&gt;&lt;/span&gt;&lt;hr&gt;
                &lt;div itemprop="address" itemscope itemtype="http://schema.org/PostalAddress"&gt;
                    &lt;h5&gt;Adres:&lt;/h5&gt;
                    &lt;p&gt;&lt;span itemprop="streetAddress"&gt; Denizler Mah. Eren Sok. No:68&lt;/span&gt;&lt;br/&gt;
                        &lt;span itemprop="addressLocality"&gt;Sireci, Fatih&lt;/span&gt;
                        &lt;span itemprop="postalCode"&gt;34110&lt;/span&gt;&lt;br/&gt;
                        &lt;span itemprop="addressCountry"&gt;İstanbul, TÜRKİYE&lt;/span&gt;&lt;/p&gt;
                    &lt;/div&gt;
                    &lt;strong&gt;Tel:&lt;/strong&gt;&lt;span itemprop="telephone"&gt;+90 212 444 19 17&lt;/span&gt;&lt;br/&gt;
                    &lt;strong&gt;Fax:&lt;/strong&gt;&lt;span itemprop="faxNumber"&gt;+90 212 444 19 05&lt;/span&gt;&lt;br/&gt;
                    &lt;strong&gt;E-mail:&lt;/strong&gt; &lt;span itemprop="email"&gt;iletisim(at)kizilyildizbaski.com.tr&lt;/span&gt;
                &lt;/div&gt;
                &lt;hr&gt;
            &lt;/div&gt;
            &lt;div class="span3"&gt;&lt;h3&gt;İletişim Formu:&lt;/h3&gt;&lt;/div&gt;
            &lt;div class="span8"&gt;
                &lt;form action="iletisim.html" method="post"&gt;
                    &lt;fieldset&gt;
                        &lt;legend&gt;Gönderen Bilgisi&lt;/legend&gt;
                        &lt;label for=""&gt;Adı Soyadı:&lt;/label&gt;
                        &lt;input type="text" id="adSoyad" name="adSoyad" placeholder="Adınız Soyadınız" /&gt;
                        &lt;label for=""&gt;E-posta Adresi:&lt;/label&gt;
                        &lt;input type="email" id="ePosta" name="ePosta" placeholder="E-posta adresiniz"/&gt;
                        &lt;label for=""&gt;Mesaj:&lt;/label&gt;
                        &lt;textarea id="formmesaj" name="formmesaj"&gt;Mesajınız&lt;/textarea&gt;&lt;br /&gt;
                        &lt;input type="submit" value="Gönder" /&gt;
                    &lt;/fieldset&gt;
                &lt;/form&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/section&gt;
</code></pre>
Sayfamız da şu şekilde:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.19.38-AM.png"><img class="alignnone size-full wp-image-301" title="Screen Shot 2012-10-22 at 10.19.38 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-22-at-10.19.38-AM.png" height="643" width="628" /></a>

Müşteriye adres veya iletşim formu ararken saç baş yoldurmayacak, gayet kullanışlı ve estetik bir sayfa oldu. Şimdilik bu kadar. Daha sonraki yazılarda diğer bölümlerle devam edeceğiz.

Dayanışmayla!
Meraklı Bilişimci