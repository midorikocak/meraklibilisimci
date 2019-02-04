---
ID: 63
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-7 —Sınıfları
  Kullanmak ve API meselesi
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-7-siniflari-kullanmak-ve-api-meselesi/
published: true
post_date: 2017-02-21 15:19:07
---


<p>Bu yazı daha önce yazdığım <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-6-girdi-s%C4%B1n%C4%B1f%C4%B1-e2c72d51686#.ykruckwzf" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-6</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-6-girdi-s%C4%B1n%C4%B1f%C4%B1-e2c72d51686[/embed]
<p>Bu yazıya kadar, bir programı sınıflar kullanarak nasıl tasarlayacağımızı, nasıl temiz kod yazacağımızı, kodlarımızı nasıl hatalara karşı kontrol edeceğimizi, sınıflarımızın sorumluluklarının ne olacağını anlattık. Peki programımızı kim nasıl kullanacak? Sınıflarımızı yazdık ve app.php dosyası içinde de kullandık, ama son kullanıcı bu programı nasıl kullanacak? Bu yazıda bu konuyu detaylıca işleyeceğiz. Ayrıca programımıza arama, sıralama, üyelik gibi ek özellikler eklemek istediğimizde ne yapacağız? Bu meseleye de bu yazıda kısaca değineceğiz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/d4c08-1y23jge7hmgrmni-y2_5xfg.jpeg">

<figcaption class="wp-caption-text">Kullanıcılar</figcaption></figure><h4>Genel olarak programların amacı</h4>
<p>Bu konuyu bu seride defalarca açıklamıştık ancak şimdi tıpkı başta sınıflarımızı tasarladığımızda yaptığımız gibi, programımızın nasıl çalışacağını ve amaçlarının ne olduğunu kısaca anlamamız gerekiyor ki, sınıflarımızı kullanacak program kodumuzu da <strong>nesne yönelimli</strong> bir şekilde tasarlayabilelim.</p>
<ol>
<li>Genellikle programların amacı kullanıcıdan istekleri ve girdiyi almak, bunu hatalı girdilere karşı doğruladıktan ve güvenlik açıklarına karşı temizledikten sonra işlemektir. Bu web uygulamalarında html dosyaları içindeki web formları aracılığı ile yapılır.</li>
<li>Kullanıcı girdileri genellikle bir dosyaya veya veri tabanına kaydedilir. Verilere ne şekilde kaydedildiği genellikle programın mantığını tutan sınıfın sorumluluğunda değildir. (MVC konusunda bu kavramı detaylıca açıklayacağım.)</li>
<li>Kullanıcı daha önce eklediği verilere erişmek ve görüntülemek isteyecektir. Yani program veri tabanından veriyi alıp, kullanıcıya, onun anlayabileceği şekilde göstermek zorundadır.</li>
</ol>
<p>Daha önce nesneleri tasarlamayı anlatırken, nesnelerin bağımsız programlar gibi canlı ve kendi kendine yeten varlıklar olmaları gerektiğinden bahsetmiştik. Yani hiçbir nesne, mantıken başka bir nesneye göbekten bağlı, olmayacak. Bir diğer kural da bir nesne içinde başka bir nesneyi new ifadesi ile yaratmamak. Böyle bir kod bloku yazıyorsak, sınıfımızın diğer nesneye göbekten bağımlıdır ve o nesnede yapılacak herhangi bir değişiklik nesnemizin davranışını ve ondan beklentilerimizi bozacaktır. Daha iyi anlamak için şöyle bir örnek vereyim: Mesela bu yazıya eklediğim linkler üzerinde hiçbir kontrolüm yok. Eğer linkte bulunan yazı silinirse veya değişip saçma sapan bir siteye giderse, yazımda saçma sapan bir bilgiye yer vermiş olacağım. Bu konuya bağımlılık enjeksiyonu ve bağımlılık çevrimi (dependency injection ve dependency inversion) deniyor. Kabul, Türkçe’ye çevirince çok abuk oldu ama konuyu detaylıca anlattığımda buna da doğru dürüst bi karşılık bulmaya çalışırız. Solid ilkeleri ile ilgili bir kaynak: <a href="http://tarikkaygusuz.com/post/solid-prensipleri" target="_blank">http://tarikkaygusuz.com/post/solid-prensipleri</a></p>
<h4>Programdan beklentilerimiz ve arayüzler</h4>
<p>Bu seride, sınıf ve program kavramlarını birbirinden ayrı düşünmemeye özen gösterdik. Bir sınıfı yazarken, yapabileceği işleri interface yani arayüzde tanımlamıştık. Daha sonra o sınıfı kullanan herhangi bir kod, sınıfın o arayüzde tanımlandığını bildiğinden erişebileceği ve kullanacağı public metotların neler olduğunu biliyordu. Herhangi bir programı web arayüzünden veya komut satırından kullandığımızda da aynı beklenti kalıplarına sahibiz. Örneğin, bir web uygulamasını veya sitesini açtığımızda, sol tarafta üstüste bir sürü link ile yapabileceğimiz işleri görebiliriz.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/8f3df-1m4v_upzwoqeyaakfipma_a.png">
</figure><p>Kullanıcıların aşina oldukları arayüzleri programlarımızda kullanırsak, hem kolay kullanım hem de anlaşılabilirlik sağlamış oluruz.</p>
<p>Eğer Unix/Linux/MacOs/BSD terminaline, kabuğuna, komut satırına, ya da adı her ne boksa veya windows’taki cmd yazınca çıkan dos ortamına, powershell’e fln alışkınsanız, komut satırında herhangi bir komut ardından -h veya — help yazdığınızda, o programına hangi parametreleri girerek işlem yapacağınızı gösteren bir yardım listesiyle karşılaşacağınızı bilirsiniz.</p>
<p>Windows ortamında, cmd.exe’yi çalıştırıp dir /? yazarsanız, içinde bulunduğunuz dizindeki dosyaları gösteren dir komutunun yardım dokümanını görürsünüz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/9141c-10sbqtk9adnhxmzerd7k7gq.png">

