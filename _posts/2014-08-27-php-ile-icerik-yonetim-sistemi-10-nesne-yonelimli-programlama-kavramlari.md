---
ID: 735
post_title: >
  PHP ile içerik yönetim sistemi – 10
  Nesne yönelimli programlama kavramları
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-10-nesne-yonelimli-programlama-kavramlari/
published: true
post_date: 2014-08-27 16:16:35
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/tree5.jpg"><img class="alignnone size-large wp-image-736" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/tree5.jpg?w=680" alt="tree5" width="680" height="816" /></a>

&nbsp;

Bu yazıya kadar hep bebek adımlarıyla ilerledik. Sıra geldi büyük adımları atmaya. Yazılımımızda sınıf yapısını kullandık. Bu zamana kadar sınıf yapısını aşağı yukarı mantığını kavrayacak şekilde öğrendiniz. Ancak bilmemiz gereken bir sürü şey daha var. Programımızı bu kavramlara uyduralım. Sınıflarımızda tek tek değişiklikler yapalım.
<h2>DRY prensibi</h2>
DRY yani "Do not Repeat Yourself" kendinizi tekrar etmeyin anlamına gelir. Kodlarınızda sürekli copy paste ettiğiniz aynı şeyler varsa, bunları gruplayıp başka bir yerden çağırabilirsiniz. Burada buna benzer bir örnek yapalım. Mesela bizim sınıflarımızın hepsine $id, $related, $db gibi değişkenler var. Ayrıca hepsinde add, edit, delete, view, show fonksiyonları var. Mesela Kullanıcılar diye yeni bir sınıf yaratmamız gerekiyor. Bu kuralları hiç bilmeyen birinin kodların içinde boğulmasını da istemeyiz.

Add, edit, delete gibi metodlarımız her sınıfta farklı, ama her sınıfta ortak kullandığımız getRelatedData ve connect metodları da var. Bunların hepsini gruplayalım. Soyut bir sınıf yaratalım. Peki soyut sınıf, abstract class nedir? Kendisinden nesne yaratamadığımız, bize rehberlik etmesini istediğimiz, içinde boş bir metod barındıran sınıftır.

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

namespace Midori\Cms;

use \PDO;

abstract class Assets{
	
    /**
    * Kategorinin tekil id'sini tutan değişken. Başka kategorilerle karışmamasını sağlar
    *
    * @var int
    */
    public $id;
 		
    /**
    * Veritabanı bağlantısını tutacak olan değişken.
    *
    * @var PDO
    */
    protected $db = false;
    
    /**
    * Bağlantı yapmaya yarayan metod
    *
    * @param PDO $db Bağlantı objesi
    * @return void
    */
    protected function connect($db){
        $this-&gt;db = $db;
    }
    
    /**
    * Sistemdeki bağlı bilgileri içeren dizi
    *
    * @var array
    */
    private $related;
    
    public function __construct($db){
        $this-&gt;db = $db;
    }
    
    /**
    * Bağlı
    *
    * @param PDO $db Bağlantı objesi
    * @return void
    */
    public function getRelatedData($related){
        $this-&gt;related = $related;
    }
 
    /**
    * Kategori ekleyen metod, verilerin kaydedilmesini sağlar.
    *
    * @param string $title Kategori başlığı
    * @param string $content Kategori içeriği
    * @param int $category_id Kategori kategorisinin benzersiz kimliği
    * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    abstract public function add();

    /**
    * Tek bir kategordeki girdileri göstereceğiz
    *
    * @param int $id Kategorinin benzersiz index'i
    * @return array gösterilebildyise dizi türünde verileri döndürsün, gösterilemediyse false, yanlış değeri döndürsün
    */
    abstract public function view($id);
    
    /**
    * Tüm girdilerin listelenmesini sağlayan metod.
    *
    * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
    */
    abstract public function show();
	
    /**
    * Tüm kategorilerin listelenmesini sağlayan metod.
    *
    * @return bool listelenebildiyse doğru, listelenemediyse yanlış değer döndürsün
    */
    abstract public function index();


