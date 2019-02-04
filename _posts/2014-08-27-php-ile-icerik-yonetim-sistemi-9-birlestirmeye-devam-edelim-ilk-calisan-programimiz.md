---
ID: 726
post_title: 'PHP ile içerik yönetim sistemi &#8211; 9 Birleştirmeye devam edelim.'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-9-birlestirmeye-devam-edelim-ilk-calisan-programimiz/
published: true
post_date: 2014-08-27 14:29:34
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/php-mysql.png"><img class="alignnone size-full wp-image-728" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/php-mysql.png" alt="PHP-Mysql" width="500" height="270" /></a>

index.php dosyamızı incelemeye devam edelim. Önce app sınıfımızı oluşturmuşuz ve bağlantı metodunu çağırmışız. Daha sonraki satırların korkutucu olduğunu kabul ediyorum. Yine her zaman yaptığımız gibi tek tek inceleyelim.

[code language="php"]
$app-&gt;connect($config['db']['host'],$config['db']['username'],$config['db']['password'],$config['db']['dbname']);

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

<ol>
	<li>$_SERVER, $_GET, $_FILES gibi değişkenler php yazılımları çalışırken sabit olan global değişkenlerdir. Örneğin dosyamızın ismini $_SERVER['SCRIPT_NAME'] ile almışız. $_SERVER['REQUEST_URI'] ise adres çubuğuna ne yazıldığı.</li>
	<li>Adresimiz http://localhost/CMS/index.php/Posts/View/1 gibi olacak. Ancak herhangi bir kimse http://localhost/CMS/ diyerek de sisteme gelebilir. strpos() metodunu kullanarak adres içinde script ismi yani index.php ifades var mı yok mu diye bakmışız.</li>
	<li>eğer varsa, bunu request_uri yani index.php/Posts/View/1 ifadesinden silmişiz. Ve kalan /Posts/View/1 ifadesini istek yani $request değişkenine atmışız.</li>
	<li>$request yani istek değişkeni App sınıfına kullanıcının sistemden ne talep ettiğini söyleyen değişken.</li>
	<li>Eğer request içinde index.php ifadesi bulunamadıysa, o zaman kullanıcı http://localhost/Cms/ adresiyle gelmiş demektir. Oradaki else ifadesi ile boş durumlarda istek yani $request değişkeninin doğrudan Posts isteğini içermesini sağladık ki, anasayfada tüm girdilerin listesi olsun.</li>
	<li>$_POST ifadesi, formlarlar veri gönderilip gönderilmediğini tutar. Eğer veri gönderildiyse bunu $data yani App::calculate($request, $data) metoduna, istekten sonra atacağımız değişken olarak belirleyelim.</li>
	<li>Eğer $_FILES değişkeni boş değilse, o zaman dosya gönderilmiş demektir. O zaman $data yani veri olarak bu dosyayı belirleyelim.</li>
	<li>Her şeye rağmen request ifadesi boşsa, garanti olsun diye posts, yani girdiler'i listelesin $request yani istek</li>
	<li>Son olarak da app sınıfından calculate metodunu çağıralım ve ekrana basalım.</li>
</ol>
App sınıfı içinde calculate metodunu açıklamaya devam edelim. Metodun ilk satırlarını tek tek açıklayalım.

