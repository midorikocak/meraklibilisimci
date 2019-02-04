---
ID: 59
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-8 Web Arayüzü
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-8-web-arayuzu/
published: true
post_date: 2017-03-10 15:06:19
---



<p>Bu yazı <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-7-s%C4%B1n%C4%B1flar%C4%B1-kullanmak-ve-api-meselesi-a03fcbfb543b#.vrs18wf5p" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-7 — Sınıfları Kullanmak ve API meselesi</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-7-s%C4%B1n%C4%B1flar%C4%B1-kullanmak-ve-api-meselesi-a03fcbfb543b[/embed]
<p>Bir önceki yazıda, API kavramını, kullanıcının uygulamaya hangi adresleri kullanarak erişebileceğini, bu adreslerin nasıl çalışacağını, yönlendirme kavramını ve arayüz mantığını anlatmıştım. Bu yazıda kullanıcının ilk olarak karşılacağı arayüzleri nasıl oluşturacağımızı, nasıl tasarlayacağımızı ve kullanacağımızı anlatacağım. Daha önce <a href="http://www.seckin.com.tr/kitap/911934237" target="_blank">Projelerle PHP 7</a> adlı kitabımda HTML konusunu anlattığım için, html sayfaları yazmak konusunda detaya inmeyeceğim. Eğer konu ile ilgili eksiğiniz varsa benim kitabımdan veya internetteki kaynaklardan eksiğinizi giderebilirsiniz.</p>
<p>Web uygulamamızda, kullanıcıya bilgileri bir HTML sayfası aracılığı ile gösterecek, ondan bilgileri bir HTML formu aracılığı ile alacak ve işleyeceğiz. Ayrıca kullanıcıdan gelecek bilgilere neden güvenmememiz gerektiğini, kötü niyetli bir kullanıcının sistemimize ve programdaki diğer kullanıcılara nasıl zarar verebileceğini göreceğiz. Ayrıca bu yazıda ilk defa uygulamamızda veriyi nasıl kaydedeceğimize kısaca giriş yapacağız.</p>
<p>Kısaca programımızda 3 ekran olacak. Birinde hali hazırda yarattığımız sözlükleri ve başlık sayılarını görüntüleyeceğiz. İkincisinde, sözlüğü ve içindeki başlıkların listesini görecek, üçüncüsünde de bir başlığa tıkladığımızda açıklamaları göreceğiz.</p>


<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/08d61-1srt-a6o-bbiqg252brd1pg.png">
</figure><figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/4b2c4-1go29rdx0hzpnb3gov6ucyq.png">
</figure><figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/a23a3-1amyxtnfjgost8vxiiyyhiw.png">

<figcaption class="wp-caption-text">Kısaca ekranlarımız</figcaption></figure>


