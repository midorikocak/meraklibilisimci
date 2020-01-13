---
ID: 42
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-5 — Sınıfı
  inşa etmek
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  http://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-5-sinifi-insa-etmek/
published: true
post_date: 2017-02-17 17:23:17
---
<figure><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/6fbe9-1sjtb0sq5eewg5hzii5co-a.png" /></figure>
Bu yazı daha önce yazdığım Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-4 yazısının devamıdır. Önce onu okumanızı öneririm.

[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-4-960bae49c4b5[/embed]

Önceki yazılarda nesne yönelimli programlama mantığını, sınıflarımızı nasıl oluşturacağımızı, tek sorumluluk prensibini, bilgi gizlemeyi, sihirli yaratıcı metotları kavramaya çalıştık. Bir önceki yazıda sadece metot isimlerini içeren arayüzler yani interface’ler yazdık. Önümüzde iki yol var:
<ol>
 	<li>Harala gürele kullanıcıyı düşünmeden sınıfların içlerini doldurmaya başlamak.</li>
 	<li>Ya da bu sınıfları kullanacak uygulamayı yazmak. Yani bu sınıfları uygulamayı yazarken test etmek ve çıkabilecek hatalara önceden önlem almak. Biz arayüz yazdığımız için kullanıcının kullanacağı kodları zaten belirtmiş olduk.</li>
</ol>
PHP’de test konusuna bu yazıda basitçe değineceğim. Çünkü kodumuzu insanlar kullanacak. Daha sonra phpUnit konusuna geldiğimizde detaylıca anlatacağım da. Bu insanların neye ihtiyaçları olduğunu, neler yapabileceklerini az çok tahmin edebiliyorsak, sınıflarımızın içlerini bu kullanıcıların yapacakları hatalara karşı dayanıklı bir şekilde doldurabiliriz. Tabii ki hiçbir kod parçası doğduğu anda hatalara karşı bağışıklık kazanmış değildir. Ama biz önceden tahmin edemeyeceğimiz durumlara olabileceğini aklımızda tutarak kodumuzu yazarsak, daha sonra kafamızı beton duvarlara vurmayız.
<figure><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/bfe7d-1vo3vmufcqmbmx4m67j0ccq.jpeg" /></figure>
<h4>Sıradan vatandaş sınıfımızı nasıl kullanır?</h4>
Sıradan vatandaş sınıfımızı arayüzlerine bakarak kullanır. Interface yani arayüz, yazdığımız sınıf için aynı zamanda bir kullanım kılavuzu işlevi de görür aslında. Bu nedenle sınıfımızı arayüze uygun hale getirmekle işe başlayabiliriz.

Şimdi Dictionary.php dosyamızın içindeki her şeyi silelim ve şu kodu ekleyelim:
<pre><strong>&lt;?php

namespace </strong>MidoriKocak;

<strong>class </strong>Dictionary <strong>implements </strong>DictionaryInterface
{
<strong>private </strong>$title;
<strong>private $entries</strong>;

<strong>public function </strong>__construct(string $title)
    {
        $this-&gt;setTitle($title);
        $this-&gt;<strong>entries </strong>= [];
    }

<strong>public function </strong>setTitle(string $title)
    {
<strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {
            $this-&gt;title = $title;
        }
    }
}</pre>
Burada yaptığımız bir kaç değişiklik var. implements kelimesini kullanarak, sınıfımızın DictionaryInterface.php içinde tanımladığımız sözlük arayüzünü kullandığını belirttik. İkinci yaptığımız değişiklik ise __construct metodunun içinde setTitle metodunu çağırdık ki, boş başlık gibi girdilerle, VALIDATION yani doğrulama kurallarımız ezilmesin. Her durumda geçerli olsun.
<figure class="wp-caption"><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/87fc9-1hf5myxbuho0ge4g-btpl0g.jpeg" />

<figcaption class="wp-caption-text">Doğrulama</figcaption></figure>
Set metotlarının hiçbir şey döndürmediğine dikkat ettiniz mi? Zorunlu olmasa da bu bir kuraldır. Peki bir kullanıcı yanlış başlık girdiğinde bundan nasıl haberimiz olacak? Ya da yanlış başlık kullanılarak sözlük yaratılmasının önüne nasıl geçeceğiz? İşte burada PHP’deki harika programlama yapısı olan try/catch yani deneme/yanılma yapısı devreye giriyor.
<h4>Dene ve Yanıl yani Try/Catch</h4>
<figure class="wp-caption"><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/bbd10-1b6lpwyda127gtoagtogawg.jpeg" />

<figcaption class="wp-caption-text">Kodu sürekli hatalara karşı kontrol edeceğiz.</figcaption></figure>
Örneğin set metotlarımızda try/Catch yani deneme yanılma blokları kullanarak, abuk subuk değerler geldiğinde kullanıcıyı bu durumdan haberdar edeceğiz ve bu duruma göre önlem alacağız ki kullanıcı programı çökertmesin. Şimdi setTitle metodumuzu şu şekilde değiştirelim:
<pre><strong>public function </strong>setTitle(string $title)
{
<strong>try </strong>{
<strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {
            $this-&gt;<strong>title </strong>= $title;
        } <strong>else </strong>{
<strong>throw new </strong>InvalidArgumentException("Wrong title value.");
        }
    } <strong>catch </strong>(Exception $e) {
<strong>echo </strong>$e-&gt;getMessage();
    }
}</pre>
Metodumuzu satır satır okuyalım.
<ol>
 	<li>Try/Catch bloklarının dışında kod olmadığına dikkat edin.</li>
 	<li>Try bloğunu açtığımızda, php yorumlayıcısından, burada olacak hataları, veya diğer bir değişle exception yani istisnai durumları gözetlemesini rica ediyoruz.</li>
 	<li>if bloğundan sonra, else bloğu ekledik ki, hatalı bir girdi olduğunda throw diyerek, önceden tanımlı istisnalardan birini fırlatalım. Burada invalidArgument yani Hatalı parametre istisnası fırlattık. Bu sayede kodu kullanan kişi, coder, yani oraya hatalı bilgi giren gerizekalı, nerede hata yaptığını anlayacak ve önlemini alacak bi zahmet. İstisna içinde göstermek istediğimiz mesajı “Wrong title value.” diyerek belirttik.</li>
 	<li>catch bloğu içerisinde Exception $e diyerek ne tipte hataya dikkat etmemiz gerektiğini tanımladık. echo $e-&gt;message ifadesiyle meydana gelen istisnanın mesajını ekrana bastık.</li>
</ol>
<figure class="wp-caption"><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/162e9-1pnkzu9sxthd_iiyklm_46w.jpeg" />

<figcaption class="wp-caption-text">İstisna yani Excetion</figcaption></figure>
Genellikle try/catch blokları bu şekilde yazılır. Ancak örneğin biz ekrana cart diye böyle birşey basarsak, bütün sitemizin ya da kullanıcıya döndürdüğümüz örneğin JSON formatındaki değerin yapısı bozulacak. (<strong>Not:</strong> JSON formatını daha sonra API bölümüne geldiğimizde detaylıca anlatacağım.) Daha sonra bu echo ifadesini değiştireceğiz, ama şimdilik böyle kalsın.

Tüm setter metotlarımızda try/catch mantığını kullanmalıyız. Bu sayede hatalı bir bilgi girişi olduğunda, nasıl bir hatayla karşılaştığımızı anlarız.

Aynı dizinde oluşturduğumuz app.php dosyasını şu şekilde değiştirelim.
<pre><strong>&lt;?php

require_once 'DictionaryInterface.php'</strong>;
<strong>require_once 'Dictionary.php'</strong>;

$dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>"Nesne Yönelimli Programlama Sözlüğü"</strong>);</pre>
Daha sonra bu dosyada sınıfımızı kullanacak diğer kodları yazacağız. Dosyayı web sunucumuzdan çağıralım. Şöyle bir görüntü karşımıza gelecek:
<figure><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/36479-1-wzrlwd5vajsyofe2uysvq.png" /></figure>
Yani diyor ki, hani verdiğin sözler, vaadettiğin public metodlar nerde? O yüzden devam edelim ve DictionaryInterface.php dosyasında tanımladığımız arayüzdeki metotları Dictionary.php dosyası içinde tanımlamaya devam edelim. setTitle metodundan sonra şu metodları sınıfımıza ekleyelim. Korkmaya gerek yok, hepsini tek tek anlatacağım.
<pre><strong>&lt;?php

