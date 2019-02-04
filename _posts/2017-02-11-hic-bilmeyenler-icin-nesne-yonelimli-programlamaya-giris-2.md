---
ID: 53
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-2
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-2/
published: true
post_date: 2017-02-11 12:02:27
---


<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/360cf-1mmvdovjj9sbxzs_tldmxga.jpeg">

<figcaption class="wp-caption-text">Sınıf</figcaption></figure><p>Bu yazı daha önce yazdığım <a href="https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-7907ef1d1d21#.3z97aut23" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya</a> Giriş yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-7907ef1d1d21[/embed]
<p>Önceki yazıda, nesne yönelimli programlama mantığını anlamaya çalıştık. Özetlemek gerekirse kabaca şunları anlatmıştım;</p>
<ol>
<li>Nesne kelimesinin ne anlama geldiğini</li>
<li>Felsefi, fiziksel, psikolojik ve dilbilimsel yönleri de olduğunu</li>
<li>Programlamada nesne kavramının ne ifade ettiğini</li>
<li>Neden nesne yönelimli programlama öğrenmemiz gerektiğini</li>
<li>Nesnelerin birbirleriyle ilişkilerini</li>
</ol>
<p>Şimdi kavramları anlatmaya ve örnekler vermeye devam edeceğim. Tüm yazılarımda olduğu gibi kavramları kuru kuruya ve salakça tanımlar vermek yerine, işe yarar, elle tutulur örneklerle mantığı okuyucunun kafasında oturtmaya çalışıyorum. Bazen yazılarımın dili laubali olabilir, ama yazının eğlenceli ve anlaşılabilir olması, bence ciddi olmasından daha avantajlı.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/17498-1t55bpcvspfemisw8swrmpg.jpeg">

