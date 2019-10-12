---
ID: 616
post_title: 'Veritabanı Nedir? SQL&#8217;e giriş &#8211; 1'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  http://www.meraklibilisimci.com/veritabani-nedir-sqle-giris-1/
published: true
post_date: 2014-07-14 20:25:52
---
Veritabanı nedir?

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/148624.jpg"><img class="alignnone size-full wp-image-628" src="http://meraklibilisimci.com/wp-content/uploads/2019/10/148624.jpg" alt="148624" width="474" height="265" /></a>

Gelin size mutlu sonla biten bir masal anlatayım. Eski hesap defterlerini hatırlar mısınız? Bunlardan en ünlüsü bakkal defteridir. Bakkal olduğumuzu düşünelim. Hangi bilgilere ihtiyacımız var? Müşterinin adı, telefonu, aldığı gofret, kola, gibi ürünler, şu anki borcu lazım. Üst satıra, bu bilgileri yazarız. Alt satırlara da müşterilerin kendi bilgilerini gireriz. Bilirsiniz değil mi? Defter kabolursa ne olur? Yanarız. Zaman geçti, bakkal defterlerinin yerini bilgisayarlar aldı. Hiç excel kullandınız mı? Bilgiler defterlerdeki gibi, satır ve sütunlarda yer alır, bunlar altalta yan yana toplanır. Bir çok işletme excel kullandı ve işlerini ilerletti. Fakat yeri geldi, bilgisayardaki binlerce ayrı ayrı excel dosyalarını yönetmek zorlaştı. Kimisi kayboldu, kimisini de kullanmak zordu. Binlerce satır veri arasından arama yapmak kolay değildi. Bu yüzden veritabanı adlı programlar geliştirildi. Belirli kurallara göre kolayca bilgiyi kaydeden, kolayca aramayı ve güncellemeyi sağlayan programlardı bunlar. Tabii herkes veritabanı kullanmayı bilmiyordu ve öğrenmesi de gerekmiyordu. Bu yüzden yazılımcılar, yani bizler, bu veritabanlarına bağlanacak, kolay bir arayüz olacak yazılımları geliştirdik. Bu sayede birçok insan bilgisayarları kullanır oldu. Kolayca bilgilerini bilgisayara yüklediler, ve ona kolayca eriştiler. PHP, MySQL, HTML5 ve Javascript sayesinde bu yazılımlar internete, yani “buluta” taşındılar, heryerden erişilebilir oldular ve güvenilir bir şekilde saklandılar. İnsanlar da yazılımcılar sayesinde sonsuza dek mutlu yaşadılar.

<a href="http://www.meraklibilisimci.com/wp-content/uploads/2019/10/db.png"><img class="alignnone wp-image-627 size-full" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/db.png" alt="db" width="474" height="525" /></a>

HMTL sayfalarının internette bilgiyi sabit bir şekilde tuttuklarını öğrenmiştik. PHP kullanarak bu bilgiler üzerinde değişiklikler, matematiksel işlemler yapabileceğimizi de gördük. Kullanıcıya saat, tarih gibi değişkenlere bağlı olarak değişen bilgileri iletebileceğimizi, kullanıcıdan formlar aracılığıyla aldığımız bilgiye göre, sayfamızdaki bilgileri değiştirebileceğimizi de anladık.

Peki ya yazılımımıza aldığımız bilgiyi kayıt etmek, daha sonra ihtiyaç duyduğumuzda tekrar kullanmak istediğimizde ne yapacağız? O zaman işte devreye veritabanları giriyor. Veritabanı bilgiyi saklamak ve belirli koşullara göre hızlıca geri getirmek için özelleşmiş yazılıma verilen isimdir.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/database1_s600x600.jpg"><img class="alignnone size-full wp-image-626" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/database1_s600x600.jpg" alt="database1_s600x600" width="400" height="300" /></a>

Peki neden aldığımız bilgiyi dosyaya direk yazmıyoruz da, veritabanı gibi bir aracı kullanıyoruz? Bunun nedeni, arama, kaydetme, bilgiyi geri getirme işlemlerini en hızlı ve bilgileri kaybetmeme garantisi ile geri getiren özelleşmiş yazılımlar kullanmanın, yazılımımızın güvenilirliğini artıracağıdır. Ayrıca yazının devamında anlatacağım SQL konusunda da neden veritabanına ihtiyaç duyduğumuzu daha iyi anlayacağız.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/mysql-big2.gif"><img class="alignnone size-full wp-image-625" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/mysql-big2.gif" alt="mysql-big2" width="425" height="283" /></a>

