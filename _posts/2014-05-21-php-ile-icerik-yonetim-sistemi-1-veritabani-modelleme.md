---
ID: 595
post_title: 'PHP ile içerik yönetim sistemi &#8211; 1 &#8211; Veritabanı Modelleme'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-1-veritabani-modelleme/
published: true
post_date: 2014-05-21 10:11:51
---
Bu zamana kadar hep statik siteleri nasıl yapacağımızdan bahsettik. Hazır içerik yönetimi sistemi olarak kendini kanıtlamış bir sistem olan wordpress'i konuştuk. Sıra geldi kendi içerik yönetim sistemimizi yazmaya.

<a style="color:#41a62a;" href="http://meraklibilisimci.com/wp-content/uploads/2018/10/how-cms-works-0.jpg"><img class="alignnone size-full wp-image-612" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/how-cms-works-0.jpg" alt="how-cms-works-0" width="474" height="320" /></a>

Bu sistemi önce OOP yani nesne yönelimli programlama ile yazacağız. Spagetti kodlamaya ise hiç girmeyeceğiz. Çünkü spaghetti kodlama çukurunda kalıp hiç kendini geliştirmeyen ve boktan kodlar üreten insanlar olmanızı istemiyorum. OOP başta zor gelebilir ama avantajlarını kullanmaya ve kodlarınıza bakım yapmanız gerektiğinde anlayacaksınız. Daha sonra ise CakePHP framework'e giriş yapacağız. MVC yapısının mantığını anlayarak işe başlayacağız. CakePHP'nin konsol uygulamasını kullanarak temel fonksiyonları içerek sınıfları otomatik üreteceğiz. Zaten birçok framework'te olan bu özellik, frameworklerin en güçlü yanlarından birini oluşturmakta.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/cake-logo.png"><img class="alignnone size-full wp-image-614" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/cake-logo.png" alt="Cake-logo" width="180" height="180" /></a>

En son olarak özel fonksiyonlarımızı yazacağız, kullanıcı girişi ve yönetimini ayarlayacağız ve görünümleri giydireceğiz. Ancak ilk yapmamız gereken şey her zamanki gibi, tüm yazılımlarımızda ilk atmamız gereken adım olan "Mantıksal Modelleme" kavramı.

Öncelikle içerik yönetim sisteminin nelerden oluştuğuna bakalım. İlk etapta sistem için en gerekli olan öğeleri ekleyeceğiz. Yani kullanıcı yönetimi, sosyal medya paylaşımı, video ekleme gibi şeyleri ikinci plana atıyoruz. İçerik yönetimini oluşturan elemanlar <strong>yazılar ve resimler</strong>. Aslında basit gibi dursa da içerik yönetim sistemimiz kullanıldıkça karmaşıklaşacak durumlar mevcut. Tek tek ele alalım.
<ol>
	<li>Yazıların içinde resimler olabilir</li>
	<li>Resimler bir araya gelip galerileri oluşturabilir</li>
	<li>Resimler aynı zamanda pdf, word dokümanı gibi dosyalardan da oluşabilir</li>
	<li>Yazılar ve resimler üst menüyü oluşturacak kategorilerin içinde yeralmak zorunda</li>
	<li>Bir kategoride birden fazla yazı varsa, blog gibi aşağıya gitmeli</li>
	<li>Bir kategoride birden fazla resim varsa ve yazıya dahil değilse galeri olarak görünmeli</li>
	<li>Galeri iki şekilde görünebilmeli. Birisi ızgara şeklinde resimler olarak, diğeri kayan resimler olarak.</li>
</ol>
Tespit ettiğimiz bu sorunlara çözüm olarak, veritabanında resimler yerine dosyalar tablosu tutacağız. Yazacağımız yazılım, dosyanın türüne göre görüntülemelerini farklı yapacak. Örneğin bir yazının içinde word, pfd, excel gibi dosyalar varsa, bunlar yazının altında ikon olarak görünecek.

Resim türündeki dosyalar yazının metninin içinde img etiketiyle görünmeli. Ayrıca veritabanından bağlanmamalı. Çünkü yazı düzenlendiği zaman resim silinirse veritabanından silinmeme durumu olabilir. Bu da veritabanında çöp veri birikmesine neden olur.

Görüldüğü gibi işler kolayca karmaşıklaşabiliyor. Bu yüzden biz de wordpress'teki gibi galeri, resim ve dosyaları yazıların içinde tutacağız. Resimler ve dosyalar için de bir ortam (media) yöneticisi oluşturacağız ki işler daha fazla karmaşıklaşmasın.

İlk önce yazı gireceğiz. Yazı girerken yazının içine resim ekleyebiliriz. Bunu eklerken ortam yöneticisi açılmalı, ortam yöneticisine yüklemeyi yapmalıyız, daha sonra da istersek yazıya bu resmin img etiketini ekleyebiliriz. Dosyaları da aynı şekilde yazıya ekleyebiliriz ancak onlar img etiketi ile değil, link olarak veya dosya ikonu olarak görünebilir.

