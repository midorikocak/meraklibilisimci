---
ID: 47
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-4
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-4/
published: true
post_date: 2017-02-15 18:04:16
---



<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/60ab0-1h0sb455xe85ehpnssbfyog.jpeg">
</figure>

<p>Bu yazı daha önce yazdığım <a href="https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-3-b2ed2bb60b51#.l82bto72w" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-3</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-3-b2ed2bb60b51[/embed]
<p>Bir önceki iki yazıda şu soruları sormuş ve kısmen cevap vermiştik:</p>
<ol>
<li>Eklemek istediğimiz başlık sözlükte yoksa ve çağırdıysak bu sorunu bildirim göstermeden nasıl hallederiz?</li>
<li>Başlık zaten varsa ve değiştirmek istemiyorsak, aynı başlığa yeni bir açıklama değerini nasıl ekleriz?</li>
<li>Bir başlığı silmek ya da düzenlemek istediğimizde ve başlıkta birden fazla açıklama varsa, tüm açıklamalara mı etki edeceğiz yoksa sadece birine mi?</li>
<li>Bir başlığa, tarih bilgisini nasıl girebiliriz? Bu tarih bilgisine dayanarak nasıl sıralama işlemi yapabiliriz?</li>
<li>Arama, filtreleme işlerini nasıl yapacağız?</li>
</ol>
<p>Önce, bir önceki yazıda spagetti usulüyle bir takım değişiklikler yapmıştık. Bu değişiklikleri Dictionary.php dosyasındaki sınıfa taşıyarak işe başlayabiliriz.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/af8a0-1_klh7s0xr1xdg5gt-i-zwa.jpeg">
</figure><p>Dictionary.php dosyamızın içine şu metodu ekleyelim:</p>
<pre><strong>public function </strong>getEntry(string $key): string<br>{<br><strong>if </strong>(<em>array_key_exists</em>($key, $this-&gt;<strong>entries</strong>)) {<br><strong>return </strong>$this-&gt;<strong>entries</strong>[$key];<br>    }<br>}</pre>
<p>2. soruyla devam edelim. Aynı başlığa birden fazla değer eklemek istediğimizde ne yapmamız gerek? Burada Dictionary sınıfımızın davranışını gözle görülür şekilde değiştirmemiz gerekecek. Yani, Dictionary sınıfı, artık kendisinden bir başlık talep ettiğimizde metin yani string değeri yerine bize bir dizi değeri döndürmeli.</p>
<h4>Sınıfları görevlerine göre parçalamak</h4>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/b8b03-1wem6vtuckwc4kzfoin7loq.jpeg">
</figure><p>Dikkat: Dictionary sınıfının sorumlulukları artıyor! Sözlük yani Dictionary sınıfı sadece verilen başlıklara karşılık açıklamaları yerine getirmek sorumluluğuna sahipti. Şimdi bir sözlük girdisinin nasıl yönetileceğine de el atmaya başladı. Bu nedenle, sınıflarımızı temiz ve düzenli tutmak istiyorsak, <strong>tek sorumluluk yani single responsibility</strong> prensibine göre sınıfımızı parçalamamız gerekiyor. Henüz tasarım ve prototip aşamasında olduğumuzdan, sınıfımızın davranışını, arayüzünü ve kodlarını istediğimiz gibi değiştirebiliriz. Ancak örneğin milyonlarca kullanıcısı olan, koda kafamıza göre müdahele etmemizin kabusa yolaçacağı durumlar profesyonel hayatımızda zırt pırt karşımıza çıkacak. İkinci aklımızda tutmamız gerek prensip <strong>Open-Closed yani Açık-Kapalı prensibi</strong>. Bu prensibe göre,</p>
<blockquote>Sınıflar değişime kapalı, gelişime açık olmalıdırlar.</blockquote>
<p>Üstte bahsettiğim sorunu çözmenin, farklı yöntemleri mevcut ki bu yöntemleri kullanmamız sayesinde Amerikayı yeniden keşfetmemize veya tekerleği bir daha icat etmemize gerek kalmasın. Bu prensibi nasıl kullanacağımıza daha sonra detaylıca değineceğim. Şimdilik sınıfımızı parçalamakla işe başlayalım. Sözlük sınıfımızı parçalayıp yeni bir girdi sınıfı hazırlayacağız. Burada özellikle dikkat etmemiz gerek nokta, sınıfların birbirlerinden bağımsız, tek başına yaşayabilen canlılar gibi olmaları. Şimdi tekrar sınıflarımızın sorumluluklarını güncelleyelim.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/cdbce-1c4-kbivbdmnqy1imgi86uw.jpeg">