<figcaption class="wp-caption-text">Dos ortamında Dır komutunun yardımı</figcaption></figure><p>Unix ortamında çalışıyorsanız, herhangi bir komutun sonuna -h veya — help yazdığınızda aynı help dokümanıyla karşılaşmayı beklersiniz. Komutu yazan programcı, gıcık veya şerefsiz değilse genelde kullanıcının bu beklentisini tatmin etmeye çalışır.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/2b8c5-1rilfsxmmq_cmrdnafde-sw.png">

<figcaption class="wp-caption-text">Unix ortamında composer komutunun yardımı</figcaption></figure><p>İlk adım olarak bu “-h” ya da “ — help” parametresini bildiğinizde, kullanacağınız program hakkında hiçbir bilginiz olmasa dahi, programı nasıl kullanacağınızı size anlatacak bilgilere bu parametreyi kullanarak erişebilirsiniz.</p>
<h4>Yenilikçi arayüzler</h4>
<p>Yani bilgisayar programlarını yazarken kullanıcıların belirli davranış kalıplarına ve beklentilerine uyarsanız, kötü tasarımınız için küfür yemezsiniz. Tıpkı daha önce verdiğim araba arayüzü örneğinde olduğu gibi, vitesi tavana, direksiyonu vitesin olduğu yere, gaz pedallarını da direksiyonun üzerine koyabilirsiniz ama tabii ki koymamalısınız. Not: Bazı zamanlarda, aşırı yenilikçi kullanıcı arayüzleri yazmanız gerekebilir. Örneğin bir siteye girip uçak bileti almak yerine chat yapan yapay zeka bot programları ile konuşarak uçak bileti alabilirsiniz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/4238a-19iol1hdrivikibg4yemv3q.png">

<figcaption class="wp-caption-text">Chatbot arayüzü</figcaption></figure><p>Bu tarz yenilikçi arayüzler, yeni yeni kullanılmaya başlansalar da, bunlar için de ortak bir standart zamanla oturacaktır. En basitinden, herhangi bir chatbot’a merhaba dediğinizde merhaba demesini beklersiniz ki bu da bir arayüzdür ve beklentilerimizi tanımlar.</p>
<h4>Yönlendirme — Routing</h4>
<p>Şimdi genel olarak bir web uygulamasından beklentilerimiz meselesine dönelim. Şimdilik kullanıcı oturum açması parola girmesi kısmını geçeceğim. O konuyu kullanıcı yönetimi konusuna geldiğimizde detaylı olarak açıklayacağım. Bir web uygulamasını açmak için ilk olarak web tarayıcısına adres gireriz, ve genellikle uygulama neyi kaydediyorsa, ilk ekranında onların sıralı listesi gelir. Örneğin YouTube sitesini açtığımızda karşımıza sıralı, ya da belli başlı kategorilere ayrılmış videoların listesini görmek isteriz.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/b4d12-1nu_whmsugomrutyclfhkka.png">

