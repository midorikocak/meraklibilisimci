---
ID: 553
post_title: 'Nesne Yönelimli Programlama Mantığı &#8211; OOP'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/nesne-yonelimli-programlama-mantigi1-oop/
published: true
post_date: 2014-03-09 15:35:58
---
<a href="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/5_kategori.jpeg"><img class="alignright size-full wp-image-554" src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/5_kategori.jpeg" alt="öğrenci-kıyafetleri" width="474" height="266" /></a>

Sürekli sağdan soldan duyuyorsunuzdur. Artık hayatımızda OOP ve NYP diye kavramlar var. Bu yazıda size teknik detaylardan daha çok sınıfları neden kullanmalıyız ve mantığı nedir onu anlatmaya çalışacağım.

Eğer siz de "ben fonksiyon yazıyorum, oop neymiş yeaaaee" demiyorsanız, kendinizi geliştirmeye de açıksanız oop'nin, yani nesne yönelimli programlamanın faydalarından başlayalım.

<strong>1. Kodunuz okunabilir olur.</strong>

Kodda kullandığınız değişkenleri, fonksiyonları rahatça görebilir ve değiştirebilirsiniz. Aynı projede çalışan sizden başka geliştiriciler kodunuzu anlayabilirler.

<strong>2. Kodunuz tekrar tekrar kullanılabilir</strong>

Örneğin her veritabanı işleminde tekrar tekrar SQL kodu yazmak yerine, bir veritabnı sınıfı kullanırsınız, ya da bu ekle, sil, göster, listele işlemlerini yapan bi sınıf oluşturursunuz, başka bir şirket bu proje oracle'da çalışsın istiyorum dediğinde apışıp kalmazsınız. Ya da bir okul için yazdığınız "<strong>öğrenciler</strong>" sınıfını, öğrencilerin notlarının yönetildiği ders yönetim sisteminde ve yemekhane yönetim sisteminde kolayca kullanabilirsiniz.

<strong>3. Kapsülleme</strong>

Kodlar üzerinde çalışan kişilerin kendilerini ilgilendirmeyen bölümlere erişmesini önler, maksimum güvenlik sağlarsınız. Hiçkimse ve hiçbir program bölümü kendisini ilgilendirmeyen koda müdahele edip çalışmasını bozamaz.

<strong>4. Tasarım avantajı</strong>

Daha önce yazılmış algoritmaları ve tasarım şablonlarını kolayca uygulama şansınız vardır. Bir de kodlar büyüdükçe yüzbinlerce satır içinde hata aramak, kodun yerini bulmak yerine, NYP size kolayca kodları sınıflandırma sağlar.

<strong>5. Gelişime açıklık</strong>

Diyelim ki öğrenci sınıfını yazdınız. Bu sınıfa ek özellikler ve metodlar eklemek istiyorsunuz. Örneğin "lise öğrencileri". Bunun için öğrenciler sınıfını değiştirmenize gerek yok. Aynı sınıfı kullanan programları bozabilirsiniz çünkü. Bunun yerine o sınıftan miras yoluyla başka bir sınıf türetirsiniz. Ek özellik ve metodları buraya yazarsınız. Bunu spaghetti kodda yapmanızın hiçbir yolu, mantığı ve faydası yok. Aynı zamanda, asıl sınıftan türeyen yeni sınıfların nasıl hareket edeceğini de belirlemek bize mantık avantajı sağlar. (polymorpism)

Buraya kadar herşeyi anlamamış olabilirsiniz. Avantajlarından bahsettik çünkü. Şimdi gelelim mantığa.

Beynimizin çalışma yapısı kavramlara, kavramların içinde bulunduğu konuma (bağlam) ve bu kavramların birbiriyle olan ilişkilerine bağlıdır. İnsan beyni, kavramları parça parça değil, bir bütün olarak algılar ve sınıflandırır.
<blockquote>Kavram, nesnel gerçekliğin insan beyninde yansıma biçimidir. Bundan ötürüdür ki her kavram doğrudan ya da dolaylı olarak nesnel gerçekliği içerir. Bu, örneğin ağaç gibi nesne kavramları için böyle olduğu gibi özgürlük gibi düşünce kavramları için de böyledir. Zümrüdü anka kuşu gibi tümüyle hayal ürünü olan kavramlar bile nesnel gerçeklikten yansımıştır. Ne var ki böyle kavramlar nesnel gerçekliğe döndürülemezler; eş deyişle denenemez, doğrulanamazlar. Bunlar bilimdışı kavramlardır. Demek ki kavramları bilimsel ve bilimdışı kavramlar olmak üzere de ayırmak gerekir.</blockquote>
<i>Atatürk Üniversitesi Sosyoloji Bölümü 1. Sınıf "Felsefeye Giriş" ve 3. Sınıf "Çağdaş Felsefe Tarihi" Dersi Ders Notları (Ömer YILDIRIM); "Felsefe Sözlüğü" Orhan Hançerlioğlu <a href="http://www.felsefe.gen.tr/felsefe_sozlugu/k/kavram_nedir_ne_demektir.asp"> http://www.felsefe.gen.tr/felsefe_sozlugu/k/kavram_nedir_ne_demektir.asp</a></i>

