---
ID: 320
post_title: Duyurular bölümünü bitirelim (blog)
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/duyurular-bolumunu-bitirelim-blog/
published: true
post_date: 2012-10-23 04:29:04
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screenshot.png"><img class="alignnone size-full wp-image-321" title="screenshot" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screenshot.png" height="225" width="300" /></a>

Duyurular bölümünü tıpkı daha önce hakkımızda bölümünde yaptığımız gibi section ve article olarak kuracağız. Fakat burada fark şu olacak. Duyurular bölümünü tıpkı bir blog gibi oluşturacağız. Herhangi bir navigasyon olmasına gerek yok. Aşağıya doğru kaydırdıkça makaleleri görebileceğiz. İstersek sadece liste gibi veya makale özeti koyup devamını gör linkini de koyabiliriz ama gerek yok. Bunun yerine biz tıpkı bir wordpress blogu gibi makaleleri koyacağız.

Hakkımızda bölümünün ilk halini hatırlıyorsunuz değil mi? Duyurular bölümü de aşağı yukarı ona benzeyecek.

Peki yapımızı nasıl belirleyeceğiz? Bunun için <a href="http://www.schema.org">Schema.org</a>'a göz atarak şöyle bir yapı oluşturuyoruz.
<pre><code>
&lt;article name="blogpost" itemscope="" itemtype="http://schema.org/BlogPosting"&gt;
    &lt;header&gt;
        &lt;a name="makale"&gt;&lt;h2 itemprop="name headline"&gt;Makale Başlığı&lt;/h2&gt;&lt;/a&gt;
        &lt;time datetime="2012-10-18" itemprop="datePublished"&gt;18 Ekim 2012&lt;/time&gt; tarihinde yayınlandı.
    &lt;/header&gt;
    &lt;div itemprop="articleBody"&gt;
        &lt;p&gt;
            Makale İçeriği
        &lt;/p&gt;
    &lt;/div&gt;
&lt;/div&gt;
</code></pre>
İtemtype özelliği olarak blogpost kullandığımıza dikkat edin. Bir kaç tane duyuru hazırlayalım. Bu duyuru makalelerimizde resim de kullanmış olalım.
<pre><code>
&lt;div class="span8"&gt;
    &lt;article itemscope itemtype="http://schema.org/BlogPosting"&gt;
        &lt;header&gt;
            &lt;a id="yonetimkurulu"&gt;&lt;h3 itemprop="name headline"&gt;Yönetim Kurulu Seçimleri gerçekleşti&lt;/h3&gt;&lt;/a&gt;
            &lt;time datetime="2012-10-18" itemprop="datePublished"&gt;18 Ekim 2012&lt;/time&gt; tarihinde yayınlandı.
        &lt;/header&gt;
        &lt;div itemprop="articleBody"&gt;
            &lt;img title="toplanti" alt="Olağan Genel Kurul Toplantısı" src="img/toplanti.jpg" /&gt;
            &lt;p&gt;Şirketimiz bünyesinde 17 Ekim 2012 Günü gerçekleşen genel kurul toplantısı Yönetim Kurulunun ivedilikle seçilmesi gündemiyle, saat 13:00'da toplandı. Yapılan oylama sonucunda şirketimiz yönetim kuruluna seçilenlerin listesi aşağıdaki gibidir.
            &lt;/p&gt;
            &lt;ul&gt;
                &lt;li&gt;Yön. Kur. Bşk. Fipob Hibnot&lt;/li&gt;
                &lt;li&gt;Yön. Kur. Bşk. Yrd. Jatizop Opep&lt;/li&gt;
                &lt;li&gt;Yön. Kur. Üy. Zatag Etmep&lt;/li&gt;
                &lt;li&gt;Yön. Kur. Üy. Isfem Isip&lt;/li&gt;
                &lt;li&gt;Yön. Kur. Üy. Amet Cesfeldo&lt;/li&gt;
                &lt;li&gt;Yön. Kur. Üy. Nejos Dezep&lt;/li&gt;
                &lt;li&gt;Den. Kur. Üy. Ocsejon Lezrelleze&lt;/li&gt;
                &lt;li&gt;Den. Kur. Üy. Natvege Vezmep Ubhas&lt;/li&gt;
                &lt;li&gt;Den. Kur. Üy. Topep Dinhom&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/div&gt;
    &lt;/article&gt;
    &lt;article itemscope itemtype="http://schema.org/BlogPosting"&gt;
        &lt;header&gt;
            &lt;a id="finansal"&gt;&lt;h3 itemprop="name headline"&gt;Finansal Tabloların Müzekere Edilmesi Ertelendi&lt;/h3&gt;&lt;/a&gt;
            &lt;time datetime="2012-10-18" itemprop="datePublished"&gt;15 Ekim 2012&lt;/time&gt; tarihinde yayınlandı.
        &lt;/header&gt;
        &lt;div itemprop="articleBody"&gt;
            &lt;img title="finansal" alt="Finansal Tabloların Müzekere Edilmesi Ertelendi " src="img/finansal.jpg" /&gt;
            &lt;p&gt;
                Pay sahiplerinin isteği üzerine finansal tabloların incelenmesi toplantı başkanının kararıyla 15 Kasım 2012 Tarihine ertelenmiştir. Tüm ilgililere saygıyla duyurulur.
            &lt;/p&gt;
            &lt;p&gt;Kızılyıldız Matbaacılık A.Ş. Yönetim Kurulu&lt;/p&gt;
        &lt;/div&gt;
    &lt;/article&gt;
    &lt;article itemscope itemtype="http://schema.org/BlogPosting"&gt;
        &lt;header&gt;
            &lt;a id="tutanak"&gt;&lt;h3 itemprop="name headline"&gt;2012 Ekim Ayındaki Genel Kurul Toplantısı Tutanağı ilan edilmiştir.&lt;/h3&gt;&lt;/a&gt;
            &lt;time datetime="2012-10-18" itemprop="datePublished"&gt;18 Ekim 2012&lt;/time&gt; tarihinde yayınlandı.
        &lt;/header&gt;
        &lt;div itemprop="articleBody"&gt;
            &lt;img title="tutanak" alt="2012 Ekim Ayındaki Genel Kurul Toplantısı Tutanağı ilan edilmiştir." src="img/tutanak.jpg" /&gt;
            &lt;p&gt;
                17 Ekim 2012 günü saat saygıdeğer Genel Kurul Üyelerinin katılımıyla saat 13:00'te gerçekleştirilen Genel Kurul Toplantısına ilişkin toplantı tutanakları ilan edilmiştir. Toplantı tutanaklarına ekte yer alan pdf dosyasından erişilebilir. Tüm ilgililere saygıyla duyurulur.
            &lt;/p&gt;
            &lt;p&gt;Kızılyıldız Matbaacılık A.Ş. Yönetim Kurulu&lt;/p&gt;
        &lt;/div&gt;
    &lt;/article&gt;
&lt;/div&gt;
</code></pre>
Blog bölümümüzü de bitirdik. Şimdi bölümün son haline bakalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-7.26.41-AM.png"><img class="alignright size-full wp-image-322" title="Screen Shot 2012-10-23 at 7.26.41 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-7.26.41-AM.png" height="385" width="628" /></a>

Bir sonraki yazıda son olarak kurumsal bölümümüzü yapacağız.

Dayanışmayla!
Meraklı Bilişimci