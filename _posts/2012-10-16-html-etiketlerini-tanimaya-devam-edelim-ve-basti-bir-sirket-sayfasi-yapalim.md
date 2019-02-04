---
ID: 161
post_title: >
  HTML etiketlerini tanımaya devam edelim
  ve basit bir şirket sayfası yapalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/html-etiketlerini-tanimaya-devam-edelim-ve-basti-bir-sirket-sayfasi-yapalim/
published: true
post_date: 2012-10-16 19:23:21
---
Daha önceden PHP'nin sunucu üzerinde çalıştığından bahsetmiştik. PHP'nin en güzel avantajlarından bir tanesi, kullanıcıdan aldığı bilgiyi işleyebilmesi. Burada PHP'nin icat edilme amacı da ortaya çıkıyor. PHP'nin HTML'den en büyük farkı, HTML statik yani, basılı kağıt gibi tek taraflı bilgiyi sunmaya yarayan bir teknoloji olması. Mesela bir siteye kayıt olmak, bir fotoğraf paylaşmak, tweet atmak gibi etkileşimli işleri yaparken ise PHP gibi sunucu tarafında çalışan bir programa ihtiyacımız var.

Ama önce gelin HTML etiketlerini tanımaya devam edelim. İlk önce öğrenmemiz gereken en önemli etiket &lt;div&gt; etiketi.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/div.jpg"><img class="alignnone size-full wp-image-163" style="border:1px solid gray;" title="div" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/div.jpg" height="149" width="264" /></a>

Div etiketi HTML sayfaları yaratırken kullanacağımız bir ingiliz anahtarı gibi. İngilizce "division" yani <strong>"bölüm"</strong> anlamına geliyor. Şimdi tipik bir html sayfasını düşünelim. En basit şekilde sayfamızda olması gerekenler neler, onları sırayla görelim. Mesela şirketimiz için bir sayfa yapmak istediğimizi hayal edelim. 2013 itibariyle tüm şirketler için zorunlu değil mi? Sayfamızda neler olmalı, şöyle bir bakalım:
<ol>
	<li>Şirketimizin adı</li>
	<li>Adresi (iletişim bilgileri) (Bize ulaşın)</li>
	<li>Ürün veya Servislerimiz</li>
	<li>Haberler, Duyurular, İlanlar</li>
	<li>Hakkımızda</li>
	<li>Kurumsal bilgiler (Mesela artık yeni yasaya göre finansal tabloların da buraya eklenmesi gerekiyor değil mi?)</li>
</ol>
Düşüncemizi biraz daha geliştirelim. En basitten adım adım ilerleyeceğiz. Her şirket veya organizasyonun bir logo'su da olması gerekir. Düşünmeye devam edelim. Sayfamızı hazırladıktan sonra Google gibi arama motorlarının bize ulaşmaları için anahtar kelimelere de ihtiyacımız var. Burada bir konuya değinmek istiyorum. Piyasada <strong>SEO</strong> adı altında faaliyet gösteren birçok şirket var. Bu şirketler websitenizi Google'da üst sıralara taşıma garantisi veriyorlar. İşini iyi yapan firmalar var mıdır bilmiyorum, ancak bazı firmalar, kendi kurdukları diğer sitelerden sizin sitenize sahte link vererek Google'ın algoritmasını aldatma yoluna gidiyorlar. İlk zamanlar siteniz gerçekten üst sıralara yükseliyor. Ancak Google bunu farkettiği anda siteniz aşşağı sıralara düşüyor ve ödediğiniz para da boşa gidiyor. Benim bu konudaki birkaç tavsiyem olacak. Eğer Google gibi arama motorlarında hakettiğiniz sırayı almak istiyorsanız, herşeyden önce;
<ol>
	<li><strong>Asla flash kullanmayın.</strong> Google flash ile kodlanan sayfaları indexlemiyor.</li>
	<li>Sitenizde giriş sayfası, <strong>hoşgeldin videosu</strong>, müzik gibi şeyler kullanmayın. Arama motorlarının da internet kullanıcılarının da bunlar için vakti çok kısıtlı.</li>
	<li>En önemlisi <strong>doğru anahtar kelimeler</strong> kullanın. Her anahtar kelimeyi eklemeyin. Sadece ilgili olanları cimrice kullanın.</li>
	<li>Bir de kodunuz temiz olsun. Yani açılan tüm etiketler kapanmış, javascript kullanıyorsanız <strong>hatasız</strong> ve test edilmiş olsun.</li>
	<li><strong>Aşırı büyük boyutlu</strong> grafikler, dosyalar kullanmayın. Bunlar hem sitenizin okunurluğunu erişilebilirliğini azaltır hem de yüklenme süresini artırarak hem arama motorlarını hem de kullanıcıları kaçırır. Bir sayfa en fazla <strong>1 saniyede</strong> yüklenmeli.</li>
	<li>Bir de paranızı her <strong>SEO'cuyum</strong> diyene kaptırmayın :)</li>