Nesne yönelimli programlama tam olarak bu mantığa dayanır. Daha önceden yapılması gereken şeyleri tek tek makineye söylediğimiz yordamsal programlamadan ziyade, gerçek hayattaki konuları ve kavramları, aralarındaki ilişkileri modellediğimiz bir programlama yapısıdır. Bu ne avantaj sağlar? Aslında avantajı program kodunu okuyan insanlar içindir. Daha önceden bahsettiğim okunabilirlik, anlşılabilirlik, yazılım projelerinin verimini artıran bir numaralı olgudur.

Örnek vererek başlayalım. Doğayı ilk sınıflandıran Aristo olmuştur. Doğada gördüğü canlıları sınıflandırmayı amaçlamıştır. Bilimsel olarak canlıları farklılaşmalarına göre tür ve sınıf olarak ayırırız ki kavramlar ve farklılıklar gözümüzde canlabilsin. Örneğin, hayvanlar, bitkiler, mantarlar, bakteriler sınıfları, sınıfların farklılıklarını daha iyi algılamamazı sağlarlar. Hayvanlar sınıfından devam edersek, memeliler, sürüngenler, balıklar, yumuşakçalar gibi sınıflara ayırabiliriz. Memeliler de farklı farklı sınıflara ayrılır. Burada en çok anlamamız gereken püf noktası, bir canlı eğer memeliler sınıfına üye ise, memeliler sınıfına özel olan süt verme, doğum yapma gibi özellikleri alır ve bu sınıfa ait diğer türlerle paylaşır.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/tax_interpret.gif"><img class="alignright size-full wp-image-555" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/tax_interpret.gif" alt="tax_interpret" width="474" height="468" /></a>

Yazdığımız yazılımlarda ilk yapacağımız işler, "Problemi belirleme (Analiz)", "Modelleme ile yapılar kurma (Kavram)", "Modellerin birbiriyle olan ilişkilerini belirleme (fonksiyonlar) (Bağlam)" ve "Test yapma" aşamalarını kafamızda canlandırmayı, nesneler ve birbirleri ile olan ilişkilerini düşünerek yapabiliriz.

Daha berrak bir örnek verelim. Mantıksal tasarımımızı doğru yaptığımızda geri dönüşlerimiz azalacaktır.

Bilal Ünal tarafından gönderilen soru üzerinden konuyu inceleyelim:
<blockquote>Midori hocam iyi günler. Lise öğrencisiyim ve yarışmaya katılacağım ve aklımda ki proje şudur ;

1-Yemekhane sistemi; öğrenci t.c kimlik numarası ve okul no'su ile giriş yapıp hangi günler yemek yemek istediğini seçecek.
2-Sınav sistemi; öğrenci aynı şekilde giriş yapıp, belirli günler yapılan dks(ders kontrol sınavı) sonuçlarına bakabilecek.</blockquote>
Görsel tasarım serisinde yaptığımız gibi, problemi öncelikle mantıksal olarak tasarlamamız gerekir. Buradaki kavramlar nelerdir?

En önce inceleyeceğimiz kavram "Öğrenci". Bu kavramın diğer kavramlarla olan ilişkisini inceleyecek iki adet yazılımımız olacak.
<ol>
 	<li>İlk projede "Yemek" kavramı var, ikinci projede "Ders" kavramı mevcut.</li>
 	<li>İlişkilere geçelim. Öğrenci "belirli günlerde", yemek yiyor.</li>
 	<li>Aynı zamanda "Öğrenci" belirli günlerde sınava giriyor.</li>
 	<li>Her dersin, belirli günlerde sınavları var.</li>
 	<li>Son olarak yemek yenilen günlerde, örneğin kahvaltı edildiyse, kahvaltı ile sınav sonuçlarının ilişkisini grafik olarak göstereceğiz.</li>