Bu zamana kadar yazılarımda, konuların teorik detayına inmeyi, okuyucunun merakına bırakarak, konuların mantığını kavratmaya ve hızlıca proje geliştirme yöntemini izledim. Bu konuyu da bu şekilde inceleyeceğim. Önce temel mantığı ve kavramları anlatacak, veritabanı mantığının yüzeysel bir şekilde anlaşılmasını sağlayacak ve asıl hedefimiz olan içerik yönetim sistemi için veritabanı geliştirme ve örnek veritabanımızı kurduktan sonra, sorgu ytapmayı öğrenceğiz. Şimdi gelelim ana kavramlara.

Genellikle yazılımlarımda kullandığım veritabanı MySQL. Açık kaynaklı, kullanım oranı yüksek, kullanıcı desteği ve bilgi olarak çok yaygın olan bir veritabanı olduğu için MySQL tercih ediyorum. MySQL'in yanı sıra, açık kaynaklı PostgreSQL, MariaDB yazılımları ve ticari olarak Oracle, MsSQL gibi veritabanları da mevcut. Bu veritabanları, ilişkisel olan ve SQL sorgulama dilini büyük oranda benzer lehçelerle kullanan veritabanlarıdır. SQL ne demeyin, geleceğiz. Bunların yanısıra, bu sıralar çok revaçta olan, İlişkisel olmayan veritabanları da mevcuttur. Bunlara kısaca No-SQL, yani SQL kullanmayan veritabanları da denir. Bu veritabanları doküman tabanlı veritabanlarıdır, yani ilişkisel değildirler. Amacınıza uygun olarak bu veritabanlarını da tercih edebilirsiniz, ancak bu tamamen ayrı bir yazı, hatta kitap konusu. Bu veritabanlarına örnek olarak MongoDB, Couchbase, vs. sayılabilir.

Basit bir şekilde akıl yürütelim. Hedefimiz içerik yönetim sistemi yazmak ve elimizde kayıt etmek istediğimiz bilgiler var. Bu bilgileri;
<ol>
 	<li>Kayıt edeceğiz (CREATE)</li>
 	<li>İhtiyaç duyduğumuzda geri getireceğiz (READ)</li>
 	<li>Değişiklik olduğunda güncelleyeceğiz (UPDATE)</li>
 	<li>Sileceğiz (DELETE)</li>
</ol>
Tüm bu işlemlere kısaca Oluştur (Create), Oku (Read), Güncelle (Update), Sil (Delete) kelimelerinin ingilizce baş harflerinden oluşan CRUD işlemleri denir. Genellikle yazılımlar bu işlemleri yapmaya yararlar.

Peki bu işlemleri nasıl yapacağız? SQL adı verilen, birçok yazılım için standart olan sorgulama dilini kullanarak. SQL, sorgulama dili aslında bir programlama dili değildir. Bu yüzden sorgulama dilidir. İngilizceye hakimseniz, anlşaılması ve kullanımı da çok kolaydır.

Başlıca SQL komutları, ingilizce kelimelerden oluşur. Biz ihtiyacımız olacak olan başlıcalarını listeleyelim. Daha sonra bu komutların nasıl kullanılacağını göreceğiz ve örneklerle destekleyeceğiz.
<ol>
 	<li>SELECT: SQL komutlarının en önemlisi, Türkçe:“Seç” anlamına gelir ve kaydedilmiş bilgiyi veritabanından okumaya yarar.</li>
 	<li>INSERT: “Ekle” demektir. Veritabanına bilgi eklememize yarar</li>
 	<li>UPDATE: “Güncelle” demektir. Veritabanında varolan bilgiyi güncellememize yarar.</li>
 	<li>DELETE: “Sil” demektir. Veritabanında varolan kaydı silmemize yarar.</li>