<figcaption class="wp-caption-text">Youtube Anasayfa</figcaption></figure><p>Daha sonra mesela eğer video yüklemek istersek, video upload linkine tıklarız. Youtube örneğinde abuk subuk bir ikon kullanmışlar. Çok önemli ve dikkat etmemiz gereken ikinci beklentimiz de şu: Upload yani Video yükleme linkine tıkladığımız zaman, adres çubuğundaki adresin değişmesi. Görelim:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/9fcfe-1kyboqxqqrwisksgiglr9fg.png">

<figcaption class="wp-caption-text">Video Yükleme</figcaption></figure><p>Gördüğümüz gibi adres https://youtube.com/upload olarak değişti.</p>
<p>Örneğin haber sitelerinde ya da wordpress bloglarında okunaklı adresler kullanıldığını görmüşsünüzdür. <a href="http://www.diken.com.tr" target="_blank">http://www.diken.com.tr</a> sitesinde bir habere tıkladığımızda, tarayıcı şöyle bir adrese gider: <a href="http://www.diken.com.tr/galatasaray-hakem-hatalariyla-basladi-pazartesi-derbisiyle-bitirdi-ayricalik-degil-tarafsizlik-istiyoruz/" target="_blank">http://www.diken.com.tr/galatasaray-hakem-hatalariyla-basladi-pazartesi-derbisiyle-bitirdi-ayricalik-degil-tarafsizlik-istiyoruz/</a></p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/25f80-1l1d2qqh1n9xsebn3qfajzq.png">
</figure><p>Ya da örnek bir uygulamada, kullanıcı uygulamayı açtığında doğrudan kaydedilen şeylerin listesini şu şekilde görebilir:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/9aac2-1ltvkgoh25pcbaepjhxn6qq.png">

<figcaption class="wp-caption-text">Ana Sayfa</figcaption></figure><p>Ya da örneğin Kullanıcı, uygulamada ayarları değiştirmek istiyorsa, settings yani ayarlar linkine tıklar ve karşısına şöyle bir görüntü gelir:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/80469-1ksfzli-wfksqfovtqctfhw.png">

<figcaption class="wp-caption-text">Ayarlar Sayfası</figcaption></figure><p>Kullanıcı ayarlar sayfasını açtığında karşısına hazırda ayarları görebileceği bir liste ve o ayarları değiştirebileceği bir form çıkmasını bekler.</p>
<p>Belirli adresleri girerek programda belirli bölümlerin çalışmasını sağlama işlemine, <strong>yönlendirme </strong>yani <strong>routing </strong>deniyor.</p>
<h4>Uygulama Programlama Arayüzü — API</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/02/03229-1lf7kuuby1sgrniz2xsba0g.jpeg">