</ol>
Şimdilik görünümü bir tarafa bırakalım. Buna CSS kısmında tekrar geri döneceğiz. Şirketimizin adı: Kızılyıldız Matbaacılık A.Ş. olsun. Logo'su da belli :) Basit olması açısından ürünlerimiz de Davetiye, Ajanda, Poster ve El ilanı olsun.

Ana sayfamızı yaparak işe başlayalım.
<pre><code>&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
      &lt;!-- Buraya içeriklerimizi ekleyeceğiz --&gt;
  &lt;/body&gt;
&lt;/html&gt;</code></pre>
Bir şeye dikkat ettiniz mi? Web tarayıcısı &lt;!--  --&gt; karakterlerin arasındaki içeriği görmezden geliyor. Nasıl ki PHP'de yorumları //, /* */ veya # ile yapıyorduk, HTML'de du bu şekilde yapıyoruz.

Şimdi anasayfamızda olmasını istediğimiz bölümlere karar verelim.
<ol>
	<li>Logo</li>
	<li>Şirket Adı</li>
	<li>Adres, Telefon ve E-posta adresi</li>
	<li>Bölümler arasında gezinmemizi sağlayacak bağlantılar</li>
	<li>Şirket hakkında kısa bilgi</li>
</ol>
Şimdi de bu bilgileri nasıl sınıflandıracağımıza karar verelim, neyse ki genellikle her internet sayfası için olan genel bir şablon var. Şöyle ki;
<ol>
	<li>Tüm sayfalarda aynı olacak bir baş ksım olmalı. Sonuçta logo, iletişim bilgileri ve sayfalar arasındaki bağlantılar her sayfada aynı olacak. (header)</li>
	<li>Her sayfadaki farklı içeriği ekleyeceğimiz bir içerik kısmı olmalı. (content)</li>
	<li>En sonda da sayfanın en altında yer alacak, yine her sayfada aynı olacak, en son olarak vermek istediğimiz bilgileri yazacağımız bir bölüm olmalı. Burada da bazı bağlantılar, kullanım kuralları, gizlilik sözleşmesi, copyright gibi bilgiler olur. Buna da altbilgi diyoruz. (footer)</li>
</ol>
Ana sayfada şirketimiz hakkında kısa bir bilgi verelim. Görünür bir yerde adres ve telefonlarımız olsun ki en çabuk erişilen bilgi bu olsun. Yukarıda saydığımız bölümlere de gitmemiz gerekiyor ayrıca. Bunun için bağlantılarımızı da ekleyeceğiz.

Şimdi gelelim sihirli etiketimizi kullanmaya. Tüm bu bölümler için &lt;div&gt; etiketini kullanabiliriz. &lt;div&gt; etiketinin name ve id özelliklerini değiştireceğiz ve onlara isim vererek bölümlerimizi oluşturacağız.
<pre><code>&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
      &lt;div id="sayfa"&gt;
          &lt;div name="ustbilgi"&gt;
              &lt;div name="logo"&gt;&lt;/div&gt;
              &lt;h1&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/h1&gt;
              &lt;div name="baglantilar"&gt;&lt;/div&gt;
          &lt;/div&gt;
          &lt;div name="adres"&gt;&lt;/div&gt;
          &lt;div name="icerik"&gt;
          &lt;/div&gt;
          &lt;div name="altbilgi"&gt;
          &lt;/div&gt;
      &lt;/div&gt;
  &lt;/body&gt;
