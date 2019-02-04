---
ID: 700
post_title: 'PHP ile içerik yönetim sistemi &#8211; 6 Veriyi html&#8217;ye çeviren PHP dosyaları'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-ile-icerik-yonetim-sistemi-6-veriyi-htmlye-ceviren-php-dosyalari/
published: true
post_date: 2014-08-25 12:30:51
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/10667_front_11-1.jpg"><img class="alignnone size-large wp-image-702" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/10667_front_11-1.jpg?w=680" alt="10667_front_11-1" width="680" height="399" /></a>

Kalan işlerimizi gözden geçirelim.
<ol>
	<li>Uygulama için konfigürasyon dosyası yazmak. Veritabanı bilgileri, saat dilimi gibi bilgileri tutsun.</li>
	<li>Veritabanı işlemlerini yapan sınıflarımız şimdilik oldukları gibi kalsınlar.</li>
	<li>Veri giren ve gösteren, düzenleyen formlarımızı tutan sayfalarımızı oluşturalım.</li>
	<li>Ama bu adımdan önce gereksiz kullanıcı girişlerini önlemek için oturum açalım. Kullanıcılar sınıfını oluşturalım. Bunun için admin bölümü sayfalarını oluşturalım.</li>
	<li>En son olarak tüm programımızı yönetecek olan dosyalarımızı oluşturup sınıflarımızı bitirelim.</li>
</ol>
Lego gibi minik minik parçaları birleştireceğiz. Bu parçaları oluştururken dikkat etmemiz gereken şey, daha sonra farklı projelerimzde de bu parçaları alıp kullanabiliyor olmamız. Bu yazıda ihtiyaç duyacağımız sayfa ve formları oluşturacağız. İçerik yönetim sistemi sayfaları nelerden oluşur peki?

Konuya veri açısından bakarsak 2 çeşit sayfamız var. Birincisi bilgi girişi yaptığımız sayfalar, ikincisi bilgi çıkışı yaptığımız sayfalar.

Konuya kullanıcı açısından bakarsak, herkese açık olan sayfalar ve yöneticiler için olan admin paneli. Örneğin herkese açık olan sayfaların içinde, bilgi girişi yapılan hangi sayfalar var? Kullanıcı yorumları, puanlama, beğenme gibi bilgi girişleri. Herkese açık sayfalarda bilgi çıkışı, kullanıcıların yazıları okudukları sayflardır. Admin panelinde bilgi çıkışı, yapılan sayfalar, verilerin listelendiği ve görüntülendiği sayflar. Admin panelinde bilgi girişi yapılan sayfalar ise, yazı ekleme, düzenleme gibi değişiklikleri yaptığımız sayfalardır.
<table>
<tbody>
<tr>
<th></th>
<th>Tüm Kullanıcılar</th>
<th>Yöneticiler</th>
</tr>
<tr>
<td> Veri girişi</td>
<td> Yorum, beğenme, puanlama</td>
<td> Yazı ekleme, düzenleme, listeleme</td>
</tr>
<tr>
<td> Veri çıkışı</td>
<td> Herkese açık yazıları görme, listeleme</td>
<td> Tüm yazıları ve yayınlanmamış yazıları görme, listeleme</td>
</tr>
</tbody>
</table>
Devam edelim; içerik yönetim sistemindeki kullanıcıya veri gösteren php sayfamızın bileşenleri neler? Tabii ki ham veri, ve bunu göstermemizi sağlayan html kodları. Diğer tüm sayfalarda olduğu gibi yazı başlığı sayfa logosu gibi şeyler. Html serisinde bunları en ince detayıyla anlattığım için konunun php ve içerik yönetim sistemini ilgilendiren kısmını yazacağım. Önce ana sayfada tüm girdilerin başlık ve özetlerini gösterdiğimiz bir index.php dosyası oluşturalım. Sayfamızda önce bütün yazıların başlıklarını gösterelim ve ilk cümleyi özetleyelim.

[code language="php"]
/*
*
* Kulllanıcılara girdileri gösteren sayfa.
*
* Bu sayfaya ham veri $posts şeklinde ilişkili dizi halinde gelecek
* biz de dosya içerisinde istediğimiz şekilde verileri göstereceğiz.
* Dosya bize ham veriyi, taglenmiş html şeklinde göstermeye yarıyor.
*
* @author Midori Kocak 2014
*
*/
&lt;?php
if(sizeof($posts&gt;0)):
    foreach($posts as $post):
        ?&gt;
        &lt;article&gt;
            &lt;h2&gt;&lt;?php echo $post['title']; ?&gt;&lt;/h2&gt;
            &lt;p&gt;&lt;?=substr($post['content'],0,40)?&gt;... &lt;a href=&quot;view.php/&lt;?=$post['id']?&gt;&quot;&gt;Devamını Oku&lt;/a&gt;&lt;/p&gt;
            &lt;small&gt;&lt;?=$post['created']?&gt;&lt;/small&gt;
        &lt;/article&gt;
        &lt;?php?
    endforeach;
endif;
?&gt;
[/code]

Burada yaptığımız, $posts değişkeni içinde gelen girdiler dizisini, okunur bir html dosyası haline getirmek. Önce bu mantığı iyi anlayalım ve en küçük parçalardan ilerleyelim. Daha sonra projemizi, lego gibi minik parçalardan birleştireceğiz. Foreach döngüsüyüle, her bir girdi dizisi elemanını alıp başlığını gösterdik. İçeriğin ilk 40 karakterini özet olarak gösterdik. Devamını oku linki yerleştirdik. Küçük bir şekilde girdinin yazıldığı tarihi de görüntüledik.

