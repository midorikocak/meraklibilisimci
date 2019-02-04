---
ID: 678
post_title: 'PHP ile içerik yönetim sistemi &#8211; 3 Sınıf taslakları'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-3-sinif-taslaklari/
published: true
post_date: 2014-08-22 23:25:04
---
<p><a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/fft99_mf3314680.jpeg"><img class="alignnone size-full wp-image-679" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/fft99_mf3314680.jpeg" alt="fft99_mf3314680" width="474" height="265" /></a></p><p>PHP ile içerik yönetim sistemi yazmaya devam ediyoruz, yapacağımız bütün işleri belirledik, şimdi sıra geldi sınıflarımızın taslaklarını hazırlamaya. 3 adet sınıfımız olacak, Posts (Girdiler), Categories (Kategoriler) ve Files (Dosyalar). Basit bi şekilde, içerik girme (add), bir adet görüntüleme (view), düzenleme (edit), silme (delete) ve listeleme (index) işlemlerini hepsinde yapacağız. Biz öncelikle girdilerden başlayalım. Taslak olarak sınıfımızı oluşturalım. Henüz fonsiyonlarımızın (metodlarımızın) içini doldurmayacağız.</p><pre>&lt;?php
/**
* Tüm sistemdeki girdileri yönetecek olan girdi sınıfıdır.
*
* Sistemdeki girdilerin düzenlenmesini, silinmesini, görüntülenmesini, 
* listelenmesini ve eklenmesini kontrol eden sınıftır.
*
* @author Midori Kocak &lt;mtkocak@mtkocak.net&gt;
*/
class Posts{
 
 /**
 * Girdinin tekil id'sini tutan değişken. Başka girdilerle karışmamasını sağlar
 *
 * @var int
 */
 public $id;
 
 /**
 * Girdi başlığı
 *
 * @var string
 */
 public $title;
 
 /**
 * Girdinin içeriği
 *
 * @var string
 */
 public $content;
 
 /**
 * Girdinin hangi tarihte oluşturulduğunu gösteren değişken
 *
 * @var string
 */
 private $created;
 
 /**
 * Girdinin hangi tarihte güncellendiğini gösteren değişken
 *
 * @var string
 */
 private $updated;
 
 /**
 * Tüm girdilerin listelenmesini sağlayan metod.
 *
 * @return bool listelenebildiyse doğru, eklenemediyse yanlış değer döndürsün
 */
 public function index(){
 }
 
 /**
 * Tek bir girdinin gösterilmesini sağlayan method
 *
 * @param int $id Girdinin benzersiz index'i
 *@return bool gösterilebildiyse doğru, eklenemediyse yanlış değer döndürsün
 */
 public function view($id){
 }
 
 /**
 * Girdi ekleyen metod, verilerin kaydedilmesini sağlar.
 *
 * @param string $title Girdi başlığı
 * @param string $content Girdi içeriği
 * @return bool eklendiyse doğru, eklenemediyse yanlış değer döndürsün
 */
 public function add($title, $content){
 }


 /**
 * Girdi düzenleyen metod. Verilen Id bilginse göre, alınan bilgi ile sistemdeki bilgiyi değiştiren
 * güncelleyen metod.
 *
 * @param int $id Girdinin benzersiz index'i
 * @return bool düzenlendiyse doğru, eklenemediyse yanlış değer döndürsün
 */
 public function edit($id){
 }

