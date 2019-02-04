---
ID: 713
post_title: 'PHP ile içerik yönetim sistemi &#8211; 8 Herşeyi birleştirmeye başlayalım'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-8-herseyi-birlestirmeye-baslayalim/
published: true
post_date: 2014-08-26 21:31:39
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/tumblr_l25wkziSJ51qzyhb5o1_1280.jpg"><img class="alignnone size-large wp-image-714" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/tumblr_l25wkziSJ51qzyhb5o1_1280.jpg?w=680" alt="tumblr_l25wkziSJ51qzyhb5o1_1280" width="680" height="917" /></a>

&nbsp;

Sıra geldi herşeyi birleştirmeye ve projemizin ilk bebek adımlarını atmasını sağlamaya. Yapmamız gerek bir kaç iş daha var ama biz projeyi birleştirmeye başlayalım.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/dizin.png"><img class="alignnone wp-image-721 size-large" src="https://meraklibilisimci.com/wp-content/uploads/2018/10/dizin.png?w=480" alt="dizin" width="480" height="1024" /></a>

&nbsp;

burada config.codekit ve composer.json dosyaları hariç dizin yapısını lokal web sunucumuzun içinde (ipucu:xampp) oluşturalım. Klasör ismimiz Cms olsun. En önemli dosyamız şu anda index.php.

Diyelim ki projemizi, ftp ile sunucuya yükledik. Kullanıcı da adres çubuğuna sitemizin adresini yazdı. Ulaşacağı ilk sayfa index.php olacak haliyle. index.php dosyasının yapması gereken işler var. Sonuçta otelde resepsiyondaki görevliler gibi bişi o. Önce bizi tanımaya çalışacak, daha sonra bize yardımcı olacak ve istediğimiz yere götürecek.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/url.jpg"><img class="alignnone size-full wp-image-715" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/url.jpg" alt="url" width="238" height="212" /></a>

index.php dosyasının yapması gereken işler sırayla;
<ol>
 	<li>Kullanıcıyı tanımak. Kullanıcıya isteğini sormak. İsteğine göre gösterilecek sayfaları seçmek. Bunun için uygulama sınıfına başvurmak. Ondan cevap beklemek.</li>
 	<li>Kullanıcıya nerede olduğunu söylemek. Admin panelindeyse admin, dış sitedeyse admin sayfalarını göstermek.</li>
 	<li>Kullanıcının bi isteği yoksa, lobide rahat etmesini sağlamak. (Ana sayfa)</li>
 	<li>Yani uygulama sınıfından gelen cevabı ekrana basmak.</li>
</ol>
Cms klasörünün içine index.php dosyamızı koyacağız. İçindeki kodlar şu şekilde olsun:

[code language="php"]
&lt;?php
require 'Lib/Posts.php';
require 'Lib/Categories.php';
require 'Lib/Files.php';

require 'Config/config.inc.php';
require 'Lib/App.php';

$app = new \Midori\Cms\App();
$app-&gt;connect($config['db']['host'],$config['db']['username'],$config['db']['password'],$config['db']['dbname']);

if(strpos($_SERVER['REQUEST_URI'],$_SERVER['SCRIPT_NAME'])!==false){
$request = str_replace($_SERVER['SCRIPT_NAME'], "", $_SERVER['REQUEST_URI']);
}
else{
$request = "/Posts/";
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
$data = "";
}
if(empty($request)){
$request = "/Posts/";
}
echo $app-&gt;calculate($request,$data);

?&gt;
[/code]

Kod sizi korkuttu mu? Korkutur. Normaldir. Ama daha önce yaptığımız gibi tek tek kodumuzun parçalarını inceleyelim.
<ol>
 	<li>require metoduyla, ihtiyacımız olan sınıf dosyalarını dosyamıza çektik.</li>
 	<li>Bunlar Lib klasörü içinde bulunan daha önce yarattığımız işlemleri yapan sınıf dosyalarımız ve veritabanı ayarlarını tutan config.inc.php. Ama meraklı bilişimci bu dosyayı oluşturmadın demeyin, bizde hiçbirşey eksik kalmaz.</li>
 	<li>Daha sonra App sınıfı dosyasından   $app = new \Midori\Cms\App(); diyerek yeni uygulama sınıfı oluşturuyoruz. Peki başındaki bu \Midori\Cms\App() olayı ne? Hemen anlatayım:</li>