namespace </strong>MidoriKocak;

<strong>class </strong>Dictionary <strong>implements </strong>DictionaryInterface
{
<strong>private $title</strong>;
<strong>private $entries</strong>;

<strong>public function </strong>__construct(string $title)
    {
        $this-&gt;setTitle($title);
        $this-&gt;<strong>entries </strong>= [];
    }

<strong>public function </strong>setTitle(string $title)
    {
<strong>try </strong>{
<strong>if </strong>(($title != <strong>""</strong>) &amp;&amp; (<em>strlen</em>($title) &lt;= 70)) {
                $this-&gt;<strong>title </strong>= $title;
            } <strong>else </strong>{
<strong>throw new </strong>InvalidArgumentException(<strong>'Wrong title value.'</strong>);
            }
        } <strong>catch </strong>(Exception $e) {
<strong>echo </strong>$e-&gt;getMessage();
        }
    }

<strong>public function </strong>getTitle(): string
    {
<strong>return </strong>$this-&gt;<strong>title</strong>;
    }

<strong>public function </strong>getEntries(): <strong>array
</strong>{
        $entries = [];
<strong>foreach </strong>($this-&gt;<strong>entries as </strong>$entry) {
            $entries[$entry-&gt;getKey()] = $entry-&gt;getValues();
        }
<strong>return </strong>$entries;
    }

<strong>public function </strong>setEntries(<strong>array </strong>$entries)
    {
<strong>try </strong>{
<strong>if </strong>(!<strong>empty</strong>($entries)) {
                $this-&gt;<strong>entries </strong>= $entries;
            } <strong>else </strong>{
<strong>throw new </strong>InvalidArgumentException(<strong>'Array cannot be empty.'</strong>);
            }
        } <strong>catch </strong>(Exception $e) {
<strong>echo </strong>$e-&gt;getMessage();
        }
    }

<strong>public function </strong>addEntry(EntryInterface $entry)
    {
        $key = $entry-&gt;getKey();
        $this-&gt;<strong>entries</strong>[$key] = $entry;
    }

<strong>public function </strong>getEntry(string $key): EntryInterface
    {
<strong>try </strong>{
<strong>if </strong>(<em>array_key_exists</em>($key, $this-&gt;<strong>entries</strong>)) {
<strong>return </strong>$this-&gt;<strong>entries</strong>[$key];
            } <strong>else </strong>{
<strong>throw new </strong>OutOfBoundsException(<strong>'Cannot find entry in dictionary'</strong>);
            }
        } <strong>catch </strong>(Exception $e) {
<strong>echo </strong>$e-&gt;getMessage();
        }
    }

<strong>public function </strong>deleteEntry(string $key)
    {
<strong>try </strong>{
<strong>if </strong>(<em>array_key_exists</em>($key, $this-&gt;<strong>entries</strong>)) {
<strong>unset</strong>($this-&gt;<strong>entries</strong>[$key]);
            } <strong>else </strong>{
<strong>throw new </strong>OutOfBoundsException(<strong>'Cannot find entry in dictionary'</strong>);
            }
        } <strong>catch </strong>(Exception $e) {
<strong>echo </strong>$e-&gt;getMessage();
        }
    }

}</pre>
Şimdi içlerini doldurduğumuz metotlara tek tek gözatalım.
<ol>
 	<li><strong>getTitle:</strong> Pek açıklayacak birşey yok. Doğrudan sözlüğün başlığını metin tipinde döndürecek.</li>
 	<li><strong>addEntry:</strong> Sözlük sınıfındaki girdiler dizisine istediğimiz başlığı ekleyecek. Burada girdi başlığının boş olup olmamasıyla, ya da girdinin açıklaması olup olmamasıyla artık ilgilenmiyoruz. Bu konular Dictionary yani sözlük sınıfımızın sorumluluğunda değil. Çünkü bunları tek bir sınıfta halletmeye kalksaydık, sözlük sınıfı devasa bir Tanrı nesnesi (God Object) olurdu, ve tek başına her boku yapmaya çalışırdı. Bu metodun içinde $entry değişkeninde girdi Arayüzü sınıfını tanımlayan (implement eden) bir girdi nesnesi geleceğinden emin olduğumuz için, gelen nesnenin doğru dürüst verilere sahip olup olmadığını doğrulamamıza gerek yok. Zaten PHP yorumlayıcısı type hinting yani tip ipucu, yani metodun parametresinin tipini EntryInterface olarak tanımladığımız için, saçma sapan bir değere izin vermeyecek. Bu yüzden tekrar try/catch bloğunda bu değeri oluşabilecek hatalara karşı kontrol etmek için doğrulama yapmamıza gerek yok. Burada daha önce arayüzü açıklarken dediğimiz gibi, set yerine add yani ekle ifadesini kullandık. Çünkü set dediğimiz zaman, sınıfa ait tek bir değişkeni değiştirmeye çalıştığımız anlaşılıyor.</li>
 	<li><strong>setEntries:</strong> Yine burada da try/catch bloğu ile gönderdiğimiz dizinin boş olup olmadığını kontrol ettik. Aslında tek tek dizinin her elemanının EntryInterface tipinde olup olmadığını da kontrol etmemiz gerekiyordu. Ancak bu metodu daha sonra, hızlıca dosyadan sınıfı oluşturmak için kullanacağımız için bu kontrolü yapmayı veriyi kaydetme kısmına bırakıyorum.</li>
 	<li><strong>getEntries:</strong> EntryInterface tipinde objelere sahip olan sınıfın $entries dizisini döndürecek olan metot. Burada kolaylık açısından, diziyi metin içeren elemanlar olarak döndürelim.</li>
 	<li><strong>getEntry:</strong> Burada try/catch bloğu ile doğrulama yaptık çünkü sorulan key yani girdi başlığı değerinin dizi içerisinde olup olmadığını kontrol etmek istiyoruz. İstisna olarak OutOfBoundsException fırlattık. Bu istisna bir dizide olmayan değere işaret ettiğimizi gösteriyor.</li>
 	<li><strong>deleteEntry:</strong> Tıpkı getEntry metodunda olduğu gibi $key değerini hatalara karşı kontrol ettik. Kod tekrarı yaptığımıza dikkat edin.</li>
