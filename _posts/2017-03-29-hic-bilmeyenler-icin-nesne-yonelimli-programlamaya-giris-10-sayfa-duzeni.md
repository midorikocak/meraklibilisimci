---
ID: 88
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-10 Sayfa Düzeni
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-10-sayfa-duzeni/
published: true
post_date: 2017-03-29 12:34:51
---



<p>Bu yazı <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-9-%C5%9Fablonlar-c0a143f8cab5#.2oz93nj5d" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-9 Şablonlar</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-9-%C5%9Fablonlar-c0a143f8cab5[/embed]
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/5d45b-1rpe0ecbhtkn-z-fhegyuwq.jpeg">

<figcaption class="wp-caption-text">Alexey Brodovitch</figcaption></figure><p>Web sayfalarında veya basılı mecralarda, hiçbir zaman veriyi, yazıyı resmi olduğu gibi okuyucuya sunmuyoruz. İnsanların yazıları rahatça okuyabilmeleri için, ya da web sayfamızda kaybolmadan dolaşabilmeleri için sayfamızdaki verileri, belirli bir düzen kullanarak sayfaya yerleştirmemiz ve biçimlendirmemiz gerekiyor. Burada web tasarımı yapmanın ilkelerine girmeyeceğim, ancak merak ediyorsanız bu konuyu araştırabilirsiniz.</p>
<p>Örneğin dümdüz veriyi ekrana bastığımızda, bunlardan bir anlam çıkarmak neredeyse imkansızdır.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/29839-1ytdlvn3bhbyredtzgjiviw.png">

<figcaption class="wp-caption-text">Arjantin Enflasyon Verisi</figcaption></figure><p>Bu yüzden bu verileri mesela grafikler kullanarak anlamlı hale getirmeye çalışırız.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/a4f92-1prjizeiccjsf0_aowtqehg.jpeg">

