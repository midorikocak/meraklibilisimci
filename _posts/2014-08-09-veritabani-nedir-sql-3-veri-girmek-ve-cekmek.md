---
ID: 644
post_title: >
  Veritabanı nedir? SQL-3 Veri girmek ve
  çekmek
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/veritabani-nedir-sql-3-veri-girmek-ve-cekmek/
published: true
post_date: 2014-08-09 11:13:31
---
Ana hedefimiz olan içerik yönetim sistemi yazmak için gereken veritabanını şu şekilde oluşturuyoruz.
<pre>CREATE TABLE IF NOT EXISTS `categories` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(255) COLLATE utf8_turkish_ci NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_turkish_ci AUTO_INCREMENT=1 ;


CREATE TABLE IF NOT EXISTS `files` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `filename` varchar(255) COLLATE utf8_turkish_ci NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_turkish_ci AUTO_INCREMENT=1 ;

CREATE TABLE IF NOT EXISTS `posts` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(255) COLLATE utf8_turkish_ci NOT NULL,
  `content` text COLLATE utf8_turkish_ci,
  `category_id` int(11) NOT NULL,
  `created` datetime NOT NULL,
  `updated` datetime NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=utf8 COLLATE=utf8_turkish_ci AUTO_INCREMENT=1 ;


</pre>
Eğer eklemediysek merakli veritabanımıza bu alanları ekleyelim. Bir içerik yönetim sistemi ile ne yapılır? Öncelikle bunları düşünelim.
<ol>
	<li>Yazı eklemek</li>
	<li>Yazıları düzenlemek (Yazi içeriğini, başlığını ve kategorisini görüntülemek)</li>
	<li>Yazıları silmek</li>
	<li>Yazılara eklenecek dosyaları yönetmek. Silmek ve düzenlemek.</li>
	<li>Tüm yazıların başlıklarının olduğu bir liste göstermek.</li>
	<li>Kategori eklemek, silmek, düzenlemek.</li>
	<li>Kategori içindeki yazıları göstermek</li>
	<li>Ayrıca yazı başlıklarını gösterirken, sayfalama yapmak, her sayfada 20 yazı göstermek, 2. sayfada bir sonraki 20 yazıyı yani 20 ile 40 arası yazıları göstermek</li>
	<li>Arama yapmak</li>
</ol>
Bu kadar basit bir sistemde bile ne kadar çok işlem var değil mi? Korkmayın, hepsini adım adım ilerleyerek öğreneceğiz.
<h2>Veri eklemek</h2>
İlk işimiz sisteme yazı eklemek. Ancak yazı eklemeden önce kategorileri oluşturmalıyız. Kategorilerimiz PHP, jQuery, SQL, Diğer olsun. Bunlardan ilk kategori olan PHP yi ekleyelim. Bu işlem için gereken SQL kodu şöyle:
<pre>INSERT INTO  `merakli`.`categories` (`id` ,`title`) VALUES (NULL ,  'PHP');
</pre>
Kodu incelediğimizde ID alanına bilgi olarak NULL, yani boş değer girdik. Çünkü veritabanı yönetim sistemi bu alanı bizim adımıza itinayla yönetiyor. AUTO INCREMENT özelliğinden dolayı id alanı otomatik artıyor. Bir satır silinse dahi o satırın id'si yeni eklenen veriye girilmiyor.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-18.51.24.png"><img class="alignnone size-full wp-image-645" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-18.51.24.png" alt="Screen Shot 2014-08-08 at 18.51.24" width="474" height="208" /></a>

Bu SQL kodunu phpMyAdmin üzerindeki SQL giriş bölümüne, girip çalıştırıyoruz, ve şöyle bi sonuç karşımıza çıkıyor.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-18.50.15.png"><img class="alignnone size-full wp-image-646" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-18.50.15.png" alt="Screen Shot 2014-08-08 at 18.50.15" width="474" height="484" /></a>

Gördüğümüz gibi, MySQL otomatik olarak 1 değerini id alanı için üretti. Şimdi de diğer kategorileri topluca giren kodu oluşturalım.
<pre>INSERT INTO  `merakli`.`categories` (`id` ,`title`) VALUES (NULL, 'jQuery'), (NULL, 'SQL'), (NULL, 'Diğer');
</pre>
İşte birden fazla değeri aynı tabloya parantez ve aralarında virgül kullanarak kolayca ekledik. Hepsini eklediğimizde ortaya çıkan sonuç şöyle:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-19.02.34.png"><img class="alignnone size-full wp-image-647" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-19.02.34.png" alt="Screen Shot 2014-08-08 at 19.02.34" width="359" height="127" /></a>