<p>Ekranların kötü göründüğüne bakmayın. Sonuçta bize yol gösterecek olan prototipler yani tasarımlar. Siz de benzer tasarımları <a href="https://fatiherikli.github.io/mockup-designer/#document/baea7eb1-a394-3cfe-b72f-53c59832b608" target="_blank">Mockup Designe</a>r ile yapabilirsiniz.</p>
<p>Genel olarak mobil ve web uygulamalarında tasarımlar aynı oluyor. Biz yine kısaca tasarımları içerdikleri elemanlara göre inceleyelim.</p>
<ol>
<li>Kaydettiğimiz verileri eklemize ve düzenlememize yarayan bir form bileşeni.</li>
<li>Kaydettiğimiz verileri listelememize yarayan bir liste bileşeni.</li>
<li>Kaydettiğimiz veriyi tek olarak görüntülememize yarayan bir diğer bileşen.</li>
</ol>
<p>Biz bu bileşenleri şimdilik program kodu olmadan kullanıcının göreceği şekilde kodlayalım. Daha sonra bu düz HTML kodlarını bileşenlerine ayıracağız ve aynı kodları tekrar etmemize gerek kalmayacak.</p>
<p>Şimdi proje dizinimizde public adlı bir klasör oluşturalım. Genellikle bu public klasörlerinde js css ve img dizinleri bulunur. public klasörünün altında css adlı bir dizin oluşturalım ve içine <a href="https://raw.githubusercontent.com/midorikocak/dictionary/v0.1-alpha/public/css/universal.css" target="_blank">şu adresteki</a> kodu universal.css olarak kaydedelim.</p>
<p>Daha sonra public dizinine geri dönelim. index.html isminde bir dosya oluşturalım. İçine şu kodları ekleyelim:</p>
<pre>&lt;!DOCTYPE <strong>html</strong>&gt;<br>&lt;<strong>html lang="en"</strong>&gt;<br>&lt;<strong>head</strong>&gt;<br>    &lt;<strong>meta charset="UTF-8"</strong>&gt;<br>    &lt;<strong>title</strong>&gt;Sözlük Uygulaması&lt;/<strong>title</strong>&gt;<br>    &lt;<strong>link rel="stylesheet" href="//fonts.googleapis.com/css?family=Roboto:300,300italic,700,700italic"</strong>&gt;<br>    &lt;<strong>link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.min.css"</strong>&gt;<br>    &lt;<strong>link rel="stylesheet" href="css/universal.css"</strong>&gt;<br>&lt;/<strong>head</strong>&gt;<br>&lt;<strong>body</strong>&gt;<br>&lt;<strong>header</strong>&gt;<br>    &lt;<strong>h1</strong>&gt;Sözlük Uygulaması&lt;/<strong>h1</strong>&gt;<br>    &lt;<strong>nav</strong>&gt;<br>        &lt;<strong>ul class="list horizontal"</strong>&gt;<br>            &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Hakkında&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>            &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Şartlar&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>            &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Gizlilik&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>        &lt;/<strong>ul</strong>&gt;<br>    &lt;/<strong>nav</strong>&gt;<br>&lt;/<strong>header</strong>&gt;<br>&lt;<strong>main</strong>&gt;<br>    &lt;<strong>aside</strong>&gt;<br>        &lt;<strong>nav</strong>&gt;<br>            &lt;<strong>ul class="list vertical"</strong>&gt;<br>                &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Sözlüklerim&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>            &lt;/<strong>ul</strong>&gt;<br>        &lt;/<strong>nav</strong>&gt;<br>    &lt;/<strong>aside</strong>&gt;<br>    &lt;<strong>section</strong>&gt;<br>        &lt;<strong>h2</strong>&gt;Sözlüklerim&lt;/<strong>h2</strong>&gt;<br>        &lt;<strong>form</strong>&gt;<br>            &lt;<strong>label for="title"</strong>&gt;Yeni Sözlük&lt;/<strong>label</strong>&gt;<br>            &lt;<strong>input type="text" id="title" name="title" placeholder="Başlık"</strong>&gt;<br><br>            &lt;<strong>input type="submit" value="Yeni Sözlük Ekle"</strong>&gt;<br>        &lt;/<strong>form</strong>&gt;<br>        &lt;<strong>table</strong>&gt;<br>            &lt;<strong>thead</strong>&gt;<br>            &lt;<strong>th</strong>&gt;id&lt;/<strong>th</strong>&gt;<br>            &lt;<strong>th</strong>&gt;Başlık&lt;/<strong>th</strong>&gt;<br>            &lt;<strong>th</strong>&gt;Girdi Sayısı&lt;/<strong>th</strong>&gt;<br>            &lt;<strong>th</strong>&gt;Düzenleme&lt;/<strong>th</strong>&gt;<br>            &lt;/<strong>thead</strong>&gt;<br>            &lt;<strong>tbody</strong>&gt;<br>            &lt;<strong>tr</strong>&gt;<br>                &lt;<strong>td</strong>&gt;14&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;Nesne Yönelimli Programlama Sözlüğü&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;24&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Düzenle &lt;/<strong>a</strong>&gt;<strong>&amp;nbsp;</strong>&lt;<strong>a href="#"</strong>&gt;Sil &lt;/<strong>a</strong>&gt;&lt;/<strong>td</strong>&gt;<br>            &lt;/<strong>tr</strong>&gt;<br>            &lt;<strong>tr</strong>&gt;<br>                &lt;<strong>td</strong>&gt;48&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;Bilişim Terimleri Sözlüğü&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;12&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Düzenle &lt;/<strong>a</strong>&gt;<strong>&amp;nbsp;</strong>&lt;<strong>a href="#"</strong>&gt;Sil &lt;/<strong>a</strong>&gt;&lt;/<strong>td</strong>&gt;<br>            &lt;/<strong>tr</strong>&gt;<br>            &lt;<strong>tr</strong>&gt;<br>                &lt;<strong>td</strong>&gt;41&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;Tıp Sözlüğü&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;250&lt;/<strong>td</strong>&gt;<br>                &lt;<strong>td</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Düzenle &lt;/<strong>a</strong>&gt;<strong>&amp;nbsp;</strong>&lt;<strong>a href="#"</strong>&gt;Sil &lt;/<strong>a</strong>&gt;&lt;/<strong>td</strong>&gt;<br>            &lt;/<strong>tr</strong>&gt;<br>            &lt;/<strong>tbody</strong>&gt;<br>        &lt;/<strong>table</strong>&gt;<br>    &lt;/<strong>section</strong>&gt;<br>&lt;/<strong>main</strong>&gt;<br>&lt;<strong>footer</strong>&gt;<br>    &lt;<strong>p</strong>&gt;<br>        Sözlük Uygulaması - Copyright - Midori Kocak - 2017<br>    &lt;/<strong>p</strong>&gt;<br>&lt;/<strong>footer</strong>&gt;<br>&lt;<strong>script src="js/main.js"</strong>&gt;&lt;/<strong>script</strong>&gt;<br>&lt;/<strong>body</strong>&gt;<br>&lt;/<strong>html</strong>&gt;</pre>
<p>Merak etmeyin bu HTML kodların tek tek uygulamamızla nasıl entegre olacağından bahsedeceğim.</p>
<p>web sunucumucdan index.html’yi çağırdığımızda şöyle bir görüntüyle karşılaşmamız gerekiyor:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/5dc9a-1rmbynzozcgcxf2u84myhta.png">