Tek bir makaleyi göstereceğimiz sayfayı kodlayalım.

[code language="php"]
/*
*
* Kulllanıcılara tek girdiyi gösteren sayfa.
*
* Bu sayfaya ham veri $post şeklinde ilişkili dizi halinde gelecek
* biz de dosya içerisinde istediğimiz şekilde verileri göstereceğiz.
* Dosya bize ham veriyi, taglenmiş html şeklinde göstermeye yarıyor.
*
* @author Midori Kocak 2014
*
*/
&lt;article&gt;
    &lt;h2&gt;&lt;?php echo $post['title']; ?&gt;&lt;/h2&gt;
    &lt;p&gt;&lt;?=$post['content']?&gt;&lt;/p&gt;
    &lt;small&gt;&lt;?=$post['created']?&gt;&lt;/small&gt;
&lt;/article&gt;
[/code]

Bunun önceki dosyadan pek bir farkı yok. Burdaki fark, sadece tek bir girdinin sayfaya geliyor olması. Yazı eklediğimiz sayfayı oluşturalım. Bir forma sahip olmak zorundayız. Add.php adlı dosyamız olsun.

[code language="php"]
/*
*
* Adminlerin yeni yazı eklediği sayfa
*
* Veriyi kullanıcıdan alacak ve gerekli yerlere göndereceğiz.
* Kategori seçeceğimiz için kategorilerin dizi olarak ($categories)
* dosyaya gelmiş olması gerekiyor. Çünkü bağlantılı bilgi.
* Biz de bundan liste oluşturacağız.
*
* @author Midori Kocak 2014
*
*/

&lt;form action=&quot;add.php&quot; method=&quot;post&quot;&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Başlık
        &lt;input type=&quot;text&quot; placeholder=&quot;large-12.columns&quot; /&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;İçerik
        &lt;textarea placeholder=&quot;small-12.columns&quot;&gt;&lt;/textarea&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Kategoriler
        &lt;select&gt;
            &lt;?php foreach ($categories as $category):?&gt;
                &lt;option value=&quot;&lt;?=$category['id']?&gt;&quot;&gt;&lt;?=$category['title']?&gt;&lt;/option&gt;
            &lt;?php endforeach:?&gt;
        &lt;/select&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/form&gt;
[/code]

Şimdilik formların ve linklerin gittikleri yerleri önemsemeyin. Doğrudan, başlık ve yazı girdiğimiz formumuzu oluşturduk. Dikkat ederseniz, kategorileri sistemden otomatik olarak çektik. Burada dinamik bir form oluşturmuş olduk.

Son olarak sayfamızı düzenleyeceğimiz sayfa:

[code language="php"]
/*
*
* Adminlerin yeni yazıları düzenlediği sayfa
*
* Yazı ekleme işlemi ile neredeyse aynı formu kullanıyoruz.
* Ancak formda eski değerleri görebilmemiz için bu sayfaya $post değişkeninin
* hazır olarak gelmesi gerekiyor.
*
* @author Midori Kocak 2014
*
*/

&lt;form action=&quot;edir.php&quot; method=&quot;post&quot;&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Başlık
        &lt;input type=&quot;text&quot; placeholder=&quot;large-12.columns&quot; value=&quot;&lt;?=$post['title']?&gt;&quot;/&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;İçerik
        &lt;textarea placeholder=&quot;small-12.columns&quot;&gt;value=&quot;&lt;?=$post['content']?&gt;&quot;&lt;/textarea&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;large-12 columns&quot;&gt;
      &lt;label&gt;Kategoriler
        &lt;select&gt;
            &lt;?php foreach ($categories as $category):?&gt;
                &lt;option value=&quot;&lt;?=$category['id']?&gt;&quot;

                    &lt;?php
                    if($category['id']==$post['category_id']){
                        echo &quot; selected &quot;
                    }
                    ?&gt;

                    &gt;&lt;?=$category['title']?&gt;&lt;/option&gt;
            &lt;?php endforeach:?&gt;
        &lt;/select&gt;
      &lt;/label&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/form&gt;
[/code]

Aslında edit sayfasından bir farkı yok, burada sadece girdinin eski değerlerini formun içine çektik. Ayrıca dikkat ederseniz, yazı hangi kategoride ise, form açılırken o kategorinin otomatik olarak seçilmesini sağladık.

Girdi eklediğimiz, düzenlediğimiz sayfalar da bu kadar. Diğer sınıflar için de aynı kodları yazacağız. Daha sonraki yazılarda admin ve ziyaretçi şemasını oluşturacağız. Kategori sayfalarını ve kullanıcı işlemlerini yapacak ve oturum açacağız. Daha sonra da projemizin legolarını birleştirecek ve bitireceğiz. OOP olarak projemizi tamamlayıp bitirdiğimizde, MVC yapısına (Model, View, Controller) (model, görüntü, kontrolcü) büyük bir adım atmış olacağız.

Projemizin şimdilik çalışmayan son hali burada:

<a href="https://github.com/mtkocak/merakli/tree/9defa4b18e71df9ff88c2376cc39baaa2ce1b50d">https://github.com/mtkocak/merakli/tree/9defa4b18e71df9ff88c2376cc39baaa2ce1b50d</a>