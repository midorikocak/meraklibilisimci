---
ID: 48
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-3
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-3/
published: true
post_date: 2017-02-13 10:02:27
---


<p>Bu yazı daha önce yazdığım <a href="https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-2-fa6aa74b93f3#.hto259cwr" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-2</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-2-fa6aa74b93f3[/embed]
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/2d9b3-1ca-_tymsuba5y_a7mciozg.jpeg">

<figcaption class="wp-caption-text">Nasıl kullanacağımızı şekliyle anlayan bir nesne</figcaption></figure><h4>Nesneyi Kullanmak ve Arayüz Kavramı</h4>
<p>Daha önce information hiding, yani bilgi gizleme kavramından bahsederken şöyle demiştik:</p>
<blockquote>araba kullanırken, motorun, katalitik konvertörün, alternatörün o anda ne yaptığı ile ilgilenmiyoruz. Araç kullanıcısı olarak bizim amacımız bir yerden bir yere gitmek, ve bunu aracın direksiyonunu, vitesini, pedallarını vb. kullanarak gerçekleştiriyoruz.</blockquote>
<p>Eğer araba kullanmayı biliyorsak, her türlü arabayı kullanabiliriz. Çünkü otomobiller üretilirken belirli standartlara uyularak üretilmekte. Çok fütüristik değilse, bir aracın, direksiyonunun, vitesliyse debriyajının gaz pedalının, sinyal kolunun vb. olduğunu önceden tahmin ediyoruz, çünkü daha önce sürücü kursunda öğrendiğimiz ve hayatımızda gördüğümüz tüm otomobillerden edindiğimiz tecrübe bilgisiyle böyle bir beklenti oluşturduk.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/00592-1ipqgbpczja7fdnybf5fevq.jpeg">

