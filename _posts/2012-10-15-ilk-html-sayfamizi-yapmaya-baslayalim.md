---
ID: 157
post_title: >
  İlk HTML sayfamızı yapmaya
  başlayalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/ilk-html-sayfamizi-yapmaya-baslayalim/
published: true
post_date: 2012-10-15 01:33:46
---
İnternette bilgileri barındıran sayfalar HTML ile yapılır demiş ve etiketlerin yapılarıyla ilgil bilgi vermiştik. Şimdi en basit HTML sayfası nelerden oluşur bir göz atalım.
<pre>&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;İlk İnternet Sayfam&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;p&gt;Haydi güzel birşeyler yapalım&lt;/p&gt;
  &lt;/body&gt;
&lt;/html&gt;</pre>
Bu gördüğümüz kodu 1-temiz.html olarak htdocs altına kaydedelim ve tarayıcımızdan <a href="http://127.0.0.1/1-temiz.html">http://127.0.0.1/1-temiz.html</a> linkini çağıralım. Korkmayın birazdan hepsini teker teker açıklayacağız. Karşımıza şöyle bir görüntü gelecek.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-15-at-4.21.08-AM.png"><img class="alignnone size-full wp-image-158" title="Screen Shot 2012-10-15 at 4.21.08 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-15-at-4.21.08-AM.png" height="165" width="331" /></a>

Tebrikler. İlk internet sayfanızı yaptınız. Şimdi gelelim yazdığımız HTML etiketlerini basitçe açıklamaya. İlk satırda yazdığımız &lt;!DOCTYPE html&gt; dosyanın HTML türünde olduğunu belirtiyor. Her HTML dosyasında bundan bulunacak. Bu ifadeden sonra gelen, &lt;html&gt;&lt;/html&gt; etiketleri, içinde yer alan bilginin HTML kodu olduğunu söylüyor. Peki &lt;head&gt; ne demek? Kafa anlamına gelen &lt;head&gt; etiketi belgemizle ilgili sayfa içeriğiyle alakası olmayan, sayfa başlığı, kullanılacak stil veya javascript dosyaları, sayfamızla ilgili bilgi veren meta etiketleri gibi bilgileri yazdığımız alan. Buradaki &lt;title&gt; etiketi ise belgemizin başlığını tanımlamamıza yarayan etiket. Gördüğümüz gibi tarayıcımızın tam tepesinde &lt;title&gt;&lt;/title&gt; arasına yazdığımız başlık şak diye belirdi.

Peki &lt;body&gt; nedir? &lt;body&gt; de gövde anlamına geliyor, belgemizin içeriğiyle ilgili herşeyi burada tutmamız gerekiyor. Peki &lt;p&gt; nedir? &lt;p&gt; de paragraf'ın p'si. Yani tarayıcıya paragrafın başladığını söylüyor. Dikkat ettiysek cümlemiz sağa sola yapışmadı ve düzgün bir şekilde ekrana geldi. Peki paragrafın bittiğini kim söylüyor? &lt;/p&gt; kapatma etiketi bu işi yapıyor. &lt;/body&gt; ile sayfa gövdesini, &lt;/html&gt; ile sayfanın tamamını kapatıyoruz.

İşte en basit HTML sayfasının yapısı böyle. Siz de isterseniz şimdi internet tarayıcınızdan sayfa kaynağını görüntüle diyerek ya da herhangi bir html sayfasını bilgisayarınıza kaydedip, bir metin editöründe açarak kurcalamaya başlayabilirsiniz.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-15-at-4.31.36-AM.png"><img class="alignnone size-full wp-image-159" title="Screen Shot 2012-10-15 at 4.31.36 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-15-at-4.31.36-AM.png" height="436" width="446" /></a>

Dayanışmayla,
Meraklı Bilişimci