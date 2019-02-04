---
ID: 757
post_title: >
  PHP ile içerik yönetim sistemi – 12
  SON Ayarlar
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-12-son-ayarlar/
published: true
post_date: 2014-09-02 21:07:19
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/7_main.jpg"><img class="alignnone size-large wp-image-758" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/7_main.jpg?w=680" alt="7_main" width="680" height="382" /></a>

Son sınıf olarak sitenin başlığını, açıklamasını ve altbilgisini (footerda bulunan copyright cümlesini) veritabanında tutacak olan ayar sınıfını gerçekleştireceğiz. Libs klasörü altında settings php dosyasını oluşturalım. Settings yine App.php içinde bulunan soyut sınıfı genişletecek. o sınıfta bulunan add edit delete index ve view soyut (yani içleri boş olan) sınıfların da için Settings yani ayarlar sınıfında yazacağız. Bir ayar sistemde varsa ikinci bir ayar eklenemeyecek. İndex, view ve show metodları da listeleme yapacak birden fazla ayar olmadığı için edit metodunun sonucunu gösterecek. Yani index, show gibi metodlara erişmek istediğimizde edit metoduna ulaşmamız gerekiyor. Bu metodlara doğal olarak View klasörü altında görünüm dosyası oluşturmayacağımızdan, bir önceki yazıda açıkladığım sonuç dizisine eklediğimiz renderFile anahtarı ile hangi görünümü kullanacağımızı tanımlayacağız ve görüntüleme işlemlerini yapan App sınıfı bu değişkeni gördüğünde, o görünümü kullanacak. Şimdi sırayla Settings (Ayarlar) sınıfını ve metodlarını inceleyelim:

[code language="php"]
&lt;?php
/**
 * Tüm sistemdeki ayarları yönetecek sınıftır.
 *
 * Sistemin kurulumunu yapan ve ayarları yöneten sınıf. Sadece tek bir ayar olmasına izin vermeli.
 *
 * @author     Midori Kocak &lt;mtkocak@mtkocak.net&gt;
 */

namespace Midori\Cms;

use \PDO;

class Settings extends Assets
{

    /**
     * Site Başlığı
     *
     * @var string
     */
    public $title;

    /**
     * Site açıklaması
     *
     * @var string
     */
    public $description;