<figcaption class="wp-caption-text">Bu ne ki şimdi?</figcaption></figure><p>Yani mesela bir otomobilde, vites sağ alt köşe yerine tavandaysa şaşırıp kalırız, ya da İngiltere’deysek bindiğimiz bir arabada direksiyonun solda değil sağda olması, önce bir alışma ve eğitim süresi gerektirir. (Ki İngiltere’de bu yüzden kiraladığım arabanın dikiz aynasını kırmışlığım var. Neyse ki kiralarken ek sigorta almıştım)</p>
<h4>Ergonomi</h4>
<p>Örneğin binlerce yıldır oturmuş çatal kaşık tasarımına baktığımızda, şeklinin insan eline oturacak şekilde tasarlandığını görürüz. Bu sayede ne işe yaradığını ve nasıl kullanılacağını bilmesek de, kaşığı sapından tutup, ucundaki çukurla bişiler yapabileceğimiz deneyerek tahmin ederiz. Bu sayede bebekler çatal kaşık kullanmayı kolayca öğrenebilirler. Burada kaşığın görevi, onun şeklini belirliyor. Kullanılan nesnelerin insanın verimli ve sağlıklı bir şekilde kullanabileceği şekilde üretilmesine, genel olarak ergonomi deniyor. Biz de tasarlayacağımız yazılımlarda insanların bu beklentilerine göre hareket edersek, insanları sıkıntıya sokan, delirten ve mutsuz eden yazılımlar yerine, onların sağlıklı bir şekilde kolayca kullanıp anlayabileceği şeyler üretmiş oluruz. <a href="http://blog.leapmotion.com/what-makes-a-spoon-a-spoon-form-and-function-in-vr-industrial-design/" target="_blank">Kaynak 1</a> <a href="http://www.ergonomi.itu.edu.tr/ergonomi.html" target="_blank">Kaynak 2</a></p>
<h4>Arayüz</h4>
<p>Otomobillerdeki, otomobili rahatça kullanmamızı sağlayan bu yapıya arayüz deniyor. İşte tüm otomobillerde standart olan örneğin vites, direksiyon gibi yapıların standart büyüklükte olması, bu standart arayüzün ortak bir şekilde tüm otomobiller tarafından paylaşılmasından kaynaklanıyor. Ayrıca biz otomobili kullanırken, katalitik konvertörün o anki sıcaklığını sürekli düzenlemek ve gözetmek zorunda değiliz. İşte Arayüz aynı zamanda bizim için gözümüzden gereksiz detayları kaldırıyor. Sınıfımızın yapacaklarına karar verdiğimiz ve tasarımını yaparken yazdığımız kullanıcı tarafından public metodların kümesine <strong>Arayüz (interface)</strong>, sınıf içindeki bir metodun alacağı parametrelerin sayısına, veri tiplerine ve döndürmesi gereken değerin veri tipine de M<strong>etodun İmzası (signature) </strong>deniyor. Arayüz kavramının detaylarına birden fazla sınıf ortak davranışı paylaşmak durumunda olduğunda tekrar detaylı olarak geri döneceğiz</p>
<h4>Sınıfımızı yazmaya devam edelim</h4>
<p>Önceki yazıda yazdığımız Dictionary Sınıfının başlık oluşturma ve değiştirme, nesneyi adam gibi yaratma işlerini güzelce halletmiştik. Şimdi nesnenin asıl görevlerini gerçekleştiren kodları yazmamız gerekiyor. Bunlar şu işlemlerden oluşuyordu;</p>
<ol>
<li>Sözlüğe bir başlık girmek.</li>
<li>Başlık içeriğini güncellemek.</li>
<li>Başlığı silmek</li>
<li>Arama, sıralama ve filtreleme yapabilmek</li>
<li>Veriyi bir dosyaya kaydedip yeniden kullanabilmek.</li>
</ol>
<p>Sırayla ilerleyeceğiz. Şimdilik konunun basit anlaşılması için, başlıkları Dictionary nesnesinde bulunan $entries adlı diziye başlık adını anahtar olarak kullanarak ekleyeceğiz. Başımıza bela olacak sorunlara önceden önlem olmaya çalışacağız ki, daha sonra ağlamayalım.</p>
<h4>Dizi üzerinde belalı işlemler</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/5bde7-1lr8iorfuxjfbhoeptbrtkg.jpeg">

<figcaption class="wp-caption-text">Yımırta</figcaption></figure><p>PHP’de array yani diziler, veriler üzerinde işlemler yapmamızı sağlayan güzel yapılardır. Şimdi henüz sınıfımıza eklemeden bir dizi üzerinde nasıl işlem yapabileceğimize bakalım. Proje dizinimiz içerisinde array.php isminde bir dosya oluşturup tarayıcı üzerinden çalıştıralım.</p>
<pre><strong>&lt;?php<br><br></strong>$entries = [];<br>$entries[<strong>'nesne'</strong>] = <strong>'Sınıf Örneği'</strong>;<br><strong>echo </strong>$entries[<strong>'nesne'</strong>];</pre>
<p>Tarayıcıyı açtığımızda şöyle bir sonuç göreceğiz:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/9b0e8-1yxcyz4lqqmvcpt4e2mauug.png">

<figcaption class="wp-caption-text">Dizide işlem</figcaption></figure><p>Hazırda bilgisayarınızda PHP yorumlayıcısı yoksa, bu minik koda şuradan da erişebilirsiniz: <a href="https://3v4l.org/CPsXm" target="_blank">https://3v4l.org/CPsXm</a> Bu sitede bilgisayarını mahvetmeden, herhangi bir yerden istediğiniz PHP kodunu test edebilirsiniz. Öneririm.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/4984c-1hr0foidrqhxql8xefcmnyg.png">
</figure><p>Burada diziye bir anahtar atadık ve o anahtar içindeki değeri çağırdık. Peki dizide olmayan bir değeri çağırırsak ne olur? Görelim:</p>
<p>Kodu şu şekilde değiştirelim:</p>
<pre><strong>&lt;?php<br><br></strong>$entries = [];<br>$entries[<strong>'nesne'</strong>] = <strong>'Sınıf Örneği'</strong>;<br><strong>echo </strong>$entries[<strong>'şey'</strong>];</pre>
<p>Şöyle bir görüntüyle karşılaşacağız.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/56bac-1x_ad09z04pzhsquyl2o-iq.png">

