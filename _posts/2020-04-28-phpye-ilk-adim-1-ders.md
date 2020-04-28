---
ID: 1752
post_title: 'PHP&#8217;ye ilk adım &#8211; 1. Ders'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: http://www.meraklibilisimci.com/?p=1752
published: true
post_date: 2020-04-28 14:42:34
---
<!-- wp:image {"id":1754,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/carbon-14.png?fit=924%2C625" alt="" class="wp-image-1754"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Bu yazı dizisinde size internette en çok kullanılan programlama dillerinden biri olan PHP'yi minik örneklerle tanıtacağım. Dizinin sonunda kendi kendinize 'sadece PHP' kullanarak web uygulamaları geliştirebilir hale geleceksiniz. </p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>PHP Nedir?</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Öncelikle PHP'nin ne olduğunu size kısaca anlatayım. PHP bir programlama dilidir. Güncel TDK sözlüğüne göre, programlama işi: "Bilgisayara bir işlemi yaptırmak için yazılan komutlar dizisi." tanımlanmış. Programlama dili ise bizim bilgisayara yapmasını istediğimiz komutları belirtirken kullandığımız  metinleri yazmamıza yardım eden araç. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Burada programlama dillerinin detaylarına girmek istemiyorum, ancak PHP'nin güçlü, kolayca yazılım geliştirmeye yarayabilen, nesne yönelimli, web odaklı bir programlama dili olduğunu söyleyebilirim sadece.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Peki PHP ne işe yarıyor? PHP'nin en büyük amacı, sunucu adı verilen ve web sayfalarını tarayıcınıza gönderen bilgisayarlarda, belirttiğimiz şekilde kullanıcıdan veya başka bir yerden verileri alıp, yine kullanıcıya veya başka bir yere işleyip göndermemizi sağlamaktır. Sonuçta olduğu gibi göndersek, bir anlamı olmazdı değil mi? </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Peki PHP'yi kimler kullanıyor? En bilinen örnek facebook, fakat neredeyse dünyadaki bütün gazeteler, bloglar, kurumsal şirket siteleri PHP ile geliştirilmiştir. Daha önceki bölümlerde PHP'yi kimlerin kullandığını belirtmiştim, burada da fazla ayrıntıya girmeden kodlamaya geçmek istiyorum.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1755,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="http://www.meraklibilisimci.com/wp-content/uploads/2020/04/main-qimg-0d210597215541d3517ecb1abd42abb8.gif" alt="https://www.quora.com/How-does-PHP-work/answer/Sanjog-Kumar-Dash" class="wp-image-1755"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Burada belirtildiği şekilde, PHP kullanıcı vasıtasıyla sunucuya tarayıcıdan gelen istekleri alır, işler, gerekirse veritabanına bağlanır ve verileri çeker, gerekirse dosyaları okur, gerekirse mail atar ve bilgiyi işleyip yine kullanıcıya veya başka bir yere gönderir. Web üzerinde çalışan bulut tabanlı bütün yazılımların temel çalışma mantığı budur.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Kurulum</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Program yazmak için ihtiyacımız olan en önemli şey, metin editörü. Oturup not defterinde de program yazabiliriz ama program yazmak hedeflenerek üretilmiş metin editörlerini kullanmak bize zaman kazandıracaktır.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Bir çok metin editörü mevcut, bunların en bilinen örnekleri, NetBeans, Eclipse, PHPStorm ve Sublime Text programlarıdır. Ben Sublime Text ve PHPStorm kullanıyorum. Şu aşamada biz Sublime Text kullanacağız.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Windows ortamında olduğumuzu var sayıyorum. Herkes Chrome tarayıcı kullanıyor olmayabilir fakat, sık kullanıldığı için örnekleri windows ve chrome üzerinden vereceğim. Siz Mac bilgisayar üzerinde Firefox tarayıcı kullanıyor olabilirsiniz. Kurulum aşamaları çok da farketmiyor anlatayım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1758,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_19_39_17.png?fit=924%2C578" alt="" class="wp-image-1758"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Tarayıcıya "sublime text yazalım" ve açılan pencerede ilk linke tıklayalım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1759,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i2.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_19_39_39.png?fit=924%2C578" alt="" class="wp-image-1759"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>"Download for windows" diyerek indirelim ve kuralım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1760,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i2.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_19_45_27.png?fit=924%2C578" alt="" class="wp-image-1760"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Sublime Text'in kurulumu gayet basit. Herhangi bir ayarlama yapmamıza gerek yok. PHP dosyalarını düzenlerken kullanacağız Sublime Text Editörünü. Sublime Text'i kullanması ücretsizdir, ama arada sırada sizden dilenci gibi para ister, çok paranız varsa bilemiycem tabi ama para ödemeden de kullanabilirsiniz.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Şimdi gelelim PHP'yi kurmaya. PHP'yi kendi bilgisayarımıza kurup çalıştırmak için bazı programları kurmaya ihtiyacımız var. Bunlar:</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>Apache web sunucusu</li><li>PHP yorumlayıcısı</li><li>MySQL veritabanı</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>En temelde, PHP ile bir uygulama geliştirmek için ihtiyacımız olan minimum şey bunlar.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1756,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_19_38_32.png?fit=924%2C578" alt="" class="wp-image-1756"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Öncelikle tarayıcıyı açıp XAMPP yazalım ve ilk çıkan linke tıklayalım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1757,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_19_38_04.png?fit=924%2C578" alt="" class="wp-image-1757"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Daha sonra indir diyerek, gelen programı indirelim ve kuralım. Xampp'ın da kurulumu çok zor değil. </p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1761,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_21_47_53.png?fit=924%2C578" alt="" class="wp-image-1761"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>İndirdiğimiz programda devam et diyerek ilerleyelim.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1762,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_21_49_15.png?fit=924%2C578" alt="" class="wp-image-1762"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Seçenekleri bu şekilde işaretleyelim ve ilerleyelim. Kurulum biraz uzun sürebilir, sorun değil.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1763,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_21_49_55.png?fit=924%2C578" alt="" class="wp-image-1763"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Bittiğinde "Do you want to start control panel now?" yani "Şimdi kontrol panelini başlatmak ister misiniz?" diye sorar, işaretleyelim.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1764,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_12_59.png?fit=924%2C578" alt="" class="wp-image-1764"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Karşımıza dil sorgusu çıkacak, ingilizceyi seçelim.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1765,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_13_07.png?fit=924%2C578" alt="" class="wp-image-1765"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Kontrol paneli açıldıktan sonra windows bizden izin ister, izin verelim.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1766,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_13_33.png?fit=924%2C578" alt="" class="wp-image-1766"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Apache ve Mysql programlarının yanında start tuşlarına basalım ve Apache ve MySQL'i çalıştıralım, izinleri onaylayalım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1767,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_14_13.png?fit=924%2C578" alt="" class="wp-image-1767"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Tebrikler. Şu anda bilgisayarınıza sunucu kurdunuz ve PHP kodlamaya hazırsınız.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Kurulumu kontrol etmek için</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Kurulumu kontrol etmek için bir tarayıcı açalım ve "localhost/dashboard/phpinfo.php" yazalım. Eğer karşımıza şu ekran geldiyse, PHP'yi doğru bir şekilde kurmuşuz demektir.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1768,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_14_55.png?fit=924%2C578" alt="" class="wp-image-1768"/></figure>
<!-- /wp:image -->

<!-- wp:heading -->
<h2>Kodlamaya başlayalım</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Kodlamaya başlamadan önce, windows'ta gizli dosyaları görüntülemek ve dosya uzantılarını görüntülemek için File Explorer ayarlarını resimde görülen şekilde yapalım:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1769,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_21_56.png?fit=924%2C578" alt="" class="wp-image-1769"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Herhangi bir klasörde seçeneklere tıklayalım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1770,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_22_10.png?fit=924%2C578" alt="" class="wp-image-1770"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Görünüm kısmında, "Bilinen dosya türleri için uzantıları gizle" seçeneğini kaldıralım ve "Gizli dosya ve klasörleri göster" seçeneğini seçelim.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Gizli dosyaları dosyaları görüntülemeyi hallettikten sonra, "C:/xampp/htdocs" dizinine gidelim ve orada "programlarım" isminde yeni bir dizin oluşturalım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1775,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/Screen-Shot-2020-04-28-at-13.46.55.png?fit=924%2C487" alt="" class="wp-image-1775"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Başlangıç menüsünden Sublime Text'i bulup çalıştıralım.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1772,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_23_14.png?fit=924%2C578" alt="" class="wp-image-1772"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Çalıştıktan sonra boş bir ekran gelecek.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1774,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/VirtualBox_Windows10_31_07_2019_22_23_03-1.png?fit=924%2C578" alt="" class="wp-image-1774"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Çıkan boş Sublime Text editörüne şu kodları yazalım.</p>
<!-- /wp:paragraph -->

<!-- wp:code {"lineNumbers":true} -->
<pre class="wp-block-code"><code lang="php" class="language-php line-numbers">&lt;?php

/*
 * Görevler:
 *
 * 1. Önce programı olduğu gibi çalıştırın.
 * 2. Daha sonra Midori yazan yere kendi isminizi yazın.
 * 3. Programı tekrar çalıştırın.
 */
$isim = 'Midori';

echo "Merhaba $isim tanıştığıma memnun oldum.";
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>Daha sonra dosyayı, daha önce oluşturduğumuz "C:/xampp/htdocs/programlar" dizinine "1-hello.php" olarak kaydedelim.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1776,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i1.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/Screen-Shot-2020-04-28-at-14.18.52.png?fit=924%2C615" alt="" class="wp-image-1776"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Tarayıcıya gidip "localhost/programlar/1-hello.php" adresini girelim. Karşımıza şöyle bir görüntü gelecek:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1777,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://i0.wp.com/www.meraklibilisimci.com/wp-content/uploads/2020/04/Screen-Shot-2020-04-28-at-14.19.22.png?fit=924%2C568" alt="" class="wp-image-1777"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Tebrikler! İlk PHP Programınızı çalıştırdınız! Şimdi kısaca kodun ne yaptığını anlatayım. </p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1753,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="http://www.meraklibilisimci.com/wp-content/uploads/2020/04/carbon-13-1024x420.png" alt="" class="wp-image-1753"/></figure>
<!-- /wp:image -->

<!-- wp:list -->
<ul><li>"&lt;?php" ifadesiyle programın bir php kodu olduğunu belirttik.</li><li>$isim diyerek bir <strong>değişken </strong> belirledik ve değişkene 'Midori' <strong>değerini </strong>atadık.</li><li>Daha sonra "echo "Merhaba $isim tanıştığıma memnun oldum.";" diyerek kullanıcıyı selamladık.</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>PHP'de ve diğer programalama dillerinde değişken, her türlü değeri alabilen, farklı değerlere isim verebilmemizi sağlayabilen yapılardır. Örneğin, isim, yaş, doğum yılı ifadeleri değişken belirtirler, çünkü değerleri sürekli değişebilir.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>PHP'de ekrana çıktı yazmayı <strong>echo </strong>ifadesiyle gerçekleştiriyoruz. Burada "çift tırnak" arasındaki ifadeler metin değerini ekrana bastığımızı belirtiyor. Eğer değişkenin değerini ekrana basmak istemeseydik o zaman da 'tek tırnak' kullanacaktık. Çıktı şu şekilde görünecekti.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":1778,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="http://www.meraklibilisimci.com/wp-content/uploads/2020/04/Screen-Shot-2020-04-28-at-14.25.29.png" alt="" class="wp-image-1778"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Dersimiz bitti. Şimdi ödev zamanı. Ödev olarak "Midori" yerine kendi adınızı yazacaksınız. Daha sonra da "Merhaba &lt;kendi-adiniz>  tanıştığıma memnun oldum." yazısını gördüyseniz bu iş tamamdır.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Tebrikler, ilk programınızı yazdınız!</p>
<!-- /wp:paragraph -->