    /**
     * Site altbilgisi
     *
     * @var string
     */
    public $copyright;

[/code]

Yine her sınıfta olduğu gibi veritabanında bu tabloda olan değişkenleri tanımladık. Add yani ekle metodu ile devam edelim:

[code language="php"]
    /**
     * Sisteme ayar ekleyen metod. Bir nevi kurulum da denilebilir.
     * Ancak önce sistemde ayar olup olmadığını kontrol etmeli, ayar varsa, hata vermelidir.
     *
     * @param string $title Site başlığı
     * @param string $description Yönetici parola
     * @param string $copyright Yönetici e-posta
     * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
     */
    public function add($title = null, $description = null, $copyright = null)
    {

        if (!$this-&gt;checkLogin()) {
            return false;
        }

        $settings = $this-&gt;view();
        if (!empty($settings['setting'])) {

            return array('template' =&gt; 'admin', 'render' =&gt; true, 'setting' =&gt; $settings['setting'], 'renderFile' =&gt; 'edit');
        }

        if ($title != null) {
            $settings = $this-&gt;show();

            if (!empty($settings['settings'])) {
                return false;
            }

            // Önce veritabanı sorgumuzu hazırlayalım.
            $query = $this-&gt;db-&gt;prepare(&quot;INSERT INTO settings SET title=:baslik, description=:aciklama, copyright=:altbilgi&quot;);

            $insert = $query-&gt;execute(array(
                &quot;baslik&quot; =&gt; $title,
                &quot;aciklama&quot; =&gt; $description,
                &quot;altbilgi&quot; =&gt; $copyright
            ));

            if ($insert) {
                // Veritabanı işlemi başarılı ise sınıfın objesine ait değişkenleri değiştirelim
                $this-&gt;id = $this-&gt;db-&gt;lastInsertId();
                $this-&gt;title = $title;
                $this-&gt;description = $description;
                $this-&gt;copyright = $copyright;

                return true;
            } else {
                return false;
            }
        } else {
            return array('render' =&gt; true, 'template' =&gt; 'admin');
        }
    }
[/code]

Metod önce kullanıcının admin panelinde oturum açıp açmadığını ve daha sonra sistemde hali hazırda ayar olup olmadığını kontrol ediyor. Eğer zaten ayar varsa, ("if (!empty($settings['settings'])) {" işlemi) false yani yanlış değeri döndürerek metodun çalışmasını sonlandırıyor.

Daha sonra her zamanki veritabanı işlemleri ile metodumuzu tamamlıyoruz. Daha sonra view yani görüntüleme metodu geliyor.

[code language="php"]
    /**
     * Tek bir ayar verisini edit işlemine yani ayar sayfasına gönderen metod. Render edilmesin
     *
     * @param int $id ayarın benzersiz index'i
     * @return array gösterilebildyise dizi türünde verileri döndürsün, gösterilemediyse false, yanlış değeri döndürsün
     */
    public function view($id = null)
    {

        // Eğer daha önceden sorgu işlemi yapıldıysa, sınıf objesine yazılmıştır.
        if ($id != null &amp;&amp; $id == $this-&gt;id) {
            return array(&quot;id&quot; =&gt; $this-&gt;id, &quot;title&quot; =&gt; $this-&gt;title, &quot;description&quot; =&gt; $this-&gt;description, &quot;copyright&quot; =&gt; $this-&gt;copyright);
        } else {

            // Buradan anlıyoruz ki veri henüz çekilmemiş. Veriyi çekmeye başlayalım
            $query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM settings LIMIT 1&quot;);
            $query-&gt;execute();
            if ($query) {
                $setting = $query-&gt;fetch(PDO::FETCH_ASSOC);

                $this-&gt;id = $setting['id'];
                $this-&gt;title = $setting['title'];
                $this-&gt;description = $setting['description'];
                $this-&gt;copyright = $setting['copyright'];

                $result = array('template' =&gt; 'admin', 'render' =&gt; true, 'setting' =&gt; $setting, 'renderFile' =&gt; 'edit');
                return $result;
            }
        }

        // Eğer işlem başarısız olduysa, false, yanlış değer döndürelim.
        return false;
    }
[/code]

Bu metodun ise görüntülenmesine gerek yok. Veritabanından ayar bilgisi olup olmadığını kontrol ediyor ve varolan ayar olarak sonuç dizisinde döndürüyor. Daha önce bahsettiğim renderFile değişkeninde belirtildiği üzere edit kullanıyor.

Show ve index metodları da yine aynı şekilde edit sonucunu döndürecek. Hatta index metodunu hiç yazmayacağız bile. Doğrudan sınıf içindeki edit metodunu çağırıp sonucunu göstereceğiz.

[code language="php"]
   /**
     * Tüm ayarların listelenmesini sağlayan metod. Edit temasını kullanır.
     *
     * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
     */
    public function show()
    {
        if (!$this-&gt;checkLogin()) {
            return false;
        }
        $oldData = $this-&gt;view();
        return array('template' =&gt; 'admin', 'render' =&gt; true, 'setting' =&gt; $oldData['setting'], 'renderFile' =&gt; 'edit');
    }

    /**
     * Kullanıcıların listelenmesini sağlayan metod. Bu metod boş olmalı
     *
     * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
     */
    public function index()
    {
        if (!$this-&gt;checkLogin()) {
            return false;
        }
        return $this-&gt;show();
    }
[/code]

En önemli metodumuz ve sınıfın heryerinde kullandığımız edit metodu:

[code language="php"]
    /**
     * Ayarı düzenlemeye yarar. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
     * güncelleyen metod.
     *
     * @param int $id Kategorinin benzersiz index'i
     * @param string $username Yönetici kullanıcı adı
     * @param string $username Yönetici parola
     * @param string $username Yönetici e-posta
     * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
     */
    public function edit($title = null, $description = null, $copyright = null)
    {
        if (!$this-&gt;checkLogin()) {
            return false;
        }
        $oldData = $this-&gt;view();
        $id = $oldData['setting']['id'];
        if ($title != null) {
            // Önce veritabanı sorgumuzu hazırlayalım.
            $query = $this-&gt;db-&gt;prepare(&quot;UPDATE settings SET title=:baslik, description=:aciklama, copyright=:altbilgi WHERE id=:id&quot;);

            $update = $query-&gt;execute(array(
                &quot;id&quot; =&gt; $id,
                &quot;baslik&quot; =&gt; $title,
                &quot;aciklama&quot; =&gt; $description,
                &quot;altbilgi&quot; =&gt; $copyright
            ));

            if ($update) {
                return true;
            } else {
                return false;
            }
        } else {
            return array('template' =&gt; 'admin', 'render' =&gt; true, 'setting' =&gt; $oldData['setting']);
        }
    }
[/code]

Edit yani güncelleme metodu, önce sınıfın içindeki view metodundan bilgiyi alıyor. Daha sonra da kendi görünümü ile render ediliyor yani işleniyor. son olarak da delete yani silme metodunu gerçekleştireceğiz. Sistemde eğer ayar tanımlıysa bunun silimesini değil sadece güncellenmesini istiyoruz:

[code language="php"]
    /**
     * Ayar silen metod, verilerin silinmesini sağlar. Ayar silinemeyeceği için içi boş.
     * Geri dönüşü yoktur.
     *
     * @param int $id Kategorinin benzersiz index'i
     * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
     */
    public function delete($id = null)
    {
        return array('template' =&gt; 'admin', 'render' =&gt; false, 'message' =&gt; 'Ayar silinemez!');
    }
[/code]

Kişi eğer bu metoda erişmeye çalışırsa doğrudan "Ayar silinemez!" mesajını görecek.

Görüntü dosyalarımız da View klasörünün içindeki Settings dizinindeki add ve edit.php dosyaları. Bunların da veriyi işleme dışında pek farkları yok. Edit.php içinde sadece hazır olan $setting değşkenini value yani değer olarak formun içine yediriyoruz:

[code language="php"]
&lt;?php
/*
*
* Sistem ayarlarının düzenlendiği sayfa
*
* @author Midori Kocak 2014
*
*/
?&gt;
&lt;form action=&quot;/Cms/index.php/Settings/edit&quot; method=&quot;post&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Site Başlığı
                &lt;input id=&quot;title&quot; name=&quot;title&quot; type=&quot;text&quot; placeholder=&quot;Site Başlığı&quot; value=&quot;&lt;?=$setting['title']?&gt;&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Site Açıklaması
                &lt;input id=&quot;description&quot; name=&quot;description&quot; type=&quot;text&quot; placeholder=&quot;Site Açıklaması&quot; value=&quot;&lt;?=$setting['description']?&gt;&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Site Altbilgi
                &lt;input id=&quot;copyright&quot; name=&quot;copyright&quot; type=&quot;text&quot; placeholder=&quot;Site Altbilgisi&quot; value=&quot;&lt;?=$setting['copyright']?&gt;&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;button type=&quot;submit&quot;&gt;Submit&lt;/button&gt;
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/form&gt;
[/code]

Add.php de aynı dosyanın value yani değer değişkenleri olmayan hali:

[code language="php"]
&lt;?php
/*
*
* Siteye ilk ayarların eklendiği sayfa
*
* Veriyi kullanıcıdan alacak ve gerekli yerlere göndereceğiz.
*
* @author Midori Kocak 2014
*
*/
?&gt;
&lt;form action=&quot;/Cms/index.php/Settings/add&quot; method=&quot;post&quot;&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Site Başlığı
        &lt;input id=&quot;title&quot; name=&quot;title&quot; type=&quot;text&quot; placeholder=&quot;Site Başlığı&quot; /&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Site Açıklaması
                &lt;input id=&quot;description&quot; name=&quot;description&quot; type=&quot;text&quot; placeholder=&quot;Site Açıklaması&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Site Altbilgi
                &lt;input id=&quot;copyright&quot; name=&quot;copyright&quot; type=&quot;text&quot; placeholder=&quot;Site Altbilgisi&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;large-12 columns&quot;&gt;
          &lt;button type=&quot;submit&quot;&gt;Submit&lt;/button&gt;
      &lt;/div&gt;
  &lt;/div&gt;
