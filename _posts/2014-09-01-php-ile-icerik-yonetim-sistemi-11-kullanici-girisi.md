---
ID: 738
post_title: >
  PHP ile içerik yönetim sistemi – 11
  Kullanıcı girişi
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-11-kullanici-girisi/
published: true
post_date: 2014-09-01 20:22:07
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/13585621.jpg"><img class="alignnone size-full wp-image-739" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/13585621.jpg" alt="13585621" width="500" height="375" /></a>

Şu anda sistemimiz yol geçen hanı gibi. Elini kolunu sallayan girip güncelleme yapabiliyor. Tabii ki bunun böyle olmaması lazım. Yöneticilerin bir giriş ekranından kullanıcı adı ve parolalarını girip oturum açmaları, daha sonra yetkileri olan sayfaları görebilmeleri gerekmekte. Ayrıca sistemin, yetkisiz girişleri önleyebilmesi de gerekiyor. Kullanıcıların kendilerine ait olan profil sayfalarında kullanıcı adlarını, e-posta adreslerini ve parolalarını da değiştirebilmeleri lazım.

Bir diğer ihtiyacımız olan özellik ise, site ayarlarını tutacak olan tablo. Site yöneticisinin içerik yönetim sisteminin site adını, açıklamasını, copyright bölümü yazısını değiştirebileceği basit bir ayarlar bölümü olmalı ki, her seferinde kodlara müdahele etmek zorunda kalınmasın.

Tüm bunları yapmak için tahmin edebileceğiniz gibi iki tane veritabanı tablosuna ihtiyacımız var. Haydi bunları mySQL workbench kullanarak görsel olarak oluşturalım.

Şu anda veritabanımız gayet basit görünüyor:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-31-21.23.54.png"><img class="alignnone size-large wp-image-741" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-08-31-21.23.54.png?w=680" alt="Ekran Resmi 2014-08-31 21.23.54" width="680" height="425" /></a>

&nbsp;

Burada daha önceden yapmayı öğrendiğimiz şekilde yeni tablolarımızı oluşturalım.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-08.22.16.png"><img class="alignnone wp-image-744 size-medium" src="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-08.21.00.png?w=300" alt="Ekran Resmi 2014-09-01 08.21.00" width="300" height="265" /><img class="alignnone wp-image-743 size-medium" src="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-08.22.16.png?w=300" alt="Ekran Resmi 2014-09-01 08.22.16" width="300" height="300" /></a>

mySQL workbench bize ihtiyacımız olan sql kodunu oluştursun:

[code language="sql"]
-- -----------------------------------------------------
-- Table `merakli`.`users`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `merakli`.`users` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `username` VARCHAR(255) NULL,
  `email` VARCHAR(255) NOT NULL,
  `password` VARCHAR(255) NOT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB;

-- -----------------------------------------------------
-- Table `merakli`.`settings`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `merakli`.`settings` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `title` VARCHAR(45) NOT NULL,
  `description` TEXT NULL,
  `copyright` TEXT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB;

[/code]

İki tablomuzu oluşturduktan sonra, mysql workbench programı ile doğrudan veritabanına bağlanıp yaptığımız değişiklikleri 'Forward Engineer' (İleri doğru mühendislik) aracıyla kaydedebilir ya da phpmyadmin programıyla ürettiğimiz SQL kodunu çalıştırabilirsiniz.

Sonuçta phpMyAdmin programını açtığımızda şöyle bir görüntüyle karşılaşmamız gerekli:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-08.23.08.png"><img class="alignnone size-large wp-image-742" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-08.23.08.png?w=680" alt="Ekran Resmi 2014-09-01 08.23.08" width="680" height="318" /></a>

Son olarak deneme kullanıcımızı oluşturalım:

[code language="SQL"]
INSERT INTO `merakli`.`users` (`id`, `username`, `email`, `password`) VALUES ('1', 'kullanici', 'email@adresim.com', MD5('midori'));
[/code]

Burada parolası md5 ile şifrelenmiş "midori" olan kullanici adi 'kullanici', eposta adresi de 'email@adresim.com' olan bir kullanıcı oluşturmuş olduk.

Veritabanı işlemlerimiz bitti. Şimdi sıra geldi sınıflarımızı oluşturmaya. Zaten elimizde add edit index delete vs. işlerini yapan soyut sınıfımız var. Oradan bu iki sınıfı da oluşturabiliriz.