Her metin ve ortamın, hangi tarihte eklendiğini sistemde tutmamız gerekiyor ki, zaman bağlı sıralayabilelim. Ayrıca güncellendiği tarihi de tutabiliriz. Kullanıcı yönetimimiz henüz yok. Fakat kullanıcı yönetimini sisteme girdiğimizde içeriklerin hangi kullanıcı tarafından eklendiğini de sistemde tutmamız lazım. Ayrıca kullanıcı yönetiminde admin yani yönetici, yazar ve yorumcu gibi görevler de olabilir. Ayrıca bir sonraki aşamada yorumlar tablosuna da ihtiyacımız olacak. Tablolarda kategoriler listesi de tutmalıyız. Bu kategorilerin üst ve alt menüleri de olabilir. Bu menüleri görüntülemek için ben superfish kullanıyorum. Her sayfa gösteriminde menüleri veriatabanından çekmemek ve veritabanına yük olmamak için cache adı verilen daha hızlı kayıt ortamlarını da kullanabiliriz, ama şimdilk bu da ikinci aşamaya kalsın.

Veritabanını modellemek için MySQL Workbench programını kullanacağız. MySQL Workbench görsel olarak veritabanını oluşturmamızı ve yönetmemizi sağlayan, görsel diyagramlardan SQL kodu üretmemizi, veritabanından da görsel diyagram üretmemizi sağlayan program.

Oluşturacağımız en temel veritabanı modeli için gerekli olan 3 tane tablomuz var. Posts, Files ve Categories. Tablo isimlerimiz ingilizce ve çoğul olmak zorunda çünkü CakePHP'nin kod üretme aracı veriatabını bu şekilde tabıyıp kod üretebiliyor.

Öncelikle MySQL Workbench programını açalım. Karşımıza şöyle bi ekran gelecek:<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.42.png"><img class="alignright size-full wp-image-605" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.42.png" alt="Screen Shot 2014-05-21 at 12.14.42" width="474" height="524" /></a>

Modelin yanındaki + işaretine basarak yeni bir model oluşturmamız gerekiyor. <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.29.png"><img class="alignright size-full wp-image-606" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.29.png" alt="Screen Shot 2014-05-21 at 12.14.29" width="474" height="488" /></a>

Modelimizin şema ismine şimdilik "merakli" dedik fakat oluşturacağımız SQL kodunda buna ihtiyacımız olmayacak. Daha sonra üst taraftaki add diagram ikonuna tıklayarak görsel modelleme ekranını açmamız gerekiyor.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.11.png"><img class="alignright size-full wp-image-607" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.11.png" alt="Screen Shot 2014-05-21 at 12.14.11" width="474" height="555" /></a>

Bu ekran açıldığında sağ tarafta <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.40.59.png"><img class="alignnone size-full wp-image-609" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.40.59.png" alt="Screen Shot 2014-05-21 at 12.40.59" width="25" height="25" /></a> ikonuna tıklayarak veya klavyeden "T" harfine basarak karelerle oluşan görsel ekranımıza bir table yerleştirelim.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.11.png"><img class="alignnone size-full wp-image-607" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.14.11.png" alt="Screen Shot 2014-05-21 at 12.14.11" width="474" height="555" /></a>

Yerleştirdiğimiz tablonun boyunu büyüttük ve sıra geldi alanları eklemeye. İlk olarak Aşağıdaki column table yazan yere çift tıklayalım ve ilk index alanımızı oluşturalım. Bu alanın adı id olmak zorunda. Alanlarımızın PK, NN, UQ, BIN, UN, ZF ve AI gibi seçenekleri olduğunu göreceksiniz. Bütün ID alanları AI yani auto increment yani sırayla artan eşsiz (unique) bir numaraya sahip olmak zorunda. Bu nedenle AI'yi işaretleyelim. Bunu her seferinde işaretlemeliyiz çünkü, MySQL Workbench otomatik olarak ilk alan için PK(primary key "birincil anahtar") ve NN(Not null "Alan boş olamaz") seçeneklerini işaretlese de AI'yi işaretlemiyor. Biz her tabloya id alanımızı girdiğimizde bunu tekrar işaretlemeliyiz.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.16.23.png"><img class="alignnone size-full wp-image-604" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.16.23.png" alt="Screen Shot 2014-05-21 at 12.16.23" width="474" height="644" /></a>burada AI'nin işaretli olması gerekiyor. Şimdi sırasıyla oluşturduğumuz alanlara bakalım.
<ol>
	<li>id: Birincil alan. Eşsiz ve her eklemeyla artan bir numaraya sahip. Boş olamaz.</li>
	<li>title: Başlık. 255 adet karakter alabiliyor. Boş olamaz. CakePHP bu alanı otomatik olarak tanıyor ve kodu buna göre üretiyor. CakePHP'de farklı isimli başlık kullanmak istersek model içinde $displayField değişkeni tanımlamalıyız ancak şu an temel seviyedeyiz.</li>
	<li>category_id: Yazının ait olduğu kategori'nin id'si. Karşı tablonun tekil ismi ve id yazdığımızda cakePHP'nin kod üreteci bu tablolar arasındaki ilişkiyi otomatik olarak algılıyor. Boş olamaz. Bu alan sayesinde bir kategorinin birden fazla yazıya sahip olabileceği ancak bir yazının sadece bir kategoriye ait olabileceği ilişkisel kuralını tanımlamış oluyoruz.</li>
	<li>created ve updated: Yazının eklendiği ve güncellendiği tarih. Bu alanı da cakePHP otomatik olarak tanıyor ve kendisi güncelliyor.</li>