<figcaption class="wp-caption-text">Uygulama arayüzü</figcaption></figure><p>Genellikle bütün uygulama arayüzleri bu yapıyı kullanırlar. O yüzden başka bir uygulama yazarken siz de bu arayüz mantığını kullanabilirsiniz. Bunu tek tek örnekleriyle anlatacağım.Şimdi bu arayüzde hangi bileşen ne iş yapar onu görelim.</p>
<h4><strong>Header yani Üstbilgi</strong></h4>
<p>Üstteki siyah kısım. Kod bloğu içinde de header etiketi içinde yer alıyor. Uygulamalarda bu kısım, her sayfada aynı olan, sayfa değiştiğinde değişmeyen, logo, ana sayfa, hakkında, gizlilik vb. gibi linkleri, eğer kullanıcı yönetiyorsak, kullanıcı adını ve kendiyle ilgili işlemleri (login/logout gibi) yapmasını yarayan bir açılır menüyü, arama yapılabiliyorsa, arama formunu içerir.</p>
<p>Mesela, facebook, twitter ve linkedin uygulamalarında bu bölümler nasıl tasarlanmış bir göz atalım:</p>
<p>Twitter Üstbilgi:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/1a8a0-1gjxitzp4tdcdaudubx30ha.png">

<figcaption class="wp-caption-text">Twitter Header</figcaption></figure><p>facebook Üstbilgi:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/f6316-14nrs5gq07yxvrluts40oqa.png">

<figcaption class="wp-caption-text">Facebook Header</figcaption></figure><p>Linkedin Üstbilgi:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/3fae1-17toban7it28dmagsvitpea.png">

<figcaption class="wp-caption-text">Linkedin Header</figcaption></figure><p>Gördüğünüz gibi uygulamada header yapıları küçük değişikliklere rağmen aynı.</p>
<h4>Aside yani Yanbilgi</h4>
<p>Genel olarak, uygulamamızı kullanırken isteğe bağlı olarak ihtiyaç duyacağımız bilgileri içeren kısmı temsil eder. Bizim kodumuzda aside etiketiyle tanımlanmıştır.</p>
<p>Index.php dosyasını açtığımızda, sol tarafta bulunan üstüste linklerle oluşturduğumuz kısım. Burası genellikle uygulama içindeki farklı modüllere ilerlememizi sağlayan linkleri içerir. Biz uygulamamızda sadece sözlük tuttuğumuz için, Sözlüklerim adlı bir link var. Buradaki link sayesinde, programın herhangi bir yerinde istediğimiz zaman Modülün ana sayfasına dönüş yapabileceğiz. Sözlüklerim için, bütün sözlüklerimi listelediğim sayfa. Örneğin facebook’ta burada, Gruplar, Sayfalar, Etkinlikler gibi linkler bulunur. Görelim:</p>
<p>facebook Yanbilgi:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/2011e-1vhtxsvry5hzcqjve4e-crq.png">