&lt;/html&gt;</code></pre>
Aşağı yukarı yapımızı oluşturduk gibi. Şimdi içlerini doldurmaya başlayacağız. Öncelikle meta yani ekbilgilerle işe başlayalım. Bildiğimiz gibi arama motorlarının sitemizi tanıması için anahtar kelimelere ihtiyacımız vardı. Bu kelimeleri cimrice seçmemiz gerekiyordu. 10-15 tane yeterli. Gelelim bunları tek tek seçmeye.

Anahtar kelimelerimiz:
<ul>
	<li>Kızılyıldız</li>
	<li>kızıl</li>
	<li>yıldız</li>
	<li>Matbaa</li>
	<li>Baskı</li>
	<li>Ajanda</li>
	<li>Davetiye</li>
	<li>Poster</li>
	<li>İlan</li>
	<li>İstanbul</li>
	<li>Sirkeci</li>
</ul>
Olsun. Gelelim bunları sitemize yerleştirmeye. Dediğimiz gibi bunlar head etiketinin içinde yer alacak. Bir diğer üstbilgi de sitemiz hakkında kısa bir açıklama olsun. Hani arama motorlarının altında çıkan yazılardan. Bunlar da çok uzun olmasın, zaten Google kesiyor.
<blockquote>"Kızılyıldız İstanbul, Sirkeci'de faaliyet göstermekte olan tasarıma önem veren yenilikçi matbaa şirketi. Başlıca ürünlerimiz: Davetiye, Ajanda, Poster ve El ilanı"</blockquote>
Şimdi sıra geldi bunları birleştirmeye.
<pre><code>
&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8" /&gt;
&lt;meta name="description" content="Kızılyıldız İstanbul, Sirkeci'de faaliyet göstermekte olan tasarıma önem veren yenilikçi matbaa şirketi. Başlıca ürünlerimiz: Davetiye, Ajanda, Poster ve El ilanı"/&gt;
&lt;meta name="keywords" content="kızılyıldız, kızıl, yıldız, matbaa, baskı, ajanda, davetiye, poster, ilan, istanbul, sirkeci"/&gt;</code></pre>
İlk önce tanımladığımız etiket, tarayıcıya belgemizin türünün ne olduğunu söylüyor, burada html şeklinde metin göndereceğimizi ve türkçe karakterlerimizi "UTF-8" ile kodlayacağımızı belirttik. Daha önce bazı php örneklerimizde Türkçe karakterlerimiz bozuk çıkmıştı hatırlarsanız. İşte bu etiket sayesinde, Türkçe karakter sorununu oratadan kaldırıyoruz. Ben genellikle karakterlerde UTF-8 tercih ediyorum. Evrensel ve genel bir kodlama standardı. Siz de bunu tercih ederseniz karakter konusunda sorun yaşamazsınız.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/google-23-nisan-logosu.jpeg"><img class="alignnone size-full wp-image-170" title="Google-23-Nisan-Logosu" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/google-23-nisan-logosu.jpeg" height="236" width="429" /></a>

Dikkat edersek meta etiketlerini kapatmadık ve bunun yerine /&gt; gibi bir ifade kullandık. Bazı etiketlerde mantıken böyle bir kullanım mevcut. Herhangi bir bilgiyi sarıp sarmalamayan etiketlerde bu yöntemi kullanıyoruz.

Anahtar kelimelerimiz ve açıklamamızı halletikten sonra üs bilgide yer alan diğer bir etiketi inceleyelim
&lt;h1&gt;etiketi başlık anlamına gelir, başlıkların büyüklüğüne göre h1, h2, h3, h4, h5, h6 ya kadar başlık ekleyebilmemize olanak sağlar.
Şu ana kadar sayfamızın tarayıcıyla ve arama motorlarıyla güzel güzel anlaşmasını sağladık. Bundan sonra da içeriklerimizi eklemeye devam edeceğiz.

Dayanışmayla!
Merakli Bilişimci