<figcaption class="wp-caption-text">Programımız lego gibi sökülüp takılabilen parçalardan oluşmalı</figcaption></figure><h4>Sözlük sınıfının sorumlulukları</h4>
<ol>
<li>Farklı başlıklara sahip olan sözlükler yaratmak, başlığı güncelleyip değiştirebilmek.</li>
<li>Arama, sıralama, güncelleme, filtreleme işlerini yapmak.</li>
<li>Sıralı olan nesne verisini, örneğin metin, word veya json formatında kullanıcıya göndermek.</li>
<li>Bir girdiği listeden silmek, yeni bir girdiyi listeye eklemek. Dikkat, girdiyi güncellemek, sözlük sınıfını alakadar etmiyor. Aynı başlıkta hali hazırda başka bir girdi listede mevcutsa, hata vermek. Çünkü girdi başlıkları benzersiz olacak. Bazı sözlüklerde aynı başlıkla farklı girdiler eklenebiliyor. Ancak bizim sözlüğümüzde girdiler 1. açıklama 2. açıklama diye ilerleyecekler.</li>
</ol>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/194f0-1feix4q13gjvpojjhilttkw.png">

<figcaption class="wp-caption-text">Girdi Örneği</figcaption></figure><h4>Girdi sınıfının sorumlulukları</h4>
<ol>
<li>Yeni bir başlık ve açıklama ile bir girdi yaratmak.</li>
<li>Girdinin başlığını ve açıklamalarını değiştirmek.</li>
<li>Girdiye yeni açıklama girmek.</li>
<li>Girdiyi silmek. Silerken açıklamalar dizisini boşaltmak. Eğer girdinin tüm açıklamaları silindiyse, girdinin kendisini silmek.</li>
<li>Sırası bilinen açıklamayı silmek, değiştirmek.</li>
</ol>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/5632d-1vnygkvns0m9c1wnvs-ws9q.jpeg">
</figure><h4>Tembel yazılımcılar için arayüz yani interface kavramı</h4>
<p>Daha önce arayüz kavramından, otomobil örneği ile bahsetmiştik. Arayüz sınıfımızın nasıl kullanıldığını dünyaya tanıtan bir programlama yapısı. Arayüzler, içi boş metodların bir listesinden başka bir şey değil aslında. Arayüzlerin içinde metodun kodundan ziyade metodun imzasını, yani aldığı parametreleri, paramtere tipini, döndüreceği değerin tipini tanımlıyoruz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/6cdf0-1ybkb9mk_9xglyt3ilc9mzq.png">

<figcaption class="wp-caption-text">Bizi sadece dışarıdaki butonlar fln ilgilendiriyor, bu butonlarla cihazı kullanıyoruz. İçindeki elektronik hedelerle alakamız yok.</figcaption></figure><p>Arayüz tanımlamak aynı zamanda, kodun nasıl çalışacağını yazmaya girişmeden önce bize genel olarak program yapısını tasarlama fırsatı veriyor. Peki PHP’de arayüz nasıl tanımlanıyor? Öncelikle arayüz yazarken arayüz adı ve sonun Interface yazmayı alışkanlık haline getirelim. Böyle yapmak zorunlu değeil ama şıklık, düzenlilik açısından şart. Bunun gibi iyi pratiklere baştan sahip olmaya çalışırsanız, daha sonra sorun yaşamazsınız. Şimdi ilk arayüzümüzü yazmaya başlayalım.</p>
<h4>Girdi Arayüzü yani EntryInterface</h4>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><br><strong>interface </strong>EntryInterface<br>{<br><strong>function </strong>setKey(string $key);<br><strong>    function </strong>getKey(): string;<br><strong>function </strong>setValues(<strong>array </strong>$values);<br><strong>function </strong>getValues(): <strong>array</strong>;<br><strong>function </strong>getValue(int $order): string;<br><strong>function </strong>setValue(int $order, string $newValue);<br><strong>function </strong>addValue(string $value);<br><strong>function </strong>deleteValue(int $order);<br>}</pre>
<p>Tıpkı sınıflarda olduğu gibi interface yani arayüzlerin de ait oldukları isim alanları yani namespaceler var. Dosyanın başına içinde bulunduğumuz namespace’yi belirttik. Aslında doğrudan Entry sınıfını yazabilirdim ama metodların içerisini doldurmaya üşendiğim için interface yazmayı tarcih ettim. Sınıfları parçalarken gaza gelip atomu parçalamaya kadar gidebiliriz ama başımıza büyük bela alırız.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/b3736-1c6ywrs8tbkugqb68qykpuq.jpeg">