[code language="php"]
    public function calculate($request, $data)
    {
        // /posts/add gibi bir request geldi.
        $params = split(&quot;/&quot;, $request);;
        $className = __NAMESPACE__.'\\'.$params[1];
        //call_user_func_array
        $class = new $className();
        $class-&gt;connect($this-&gt;db);
        $class-&gt;getRelatedData($this-&gt;injectRelatedData());
[/code]

<ol>
	<li>Split metoduyla örneğin /Posts/View/1 ifadesini bir dizi olacak şekilde parçaladık.</li>
	<li>$className değişkenine __NAMESPACE__ ile namespace ifadesini dahil ettik. Yani namespace \Midori\Cms ise $params[1]'de Posts olacağından $className ifadesi \Midori\Cms\Posts olacak</li>
	<li>$class ifadesindeki new $className(); ifadesi ile, gelen istekteki sınıfın objesini oluşturduk.</li>
	<li>$class-&gt;connect($this-&gt;db) ifadesinde her sınıfta olan bağlan metodunu çağırdık ve db nesnemizi karşıdaki sınıfa gönderdik.</li>
	<li>$class-&gt;getRelatedData($this-&gt;injectRelatedData()); ifadesiyle de kategorilerin listesini dizi olarak sınıfa gönderdik ki, örneğin yeni girdi eklerken, kategorilerin listesini form içinde gösterebilelim.</li>
</ol>
Kalan kodlarla devam edelim. Az kaldı.

[code language="php"]
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
[/code]

<ol>
	<li>Eğer data verisi gelmediyse, boşsa, bu demek oluyor ki, istek bir formdan gelmiyor ve veri içermiyor. Bu sayede add veya edit, ekleme güncelleme işlemi olmadığını anlıyoruz.</li>
	<li>$params[2] ifadesi /Posts/add veya /Posts/view  ifadelerinde, add ve view kelimelerini tutar yani sınıfın yapılacak işini, sınıftan istediğimiz metodu. if($params[2]!=null) ifadesiyle sınıf içinde bir istek olduğunu anlıyoruz. Eğer bu ifade boş olsaydı Yani istek sadece /Posts şeklinde gelmiş olsaydı. O zaman bu isteği direk index işlemine, yani tüm girdileri public bir şekilde ziyaretçilere listeleme işlemine göndereceğiz.</li>
	<li>$params[3] ifadesi sadece /Posts/edit/3, /Categories/delete/1 veya /Posts/view/2 gibi $id yani tekil veriyle işlem yaptığımız durumlarda, yani güncelleme, tek veri getirme ve silme işlemleri sırasında geçerli olacak. Bu durumda $data = $class-&gt;$params[2]($params[3]); ifadesini $post-&gt;add(5) gibi bir ifadeye otomatik olarak çeviriyoruz.</li>
	<li>Eğer $params[3] ifadesi boşsa, bu da index, show gibi tüm verileri listeleyen bir metoddur. O zaman da doğrudan $data = $class-&gt;$params[2]() ifadesi $class değişkeni içinde $post sınıfı ve $params[2] değişkeninde örneğin 'show' ifadesi varsa $post-&gt;show() gibi çalışacaktır.</li>
	<li>Son iki maddede $data içine ham verileri alıyoruz. Data değişkeni bir dizi, sınıflarımızın metodları çıktı olarak dizi üretmeliler. Bu dizilerle beraber bir kaç bilgilye daha ihtiyacımız var. Metodun admin veya public temayı mı kullanması gerektiği ve metodun herhangi bi görünüme ihtiyaç duyup duymadığı. Örneğin, delete metodlarının bir görünümlerinin olmasına gerek yok, veri silindikten sonra doğrudan admin teması ile örneğin girdilerin listelendiği bölüme gidebilir. Bunları da sınıfın içinde metodların cevabında tanımlıyoruz. Her metod cevabında $data['render'] ve $data['template'] bilgileri olmalı. $data['render'] true yani doğru değerse, o metoda ait olan view dosyası gösterilsin. $data['template'] ifadesi public veya admin ise o temalara göre html cevapları oluşturulsun.</li>
</ol>

[code language="php"]
                if($data['render']!=false)
                {
                    $content = array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/'.mb_strtolower($params[2]).'.php',$data));
                    return $this-&gt;render('./www/'.$data['template'].'.php', $content);
                }
                else
                {
                    $data = $class-&gt;show();
                    $content =  array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/show.php',$data));
                    return $this-&gt;render('./www/'.$data['template'].'.php', $content);
                }
            }
            else{
                $data = $class-&gt;index();
                $content =  array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/index.php',$data));
                return $this-&gt;render('./www/'.$data['template'].'.php', $content);
            }
        }
[/code]

<ol>
	<li>Metoddan gelen cevapta render kısmı false değerine eşitse, delete gibi bir işlemimiz var. $content gibi bir değişken oluşturuyoruz. Bu değişken aslında bir dizi, 'related' kısmında bağlantılı bilgileri tutuyor, yani burada kategorilerin listesini. 'content' kısmında, render isimli metoddan gelen cevabı tutuyor.</li>
	<li>Peki render metodu nedir, yazının devamında satır satır açıklayacağım ama, burada kullandığımız için ön bilgi vereyim. Metoddan gelen ham bilgiyi alır, her metod için tanımladığımız view dosyalarını çeker, bunları da beraber gösterir. Biz burda render metodunu iki kere çağırıyoruz. Önce metoda özgü view dosyasının cevabını alıyoruz, daha sonra da tema değeri neyse admin veya public, onu gönderiyoruz, sonucu da cevap olarak döndürüyoruz. index.php'de de bu cevabı ekrana basmıştık.</li>
	<li>$render değişkeni false değilse, yani metodun view dosyasını basmak istiyorsak, o zaman $params[2] örneğin, add veya edit ise, bunu render dosyasına dosya adı olarak gönderiyoruz.</li>
	<li>False ise, her sınıfta tanımladığımız, admin listesini yani show kısmını çağırıyoruz. false olanlar zaten genellikle delete gibi admin işlemleri olduğu için admin listeleme işini yapan show metoduna gitmesi yeterli. Show metodunu daha sonra açıklayacağım.</li>
	<li>Eğer $params[2] yani add edit delete gibi ifadeler boşsa, yani istek olarak sadece Posts, Categories gibi bir kelime geldiyse, o zaman bu sınıfların herkese açık olan (admin paneli değil) index metodlarını çağıralım.</li>