 /**
 * Girdi silen metod, verilerin silinmesini sağlar.
 * Geri dönüşü yoktur.
 *
 * @param int $id Girdinin benzersiz index'i
 * @return bool silindiyse doğru, eklenemediyse yanlış değer döndürsün
 */
 public function delete($id){
 }
 
?&gt;
</pre><p>Bu kod örneğinde bilmediğimiz kelimeler var evet! Baştan başlayalım:</p><ol><li>author: Sınıf dosyasını kim yazdı? Onu yazıyoruz. Aynen bu formatta.</li><li>@var: variable yani değişken demek, string, int ya da bool ile devam eder. string: yazı, int: sayı, bool ise, true/false, yani doğru yanlış belirten değişkenin adıdıdır, daha sonra da ne halta yaradıklarını açıklıyoruz.</li><li>@param: fonksiyon, yani metodlarımızın parametre yani girdi olarak ne aldıklarını tek tek, alt alta ve veri tipleriyle girdiğimiz açıklama bloğu. bu tarzda yazmaya çok dikkat ediyoruz arkadaşlar. Yazmasam noolur demeyin, yazın. Daha sonraki yazılarda bunun neden böyle olduğunu anlatacağım.</li><li>@return: string, int, bool, ile devam ediyor. fonksiyonun ne değer döndürdüğünü belirttiğimiz açıklama. Hiçbişey döndürmüyorsa, kısaca void, yani boş diyoruz.</li><li>public: yani yiğidin malı meydanda olur. bu değişken veya metoda, sınıf dışında heryerden erişilir. anlamadıysanız önemli değil açıklayacağım sonra. Kullanırken.</li><li>private: Özel, yani bu sınıfın bu özelliğine sadece sınıf içerisinden erişilebilir ve değiştirilebilir.  Burada created ve updated, yani güncellendi ve değiştirildi bilgilerini özel tanımladık. Çünkü özel bir saat tarih fonsiyonu kullanarak bu değişkenleri kaydedeceğiz, sınıf dışından başka kimse bunlara ulaşıp değiştirip görüntüleyemeyecek. Bunlar gizli saklı.</li></ol><p>Bilmediğimiz kelimeleri öğrendik. Biraz daha açıklama yapalım. Private olarak tanımladığımız değişkenlere dışarıdan erişemiyoruz ve değştiremiyoruz. O zaman ne yapacağız? Bu değişkenlere sonuçta sınıf içindeki herhangi bir fonksiyon erişebiliyor:</p><pre> /**
 * Şu anki tarihi döndüren metod
 *
 * @return string tarihi mysql formatında döndürür
 */
 public function getDate($id){
     $currentDate = date("Y-m-d H:i:s");
     return $currentDate;
 }</pre><p>Burada gördüğümüz son fonksiyon, bize o anki tarihi verecek olan fonksiyon. Bunu yardımcı olarak sınıfımıza dahil ettik. Ama mesela başka sınıflarda da bunu kullanmamız gerekseydi, bu yardımcı fonksiyonları başka bir sınıf altında toplayıp yarattığımız sınıfa dahil edebilirdik.</p><p>Gördüğünüz gibi fonkiyonlarımızın içleri şu anda boş. Bunun nedeni şu anda sadece sınıf yapısına hakim olmaya çalışmamız. Bu yüzden içini doldurmadan girdiler sınıfı ile başladık. Aslında, girdiler, kategoriler ve dosyalar sınıfında yapmamız gereken işlemler hep aynı, bunlar CRUD adı verilen, veri ekleme, düzenleme, çekme, listeleme ve silme işlemleri.</p><p>Bunların her birini, öğrendiğimiz SQL kodları ile üreteceğimiz sınıfa dahil edebiliriz. Evet. Ancak bu şekilde kod tekrar etmiş olur. Bir de sınıf php dosyamızın için SQL koyduğumuzu düşünürseniz, mySQl ile uyumlu kod, msSQL ile veya SQLite ile çalışmayabilir. Bu gibi problemleri önlemek için veritabanı işlemlerini kendi program yapımızın dışında tutmamız gerekiyor.</p><p>Şimdilik bu kadar. Bir sonraki yazıda, bu yazıda merak ettiğiniz gizemleri tek tek ele alıp çözeceğiz.</p><p><a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/plm-internet-web-database.png"><img class="alignnone size-full wp-image-680" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/plm-internet-web-database.png" alt="plm-internet-web-database" width="256" height="256" /></a></p>