&lt;/form&gt;
[/code]

Böylelikle çalışan programımız bitiyor. Sonuçta ayarları da sisteme entegre etmemiz lazım: Bunu da önce App.php ile settings sınıfından çekeceğiz ve www dizini altındaki public.php içinde kullanacağız. App.php içinde ayarları çekiyoruz.

[code language="php"]
    /**
     * Tüm sitedeki ayarları çektiğimiz metod
     *
     * @return array
     */
    public function getSettings()
    {
        $settings = new Settings($this-&gt;db);
        $setting = $settings-&gt;view();
        $this-&gt;settings = $setting['setting'];
    }
[/code]

Kök dizindeki index.php içinde bu sınıfın bu metodunu kullanıp sistemin her yerine gönderiyoruz:

[code language="php"]
&lt;?php
    require 'Vendor/autoload.php';
    require 'Config/config.inc.php';
    require 'Lib/App.php';
    session_start();

    $app = new \Midori\Cms\App();
    $app-&gt;connect($config['db']['host'],$config['db']['username'],$config['db']['password'],$config['db']['dbname']);
    $app-&gt;getSettings(); // &lt;----  Tam olarak burada Ayarları çekiyoruz
[/code]

Sonuç olarak sayfamız bitmiş oluyor. Şimdi bunların nasıl göründüklerine bakalım:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-02-23.40.11.png"><img class="alignnone size-large wp-image-759" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-02-23.40.11.png?w=680" alt="Ekran Resmi 2014-09-02 23.40.11" width="680" height="310" /></a>

Sitedeki görünümü de şu şekilde:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-02-23.41.24.png"><img class="alignnone size-large wp-image-760" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-02-23.41.24.png?w=680" alt="Ekran Resmi 2014-09-02 23.41.24" width="680" height="362" /></a>

Admin panelindeki butonları da settings bölümüne gidecek şekilde değiştiriyoruz:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-02-23.43.28.png"><img class="alignnone size-large wp-image-761" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-02-23.43.28.png?w=680" alt="Ekran Resmi 2014-09-02 23.43.28" width="680" height="894" /></a>

[code language="php"]
            &lt;ul class=&quot;right&quot;&gt;
                &lt;li class=&quot;has-dropdown&quot;&gt;
                    &lt;a href=&quot;#&quot;&gt;Admin&lt;/a&gt;
                    &lt;ul class=&quot;dropdown&quot;&gt;
                        &lt;li&gt;&lt;a href=&quot;/Cms/index.php/Users/show&quot;&gt;Tüm Kullanıcılar &amp;rarr;&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href=&quot;/Cms/index.php/Users/add&quot;&gt;Yeni Kullanıcı&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href=&quot;/Cms/index.php/Users/edit/&lt;?=$_SESSION['id']?&gt;&quot;&gt;Profilim&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href=&quot;/Cms/index.php/Users/logout&quot;&gt;Çıkış yap&lt;/a&gt;&lt;/li&gt;
                    &lt;/ul&gt;
                &lt;/li&gt;
                &lt;li class=&quot;divider&quot;&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href=&quot;/Cms/index.php/Settings/add&quot;&gt;Ayarlar&lt;/a&gt;&lt;/li&gt;
            &lt;/ul&gt;
[/code]

Programımız burada tamamlandı. Kodların son hali burda:

<a href="https://github.com/mtkocak/merakli">https://github.com/mtkocak/merakli</a>