</ol>
Eğer formumuzla birlikte veri geldiyse yapmamız gereken bi kaç cinlik var;

[code language="php"]
        else{
            call_user_func_array ( array($class, $params[2]), $data );
            $data = $class-&gt;show();
            $content =  array('related'=&gt;$this-&gt;injectRelatedData(),'content'=&gt;$this-&gt;render('./View/'.$params[1].'/show.php',$data));
            return $this-&gt;render('./www/'.$data['template'].'.php', $content);
        }
[/code]

<ol>
	<li>$data kısmından veri geldi. O zaman bu data'yı çağırdığımız sınıfın metodlarında kullanacağız.</li>
	<li>Sınıflarımızda metodlarımız örneğin, $posts-&gt;add($title,$content,$category_id) gibi parametreler alan metodlar.</li>
	<li>Ancak bizim elimizde verileri içeren diziler var. $data = array('category_id'=&gt;1, 'title'=&gt;'PHP Nedir?', 'content'=&gt;'İçerik bilgisi'). Veri bizim elimize bu şekilde geldiğinde, her sınıfı da array yani dizi kabul edip çalışacak şekilde değiştiremeyeceğimize göre, call_user_func_array ( array($class, $params[2]), $data ); metodunu kullanmak işimizi çözecektir. Peki ne işe yarar bu fonksiyon? Verdiğimiz fonksiyon ismi ile verdiğimiz veri içeren diziyi alıp, fonksiyona parametre olarak yerleştirip, çalıştıran ve sonucu bize döndüren müthiş bir öntanımlı php metodu. Biz de burada bunu kullandık.</li>
	<li>Add, edit gibi veri içeren form cevaplarını alıp kaydettikten sonra da yine her sınıf için tanımlı olan show metodu ile admin listeleme sayfasına geri döndük. Çünkü güncelle veya ekle işlemleri sonuçlandıktan sonra o sınıfın (mesela, girdiler, kategoriler) admin temalı sayfasına gitmeliyiz. Bu show metodunu da, sınıflarda yaptığımız değişikliklerde anlatacağım.</li>
</ol>
App sınıfı içinde, temaları verilerle birleştiren render metodu:

[code language="php"]
    public function render($file, $vars){

        if (is_array($vars) &amp;amp;&amp;amp; !empty($vars)) {
            extract($vars);
        }

        ob_start();
        include $file;
        return ob_get_clean();
    }
[/code]