<figcaption class="wp-caption-text">Arjantin Enflasyon Grafiği</figcaption></figure><p>Yani amacımız sadece verilerimizin güzel gözükmesi değil, anlaşılabilir olması, uygulamamızın kolay kullanılabilmesi, okunaklı olması, belli amaçlar için aynı veriyi farklı şekilde görüntüleyebilmemiz (yeniden kullanılabilirlik) de aynı zamanda. Sayfa düzeni, veya herhangi bir şeyi tasarlarken, hatta kod yazarken kullanıcıların kolay kullanımını aklımızda tutmamız çok önemli. Ancak kolaylık, basitlik konusunda aklımızda tutmamız gereken diğer bir ilke ise şu:</p>
<blockquote>Her şey olabildiğince <strong>basit</strong> olmalıdır, ama olabildiğinden daha <strong>basit</strong> olmamalıdır. Albert Einstein</blockquote>
<p>Bu alıntıyı yapmamdaki sebep şu, siz işleri gelecekteki kullanıcılar kullanacak diye basitleştirmek ve mükemmelleştirmek için uğraşabilirsiniz. Uygulamanın, tasarımın ya da kodun, şurasını veya burasını iyileştirmek için günlerce aylarca uğraşabilirsiniz, ancak mükemmelleştirmeye çalışırken asıl amacı gözden kaçırabilirsiniz. Albert Einstein burada buna parmak basıyor. Bu hatayı 10 yıllık profesyonel yazılım hayatımda çok yaptım. Bu yüzden bu konuyu sürekli aklınızda tutmanızı, mükemmel değil, ama temiz, düzgün, çalışan ve daha sonra düzeltebileceğiniz incelikli prototipler üretmenizi öneririm.</p>
<p>Şimdi, dönelim tekniğe. Daha önceden Dekoratör tasarım deseninden bahsettik, yani bir veriyi alıp HTML etiketlerine sarmalayıp onu temiz bir web sayfası olarak kullanıcıya sunuyorduk. Bir önceki yazıda bunu yaptık. Şimdi veriyi değil de, bu ürettiğimiz bileşenleri de sarmalayabilecek bir yazılım yazalım. Yani Sayfa bileşeni, yan bilgi, ana bilgi, alt bilgi, form gibi bileşenleri barındırsın ve bunları gerektiğinde LEGO gibi birbirine ekleyip çıkarabilelim. Bu tasarım mantığına bileşen tabanlı geliştirme deniyor. <a href="https://www.webcomponents.org/" target="_blank">Web Components Standardı</a>, <a href="https://facebook.github.io/react/" target="_blank">React.js</a>, <a href="https://vuejs.org/" target="_blank">Vue.js</a> bu ilkeyi uygulamalarımızda kullanmamızı sağlayan teknolojiler. Kitabın sonuna doğru bu teknolojilerden de detaylı olarak bahsedeceğim.</p>
<p>Önce daha önce <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-8-web-aray%C3%BCz%C3%BC-928ebadd142c" target="_blank">şurada</a> bahsettiğim bileşenleri tek tek listeleyelim.</p>
<ol>
<li>Head — Her sayfada olacak ama görünmeyecek, css gibi ihtiyaç duyduğumuz dosyaların listesini tutacağımız bileşen. &lt;head&gt; etiketi içinde yeralacak. Sayfanın başlığını belirlediğimiz &lt;title&gt; etiketi burada olacak.</li>
<li>Üst Bilgi — Bütün sayfalarda değişmeyen, logo, üst navigasyon yani yön bulma linklerini, eğer varsa fb veya Twitter’daki gibi üst arama çubuğunu barındıracak, gerekiyorsa kullanıcının çıkış yapıp kendi profilini göreceği açılır menüleri tutacak bileşen. &lt;header&gt; etiketi ile tanımlanıyor.</li>
<li>Yan bilgi — Opsiyonel bir bileşen, genellikle içinde olduğumuz program bileşeninin varsa iç bölümlerinde gezinmemize yarar, yani bu bölümleri link olarak listeler. Bazı programlarda, o an programı kullanan kullanıcı ile bilgileri de listeleyebiliyor.</li>
<li>Ana bilgi — Buna main de deniyor ve &lt;main&gt; etiketi ile tanımlanıyor. Her sayfada bir adet bulunmak zorunda. Eğer bir sayfada önem olarak birbirine eşit farklı bölümler kullanacağım diyorsanız, &lt;section&gt; yani bölüm etiketini kullanacaksınız.</li>
<li>Alt Bilgi — Yine bütün sayfalarda değişmeyecek olan alt bilgi kısmı. Genellikle, sayfaların copyright, telif, gizlilik ve kullanım sözleşmesi gibi sabit kısımları, varsa şirket adresi iletişim gibi bilgiler burada yer almalıdır. &lt;footer&gt; etiketi ile tanımlanır.</li>
<li>Yeniden kullanılabilen bileşenler. Bunlara eleman / element ya da bileşen / component de denebiliyor. Lego gibi programlama amacında olduğumuzdan bu konunun mantığını anlamanız çok önemli. Bunu en kolay şu şekilde anlatabilirim. Örneğin, facebook’ta kendi duvarımızda yeni birşey paylaştığımızda ya da herhangi bir arkadaşımızın duvarında veya bir grupta birşey paylaşmak istediğimizde aynı form bileşeni ortaya çıkıyor ve biz bişiler yazıp gönder tuşuna basıyoruz.</li>
</ol>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/07e51-1y_e99bjahos0v3dnodmpzg.png">

<figcaption class="wp-caption-text">Duvara bişiler yazarken</figcaption></figure><figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/af7bc-1zuhbcz1b75z7hbejaejdbq.png">