    /**
    * Kategori düzenleyen metod. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
    * güncelleyen metod.
    *
    * @param int $id Kategorinin benzersiz index'i
    * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    abstract public function edit();
    

    /**
    * Kategori silen metod, verilerin silinmesini sağlar.
    * Geri dönüşü yoktur.
    *
    * @param int $id Kategorinin benzersiz index'i
    * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
    */
    abstract public function delete($id);
	
}
?&gt;
[/code]

Lib klasörümüzün içine Assets.php diye bir dosya oluşturalım. Daha sonra diğer sınıflarımızdan bu dosyada olan bütün kodları silelim. Dikkat abstract olanlara dokunmayalım.

[code language="php"]
&lt;?php
/**
* Tüm sistemdeki girdileri yönetecek olan girdi sınıfıdır.
*
* Sistemdeki girdilerin düzenlenmesini, silinmesini, görüntülenmesini, 
* listelenmesini ve eklenmesini kontrol eden sınıftır.
*
* @author     Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/

namespace Midori\Cms;

use \PDO;

class Posts extends Assets{
	

    /**
    * Girdi başlığı
    *
    * @var string
    */
    public $title;
	
[/code]

Posts sınıfımız şimdi böyle. Diğer sınıflarda da aynı işlemleri yapalım. Önemli oranda satırdan kurtulduk.

Extends diyerek aslında bir kavramı daha öğrendik sayılır. Miras Alma. Sınıflar birbirlerinden özellikleri  ve metodları devralabilirler. Devraldıkları metodları da değiştirip farklı bir şekilde kullanabilirler. buna da çok biçimlilik diyoruz. (polymorphism) Örneğin, memeli özelliklerini devralan kedi ve köpek sınıfı, memeli sınıfında yer alan ses çıkar metodlarını "hav hav" ve "miyav" diye değiştirmişler. Burda da add, edit, delete gibi aynı isimli ama farklı işlemleri yapan metodlar bu duruma güzel bir örnek oluşturuyorlar.
<h2>Kapsülleme</h2>
Yani bu kadar anlamsız bir ismi olan bir kavram basitçe nasıl anlatılır ki? Public değişkenlerimiz vardı hatırlarsanız. Bu değişkenlere sınıf dışından erişilebilir ve değiştirilebilirler. Private değişkenlere ise sınıf dışından ulaşılamaz. Genellikle private değişken kullanmak önerilir ki, kodlarımızın üzerinde çalışan diğer arkadaşlar sınıf içindeki değerleri pat diye değiştirmesinler. Peki sınıf dışından erişilemeyen değişkene nasıl ulaşacağız? public getTitle() gibi bir metodla, bunlara get set metodları deniyor. Bu değişkenlere erişirken ve değiştirirken, değerlerin kontrol altında olmalarını sağlıyorlar.

[code language="php"]
&lt;?php

class Categpries{
    
    private $title;
    
    public function getTitle(){
        return $this-&gt;title;
    }
    
    public function setTitle($title){
        $this-&gt;title = $title;
    }
}

?&gt;
[/code]

<h2>__construct()</h2>
Bunun gibi iki alt çizgiyle çalışan metodlar var. Bizim şimdilik ihtiyacımız olan __construct() ve __destruct() metodları. __construct() metodu, sınıftan obje üretildiğinde çalışan metodlar. Biz soyut assets sınıfımızda construct metodunda connect metodunu çağırdık. Bunu neden yaptık? Çünkü eğer connect metodu çağırılmadıysa, sistemin hata vermesini istiyoruz.

Tüm kodlarımızı bu şekilde değiştirdikten sonra kodlarımızın son hali şu şekilde. (İpucu değişiklikler Lib klasöründe) :

<a href="https://github.com/mtkocak/merakli/tree/fbf9dddd81217a9cb1b682a8c136e25e28088aed ">https://github.com/mtkocak/merakli/tree/fbf9dddd81217a9cb1b682a8c136e25e28088aed </a>