</ol>
<figure class="wp-caption"><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/46eaf-18vtdrxkoc_1ypbi_2xkn1w.jpeg" />

<figcaption class="wp-caption-text">Sözlük programımızı yazmaya devam ediyoruz.</figcaption></figure>
<h4>Kod tekrarlarını önlemek</h4>
Şahsen yapılan kod tekrarlarına uyuz olan bir insan olduğum ve kopyalayıp yapıştırılan kod öbekleri, kodumuzu saçma bi şekilde şişmanlatacağından tekrarlanan kodu ayrı bir metot haline getireceğim.

Şimdi en sondaki getEntry ve deleteEntry metotlarını silelim ve şu kodu ekleyelim:
<pre><strong>private function </strong>isKeyInEntries($key) :bool
{
<strong>try </strong>{
<strong>if </strong>(!<em>array_key_exists</em>($key, $this-&gt;<strong>entries</strong>)) {
<strong>throw new </strong>OutOfBoundsException(<strong>'Cannot find entry in dictionary'</strong>);
        } <strong>else </strong>{
<strong>return true</strong>;
        }
    } <strong>catch </strong>(Exception $e) {
<strong>echo </strong>$e-&gt;getMessage();
    }
<strong>return false</strong>;
}

<strong>public function </strong>getEntry(string $key): EntryInterface
{
<strong>if </strong>($this-&gt;isKeyInEntries($key)) {
<strong>return </strong>$this-&gt;<strong>entries</strong>[$key];
    }
}