</ol>
Diğer tabloları da aynı şeyleri gözeterek oluşturuyoruz.<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.26.46.png"><img class="alignnone size-full wp-image-602" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.26.46.png" alt="Screen Shot 2014-05-21 at 12.26.46" width="474" height="200" /></a>

Sonuç olarak elimizde 3 adet tablodan oluşan basit bir veritabanı var. Modellemeye ilk aşamada ne kadar fazla dikkat edersek, daha sonra işimiz kolaylaşır ve işlerin karışmasını ve modelleme fazına tekrar dönmemizi önlemiş oluruz.

<img class="alignnone size-full wp-image-603" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.26.38.png" alt="Screen Shot 2014-05-21 at 12.26.38" width="474" height="367" />

MySQL Workbenchin database menüsüne tıklayalım. Forward engineer ile kodumuzu oluşturalım. Biz MySQL Workbenchden veritabanına bağlanmayacağız ancak bağlantımız olması ve MySQL'in bilgisayarımızda kurulu olması gerekiyor. Forward engineer'den ileri ileri diyelim ve database bağlantı bilgilerimizi girelim. <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.27.37.png"><img class="alignnone size-full wp-image-601" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.27.37.png" alt="Screen Shot 2014-05-21 at 12.27.37" width="474" height="339" /></a>

Program bize gerekli sql kodunu üretecek. İstediğimiz bir text editör doyasını açalım ve

CREATE SCHEMA IF NOT EXISTS `merakli` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci ;
USE `merakli` ;

kısmını ve bütün  `merakli`  kelimelerini silelim.<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.28.28.png"><img class="alignnone size-full wp-image-599" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.28.28.png" alt="Screen Shot 2014-05-21 at 12.28.28" width="474" height="237" /></a> <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.28.15.png"><img class="alignnone size-full wp-image-600" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.28.15.png" alt="Screen Shot 2014-05-21 at 12.28.15" width="474" height="332" /></a>

daha sonra phpmyadmin programını açıp veritabanımızı oluşturalım. Veritabanimizin adı örneğin 'merakli' olsun. Karakter sınıfı olarak da "utf8_turkish_ci" seçelim.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-13.04.06.png"><img class="alignnone size-full wp-image-610" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-13.04.06.png" alt="Screen Shot 2014-05-21 at 13.04.06" width="474" height="201" /></a>

Veritabanımız oluştuktan sonra, temizlediğimiz sql kodunu, phpmyadmin'de üst menüde SQL yazan menüye tıkladımızda ortaya çıkan metin bölümüne yapıştıralım ve 'GO' diyerek çalıştıralım.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.29.38.png"><img class="alignnone size-full wp-image-597" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.29.38.png" alt="Screen Shot 2014-05-21 at 12.29.38" width="474" height="338" /></a>

&nbsp;

Kodu çalıştırdığımızda veritabanımızda artık istediğimiz tabloları eklemiş olduk:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.29.53.png"><img class="alignnone size-full wp-image-596" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-05-21-at-12.29.53.png" alt="Screen Shot 2014-05-21 at 12.29.53" width="474" height="251" /></a>

Bir sonraki yazıda Nesne Yönelimli Programlama metodları kullanarak içerik yönetim sistemimizi oluşturmaya başlayacağız.

Kaynaklar:
<ol>
	<li><a href="http://www.mysql.com/products/workbench/">http://www.mysql.com/products/workbench/</a></li>
	<li><a href="http://www.iainbenson.com/programming/icms/">http://www.iainbenson.com/programming/icms/</a></li>
	<li><a href="http://www.inqbation.com/how-cms-works/">http://www.inqbation.com/how-cms-works/</a></li>
	<li><a href="http://www.webdesignviews.com/2011/05/history-of-open-source-content-management-systems/">http://www.webdesignviews.com/2011/05/history-of-open-source-content-management-systems/</a></li>
	<li><a href="http://www.rocketmill.co.uk/cakephp-and-mysql-workbench-how-to-make-them-work-together">http://www.rocketmill.co.uk/cakephp-and-mysql-workbench-how-to-make-them-work-together</a></li>
	<li><a href="http://book.cakephp.org/2.0/en/tutorials-and-examples/blog/blog.html%20">http://book.cakephp.org/2.0/en/tutorials-and-examples/blog/blog.html </a></li>
	<li><a href="http://alvinalexander.com/php/cakephp-cheat-sheet-reference-page-examples">http://alvinalexander.com/php/cakephp-cheat-sheet-reference-page-examples</a></li>
	<li><a href="http://technet.weblineindia.com/web/cakephp-naming-convention-standard/">http://technet.weblineindia.com/web/cakephp-naming-convention-standard/</a></li>
</ol>