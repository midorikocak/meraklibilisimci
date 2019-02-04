---
ID: 631
post_title: 'VERİTABANI NEDİR? SQL’LE BİRŞEYLER YAPMAK: SQL – 2'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/veritabani-nedir-sqlle-birseyler-yapmak-sql-2/
published: true
post_date: 2014-08-08 13:43:30
---
Bir önceki yazıda veritabanının ne olduğundan ve ne işe yaradığından, belli başlı SQL komutlarından bahsettik. SQL'in açılımı, "yapılandırılmış sorgulama dili". Programlama dili değil, öğrenmesi kullanması inanılmaz kolay, soru sormaya, cevap almaya yarayan müthiş bir dil. Biz de en kolay işlemlerden en çok ihtiyaç duyacağımız işlemlere, sorguları anlatacağız ve derinlere dalmayı size bırakacağız, tüm yazılarda olduğu gibi. Nihai hedefimiz, içerik yönetim sistemi veya blog yazmak, yani bilgileri girmek, bilgileri almak, aslında bu mantıkla her türlü yönetim sistemi yazılımını kuracağınız yapıya göre üretebilirsiniz. Yani yazı yerine personel olursa, personel yönetim sistemi, personel yerine ürün ve satış olursa, komple bir e-ticaret sistemi de yazabilirsiniz. Dediğim gibi, derinlere dalmak, sizin merakınıza kalmış, bebek adımlarıyla ilerliyoruz, herşey çok kolay ve zevkli olmalı ki korkmayalım ve de hevesimiz kaçmasın. MySQL'i yani sistemimizde kullanacağımız veritabanı yazılımını yönetmemiz için phpMyAdmin adlı web aracına ihtiyacımız var. Önce phpMyAdmin'i bulalım. Hatırlarsanız daha önce xampp kurduğumuza sistemimize yüklendiğini söylemiştim. Tarayıcının adres çubuğuna http://localhost/phpmyadmin yazmalıyız. Karşımıza şöyle bir ekran gelecek. <a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/apache-phpmyadmin.gif"><img class="alignnone size-full wp-image-634" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/apache-phpmyadmin.gif" alt="Apache-phpmyadmin" width="474" height="395" /></a>   Gördüğümüz 'Create Database' alanına istediğimiz veritabanı ismini girerek veritabanını oluşturabiliriz. Sağında çıkan utf-8 gibi öğeler içeren liste ise veritabanımızda hangi karakterlerde bilgi tutacağımızı belirtir. Burası önemli, çünkü çince tutacaksak çince, rusça tutacaksak ve özel karakter seti kullanmak istiyorsak farklı karakter setlerini seçebiliriz. Biz şimdilik türkçeye ve dier dillere evrensel destek olan utf-8 karakter kodlamasını kullanacağız. SQL yazan yere tıklayalım, ve ordan SQL sorgularımızı tek tek girmeye başlayalım:
<pre>CREATE DATABASE content
DEFAULT CHARACTER SET utf8 COLLATE utf8_turkish_ci;</pre>
Buradaki komut veritabanını yaratma komutuydu. İsim olarak ben 'content' seçtim, yani ingilizce içerik demek, siz istediğiniz ismi verebilirsiniz. Sağdaki menüden content isimli veritabanımızı seçelim. Aslında biz veritabanımızı phpMyAdmin kullanara seçiyoruz ama phpMyAdmin üzerinde işlem yapacağı veritabanını seçmek için
<pre>USE content;</pre>
Use yani "kullan kelimesini kullandık." Mantık yürütürsek, veritabanımızı oluştururken CREATE yani yarat komutunu kullanmıştık. Peki bilgileri içeren tabloları kullanmak için ne kullanacağız. Tahmin ettiğiniz gibi CREATE komutunu kullanacağız. Ama tabloyu nasıl oluşturacağız, ve tablo nelerden oluşur onlara bir göz atalım.
<ol>
	<li>Tablo veritabanında bilgileri tutmaya yarayan alandır. Tabloların ayrı ayrı isimleri bulunur. Örneğin, öğrenciler, kullanıcılar, yazılar tablosu gibi.</li>
	<li>Her tabloda tutulan bilgi farklı farklı özelliklere sahiptir. Mesela bir öğrencinin, öğrenci numarası, adı, soyadı gibi bilgiler varken, bir ürünün fiyatı vardır. Bunlara tablonun alanları denir.</li>
	<li>Öğrenci numarasının veya fiyatın sayı olarak tutulmasını zorlayabiliriz, yani sayı değil de 'asfdghgjklş' gibi bi bilgi giriliyorsa, bunun hata vermesini sağlayabiliriz, bunun için de veri tiplerini belirlememiz gerekir.</li>
	<li>İki tane öğrencimiz olsun, bunların ikisinin de adı "Deniz Mahir" olsun. Bu iki öğrenciyi birbirinden ayrımak için her öğrenciye ayrı verilecek bir numaraya ihtiyacımız var. Öğrenci numarası, her öğrenci için farklıdır. (UNIQUE) Bu bilgiye 'id' diyoruz, arama yaparken bu numaraya göre arama yaparız ki tek bir kayıda ulaşalım. Bu tek kayıt veren alana 'birincil anahtar' veya ingilizce 'PRIMARY KEY' denir.</li>
	<li>Her girdiğimiz id alanını tek tek aklımızda tutmamıza veya son öğrencinin numarasını tek tek artırmamıza gerek yok, ki son öğrenci silinmiş olabilir.  Bu yüzden birincil anahtara 'otomatik artırma' yani 'AUTO INCREMENT' özelliği vermemiz gerekir.</li>
	<li>Farklı bilgilerin de eşsiz olmasını sağlayabiliriz. Yani aynı e-posta adresiyle kayıt yapılmamasını sağlayabiliriz. Bu bilgilere 'eşsiz' yani 'UNIQUE' özelliği vermemiz gerekir.</li>