<figcaption class="wp-caption-text">E yok ki.</figcaption></figure><p>Notice yani bildirim ifadesi burda kodumuzun çalışmasının durmadığını ama ileride başımıza belalar açılacağını bildiriyor.</p>
<p>Aklımıza şöyle sorular gelmesi gerekiyor:</p>
<ol>
<li>Eklemek istediğimiz başlık sözlükte yoksa ve çağırdıysak bu sorunu bildirim göstermeden nasıl hallederiz?</li>
<li>Başlık zaten varsa ve değiştirmek istemiyorsak, aynı başlığa yeni bir açıklama değerini nasıl ekleriz?</li>
<li>Bir başlığı silmek ya da düzenlemek istediğimizde ve başlıkta birden fazla açıklama varsa, tüm açıklamalara mı etki edeceğiz yoksa sadece birine mi?</li>
<li>Bir başlığa, tarih bilgisini nasıl girebiliriz? Bu tarih bilgisine dayanarak nasıl sıralama işlemi yapabiliriz?</li>
<li>Arama, filtreleme işlerini nasıl yapacağız?</li>
</ol>
<p>Gördüğümüz gibi iş şimdiden boka sarmaya başladı. Sorunu spagetti bir fonksiyonla çözmeye çalışalım:</p>
<pre><strong>&lt;?php<br><br>function </strong>getEntry(string $title){<br><strong>if</strong>(!<strong>isset</strong>($entries[$title])){<br><strong>return </strong>$entries[$title];<br>    }<br>}<br><br>$entries = [];<br>$entries[<strong>'nesne'</strong>] = <strong>'Sınıf Örneği'</strong>;<br><br><strong>echo </strong>getEntry(<strong>'nesne'</strong>).<strong>"&lt;br&gt;"</strong>;<br><br>$entries[<strong>'şey'</strong>] = <strong>'İsimsiz nesne'</strong>;<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>).<strong>"&lt;br&gt;"</strong>;<br><br><em>print_r</em>($entries);<br><br>$entries[<strong>'şey'</strong>] = <strong>null</strong>;<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>).<strong>"&lt;br&gt;"</strong>;<br><br><em>print_r</em>($entries);</pre>
<p>getEntry metodundan sonraki “<strong>&lt;br&gt;</strong>” ifadesine takılmayın. Fonksiyondan dönen metin değeri ile “<strong>&lt;br&gt;</strong>” yani alt satır etiketini birleştirdik. Şöyle hatalarla karşılaşacağız.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/75bbf-1anyvbqy8fe6mkpx5ppd1gw.png">
</figure><p>Fonksiyonumuz çalışmıyor çünkü global olarak tanımlanmış $entries adlı değişkene erişemiyor. PHP’de ve birçok C benzeri dilde {} süslü parantezlerle ayrılmış kodlara blok deniyor, ve bloklardaki kodlar, sadece bu blok içinde tanımlanmış değerlere erişebiliyor. (Kapsam yani Scope kavramı) Bunu geçici olarak çözmenin yolu var ama kötü pratik olduğundan ve tüm güvenlik önlemlerini mahvettiğinden anlatmıyorum bile. İşi yanlış yapmayı değil doğru yapmayı öğrenmemiz gerek.</p>
<p>Bunu geçici olarak spagetti kodunda şu şekilde çözebiliriz. getEntry metodunda üzerinde işlem yapacağımız diziyi parametre olarak gireceğiz.</p>
<pre><strong>&lt;?php<br><br>function </strong>getEntry(string $title, <strong>array </strong>$array){<br><strong>if</strong>(<strong>isset</strong>($array[$title])){<br><strong>return </strong>$title.<strong>' ifadesinin değeri: '</strong>.$array[$title].'&lt;br&gt;';<br>    }<br>}<br><br>$entries = [];<br>$entries[<strong>'nesne'</strong>] = <strong>'Sınıf Örneği'</strong>;<br><br><strong>echo </strong>getEntry(<strong>'nesne'</strong>, $entries);<br><br>$entries[<strong>'şey'</strong>] = <strong>'İsimsiz nesne'</strong>;<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>, $entries);<br><br><em>print_r</em>($entries);<br><br>$entries[<strong>'şey'</strong>] = <strong>null</strong>;<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>, $entries);<br><br><em>print_r</em>($entries);</pre>
<p>Satır satır kodu inceleyelim.</p>
<ol>
<li>array $array diyerek, fonksiyonumuzun kapsam yanı scope’sinin içine işlem yapacağmız diziyi kopyaladık. Eğer kopyalamak yerine diziye doğrudan erişmek ve değişiklik yapmak isteseydik &amp;$array dememiz gerekiyordu. Buna Call by Reference yani Referans ile çağırma deniyor. Şimdilik bunun detayına girmeyeceğim.</li>
<li>Fonskiyonumuzun değer döndürüp döndürmediğini anlamak için dönen değeri $title.’ ifadesinin değeri: ‘.$array[$title].’&lt;br&gt;’; olarak değiştirdik.</li>
<li>Fonksiyonu her çağırdığımızda birleştirdiğimi ‘&lt;br&gt;’ ifadesini direk fonskiyonun içine yazdık ve kod tekrarını önledik.</li>
<li>fonksiyon içinde isset kullanarak değerin var olup olmadığını kontrol ettik, ya da kontrol ettiğimizi sandık.</li>
<li>yaptığımız her işlemden sonra dizimizin o anki durumunu print_r fonksiyonu ile ekrana bastık.</li>
<li>$entries[‘şey’] = null; ifadesine kadar herşey normal. Ama bu ifadede fonskiyonumuz saçmalayacak. Görelim:</li>
</ol>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/3cd5e-1yyszlnacjbaswcl_b_rw1g.png">
</figure><h4>Null belası</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/492a4-16sohhad9s3r0hwh5f74xlw.jpeg">

