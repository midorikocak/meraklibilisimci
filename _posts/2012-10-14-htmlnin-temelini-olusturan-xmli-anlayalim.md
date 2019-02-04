---
ID: 154
post_title: 'HTML&#8217;nin temelini oluşturan XML&#8217;i anlayalım'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/htmlnin-temelini-olusturan-xmli-anlayalim/
published: true
post_date: 2012-10-14 02:53:59
---
Form ile veri girmeye başlamadan önce biraz HTML'den bahsetmekte yarar var.  HTML yani Hyper Text Markup Language internet sayfası oluşturmaya yarayan etiketleme dilidir. Bir programlama dili değildir. Belli başlı bilgileri farklı etiketlerle bilgisayarların anlamalarını sağlayan XML dilinin bir türüdür. Burada etiketler, sayfalarımızın Firefox, Chrome, Safari ve (ne yazık ki) IE tarafından anlaşılamalarını sağlayan kodlardır.<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5_logo_512.png"><img class="alignright" title="HTML5_Logo_512" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/html5_logo_512.png?w=300" height="300" width="300" /></a>

En basit anlatımıyla bir etiketten bahsettiğimizde aklımıza &lt;etiket&gt; gibi bir ifade gelir. HTML dilinde çoğu etiket &lt;/etiket&gt; şeklinde kapatılmak zorundadır. Mesela meyvelerdan bahseden bir XML dosyası şu şekilde tanımlanabilir.
<pre>&lt;meyveler&gt;
    &lt;meyve&gt;Elma&lt;/meyve&gt;
    &lt;meyve&gt;Armut&lt;/meyve&gt;
    &lt;meyve&gt;Kiraz&lt;/meyve&gt;
    &lt;meyve&gt;Çilek&lt;/meyve&gt;
&lt;/meyveler&gt;</pre>
Buraya baktığımızda kabaca dokümanın neden bahsettiğini anlayabiliyoruz. Ayrıca etiketlerin farklı özellikleri de olabilir. Bunlar da şu şekilde gösterilir:
<pre>&lt;ogrenciler&gt;
    &lt;ogrenci yas="21" no="121"&gt;Cevahir Bardakçı&lt;/ogrenci&gt;
    &lt;ogrenci yas="20" no="62"&gt;Mahir Deniz&lt;/ogrenci&gt;
    &lt;ogrenci yas="22" no="910"&gt;Hüseyin Ulaş&lt;/ogrenci&gt;
    &lt;ogrenci yas="21" no="68"&gt;İbrahim Erdal&lt;/ogrenci&gt;
&lt;/ogrenciler&gt;</pre>
Gördüğümüz gibi burada no="" ifadesiyle ek özellik tanımlayabildik. Dikkat ederseniz, burada birden fazla özellik de tanımlayabiliyoruz. Bu sayede elimizdeki bilgileri hem anlamlandırıyor hem de zenginleştirebiliyoruz. Genellikle XML dosyaları bu şekilde çalışır.

Şimdilik bu kadar, daha sonra HTML konusuna devam edeceğiz.

Dayanışmayla,
Meraklı Bilişimci