---
ID: 693
post_title: >
  PHP ile içerik yönetim sistemi – 5
  Gereksiz kod tekrarlarından kaçınmak
  ve hataları başından önlemek
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-5-gereksiz-kod-tekrarlarindan-kacinmak-ve-hatalari-basindan-onlemek/
published: true
post_date: 2014-08-25 09:35:10
---
<p><a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/siyahbeyaz.jpg"><img class="size-full wp-image-695 aligncenter" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/siyahbeyaz.jpg" alt="siyahbeyaz" width="300" height="300" /></a></p>
<p>Kalan iki sınıfımız daha var. Kategoriler ve Resimler. Bir önceki bölümde hazırladığımız gibi, diğer iki sınıf dosyasını da hazırlayalım:</p>
<p>Kategoriler sınıfı:</p>
[code language="php"]
&lt;?php
/**
* Tüm sistemdeki kategorileri yönetecek olan kategori sınıfıdır.
*
* Sistemdeki kategorilerin düzenlenmesini, silinmesini, görüntülenmesini, 
* listelenmesini ve eklenmesini kontrol eden sınıftır.
*
* @author     Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/
class Categories{
	
    /**
    * Kategorinin tekil id'sini tutan değişken. Başka kategorilerle karışmamasını sağlar
    *
    * @var int
    */
    public $id;
 
    /**
    * Kategori başlığı
    *
    * @var string
    */
    public $title;
	
	
    /**
    * Veritabanı bağlantısını tutacak olan değişken.
    *
    * @var PDO
    */
    private $db;

    /**
    * Veritabanına bağlanmaya yarayan yardımcı metod
    *
    * @param string host Veritabanı sunucusunun adresi
    * @param string dbname Veritabanı adı
    * @param string username Kullanıcı adı
    * @param string password Parola
    * @return string bağlanılabildiyse doğru, bağlanamadıysa hata mesajı döndürsün.
    */
    public function connect($host, $username, $password, $dbname){ 
        try {
            return $this-&gt;db = new PDO(&quot;mysql:host=&quot;.$host.&quot;;dbname=&quot;.$dbname.&quot;&quot;, &quot;&quot;.$username.&quot;&quot;, &quot;&quot;.$password.&quot;&quot;, array(
                PDO::MYSQL_ATTR_INIT_COMMAND =&gt; &quot;SET NAMES utf8&quot;,
                PDO::ATTR_ERRMODE =&gt; PDO::ERRMODE_EXCEPTION
            ));
        } catch ( PDOException $e ){
            return $e-&gt;getMessage();
        }
    }
    
 
    /**
    * Kategori ekleyen metod, verilerin kaydedilmesini sağlar.
    *
    * @param string $title Kategori başlığı
    * @param string $content Kategori içeriği
    * @param int $category_id Kategori kategorisinin benzersiz kimliği
    * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function add($title){
		
		
        // Önce veritabanı sorgumuzu hazırlayalım.
        $query = $this-&gt;db-&gt;prepare(&quot;INSERT INTO categories SET title=:baslik&quot;);
	
        $insert = $query-&gt;execute(array(
            &quot;baslik&quot;=&gt;$title
        ));
	
        if($insert){
            // Veritabanı işlemi başarılı ise sınıfın objesine ait değişkenleri değiştirelim
            $this-&gt;id = $this-&gt;db-&gt;lastInsertId();
            $this-&gt;title = $title;
            
            return true;
        }
        else{
            return false;
        }
    }

    /**
    * Tek bir kategorinin gösterilmesini sağlayan method
    *
    * @param int $id Kategorinin benzersiz index'i
    * @return array gösterilebildyise dizi türünde verileri döndürsün, gösterilemediyse false, yanlış değeri döndürsün
    */
    public function view($id){

        // Eğer daha önceden sorgu işlemi yapıldıysa, sınıf objesine yazılmıştır.
        if($id == $this-&gt;id){
            return array(&quot;id&quot;=&gt;$this-&gt;id,&quot;title&quot;=&gt;$this-&gt;title);
        }
        else{
            // Buradan anlıyoruz ki veri henüz çekilmemiş. Veriyi çekmeye başlayalım
            $query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM posts WHERE id=:id&quot;);
            $query-&gt;execute(array(':id'=&gt;$id));
		
            if($query){
                $result = $query-&gt;fetch(PDO::FETCH_ASSOC);
                
                $this-&gt;id = $result['id'];
                $this-&gt;title = $result['title'];
                
                return $result;
            }
        }
	
        // Eğer iki işlem de başarısız olduysa, false, yanlış değer döndürelim.
        return false;
    }
	
    /**
    * Tüm kategorilerin listelenmesini sağlayan metod.
    *
    * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
    */
    public function index(){
		$query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM categories&quot;);
        $query-&gt;execute();
        if($query){
            // Buradaki fetchAll metoduyla tüm değeleri diziye çektik.
            return $query-&gt;fetchAll(PDO::FETCH_ASSOC);
        }
        else
        {
            return false;
        }
    }


    /**
    * Kategori düzenleyen metod. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
    * güncelleyen metod.
    *
    * @param int $id Kategorinin benzersiz index'i
    * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function edit($id, $title){
        
		
        // Önce veritabanı sorgumuzu hazırlayalım.
        $query = $this-&gt;db-&gt;prepare(&quot;UPDATE categories SET title=:baslik WHERE id=:id&quot;);
	
        $update = $query-&gt;execute(array(
            &quot;baslik&quot;=&gt;$title,
            &quot;id&quot;=&gt;$id
        ));
		
        if ( $update ){
             return true;
        }
        else
        {
            return false;
        }
    }

    /**
    * Kategori silen metod, verilerin silinmesini sağlar.
    * Geri dönüşü yoktur.
    *
    * @param int $id Kategorinin benzersiz index'i
    * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function delete($id){
        $query = $this-&gt;db-&gt;prepare(&quot;DELETE FROM categories WHERE id = :id&quot;);
        $delete = $query-&gt;execute(array(
           'id' =&gt; $id
        ));
    }
	
}
?&gt;


[/code]
<p>Dosyalar sınıfı:</p>
[code language="php"]
&lt;?php
/**
* Tüm sistemdeki dosyaları yönetecek olan dosya sınıfıdır.
*
* Sistemdeki dosyaların düzenlenmesini, silinmesini, görüntülenmesini, 
* listelenmesini ve eklenmesini kontrol eden sınıftır.
*
* @author     Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/
class Files{
	
    /**
    * Dosyanın tekil id'sini tutan değişken. Başka dosyalarle karışmamasını sağlar
    *
    * @var int
    */
    public $id;
 
    /**
    * Dosya ismi
    *
    * @var string
    */
    public $filename;
	
    /**
    * Veritabanı bağlantısını tutacak olan değişken.
    *
    * @var PDO
    */
    private $db;

    /**
    * Veritabanına bağlanmaya yarayan yardımcı metod
    *
    * @param string host Veritabanı sunucusunun adresi
    * @param string dbname Veritabanı adı
    * @param string username Kullanıcı adı
    * @param string password Parola
    * @return string bağlanılabildiyse doğru, bağlanamadıysa hata mesajı döndürsün.
    */
    public function connect($host, $username, $password, $dbname){ 
        try {
            return $this-&gt;db = new PDO(&quot;mysql:host=&quot;.$host.&quot;;dbname=&quot;.$dbname.&quot;&quot;, &quot;&quot;.$username.&quot;&quot;, &quot;&quot;.$password.&quot;&quot;, array(
                PDO::MYSQL_ATTR_INIT_COMMAND =&gt; &quot;SET NAMES utf8&quot;,
                PDO::ATTR_ERRMODE =&gt; PDO::ERRMODE_EXCEPTION
            ));
        } catch ( PDOException $e ){
            return $e-&gt;getMessage();
        }
    }
 
    /**
    * Dosya ekleyen metod, verilerin kaydedilmesini sağlar.
    *
    * @param string $title Dosya başlığı
    * @param string $content Dosya içeriği
    * @param int $category_id Dosya kategorisinin benzersiz kimliği
    * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function add($filename){
		
		
        // Önce veritabanı sorgumuzu hazırlayalım.
        $query = $this-&gt;db-&gt;prepare(&quot;INSERT INTO posts SET filename=:dosyaadi&quot;);
	
        $insert = $query-&gt;execute(array(
            &quot;dosyaadi&quot;=&gt;$filename,
        ));
	
        if($insert){
            // Veritabanı işlemi başarılı ise sınıfın objesine ait değişkenleri değiştirelim
            $this-&gt;id = $this-&gt;db-&gt;lastInsertId();
            $this-&gt;filename = $filename;
            
            return true;
        }
        else{
            return false;
        }
    }

    /**
    * Tek bir dosyanın gösterilmesini sağlayan method
    *
    * @param int $id Dosyanın benzersiz index'i
    * @return array gösterilebildyise dizi türünde verileri döndürsün, gösterilemediyse false, yanlış değeri döndürsün
    */
    public function view($id){

        // Eğer daha önceden sorgu işlemi yapıldıysa, sınıf objesine yazılmıştır.
        if($id == $this-&gt;id){
            return array(&quot;id&quot;=&gt;$this-&gt;id,&quot;filename&quot;=&gt;$this-&gt;filename);
        }
        else{
            // Buradan anlıyoruz ki veri henüz çekilmemiş. Veriyi çekmeye başlayalım
            $query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM files WHERE id=:id&quot;);
            $query-&gt;execute(array(':id'=&gt;$id));
		
            if($query){
                $result = $query-&gt;fetch(PDO::FETCH_ASSOC);
                
                $this-&gt;id = $result['id'];
                $this-&gt;title = $result['filename'];
                
                return $result;
            }
        }
	
        // Eğer iki işlem de başarısız olduysa, false, yanlış değer döndürelim.
        return false;
    }
	
    /**
    * Tüm dosyaların listelenmesini sağlayan metod.
    *
    * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
    */
    public function index(){
		$query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM files&quot;);
        $query-&gt;execute();
        if($query){
            // Buradaki fetchAll metoduyla tüm değeleri diziye çektik.
            return $query-&gt;fetchAll(PDO::FETCH_ASSOC);
        }
        else
        {
            return false;
        }
    }


    /**
    * Dosya düzenleyen metod. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
    * güncelleyen metod.
    *
    * @param int $id Dosyanın benzersiz index'i
    * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function edit($id, $filename){
        
        // Tarih içeren alanları elle girmiyoruz. Sistemden doğrudan isteyen fonksiyonumuz var.
        $date = $this-&gt;getDate();
		
        // Önce veritabanı sorgumuzu hazırlayalım.
        $query = $this-&gt;db-&gt;prepare(&quot;UPDATE files SET filename=:filename WHERE id=:id&quot;);
	
        $update = $query-&gt;execute(array(
            &quot;filename&quot;=&gt;$filename,
        ));
		
        if ( $update ){
             return true;
        }
        else
        {
            return false;
        }
    }

    /**
    * Dosya silen metod, verilerin silinmesini sağlar.
    * Geri dönüşü yoktur.
    *
    * @param int $id Dosyanın benzersiz index'i
    * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function delete($id){
        $query = $this-&gt;db-&gt;prepare(&quot;DELETE FROM files WHERE id = :id&quot;);
        $delete = $query-&gt;execute(array(
           'id' =&gt; $id
        ));
    }
	
}
?&gt;
[/code]
<p>Şimdilik burada dosya ve dizin işlemlerini kodun içine yerleştirmedim.</p>
<p>Bir şey dikkatinizi çekti mi? Üç sınıfta da kodlar neredeyse aynı. Bir sürü tekrar var. Kendimizi tekrar etmememiz gerekiyor. Bir şey eğer çok kullanılıyorsa, bunu gruplayıp, ihtiyacımız olduğu zaman kullanmalıyız. Bunu şimdilik sonraya bırakalım.</p>
<p>Projeyi ne de olsa çalışıyor diye bu şekilde bırakırsanız, hapı yutmanız mümkündür. Neden mi? Çünkü, her sınıfın içinde ayrı bir veritabanı bağlantısı fonksiyonu var. Bu kesinlikle olmaması gereken bişey. Bu şekilde hangi sınıfın hangi veritabanına bağlandığını kontrol edemeyiz.</p>
<p>Bunlardan farklı olarak, her sınıfta veritabanı nesnesini yeniden oluşturuyoruz. Eğer veritabanı sınıfı bozuksa, bu sınıfımızın çalışmasını öldürecektir. Bunun yerine nesneyi farklı bir yerden sınıfa dahil etmek daha doğru olacak.</p>
<p>Ayrıca farklı bir veritabanı kullanmak istediğimizi farzedelim. Binlerce satır kodu nasıl değiştireceğiz? Bu yüzden sınıflar içerisinde SQL kodu kullanmak gerçekten mide bulandırıcı. Yine de şimdilik SQL kodları orda kalsın.</p>
<p>En çok kullandığımz kod, veritabanına bağlanmak için kullandığımız.</p>
[code language="php"]
 /**
    * Veritabanı bağlantısını tutacak olan değişken.
    *
    * @var PDO
    */
    private $db;

    /**
    * Veritabanına bağlanmaya yarayan yardımcı metod
    *
    * @param string host Veritabanı sunucusunun adresi
    * @param string dbname Veritabanı adı
    * @param string username Kullanıcı adı
    * @param string password Parola
    * @return string bağlanılabildiyse doğru, bağlanamadıysa hata mesajı döndürsün.
    */
    public function connect($host, $username, $password, $dbname){ 
        try {
            return $this-&gt;db = new PDO(&quot;mysql:host=&quot;.$host.&quot;;dbname=&quot;.$dbname.&quot;&quot;, &quot;&quot;.$username.&quot;&quot;, &quot;&quot;.$password.&quot;&quot;, array(
                PDO::MYSQL_ATTR_INIT_COMMAND =&gt; &quot;SET NAMES utf8&quot;,
                PDO::ATTR_ERRMODE =&gt; PDO::ERRMODE_EXCEPTION
            ));
        } catch ( PDOException $e ){
            return $e-&gt;getMessage();
        }
    }
