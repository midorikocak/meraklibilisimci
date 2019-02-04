---
ID: 324
post_title: 'Yeni Türk Tücaret Kanunu&#8217;nun Gerektirdiği Kurumsal Bilgiler Bölümünü Bitirelim ve Sitemizi Tamamlayalım'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/yeni-turk-tucaret-kanununun-gerektirdigi-kurumsal-bilgiler-bolumunu-bitirelim-ve-sitemizi-tamamlayalim/
published: true
post_date: 2012-10-23 17:33:01
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.22.58-AM.png"><img class="alignright size-full wp-image-261" title="Screen Shot 2012-10-19 at 11.22.58 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.22.58-AM.png" height="380" width="628" /></a>

Evet sitemiz ufak ufak bitiyor. Son olarak yeni Türk Ticaret Kanunu'nun gerektirdiği kurumsal bilgileri içeren Kurumsal bölümümüzü de yaptıktan sonra html5 ile hazırladığımız şirket internet sitesi örneğimizi bitiriyoruz.

Peki kurumsal bölümüne eklememiz gereken bilgiler nelerdir? Yeni TTK bizden neler istiyor? <a href="http://www.sevka.net/haberler-137-Yeni_Turk_Ticaret_Kanununa_gore_olmasi_gereken_web_sitesinin_ozellikleri_nedir?.html">Şurada</a> ve <a href="http://www.muhasebetr.com/yeni-turk-ticaret-kanununda-sirketler-icin-web-sitesi-zorunlulugu-ve-uyulmamasi-halinde-cezasi/">şurada</a> belirtildiği üzere ilk olarak şirket ile ilgili temel bilgileri eklememiz gerekiyor. Bunlar;
<ol>
	<li>Ticaret Ünvanı (Ticaret Sicilinde belirtildiği gibi)</li>
	<li>Ticaret Sicil No.</li>
	<li>Bağlı olunan ticaret odası</li>
	<li>Kuruluş Tarihi</li>
	<li>Yetkili Müdürlerin Adı Soyadı</li>
</ol>
Bu bilgileri güzel bir şekilde görüntülemek için tablo kullanalım:
<pre><code>
&lt;table class="table table-hover"&gt;
    &lt;tr&gt;
        &lt;td&gt;&lt;strong&gt;Ticaret Ünvanı&lt;/strong&gt;: &lt;/td&gt;
        &lt;td&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
        &lt;td&gt;&lt;strong&gt;Ticaret Sicil No&lt;/strong&gt;: &lt;/td&gt;
        &lt;td&gt;283723-23498-2434&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
        &lt;td&gt;&lt;strong&gt;Bağlı Olunan Ticaret Odası&lt;/strong&gt;: &lt;/td&gt;
        &lt;td&gt;İstanbul Matbaacılar Odası&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
        &lt;td&gt;&lt;strong&gt;Kuruluş Tarihi&lt;/strong&gt;: &lt;/td&gt;
        &lt;td&gt;14 Mart 1971&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
        &lt;td&gt;&lt;strong&gt;Yetkili Müdür&lt;/strong&gt;: &lt;/td&gt;
        &lt;td&gt;Soner Kabadayısarı&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;
</code></pre>
Burda ne yaptık? Önce table etiketiyle yeni bir tablo oluşturduk. Bu etikete twitter bootstrap kütüphanesindeki table ve table-hover class özelliklerini verdik ki hem görünümü düzgün olsun, hem de tablo hücrelerinin üzerine geldiğimizde hücre renk değştirsin.
etiketiyle yeni bir satır oluşturduk ve td etiketiyle de hücrelerin içine bilgileri ekledik. Eğer sütunlarımıza başlık eklemek isteseydik th etiketini kullanmamız gerecekti. Sonuç olarak görüntümüz şu şekilde:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-23-at-8.17.18-pm1.png"><img class="alignright size-full wp-image-336" title="Screen Shot 2012-10-23 at 8.17.18 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-23-at-8.17.18-pm1.png" height="226" width="619" /></a>