Kullanıcılar sınıfını tasarlamakla işe başlayalım. Elimizde id hariç 3 tane değişken var. username (kullanıcı adı), password (parola) ve email (e-posta). Peki neyi nasıl yapmalı?
<ol>
	<li>Sistemde yönetici yoksa, demek ki sistem kurulum aşamasındadır. sisteme ilk kullanıcı parolasız eklenebilmeli. Kurulum bölümünü, ayarlar sınıfını tamamlarken yazacağız. (register)</li>
	<li>Kullanıcı sistemde oturum açabilmeli. (login)</li>
	<li>Kullanıcı parolasını, e-posta adresini ve kullanıcı adını değiştirebilmeli. Yalnız bu e-posta adresini ve kullanıcı adını değiştirirken, sistemde zaten olmayan bir kullanıcı adı ve e-posta seçtiğinden emin olmalıyız. (Gelişmiş sistemlerde bu değişiklikler yapıldığında e-posta ile onay ve bilgilendirme mesajları gider. Şimdilik bu konuya girmeyeceğiz.) (edit)</li>
	<li>Kullanıcı oturumunu kapatabilmeli. (logout)</li>
	<li>Kullanıcı isterse hesabını silebilmeli. Bunu da kullanıcının kendi hesabıyla ilgili işlemleri yaptığı profil sayfasına seçenek olarak koyabiliriz. (delete)</li>
	<li>Her kullanıcı aslında yönetici olduğu için diğer kullanıcıları da yönetebilmeli. (show)</li>
</ol>

Önce her sınıfta login olup olunmadığını kontrol eden checkLogin metodumuzu soyut Assets sınıfımıza ekleyelim. Add edit gibi admin metodları için oturup açılıp açılmadığını bu metod kontrol edecek.

[code language="php"]
    /**
     * Sistemde oturum açılıp açılmadığını gösteren metod
     *
     * @return bool
     */
    public function checkLogin()
    {
        // Burada tekrar oturum kontrolü yapıyoruz:
        if(!isset($_SESSION['username'])){
            return false;
            //return array('render'=&gt;false,'template'=&gt;'public','message'=&gt;'Lütfen oturum açınız!');
        }
        else{
            return true;
        }
    }
[/code]

PHP'de sunucuda scriptin heryerden erişebildiği değişkenlere $_SESSION deniyor. $_SESSION sunucuya her gelen ziyaretçi için ayrıca üretilir ve ziyaretçi siteden çıktığında silinirler. Biz de önce login metodunda bu değişkeni üreteceğiz. Ayrıca yazılımımız kullanıcılar için oturum açmalı bir sistem haline geldiğinden, program çalışır çalışmaz, session_start(); komutuyla index.php içinde oturumu çalıştırıyoruz.

Şimdi tek tek Kullanıcılar sınıfını oluşturduğumuz Lib klasörü Users.php dosyasını tek tek inceleyelim:

[code language="php"]
&lt;?php
/**
 * Tüm sistemdeki kullanıcıları yönetecek olan kategori sınıfıdır.
 *
 * Sistemdeki yöneticilerin oturum açmalarını, parola değiştirmelerini sağlayan sınıf.
 *
 * @author     Midori Kocak &lt;mtkocak@mtkocak.net&gt;
 */

namespace Midori\Cms;

use \PDO;

/**
 * Class Users
 * @package Midori\Cms
 */
class Users extends Assets
{


    /**
     * Yönetici kullanıcı adı
     *
     * @var string
     */
    public $username;

    /**
     * Yönetici e-postası
     *
     * @var string
     */
    public $email;