</ol>
Yaratmamız gereken sınıflar Öğrenci, Ders, Yemek, Sınav. Yemeğin farklı türleri varsa, onları da alt sınıf olarak veya özellik olarak belirleyebiliriz. Kahvaltı, öğlen yemeği, akşam yemeği gibi. Benzer bi ilişki sınav kavramı için de geçerli, sınav kavramının ders özelliği de, matematik, fizik, kimya vb. gibi oluşturulmuş ders sınıfının üyeleri arasından seçilebilir. Programın ilerlemesi sırasında değişimi de veritabanına kaydetmek en mantıklı çözüm olacak.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/1sinif_uyum_programi_9_13_eylul_2013_h89036.jpg"><img class="alignright size-full wp-image-556" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/1sinif_uyum_programi_9_13_eylul_2013_h89036.jpg" alt="1sinif_uyum_programi_9_13_eylul_2013_h89036" width="474" height="228" /></a>

Ogrenci'nin sistemde yapacağı işlemleri düşünelim.
<ol>
 	<li>tckimlik no, ogrenci no ve parola ile giriş yapmak</li>
 	<li>yemek sisteminde, rezervasyon yapmak. gününü ve yemek türünü seçmek.</li>
 	<li>ders sisteminde, sınava kayıt yaptırmak, sınav sonuçlarına bakmak.</li>
</ol>
İlk öğrenci sınıfımızı şu şekilde oluştururuz. Burada ilk önce construct metodunu ve get/set metodlarını incelemenizi öneririm.
<pre><code>
&lt;?php
class ogrenci
{
    private $tcKimlikNo;
    private $parola;
    public $ogrenciNo;

// Sınıf yaratılırken kullanılacak metod. Örneğin 1234567 ogrenci nolu ogrenci, şu şekilde yaratılır.
/*
$ilkOgrenci = new ogrenci('12345678910','1234567','asdfjkahsdjk');
*/
    public function _construct($tcKimlikNo,$parola,$ogrenciNo)
    {
        $this-&gt;setParola($parola);
        $this-&gt;setOgrenciNo($ogrenciNo);
        $this-&gt;setTcKimlikNo($tcKimlikNo);
    }

    public function girisYap($tcKimlikNo,$parola,$ogrenciNo)
    {
    // DB sınıfımız olduğunu varsayalım, ve db sınıfından students tablosuna, tckimlikno ev ogrencino verdiğimizde bu bize parolayı döndurdugunu düşünelim.
        if($db-&gt;login($tcKimlikNo,$ogrenciNo)==$parola){
            return true;
        }
        else{
            return false;
        }
    }

    // get set fonksiyonları
    public function getOgrenciNo(){
        return $this-&gt;ogrenciNo;
    }

    public function getTcKimlikNo(){
        return $this-&gt;tcKimlikNo;
    }

    public function getParola(){
        return $this-&gt;parola;
    }

    private function setTcKimlikNo($tcKimlikNo){
        $this-&gt;tcKimlikNo = $tcKimlikNo;
    }

    private function setParola($parola){
        $this-&gt;parola = $parola;
    }

    private function setOgrenciNo($ogrenciNo){
        $this-&gt;ogrenciNo = $ogrenciNo;
    }
}
</code></pre>
Burada private ve public kavramları da sınıfın dışından erişilebilecek metod ve değişkenleri belirtir. Mesela bu sınıftan kullanığımız $db-&gt;login() metodu, eğer public olarak tanımlanmış olmasaydı, hata alacaktık. Public olarak tanımlanmış değişken ve metodlara sınıf dışından erişebilirken, private olarak tanımlanmış metod ve değişkenlere sadece sınıfa üye olan fonksiyonlardan erişebiliriz. Bu kodda kullanılan $this-&gt;setOgrenciNo() ifadesindeki $this kavramı da, o sınıfta türetilen metod ve değişkenlere aynı sınıf içerisinden erişilmesini sağlar.

Kaynaklar:
<ol>
 	<li>http://www.php.net/manual/tr/language.oop5.php</li>
 	<li>http://www.realdealmarketing.net/docs/index.html</li>
 	<li>https://www.cs.drexel.edu/~introcs/Fa12/notes/06.1_OOP/Advantages.html?CurrentSlide=3</li>
 	<li>https://forum.ceviz.net/genel-programlama/109354-nesne-yonelimli-programlamanin-avantajlari.html</li>
 	<li>http://ismek.ibb.gov.tr/ismek-el-sanatlari-kurslari/webedition/file/2013_hbo_program_modulleri/nesnetabanliprogramlama1.pdf</li>
 	<li>http://www.felsefe.gen.tr/felsefe_sozlugu/k/kavram_nedir_ne_demektir.asp</li>
 	<li>http://torpil.com/egitim/lise-konulari/felsefe/hhcfp/felsefenin-bolumleri.html</li>
 	<li>http://w2.anadolu.edu.tr/aos/kitap/EHSM/1024/unite04.pdf</li>
 	<li>http://tr.wikipedia.org/wiki/Nesne_Y%C3%B6nelimli_Programlama</li>
 	<li>http://www.vanherbaryum.yyu.edu.tr/f/taksonomi.html</li>
</ol>