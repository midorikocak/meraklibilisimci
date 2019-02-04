---
ID: 684
post_title: 'PHP ile içerik yönetim sistemi &#8211; 4 Sınıflarımızı yazmaya başlayalım.'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-4-siniflarimizi-yazmaya-baslayalim/
published: true
post_date: 2014-08-23 10:43:36
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/sinif-ogretmenligi-bolumu_clip_image006.jpg"><img class="alignnone size-medium wp-image-683" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/sinif-ogretmenligi-bolumu_clip_image006.jpg?w=300" alt="sinif-ogretmenligi-bolumu_clip_image006" width="300" height="225" /></a>

Bir önceki örneğimizde sınıfımızdaki metodların içlerini boş bırakmıştık. Şimdi tek tek bu metodların içlerini dolduracağız. Öncelikle veritabanına bağlanacağız. Ancak bu bağlantıyı, sınıf çalışıyorken bir değişkende tutmamız gerek.

[code language="php"] /**
 * Veritabanı bağlantısını tutacak olan değişken.
 *
 * @var PDO
 */
 private $db;

 /**
 * Veritabanına bağlanmaya yarayan metod
 *
 * @param string host Veritabanı sunucusunun adresi
 * @param string dbname Veritabanı adı
 * @param string username Kullanıcı adı
 * @param string password Parola
 * @return string bağlanılabildiyse doğru, bağlanamadıysa hata mesajı döndürsün.
 */
 public function connect($host, $username, $password, $dbname){ 
 	try {
 		return $this-&gt;db = new PDO(&amp;quot;mysql:host=&amp;quot;.$host.&amp;quot;;dbname=&amp;quot;.$dbname.&amp;quot;&amp;quot;, &amp;quot;&amp;quot;.$username.&amp;quot;&amp;quot;, &amp;quot;&amp;quot;.$password.&amp;quot;&amp;quot;);
 	} catch ( PDOException $e ){
		return $e-&gt;getMessage();
	}
 }
[/code]

Korkuttu mu? Korkutmasın. Tek tek bakalım:
<ol>
	<li>Sınıfımızın genelinde kullanacağımız $db değşkenini tanımladık</li>
	<li>Fonksiyonun içine kullanıcı adı, parola, veritabanı ismi ve sunucu adresini girdik</li>
	<li>Yeni bir veritabanı bağlantısı oluşturduk.</li>
	<li>Bağlanamazsa, hata mesajını metodun çıktısı olarak vermesini (return etmesini) sağladık.</li>
</ol>
Şimdi ekleme, güncelleme, silme ve listeleme ve gösterme metodlarını dolduralım.