<figcaption class="wp-caption-text"><a href="https://www.smartfile.com/infographic/api/" target="_blank">https://www.smartfile.com/infographic/api/</a></figcaption></figure><p>Diyelim ki sözlük uygulamamızın internet adresi, http://dictionary.mynameismidori.com olsun. Örneğin yygulamadaki varolan sözlükleri listelemek istersek, http://dictionary.mynameismidori.com/dictionaries adresine gireceğimizi biliriz. Kısaca bu linkleri inceleyelim</p>
<ol>
<li>
<strong>/dictionaries: </strong>Sözlükleri listeleyece olan link</li>
<li>
<strong>/dictionaries/add: </strong>Yeni bir sözlük oluşturmamızı sağlayan formu karşımıza çıkarmalı.</li>
<li>
<strong>/dictionaries/12:</strong> 12 nolu id’ye sahip olan sözlüğü getirecek. Not: id dediğimiz numara, her varlık için eşsiz olan ve varlıkları birbirinden ayırmamızı sağlayan değişkendir. Örneğin, biz sözlük girdilerinde, girdi başlıklarını benzersiz olarak tanımladık. Yani ‘nesne’ adında başka bir girdi olmayacak. Bu sayede bir girdiye erişmek için anahtar olarak bu kelimeyi URL yani web adresi içinde kullanabiliriz.</li>
<li>
<strong>/dictionaries/12/edit:</strong> 12 numaralı sözlüğün, örneğin başlığını değiştirmemizi sağlayacak olan formu çıkaran adres.</li>
<li>
<strong>/dictionaries/12/delete:</strong> 12 numaralı sözlüğü silmemizi sağlayacak adres. Dikkat: Bu adrese erişildiğinde kullanıcıya emin misiniz diye bir bildirim yapılmalı ki, yanlışlıkla silme durumu olmasın.</li>
<li>
<strong>/dictionaries/12/entries:</strong> 12 nolu sözlüğe ait bütün başlıkların listesini getirmeli.</li>
<li>
<strong>/dictionaries/12/entries/add:</strong> 12 nolu sözlüğe ait yeni başlık eklememizi sağlayan formu göstermeli.</li>
<li>
<strong>/dictionaries/12/entries/nesne:</strong> İşte burada id, yani benzersiz anahtar olarak başlık kullandığımız için, linkimiz bu şekilde oluyor. Girdideki değerleri gösterecek. Bu sayfaya /dictionaries/12/entries/nesne/values adresiyle de erişebiliriz. Çünkü nesne girdisindeki açıklamaları zaten gösteren sayfa bu sayfa. Not: Peki ya add isminde çakışan bir başlık girilirse? Buna da dikkat etmemiz gerekiyor.</li>
<li>
<strong>/dictionaries/12/entries/nesne/edit: </strong>Nesne başlığına sahip olan girdinin başlığını değiştirmemizi sağlayan formu gösterecek.</li>
<li>
<strong>/dictionaries/12/entries/nesne/values/add: </strong>Nesne başlığına yeni açıklama eklememizi sağlayacak formu göstermeli.</li>
<li>
<strong>/dictionaries/12/entries/nesne/values/1:</strong> Nesne başlığında 1. sıradaki açıklamayı vermeli. Biz burada id, yani anahtar olarak değerin dizideki sırasını kullandık. Fakat doğru bir pratik olarak int yani tamsayı tipinde bir anahtar kullanmalıyız.</li>
<li>
<strong>/dictionaries/12/entries/nesne/values/1/edit:</strong> Nesne başlığında 1. sıradaki açıklamayı değiştiren formu göstermeli.</li>
<li>
<strong>/dictionaries/12/entries/nesne/values/1/delete:</strong> Nesne başlığında 1. sıradaki açıklamayı silecek olan adres.</li>
</ol>
<p>Dikkat ettiyseniz, adresler belli deseni takip ediyor. Yani kaydettiğimiz varlığın çoğul ismi — anahtar değeri — add,edit,delete komutlarından bir tanesi. Eğer komut yoksa, hazırda kaydedilmiş varlıkları listeliyor veya anahtar varsa o varlığı ve bağlantılı varlıkları gösteriyor. Yani 12 numaralı sözlüğü açtığımızda, aynı zamanda aksini belirtmediysek, sözlükteki girdilerin listesini de görebilmeliyiz. Aslında bu listeleme işlemine de index deniyor. Yani <strong>/dictionaries/12/entries/ </strong>linki ile<strong> /dictionaries/12/entries/index </strong>linki aynı yere gidiyor.</p>
<p>İşte programı kullanmak için girdiğimiz bu adreslere programımızın <strong>Uygulama Programlama Arayüzü</strong> veya <strong>API</strong>’si deniyor. Daha bilimsel bir tanımlama verecek olursak:</p>
<blockquote>Uygulama Programlama Arayüzü (UPA) [İngilizce: Application Programming Interface — API], işletim sisteminin, bir kütüphanenin veya bir servisin diğer programlara sağladığı fonksiyon ve sınıf kümesidir. Kaynak: <a href="http://www.emo.org.tr/ekler/1db5dd8fa2d87e7_ek.pdf" target="_blank">http://www.emo.org.tr/ekler/1db5dd8fa2d87e7_ek.pdf</a>
</blockquote>
<p>Başka bir kaynak da şurada: <a href="http://koddit.com/yazilim/api-nedir-ne-ise-yarar-orneklerle-inceleyelim/" target="_blank">http://koddit.com/yazilim/api-nedir-ne-ise-yarar-orneklerle-inceleyelim/</a></p>
<p>API’lar sayesinde, örneğin, bir kullanıcıya ait twitter akışını, tıpkı o kullanıcının twitter profilini açmış gibi kendi sayfamızda gösterebiliyoruz. Bu konuyu farklı API’ları kullanmak bölümünde detaylıca anlatacağım.</p>
<p>Yani sınıflarımızı kullanacak program kodunu yazarken, ayrı ayrı index.php, add.php, edit.php gibi dosyalar yazıp tarayıcıyı bu sayfalara yönlendirmek yerine, kullanıcının isteklerini alıp yönlendiren bir program koduna ihtiyacımız olacak. Bunu da bir sonraki yazıda yapacağız.</p>
<p>Bir sonraki yazıya şuradan ulaşabilirsiniz:</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-6-girdi-s%C4%B1n%C4%B1f%C4%B1-e2c72d51686[/embed]
<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>