Tüm bu seride amacımız, veritabanı bağlantılarını kullanarak basit bir şekilde sınıf yapısını anlamak, öğrendiğimiz php bilgisi ile ortaya işimize yarayacak bir program çıkarmaktı. Tabii ki sistemimizin bazı eksikleri var. Bunları tamamlamayı size bırakıyorum. Ödev olarak bunları gerçekleştirebilirsiniz. Github üzerinden paketi çatallayıp değişiklikler yapın ve pull request gönderin derim:
<ol>
	<li>Medya galerisi görünümü</li>
	<li>Medya galerisinden seçtiğimiz resimi yazıya dahil etmek</li>
	<li>Hazır metin editörlerini yazı güncelleme textarea'ları ile birleştirmek. (WYSIWYG) (TinyMCE gibi.)</li>
	<li>E-posta ile kullanıcının şifresini ve e-postasını değiştirdiğini haberdar etmek. Bunun için Vendor klasörüne SwiftMailer sınıfını dahil edebilirsiniz.</li>
	<li>Sayfalama yani pagination işlemleri</li>
</ol>
Seri'nin sonunda daha anlatmamız gereken bazı konular da var. Yeni yazılarda bunlara da değineceğiz:
<h2>MVC:</h2>
Örneğin, mySQL yerine msSQL veya oracle veritabanlarını kullanmamız gerekseydi, sql kodlarımız sınıflara gömülü olduğundan her seferinde bunları tek tek satır satır değiştirmemiz gerekirdi. Bunun yerine ORM adı verilen veritabanı bağlantılarını kullanabilirdik. Bu sayede işleri yapan sınıfları, bilgileri çeken sınıftan ayırmış olurduk. Hali hazırda sistemimiz zaten V ve C kısımlarını yani view ve controller yapılarını karşılasa da C ve M birleşik. Yani veriyi çeken model ile işleri yapan kontrolör aynı sınıfta tanımlanmış. Bu da daha sonra sorunlara yol açacaktır.
<h2>Routing (Yönlendirme):</h2>
Şu anda sisteme gelen bütün isteklerin index.php olarak gelmesi gerekiyor. Örneğin index.php/Posts/edit/4 gibi. Bunun yerine www.site.com/admin aracılığıyla doğrudan admin paneline, ya da www.site.com/yazi-basligi gibi bir linkle doğrudan istenen yazıya erişmek isteyebilirdik. Bunu da routing yani yönlendirme işlemleriyle hallediyoruz.
<h2>phpDoc:</h2>
Her sınıfın üzerinde bulunan şunun gibi bölümler dikkatinizi çekmiştir.

[code language="php"]
&lt;?php
/**
 * Tüm sistemdeki ayarları yönetecek sınıftır.
 *
 * Sistemin kurulumunu yapan ve ayarları yöneten sınıf. Sadece tek bir ayar olmasına izin vermeli.
 *
 * @author     Midori Kocak &lt;mtkocak@mtkocak.net&gt;
 */

namespace Midori\Cms;
[/code]

Bunlar aslında hiçbir işe yaramayan yorum blokları değil. phpDocumentor aracı ile yazılım dokümantasyonu oluşturmamızı ve daha sonra yazılım üzerinde çalışacak insanlar için kullanım klavuzunu otomatik oluşturmamızı sağlayan bölümlerdir. Bunlar sayesinde şu şekilde kod dokümantasyonu oluşturabiliyoruz. Ki bizim yazılım paketimizde de Docs/ dizini altında bu dokümantasyon mevcut.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-03-00.01.22.png"><img class="alignnone size-large wp-image-762" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-03-00.01.22.png?w=680" alt="Ekran Resmi 2014-09-03 00.01.22" width="680" height="394" /></a>

&nbsp;
<h2>Yazılım testleri:</h2>
OOP yani nesne yönelimli programlama mantığına hızlıca giriş yapmak için test konusuna girmedik. Ancak yurtdışında ve profesyonel çalışan yazılım şirketlerinde önce kod yazılmaz, kod test edilmez. Önce test sınıfları yazılır, daha sonra bu test sınıflarına kod yazılır. PHP'de bu phpUnit kütüphanesi ile yapılır. Bunu da daha sonraki bir yazıda anlatacağım.
<h2>Composer:</h2>
Sistemin ihtiyaç duyduğu dış kütüphaneleri otomatik olarak çekmemizi sağlayan ve yazılımımızın tek bir komutla yüklenmesini sağlayan, dışarıdan gelen sınıfları ve kendi sınıflarımızı otomatik olarak yazılıma dahil eden yazılımdır. Bu konuda da ayrı bir yazı yazmak gerekiyor.
<h2>CakePHP:</h2>
MVC kullanmamız gerektiğini belirtmiştik. Bu konuda MVC yapısını kullanan hazır kütüphaneler var. Bunlardan benim en sevdiğim ve MVC mimarisini en kolay kullanan ve en kolay şekilde anlatan CakePHP. Bunun yanı sıra Laravel de en son php teknolojilerini kullanan ve gerçekten popüler bir framework. Bir yazı serisinde bu iki kütüphane ile aynı yazılımı gerçekleştireceğiz.