</ol>
<h2>Namespace</h2>
Diyelim ki bir yazılım yazdık, yazılımımızda da bir sürü sınıf kullandık. Örneğin, $file = new Files() diye bir sınıfımız var. Daha sonra başka bir kütüphane içerisinden bir sınıf kullanmamız gerekti, onun da adı Files. E ne olacak? Çakışacak. İşte bu çakışmayı önlemek için başına namespace dediğimiz bu kısaltmaları koyuyoruz, ki karışmasın. Bizde bunların adı \Midori\Cms. Bu sayede sınıflarımız gayet derli toplu oluyor. Peki kullanmasak olur muydu? Evet olurdu, ama projemiz çakışmalara da açık olurdu.

index.php dosyasında App diye bir sınıf var. Bu app sınıfı yazılımdaki her türlü işimizi yapmak zorunda olan bir tür işçi. Gelin App sınıfını inceleyim. Bu app sınıfını Cms altındaki Lib klasörüne kaydedelim. index.php bu app sınıfı ile bir nevi konuşuyor ve hangi durumda ne yapılması gerektiğini söylüyor. index.php resepsiyonist ise App sınıf otel müdürü gibi bişey.

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/hotel-staff-managers.jpg"><img class="alignnone size-full wp-image-722" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/hotel-staff-managers.jpg" alt="hotel-staff-managers" width="591" height="591" /></a>

&nbsp;

Otel müdürünün yapması gereken bir takım işler olduğu gibi (hangi odaların kullanılabilir olduğuna karar vermek vs. gibi) App sınıfının da özel birtakım görevleri var. Appa metodu tüm diğer sınıfları kullanan, onlardan gerektiğinde objeler oluşturan sınıftır. Hadi kodu inceleyelim;

[code language="php"]
&lt;?php
/**
* Uygulamamızı çalıştıracak olan sınıf
*
* Sistemdeki tüm sınıfların içermeleri gereken veritabanı ve diğer bilgileri tutan sınıf.
*
* @author Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/

namespace Midori\Cms;

use Midori\Cms;
use \PDO;

class App{

/**
* Veritabanı bağlantısını tutacak olan değişken.
*
* @var PDO
*/
private $db = false;

/**
* Veritabanına bağlanmaya yarayan kurucu metod
*
* @param string host Veritabanı sunucusunun adresi
* @param string dbname Veritabanı adı
* @param string username Kullanıcı adı
* @param string password Parola
* @return string bağlanılabildiyse doğru, bağlanamadıysa hata mesajı döndürsün.
*/
public function connect($host, $username, $password, $dbname){
try {
return $this-&gt;db = new PDO("mysql:host=".$host.";dbname=".$dbname."", "".$username."", "".$password."", array(
PDO::MYSQL_ATTR_INIT_COMMAND =&gt; "SET NAMES utf8",
PDO::ATTR_ERRMODE =&gt; PDO::ERRMODE_EXCEPTION
));
} catch ( PDOException $e ){
return $e-&gt;getMessage();
}
}

public function injectRelatedData(){
$categories = new Categories();
$categories-&gt;connect($this-&gt;db);
return $categories-&gt;index();
}

public function calculate($request, $data)
{
// /posts/add gibi bir request geldi.
$params = split("/", $request);;
$className = __NAMESPACE__.'\\'.$params[1];
//call_user_func_array
$class = new $className();
$class-&gt;connect($this-&gt;db);
$class-&gt;getRelatedData($this-&gt;injectRelatedData());

if(empty($data))
{
if($params[2]!=null)
{
if(isset($params[3]))
{
$data = $class-&gt;$params[2]($params[3]);
}
else
{
$data = $class-&gt;$params[2]();
}
if($data['render']!=false)
{
$content = array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/'.mb_strtolower($params[2]).'.php',$data));
return $this-&gt;render('./www/'.$data['template'].'.php', $content);
}
else
{
$data = $class-&gt;show();
$content = array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/show.php',$data));
return $this-&gt;render('./www/'.$data['template'].'.php', $content);
}
}
else{
$data = $class-&gt;index();
$content = array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/index.php',$data));
return $this-&gt;render('./www/'.$data['template'].'.php', $content);
}
}
else{
call_user_func_array ( array($class, $params[2]), $data );
$data = $class-&gt;show();
$content = array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/show.php',$data));
return $this-&gt;render('./www/'.$data['template'].'.php', $content);
}
// var_dump($params);
// $posts = new Posts();
// $posts-&gt;connect($this-&gt;db);
// return $posts-&gt;view(1);
}

public function render($file, $vars){

if (is_array($vars) &amp;&amp; !empty($vars)) {
extract($vars);
}

ob_start();
include $file;
return ob_get_clean();
}

}
?&gt;
[/code]