    /**
     * Yönetici parolası
     *
     * @var string
     */
    private $password;

[/code]

Sınıfı tanımladık. Sınıfta metod tanımlarken bazı şeyleri farklı yapacağız. Sınıflarımız App.php sınıfı tarafından çağırılıyor ne de olsa. Sırayla inceleyelim. Kullanıcı eklememize yarayan add metodu:

[code language="php"]
    /**
     * Kullanıcı ekleyen metod, verilerin kaydedilmesini sağlar. Sistemde hiç kullanıcı yoksa
     * public olsun, kullanıcı varsa admin temasını işlesin. (render etsin)
     *
     * @param string $username Yönetici kullanıcı adı
     * @param string $password Yönetici parola
     * @param string $password2 Yönetici parola kontrol değeri
     * @param string $email Yönetici e-posta
     * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
     */
    public function add($username = null, $email = null, $password = null, $password2 = null)
    {
        $users = $this-&gt;index();
        // Login olup olmadığımızı ve sistemde kullanıcı olup olmadığını kontrol eden metod.
        if (!$this-&gt;checkLogin()) {
            return false;
        }

        if ($password != $password2) {
            return false;
        }

        // 3 değişkenin de boş olmaması gerekiyor
        if ($username != null &amp;&amp; $email != null &amp;&amp; $password != null) {
            // Önce veritabanı sorgumuzu hazırlayalım.
            $query = $this-&gt;db-&gt;prepare(&quot;INSERT INTO users SET username=:kullaniciadi, password=:parola, email=:eposta&quot;);

            $insert = $query-&gt;execute(array(
                &quot;kullaniciadi&quot; =&gt; $username,
                &quot;parola&quot; =&gt; md5($password),
                &quot;eposta&quot; =&gt; $email,
            ));

            if ($insert) {
                // Veritabanı işlemi başarılı ise sınıfın objesine ait değişkenleri değiştirelim
                $this-&gt;id = $this-&gt;db-&gt;lastInsertId();
                $this-&gt;username = $username;
                $this-&gt;password = $password;
                $this-&gt;email = $email;

                return true;
            } else {
                return false;
            }
        } else {
            return array('render' =&gt; true, 'template' =&gt; 'admin');
        }
    }
[/code]

Kullanıcı ekleme işlemini yaparken, oturum açılıp açılmadığını önce kontrol ettik. Eğer formdan gelen iki parola verisi eşit değilse de hata versin. Daha sonra metoda giren değişkenlerin boş olup olmadığını kontrol ediyoruz. Daha sonra diğer metodlarda yaptığımız gibi veritabanı metodlarımızı çalıştırıyoruz.

View/Users/add.php dosyası da şu şekilde, daha önceden anlattığımızdan pek de bir farkı yok.

[code language="php"]
&lt;?php
/*
*
* Adminlerin yeni kullanıcı eklediği sayfa
*
* Veriyi kullanıcıdan alacak ve gerekli yerlere göndereceğiz.
*
* @author Midori Kocak 2014
*
*/  
?&gt;
&lt;form action=&quot;/Cms/index.php/Users/add&quot; method=&quot;post&quot;&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Kullanıcı Adı
        &lt;input id=&quot;username&quot; name=&quot;username&quot; type=&quot;text&quot; placeholder=&quot;Kullanıcı Adı&quot; /&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;E-posta Adresi
                &lt;input id=&quot;email&quot; name=&quot;email&quot; type=&quot;text&quot; placeholder=&quot;E-Posta Adresi&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Parola
                &lt;input id=&quot;password&quot; name=&quot;password&quot; type=&quot;password&quot; placeholder=&quot;Parola&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Parola Tekrarı
                &lt;input id=&quot;password2&quot; name=&quot;password2&quot; type=&quot;password&quot; placeholder=&quot;Parola Tekrarı&quot; /&gt;
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

Tek kullanıcı gösterme metoduyla devam edeceğiz:

[code language="php"]
    /**
     * Tek bir kullanıcı verisini edit işlemine yani profil sayfasına gönderen metod. Render edilmesin
     *
     * @param int $id Kullanıcının benzersiz index'i
     * @return array gösterilebildyise dizi türünde verileri döndürsün, gösterilemediyse false, yanlış değeri döndürsün
     */
    public function view($id)
    {

        // Login olup olmadığımızı ve sistemde kullanıcı olup olmadığını kontrol eden metod.
        if (!$this-&gt;checkLogin()) {
            return false;
        }
        // Eğer daha önceden sorgu işlemi yapıldıysa, sınıf objesine yazılmıştır.
        if ($id == $this-&gt;id) {
            return array(&quot;id&quot; =&gt; $this-&gt;id, &quot;username&quot; =&gt; $this-&gt;username, &quot;email&quot; =&gt; $this-&gt;email, &quot;password&quot; =&gt; $this-&gt;password,);
        } else {
            // Buradan anlıyoruz ki veri henüz çekilmemiş. Veriyi çekmeye başlayalım
            $query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM users WHERE id=:id&quot;);
            $query-&gt;execute(array(':id' =&gt; $id));

            if ($query) {
                $user = $query-&gt;fetch(PDO::FETCH_ASSOC);

                $this-&gt;id = $user['id'];
                $this-&gt;username = $user['username'];
                $this-&gt;password = $user['password'];

                $result = array('template' =&gt; 'admin', 'user' =&gt; $user, 'render' =&gt; true);
                return $result;
            }
        }