<figcaption class="wp-caption-text">Gruba bişiler yazarken</figcaption></figure><p>İşte bu elemanı (ya da bileşeni) tekrar tekrar yazmamıza gerek yok, belli özelliklerini değiştirip, başka bir sayfada çağırıp kullanabilmemize yeniden kullanılabilirlik deniyor. İşte nesne yönelimli programlamanın bir diğer faydası da bu. Bu konuya da detaylıca sayfa kodunu yazmaya başladığımızda değineceğim.</p>
<h4>Yeniden kullanılabilirlik, kod tekrarını önler</h4>
<p>DictionaryView ve EntryView isimleriyle yarattığımız dosyaların birbirine benzediğine dikkat edin demiştim. Bir önceki yazıda kod tekrarını önlemekten bahsetmiştim. Şimdi gelin bu iki dosyadan kurtulalım. Program dizinimizin içinde View.php adlı bir dosya oluşturalım ve içeriğini şöyle değiştirelim:</p>
<pre><strong>&lt;?php<br>namespace </strong>MidoriKocak;<br><br><strong>class </strong>View<br>{<br><strong>private $data</strong>;<br><br><strong>public function </strong>__construct()<br>    {<br>        $this-&gt;<strong>data </strong>= [];<br>    }<br><br><strong>public function </strong>set()<br>    {<br>        $args = <em>func_num_args</em>();<br><strong>if </strong>($args == 1 &amp;&amp; <em>is_array</em>(<em>func_get_arg</em>(0))) {<br>            $this-&gt;<strong>data </strong>= <em>func_get_arg</em>(0);<br>        } <strong>elseif </strong>($args == 2 &amp;&amp; <em>is_string</em>(<em>func_get_arg</em>(0))) {<br>            $this-&gt;<strong>data</strong>[<em>func_get_arg</em>(0)] = <em>func_get_arg</em>(1);<br>        } <strong>else </strong>{<br><strong>throw new </strong>InvalidArgumentException(<strong>'Cannot set variable for View.'</strong>);<br>        }<br>    }<br><br><strong>public function </strong>render(string $filename)<br>    {<br><em>extract</em>($this-&gt;<strong>data</strong>);<br><br><em>ob_start</em>();<br><strong>require 'Template/' </strong>. $filename . <strong>'.php'</strong>;<br><strong>return </strong><em>ob_get_clean</em>();<br>    }<br>}</pre>
<p>Her zaman yaptığım gibi kodu tek tek açıklamaya başlayalım. Daha önce her görünüm sınıfı için $this-&gt;dictionary veya $this-&gt;entry gibi değişkenler kullanarak, görünüm sınıfımıza veri enjekte ediyorduk. İki görünüm sınıfında da render, template ve __construct metodları değişken isimleri hariç aynıydı. Bunun yerine tek bir sınıf kullanıp işimizi halletmek için data adlı bir dizi değişkeni belirledik. __construct metodunda yani new diyerek sınıftan bir nesne yarattığımız anda, php yorumlayıcısı bizim için bu boş diziyi anında oluşturacak.</p>
<p>Asıl hinlik cinlik yaptığımız kısım set yani değişkenleri belirlediğimiz metod. Bu metod Görünüm yani View sınıfına göndermek istediğimiz, template dosyalarımızın kullanacağı değişkenleri enjekte etmemize yarıyor. Yani örneğin bir template yani şema dosyasında $renk adlı değişken tanımlamak ve bu değişkene “pembe” değeri vermek istersem bunu $view-&gt;set(‘renk’,’pembe’) diyerek yapabilirim. Peki birden fazla değişkeni aynı anda bir dizi kullanarak göndermek istersem? Bunun için de metoda sadece $view-&gt;set($array) ifadesini kullanarak $array ismindeki değişkeni göndereceğim. Peki metodu bu iki farklı parametreyle çağırmamızı sağlayacak olan yöntem ne? Birincisi opsiyonel parametreler kullanmak yani metodu şu şekilde tanımlamak:</p>
<pre><strong>public function </strong>set($value, $name = <strong>null</strong>)</pre>
<p>Ancak bu şekilde metod ismi ve parametlerin isimlendirmesi anlamsız ve okunaksız oldu. Çünkü ikinci name yani isim parametresini opsiyonel tanımladığımda, $value adlı değişken dizi olmak zorunda. Ancak ben $value değişkenini sadece tek bir değişkenin değerini belirlemek için ifade ediyordum. Bunun yerine PHP de uzun süredir bulunan variadic yani parametlerinin sayısı değişebilen metod kullanmayı tercih ettim.</p>
<p>Bunu da metod çağırıldığında parametrelerin sayısını veren <em>func_num_args</em>() metodu ve sırasına göre metoda gönderilmiş parametrenin değerine değişken ismi kullanmadan erişmemizi sağlayan <em>func_get_arg</em>() yöntemlerini kullanarak sağladım. Bu tarz metodların, C ve C++ dilinde komut satırı uygulamaları yazılırken kullanıldığını görmüşsünüzdür. Çünkü tek bir program komut satırından çağırılırken, kaç parametrenin kaç değer alacağı önceden bilinmiyor. Örneğin diyelim ki composer adlı programı şu şekilde çağırabiliriz.</p>
<pre><strong><em>$&gt; composer help </em></strong>--<strong><em>format</em></strong>=<strong><em>xml </em>list</strong></pre>
<p>Burada help, programa verdiğimiz birinci parametre, format=xml ikinci parametre ve list de üçüncü parametre oluyor. Linux ortamına alışkın değilseniz, ya da Windows üzerinde cmd.exe kullanmadıysanız buraları anlamamanız gayet doğal. Sorun değil, öğrenmesi de zor değil. Tavsiye ederim.</p>
<p>Render metodu daha önceki görünüm sınıflarıyla aynı. Tek fark extract metodunu kullanmamız. buradaki extract($this-&gt;data) ifadesiyle, örneğin, data dizisi içinde ‘renk’=&gt;’pembe’ değerinde bir eleman tanımlandıysa, buradaki değişkeni doğrudan echo $renk; diyerek kullanabiliyoruz mesela. Dikkat etmemiz gereken en önemli nokta, kullanıcıdan gelen hiçbir veriyi buraya temizlemeden sokuşturmamamız. Yani bu metoda parametre olarak girecek her tür kullanıcının form üzerinden girdiği veriye htmlspecialchars() metodunu kullanarak müdahele etmemiz gerekiyor yoksa 14–15 yaşındaki veletler sistemimizi hem çok pis hacklerler, hem de bizimle dalga geçerler. Bu konudan da güvenlik bölümüne vardığımızda detaylıca bahsedeceğim.</p>
<p>Şimdi app.php dosyasını açalım ve şu şekilde değiştirelim:</p>
<pre><strong>&lt;?php<br><br>require_once 'DictionaryInterface.php'</strong>;<br><strong>require_once 'Dictionary.php'</strong>;<br><strong>require_once 'EntryInterface.php'</strong>;<br><strong>require_once 'Entry.php'</strong>;<br><strong>require_once 'View.php'</strong>;<br><br><strong>try </strong>{<br>    $dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>"Nesne Yönelimli Programlama Sözlüğü"</strong>);<br><br>    $nesne = <strong>new </strong>MidoriKocakEntry(<strong>'nesne'</strong>, <strong>'aklımızın dışındaki herşey'</strong>);<br><br>    $nesne-&gt;addValue(<strong>'harika bişi'</strong>);<br>    $nesne-&gt;addValue(<strong>'ingilizce object'</strong>);<br><br>    $şey = <strong>new </strong>MidoriKocakEntry(<strong>'şey'</strong>, <strong>'ismi olmayan nesne'</strong>);<br><br>    $dictionary-&gt;addEntry($nesne);<br>    $dictionary-&gt;addEntry($şey);<br><br>    $entriesArray = $dictionary-&gt;getEntriesAsArray();<br><br>    $entries = $dictionary-&gt;getEntries();<br><br>    $dictionaryView = <strong>new </strong>MidoriKocakView();<br><br>    $dictionaryView-&gt;set(<strong>'dictionary'</strong>, $dictionary);<br><br><strong>echo </strong>$dictionaryView-&gt;render(<strong>'dictionary'</strong>);<br><br>} <strong>catch </strong>(Exception | <strong><em>Error </em></strong>$e) {<br><strong>echo 'Error on line ' </strong>. $e-&gt;getLine() . <strong>' in ' </strong>. $e-&gt;getFile()<br>        . <strong>': &lt;b&gt;' </strong>. $e-&gt;getMessage();<br>}</pre>
<p>Dikkat ettiyseniz artık DictionaryView ve EntryView Dosyalarına ihtiyacımız kalmadı. Bunun yerine sadece tek bir sınıf kullandık.</p>
<p>App.php’yi web sunucumuzu kullanıp açtığımızda, tek bir görünüm sınıfının işleri başarıyla yerine getirdiğiniz göreceğiz.</p>