<figcaption class="wp-caption-text">bela</figcaption></figure><p>İlk iki durumda, getEntry fonskiyonu sorunsuz çalıştı. Ama fonksiyonda değerin olup olmadığını isset ile kontrol ettiğimiz için, dizide şey değeri var olduğu halde, şey ifadesinin değeri: yazmadı. Halbuki print_r ile dizinin içindekileri görüntülediğimizde şey anahtarının dizide halen var olduğunu görüyoruz. Peki bunu nasıl düzeltebiliriz? PHP’de önceden tanımlı olan array_key_exists fonksiyonunu kullanarak. Bu sayede örneğin “şey” anahtarı ibnelik olsun diye null değerine bilerek eşitlense bile metodumuz o değerin halen orda olduğunu anlayacak:</p>
<pre><strong>&lt;?php<br><br>function </strong>getEntry(string $title, <strong>array </strong>$array)<br>{<br><strong>if </strong>(<em>array_key_exists</em>($title, $array)) {<br><strong>return </strong>$title . <strong>' ifadesinin değeri: ' </strong>. $array[$title] . <strong>'&lt;br&gt;'</strong>;<br>    }<br>}<br><br>$entries = [];<br>$entries[<strong>'nesne'</strong>] = <strong>'Sınıf Örneği'</strong>;<br><br><strong>echo </strong>getEntry(<strong>'nesne'</strong>, $entries);<br><br>$entries[<strong>'şey'</strong>] = <strong>'İsimsiz nesne'</strong>;<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>, $entries);<br><br><em>print_r</em>($entries);<br><br><strong>echo "&lt;br&gt;"</strong>;<br><br>$entries[<strong>'şey'</strong>] = <strong>null</strong>;<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>, $entries);<br><br><em>print_r</em>($entries);</pre>
<p>Çalıştıralım ve görelim:</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/e9f68-1zl4rg5wzysftxyexmwxvsg.png">
</figure><p>Yaptığımız değişiklik sayesinde, dizi içinde bir değer null değerine eşdeğer olsa bile, fonksiyonumuz bunu algılıyor ve dizi elemanını anahtarıyla basabiliyor. Burada anlamanızı istediğim şey, null’a güvenmeyin, hatta kodunuzda null ne kadar az ise o kadar temiz demektir. Null belası için <a href="https://www.ibuildings.nl/blog/2016/01/programming-guidelines-part-2-getting-rid-null" target="_blank">şu kaynağı</a> okumanızı öneririm.</p>
<h4>Diziden veriyi silmek</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/92c6f-1wpcrlqm_ytb7hw_huqz1pw.jpeg">

