---
ID: 665
post_title: >
  Temel SQL serisi, SON SQL-5 Sayfalama ve
  Arama işlemleri
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/temel-sql-serisi-son-sql-5-sayfalama-ve-arama-islemleri/
published: true
post_date: 2014-08-18 12:44:58
---
Bir sürü şeyi hallettik. Veri ekleme, düzenleme, güncelleme ve silme. Bir de birleştirme. Geriye ne kaldı? Görelim bakalım..
<ol>
 	<li>Tüm yazıların başlıklarının olduğu bir liste göstermek.</li>
 	<li>Kategori eklemek, silmek, düzenlemek.</li>
 	<li>Kategori içindeki yazıları göstermek</li>
 	<li>Ayrıca yazı başlıklarını gösterirken, sayfalama yapmak, her sayfada 20 yazı göstermek, 2. sayfada bir sonraki 20 yazıyı yani 20 ile 40 arası yazıları göstermek</li>
 	<li>Arama yapmak</li>
</ol>
Başlık listesi görüntülememek de çok kolay.
<pre>SELECT title FROM posts;
</pre>
Bu komutu yazdığımız zaman Girdilerden sadece başlıkların olduğu listeyi çekebiliyoruz. 2. maddedeki ekleme, silme, düzenleme işlemlerinden zaten bahsetmiştik. Kategori içindeki yazıları da verileri birleştirerek alıyoruz. Bunu da bir önceki yazıda hallettik.
<h2>Sayfalama</h2>
Sayfalama dediğimiz olay, örneğin 1 milyon makale olan bir internet sitesinde, hiçbir kısıtlama olmadan "SELECT * FROM posts" dersek, hem kullanıcı bir milyon makalenin inmesini bekler, hem de bu veriyi çeken yazılım da belirli bir süre sonra timeout olur, yani sonsuza dek sistemin bu işleme kilitlenmesini engellemek için konulan zaman ve bellek sınırına ulaşacağı için veri çekme işlemi yarım kalır. Bu nedenle basit bir mantıkla, ne kadar veri çekeceğimizi LIMIT ifadesiyle sisteme söyleyeceğiz.
<pre>SELECT * FROM `posts` ORDER BY 'created' DESC LIMIT 0,20;</pre>
Komutumuzu inceleyelim:
<ol>
 	<li>SELECT: Seç ifadesiyle * diyerek tüm alanları istediğimizi ve FROM posts diyerek girdiler tablosundan tüm verileri çekiyoruz</li>
 	<li>ORDER BY ifadesiyle 'created' yani, oluşturma tarihine göre veriyi sıralamak istediğimizi yazdık.</li>
 	<li>DESC ifadesiyle Descending yani azalarak en yeniden en eskiye göre verilerin çekilmesini istediğimizi belirttik, Ascending ASC yani artarak deseydiki, ilk gelen veri en eski veri olacaktı.</li>
 	<li>LIMIT 0,20 diyerek gelen verilerin ilk 20 adedini istediğimizi söyledik.</li>
 	<li>2. Sayfaya gitmek isteseydik, LIMIT, 20, 40 dememiz gerekiyordu. Bu şekilde 100 kaydımız varsa, her sayfada 20 adet veri çekerek, tek sayfada 100 girdi göstermek yerine, 5 adet sayfada 20'şer girdi gösterdik ki, kullanıcıların internet kotalarını doldurmayalım ve verinin yüklenmesini beklerken sıkılıp sistemimizden çıkmasınlar.</li>
</ol>
<h2>Arama</h2>
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-18-15.15.54.png"><img class="alignnone size-full wp-image-667" src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-18-15.15.54.png" alt="Ekran Resmi 2014-08-18 15.15.54" width="474" height="217" /></a>

Sitelerde genelde gördüğümüz arama formları nasıl yapılıyor? Örneğin, başlıklar içinde, veya yazıda geçen bir kelimeyi nasıl ararız? Bunun bi kolay yöntemi var bir de daha profesyonel yöntemi. Biz kolay yönteminden başlayacağız.
<pre>SELECT title FROM categories WHERE title LIKE '%php%';</pre>
Kodu her zaman yaptığımız gibi, phpMyAdmin'in veritabanı seçtikten sonra gelen SQL menüsüne yapıştırıp, GO diyerek çalıştıralım.

<a href="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-18-15.23.37.png"><img class="alignnone size-medium wp-image-670" src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-18-15.23.32.png?w=300" alt="Ekran Resmi 2014-08-18 15.23.32" width="300" height="199" /></a>

<a href="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-18-15.23.37.png"><img class="alignnone size-medium wp-image-669" src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-18-15.23.37.png?w=300" alt="Ekran Resmi 2014-08-18 15.23.37" width="300" height="236" /></a>