<figcaption class="wp-caption-text">facebook aside</figcaption></figure><p>Twitter Yanbilgi:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/70b59-1ivursn5ufxorhnkdlilprq.png">

<figcaption class="wp-caption-text">Twitter Aside</figcaption></figure><p>Linkedin Yanbilgi:</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/54172-13_xlltw1os-7-7jbzvfhng.png">
</figure><p>Mesela linkedin ve twitter örneklerine baktığımızda, kendi profiliml ilgili bilgileri ve istatistikleri görmemi sağlayan bir profil bileşeni konmuş. Facebook örneğinde sadece kullanıcı adı ve kullanıcı resmi içeren minik bir link konmuş.</p>
<h4>Main yani Asıl işi yaptığımız kısım</h4>
<p>Bu kısım kaydettiğimiz varlığın, yani video, tweet, paylaşım gibi bilgilerin sırayla listelendiği kısım olacak. Bazen kullanıcı uygulamayı açtığında, dashboard yani gösterge paneli veya kontrol paneli dediğimiz, grafiklerle uygulama istatistiklerini gösteren bir kısımla da karşılaşabiliyor.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/b7d86-1aab9-j1agmk0eejge48nzq.png">

<figcaption class="wp-caption-text">Gösterge Paneli</figcaption></figure><p>Ancak bizim şu an incelediğimiz, twitter, linkedin ve facebook örneklerinde sayfayı açtığımızda, uygulamamızda yönettiğimiz asıl varlığı eklememize yarayan minik bir form ve akış yani feed dediğimiz iki modül main yani ana ekranda bulunuyor. Örnekleri görelim:</p>
<p>Twitter:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/1459d-1culjximunzvhpjrqn9svjq.png">

<figcaption class="wp-caption-text">Twitter Akış</figcaption></figure><p>Facebook:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/6cbf1-10j_laqyqzzhfxoafs69a4g.png">

<figcaption class="wp-caption-text">Facebook Akış</figcaption></figure><p>Linkedin:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/26854-1jsjqhfso5oinp7cyvqnxrq.png">

<figcaption class="wp-caption-text">Linkedin Akış</figcaption></figure><p>Gördüğümüz gibi üç örnekte de, minik bir form ve varlıkları tek tek listeleyen akış dediğimiz bir kısım var.</p>
<p>Akış yani feedlerde lazy loading, yani tembel yükleme dediğimiz mantık işliyor. Yani binlerce, milyonlarca paylaşımı veya tweet’i bir anda göstermek yerine, örneğin ilk 10 tanesi yükleniyor, ve kullanıcı sayfayı aşağı kaydırdığında bir 10 tanesi daha yükleniyor. Başka bir yöntem de pagination ya da sayfalama.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/ddd5b-1kdatqu9ec7g7douuexuy1w.png">