App.php dosyası biraz daha korkunç görünebilir, kabul ediyorum ama yine tek tek anlatacağım.
<ol>
 	<li>Namespace kavramını anlatmıştım ya, önce namespace tanımladık. \Midori\Cms diye.</li>
 	<li>App sınıfında PDO kütüphanesini kullanıyoruz. Bu yüzden use \PDO diyerek karışmayı da önlüyoruz.</li>
 	<li>Diğer sınıfların içinde kullanacağımız veritabanı objesini burda private $db içinde tanımladık.</li>
 	<li>connect yani bağlan metodu daha önce her sınıfta kullandığımız bağlanma metoduydu. Diğer tüm sınıflarda onu kullanmamak ve tek seferde çağırmak için burada tanımladık. Nasıl çalıştığını zaten biliyoruz.</li>
 	<li>injectRelatedData, bağlı bilgileri ekle metodu. Örneğin girdiler yani posts sınıfı ile işlemler yapacağız. Girdi eklemek için kategorilerin listesine ihtiyacımız var. Burada kategorilerin listesini çekip o sınıfın içine göndermemiz gerek. Bu metodla bu işi hallediyoruz.</li>
 	<li>En belalı metodumuz. Calculate yani hesapla metodu. Neredeyse tüm işleri yapan metodumuz. Bu metodda belki bilmediğimiz bir sürü kavram var ama korkmaya gerek yok hepsini tek tek inceleyeceğiz. Metod iki tane parametre almış. Bu parametrelerden biri $request diğer de $data. $request yani istek, kullanıcının bizden neyi istediği ve bu isteğe göre yapacağımız şeyleri belirten veridir. Örneğin istek olarak /Posts/View/1 gibi bişey gelirse, burdan kullanıcının 1 numaralı id'ye sahip olan Girdiği görmek istediğini şıp diye anlayabiliriz. $data ise, örneğin /Posts/add yani "Bu girdiyi sistmeme eklemek istiyorum" gibi bir istek varsa ve bununla birlikte bize kullanıcı girdi verisi yolladıysa, onu tutan değişkendir. Buradan bunu anlıyoruz.</li>
</ol>
Calculate metoduna devam etmeden, index.php dosyasında bu metodu nasıl çağırdığımıza bir geri dönelim.

[code language="php"]
$app-&gt;connect($config['db']['host'],$config['db']['username'],$config['db']['password'],$config['db']['dbname']);

if(strpos($_SERVER['REQUEST_URI'],$_SERVER['SCRIPT_NAME'])!==false){
$request = str_replace($_SERVER['SCRIPT_NAME'], "", $_SERVER['REQUEST_URI']);
}
else{
$request = "/Posts/";
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
$data = "";
}
if(empty($request)){
$request = "/Posts/";
}
echo $app-&gt;calculate($request,$data);
[/code]

index.php metodumuza geri döndük. Tek tek yaptıklarımızı incelemek için bir sürü zamanımız var. İçeride bilmediğimiz bir sürü yeni metod ve değişken var. Peki ne bunlar? Merak etmeyin, anlatıyorum:
<ol>
 	<li>$config. yani ayarları tutan değişken. config.inc.php dosyasını include etmiştik yani yazılıma dahil etmiştik ya. Bu dosyadaki değişkenleri kullanıyoruz ki, programı her çalıştırdığımızda veritabanı bilgilerini girmeyelim, sadece bu dosyayı değiştirmemiz yeterli olsun.</li>
</ol>
config.inc.php dosyasını Cms dizini altında Config dizini içine kaydedelim ve içeriğine de şunları ekleyelim:

[code language="php"]
&lt;?php
/**
* Tüm sistemdeki ayarları buradan hallediyoruz.
*
* Veritabanına kaydetmediğimiz ve sürekli değişmeyecek
* olan veritabanı sunucusu, cache tipi gibi bilgileri
* bu dosyada saklayacağız.
*
* @author Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/

$config = array(
"db"=&gt; array(
"dbname"=&gt;"merakli",
"host"=&gt;"localhost",
"username"=&gt;"root",
"password"=&gt;"midori"
)
);

?&gt;
[/code]

Burada ayarları tutan bir dizi oluşturduk ve tüm yazılımımızda sürekli aynı ayarları girmemek için kullanacağımız ayar değişkenlerini kaydedip kullanıyoruz.

Şu anda ayar dosyası oluşturmayı ve index.php ve App sınıfı kavramlarına giriş yaptık. Bir sonraki yazıda App.php sınıfını ve index.php içerisinde yaptığımız işlemleri ve kütüphanleremizde yaptığımız değişiklikleri incelemeye devam edeceğiz.

Kodun şu andaki son hali de şurda:

<a href="https://github.com/mtkocak/merakli/tree/cf5545a474f6ccf8b0ab521edb603629ba7d23ed">https://github.com/mtkocak/merakli/tree/cf5545a474f6ccf8b0ab521edb603629ba7d23ed</a>