Gördüğümüz gibi tüm diğer kategoriler için id alanını, MySQL veritabanı yönetici programı otomatik olarak güncelledi.

Şimdi veri girişi yapmanın bir diğer yolunu, yani phpMyAdmin kullanarak giriş yapmayı deneyelim. Gireceğimiz veri bir yazı olsun ve PHP kategorisinde olsun. Ancak bir de ne görelim. Yazılar tablosuna yani posts içine içerik girmemize yarayacak içerik alanımız yok! Peki ne yapacağız? Tablo yapısını değiştirmemiz lazım:
<pre> ALTER TABLE  `posts` ADD  `content` TEXT NULL AFTER  `title`</pre>
Burada MySQL'e söylediğimiz şey, title yani başlık alanından sonra text (metin) tipinde content yani içerik alanı ekleyeceğiz ve NULL yani boş değer alabilir. NULL yani boş değer verdiğimizde hata vermesini ve satırı eklememesini isteseydik NOT NULL kuralını eklemeliydik.

Bunu yaptıktan sonra bir yazı ekleyelim. Bunu da phpMyAdmin Kullanarak şu şekilde yapabiliriz;

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-20.46.27.png"><img class="alignnone size-full wp-image-648" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-20.46.27.png" alt="Screen Shot 2014-08-08 at 20.46.27" width="474" height="302" /></a>

Yazıyı ekledikten sonra phpMyAdmin'de tablomuza baktığımızda son durum şu şekilde:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-20.52.45.png"><img class="alignnone size-full wp-image-649" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-08-at-20.52.45.png" alt="Screen Shot 2014-08-08 at 20.52.45" width="474" height="193" /></a>

&nbsp;

Dikkat! phpMyAdmin'in tabloya bakarken ürettiği koda dikkat ettiniz mi?
<h2>Verileri okumak, listelemek</h2>
<pre>SELECT * FROM  `posts` LIMIT 0 , 30
</pre>
Korkmak yok! Adım adım, parça pinçik bu kodu inceleyelim.
<ol>
	<li>SELECT: "Seç" demektir. Verinin sistemden çekileceğini belirtir.</li>
	<li>*: Tüm tablolar demektir. Eğer sadece title ve content alanlarını isteseydik, SELECT title,content demeliydik</li>
	<li>FROM: Hangi tablodan veri çekeceğimizi belirtir. Burada posts tablosundan veri çektiğimiz için FROM 'posts' yazmamız yeterli</li>
	<li>LIMIT: Sınırlamak demektir, burada 0 ile 30 id'si arasındaki satırları çekeceğimizi sisteme söyledik.</li>
</ol>
SELECT yani veri çekme ifadesinde başka önemli olan şeyler var. Bunları birtakım özel durumları inceleyerek açıklamaya çalışalım.
<ol>
	<li>WHERE: Yani koşul ifadesi, örneğin id'si 3 olan makaleyi sistemden çemek istersek SELECT * FROM posts WHERE id=3 dememiz gerek. Bence en önemli ifade bu veri çekerken.</li>
	<li>ASC/DESC: Örneğin fiyatları büyükten küçüğe ya da küçükten büyüğe sıralarken azalan artan koşulunu vermek için kullandığımız ifade. DESC azalarak yani büyükten küçüğe, ASC ise artarak yani küçükten büyüğe sıralamaya yarar.</li>
	<li>Bunun dışında ORDER BY, GROUP BY ifadeleri de mevcut ORDER BY ifadesi sıralama yaparken hangi alanı kullanacağımızı seçmeye yararken, GROUP by, bir alan seçtiğimizde o alanın aynı öğelerini gruplayarak tek bir satır elde etmemize yarar. Bu ifadeler biraz detay oldukları için girmiyorum. Zamanı geldiğinde kullanacağız zaten.</li>
</ol>
Dikkatimizi çekmesi gereken birşey daha var. Created ve Updated, yani yaratma ve güncelleme tarihlerini boş bıraktık. Bu alanlar null yani boş değer alabildikleri için, MySQL hata vermedi ancak, kendisi veritipine uygun birşekilde 0000-00-00 00:00:00 değerlerini üretip girdi.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.35.14.png"><img class="alignnone size-full wp-image-651" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.35.14.png" alt="Screen Shot 2014-08-09 at 13.35.14" width="258" height="65" /></a>