Kodu her zaman yaptığımız gibi adım adım inceleyelim
<ol>
 	<li>SELECT title FROM categories: Her zamanki veri çekme kodumuz, kategoriler tablosundan title yani başlık alanını çektik.</li>
 	<li>WHERE title LIKE '%php%'; Koşul ifadelerini biliyoruz. Burada LIKE, gibi demek. Yani title='php' deseydik, değeri 'php' ye eşit olan veri satırını alacaktık. Ancak burada LIKE dediğimiz için ve % işaretini kullandığımız için, php'den farklı olan verileri de getirecek. Sadece LIKE '%php' kullansaydık, sonunda php geçen tüm ifadeleri bulacaktı, 'herkes için php' gibi. Ancak 'php hakkında herşey ifadesini bulamayacaktı.'</li>
 	<li>sadece 'php hakkında herşey' örneğinde olduğu gibi 'php' ifadesiyle başlayan bütün verileri çekmek isteseydik, LIKE 'php%' kullanmamız gerekirdi.</li>
 	<li>php ifadesinin başında ve sonunda ne olduğu önemli değil, içinde php geçen tüm ifadeleri aramak istediğimiz için komutumuzda LIKE '%php%' ifadesini kullandık.</li>
</ol>
Son olarak like ile arama yavaş olduğundan ve verilerimiz çok uzun ise daha etkili bir yöntem olarak FULL-TEXT SEARCH, yani tam metin arama kullanabiliriz. Bunun için arama yapacağımız alanlara text index vermemiz gerekiyor.
<pre>ALTER TABLE categories ADD FULLTEXT( title );</pre>
Bu işlemi yaptıktan sonra arama işlemimizi şu şekilde yapmamız gerekir:
<pre>SELECT title FROM categories WHERE MATCH(title) AGAINST ('PHP')</pre>
Bu yöntem büyük verilerle çalışırken daha hızlı. Ancak veritabanımızı oluştururken myISAM tipinde oluşturmamız gerekiyor.

Bu yazı serisinde temel SQL ve mySQL bilgilerini öğrendik. Artık temel veritabanı bilgisine sahipsiniz. Her zaman yaptığımız gibi, kullanım klavuzu kafasında kafamızı zor şeylerle karıştırmadan bebek adımlarıyla önce mantığını anlatmaya çalıştık. Detaylara inmeyi projelerinizde sizlere bıraktım.

Daha ileri konuları araştırmak isterseniz:
<ol>
 	<li>Veritabanı fonksiyonları, SUM(), COUNT(), CONCATENATE() gibi.</li>
 	<li>VIEW yaratarak kullanıcıların veritabanını bozmasını engellemek.</li>
 	<li>Stored procedure, yani kayıtlı fonksiyon üretme, TRIGGER oluşturma, oracle'da PL/SQL diline benzer</li>
 	<li>Veritabanı motorları, InnoDB ve MyISAM arasındaki farklar</li>
 	<li>Uzaktaki anahtarlar, FOREIGN KEY, CASCADE  ON UPDATE, CASCADE ON DELETE gibi işlemler</li>
 	<li>Veritabanı performansını artırma, sorgu iyileştirme</li>
 	<li>Veritabanına farklı kaynaklardan veri çekme, .CSV veya MsSQL gibi</li>
 	<li>SQLite gibi basit, PostgreSQL gibi ileri düzey veritabanları</li>
 	<li>Doküman tabanlı NoSQL veritabanları</li>
</ol>
Bunlar gibi ileri düzey konuları, sistemlerinizde ihtiyaç duydukça araştırıp kullanacaksınız.

Şimdilik bu kadar. Hep meraklı olun, meraklı kalın.

Kaynaklar:
<ol>
 	<li><a href="http://php.net/manual/tr/intro-whatis.php">http://php.net/manual/tr/intro-whatis.php</a></li>
 	<li><a href="http://www.cemdemir.net/jquery/jquery-nedir-nasil-kullanilir-nasil-ogrenilir-465.html">http://www.cemdemir.net/jquery/jquery-nedir-nasil-kullanilir-nasil-ogrenilir-465.html</a></li>
 	<li><a href="http://stackoverflow.com/questions/759580/how-to-implement-a-keyword-search-in-mysql">http://stackoverflow.com/questions/759580/how-to-implement-a-keyword-search-in-mysql</a></li>
 	<li><a href="http://devzone.zend.com/26/using-mysql-full-text-searching/">http://devzone.zend.com/26/using-mysql-full-text-searching/</a></li>
 	<li><a href="http://dev.mysql.com/doc/refman/5.0/en/faqs-stored-procs.html">http://dev.mysql.com/doc/refman/5.0/en/faqs-stored-procs.html</a></li>
 	<li><a href="http://www.bakale.com/mysql/myfultext.htm">http://www.bakale.com/mysql/myfultext.htm</a> BUNA DIKKAT</li>
</ol>