</ol>
Veritabanı yazılımında verilerimizi veritabanı adlı dosyalarda tuttuğumuzu belirtmiştik. Excel kullandıysanız bilirsiniz, farklı bilgileri farklı farklı excel dosyalarında tutarız. Bir excel dosyasında satır ve sütünlardan oluşan tablolar vardır. Veritabanları da bu excel dosyalarına benzer. İçlerinde farklı farklı tablolar vardır. Tablolar, satır ve sütunlardan oluşur. Excel'de ilk sütuna bilgilerin isimlerini yazarız. Excele geçen modern bir bakkal olduğumuzu düşünelim tablomuz şu şekilde olacak:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-07-11-at-08.42.57.png"><img class="alignnone size-full wp-image-622" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-07-11-at-08.42.57.png" alt="Screen Shot 2014-07-11 at 08.42.57" width="474" height="289" /></a>

Bir sürü müşterinin farklı bilgilerini binlerce ayrı dosyada tutmak zor. Artı iki milyon müşterinin kaydını tuttuğumuz düşünelim, o zama işte veritabanına ihtiyacımız var. Veriye anında ulaşıp, anında üzerinde değişiklik yapmak için.

Baştaki amacımızdan sapmayalım. Hedefimiz, içerik yönetim sistemi yazmak. Bunun için bir adet veritabanına, birkaç tabloya, bu tablo üzerinde alanlara, bu alanlar için veritiplerine ihtiyacımız var.

SQL sorgulama dili ile tüm bunları oluşturumamız için ihtiyaç duyduğumuz komutları da çok az ve çok kolay.
<ol>
 	<li>CREATE: “Yarat” anlamına geliyor. Akıl yürütürsek, veritabanı ve tablo yaratırken ihtiyaç duyacağımız komut budur.</li>
 	<li>ALTER: “Değiştir” anlamına gelir. Yarattığımız bi yapı üzerinde değişiklik yapmak istediğimizde bu komutu kullanacağız.</li>
 	<li>DROP: “Yoket” anlamaına geliyor. Yapıları yoketmek, istediğimizde bunu kullanırız.</li>
 	<li>TRUNCATE: “Boşalt” anlamına geliyor. Yapıları boşaltmak isterske bu komuta ihtiyacımız var.</li>
</ol>
Hedefimiz, içerik yönetim sistemi yani blog yazmak. Bunun için atmamız gereken ilk adım herşeyi ilk olarak aklımızda, mantıksal olarak modellemek, yapıları aklımızda kurmak, soru sormak, akıl yürütmek. İçerik yönetim sistemi için nelere ihtiyacımız var?
<ol>
 	<li>Yazı: Yazının yazıldığı tarihi bilmemiz gerekir ki, zaman göre sıralayalım, içeriği, kim tarafından yazıldığı, konusu</li>
 	<li>Resim ya da herhangi bir dosya, dosyanın bilgisayarda tutulduğu adres.</li>
</ol>
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/phpmyadmin-1351692685.png"><img class="alignnone size-full wp-image-624" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/phpmyadmin-1351692685.png" alt="phpmyadmin-1351692685" width="474" height="335" /></a>

En basit içerik yönetim sistemimiz için gerekli olan bilgiler bunlar. Birazdan bunları tek tek komutlarını sisteme gireceğiz. Ama önce MySQL programını ve PhpMyAdmin yazılımlarını yüklememiz gerekiyor ki, biz daha önce Xampp sunucusunu kurduğumuzda bu yazılımlar da sistemimize otomatik olarak yüklenmişti. Xampp'ı kurmadıysak kuralım. Kurduysak internet taraycımızı açıp, adres satırına 127.0.0.1 veya <a href="http://locallhost/">http://locallhost</a> yazalım.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-07-14-at-23.19.19.png"><img class="alignnone size-full wp-image-621" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-07-14-at-23.19.19.png" alt="Screen Shot 2014-07-14 at 23.19.19" width="474" height="347" /></a>

Bu işlemleri, tarayıcı yerine komut satırından MySQL programının kendisi ile de yapabiliriz. Ancak biz hızılca proje oluşturduğumuz için bu işleri phpMyAdmin'i kullanarak yapacağız.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/phpmyadmin-users.jpg"><img class="alignnone size-full wp-image-623" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/phpmyadmin-users.jpg" alt="phpmyadmin-users" width="474" height="339" /></a>

Devamı bir sonraki yazıda...

Kaynaklar:
<ol>
 	<li>http://en.wikipedia.org/wiki/Create,_read,_update_and_delete</li>
</ol>