<figcaption class="wp-caption-text">Ben çeşmeden kana kana su içmeyi çok severim mesela.</figcaption></figure><p>Hayatta herşeyi yaparken bir amacımız var, örneğin su içerken amacımız susuzluk hissimizi gidermek. Bu işi yaparken de belli başlı yöntemler kullanabiliriz. Örneğin;</p>
<ol>
<li>Bardağa çeşmeden su doldurabiliriz.</li>
<li>Bakkaldan 0,5 litrelik su alabiliriz.</li>
<li>Çeşmeye ağzımızı dayayıp lıkır lıkır buz gibi suyu içebiliriz.</li>
</ol>
<p>Yani belli bir amacı gerçekleştirmek için, farklı yöntemler uygulayabiliriz. Bu işi yaparken, ilk durumda susuzluk hissimiz, atıyorum %100 iken, işlemi gerçekleştirdikten sonra susuzluk hissimiz %0'a iner. Bilgisayar programları yazarken de, yazdığımız programların, belli kullanıcılar için, belli amaçları gerçekleştirmesini isteriz. İşte, programlarımızı, nesnelerimiz yazarken yapmamız gereken ilk iş, amacımızın ne olduğuna karar vermek. İkincisi de bu programı kimin kullanacağı. Şu anda düşünme tasarlama aşamasındayız. Yani özetle, belli kullanıcılar var ve bu kullanıcıların gerçekleştirmek istediği şeyler, ulaşmak istedikleri sonuçlar var.</p>
<h4>Üzümünü ye, bağını sorma (Information Hiding)</h4>
<p>Çeşme örneğinde, oturtmamız gereken en önemli mantık şu: Suyu içen kişi suyun dağdan mı, pınardan mı, nehirden mi geldiğini önemsemez. Onun için önemli olan, suyun temizliği, soğukluğu gibi kendini doğrudan ilgilendiren konulardır. Kitaplarda çok sık kullanılan bir diğer örnek, araba kullanırken, motorun, katalitik konvertörün, alternatörün o anda ne yaptığı ile ilgilenmiyoruz. Araç kullanıcısı olarak bizim amacımız bir yerden bir yere gitmek, ve bunu aracın direksiyonunu, vitesini, pedallarını vb. kullanarak gerçekleştiriyoruz. İşte bu “üzümünü ye, bağını sorma” olayına nesne yönelimli programlamada “bilgi gizleme” veya ingilizcesiyle “information hiding” deniyor.</p>
<p>Dolayısıyla bir programı yazmaya başlarken önce programın amacına karar vereceğiz. İşi nasıl yapacağına sonra karar vereceğiz.</p>
<h4>Genel olarak programlar</h4>
<p>Günümüzde genel olarak yazılımlara baktığımızda, basitçe hepsinin listelerden oluştuğunu görüyoruz. Programlar, bu listelere yeni kayıt eklemek, kayıt güncellemek, silmek ve görüntüleme işlemleri yapıyorlar. En basitinden bir yapılacaklar listesi uygulamasına yapacağımız işleri, bir bloga uygulamasına makalelerimizi kaydederken, Youtube videoları, instagram resimleri, twitter 140 karakterlik mesajları ve facebook’da saçma sapan şeyleri kaydetmemizi sağlıyor. Yani bu programların temel olarak mantığı aynı. Bu temel amaç dışındaki herşey ekstra. Bu program örneğine CRUD, yani create (yarat), read (oku), update (güncelle), delete (sil) deniyor. Ayrıca bu programlarda, kayıtlar üzerinde arama, filtreleme, sıralama işlemleri yapabiliyoruz. Mesela GittiGidiyor, HepsiBurada veya Sahibinden gibi sitelerde, aradığımız ürünleri fiyatlarına ya da eklenme tarihlerine göre sıralayabiliyoruz.</p>
<h4>Sözlük Uygulaması</h4>
<p>Sözlük derken, ekşisözlük değil tabii. Yeni yazdığım Nesne Yönelimli Programlama kitabı için bir sözlük uygulamasına ihtiyacım var. Girdilerin eklenebildiği, aranabildiği, farklı farklı sözlükler oluşturabileceğim, basit bir uygulama yapmak istiyorum ki, kitabımın sonunda bu sözlüğe yer verebileyim. Bu örnek uygulama da CRUD mantığı ile çalışacak. Şimdi tek tek programla yapmak istediğim şeylere bakalım:</p>
<ol>
<li>Bir kullanıcı olarak farklı farklı sözlükler yaratmak istiyorum. Bu sözlükleri açıp, içindeki girdileri görmek istiyorum.</li>
<li>Sözlüğe yeni bir girdi, yani başlık ve açıklama girmek istiyorum. (Şimdilik her başlıkta sadece tek bir açıklama metin alanı olacak.) (Create)</li>
<li>Başlığı girdiğimde, açıklamayı görmek istiyorum. (Read)</li>
<li>Bu girdileri listelemek istiyorum. (Her sayfada 10'ar tane olacak şekilde. Buna pagination deniyor.) Ayrıca listeyi istersem sıralamak istiyorum. Örneğin alfabetik olarak ya da ekleme tarihine göre. (Sort)</li>
<li>Girdiyi hatalı girdiysem, güncellemek ya da silmek istiyorum. (Update, Delete)</li>
<li>Arama yapmak istiyorum. (Hem başlıklarda hem de açıklama metninde) (Search)</li>
<li>Sözlüğün Word dosyası olarak çıktısını almak istiyorum.</li>
</ol>
<p>EkşiSözlükteki gibi farklı kullanıcıların benim sözlüğüme eklenti yapmalarını veya sözlüğümü görmelerini istemiyorum, ama bu sonraki konu. Şimdilik en temel ihtiyaçlara odaklanmak en doğrusu. Mesela ekşiSözlükteki gibi bir başlığa birden fazla girdi eklemek, birden fazla kullanıcının sözlüklere ekleme yapabilmesini sağlamak, girdileri sosyal medyada paylaşmak, etiket girmek veya bkz. ile bir başlıktan diğer bir başlığa link oluşturmak gibi özellikleri sonradan da geliştirebiliriz. Bunları işe başlar başlamaz, aa ilerde kullanılır diye yazmaya kalkarsak ayvayı yeriz ki bu da yazılımcıların yaptığı en büyük hatalardan biridir. (Buna featuritis veya feature creep deniyor.)</p>
<p>İstediklerimi, yani ihtiyaçlarımı (requirements) listeledikten sonra, yazacağım programın hangi sınıflardan oluşacağına karar vermeye geldi sıra. Bunu yaparken İhtiyaçlardaki isimlere bakmak, sınıf tasarımı yapmada verimli yöntemlerden bir tanesi. İsimlere tek tek bakalım:</p>
<ol>
<li>Sözlük (Yani bir başlık metni, mesela Felsefe Sözlüğü ya da Nesne Yönelimli Programlama sözlüğü gibi.)</li>
<li>Başlık (Her başlığın şimdilik tek bir açıklama metni olacak)</li>
<li>Kullanıcı (Yani ben.)</li>
</ol>
<p>Peki bu nesneleri nasıl kullanacağım? Buna da tek tek karar vermek gerekiyor. Nesneleri iyi ayarlamanın en iyi yollarından biri, onların sorumluluklarını önceden iyi belirlemektir. Ayrıca aklımızda tutmamız gereken önemli bir konu da, her nesnenin bir adet sorumluluğa sahip olmasıdır ki buna Tek Sorumluluk Prensibi yani (Single Responsibility Principle) deniyor. Yani yazacağımız nesne tek bir işi düzgünce yapan, bağımsız bir program gibi olacak. İstersek bu nesneyi programdan koparıp başka bir programda kullanabileceğiz.</p>
<p>Nesne tek başına her boku yapmaya çalışmıycak arkadaşlar. Yani sözlük nesnesi, kullanıcıları yönetmiycek, şifrelerle ilgilenmiycek, kendi başına temiz temiz bağımsız şekilde çalışacak. Eğer bir nesne her boku tek başına yapıyorsa bu kötü tasarımdır ve buna Tanrı Nesnesi (God Object) denir, test edilmesi zordur, sırt pırt hata çıkarır. Uzak durun.</p>
<p>Yeri geldiğinde bu prensiplere de ayrıntısıyla değineceğim. <a href="http://www.barbarosgurcan.com/post/solid-principles-nedir-solid-ilkeleri" target="_blank">Şurada</a> konuyla ilgili güzel bir kaynak mevcut.</p>
<h4>Beklentiler</h4>
<p>Sınıflarımızdan beklentilerimizi başta belirlemek uygulama tasarımımızın en önemli kısmı. Yani Sözlük sınıfı ile ne yapacağız, nasıl kullanacağız, sözlük sınıfı bize hangi hizmetleri sunacak ona karar verdiğimiz anda, işimiz %90 oranında kolaylaşacak. Sözlük sınıfı ile yapabileceğimiz şeyler şimdilik şunlar olsun:</p>
<ol>
<li>Sözlük bir isimle oluşturmak. (construct)</li>
<li>Bu adı değiştirmek yani güncellemek. (setTitle)</li>
<li>Sözlüğe girdi eklemek. (addEntry)</li>
<li>Tüm başlıkları görüntülemek. (getEntries)</li>
<li>Başlıklar içinde arama yapmak. (search)</li>
<li>Dönen başlıkları ada göre veya eklenme tarihine göre sıralamak. (sort)</li>
</ol>
<p>Şimdilik basitçe sözlük sınıfı ile yapabileceğimiz işlemlerin bunlar olduğuna karar verdik.</p>
<p>Burada foksiyonlar, koşullar, döngüler değişkenler gibi temel programlama bilginiz olduğunu farzediyorum. Eğer bu konularda bilginiz yoksa, kitapçılardan <a href="http://www.seckin.com.tr/kitap/911934237" target="_blank">Projelerle PHP 7</a> adlı kitabımı satın alabilirsiniz. Satın alma linki de şu: <a href="http://www.seckin.com.tr/kitap/911934237" target="_blank">www.seckin.com.tr/kitap/911934237</a></p>
<p>Kodları yazarken ingilizce kullanmaya özen gösteriyorum. Özellikle değişken isimlerinizin, yorumlarınızın ingilizce olması önemli. İngilizce dünyada evrensel bir dil olduğundan ve genellikle açık kaynaklı yazılımlar geliştirdiğimden, kodlarımın Mozambik’te veya Çin’de öğrenmeye istekli bir kişi tarafından okunabiliyor olması önemli. İngilizce’nin önemi konusunda ayrı bir makale de yazacağım.</p>
<p>Önceden kurduğunuzu tahmin ettiğim webserver’in içinde dictionary isimli bir dizin oluşturalım. Bu dizinde Dictionary.php isimli bir dosya açalım (İlk harf özellikle büyük olsun ki dosyanın bir sınıf içerdiğini anlayalım) ve sınıfımızı içinde metodlar olmadan yazmaya başlayalım:</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><br><strong>class </strong>Dictionary<br>{<br><strong>private $title</strong>;<br><strong>private $entries</strong>;<br>}</pre>
<p>Satır satır ilerleyelim. Namespace dediğimiz kavram, yazdığımız sınıfların, aynı isimdeki diğer sınıflarla karışmamasını sağlayan, PHP 5.3 versiyonunda gelen bir icat. Ben örneklerimde kendi ismimi kullanıyorum, fakat bu konuda farklı doğru pratikler mevcut. Bunları daha detaylı anlatacağım.</p>
<p>“class Dictionary” diyerek sınıfımızın adına karar verdikten sonra, {} süslü parantezler içinde sınıfımızın değişken ve metodlarını yazacağız. Burada $title ve $entries, sınıfımıza ait değişkenler. Değişken ve metodların başına private yazdığımızda, o değişken ve metodlara sadece o sınıf içerisinden erişebiliyoruz ki, başka sınıflar, benim sınıfıma ait değişkenlere kafalarına göre erişip değiştirmesinler. Değişkenler ayrıca public ve protected’da oluyorlar. Değişken public olduğunda, süslü parantezin dışından herhangi bir programcı değişkenin anlık değerini değiştirebilir ve sınıfımızın çalışmasını bok edebilir. Doğru bir pratik olarak bütün değişkenlerinizi, private başlatmaya alışmanız çok önemli. Protected kavramını daha sonra anlatacağım.</p>
<h4>Getter, Setter metodları. (alıcı, düzenleyici)</h4>
<p>E peki bütün değişkenler private olursa bunlara nasıl erişeceğiz? Getter ve Setter metodları ile. İsimlerinin illa getBilmemne olmasına gerek yok ama doğru ve oturmuş bir pratik olarak nesne değişkeninizin ismi ne ise, başına get yazmak iyidir. Yani başlığı dışarıdan almak için getTitle, düzenlemek için de setTitle public metodlarına ihtiyacımız var. Bu sayede örneğin, kullanıcının boş başlık oluşturmasını engelleyebiliriz, ya da başlık için bir karakter sınırı koyabiliriz ki, adam başlığa bir trilyon karakter girmeye çalışıp programımızı çökerttirmesin.</p>
<pre><strong>public function </strong>setTitle(string $title)<br>{<br><strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {<br>        $this-&gt;<strong>title </strong>= $title;<br>    }<br>}</pre>
<p>public function diyerek metodumuza dışarıdan erişilebileceğini belirttik. string $title diyerek, string değişkeninin string yani metin tipinde olmasını garantiledik. Buna “type hinting” yani tip ipucu deniyor. PHP 5 sürümünden beri var. İlk if bloğunda göreceğimiz şekilde değişkenin boş olmadığını ve uzunluğunun da en çok 70 karakterden oluşması gerektiğini söyledik.</p>
<p>Burada yaptığımız işleme <strong>VALIDATION</strong> yani <strong>doğrulama</strong> deniyor ki, kullanıcılardan girdi alan uygulamalar yazarken, güvenlik açısından çok dikkat etmemiz bir kavram. Tüm kullanıcı girdileri lanetlidir diye bir söz vardır. Programımızın düzgün çalışmasını, daha programı yazarken bu şekilde garanti altına alıyoruz. Bir de bazı pislik insanların kalkıp bu girdilere HTML, Javascript, SQL kodu sokuşturmalarına da engel olmalıyız. Bunun için de belirli güvenlik önlemleri var. Bu işleme de <strong>SANITIZATION</strong> yani <strong>temizleme</strong> deniyor. Bu konuya da programımız, internet formundan kullanıcı girdileri alacak hale geldiğinde derinlemesine girişeceğiz.</p>
<p>Bu tip küçük detaylara dikkat ettiğimizde, programımızın nispeten hatasız çalışmasını, başımızı ağrıtacak bug’lar ortaya çıkmamasını garanti etmiş oluyoruz.</p>
<p>Eğer sınıf değişkenimiz public $title; şeklinde belirtilmiş olsaydı, dışarıdan herhangi bir kimse bizim validation kurallarımızı sallamadan sınıfımızın değişkenine tecavüz edebilirdi ki bunu istemeyiz. Bu yüzden nesne yönelimli programlamayı öğrenirken, gerçek hayatta kullanılan pratiklere en baştan aşina olmanızı istiyorum.</p>
<pre>$this-&gt;<strong>title </strong>= $title;</pre>
<p>$this ifadesi, burada içinde bulunduğumuz sınıfa ait nesneyi ifade ediyor. “-&gt;” operatörüyle değişken eğer bir nesne ise, sahip olduğu değişkene erişebiliyoruz. Nesneyi programımızda takır takır kullanmaya başladığımızda size, sınıf ve nesne kavramı arasındaki farkı da anlatacağım. Devam edelim.</p>
<p>Peki $title değişkenimize nasıl erişeceğiz? Bunun için de getTitle() isimli bir metod yazacağız. Bu metodun tek görevi, sınıfta bulunan private $title değişkenini kullanıcıya döndürmek.</p>
<pre><strong>public function </strong>getTitle():string<br>{<br><strong>return </strong>$this-&gt;<strong>title</strong>;<br>}</pre>
<p>Metodu yazarken : işaretinden sonra gelen string kelimesine dikkat ettiniz mi? Bu PHP 7 ile gelen harika bir yenilik, “return type” yani dönüş tipi olarak adlandırılıyor. Bu da metodumuzun hangi değeri döndüreceğini önceden belirlememizi sağlıyor. Yani kazara başka bir tipte değişken döndürmeyeceğiz ki, programımızı kullanan kullanıcı string yani metin yerine int yani sayı görüp afallamasın, mavi ekran vermesin, bug arayıp kafasını duvarlara vurmasın.</p>
<p>Sınıfımızın son hali şu şekilde:</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><br><strong>class </strong>Dictionary<br>{<br><strong>private $title</strong>;<br><strong>private $entries</strong>;<br><br><strong>public function </strong>setTitle(string $title)<br>    {<br><strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {<br>            $this-&gt;<strong>title </strong>= $title;<br>        }<br>    }<br><br><strong>public function </strong>getTitle():string<br>    {<br><strong>return </strong>$this-&gt;<strong>title</strong>;<br>    }<br><br>}</pre>
<p>Dikkat etmeniz gerek iki kavram şunlar:</p>
<ol>
<li>
<strong>Sınıf</strong>: Bir nesnenin kalıbını belirler.</li>
<li>
<strong>Nesne</strong>: Sınıftan kullanıcı tarafından üretilir.</li>
</ol>
<p>Yani bu ikisi birbirinin aynısı değilidir. Mesela Sınıf audi A8'in çizimleri ise, nesne, yollarda züppelik yapan, makas atan 34TT264 plakalı hıyar arabadır.</p>
<p>Peki kullanıcı bu sınıfı nasıl kullanacak? Aynı dizin altında app.php isimli bir dosya oluşturalım:</p>
<pre><strong>&lt;?php<br><br>require_once 'Dictionary.php'</strong>;<br>$dictionary = <strong>new </strong>MidoriKocakDictionary();<br><strong>echo </strong>$dictionary-&gt;getTitle();</pre>
<p>Require ifadesiyle aynı dizindeki Dictionary.php dosyasını çağırdık. Dosya çağırma işleminin 4 adet yöntemi var.</p>
<ol>
<li>
<strong>require:</strong> Dosyayı çağırır, bulamazsa programın çalışmasını durdurur.</li>
<li>
<strong>require_once: </strong>Dosyayı bir sefer çağırır, yani daha önce herhangi bir yerde require veya require_once ifadesiyle aynı dosya çağırıldıysa tekrar çağırmaz. Dosya bulunamadıysa, programın çalışmasını durdurur.</li>
<li>
<strong>include:</strong> Dosyayı çağırır, bulamazsa HATA (Warning) mesajı verir ama programı çalıştırmaya devam eder. Eğer o dosyada tanımlanan bir metoda veya değişkene erişmeye çalışırsanız, hata alır bol bol nerde hata yaptım diye ağlarsınız.</li>
<li>
<strong>include_once: </strong>Dosyayı bir sefer çağırır, yani daha önce herhangi bir yerde include veya include_once ifadesiyle aynı dosya çağırıldıysa tekrar çağırmaz. Dosya bulunamadıysa, çalışır ve kafanızı duvarlara vurursunuz.</li>
</ol>
<p>O yüzden şimdilik require_once kullanacağız. Daha sonra, <a href="https://getcomposer.org/" target="_blank">composer</a> ve autolader kullanmaya başladığımızda bunlara veda edeceğiz, ama onu composer bölümünde anlatacağım. Şimdilik takılmayın. <a href="https://getcomposer.org/" target="_blank">https://getcomposer.org/</a></p>
<p>$dictionary isimli bir değişken oluşturduk ve sınıfımızın başında belirttiğimiz Namespace ismi ile sınıfımızı new ifadesiyle yarattık. Dosyayı daha önceden doğru dürüst kurmuş olduğunuzu tahmin ettiğim yerel webserver üzerinden 127.0.0.1/dictionary/app.php adresiyle çağıralım.</p>
<p>Şöyle ölümcül bir hatayla karşılaşmamız gerekiyor, hatayı göremiyorsanız, PHP hata gösterme ayarlarınız kapalıdır. Onu da bi zahmet php.ini içinden açmalısınız, detaya girmiyorum.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/f3a12-1stgcipk_ctuuhgn8x8794w.png">

<figcaption class="wp-caption-text">Ölümcül hata</figcaption></figure><p>Hata neden oldu? Çünkü, $title değişkenimizi set etmeden, yani ona bir değer vermeden istemeye kalktık. getTitle metodunun sonuna :string yazarak metin tipinde bir değişken döndürmesini emrettik ama herhangi bir değer atamadığımızdan null döndürmeye kalktı. Bu tanımlamayı yaptığımız için ileride olabilecek bir çok bug’ın önüne geçmiş olduk. <strong>Null</strong> değişkenin henüz tanımlı olmadığını ya da bilerek veya isteyerek null değerine eşit olduğunu gösteren “yok” anlamına gelen ifadedir. Bu null belasından neden kaçmamız gerektiğini detaylıca, en iyi pratikler bölümünde detaylıca yazacağım.</p>
<p>Önce app.php içinde setTitle yazarak bu olayı çözebilirdik ama zırt pırt bunu kontrol edemeyiz ve programımızın da hata vermesini önlemek istiyoruz peki ne yapacağız? Sihirli __construct() metodunu kullanacağız.</p>
<h4>__construct() metodu</h4>
<p>PHP’de bir metodun başında iki alt çizgi varsa, ve tanımlı sihirli metodlardan (magic methods) bir tanesiyse, PHP yorumlayıcısı metodu tanır, ve gerektiği zamanda kendisi çalıştırır. Construct, yani inşa et metodu da, biz new MidoriKocakDictionary() dediğimiz anda çalışacak olan metod. Yani bir sınıftan nesne yarattığımızda bu metod çalışacak. Şu şekilde sınıfımızın başına __construct metodunu ekleyelim:</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><br><strong>class </strong>Dictionary<br>{<br><strong>private $title</strong>;<br><strong>private $entries</strong>;<br><br><strong>public function </strong>__construct(string $title)<br>    {<br>        $this-&gt;<strong>title </strong>= $title;<br>        $this-&gt;<strong>entries </strong>= [];<br>    }<br><br><strong>public function </strong>setTitle(string $title)<br>    {<br><strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {<br>            $this-&gt;<strong>title </strong>= $title;<br>        }<br>    }<br><br><strong>public function </strong>getTitle():string<br>    {<br><strong>return </strong>$this-&gt;<strong>title</strong>;<br>    }<br>}</pre>
<p>Burada construct metodunda, parametre olarak string $title, yani metin tipinde başlık değişkeni tanımladı. $title parametresini kullanarak $this-title ifadesiyle nesnemizin $title değişkenini tanımladık. Null belasından kaçmak için de $entries değişkenimize boş bir dizi (array) ekledik. Daha sonra sözlüğe kaydedeceğimiz kelimeleri bu dizide tutacağız.</p>
<p>app.php’yi çalıştıralım ve ikinci ölümcül hatamızla karşılaşalım:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/4a52b-1es38nkepicntrx1gvi2otq.png">

<figcaption class="wp-caption-text">İkinci ölümcül hata</figcaption></figure><p>Hata neden oldu? Çünkü app.php’yi değiştirmedik. __constructor() metodu içinde metin tipinde bir parametre olması gerektiği ve biz new MidoriKocakDictionary() şeklinde çağırdığımızdan, PHP derleyicisi, “E başlık nerde ulan?” hatası verdi. app.php’yi şu şekilde değiştirelim:</p>
<pre><strong>&lt;?php<br><br>require_once 'Dictionary.php'</strong>;<br>$dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>"Nesne Yönelimli Programlama Sözlüğü"</strong>);<br><strong>echo </strong>$dictionary-&gt;getTitle();</pre>
<p>Tarayıcı ile app.php dosyasını açalım ve tertemiz başlığımızı görelim:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/dba81-1_rbofyxyfruad7lo48lcrg.png">

<figcaption class="wp-caption-text">Hatasız mis gibi.</figcaption></figure><p>Bu yazıda şimdilik anlatacaklarım bu kadar.</p>
<h4>Özetle;</h4>
<ol>
<li>Sınıf ve nesne kavramlarının ne olduklarını</li>
<li>Sınıfların nasıl tasarlandıklarını</li>
<li>Ne işe yaradıklarını</li>
<li>Nasıl yazıldıklarını</li>
<li>Nasıl kullanılmaları gerektiğini</li>
<li>Sihirli __constructor() metodunu öğrendik</li>
</ol>
<p>Bir sonraki yazıda, sınıfımızı oluşturmaya ve programımızı yazmaya devam edeceğiz.</p>
<p>Bir sonraki yazıya şuradan ulaşabilirsiniz:</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-7907ef1d1d21[/embed]
<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>