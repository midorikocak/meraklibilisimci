---
ID: 60
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş-9 Şablonlar
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris-9-sablonlar/
published: true
post_date: 2017-03-18 10:31:50
---


<p>Bu yazı <a href="https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-8-web-aray%C3%BCz%C3%BC-928ebadd142c#.10xwtp7fb" target="_blank">Hiç Bilmeyenler İçin Nesne Yönelimli Programlamaya Giriş-8 -Web Arayüzü</a> yazısının devamıdır. Önce onu okumanızı öneririm.</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-8-web-aray%C3%BCz%C3%BC-928ebadd142c[/embed]
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/4e4dd-1vgudw22ssixgajw_pnzllg.jpeg">
</figure><p>Bir önceki yazıda View yani görünüm sınıflarından bahsettik ve EntryView adında bir sınıf oluşturduk. Veriyi HTML kodlarıyla render metodunun içinde sardık ve sunumunu yaptık. Şimdi aynı render metodunu bir template yani şablon metodu kullanacak şekilde değiştirelim.</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><strong>class </strong>EntryView<br>{<br><strong>private $entry</strong>;<br><br><strong>public function </strong>__construct(EntryInterface $entry = <strong>null</strong>)<br>    {<br><strong>if </strong>($entry !== <strong>null</strong>) {<br>            $this-&gt;<strong>entry </strong>= $entry;<br>        }<br>    }<br><br><strong>private function </strong>template(EntryInterface $entry)<br>    {<br>        $title = <strong>"&lt;h3&gt;" </strong>. $entry-&gt;getKey() . <strong>"&lt;/h3&gt;"</strong>;<br>        $values = $entry-&gt;getValues();<br>        $list = <strong>""</strong>;<br><strong>foreach </strong>($values <strong>as </strong>$value) {<br>            $list .= <strong>"&lt;li&gt;" </strong>. $value . <strong>"&lt;/li&gt;"</strong>;<br>        }<br><br>        $result = <strong>"&lt;p class='entry'&gt;" </strong>. $title . <strong>"&lt;ol class='values'&gt;" </strong>. $list . <strong>"&lt;/ol&gt;" </strong>. <strong>"&lt;/p&gt;"</strong>;<br><br><strong>return </strong>$result;<br>    }<br><br><strong>public function </strong>setEntry(EntryInterface $entry)<br>    {<br>        $this-&gt;<strong>entry </strong>= $entry;<br>    }<br><br><strong>public function </strong>render()<br>    {<br><strong>if </strong>(!<strong>isset</strong>($this-&gt;<strong>entry</strong>)) {<br><strong>throw new </strong>Exception(<strong>'Cannot render without entry'</strong>);<br>        }<br><br><strong>return </strong>$this-&gt;template($this-&gt;<strong>entry</strong>);<br>    }<br>}</pre>
<p>Bu kodda, önce private yani özel bir template metodu oluşturduk. Dikkat ettiyseniz Template metodu içindeki $this kullanmadık değişkenleri, $this ifadesinden kurtardık. Kodumuz bu haliyle de aynı şekilde çalışacak. Ancak bizim amacımız mümkün olduğunca PHP kodu ile HTML kodlarını birbirinden ayırmak. Bunun için içinde bulunduğumuz dizinde Template adında bir klasör oluşturalım ve bu dizinin içinde entry.php adında bir dosya oluşturalım. entry.php dosyasının içeriği şöyle olsun:</p>
<pre>&lt;<strong>p </strong>class=<strong>"entry"</strong>&gt;<br>    &lt;<strong>h3</strong>&gt;<strong>&lt;?= </strong>$entry-&gt;getKey() <strong>?&gt;</strong>&lt;/<strong>h3</strong>&gt;<br>    &lt;<strong>ol </strong>class=<strong>"values"</strong>&gt;<br><br><strong>&lt;?php foreach </strong>($entry-&gt;getValues() <strong>as </strong>$value): <strong>?&gt;<br><br></strong>&lt;<strong>li</strong>&gt;<strong>&lt;?= </strong>$value <strong>?&gt;</strong>&lt;/<strong>li</strong>&gt;<br><br><strong>&lt;?php endforeach</strong>; <strong>?&gt;<br><br></strong>&lt;/<strong>ol</strong>&gt;<br>&lt;/<strong>p</strong>&gt;</pre>
<p>Not: Buraya böyle salak salak boşluklar koymamın sebebi, kısa foreach yani süslü parantez yerine iki nokta ile biten döngü kullandığımda, html dosyası olarak çıktısı alınacak php dosyasında, php etiketlerinin, indentasyonu, yani html etiketlerinin hizalanmasını bozması. Normalde, performans için, etiket dışındaki bütün bu boşluk ve yeni satır karakterlerini siliyoruz, ancak ben kitapta kod örneklerinin düzgün olması için bu boşlukları koydum.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/fe725-1xeqwp0m_xnmunsijbgtwvq.jpeg">
</figure><p>Şimdi EntryView dosyasına dönüp template metodunun içeriğini şöyle değiştirelim:</p>
<pre><strong>private function </strong>template(EntryInterface $entry)<br>{<br><em>ob_start</em>();<br><strong>require 'Template/entry.php'</strong>;<br><strong>return </strong><em>ob_get_clean</em>();<br>}</pre>
<p>Yepyeni iki metod ile karşı karşıyayız. Output buffer yani ob_start() metodu, php’de ekrana basılacak olan herşeyi kaydetmeye yarar. Yani ob_start dediğimiz anda echo diyerek veya örneğin burada require diyerek çağırdığımız dosyanın metin içeriğini kamera gibi kaydetmeye başlıyoruz. ob_end_clean() metodu ise bu kaydettiğimiz şeyleri döndürür ve kaydettiğimiz output buffer denen zımbırtıyı siler. Bu sayede, tema dosyalarını kullanabilir, onları istediğimiz zaman ekrana istediğimiz değişkenlerle basabiliriz.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/2dd19-1gi2ikx2a9smexpslisxyia.jpeg">
</figure><p>Şimdi, Template dizinimiz içinde dictionary.php isminde ikinci bir dosya oluşturalım. Bu yazacağımız DictionaryView yani Sözlük Görünüm sınıfımızın tema/şablon dosyası olacak. İçeriğini şu şekilde oluşturup kaydedelim:</p>
<pre>&lt;<strong>p </strong>class=<strong>"dictionary"</strong>&gt;<br>    &lt;<strong>h2</strong>&gt;<strong>&lt;?= </strong>$dictionary-&gt;getTitle() <strong>?&gt;</strong>&lt;/<strong>h2</strong>&gt;<br><br><strong>&lt;?php foreach </strong>($dictionary-&gt;getEntries() <strong>as </strong>$entry): <strong>?&gt;<br><br></strong>&lt;<strong>p </strong>class=<strong>"entry"</strong>&gt;<br>        &lt;<strong>h3</strong>&gt;<strong>&lt;?= </strong>$entry-&gt;getKey() <strong>?&gt;</strong>&lt;/<strong>h3</strong>&gt;<br>        &lt;<strong>ol </strong>class=<strong>"values"</strong>&gt;<br><br><strong>&lt;?php foreach </strong>($entry-&gt;getValues() <strong>as </strong>$value): <strong>?&gt;<br><br></strong>&lt;<strong>li</strong>&gt;<strong>&lt;?= </strong>$value <strong>?&gt;</strong>&lt;/<strong>li</strong>&gt;<br><br><strong>&lt;?php endforeach</strong>; <strong>?&gt;<br><br></strong>&lt;/<strong>ol</strong>&gt;<br>    &lt;/<strong>p</strong>&gt;<br><br><strong>&lt;?php endforeach</strong>; <strong>?&gt;<br><br></strong>&lt;/<strong>p</strong>&gt;</pre>
<p>Daha sonra bir üst klasörde DictionaryView.php adlı bir dosya oluşturalım. İçi de şöyle olsun:</p>
<pre><strong>&lt;?php<br><br>namespace </strong>MidoriKocak;<br><br><strong>class </strong>DictionaryView<br>{<br><strong>private $dictionary</strong>;<br><strong>private $entryView</strong>;<br><br><strong>public function </strong>__construct(DictionaryInterface $dictionary)<br>    {<br>        $this-&gt;<strong>dictionary </strong>= $dictionary;<br>    }<br><br><strong>private function </strong>template(DictionaryInterface $dictionary)<br>    {<br><em>ob_start</em>();<br><strong>require 'Template/dictionary.php'</strong>;<br><strong>return </strong><em>ob_get_clean</em>();<br>    }<br><br><strong>public function </strong>render()<br>    {<br><strong>if </strong>(!<strong>isset</strong>($this-&gt;<strong>dictionary</strong>)) {<br><strong>throw new </strong>Exception(<strong>'Cannot render without dictionary'</strong>);<br>        }<br><br><strong>return </strong>$this-&gt;template($this-&gt;<strong>dictionary</strong>);<br>    }<br>}</pre>
<p>Bişi dikkatinizi çekti mi? EntryView ve DictionaryView dosyaları birbirine benzemeye başladı. Kod tekrarını önlemek için ne yapıyorduk? Kodları birleştirip başka bir yere referans veriyorduk. Kalıtım konusuna geldiğimizde bu konuya detaylı olarak değineceğim.</p>
<p>Şimdi app.php dosyamızı, DictionaryView adlı yeni dosyamızı kullanacak şekilde değiştirelim.</p>
<pre><strong>&lt;?php<br><br>require_once 'DictionaryInterface.php'</strong>;<br><strong>require_once 'Dictionary.php'</strong>;<br><strong>require_once 'EntryInterface.php'</strong>;<br><strong>require_once 'Entry.php'</strong>;<br><strong>require_once 'EntryView.php'</strong>;<br><strong>require_once 'DictionaryView.php'</strong>;<br><br><strong>try </strong>{<br>    $dictionary = <strong>new </strong>MidoriKocakDictionary(<strong>"Nesne Yönelimli Programlama Sözlüğü"</strong>);<br><br>    $nesne = <strong>new </strong>MidoriKocakEntry(<strong>'nesne'</strong>, <strong>'aklımızın dışındaki herşey'</strong>);<br><br>    $nesne-&gt;addValue(<strong>'harika bişi'</strong>);<br>    $nesne-&gt;addValue(<strong>'ingilizce object'</strong>);<br><br>    $şey = <strong>new </strong>MidoriKocakEntry(<strong>'şey'</strong>, <strong>'ismi olmayan nesne'</strong>);<br><br>    $dictionary-&gt;addEntry($nesne);<br>    $dictionary-&gt;addEntry($şey);<br><br>    $entriesArray = $dictionary-&gt;getEntriesAsArray();<br><br>    $entries = $dictionary-&gt;getEntries();<br>    $dictionaryView = <strong>new </strong>MidoriKocakDictionaryView($dictionary, <strong>new </strong>MidoriKocakEntryView());<br><br><strong>echo </strong>$dictionaryView-&gt;render();<br><br>} <strong>catch </strong>(Exception $e) {<br><strong>echo 'Error on line ' </strong>. $e-&gt;getLine() . <strong>' in ' </strong>. $e-&gt;getFile()<br>        . <strong>': &lt;b&gt;' </strong>. $e-&gt;getMessage();<br>}</pre>
<p>Herşeyi tamamladığımıza göre tarayıcımızı açalım:</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/cdcb8-1wl7q6fwjtlwwjr7pztimoa.png">