Burada da yaptığımız işlemler şu şekilde:
<ol>
	<li>Önce temayı yazdığımız dosyanın ismini alıyoruz. Bu /View/Posts/add.php de olabilir /www/admin.php de olabilir.</li>
	<li>Daha sonra $vars ile örneğin, tüm postları içeren bilgileri alıyoruz ki, girdilerin listelendiği sayfada görüntüleyebilelim.</li>
	<li>extract ifadesi ile o değişkenin içindeki tüm değerleri kullanılır hale getiriyoruz. Mesela vars olarak $vars= array('posts'=&gt;array([0]=&gt;'array('title'=&gt;'baslik' ... ))) gibi bir dizi geldi. Extract komutu ile buradaki posts anahtarını $posts değişkeni olarak kullanabiliyoruz. Bu sayede tema dosyamızdaki posts değişkeni bu veriyi kullanabilir oluyor.</li>
	<li>ob_start() ve ob_end_clean() metodları, tema dosyalarımızdaki echo ifadelerinin ekrana basılmak yerine bir değişkene atılmasını sağlıyor. Burada render metodu tema ile düzenlenmiş, derlenip toparlanmış html dosyasını döndürüyor.</li>
</ol>
<h2>Sınıflardaki değişkenler</h2>
Tüm sınıfların kodlarını bölüm sonunda paylaşacağım ama burada tek tek yaptığımız değişiklikleri inceleyelim.

[code language="php"]
namespace Midori\Cms;

use \PDO;
[/code]

Sınıfları tanımlamadan önce her sınıfın başına namespace tanımlaması getirdik ki, kendi sınıflarımız, daha sonradan yazılıma dahil olacak sınıflarla çakışmasın. use \PDO ifadesiyle de yaptığımız PDO yani veritabanı işlemleri sınıfını çağırırken metodların başına \PDO\pdo gibi namespace ismi yazmak zorunda olmayalım.

[code language="php"]
    /**
    * Sistemdeki bağlı bilgileri içeren dizi
    *
    * @var array
    */
    private $related;

    /**
    * Bağlı
    *
    * @param PDO $db Bağlantı objesi
    * @return void
    */
    public function getRelatedData($related){
        $this-&gt;related = $related;
    }
[/code]

Sınıf değşkenlerine alakalı bilgiyi de dahil ettik. Çünkü örneğin, yazı ekleme formunda kategori listesine ihtiyacımız olacak, bu bilgiyi her seferinde çekmek yerine ihtiyacımız olduğunda bu değişkene gönderebilelim. Gördüğünüz gibi aslında sınıflar birbirleriyle konuşuyorlar ve birbirlerine mesaj, bilgi gönderebiliyorlar. Bunu da bağımlı olmadan yapabiliyorlar. getRelatedData yani bağlı bilgileri al metodu da, bu sistemde kategori bilgilerini alıp, $related değişkenine yazmaya yarıyor.

[code language="php"]
    /**
    * Bağlantı yapmaya yarayan metod
    *
    * @param PDO $db Bağlantı objesi
    * @return void
    */
    public function connect($db){
        $this-&gt;db = $db;
    }
[/code]

Her sınıfta olması gereken connect() yani bağlanma metodu. Sürekli farklı farklı veritabanı bağlantısı yapmak yerine bu metodu kullandık ve sınıfa PDO yani bağlantı sınıfından ürettiğimiz nesneyi dışarıdan dahil ettik. Yani sınıfımız, PDO sınıfına bağımlılıktan kurtuldu. Aynı prepare gibi metodları kullanan bir başka sınıfı da veritabanı sınıfı olarak dahil edebilirdik.

[code language="php"]
//add metodunda, veri gelmediyse döndürdüğümüz değerler
return array('render'=&gt;true,'template'=&gt;'admin','categories'=&gt;$this-&gt;related['categories']);
[/code]

Artık tüm metodların cevap olarak dizi döndürmesi ve bu dizilerin içinde 'render'=&gt; true/false ve 'template'=&gt;admin/public olması gerekiyor. Ayrıca bağlı bilgileri içeren değişkenleri de buradan temanın içine gidecek olan mesaja gönderebiliyoruz. Buradaki related, girdi ekleme formunun içindeki kategori seçmeye yarayan dropdown listenin içeriğini oluşturuyor.

[code language="php"]
    /**
    * Tüm girdilerin listelenmesini sağlayan metod.
    *
    * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
    */
    public function show(){
		$query = $this-&gt;db-&gt;prepare(&quot;SELECT * FROM posts&quot;);
        $query-&gt;execute();
        if($query){
            // Buradaki fetchAll metoduyla tüm değeleri diziye çektik.
            $result = array('render'=&gt;true,'template'=&gt;'admin','posts'=&gt;  $query-&gt;fetchAll(PDO::FETCH_ASSOC));
            return $result;
        }
        else
        {
            return false;
        }
    }
[/code]

Artık tüm sınıflarımızda, show metodu da var. Show metodu, index metodundan farklı değil. Tek farklı tema olarak, admin temasını kullanması.

[code language="php"]
        else{
            $oldData = $this-&gt;view($id);
            return  array('template'=&gt;'admin','render'=&gt;true,'categories'=&gt;$this-&gt;related['categories'],'post'=&gt;$oldData['post']);
        }
[/code]

Artık tüm edit yani güncelleme fonksiyonlarında $oldData değişkeni var. $oldData değişkeni, girdinin o anki halini alıyor ve düzenleme formuna öntanımlı değer olarak tanımlıyor. Yani 1 numaralı girdiyi düzenliyorsak, başlık bölümündeki PHP Nedir? ifadesini formda değer olarak görebiliyoruz.

[code language="php"]
return array('template'=&gt;'admin','render'=&gt;false);
[/code]

Bu da her silme metoduna koymamız gerekn dönüş verisi. Bu da App::calculate metodunda, render işlemleri sırasında bu metodun render edilmemesini bunun yerine, sadece O sınıfa ait admin listesinin render edilmesini sağlıyor.

Aslında yaptığımız çoğu işlemin, daha kolay ve daha sorunsuz bir şekilde yapılmasını sağlayan bazı nesne yönelimli programlama ilkeleri ve metodları var. Bir sonraki yazıda tüm bu kavramlardan bahsedeceğim.

Tüm sınıflarımızda bu değişiklikleri yaptığımızda programımız son bir kaç adım dışında bitmiş oluyor. Nedir bu adımlar? Sayfalama, kullanıcı oturum açma, yanlış girişleri engelleme, hatalı giriş olduğunda 404 sayfası gösterme.

Şimdilik bu kadar.

Tüm çalışan kodlarımız da burada:

<a href="https://github.com/mtkocak/merakli/tree/cf5545a474f6ccf8b0ab521edb603629ba7d23ed">https://github.com/mtkocak/merakli/tree/cf5545a474f6ccf8b0ab521edb603629ba7d23ed</a>