<figcaption class="wp-caption-text">O kadar çok berbat kod gördüm ki, artık dünyaya ben de böyle bakıyorum.</figcaption></figure><p>Einstein’in şöyle bir lafı var:</p>
<blockquote><em>Everything should be made as simple as possible, but not simpler. Albert Einstein</em></blockquote>
<p>Yani meali, “Herşey olabildiğince basit yapılmalıdır, ancak bundan daha basit olmamalıdır.” O yüzden şimdilik başta karar verdiğimiz görev ve sorumlulukların dışında nesneler oluşturmuyoruz ki proje bitsin.</p>
<p>Arayüzü satır satır okumaya devam edelim.</p>
<ol>
<li>
<strong>setKey:</strong> metin olarak bir başlık alacak. Girdinin başlığını belirliycek.</li>
<li>
<strong>getKey:</strong> başlığı metin olarak döndürecek.</li>
<li>
<strong>setValues:</strong> girdi içindeki açıklama listesini doğrudan değiştirmemizi sağlayacak. Şimdi farkettiğim üzere şimdilik bu metoda ihtiyacımız yok. Basitlik, bilgi gizleme ve güvenlik açısından silebiliriz. Ne kadar az metod o kadar kolay kullanım çünkü.</li>
<li>
<strong>getValues:</strong> girdiye ait başlıkları doğrudan dizi olarak döndüren metod.</li>
<li>
<strong>getValue:</strong> değerine erişmek istediğimiz açıklamaya sırasını belirterek erişmemizi sağlayan metod.</li>
<li>
<strong>setValue:</strong> değerine değiştirmek istediğimiz açıklamaya sırasını belirterek değiştirmemizi sağlayan metod.</li>
<li>
<strong>addValue:</strong> Sıra belirtmeden, doğrudan açıklamalar dizisine açıklama eklememizi sağlayan metod. Kolay kullanım için.</li>
<li>
<strong>deleteValue:</strong> Sıra belirterek istediğimiz açıklama değerini silmemizi sağlayan metod.</li>
</ol>
<p>Gördüğümüz gibi, elimizde bağımsız, başka bir sınıfla alakası olmayan, kendi başına bir program gibi kullanabileceğimiz bir sınıf arayüzü oluştu.</p>
<h4>Sözlük arayüzü yani DictionaryInterface</h4>
<p>Şimdi Sözlük sınıfına baştan yeni bir arayüz yazalım ve bu arayüz de girdileri yönetmek için bu girdi arayüzünü kullansın.</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><strong>interface </strong>DictionaryInterface<br>{<br><strong>function </strong>setTitle(string $title);<br><strong>function </strong>getTitle(): string;<br><strong>function </strong>setEntries(<strong>array </strong>$array);<br><strong>function </strong>getEntries(): <strong>array</strong>;<br><strong>function </strong>addEntry(EntryInterface $entry);<br><strong>function </strong>getEntry(string $key): EntryInterface;<br><strong>function </strong>deleteEntry(string $key);<br>}</pre>
<p>Bu arayüzü de satır satır inceleyelim.</p>
<ol>
<li>
<strong>setTitle:</strong> Oluşturacağımız sözlüğün başlık değişkenini değiştirmemizi, metin tipinde bir parametre alarak sağlayan metod. (set metodlarının hiçbirşey döndürmediğine dikkat edin. Set metodlarında hata olup olmadığını nasıl anlayacağız peki? Buna da hata denetimi konusuna geldiğimizde detaylıca değineceğim.)</li>
<li>
<strong>getTitle:</strong> Başlık değişkenini metin olarak döndürmek zorunda olan metod.</li>
<li>
<strong>addEntry:</strong> Sözlüğümüze entry yani girdi sınıfından bir nesneyi eklememizi sağlar. Set yerine add yani ekle ifadesini kullandık ki, sınıfta birden fazla entry yani girdi tutulduğu metodun adından anlaşılsın.</li>
<li>
<strong>getEntry:</strong> (metin tipinde $key) degeri girerek basliga erismemizi saglar.</li>
<li>
<strong>setEntries:</strong> Bu da sözlük sınıfında verileri tuttuğumuz diziyi değiştirmemizi sağlayan metod. Kullanırken dikkatli olmalı ve diziyi direk entries yani girdiler değişkenine eklememeli, tek tek girdiler kurallara uyuyor mu kontrol ederek sağlam verileri diziye eklemeliyiz.</li>
<li>
<strong>getEntries:</strong> Varolan verileri dizi şeklinde döndüren metod. Girdi sınıfından nesneler içeren bir dizi döndürecek.</li>
<li>
<strong>deleteEntry:</strong> Sözlükten adını belirttiğimiz girdiyi silen metod. Eğer bir girdinin hiç açıklaması yoksa, bu başlık da otomatik olarak silinmeli. Ancak buna daha sonra dikkat edeceğiz.</li>
</ol>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/b86b0-1gaxou01mwdb_qdzgqc7iyw.gif">

<figcaption class="wp-caption-text">Minik minik nesneler</figcaption></figure><p>Şimdilik bu kadar. Bir sonraki yazıda bu arayüzlerin içini nasıl dolduracağımıza ve kodu nasıl kullanıp test edeceğimize bakacağız.</p>
<p>Sevgiyle kalın.</p>
<p>Bir sonraki yazıya <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-5-s%C4%B1n%C4%B1f%C4%B1-in%C5%9Fa-etmek-83036f340215#.nyaf1iwql" target="_blank">buradan </a>ulaşabilirsiniz:</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-3-b2ed2bb60b51[/embed]

<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>