<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/a9df4-1rehkd-zmsd4-i0zukehhha.png">
</figure><figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/06c8e-1l6x8fbcpxix9nap43gsseg.png">
</figure>


<p>Bu yazıda son olarak dikkat etmenizi istediğim bir satır da şu:</p>
<pre>} <strong>catch </strong>(Exception | <strong><em>Error </em></strong>$e) {</pre>
<p>Burada Error ifadesini de catch bloğuna ekledik ki, sadece exception tipinde değil, error tipinde de hataları yakalayalım. Eğer bunu yapmasaydık ve diyelim ki app.php içinde $dictionaryView-&gt;set(<strong>‘dictionary’</strong>, $dictionary); yazmayı unutsaydık, yani template dosyasında olmayan değişkenlere erişmeye çalışsaydık PHP yorumlayıcısı şu şekilde isyan bayrağını çekecekti.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/eaa59-1yfivxty1edl9k7y0d2ndfa.png">
</figure><p>Bunun yerine Error $e diyerek istisnaların yanında hataları da aynı şekilde yakalamak istediğimizi belirttik ve kullanıcının doğru düzgün bir hata mesajı görmesini sağladık:</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/419a0-1lfrxbxylvnaezalsk3m_lg.png">
</figure><p>Bu sayede hatanın nerde olduğunu kolayca bulup onu böcek gibi ezebiliriz. Şimdilik bu kadar. Bir sonraki yazıda bileşenleri birleştirip bir sayfa oluşturacağız (nihayet).</p>
<p>Bir sonraki yazıya şuradan ulaşabilirsiniz:</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-9-%C5%9Fablonlar-c0a143f8cab5[/embed]

<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>