<figcaption class="wp-caption-text">Sözlük Görünümü</figcaption></figure><p>Gördüğümüz gibi, sözlüğümüzün başlığını ekrana bastık, daha sonra sözlüğün sahip olduğu girdilere göre verileri listelemeye başladık, her girdinin başlığını ve içlerindeki her açıklamayı ekrana bastık. Bunları yapmak için de tema dosyaları kullandık. Şimdi sayfamızın kaynağına bakalım.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/03/e0b8c-1jkamnrr0ycf64qwhhxavfq.png">

<figcaption class="wp-caption-text">Sayfa Kaynağı</figcaption></figure><p>İşte şimdi sayfamız birbirine girmiş etiketler yumağı yerine doğru dürüst bir HTML sayfasına benzedi. Peki bu düzgün formatlı bir html sayfası mı? Hayır, sadece dümdüz verileri listeliyoruz. Hala bir uygulamaya benzemiyor. Bir sonraki yazıda, tasarımını yaptığımız uygulamamızın sayfa düzenlerini nasıl oluşturup kullanacağımızı öğreneceğiz.</p>
<p>Bir sonraki yazıya buradan erişebilirsiniz:</p>
[embed]https://medium.com/@mtkocak/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-8-web-aray%C3%BCz%C3%BC-928ebadd142c[/embed]
<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2016/12/cceb0-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>