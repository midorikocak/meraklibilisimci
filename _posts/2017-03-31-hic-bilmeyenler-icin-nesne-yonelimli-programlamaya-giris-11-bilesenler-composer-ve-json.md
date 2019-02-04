---
ID: 30
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-11 Bileşenler,
  Composer ve JSON
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-11-bilesenler-composer-ve-json/
published: true
post_date: 2017-03-31 12:32:44
---


<p>Bu yazı <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-10-sayfa-d%C3%BCzeni-b30a3dae138f" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-10 Sayfa Düzeni</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-10-sayfa-d%C3%BCzeni-b30a3dae138f[/embed]
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/47740-1wqg0ht4dxgq08eg_rtqxlw.png">

<figcaption class="wp-caption-text">Bileşen</figcaption></figure><p>Bir önceki yazıda View yani görünüm sınıfını her türlü şemayı kullanabilecek şekle dönüştürdük ve kullandık. Şimdi teker teker public dizini altında oluşturduğumuz index.html dosyasını parçalayalım ve tema dosyalarına dönüştürelim. Daha önceden oluşturduğumuz Template yani şablon klasöründe tek tek ismini vereceğim dosyaları oluşturun ve kodlarını içine kopyalayın.</p>
<ol><li><strong>layout.php:</strong></li></ol>
<pre>&lt;!DOCTYPE <strong>html</strong>&gt;<br>&lt;<strong>html lang="en"</strong>&gt;<br>&lt;<strong>head</strong>&gt;<br>    &lt;<strong>meta charset="UTF-8"</strong>&gt;<br>    &lt;<strong>title</strong>&gt;<br><br><strong>&lt;?= </strong>$title <strong>?&gt;<br><br></strong>&lt;/<strong>title</strong>&gt;<br>    &lt;<strong>link rel="stylesheet" href="//fonts.googleapis.com/css?family=Roboto:300,300italic,700,700italic"</strong>&gt;<br>    &lt;<strong>link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.min.css"</strong>&gt;<br>    &lt;<strong>link rel="stylesheet" href="public/css/universal.css"</strong>&gt;<br>&lt;/<strong>head</strong>&gt;<br>&lt;<strong>body</strong>&gt;<br><br><strong>&lt;?= </strong>$content <strong>?&gt;<br><br></strong>&lt;<strong>script src="public/js/main.js"</strong>&gt;&lt;/<strong>script</strong>&gt;<br>&lt;/<strong>body</strong>&gt;<br>&lt;/<strong>html</strong>&gt;</pre>
<p>Bu şablon bizim için basit, hiçbirşeyi olmayan bir html sayfasının kodlarını tutuyor. Burada dikkat ettiyseniz, $title ve $content değişkenlerini tanımlamışız. Bu sayede aynı temayı kullanarak istediğimiz sayfa başlığını ve içeriğini tanımlayabiliriz. Diğer dosyalarda da aynı yöntemi kullanacağız.</p>
<p>2. <strong>header.php</strong></p>
<pre>&lt;<strong>header</strong>&gt;<br>    &lt;<strong>h1</strong>&gt;<br><br><strong>&lt;?= </strong>$title <strong>?&gt;<br><br></strong>&lt;/<strong>h1</strong>&gt;<br>    &lt;<strong>nav</strong>&gt;<br>        &lt;<strong>ul class="list horizontal"</strong>&gt;<br>            &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;About&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>            &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Terms&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>            &lt;<strong>li</strong>&gt;&lt;<strong>a href="#"</strong>&gt;Privacy&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br>        &lt;/<strong>ul</strong>&gt;<br>    &lt;/<strong>nav</strong>&gt;<br>&lt;/<strong>header</strong>&gt;</pre>
<p>Burada yine aynı $title değişkenini kullandığımıza dikkat edin. &lt;nav&gt; etiketiyle belirlediğimiz link listesi kısmı şimdilik o kadar önemli değil. İstersek o bölümü de değişken bi eleman haline getirebiliriz. Hatta yapalım. aynı klasör içinde nav.php isimli bir dosya oluşturalım. İçeriğini şu şekilde değiştirelim:</p>
<pre>&lt;<strong>nav</strong>&gt;<br>    &lt;<strong>ul class="list &lt;?= </strong>$direction <strong>?&gt;"</strong>&gt;<br><br><strong>&lt;?php foreach </strong>($links <strong>as </strong>$link): <strong>?&gt;<br><br></strong>&lt;<strong>li</strong>&gt;&lt;<strong>a href="&lt;?= </strong>$link-&gt;<strong>href ?&gt;"</strong>&gt;<strong>&lt;?= </strong>$link-&gt;<strong>textContent ?&gt;</strong>&lt;/<strong>a</strong>&gt;&lt;/<strong>li</strong>&gt;<br><br><strong>&lt;?php endforeach</strong>; <strong>?&gt;<br><br></strong>&lt;/<strong>ul</strong>&gt;<br>&lt;/<strong>nav</strong>&gt;</pre>
<p>Elemanımız links diye bir değişkene erişip onun href özelliğine ve textContent yani metin içeriğine erişmeye çalışıyor. Peki henüz böyle bir sınıf var mı? Hayır yok, çünkü daha yazmadım. Daha sonra bunun gibi elemanları da ayrı bir sınıf haline getireceğiz. Şimdilik header.php yazdığımız şekilde kalsın. Daha sonra bunun gibi elemanların sınıflarını yazmaya başladığımızda, varolan şemaları değiştirebiliriz nasılsa.</p>
<p>3. <strong>main.php</strong></p>
<pre>&lt;<strong>main</strong>&gt;<br>    &lt;<strong>aside</strong>&gt;<br><br><strong>&lt;?= </strong>$aside <strong>?&gt;<br><br></strong>&lt;/<strong>aside</strong>&gt;<br>    &lt;<strong>section</strong>&gt;<br>        &lt;<strong>h2</strong>&gt;<br><br><strong>&lt;?= </strong>$title <strong>?&gt;<br><br></strong>&lt;/<strong>h2</strong>&gt;<br><br><strong>&lt;?= </strong>$content <strong>?&gt;<br><br></strong>&lt;/<strong>section</strong>&gt;<br>&lt;/<strong>main</strong>&gt;</pre>
<p>Burda yine bileşenin başlık ve içeriğini $title ve $content değişkenleriyle belirledik.</p>
<p>4. <strong>footer.php</strong></p>
<pre>&lt;<strong>footer</strong>&gt;<br>    &lt;<strong>p</strong>&gt;<br>        Dictionary App - Copyright - Midori Kocak - 2017<br>    &lt;/<strong>p</strong>&gt;<br>&lt;/<strong>footer</strong>&gt;</pre>
<p>Şimdilik footer yani alt bilgi kısmının içeriği sabit, daha sonra yine bu eleman için istediğimiz değişkenleri tanımlayabiliriz.</p>
<p>Hazırda aynı dizin içerisinde dictionary.php ve entry.php dosyaları olmalı.</p>
<p>Ana dizindeki app.php dosyamıza geri dönelim. Hala sınıflarımızı çağırmak için iğrenç bir spagetti kodu yazıyoruz, ancak bu sorunu da çözeceğiz.</p>
<pre><strong>&lt;?php<br><br>require_once 'DictionaryInterface.php'</strong>;<br><strong>require_once 'Dictionary.php'</strong>;<br><strong>require_once 'EntryInterface.php'</strong>;<br><strong>require_once 'Entry.php'</strong>;<br><strong>require_once 'View.php'</strong>;<br><br><br><strong>try </strong>{<br><br><em>// İstediğimiz başlıkla sözlük sınıfından yeni bir nesne oluşturduk<br></em>$dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>"Nesne Yönelimli Programlama Sözlüğü"</strong>);<br><br><em>// Kelime sınıfından yeni bir nesne oluşturduk.<br></em>$nesne = <strong>new </strong>MidoriKocakEntry(<strong>'nesne'</strong>, <strong>'aklımızın dışındaki herşey'</strong>);<br><br><em>// kelimeye başka açıklamalar ekledik.<br></em>$nesne-&gt;addValue(<strong>'harika bişi'</strong>);<br>    $nesne-&gt;addValue(<strong>'ingilizce object'</strong>);<br><br><em>// Kelime sınıfından istediğimiz verilerle başka bir nesne türettik.<br></em>$şey = <strong>new </strong>MidoriKocakEntry(<strong>'şey'</strong>, <strong>'ismi olmayan nesne'</strong>);<br><br><em>// bu iki kelimeyi sözlük nesnesine ekliyoruz.<br>    // Bu sayede sözlük kelime nesnelerine erişebiliyor.<br></em>$dictionary-&gt;addEntry($nesne);<br>    $dictionary-&gt;addEntry($şey);<br><br><em>// View yani görünüm sınıfından yeni bir nesne oluşturduk.<br></em>$dictionaryView = <strong>new </strong>MidoriKocakView();<br><br><em>// Görünüm sınıfı içindeki data dizisine dictionary anahtarıyla sözlük değişkenimizi ekledik.<br>    // Bu sayede, dictionary.php adlı şablon dosyasına, $dictionary yazan yerde, bu nesneye erişim<br>    // sağlanacak. Örneğin $dictionary-&gt;getTitle() gibi.<br>    // Aslında şablonların sınıflara bu şekilde erişmesi doğru olmayabilir, ancak şimdilik böyle bırakalım.<br></em>$dictionaryView-&gt;set(<strong>'dictionary'</strong>, $dictionary);<br><br><em>// Görünüm yani view sınıfımıza dictionary.php tema dosyasını kullanarak içeriği vermesini söyledik.<br>    // Bu gelen içeriği dictionaryContent adlı bir değişkene atadık ki daha sonra bu veriyi kullanabilelim.<br></em>$dictionaryContent = $dictionaryView-&gt;render(<strong>'dictionary'</strong>);<br><br><em>// Elemanları oluşturmaya başladık<br>    // Yine görünüm sınıfından yeni bir nesne türettik ve değişkenlerini belirledik.<br>    // Burada header yani üst bilgi kısmını oluşturduk.<br></em>$header = <strong>new </strong>MidoriKocakView();<br>    $header-&gt;set(<strong>'title'</strong>, <strong>'Sözlük Uygulaması'</strong>);<br>    $headerContent = $header-&gt;render(<strong>'header'</strong>);<br><br><em>// Main elemanını oluşturduk ve değişkenlerini belirledik.<br></em>$main = <strong>new </strong>MidoriKocakView();<br>    $main-&gt;set(<strong>'aside'</strong>, <strong>'aside'</strong>);<br>    $main-&gt;set(<strong>'title'</strong>, <strong>'Sözlüklerim'</strong>);<br>    $main-&gt;set(<strong>'content'</strong>, $dictionaryContent);<br>    $mainContent = $main-&gt;render(<strong>'main'</strong>);<br><br><em>// footer elemanını oluşturduk.<br></em>$footer = <strong>new </strong>MidoriKocakView();<br>    $footerContent = $footer-&gt;render(<strong>'footer'</strong>);<br><br><em>// Son olarak page yani sayfa diye bir değişken oluşturduk. <br><br></em>$page = <strong>new </strong>MidoriKocakView();<br><br><em>// Önceki elemanlarda olduğu gibi değişkenleri belirledik.<br></em>$page-&gt;set(<strong>'title'</strong>, <strong>'Sözlük Uygulaması'</strong>);<br><br><em>// Buraya dikkat, burada 3 ayrı hazırlanmış temanın içeriğini birbirine ekledik<br>    // Ve bunu content olarak tanımladık ki, layout.php'deki $content değişkeninin<br>    // bulunduğu yerde bu birbirine eklenmiş 3 içerik görünsün.<br></em>$page-&gt;set(<strong>'content'</strong>, $headerContent . $mainContent . $footerContent);<br><br><em>// layout.php'yi yani sayfa düzeni şablonunu kullanarak çıktı aldık.<br></em><strong>echo </strong>$page-&gt;render(<strong>'layout'</strong>);<br><br>} <strong>catch </strong>(Exception | Error $e) {<br><strong>echo 'Error on line ' </strong>. $e-&gt;getLine() . <strong>' in ' </strong>. $e-&gt;getFile()<br>        . <strong>': &lt;b&gt;' </strong>. $e-&gt;getMessage();<br>}</pre>
<p>Bu kodu web sunucumuzu kullanarak çalıştırdığımızda şöyle bir görüntüyle karşılaşmalıyız.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/17c1f-1fnctp509sjzfmstfddl-mq.png">
</figure><p>Aside kısmında sadece aside kelimesini görüntüledik. Bu bir hata değil.</p>
<p>Şimdi kodumuzu satır satır inceleyelim. $dictionaryContent = $dictionaryView-&gt;render(‘dictionary’); ifadesine kadar herşey önceki yazıda yaptığımız şeylerle aynı. Önceki yazıda kodlarımızda yorumlar yoktu ancak ben daha kolay anlaşılması için bunları ekledim. Bu kod bloğu içinde daha iyi olabilecek şeyler var. Bunları tek tek anlatacağım. En baştan başlayalım.</p>
<h4>Composer aracı, Programımıza yeni bileşenler eklemek, bileşenleri yönetmek ve kolayca kullanmak</h4>
<p>app.php dosyasını açtığımızda ilk karşılaştığımız satırlar şu şekilde. Yanlış değil de daha temiz şekilde yapılabilecek şeyler var.</p>
<pre><strong>&lt;?php<br><br>require_once 'DictionaryInterface.php'</strong>;<br><strong>require_once 'Dictionary.php'</strong>;<br><strong>require_once 'EntryInterface.php'</strong>;<br><strong>require_once 'Entry.php'</strong>;<br><strong>require_once 'View.php'</strong>;</pre>
<p>Buradaki sorun, ihtiyaç duyduğumuz bütün sınıfları tek tek dosyanın üzerine yazmak zorunda oluşumuz. Biz 5 adet sınıf kullandığımız için bu pek sorun değil. Ancak çok kapsamlı bir yazılımda onlarca kütüphaneye ihtiyaç duyduğumuzu düşünürsek, atıyorum 64 adet dosyayı buraya tek tek yazmamız zor. Ayrıca sınıfları dosya isimleriyle tek tek çağırmak beni mutlu etmiyor. Bir de, çağırdığımız dosyaların yeni mi, eski mi, programda eriştiğimiz şekilde hata oluşturmadan çalışabileceklerinden emin olamıyoruz. Çünkü başka bir programcı girip o dosyayı darmadağın edebilir. Bu meseleyi <strong>composer</strong> denen vazgeçilmez aracı kullanarak hallediyoruz. Composer programını tıpkı telefondaki uygulamaları yüklediğiniz AppStore, PlayStore gibi programlar gibi düşünebilirsiniz. Composer sayesinde yazılımınızın ihtiyaç duyduğu kütüphane, uygulama ve sınıfları otomatik olarak ihtiyaç duyduğunuz paket isimlerini sürümleriyle beraber programınızın kök dizininde oluşturacağınız composer.json dosyasına yazacaksınız. composer install komutunu çalıştırdığınız anda composer programı, belirlediğimiz paketleri vendor dizinine göre sürüm numaralarını kullanarak indirecek, ve autoloader.php adında bir dosya oluşturacak. Biz yukarıdaki gibi bağımlılıkları tek tek yazmak yerine sadece bu autoloader.php dosyasını programımızda require komutu ile çağıracağız ve ihtiyaç duyduğumuz uygulama, sınıf ve kütüphanelere tek tanımlamayla erişebileceğiz. Ayrıca bileşenleri güncellemek istediğimizde bunları her bileşenin kodunu kaynağından indirip kopyala yapıştır yapmayla uğraşmak yerine otomatik olarak yapabileceğiz.</p>
<p><strong>Composer Kurulumu</strong></p>
<p>Windows ortamında çalışıyorsanız Composer aracını kurmak için en kolay yöntem <a href="https://getcomposer.org/Composer-Setup.exe" target="_blank">https://getcomposer.org/Composer-Setup.exe</a> dosyasını indirip çalıştırmak. Linux ve Mac ortamında çalışıyorsanız, <a href="https://getcomposer.org/installer" target="_blank">https://getcomposer.org/installer</a> dosyasını indirip, terminal üzerinde `php installer`diyerek çalıştırmanız gerekiyor. Program sizin ortamınıza göre gerekli düzenlemeleri yapıp kurulumu otomatik olarak gerçekleştiriyor. Daha çok ayrıntı için <a href="https://getcomposer.org/doc/00-intro.md" target="_blank">https://getcomposer.org/doc/00-intro.md</a> sayfasına bakmanızı öneririm.</p>
<h4>PHP için AppStore: Packagist</h4>
<p>Composer ile kullanabileceğimiz diğer bir eşsiz araç ise <a href="http://www.packagist.org" target="_blank">Packagist.org</a>. Packagist.org sitesi sayesinde istediğimiz konuyla ilgili herhangi bir kütüphane veya uygulamaya kolaylıkla erişebiliyoruz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/ff38a-1os4igyg4lhsfryiwu0shvq.png">

<figcaption class="wp-caption-text">Packagist.org</figcaption></figure><p><a href="http://www.packagist.org" target="_blank">Packagist.org</a> sitesini, Android telefonlardaki Google Play Store veya Apple telefonlardaki AppStore uygulamalarına benzetebiliriz. Kayıtlı tüm php kütüphane, sınıf veya uygulamalarının güncel ve geçmiş sürümlerine buradan ulaşabilir, kelime bazlı arama yapabiliriz. Composer ile bir bileşeni kendi uygulamamızda kullanmak istediğimizde, composer aracı, girdiğimiz uygulamanın isminin packagist.org üzerinde kayıtlı olup olmadığına bakar, ve kayıtlı ise programımızın kök dizininde vendor adlı bir dizin oluşturur. Packagist üzerinde kayıtlı olan eklemek istediğimiz bileşeni, çoğunlukla github üzerinden indirir ve vendor dizinine kaydeder. Ayrıca vendor dizini altında autoload.php adlı bir dosya oluşturur. Biz de kendi uygulamamızı kullanırken tek tek bütün dış veya kendi yazdığımız bileşenleri require ile yukarıda yaptığımız gibi çağırmak yerine, autoload.php require komutu ile çağırarak tek bir seferde erişebiliriz.</p>
<h4>Composer kullanımı</h4>
<p>Şimdi composer’i nasıl kullanacağımıza bir göz atalım. Windows üzerinde CMD ile, Mac veya Linux ortamında komut satırı ile composer’i composer komutunu kullanarak çağırabildiğimizi farzediyorum.</p>
<p>Şu ana kadar yazdığımız sözlük programının dizini şu şekilde görünüyor olmalı:</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/dc4e6-1t2avfxs2utl9kpwyuongla.png">
</figure><p>Eğer programı şu ana kadar web sunucusunu kullanarak çalıştırabildiyseniz, bir iki dosya farklılığı olması o kadar önemli değil. Yazdığımız sözlük programının dosyalarının olduğu dizine gidelim ve o dizinde şu komutu çalıştıralım:</p>
<pre>$&gt; composer require phpunit/phpunit</pre>
<p>Burada require ifadesiyle programımızın phpunit adlı bileşene ihtiyaç duyduğunu belirtiyoruz. <strong>phpunit</strong> nedir diyorsanız, programımızı test etmemize yarayan vazgeçilmez bir test aracı. Ona da bir sonraki bölümde detaylıca değineceğim. Composer vendor adlı bir dizin oluşturacak ve tek tek gerekli bileşenleri o dizine indirecek. İndirmesi, internet bağlantınızın hızına göre uzun sürebilir, telaşa kapılmayın. İşlem bittikten sonra ekrana şöyle bir görüntü gelmesi gerek. Eğer hata aldıysanız, dosya dizin izinlerinizi kontrol etmenizi öneririm. Ayrıca composer kurulumunuzda da sorun olabilir.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/1c300-1lp4qvs2bckwiyfqae3atwg.png">

<figcaption class="wp-caption-text">Görüntü bu şekildeyse sorun yok.</figcaption></figure><p>Şimdi sözlük programımızın olduğu dizine tekrar bakalım.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/b2699-194rel-vx0fgunmt38zlo3g.png">

<figcaption class="wp-caption-text">Composer’den sonra</figcaption></figure><p>1 adet yeni dizin ve 2 yeni dosya oluştuğunu görüyoruz. Bunları tek tek anlatayım:</p>
<h4>Vendor dizini</h4>
<p>Vendor dizini programımızın ihtiyaç duyduğu ve composer tarafından indirilen bileşenlerin tutulduğu dizindir. Ayrıca indirdiğimiz bileşenlerin getirdiği ek araçlar varsa onlar da bu dizinde tutulur. Ayrıca herşey indirilip bittikten sonra, autoload.php adlı, bizim tüm bileşenleri kullanıcı programımıza eklememizi sağlayan dosyayı da oluşturur composer. Şimdi vendor dizinine bir göz atalım:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/a73fe-1-tnc9u4fkhxzp-a0iyj6wg.png">

<figcaption class="wp-caption-text">Vendor dizini içeriği</figcaption></figure><p>Burada bin, komut satırı, terminal ya da cmd’den çağırabileceğimiz araçları içeren dizindir. Örneğin, phpunit aracı buraya yüklenmiş durumda. İhtiyaç duyduğumuzda buradan çağırabiliriz.</p>
<p>Composer dizininde composer’in kendi ihtiyaç duyduğu dosyalar bulunuyor. Bu dosyalar autoload.php tarafından erişiliyor. Bence fazla kurcalamaya gerek yok. Üzümünü ye bağını sorma demişler yani information hiding. Ancak composer’in nasıl çalıştığını merak ediyorsanız dosyaların içini açıp bakabilirsiniz. Açık kaynağın güzelliği de burada.</p>
<p>Diğer tüm dizinler, phpunit aracının ihtiyaç duyduğu ek kütüphaneler ve uygulamaları içeriyor.</p>
<p>Burada composer.json dosyasını inceleyeceğiz ancak json formatından bahsetmemiz gerekiyor. Eğer json formatını biliyorsanız JSON bölümünü atlayabilirsiniz.</p>
<h4>JSON</h4>
<p>JSON kısaltması “JavaScript Object Notation” yani Javascript Nesne Gösterimi anlamına geliyor. Javascript’te nesneleri nasıl tanımlıyorsak, json dosyalarını o şekilde biçimlendiriyoruz. Son zamanlarda JSON biçimi, internet üzerinden veri gönderip almada standart hale geldi diyebiliriz. Çünkü daha önce kullanılan xml formatı aynı veriyi tanımlamak için daha uzun dosyalara ihtiyaç duyuyor. Örnek vereceğim ama önce json’u tanımaya devam edelim.</p>
<p>JSON dosyaları Nesne veya Dizi şeklinde şeklinde olabilirler. Biz nesne tanımlama ile başlayalım. Buradaki JSON örneklerini data.json diye kaydedip istediğimiz json dosyasında hata almadan kullanabiliriz.</p>
<pre>{<br><br>}</pre>
<p>Burada boş bir JSON nesnesi oluşturduk. Eğer <a href="https://jsonformatter.curiousconcept.com/#" target="_blank">https://jsonformatter.curiousconcept.com/</a> adresine gidip bu kodu yazarsak, kodun valid json olduğunu göreceğiz. Siz de json örnekleri oluşturmak istediğinizde, kodunuzu kontrol etmek için bu aracı kullanabilirsiniz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/f21ce-1qss4nlncfvskaxsrsfghwa.png">

<figcaption class="wp-caption-text">Json kodunu test etmek</figcaption></figure><p>Json nesneleri verileri “anahtar”:değer şeklinde tutarlar.</p>
<pre>{<br><strong>"name"</strong>: <strong>"Deniz"</strong>,<br><strong>"lastname"</strong>: <strong>"Mahir"</strong>,<br><strong>"age"</strong>: 30,<br><strong>"immortality"</strong>: <strong>true<br></strong>}</pre>
<p>Örneğin bir burada çift tırnak kullanarak tanımladığımız kelimeler, anahtar isimlerini belirtirler ve benzersiz olmak durumundadırlar. Yani aynı kişinin birden fazla soyadı alanı olamaz. JSON aslında PHP’de Dizi/Array veri yapısına benziyor bir bakıma.</p>
<p>Değer kısmında kullanabileceğimiz veri tipleri ise kısıtlı. Bir JSON değeri, bir metin, bir sayı, bir nesne, bir dizi, doğru/yanlış şeklinde boolean değer ve null tipinde olabilir. Json formatında değerler javascript nesnelerinde olduğu gibi fonksiyon, tarih ve undefined yani tanımsız tipinde olamazlar. Olurlarsa, JSON okuyan program hata verir. Kodumuz patlar ağlarız. Kaynak: <a href="https://www.w3schools.com/js/js_json_syntax.asp" target="_blank">https://www.w3schools.com/js/js_json_syntax.asp</a></p>
<p>JSON ayrıca veriyi dizi yani array olarak kaydetmemize de imkan veriyor.</p>
<pre>[<br><strong>"Ethem"</strong>,<br><strong>"Abdullah"</strong>,<br><strong>"Ali İsmail"</strong>,<br><strong>"Ahmet"</strong>,<br><strong>"Medeni"</strong>,<br><strong>"Mehmet"</strong>,<br><strong>"Hasan"</strong>,<br><strong>"Berkin"<br></strong>]</pre>
<p>Burada metin tipindeki verileri dizi olarak json dosyasına kaydettik. Dikkat. Tek bir json dosyasında, tek bir nesne ya da tek bir dizi olmalı. Eğer birden fazla nesneyi tek dosyada tutmamız gerekseydi nesneleri dizinin içinde tutacaktık.</p>
<pre>[<br>  {<br><strong>"name"</strong>: <strong>"Ethem"</strong>,<br><strong>"age"</strong>: 27<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Abdullah"</strong>,<br><strong>"age"</strong>: 22<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Ali İsmail"</strong>,<br><strong>"age"</strong>: 19<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Ahmet"</strong>,<br><strong>"age"</strong>: 22<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Medeni"</strong>,<br><strong>"age"</strong>: 18<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Mehmet"</strong>,<br><strong>"age"</strong>: 19<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Hasan Ferit"</strong>,<br><strong>"age"</strong>: 21<br>  },<br>  {<br><strong>"name"</strong>: <strong>"Berkin"</strong>,<br><strong>"age"</strong>: 15<br>  }<br>]</pre>
<p>Ayrıca bir nesne içinde bir değeri dizi olarak da tanımlayabiliriz. <a href="https://www.w3schools.com/js/js_json_arrays.asp" target="_blank">Kaynak</a></p>
<pre>{<br><strong>"name"</strong>:<strong>"John"</strong>,<br><strong>"age"</strong>:30,<br><strong>"cars"</strong>:[ <strong>"Ford"</strong>, <strong>"BMW"</strong>, <strong>"Fiat" </strong>]<br>}</pre>
<p>Şimdi JSON’un nasıl tanımlandığını ve söz dizimi yapısını kısaca anladığımıza göre PHP’de nasıl kullanıyoruz ona bakalım. PHP’de json için kullandığımız iki fonksiyon mevcut. Bunlar <strong>json_encode()</strong> ve <strong>json_decode()</strong> yöntemleri. json_encode, bir diziyi geçerli bir JSON metnine dönüştürür. json_decode fonksiyonu ise geçerli bir json metnini, dizi ya da nesneye dönüştürür. Örneğin, $array = json_decode($jsonString, true) dediğimizde json verilerine birebir sahip olan bir php dizisi elde ederiz. Eğer true kullanmadan doğrudan $object = json_decode($jsonString) deseydik, elemanlarına $object-&gt;name gibi ifadeler kullanarak erişebileceğimiz nur topu gibi bir nesneye sahip olacaktık. Nesnelerin saklanması, metine çevirilmesi, ekrana basılması, klonlanması ve uyandırılması (metinden tekrar nesne üretilmesi) gibi konulara daha sonra detaylıca değineceğim.</p>
<p>Daha sonra programlar ya da sınıflar arası ya da internet üzerinde veri alışverişi yaparken JSON verisini PHP ile bol bol kullanacağız. (Anahtar kelimeler: AJAX, curl, stream, request, response, JS:promise)</p>
<p>JSON kısmını anladığmıza göre composer.json dosyasına geri dönelim.</p>
<h4>composer.json</h4>
<p>Composer.json adlı dosya, ithiyaç duyduğumuz bileşenlerin çetelesini tuttuğumuz liste aslında. Açıp bakalım.</p>
<pre>{<br><strong>"require"</strong>: {<br><strong>"phpunit/phpunit"</strong>: <strong>"^6.0"<br></strong>}<br>}</pre>
<p>Burada require olarak tanımlanan değer programımızın ihtiyaç duyduğu bileşenleri listelememize yarıyor. phpunit adlı github kullanıcısının yine phpunit adlı kütüphanesine erişmek istediğimizi belirtmişiz. Değer olarak belirlediğimiz ifade ise ihtiyaç duyduğumuz paketin versiyonu. “^6.0” ifadesiyle 6 ve 7 sürümleri arasındaki herhangi bir sürüm işimizi görür demişiz. Geçmiş bir sürüme ihtiyaç duysaydık, onu da burada ifade edecektik.</p>
<p>Örneğin programımızı birine göndermek isteseydik, vendor klasörünü doğrudan silip sadece kendi yazdığımız kaynak dosyalarını ve composer.json dosyasını daha kısa sürede gönderebilirdik. Bu sayede gönderdiğimiz kişi composer install komutunu kullanarak bileşenleri ayrıca yükleyebilir.</p>
<h4>composer.lock</h4>
<p>Bu dosya composer aracı tarafından otomatik olarak oluşturulan bir dosya. Vendor dizini içine kaydedilmiş bütün bileşenlerin sürüm numaralarının kaydedildiği bir dosya. Bununla ilgili Davey Shafik <a href="https://blog.engineyard.com/2014/composer-its-all-about-the-lock-file" target="_blank">şu adreste</a> konuyu şöyle açıklamış:</p>
<p><code>composer install</code> çalıştığında:</p>
<ul>
<li>
<code>composer.lock</code> dosyası ver mı yok mu bakılır.</li>
<li>Yoksa <code>composer update</code> çalıştırılır ve bir adet yaratılır.</li>
<li>
<code>composer.lock</code> dosyası mevcutsa, lock dosyasında belirtilen sürümler yüklenir.</li>
</ul>
<p><code>composer update</code> yani güncelleme komutu çalıştığında:</p>
<ul>
<li>
<code>composer.json</code> var mı yok mu bakılır.</li>
<li>Belirlediğimiz versiyona göre bağımlı olunan bileşenlerin en son sürümleri belirlenir.</li>
<li>En son sürümler yüklenir, yani güncelleme yapılır.</li>
<li>Son olarak <code>composer.lock</code> en son sürümü yüklenmiş bileşenleri göstermesi için yeni sürüm numaralarıyla güncellenir.</li>
</ul>
<p>Kaynak: <a href="https://blog.engineyard.com/2014/composer-its-all-about-the-lock-file" target="_blank">https://blog.engineyard.com/2014/composer-its-all-about-the-lock-file</a></p>
<p>Bu iki dosya ve dizini de anladığımıza göre composer’in nasıl yüklendiğini ve composer ile nasıl bileşenlerin programımıza indirildiğini anlamışız demektir. Bir sonraki yazıda, app.php kodumuzu satır satır incelemeye devam edeceğiz ve işleri nasıl daha iyi yapabileceğimize bakacağız.</p>
<p>Bir sonraki yazı şurda:</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-10-sayfa-d%C3%BCzeni-b30a3dae138f[/embed]
<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>