</ol>
Gelelim elimizdeki son tablo yaratma koduna;
<pre>CREATE TABLE IF NOT EXISTS `posts` (
  `id` int(11) NOT NULL,
  `title` varchar(255) COLLATE utf8_turkish_ci NOT NULL,
  `category_id` int(11) NOT NULL,
  `created` datetime NOT NULL,
  `updated` datetime NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_turkish_ci;
</pre>
Burada id, satırları birbirinden ayrıt etmemizi sağlayan anahtar alan. Diğer herşey aynı olsa bile, bu id alanından iki tane aynı değer taşıyan satır olamaz. Bi nevi kimlik kartı gibi düşünebiliriz. Adı üstünde.

int(11), varchar(255), datetime gibi alanların isminden sonra gelenler de veritiplerini gösteriyor. Örneğin yaş alanına sayı girmeye zorlamak için int(11) yani 11 haneli tamsayı olduğunu belirtmek zorundayız.

varchar(255) 255 karakter gireceğimiz bir alanı belirtiyor. "datetime" ise saat ve tarih bilgisi girmek zorunda olduğumuz alanın veri tipini temsil eder. Bunlar gibi, text, boolean, date gibi veritipleri de vardir. Şimdilik veri tipleri konusunda da detaya girmiyorum. Zaten en çok kullandığımız veritipleri de genellikle bunlar.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-16.41.54.png"><img class="alignnone size-full wp-image-640" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-16.41.54.png" alt="Screen Shot 2014-08-08 at 16.41.54" width="474" height="213" /></a>

İlk tablomuzu yaratma kodumuzu phpmy admine gidip yapıştıracağız ve ilk tablomuz oluşmuş olacak.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-16.41.44.png"><img class="alignnone size-full wp-image-641" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-16.41.44.png" alt="Screen Shot 2014-08-08 at 16.41.44" width="474" height="226" /></a>

Tebrikler! Artık elimizde bir veritabanımız ve veritabanı tablomuz var. Bir sonraki yazıda bilgi girmeyi ve bilgi çekmeyi öğreneceğiz.