Daha sonra bir çizim programında çizdiğimiz yönetim şemasını da siteye ekleyelim. Kurumsal bilgiler bölümünü aynen hakkımızda bölümünde yaptığımız gibi sağ tarafta tab bağlantılarına sahip olan article etiketleri şeklinde hazırlayacağız.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/yonetim1.png"><img class="alignright size-full wp-image-337" title="yonetim" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/yonetim1.png" height="439" width="628" /></a>

Bu bölümün kodu şu şekilde olacak. Yapı olarak hakkımızda bölümünden farkı yok. Article etiketi içinde makale ve tarih bilgisi sonra da içerik.
<pre><code>&lt;article class="tab-pane" id="yonetim" itemscope itemtype="http://schema.org/Article"&gt;
    &lt;header&gt;
        &lt;h3&gt;&lt;span itemprop="name"&gt;Yönetim Şeması&lt;/span&gt;&lt;/h3&gt;
        &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-20"&gt;20 Ekim 2012&lt;/time&gt; tarihinde eklendi&lt;/p&gt;
    &lt;/header&gt;
    &lt;p&gt;17 Ekim 2012 Tarihi itibariyle şirketimizin yönetim şeması aşağıdaki gibidir. Tüm ilgililere duyurulur.&lt;/p&gt;
    &lt;p&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/p&gt;
 &lt;img title="yonetim" alt="Yönetim Şeması" src="img/yonetim.png" /&gt;
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
&lt;p&gt;&lt;strong&gt;Yetkili Müdür: &lt;/strong&gt; Soner Kabadayısarı&lt;/p&gt;
&lt;/article&gt;</code></pre>
Görüntümüz de şu şekilde:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-23-at-8.22.24-pm1.png"><img class="size-full wp-image-340 alignnone" title="Screen Shot 2012-10-23 at 8.22.24 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-23-at-8.22.24-pm1.png" height="415" width="496" /></a>

Ortaklık yapısı bölümünü de aynı şekilde makale olarak oluşturduk.
<pre><code>
&lt;article class="tab-pane" id="ortaklik" itemscope itemtype="http://schema.org/Article"&gt;
    &lt;header&gt;
        &lt;h3&gt;&lt;span itemprop="name"&gt;Ortaklık Yapısı&lt;/span&gt;&lt;/h3&gt;
        &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-20"&gt;20 Ekim 2012&lt;/time&gt; tarihinde eklendi&lt;/p&gt;
    &lt;/header&gt;
    &lt;p&gt;17 Ekim 2012 Tarihi itibariyle şirketimizin ortaklık yapısı aşağıdaki gibidir. Tüm ilgililere duyurulur.&lt;/p&gt;
    &lt;p&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/p&gt;
    &lt;p&gt;5.000.000 TL Sermaye Bedeli ile&lt;/p&gt;
    &lt;ul&gt;
        &lt;li&gt;%51 2.550.000 TL Bedelle Sosyal Holding A.Ş.&lt;/li&gt;
        &lt;li&gt;%10 500.000 TL Bedelle Rebi Komercan&lt;/li&gt;
        &lt;li&gt;%20 1.000.000 TL Bedelle Yusuf Çugaşvili&lt;/li&gt;
        &lt;li&gt;%20 1.000.000 TL Bedelle Veli İliç Ulyanoğlu&lt;/li&gt;
    &lt;/ul&gt;
&lt;/article&gt;
</code></pre>
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-23-at-8.23.15-pm1.png"><img title="Screen Shot 2012-10-23 at 8.23.15 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2012-10-23-at-8.23.15-pm1.png" height="209" width="628" /></a>