[code language="php"]    /**
    * Girdi ekleyen metod, verilerin kaydedilmesini sağlar.
    *
    * @param string $title Girdi başlığı
    * @param string $content Girdi içeriği
    * @param int $category_id Girdi kategorisinin benzersiz kimliği
    * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function add($title, $content, $category_id){
		
        // Tarih içeren alanları elle girmiyoruz. Sistemden doğrudan isteyen fonksiyonumuz var.
        $date = $this-&gt;getDate();
		
        // Önce veritabanı sorgumuzu hazırlayalım.
        $query = $this-&gt;db-&gt;prepare(&amp;quot;INSERT INTO posts SET title=:baslik, content=:icerik, created=:created, category_id=:category, updated=:updated&amp;quot;);
	
        $insert = $query-&gt;execute(array(
            &amp;quot;baslik&amp;quot;=&gt;$title,
            &amp;quot;icerik&amp;quot;=&gt;$content,
            &amp;quot;category&amp;quot;=&gt;$category_id,
            &amp;quot;created&amp;quot;=&gt;$date,
            &amp;quot;updated&amp;quot;=&gt;$date
        ));
	
        if($insert){
            // Veritabanı işlemi başarılı ise sınıfın objesine ait değişkenleri değiştirelim
            $this-&gt;id = $this-&gt;db-&gt;lastInsertId();
            $this-&gt;title = $title;
            $this-&gt;content = $content;
            $this-&gt;created = $date;
            $this-&gt;updated = $date;
            $this-&gt;category_id = $category_id;
            
            return true;
        }
        else{
            return false;
        }
    }
[/code]

Yine işlemimizi adım adım inceleyelim.
<ol>
	<li>Önce daha önceden hazırlamış olduğumuz sorguları oluşturduk ve değişkenleri içeri yerleştirdik.</li>
	<li>Daha sonra execute metoduyla sorguyu çalıştırdık.</li>
	<li>En sonunda eğer işlem başarılı oldu ise, sınıftan ürettiğimiz objeye ait değişkenleri değiştirdik. (Bu cümleyi anlayamadıysanız sorun değil.)</li>
</ol>
Güvenlik için dışarıdan gelen $title ve $content verisini de sorguya execute metoduyla dahil ettik ki, sistemimize hacker'lar saldırmasın. Değişkenleri SQL sorgularına hiçbir kontrol olmadan sokmak, gerizekalılıktır arkadaşlar. Örneğin elimizdeki sorgu, SELECT * FROM users WHERE id='osman' AND password = $password olsun. $id verisi geldiğinde kullanıcıyı sisteme sokalım. Eğer password dediğimiz veri string değil de, '' OR '1'='1' gibi bir ifadeyse sorgunuz şöyle olur: SELECT * FROM users WHERE id='osman' password ='' OR '1'='1'; Eleman pat diye sisteminize girer. Yani msql fonksiyonlarını güvenlik için kullanmıyorum ve anlatmıyorum. PDO kütüphanesini kullanmamızın sebebi de bu.

Genel olarak veritabanı kullanan işlemlerimiz neredeyse aynı.

[code language="php"]  /**
 * Tek bir girdinin gösterilmesini sağlayan method
 *
 * @param int $id Girdinin benzersiz index'i
 * @return array gösterilebildyise dizi türünde verileri döndürsün, gösterilemediyse false, yanlış değeri döndürsün
 */
 public function view($id){

 // Eğer daha önceden sorgu işlemi yapıldıysa, sınıf objesine yazılmıştır.
 if($id == $this-&gt;id){
 return array(&amp;quot;id&amp;quot;=&gt;$this-&gt;id,&amp;quot;title&amp;quot;=&gt;$this-&gt;title,&amp;quot;content&amp;quot;=&gt;$this-&gt;content, &amp;quot;category_id&amp;quot;=&gt;$this-&gt;category_id, &amp;quot;created&amp;quot;=&gt;$this-&gt;created, &amp;quot;updated&amp;quot;=&gt;$this-&gt;updated);
 }
 else{
 // Buradan anlıyoruz ki veri henüz çekilmemiş. Veriyi çekmeye başlayalım
 $query = $this-&gt;db-&gt;prepare(&amp;quot;SELECT * FROM posts WHERE id=:id&amp;quot;);
 $query-&gt;execute(array(':id'=&gt;$id));
 
 if($query){
 $result = $query-&gt;fetch(PDO::FETCH_ASSOC);
 
 $this-&gt;id = $result['id'];
 $this-&gt;title = $result['title'];
 $this-&gt;content = $result['content'];
 $this-&gt;created = $result['created'];
 $this-&gt;updated = $result['updated'];
 $this-&gt;category_id = $result['updated'];
 
 return $result;
 }
 }
 
 // Eğer iki işlem de başarısız olduysa, false, yanlış değer döndürelim.
 return false;
 }
[/code]

Yine adım adım inceleyelim. Önce sınıfımızdan yaratılan objemize daha önceden verinin çekilip çekilmediğini kontrol ettik. Veri çekildiyse sorun yok, doğrudan değer döndürebiliriz. Yok eğer çekilmediyse, o zaman klasik pdo sorgumuzu oluşturduk. PDO::FETCH_ASSOC ifadesiyle sonucu alan isimlerinin dizi anahtarları şeklinde içeren bir dizi olarak çekmek istediğimizi belirttik. Bu ayarla ilgil başka özellikle de var, her zamanki gibi anlatmıyorum, siz ihtiyacınız olduğunda araştırırsınız.

Metodlarımızı doldurmaya devam edelim. Tüm verileri çeken index metodumuzu oluşturalım:

[code language="php"]    /**
    * Tüm girdilerin listelenmesini sağlayan metod.
    *
    * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
    */
    public function index(){
	$query = $this-&gt;db-&gt;prepare(&amp;quot;SELECT * FROM posts&amp;quot;);
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
[/code]

Buradaki tek fark şu, fetchAll metodu kullanarak, tüm cevap satırlarını dizi olarak döndürüyoruz. Sırada girdileri düzenlediğimiz metod var.

[code language="php"]    /**
    * Girdi düzenleyen metod. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
    * güncelleyen metod.
    *
    * @param int $id Girdinin benzersiz index'i
    * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function edit($id, $title, $content, $category_id){
        
        // Tarih içeren alanları elle girmiyoruz. Sistemden doğrudan isteyen fonksiyonumuz var.
        $date = $this-&gt;getDate();
		
        // Önce veritabanı sorgumuzu hazırlayalım.
        $query = $this-&gt;db-&gt;prepare(&amp;quot;UPDATE posts SET title=:baslik, content=:icerik, category_id=:category, updated=:updated WHERE id=:id&amp;quot;);
	
        $update = $query-&gt;execute(array(
            &amp;quot;baslik&amp;quot;=&gt;$title,
            &amp;quot;icerik&amp;quot;=&gt;$content,
            &amp;quot;category&amp;quot;=&gt;$category_id,
            &amp;quot;updated&amp;quot;=&gt;$date,
            &amp;quot;id&amp;quot;=&gt;$id
        ));
		
        if ( $update ){
             return true;
        }
        else
        {
            return false;
        }
    }
[/code]

Daha önceki veritabanı sorguları bölümünden hatırlayacağımız gibi, verileri düzenlerken UPDATE komutunu çalıştırıyoruz. Yine değişkenlerimizi ve sorgumuzu korumak adına prepare (hazırla) ve execute (çalıştır) metodlarını kullandık. Son bir işlemimiz kaldı. O da verileri silmek.

[code language="php"]    /**
    * Girdi silen metod, verilerin silinmesini sağlar.
    * Geri dönüşü yoktur.
    *
    * @param int $id Girdinin benzersiz index'i
    * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    public function delete($id){
        $query = $this-&gt;db-&gt;prepare(&amp;quot;DELETE FROM posts WHERE id = :id&amp;quot;);
        $delete = $query-&gt;execute(array(
           'id' =&gt; $id
        ));
    }
[/code]

Girdimizi basitçe sildikten sonra sınıfı nasıl kullanacağımıza bir göz atalım. Aynı klasörde index.php isimli bir dosya yaratalım.

[code language="php"]&lt;?php
$post = new Posts();
$post-&gt;connect('localhost','kullanici','parola','merakli');
$post-&gt;add(&amp;quot;CMS&amp;quot;, &amp;quot;Neden bu kadar çok kısaltma kullanıyorsun ey meraklibilisimci.com???&amp;quot;,1);
$post-&gt;add(&amp;quot;PHP&amp;quot;, &amp;quot;AngularJS diye bişey çıkmış&amp;quot;,1);
$post-&gt;edit(1, &amp;quot;OOP'ye giriş&amp;quot;, &amp;quot;OOP'yi çok severiz. OOP kullanmamak çok sıkıntı çıkarır, spaghetti insanın midesini bozar.&amp;quot;,1);
$post-&gt;delete(2);
var_dump($post-&gt;index());
?&gt;[/code]

Önce new komutuyla sınıfımızdan bir obje ürettik. Bağlatı işlemi yaptık. İki makale ekledik, 1 numaralı id'ye sahip olan makaleyi güncelledik, ve 2 numaralı id'ye sahip olan makaleyi de sildik. En son olarak da ekrana veritabanımıza eklediğimiz verilerin çıktısı gelcek. Görüntüsü de şöyle olacak:

[code language="php"]array (size=1)
  0 =&gt; 
    array (size=6)
      'id' =&gt; string '1' (length=1)
      'title' =&gt; string 'OOP'ye giriş' (length=10)
      'content' =&gt; string 'OOP'yi çok severiz. OOP kullanmamak çok sıkıntı çıkarır, spaghetti insanın midesini bozar.' (length=99)
      'category_id' =&gt; string '1' (length=1)
      'created' =&gt; string '2014-08-18 00:00:00' (length=19)
      'updated' =&gt; string '2014-08-18 00:00:00' (length=19)
[/code]

<a href="https://github.com/mtkocak/merakli/blob/d1cb92d2724434030d2c3be2a120ac74b9ae746c/posts.php">Sınıfımızın son hali</a> <a href="https://github.com/mtkocak/merakli/blob/d1cb92d2724434030d2c3be2a120ac74b9ae746c/posts.php">https://github.com/mtkocak/merakli/blob/d1cb92d2724434030d2c3be2a120ac74b9ae746c/posts.php</a>

Şu ana kadar tek bir sınıf ve veritabanı tablosu için back-end'de yani sunucu tarafında yapmamız gerekenleri gördük, veriyi ekledik, düzenledik, sildik, değiştirdik ve listeledik. Daha sonra diğer sınıfları oluşturarak devam edeceğiz. Siz de teme mantığı anladığınız üzere, kendi sınıflarınızı yazmaya başlayabilirsiniz.

&nbsp;

Kaynaklar
<ol>
	<li><a href="http://www.erbilen.net/816-pdo-kullanimi.html">http://www.erbilen.net/816-pdo-kullanimi.html</a></li>
	<li><a href="http://omerozkan.net/oop-kapsulleme/">http://omerozkan.net/oop-kapsulleme/</a></li>
	<li><a href="http://omerozkan.net/oop-kalitim/">http://omerozkan.net/oop-kalitim/</a></li>
	<li><a href="http://omerozkan.net/oop-polimorfizm/">http://omerozkan.net/oop-polimorfizm/</a></li>
	<li><a href="http://omerozkan.net/oop-soyutlama/">http://omerozkan.net/oop-soyutlama/</a></li>
	<li><a href="http://www.yazilimciblog.com/oop-temel-prensipleri/">http://www.yazilimciblog.com/oop-temel-prensipleri/</a></li>
	<li><a href="http://www.csharpnedir.com/articles/read/?id=101http://www.kazimapanoglu.com/makaleler/csharp/11-csharp-oop/4-encapsulation">http://www.csharpnedir.com/articles/read/?id=101http://www.kazimapanoglu.com/makaleler/csharp/11-csharp-oop/4-encapsulation</a></li>
	<li><a href="https://semihkirdinli.wordpress.com/category/object-oriented-programming/">https://semihkirdinli.wordpress.com/category/object-oriented-programming/</a></li>
</ol>