        // Eğer iki işlem de başarısız olduysa, false, yanlış değer döndürelim.
        return false;
    }
[/code]

Bu metodu diğer metodlarda olduğu gibi kullanmayacağız. Sadece edit, yani güncelleme metodu için veri göndermesini sağlayacağız. Yani tek bir kullanıcıyı gösteren bir sayfa yerine, admin panelinde profilimigöster seçeneğine tıkladığımızda edit yani güncelle bölümü çağırılacak.

Listeleme metodu ise admin panelinde tüm kullanıcıları listelememize yarıyor.

[code language="php"]
    /**
     * Tüm kullanıcıların listelenmesini sağlayan metod.
     *
     * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
     */
    public function show()
    {

        // Login olup olmadığımızı ve sistemde kullanıcı olup olmadığını kontrol eden metod.
        if (!$this-&gt;checkLogin()) {
            return false;
        }

        $query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM users&quot;);
        $query-&gt;execute();
        if ($query) {
            // Buradaki fetchAll metoduyla tüm değeleri diziye çektik.
            $result = array('render' =&gt; true, 'template' =&gt; 'admin', 'users' =&gt; $query-&gt;fetchAll(PDO::FETCH_ASSOC));
            return $result;
        } else {
            return false;
        }
    }
[/code]

Görüntülenmesinde yine bir fark yok. Metoddan dönen sonuç verisini, View/Users/show.php'de göstereceğiz.

[code language="php"]
&lt;?php
/*
*
* Yöneticilere verileri listeleyen sayfa
*
* Verileri bu tablo vasıtasıyla listeleyip,
* ID'ye göre silme ve düzenleme linklerini oluşturacağız.
*
* @author Midori Kocak 2014
*
*/
?&gt;
&lt;h2&gt;Kullanıcılar&lt;/h2&gt;
&lt;table&gt;
    &lt;thead&gt;
        &lt;tr&gt;
            &lt;th&gt;Id&lt;/th&gt;
            &lt;th&gt;Kullanıcı Adı&lt;/th&gt;
            &lt;th&gt;E-posta&lt;/th&gt;
            &lt;th&gt;İşlemler&lt;/th&gt;
        &lt;/tr&gt;
    &lt;/thead&gt;
    &lt;tbody&gt;
        &lt;?php
        foreach($users as $user):
            ?&gt;
            &lt;tr&gt;
                &lt;td&gt;&lt;?=$user['id']?&gt;&lt;/td&gt;
                &lt;td&gt;&lt;?=$user['username']?&gt;&lt;/td&gt;
                &lt;td&gt;&lt;?=$user['email']?&gt;&lt;/td&gt;
                &lt;td&gt;&lt;a href=&quot;/Cms/index.php/Users/edit/&lt;?=$user['id']?&gt;&quot;&gt;Güncelle&lt;/a&gt;  &lt;a href=&quot;/Cms/index.php/Users/delete/&lt;?=$user['id']?&gt;&quot;&gt;Sil&lt;/a&gt;&lt;/td&gt;
            &lt;/tr&gt;
            &lt;?php
        endforeach;
        ?&gt;
    &lt;/tbody&gt;
&lt;/table&gt;
[/code]

Soyut sınıfta index metodunu tanımladığımız için onu da yazmalıyız:

[code language="php"]
    /**
     * Kullanıcıların listelenmesini sağlayan metod. Bu metodu liste çekmek için kullandık
     * Bu metod da view metodu gibi render edilmiyor.
     *
     * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
     */
    public function index()
    {
        return $this-&gt;show();
    }
[/code]

Show metodundan gelen veriyi aynısıylar döndürdük. Doğrudan show metodunda checkLogin yani oturum açılıp açılmadığını kontorl ettiğimiz için, başka bişi yazmaya gerek kalmadı.