Şimdilik bu kadar. Her zaman kendinizi geliştirmeye istekli ve azimli olunuz, çünkü öğrenmenin gerçekten sonu yok.
<h3>Seri kaynakçası:</h3>
http://omerozkan.net/oop-kapsulleme/
http://omerozkan.net/oop-kalitim/
http://omerozkan.net/oop-polimorfizm/
http://omerozkan.net/oop-soyutlama/
http://www.yazilimciblog.com/oop-temel-prensipleri/
http://www.csharpnedir.com/articles/read/?id=101
http://www.kazimapanoglu.com/makaleler/csharp/11-csharp-oop/4-encapsulation
http://zeroturnaround.com/rebellabs/object-oriented-design-principles-and-the-5-ways-of-creating-solid-applications/
https://semihkirdinli.wordpress.com/category/object-oriented-programming/
http://www.barbarosgurcan.com/post/Agile-Software-Development-Cevik-Yaz%C4%B1l%C4%B1m-Gelistirme.aspx
http://www.barbarosgurcan.com/post/SOLID-Principles-nedir-SOLID-ilkeleri.aspx
http://www.sitepoint.com/introduction-to-phpdoc/
http://www.glenscott.co.uk/blog/phpdocumentor-in-5-minutes/
http://www.cangelis.com/php-ve-tdd-phpunit-nasil-kullanilir/
http://www.zskblog.com/detay.aspx?id=14
http://code.tutsplus.com/tutorials/object-oriented-php-for-beginners--net-12762
http://code.tutsplus.com/tutorials/dependency-injection-in-php--net-28146
http://www.slideshare.net/yuxel/phpunit-ve-laravel
http://culttt.com/2013/03/25/what-are-php-lambdas-and-closures/
http://code.tutsplus.com/tutorials/dependency-injection-huh--net-26903
http://www.erbilen.net/816-pdo-kullanimi.html
http://www.cyber-warrior.org/dokuman/Default.Asp?Data_id=4589
http://en.wikipedia.org/wiki/SQL_injection
http://stackoverflow.com/questions/1387547/what-is-the-most-scalable-php-based-directory-structure-for-a-large-site
http://www.garfieldtech.com/blog/php-project-structure
http://www.slideshare.net/pmjones88/organizing-your-php-projects-2010-confoo
http://code.tutsplus.com/tutorials/organize-your-next-php-project-the-right-way--net-5873
http://csswizardry.com/2011/01/create-a-centred-horizontal-navigation/
http://code.tutsplus.com/tutorials/using-htaccess-files-for-pretty-urls--net-6049
http://www.sitepoint.com/php-dependency-management-with-composer/
http://jade-lang.com/
http://mariehogebrandt.se/articles/using-grunt-php-quality-assurance-tools/
http://anantgarg.com/2009/03/13/write-your-own-php-mvc-framework-part-1/
http://www.youtube.com/watch?v=CWwe9Z0Gyew
http://stackoverflow.com/questions/13007094/pdo-connection-class-using-singleton-pattern
http://weebtutorials.com/2012/03/pdo-connection-class-using-singleton-pattern/
http://www.zskblog.com/detay.aspx?id=14
https://thomashunter.name/blog/polymorphism-abstract-classes-and-interfaces-in-php/
http://www.techflirt.com/tutorials/oop-in-php/abstract-classes-interface.html
http://stackoverflow.com/questions/7971770/dynamic-parameters-in-abstract-methods-in-php
http://php.net/manual/tr/language.oop5.abstract.php
http://www.zskblog.com/detay.aspx?id=14
http://www.w3schools.com/php/php_sessions.asp