[/code]
<p>Bu kod tüm sınıflarda aynı. Bu sınıfı kodlarımızdan silelim ve ayrı bir sınıf yaratalım. Ancak tüm diğer sınıflarımızda bu yeni bağlantı sınıfını kullanalım.</p>
[code language="php"]
&lt;?php
/**
* Uygulamamızı çalıştıracak olan sınıf
*
* Sistemdeki tüm sınıfların içermeleri gereken veritabanı ve diğer bilgileri tutan sınıf.
*
* @author   Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/

namespace Midori\Cms;

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
    public function __construct($host, $username, $password, $dbname){ 
        try {
            return $this-&gt;db = new PDO(&quot;mysql:host=&quot;.$host.&quot;;dbname=&quot;.$dbname.&quot;&quot;, &quot;&quot;.$username.&quot;&quot;, &quot;&quot;.$password.&quot;&quot;, array(
                PDO::MYSQL_ATTR_INIT_COMMAND =&gt; &quot;SET NAMES utf8&quot;,
                PDO::ATTR_ERRMODE =&gt; PDO::ERRMODE_EXCEPTION
            ));
        } catch ( PDOException $e ){
            return $e-&gt;getMessage();
        }
    }
}
?&gt;
[/code]
<p>Bu bağlantı sınıfımızı oluşturduk. Tek veritabanı bağlantımızı bu sınıftan çağıracağız. __construct() kısmına dikkat ettiniz mi? "__" ifadesi ile bağlayan metodlar sihirli metodlardır. __consturct() ifadesi, sınıftan yeni bir metod yaratıldığına otomatik olarak çalışan metodlardır. Bunu anlattım ama bunu kullanmayacağız. Çünkü her programı çalıştırdığımızda bu ayarları tek tek girmemiz saçma olur. Bunun yerine temel bir program sınıfı yaratacağız. Bütün gereklilikleri alsın, ayarları belirlesin ve programı kullanımımıza hazır hale getirsin. Bunu da bir sonraki yazıda yapacağız.</p>