<figcaption class="wp-caption-text">Sayfalama</figcaption></figure><p>Sayfalama sayesinde takip ettiğimiz verilerin tamamını sayfaya indirip görüntülemek yerine, ilk 10 tanesini ilk sayfada görüntüleyecek ve kullanıcı eğer isterse sonraki sayfalara tıklayarak kalan varlıkları görüntüleyecek. Biz henüz <strong>javascript</strong> kısmına gelmediğimiz için uygulamamızda bu yöntemi kullanacağız.</p>
<h4>PHP’de Görünümler yani View’lar</h4>
<p>Yukarıda paylaştığım HTML örneği, son kullanıcının uygulamamızı açtığında, tarayıcısına gidecek olan HTML kodudur. Şimdi, kullanıcının bu kodu nasıl elde edeceğine, server yani sunucu tarafında bizim karar vermemiz gerekiyor. PHP’de bunu yapmanın birden fazla yolu var.</p>
<ol>
<li>Düz PHP dosyasında, PHP ve HTML kodlarını karıştırmak.</li>
<li>Tema olarak kullanacağımız PHP dosyaları oluşturmak ve yine PHP ve HTML kodlarını karıştırmak.</li>
<li>Nesne yönelimli olarak bir View yani Görünüm sınıfı oluşturmak ve bu sınıfı kullanmak. Hatta kullanıcıya göstereceğimiz form, liste gibi modüller için de ayrı sınıflar oluşturmak.</li>
</ol>
<p>Bu konu aslında “separation of concerns” yani tam çevirmek gerekirse “ilgilerin birbirinden ayrılması” konusuna giriyor ve MVC yani model-view-controller kısmını anlattığımda detaylıca bahsedeceğim kısımla alakalı ancak, şimdilik o bölüme girmeden nesne yönelimli olarak kullanıcının görüntüleyeceği HTML kodunu yönetmenin dışına çıkmayacağız. Biz bu yazı serisinde Nesne Yönelimli Programlama ile ilgili olduğumuzdan, 3. yöntemle yani View sınıfları kullanarak bi işi halledeceğiz.</p>
<p>Piyasada örneğin <a href="http://platesphp.com/" target="_blank">Plates</a>, <a href="https://github.com/auraphp/Aura.View" target="_blank">Aura</a> veya <a href="https://laravel.com/docs/5.4/blade" target="_blank">Blade</a> gibi anlattığımız işleri gerçekleştiren kütüphaneler mevcut, ancak biz bu seride konuları temelinden aldığımız kendi sınıflarımızı kendimiz yazacağız. Daha sonra, profesyonel işlerimizde tabii ki, vakit kazanmak adına piyasadaki hazır kütüphane ve frameworkleri (uygulama çerçevelerini) kullanabiliriz. (Framework konusunu da serinin sonunda detaylıca anlatacağım.) Ancak şimdilik herşeyi kendimiz yapacağız ki, konuyu detayıyla kavrayabilelim.</p>
<p>Daha önce sınıflarımızın, bağımsız, kendi başına çalışabilen bir uygulama gibi olmaları gerektiğini, belli bir amaca ve tek bir sorumluluğa sahip olması gerektiğinden bahsetmiştik. Şimdi bu düşünceyi aklımızda tutarak View yani Görünüm sınıfımızı tasarlamaya başlayalım. Önce görünüm sınıfımızın ne yapması gerektiğine karar verelim ve son kullanıcının onu nasıl kullacağını gösterecek arayüzü oluşturalım. Peki View yani Görünüm sınıfımızın yapması gerekenler neler?</p>
<ol>
<li>Verdiğimiz veriyi, doğru dürüst bir şekilde, doğru biçim ile kullanıcıya sunmak.</li>
<li>Gerekirse, aynı veriyi, başka biçimlerle kullanıcıya sunmak. (Örneğin JSON ya da desktop uygulamasının GUI yani grafik kullanıcı arayüzüne uyumlu olacak biçimde) (JSON konusunu daha sonra detaylı olarak anlatacağım.)</li>
<li>Kullanıcının yaptığı işlemleri tespit edip ona göre kullanıcıyı yönlendirmek. Yani kullanıcı, programımızın diğer kısımları ile muhattap olmak yerine, sadece Görünüm yani View sınıfı ile muhattap olmalı.</li>
<li>İstediğimizde aynı veriyi web üzerinde ya da terminal ekranında görüntülemek için aynı arayüzü kullanan farklı View sınıfları kullanabiliriz.</li>
<li>Görünüm sınıfımızın veriyi sarmalamak için kullanacağı bir Template’si yani şablonu olmalı.</li>
</ol>
<p>View yani Görünüm sınıfını daha da karmaşıklaştırabiliriz ancak şimdilik en basit özellik ve metodları düşünerek işe başlayalım. Entry yani Girdi sınıfımız için program dizinimiz içinde EntryView.php adında bir dosya oluşturalım ve içine şu kodları ekleyelim:</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><strong>class </strong>EntryView<br>{<br><strong>private $entry</strong>;<br><br><strong>public function </strong>__construct(EntryInterface $entry = <strong>null</strong>)<br>    {<br><strong>if </strong>($entry !== <strong>null</strong>) {<br>            $this-&gt;<strong>entry </strong>= $entry;<br>        }<br>    }<br><br><strong>public function </strong>setEntry(EntryInterface $entry)<br>    {<br>        $this-&gt;<strong>entry </strong>= $entry;<br>    }<br><br><strong>public function </strong>render()<br>    {<br><strong>if </strong>(!<strong>isset</strong>($this-&gt;<strong>entry</strong>)) {<br><strong>throw new </strong>Exception(<strong>'Cannot render without entry'</strong>);<br>        }<br><br>        $title = <strong>"&lt;h3&gt;" </strong>. $this-&gt;<strong>entry</strong>-&gt;getKey() . <strong>"&lt;/h3&gt;"</strong>;<br>        $values = $this-&gt;<strong>entry</strong>-&gt;getValues();<br>        $list = <strong>""</strong>;<br><strong>foreach </strong>($values <strong>as </strong>$value) {<br>            $list .= <strong>"&lt;li&gt;" </strong>. $value . <strong>"&lt;/li&gt;"</strong>;<br>        }<br><br>        $result = <strong>"&lt;p class='entry'&gt;" </strong>. $title . <strong>"&lt;ol class='values'&gt;" </strong>. $list . <strong>"&lt;/ol&gt;" </strong>. <strong>"&lt;/p&gt;"</strong>;<br><br><strong>return </strong>$result;<br>    }<br>}</pre>
<p>Şu duruma dikkat edelim: EntryView sınıfımız, EntryInterface yani Girdi Arayüzü ile muhattap oluyor, ve Girdi sınıfını bu arayüze göre kullanıyor. Constructor yani sihirli yaratma metodumuzda paramtere EntryInterface $entry = null ifadesini kullandık. Buradaki = null ifadesi, $entry değişkeninin opsiyonel olduğunu belirtir. Yani istersek boş bir entry sınıfı oluşturabiliriz ve setEntry metodu ile istediğimiz girdiyi bu view yani görünüm sınıfı içerisine data yani veri olarak yerleştirebiliriz. Bu sayede her girdi için yeni bir görünüm sınıfı yaratmamıza gerek kalmaz.</p>
<p>Render yani sunum metodumuzda, constructor yani sihirli yaratma metodunda, $entry değişkenini opsiyonel olarak tanımladığımız için, hatalara karşı sınıf içindeki $this-&gt;entry değişkeninde tanımlı olan girdi verisini kontrol ettik ki, herhangi bir kişi, setEntry demeden veya constructor içinde girdiyi tanımlamadan render yani sunum metodunu çalıştırıp hataya yol açmasın. if (!isset($this-&gt;entry)) bloğu içinde bu kontrolü yapıyoruz.</p>
<p>Daha sonra, girdi sınıfından başlık ve değerler gibi verileri çekip, html kodu içinde sarmalıyoruz. Görünüm için başka bir sınıf oluşturup, asıl nesnenin verilerini bu şekilde sarıp sarmalamaya Decorator yani Dekoratör tasarım deseni deniyor. Tasarım desenleri kısmına geldiğimizde bu konuyu daha detaylıca anlatacağım.</p>
<p>Aslında PHP kodları içinde html etiketlerini karıştırıp kullanmayı sevmem. Bana spagetti kodu hatırlatıyor. Şimdilik kolay olması amacıyla bu şekilde anlatıyorum. Ancak daha sonra bir şablon dizini oluşturup, veriyi sarmalayacağımız HTML kodlarını ayrı ayrı php şablon dosyalarında tutacağız. View sınıfımız tema dosyasını açıp, sunumu o şekilde yapacak.</p>
<p>Şimdi Dictionary.php dosyası içinde yapmamız gereken küçük bir değişiklik var. Dictionary.php içindeki getEntries metodu bize metin dizisi döndürüyordu. Bunun yerinde EntryView sınıfını kullanacağımız için entry yani girdi dizisine ihtiyacımız var. Dosyadaki getEntries metodunun adını getEntriesAsArray olarak değiştirelim ve yeni yazacağımız getEntries metodunda doğrudan $this-&gt;entries içinde tanımlı olan girdi nesnelerinin dizisini döndürelim.</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><strong>class </strong>Dictionary <strong>implements </strong>DictionaryInterface<br>{<br><strong>private $title</strong>;<br><strong>private $entries</strong>;<br><br><strong>public function </strong>__construct(string $title)<br>    {<br>        $this-&gt;setTitle($title);<br>        $this-&gt;<strong>entries </strong>= [];<br>    }<br><br><strong>public function </strong>setTitle(string $title)<br>    {<br><strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {<br>            $this-&gt;<strong>title </strong>= $title;<br>        } <strong>else </strong>{<br><strong>throw new </strong>InvalidArgumentException(<strong>'Wrong title value.'</strong>);<br>        }<br>    }<br><br><strong>public function </strong>getTitle(): string<br>    {<br><strong>return </strong>$this-&gt;<strong>title</strong>;<br>    }<br><br><strong>public function </strong>getEntriesAsArray(): <strong>array<br></strong>{<br>        $entries = [];<br><em>/* </em><strong><em>@var </em></strong><em>$entry EntryInterface */<br></em><strong>foreach </strong>($this-&gt;<strong>entries as </strong>$entry) {<br>            $entries[$entry-&gt;getKey()] = $entry-&gt;getValues();<br>        }<br><strong>return </strong>$entries;<br>    }<br><br><strong>public function </strong>getEntries(): <strong>array<br></strong>{<br><strong>return </strong>$this-&gt;<strong>entries</strong>;<br>    }</pre>
<p>Bu sayede app.php kodu içinde girdi nesnelerinin dizisine dışarıdan erişebileceğiz. app.php dosyamızı şu şekilde değiştirelim:</p>
<pre><strong>&lt;?php<br><br>require_once 'DictionaryInterface.php'</strong>;<br><strong>require_once 'Dictionary.php'</strong>;<br><strong>require_once 'EntryInterface.php'</strong>;<br><strong>require_once 'Entry.php'</strong>;<br><strong>require_once 'EntryView.php'</strong>;<br><br><strong>try </strong>{<br>    $dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>"Nesne Yönelimli Programlama Sözlüğü"</strong>);<br><br>    $nesne = <strong>new </strong>MidoriKocakEntry(<strong>'nesne'</strong>, <strong>'aklımızın dışındaki herşey'</strong>);<br><br>    $nesne-&gt;addValue(<strong>'harika bişi'</strong>);<br>    $nesne-&gt;addValue(<strong>'ingilizce object'</strong>);<br><br>    $şey = <strong>new </strong>MidoriKocakEntry(<strong>'şey'</strong>, <strong>'ismi olmayan nesne'</strong>);<br><br>    $dictionary-&gt;addEntry($nesne);<br>    $dictionary-&gt;addEntry($şey);<br><br>    $entries = $dictionary-&gt;getEntries();<br><br><strong>foreach </strong>($entries <strong>as </strong>$entry) {<br>        $entryView = <strong>new </strong>MidoriKocakEntryView($entry);<br><strong>echo </strong>$entryView-&gt;render();<br>    }<br><br>} <strong>catch </strong>(Exception $e) {<br><strong>echo 'Error on line ' </strong>. $e-&gt;getLine() . <strong>' in ' </strong>. $e-&gt;getFile()<br>        . <strong>': &lt;b&gt;' </strong>. $e-&gt;getMessage();<br>}</pre>
<p>Yeni oluşturduğumuz EntryView dosyasını “require_once ‘EntryView.php’;” ifadesiyle dosyamıza ekledik.</p>
<p>Yaptığımız tek değişiklik, printr($entries) ifadesinin yerine şu kodları yazmak oldu:</p>
<pre><strong>foreach </strong>($entries <strong>as </strong>$entry) {<br>    $entryView = <strong>new </strong>MidoriKocakEntryView($entry);<br><strong>echo </strong>$entryView-&gt;render();<br>}</pre>
<p>foreach ifadesi ile $entries değişkeni içindeki her bir girdi nesnesine eriştik, ve her biri için yeni bir EntryView yani Girdi Görünümü sınıfı (ya da dekoratörü) yarattık. Şimdi web sunucumuzdan app.php’yi açtığımızda şöyle bir görüntünün karşımıza gelmesi gerekiyor:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/f921e-1cd0-dje_jjq8zpl_oobvha.png">

<figcaption class="wp-caption-text">HTML oluşturan sınıf</figcaption></figure><p>Şimdi biraz daha HTML sayfasına benzemeye başladı. Sayfa kaynağına baktığımızda şu kodları görmeliyiz:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/4fa46-1okqzzufbw26q_pgt391tbg.png">

<figcaption class="wp-caption-text">Sayfa Kaynağı</figcaption></figure><p>Gördüğümüz gibi, sınıfımız ham veriyi aldı ve bizim istediğimiz şekilde HTML kodlarının içine sardı. Şimdilik uygulamamız düzgün bir web sayfası gibi görünmemekle beraber, View yani görünüm sınıflarının ne işe yaradığını, dekoratör tasarım deseninin mantığını ve Ham verinin nasıl süsleneceğini iyice anladık. Bir sonraki yazıda sözlük için görünüm sınıfını oluşturacağız ve ufaktan sayfa şablonlarımızı yazmaya başlayacağız.</p>
<p>Bir sonraki yazıya şuradan ulaşabilirsiniz:</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-7-s%C4%B1n%C4%B1flar%C4%B1-kullanmak-ve-api-meselesi-a03fcbfb543b[/embed]

<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>