<figcaption class="wp-caption-text">dizi hedesi</figcaption></figure><p>Buraya kadar tamam. Peki diziden veriyi silmek istediğimizde ne yapacağız? Ve getEntry metodumuz nasıl saçmalamayacak? unset fonskiyonunu kullanacağız. Örneğimize devam edelim, kodumuzun sonuna şu satırları ekleyelim :</p>
<pre><strong>echo "&lt;br&gt;"</strong>;<br><br><strong>unset</strong>($entries[<strong>'şey'</strong>]);<br><br><strong>echo </strong>getEntry(<strong>'şey'</strong>, $entries);<br><br><em>print_r</em>($entries);</pre>
<p>Çalıştırdığımızda dizi içindeki anahtarın temiz bir şekilde silindiğini görüyoruz.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/a6df3-14tla9yd3wkczbozl-kff9a.png">
</figure><p>Şöyle bir sorun var yalnız. getEntry() fonksiyonunu çağırdığımızda değerin var olup olmadığından haberimiz olmuyor. Eğer değer varsa yazıyı döndürüyor, değer yoksa, hiç bir sonuç elde edemiyoruz. Bu bir sorun mu? Bence evet, çünkü programımızın doğru çalışıp çalışmadığını, kod üzerinde hata yapıp yapmadığımızı anlayamıyoruz. Bu sorunu if bloğundan sonra else bloğu ekleyerek çözebiliriz. Ama pek şık değil. Herhangi bir hatayı önceden görmemizi ve ona göre önlem almamızı sağlayacak olan try-catch blokları var. Ama bu konuyu zamanı geldiğinde detaylıca anlatacağım.</p>
<p>Şu soruları sormuştuk:</p>
<ol>
<li>Eklemek istediğimiz başlık sözlükte yoksa ve çağırdıysak bu sorunu bildirim göstermeden nasıl hallederiz?</li>
<li>Başlık zaten varsa ve değiştirmek istemiyorsak, aynı başlığa yeni bir açıklama değerini nasıl ekleriz?</li>
<li>Bir başlığı silmek ya da düzenlemek istediğimizde ve başlıkta birden fazla açıklama varsa, tüm açıklamalara mı etki edeceğiz yoksa sadece birine mi?</li>
<li>Bir başlığa, tarih bilgisini nasıl girebiliriz? Bu tarih bilgisine dayanarak nasıl sıralama işlemi yapabiliriz?</li>
<li>Arama, filtreleme işlerini nasıl yapacağız?</li>
</ol>
<p>Bunlardan ilk üç soruya kısmen cevap verdik. Bir sonraki yazıda kalan soruları aklımızda tutarak Dictionary.php dosyasındaki sınıfa geri döneceğiz..</p>
<p>Bir sonraki yazı şurda:</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-2-fa6aa74b93f3[/embed]
<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>