Buradaki alanı düzenlemeliyiz. Bunun için phpMyAdmin'de edit ikonuna tıklayalım.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.37.16.png"><img class="alignnone size-full wp-image-652" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.37.16.png" alt="Screen Shot 2014-08-09 at 13.37.16" width="474" height="71" /></a>

Kalem işaretine tıkladığımızda karşımıza satırı düzenleme ekranı çıkar.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.37.06.png"><img class="alignnone size-full wp-image-653" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.37.06.png" alt="Screen Shot 2014-08-09 at 13.37.06" width="474" height="304" /></a>

Düzenleme ekranında created ve updated alanlarının en sonundaki takvim ikonuna tıkladığımızda istediğimiz tarihi seçebiliriz.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.39.45.png"><img class="alignnone size-full wp-image-654" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.39.45.png" alt="Screen Shot 2014-08-09 at 13.39.45" width="474" height="301" /></a>

Buradan bugünün tarihini ve istediğimiz saati seçip Go butonuna basıp düzenleme işlemini tamamlayabiliriz. (İpucu olarak söyleyeyim, phpMyAdmin sistemi bu tarih seçme işlemleri için jQuery UI kütüphanesini kullanıyor.)

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.42.15.png"><img class="alignnone size-full wp-image-655" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-13.42.15.png" alt="Screen Shot 2014-08-09 at 13.42.15" width="461" height="564" /></a>

&nbsp;

İşte phpMyAdmin bir satırı otomatik olarak düzenledi ve gereken SQL kodunu da üretti.
<h2>Veriyi düzenlemek</h2>
Veriyi düzenlerken kullandığımız kodu adım adım inceleyelim.
<pre>UPDATE  `merakli`.`posts` SET  `created` =  '2014-08-09 00:00:00', `updated` =  '2014-08-09 00:00:00' WHERE  `posts`.`id` =1;
</pre>
UPDATE: Güncelle emrini sisteme veriyoruz. Her komuttan sonra MySQL bize soruyor: 'Neyi güncelleyeyim?' biz de yanına alan adını yazıyoruz. 'posts'. Burada farklı bir ifade dikkatinizi çekmiştir. Farklı veritabanlarından da sorgu çekebildiğimiz için veritabanı ismini de başa 'merakli'.'posts' diye yazmamız mümkün.

SET: Ayarla, emrini veriyoruz. MySQL yine soruyor. "Neyi ayarlayayım?" Biz de created alanını '2014-08-09 00:00:00', updated alaınını da '2014-08-09 00:00:00' yapmasını söylüyoruz. Nerde (WHERE) diyor. Biz de id alanının 1'e eşit olduğu satırı seç diyoruz. Bu kadar basit.
<h2>Veriyi silmek</h2>
Bu yazı için son olarak bu satırı silelim. Bunun için satırın başındaki delete ikonuna tıklayalım. Girilmez levhası şeklinde olan ikona. Buna bu kadar uyarı ikonları vs konmasının sebebi, yanlışlıkla sileceğiniz satırı geri getiremeyeceğinizden. <a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-14.08.05.png"><img class="alignnone size-full wp-image-656" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-14.08.05.png" alt="Screen Shot 2014-08-09 at 14.08.05" width="450" height="100" /></a>

Zaten tıkladığımız anda bir uyarı penceresi çıkıyor ve gerçekten silme işleminden emin olmadığmızı soruyor. Ki boş bulunup verimizi kaybetmeyelim.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-14.08.13.png"><img class="alignnone size-full wp-image-657" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-09-at-14.08.13.png" alt="Screen Shot 2014-08-09 at 14.08.13" width="474" height="239" /></a>
<pre>DELETE FROM posts WHERE id=1</pre>
Burada WHERE yani koşul ifadesinden sonra id=1 de diyebiliriz, ya da posts.id=1 diyerek alanın ait olduğu tabloyu da belirtebiliriz. Bu birden fazla tabloya aynı anda sorgu yapıyorsak, alan isimlerinin çakışmalarını önleyecektir.

Bu yazı için şimdilik bu kadar, veri girme, çekme, güncelleme, silme gibi en basit SQL işlemlerini öğrendik. Sıradaki yazıda içerik yönetim sistemimiz için ihtiyacımız olan işlemleri öğreneceğiz.