Sıra düzenleme metodunda:

[code language="php"]
    /**
     * Kullanıcıyı düzenlemeye yarar. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
     * güncelleyen metod. Bu sayfa aynı zamanda kullanıcının profil sayfası olarak da görünmeli. View metodundan
     * hazır verileri alıp göstersin.
     *
     * @param int $id Kategorinin benzersiz index'i
     * @param string $username Yönetici kullanıcı adı
     * @param string $password Yönetici parola
     * @param string $password2 Yönetici parola kontrol değeri
     * @param string $email Yönetici e-posta
     * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
     */
    public function edit($id = null, $username = null, $password = null, $password2 = null, $email = null)
    {
        // Login olup olmadığımızı ve sistemde kullanıcı olup olmadığını kontrol eden metod.
        if (!$this-&gt;checkLogin()) {
            return false;
        }

        if ($password != $password2) {
            return false;
        }

        if ($id != null &amp;&amp; $username != null &amp;&amp; $password != null &amp;&amp; $email != null) {
            // Önce veritabanı sorgumuzu hazırlayalım.
            $query = $this-&gt;db-&gt;prepare(&quot;UPDATE users SET username=:kullaniciadi, password=:parola, email=:eposta WHERE id=:id&quot;);

            $update = $query-&gt;execute(array(
                &quot;id&quot; =&gt; $id,
                &quot;kullaniciadi&quot; =&gt; $password,
                &quot;parola&quot; =&gt; md5($password),
                &quot;eposta&quot; =&gt; $email
            ));

            if ($update) {
                return true;
            } else {
                return false;
            }
        } else {
            $oldData = $this-&gt;view($id);
            return array('template' =&gt; 'admin', 'render' =&gt; true, 'user' =&gt; $oldData['user']);
        }
    }
[/code]

Her zaman yaptığımız gibi veritabanı işlemleri ve eğer data gelmediyse, yani forma veri girilmediyse, view metodundan gelen bilgiyi forma döndürdük. Görüntüsüne bakalım:

[code language="php"]
&lt;?php
/*
*
* Adminlerin kullanıcıları düzenlediği sayfa
*
* Kullanıcı ekleme işlemi ile neredeyse aynı formu kullanıyoruz.
* Ancak formda eski değerleri görebilmemiz için bu sayfaya $user değişkeninin
* hazır olarak gelmesi gerekiyor.
*
* @author Midori Kocak 2014
*
*/
?&gt;

&lt;form action=&quot;/Cms/index.php/Users/edit/&lt;?=$user['id']?&gt;&quot; method=&quot;post&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Kullanıcı Adı
                &lt;input id=&quot;username&quot; name=&quot;username&quot; type=&quot;text&quot; placeholder=&quot;Kullanıcı Adı&quot; value=&quot;&lt;?=$user['username']?&gt;&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;E-posta Adresi
                &lt;input id=&quot;email&quot; name=&quot;email&quot; type=&quot;text&quot; placeholder=&quot;E-Posta Adresi&quot; value=&quot;&lt;?=$user['email']?&gt;&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Parola
                &lt;input id=&quot;password&quot; name=&quot;password&quot; type=&quot;password&quot; placeholder=&quot;Parola&quot; /&gt;
            &lt;/label&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class=&quot;row&quot;&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Parola Tekrarı
                &lt;input id=&quot;password2&quot; name=&quot;password2&quot; type=&quot;password&quot; placeholder=&quot;Parola Tekrarı&quot; /&gt;
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

$user değişkeniyle gelen bilgiyi form içindeki input yani girişlere value yani değer olarak girdik.

Geldik en muhteşem ve en belalı metodumuza, login yani oturum aç metodu:

[code language="php"]
    /**
     * Kullanıcı girişi yapan metod
     *
     * @param $username
     * @param $password
     * @return array
     */
    public function login($username = null, $password = null)
    {
        if (!$this-&gt;checkLogin()) {
            // Buradan anlıyoruz ki veri henüz oturum açılmamış.
            $query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM users WHERE username=:kullaniciadi AND password=:parola&quot;);

            $query-&gt;execute(array(
                'kullaniciadi' =&gt; $username,
                'parola' =&gt; md5($password),
            ));

            if ($query) {
                $user = $query-&gt;fetch(PDO::FETCH_ASSOC);

                // Kullanıcı adı veya parolası hatalıysa
                if (!$user) {
                    return array('template' =&gt; 'public', 'render' =&gt; true, 'message' =&gt; 'Hatalı kullanıcı adı veya parola.');
                }

                $this-&gt;id = $user['id'];
                $this-&gt;$username = $user['username'];
                $this-&gt;$password = $user['password'];

                // Session işlerini hallediyoruz.

                $_SESSION['username'] = $user['username'];
                $_SESSION['id'] = $user['id'];

                return array('template' =&gt; 'admin', 'render' =&gt; false, 'message' =&gt; 'Oturum açıldı', 'user' =&gt; $user);
            }
        } else {
            return array('template' =&gt; 'admin', 'render' =&gt; false, 'message' =&gt; 'Zaten oturum açıldı!');
        }
        return false;
    }
[/code]

Burada farklı olan iki şey var. Birincisi login işleminde gelen parola bilgisini md5() metodu ile şifreledik. Ve gelen veriyi daha önceden yine md5 ile kaydettiğimiz için o bilgiyle karşılaştırdık ki, hacker abilerimiz veritabanımıza girseler de parolalarımız çalamasınlar. Tabii ki bu yöntem de 100% güvenli değil. Bunlara da güvenlik konusunu incelediğimizde gireriz. Ancak şu an için bu kadar güvenlik yeterli.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-23.05.11.png"><img src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-23.05.11.png?w=680" alt="Ekran Resmi 2014-09-01 23.05.11" width="680" height="489" class="alignnone size-large wp-image-753" /></a>

Login metodunun görüntüsü her sistemde olduğu gibi bir oturum açma sayfası olan form:

[code language="php"]
&lt;?php
/*
*
* Kullanıcıların oturum açtığı sayfa.
*
* Veriyi kullanıcıdan alacak ve gerekli yerlere göndereceğiz.
*
* @author Midori Kocak 2014
*
*/  
?&gt;
&lt;div class=&quot;row&quot;&gt;
  &lt;div class=&quot;small-6 large-centered columns&quot;&gt;
      &lt;form action=&quot;/Cms/index.php/Users/login&quot; method=&quot;post&quot;&gt;
        &lt;div class=&quot;row&quot;&gt;
          &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Kullanıcı adı
              &lt;input id=&quot;username&quot; name=&quot;username&quot; type=&quot;text&quot; placeholder=&quot;Kullanıcı adı&quot; /&gt;
            &lt;/label&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;row&quot;&gt;
          &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;label&gt;Parola
              &lt;input id=&quot;password&quot; name=&quot;password&quot; type=&quot;password&quot; placeholder=&quot;Parola&quot; /&gt;
            &lt;/label&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;row&quot;&gt;
            &lt;div class=&quot;large-12 columns&quot;&gt;
                &lt;button type=&quot;submit&quot;&gt;Gönder&lt;/button&gt;
            &lt;/div&gt;
        &lt;/div&gt;
      &lt;/form&gt;
  &lt;/div&gt;
&lt;/div&gt;
[/code]

Oturum açtıktan sonra da karşımıza gelen sayfa:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-23.06.44.png"><img src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Ekran-Resmi-2014-09-01-23.06.44.png?w=680" alt="Ekran Resmi 2014-09-01 23.06.44" width="680" height="192" class="alignnone size-large wp-image-754" /></a>

Dikkat ettiyseniz, işlemden sonra işlemin sonucunu bir mesajla görüntülüyoruz. Bunları login metodunun içindeki return dizisinin içindeki mesaj verisiyle hallettik.

Oturumu kapatmak için session değişkenini sileceğiz. Bunu da değişkenleri hafızadan silen unset() metoduyla halledeceğiz. Bir görünüm render etmesine gerek yok:

[code language="php"]
    /**
     * Kullanıcının sistemden çıkmasını sağlayan metod
     *
     */
    public function logout()
    {
        unset($_SESSION['username']);
        return array('template' =&gt; 'public', 'render' =&gt; false, 'message' =&gt; 'Sistemden çıktınız');
    }
[/code]

Bu da anasayfaya dönerken "Sistemden çıktınız" mesajını gösterecek.

Son metodumuz kullanıcıları silen metod:

[code language="php"]
    /**
     * Kullanıcı silen metod, verilerin silinmesini sağlar.
     * Geri dönüşü yoktur.
     *
     * @param int $id Kategorinin benzersiz index'i
     * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
     */
    public function delete($id)
    {
        if (!$this-&gt;checkLogin()) {
            return false;
        }
        $query = $this-&gt;db-&gt;prepare(&quot;DELETE FROM users WHERE id = :id&quot;);
        $query-&gt;execute(array(
            'id' =&gt; $id
        ));
        return array('template' =&gt; 'admin', 'render' =&gt; false);
    }
[/code]

Bu metodun da sistemdeki diğer silme metodlarından farkı yok. Bu metoda, sistemde eğer kullanıcı kalmadıysa, silmeyi önlemek için return false işlemi konabilir. Ancak bunu size bırakıyorum.

Kullanıcı metodlarını bitirdikten sonra gelelim bu metodları App.php sınıfında, yani uygulamamızın ana sınıfında nasıl kullandığımızda. App sınıfında yaptığımız iki önemli değişiklik var. Birincisi, mesajları sisteme nasıl göndereceğimiz. Bunu www dizini içindeki admin.php ve public.php şemalarının içinde mesaj değişkeni tanımlandıysa göstereceğimiz kod parçasını $content değişkeninden hemen önce ekliyoruz:

[code language="php"]
    &lt;div class=&quot;row&quot;&gt;
        &lt;?php
        if(isset($message)):
        ?&gt;
        &lt;div data-alert class=&quot;alert-box&quot;&gt;
            &lt;?=$message?&gt;
            &lt;a href=&quot;#&quot; class=&quot;close&quot;&gt;&amp;times;&lt;/a&gt;
        &lt;/div&gt;
        &lt;?php
        endif;
        ?&gt;
        &lt;div class=&quot;large-12 columns&quot;&gt;
            &lt;?php echo $content; ?&gt;
        &lt;/div&gt;
    &lt;/div&gt;
[/code]

public.php de ve admin.php içinde de aynı kodu kullandık.

App.php yani uygulama sınıfındaki değişikliklere gelelim. Burasını dikkatle takip etmeniz gerekebilir.

[code language="php"]
    /**
     * Sistemdeki bütün görüntüleme hesaplama işlemlerini yapan metod
     *
     * @param $request
     * @param $data
     * @return string
     */
    public function calculate($request, $data)
    {
        // /posts/add gibi bir request geldi.
        $params = split(&quot;/&quot;, $request);
        $className = __NAMESPACE__ . '\\' . $params[1];
        //call_user_func_array
        $class = new $className($this-&gt;db);
        $class-&gt;getRelatedData($this-&gt;injectRelatedData());

        // Bu sınıfı tamamen değiştirmemiz gerek. Kullanıcının oturum açıp açmadığını
        // açtıysa, oturum bilgilerine göre neyin nasıl görüntüleneceğini belirlemeliyiz.
        //  Mesajlar uçuyordu halloldu

        if (empty($data)) {
            if ($params[2] != null) {
                if (isset($params[3])) {
                    $data = $class-&gt;$params[2]($params[3]);
                } else {
                    $data = $class-&gt;$params[2]();
                }
                if (isset($data['message'])) {
                    $message = $data['message'];
                } else {
                    $message = null;
                }

                if (isset($data['renderFile'])) {
                    $params[2] = $data['renderFile'];
                    $renderFile = $data['renderFile'];
                } else {
                    $renderFile = 'show';
                }

                if (isset($data['render']) &amp;&amp; $data['render'] != false) {
                    $content = array('message' =&gt; $message, 'related' =&gt; $this-&gt;injectRelatedData(), 'content' =&gt; $this-&gt;render('./View/' . $params[1] . '/' . mb_strtolower($params[2]) . '.php', $data));
                    return $this-&gt;render('./www/' . $data['template'] . '.php', $content);
                } else {
                    if (isset($data['message'])) {
                        $message = $data['message'];
                    } else {
                        $message = null;
                    }
                    if ($class-&gt;show() != false) {
                        // login sayfasına gitsin
                        $data = $class-&gt;show();
                        $content = array('message' =&gt; $message, 'related' =&gt; $this-&gt;injectRelatedData(), 'content' =&gt; $this-&gt;render('./View/' . $params[1] . '/' . $renderFile . '.php', $data));
                        return $this-&gt;render('./www/' . $data['template'] . '.php', $content);
                    } else {
                        $content = array('message' =&gt; $message, 'related' =&gt; $this-&gt;injectRelatedData(), 'content' =&gt; $this-&gt;render('./View/Users/login.php', $data));
                        return $this-&gt;render('./www/public.php', $content);
                    }
                }
            } else {


                $data = $class-&gt;index();

                if (isset($data['renderFile'])) {
                    $params[2] = $data['renderFile'];
                    $renderFile = $data['renderFile'];
                } else {
                    $renderFile = 'index';
                }


                if (isset($data['message'])) {
                    $message = $data['message'];
                } else {
                    $message = null;
                }
                $content = array('message' =&gt; $message, 'related' =&gt; $this-&gt;injectRelatedData(), 'content' =&gt; $this-&gt;render('./View/' . $params[1] . '/' . $renderFile . '.php', $data));
                return $this-&gt;render('./www/' . $data['template'] . '.php', $content);
            }
        } else {
            $data = call_user_func_array(array($class, $params[2]), $data);

            if (isset($data['renderFile'])) {
                $params[2] = $data['renderFile'];
                $renderFile = $data['renderFile'];
            } else {
                $renderFile = 'show';
            }

            if (isset($data['message'])) {
                $message = $data['message'];
            } else {
                $message = null;
            }

            if ($class-&gt;show() != false) {
                // login sayfasına gitsin
                $data = $class-&gt;show();
                $content = array('message' =&gt; $message, 'related' =&gt; $this-&gt;injectRelatedData(), 'content' =&gt; $this-&gt;render('./View/' . $params[1] . '/' . $renderFile . '.php', $data));
            } else {
                $content = array('message' =&gt; $message, 'related' =&gt; $this-&gt;injectRelatedData(), 'content' =&gt; $this-&gt;render('./View/Users/login.php', $data));
            }
            return $this-&gt;render('./www/' . $data['template'] . '.php', $content);
        }
    }