Mali tablolar ve Diğer Kurumsal Belgeler bölümleri ile ilgili söylemek istediğim bir şey var. Bu bölümler daha önce duyurular bölümünde yaptığımız gibi blog şeklinde olacak. Herhangi bir belge eklediğimizde şu şu belge eklendi başlığı ile makaleyi göreceğiz. Bu belgeler için bir kaç tane ikon hazırladım. Bunlar için openoffice'in ikonlarını kullandım ne de olsa açık kaynaklı. :)

<img class="alignleft size-full wp-image-341" title="document" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/document1.png" height="63" width="63" /><img class="alignleft size-full wp-image-342" title="pdf" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/pdf1.png" height="61" width="60" /><img class="alignleft size-full wp-image-344" style="color:#333333;font-style:normal;line-height:24px;" title="spreadsheet" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/spreadsheet1.png" height="63" width="63" /><img class="alignleft" title="presentation" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/presentation1.png" height="63" width="63" />

Bu ikonları her belge eklediğimde kullanacağım. Şimdi bölümümüzün kodlarını inceleyelim. Yine burada da farklı olan bir şey yok. Bu bölüm için tek farklı olan şey olan article etiketi içinde başka bir article etiketi kullandığımıza dikkat edin. HTML5 bu tarz yapılara çok abartmamak kaydıyla izin veriyor. Belki burada section kullanmak daha doğru olabilirdi ancak onu da son rötüşları yapacağımız yayınlama bölümüne bırakalım.
<pre><code>
 &lt;article class="tab-pane" id="malitablolar" itemscope itemtype="http://schema.org/Article"&gt;
        &lt;header&gt;
            &lt;h3&gt;&lt;span itemprop="name"&gt;Mali Tablolar&lt;/span&gt;&lt;/h3&gt;
        &lt;/header&gt;
        &lt;p&gt;&lt;/p&gt;
        &lt;article class="offset1" id="ücyillik" itemscope itemtype="http://schema.org/Article"&gt;
            &lt;header&gt;
                &lt;h4&gt;&lt;span itemprop="name"&gt;2009-2012 3 Yıllık Finansal Plan Eklendi&lt;/span&gt;&lt;/h4&gt;
                &lt;p&gt;&lt;time itemprop="pubdate" datetime="2010-10-08"&gt;8 Ekim 2012&lt;/time&gt;&lt;/p&gt;
            &lt;/header&gt;
            &lt;p&gt;17 Ekim 2012 Tarihi itibariyle şirketimizin 3 yıllık finansal yapısı aşağıdaki gibidir. Tüm ilgililere duyurulur.&lt;/p&gt;
            &lt;p&gt;Kızılyıldız Matbaacılık A.Ş.&lt;/p&gt;
            &lt;a href="ücyillik.pdf" alt="3 Yıllık Finansal Plan"&gt;&lt;img src="img/ikonlar/spreadsheet.png" /&gt;&lt;/a&gt;
            &lt;a href="ücyillik.pdf" alt="3 Yıllık Finansal Plan"&gt;2009-2012 Finansal Plan&lt;/a&gt;
        &lt;/article&gt;
    &lt;/article&gt;
</code></pre>
İki bölümümüzün de yapısı aynı. Bunlara her belge eklediğimizde blog yapısı olduğundan dolayı sayfa aşağı doğru uzayacak:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-8.30.40-PM.png"><img class=" wp-image-334 alignnone" title="Screen Shot 2012-10-23 at 8.30.40 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-8.30.40-PM.png" height="197" width="628" /></a>

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-8.30.45-PM.png"><img class="alignnone size-full wp-image-333" title="Screen Shot 2012-10-23 at 8.30.45 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-23-at-8.30.45-PM.png" height="191" width="628" /></a>

Sitemizin son bölümünü de tamamladık. Bir sonraki bölümde son rötüşları yapacak ve sitemizi FTP istemcisi kullanarak nasıl yayınlayacağımızı göreceğiz.

Dayanışmayla!
Meraklı Bilişimci