<strong>public function </strong>deleteEntry(string $key)
{
<strong>if </strong>($this-&gt;isKeyInEntries($key)) {
<strong>unset</strong>($this-&gt;<strong>entries</strong>[$key]);
    }
}</pre>
Gördüğünüz gibi isKeyInEntries adında bir metod yazdık. :bool diyerek kesinlikle bool yani true false, yani doğru yanlış tipinde bir değişken döndürmesi gerektiğini belirttik. Metodun sonuna return false koyduk ki, başta belirttiğimiz return sözüne uyalım. Eğer bunu buraya koymazsak, kullandığımız ide veya phpmd, phpcs gibi kod kontrol araçları, neden metod kodunda birşey döndürmüyorsun diyebilir. if bloğu içinde return ifadesi olması yeterli değil. Kod her durumda eğer birşey döndürmeyi taahüt ettiyse o değer tipinde bir değişkeni döndürmeli. (Not: Null Object Pattern kısmında bu konuyu detaylıca anlatacağım.)

isBilmemne şeklinde yazilan metodlar genellikle kontrol metodlarıdır ve true veya false döndürürler. Bu try/catch bloğunda yaptığımız kontrol işini bizim için yapacak olan metot. private diyerek bu metodun sadece sınıf içerisinden erişilebileceğini belirttik. Bu sayede programı kullanan herhangi bir kimsenin bu metodun varlığından haberi olmayacak. Bu şekilde metotlar içinde kullandığınız, zırt pırt tekrar eden kod bloklarını ayrı bir private metot haline getirirsek, sınıflarımızı önemli ölçüde fit bir hale getirmiş oluruz.