[/code]

Hesaplama yani calculate metodu içinde yaptığımız en önemli değişiklik eğer herhangi bir metoddan sadece false yani hata değeri döndüyse, kullanıcıları doğrudan login sayfasına yönlendirmek. Ayrıca mesaj verisini de burada render metodlarımızın içine yedirdik. Bir başka değişiklik ise renderFile değişkeni. Bu değişken sayesinde eğer bir metodun farklı bir değişkenin görünümünü kullanmasını istiyorsak, metodun döndürdüğü dizi içinde bunu renderFile değişkeni ile tanımlıyoruz. Bu değişkeni daha çok settings yani ayarlar sınıfında tanımladık.

Son olarak, şu anda index.php yani kullanıcının ilk girdiği dosyada her giren kullanıcı için bir oturum bilgisi tanımlanmıyor. Bunu da session_start() metodu ile hallediyoruz:

[code language="php"]
&lt;?php
    require 'Vendor/autoload.php';
    require 'Config/config.inc.php';
    require 'Lib/App.php';
    session_start();
    
    $app = new \Midori\Cms\App();
    $app-&gt;connect($config['db']['host'],$config['db']['username'],$config['db']['password'],$config['db']['dbname']);
    $app-&gt;getSettings();

    if(strpos($_SERVER['REQUEST_URI'],$_SERVER['SCRIPT_NAME'])!==false){
        $request = str_replace($_SERVER['SCRIPT_NAME'], &quot;&quot;, $_SERVER['REQUEST_URI']);
    }
    else{
        $request = &quot;/Posts/&quot;;
    }

    if(!empty($_POST))
    {
        $data = $_POST;
    }
    elseif(!empty($_FILES))
    {
        $data = $_FILES;
    }
    else{
        $data = &quot;&quot;;
    }
    if(empty($request)){
        $request = &quot;/Posts/&quot;;
    }
    echo $app-&gt;calculate($request,$data);
[/code]

Oturum açma ile işlemlerimiz şimdilik bu kadar. Zor bir bölüm olduğunu kabul ediyorum. Ancak tek tek adım adım giderseniz, anlamak ve uygulamak gayet basit.

Bir sonraki yazıda ayarlar sınıfımızı tanımlayacağız.

Dayanışmayla.