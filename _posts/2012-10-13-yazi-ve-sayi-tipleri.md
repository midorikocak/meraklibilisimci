---
ID: 150
post_title: Yazı ve Sayı Tiplerini öğrenelim
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/yazi-ve-sayi-tipleri/
published: true
post_date: 2012-10-13 23:40:55
---
<!-- wp:paragraph -->
<p>PHP'nin çok güzel bir özelliği var. Hızlı bir şekilde değişkeni tanımlayabiliyoruz. Yani değişkenin yazı mı, sayı mı, yoksa virgüllü sayı mı olduğunu önceden belirtmemize gerek yok. Tek tırnak ya da çift tırnak içindeki metinleri otomatik olarak karakter olarak tanıyor. Sadece sayı olarak tanımlamak istiyorsak, direk sayıya eşitlememiz yetiyor. Bunun dışında başka veri tipleri de var ama bu seviyede bunları bilmemiz yeterli. Ne demiştik, her şey yerinde ve zamanında güzel.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":124,"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.24-PM.png"><img src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.24-PM.png" alt="" class="wp-image-124"/></a></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Sayı değişkenleri tanımlarken, = işaretinden sonra işlem yapabiliyoruz. Yani toplama(+)<br>, çıkarma(-), çarpma(*) ve bölme(/) gibi bir çok işlemi hem sayılar, hem de başka sayı değişkeni kullanarak yapabiliyoruz.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Şimdi htdocs altından 2-işlem.php'yi açalım ve incelemeye başlayalım.</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">&lt;?php

/**  
*                    Merakli Bilişimci
*                   meraklibilisimci.com
**/

// PHP değişkenlerin tiplerini önceden belirtmeye gerek yoktur.

$isim ="Mutlu "; // Tırnak içinde değer verilen değişkenler string olarak algılanır
$soyad ="Koçak";
$dogumYili = 1984; //Tırnak kullanılmazsa PHP Derleyicisi değişkeni sayı kabul eder
$telefon = "05337428708";
$yas = 2012 - $dogumYili; //Değişkenler ile veri tipi doğruysa matematiksel işlem yapılabilir</pre>
<!-- /wp:preformatted -->

<!-- wp:paragraph -->
<p>Gördüğümüz gibi yazı saklamak istediğimiz değişkeni tanımlarken çif tırnak kullandığımız zaman şöyle bir olay var; metnin içine direk başka değişken yazabiliyoruz. PHP yorumlayıcısı metni okurken bu değşkenlerin değerini hafızadan çekip metni otomatik olarak oluşturuyor.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Dosyada biraz daha ilerleyelim ve 18. satırda başlayan koda bakalım.</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">$mesaj = "Merhaba $isim $soyad, $yas yaşındasınız.
"; // PHP derleyicisi mesajın içerisindeki değişkenleri gösterir.
echo $mesaj;

// Merhaba Mutlu  Koçak, 2012-1984 yaşındasınız</pre>
<!-- /wp:preformatted -->

<!-- wp:paragraph -->
<p>Dosyamızı h<a href="//127.0.0.1/mtkocakPhpEgitimi/2-islem.php">ttp://127.0.0.1/mtkocakPhpEgitimi/2-islem.php</a> adresinden çağırdığımız zaman başında yorum olmayan echo işlevi çalışacak ve ekrana şöyle bir görüntü gelecek:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1659,"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/10/yas.jpg"><img src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/yas.jpg" alt="" class="wp-image-1659"/></a></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Buralar biraz sıkıcı geliyor olabilir, ancak bebek adımları atıyoruz. Zıplamak için önce yürümeyi öğrenmemiz lazım.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Gördüğümüz gibi PHP Yorumlayıcısı otomatik olarak tırnak içerisindeki değişkenlerin değerini atadı ve ekrana bu şekilde yansıttı.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Şimdi 18.satırdaki echo $mesaj; ifadesinin başına # veya // işaretini koyalım ve yorum haline getirelim ki çalışmasın. Bunun yerine tek tırnak kullandığımız 28.satırdaki</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>#echo $degiskensiz;</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>işlevinin başındaki # işaretini kaldıralım ve bu şekilde çalıştıralım.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Gördüğümüz gibi çift tırnak yerine, tek tırnak kullandığımızda, şu şekilde bir görüntü alıyoruz:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":126,"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-2.34.05-AM.png"><img src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-2.34.05-AM.png" alt="" class="wp-image-126"/></a></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Tek tırnak kullandığımızda Php yorumlayıcısı $ ile baslayan degiskenleri önemsemedi ve metini direk ekrana yansıttı. Bütün bunlar özellikle form ile işlem yaparken çok işimize yarayacak.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Daha sonra 28. satırdaki echo $degiskensiz; ifadesinin başına tekrar # karakterini koyalım. 31. satırdaki echo $islem; ifadesinin başındaki # karakterini kaldıralım.</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">$islem = "Merhaba ".$isim." ".$soyad.", ".$yas." yaşındasınız.
";
echo $islem;</pre>
<!-- /wp:preformatted -->

<!-- wp:paragraph -->
<p>Örnekte, herhangi iki değişken ya da tırnak içinde bulunan metinler arasındaki nokta(.) işareti de metin türü değişkenleri birleştirme operatörüdür. (String Concatenation.) Örneğin</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>$ad = "Adım"</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>$soayd = "Soyadım";</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>$tamAdim = $ad." Gobek Adım ".$soyad;</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Burada eşittirden sonra ya da herhangi bir yerde, mesela noktalı virgülden önce boşluk bırakırsak, php yorumlayıcısı bunları görmeyecek.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Nasıl ki</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>$sonuc = 3+5; ile $sonuc = 3 + 5 ;</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>aynı sonucu verecektir. Ancak biz yine de okunurluk açısından böyle gereksiz boşlukları kullanmayalım.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Dosyayı bu şekilde çağırdığımızda karşımıza çıkan sonuç şöyle;</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1659,"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-2.29.51-AM.png"><img src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/yas.jpg" alt="" class="wp-image-1659"/></a></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Gördüğümüz gibi Php yorumlayıcısı ayrı ayrı değişkenleri ve Çift tırnak içindeki karakterleri birleştirdi ve bize bu şekilde yansıttı.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Kullandığımız &lt;br /&gt; html tagi, alt satıra geçmeye yarıyor. Tarayıcı bu tag'i tanıyıp, ardından gelen metni bir alt satıra yazacak.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Bunun gibi &lt;p&gt; ve &lt;/p&gt; tagleri arasında yazdığımız metinlerin de tarayıcı paragraf olduğunu anlayacak ve buna göre davranacaktır. (CSS sayfa stiline göre altında, yanında boşluk bırakacak, ya da renklendirecek.)</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Şu ana kadar, değişken atamayı, yazıları ve sayıları göstermeyi anlamış bulunuyoruz.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Dayanışmayla,<br>Meraklı Bilişimci</p>
<!-- /wp:paragraph -->