Şimdi örneğin hatalı bir durumda ne olacağını görmek için, app.php dosyamızı şu şekilde değiştirelim:
<pre><strong>&lt;?php

require_once 'DictionaryInterface.php'</strong>;
<strong>require_once 'Dictionary.php'</strong>;

$dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>""</strong>);
$dictionary-&gt;setTitle(<strong>"Doğru başlık"</strong>);
$dictionary-&gt;getTitle();</pre>
app.php dosyasını web sunucumuzdan çağırdığımızda şöyle bir şey karşımıza çıkmalı:
<figure class="wp-caption"><img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/bfb0b-1ziigvox8erk7fuwoej0frq.png" />

<figcaption class="wp-caption-text">Yakalanmış istisna durumu</figcaption></figure>
Gördüğümüz gibi, kodumuz hatalı girdiyi yakaladı ve php yorumlayıcısı kodun kalan kısmını çalıştırmadı. Bu sayede ne çeşit bir hatayla karşılaştığımızı anladık. Daha sonra bu hata mesajını da özelleştirmeyi göstereceğim.

Şimdilik bu kadar. Bir sonraki yazıda Girdi yani Entry sınıfımızı tanımlayacağız. Sevgiyle kalın.

<hr />

<figure class="wp-caption"><img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg" />

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure>
<em>Ben </em><a href="http://mtkocak.net" target="_blank" rel="noopener noreferrer"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank" rel="noopener noreferrer"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank" rel="noopener noreferrer"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em>
Özgeçmişim: </em><a href="http://represent.io/midorikocak.pdf" target="_blank" rel="noopener noreferrer"><em>http://represent.io/midorikocak.pdf</em></a><em>
Websitem: </em><a href="http://mtkocak.net" target="_blank" rel="noopener noreferrer"><em>http://mtkocak.net</em></a>