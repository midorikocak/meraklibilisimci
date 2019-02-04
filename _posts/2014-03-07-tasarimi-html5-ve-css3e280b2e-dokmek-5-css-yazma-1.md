---
ID: 541
post_title: 'Tasarımı HTML5 ve CSS3′e dökmek (5) – CSS Yazma &#8211; 1'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: 'https://www.meraklibilisimci.com/tasarimi-html5-ve-css3%e2%80%b2e-dokmek-5-css-yazma-1/'
published: true
post_date: 2014-03-07 16:27:23
---
Neredeyse herşey hazır. Hala tek satır kod yazmadık. Ama bütün bileşenler yerli yerinde. Şimdi sıra bu bileşenlerin görünümlerini tasarımcının istediği gibi şekillendirmemizde.

Bildiğiniz gibi ben bu blog'da PHP veya CSS el kitabı gibi herşeyi detaylı olarak anlatmıyorum. Konuların önce mantığını vermeye, daha sonra mantığını anlayan kişinin de merak ederek üreterek detaylara ineceğine inanıyorum. Sonuçta öğrenmeye yeni başlamış korku içindeki bir insanı ince detaylarda boğmamak gerekiyor. Bu nedenle bu yazıda da CSS detaylarını anlatmayacağım. Sadece temellerinden ve en çok ihtiyaç duyulan şeylerden bahsederek uygulamaya geçiyoruz.

CSS, "cascading style sheets", "Basamaklı Biçim Sayfaları", bir internet sayfasını ve bölümleri oluşturna tag'leri (etiketleri) istediğimiz gibi renklendirmemizi, şekillendirmemizi sağlayan şablon dosyalarıdır.
<p style="text-align:left;"><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/xml_doc2.gif"><img class="size-full wp-image-542 aligncenter" alt="xml_doc2" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/xml_doc2.gif" width="363" height="274" /></a>İnternet sayfalarından bilgiyi metin olarak almıyoruz, bazı başlıkların daha büyük, bazılarının daha küçük, daha okunaklı olmalarını amaçlıyoruz. Bazen ise vermek istediğimiz mesaja göre farklı tasarımlar yapmamız gerekiyor. Daha önce yazdığım CSS makalesinde CSS konusunda detaylar vermiştim. Ancak kısaca değinmek gerekirse şu;</p>
<p style="text-align:left;">Bir html etiketinin en önemli iki özelliği var. "id" ve "class".  Örneğin</p>

<pre><code>&lt;div id="ozet-menu" class="mavi-kenar beyaz-arka"&gt;&lt;/div&gt;</code></pre>
gibisinden bir etiketimiz olduğunu düşünelim. Burada id özelliği sadece o etikete özgü olan özel isimdir. Ve başka bir etiket aynı özel isimi alamaz, ve tek bir birleşik kelimeden oluşur. Ama class birden fazla olabilir, ve birden fazla etikete aynı class kullanara süsleme yapılabilir. Bu mantığı anlamak çok önemli.

CSS'leri siteye yedirirken atmamız gereken temel adımlar var.
<ol>
	<li>Font büyüklüklerini, tiplerini ve renklerini ayarlamak</li>
	<li>Listeleri biçimlendirmek (ul/li)</li>
	<li>Boyutları ayarlamak, mesela bir imajın içinde bulunduğu div'in boyuna gelmesini istediğimizi CSS dosyamıza yazmak</li>
	<li>Kenar boşluklarını ve iç boşlukları düzenlemek (margin ve padding kavramı)</li>
	<li>Arka plan imajlarını ve renklerini ayarlamak, varsa üzerine gelince renk değiştiren görünen kısımları belirlemek (hover)</li>
	<li>Bunlardan başka varsa eğer, animasyon, sağa sola kaydırma, döndürme gibi CSS3'ün getirdiği ek özelliklerden faydalanmak</li>
</ol>
Fon büyüklükleri, tipleri ve kenar boşlukları için melek kalpli tasarımcılarımız aynı zamanda bize guideline yani rehber olarak bir dosya vermiş, vermeselerdi, .psd dosyasını açıp, ruler tool ile resmin orasını burasını ölçmek zorunda kalacaktık.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/midori-sizes-04.jpg"><img class="alignright size-full wp-image-543" alt="midori-sizes-04" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/midori-sizes-04.jpg" width="474" height="841" /></a>

Şimdi yavaş yavaş bu dosyayı CSS3 kodu haline getirmeye başlayalım. Önce en üstten dosyamızı okumaya başladığımızda kenar boşlukları ve iç boşluklar olduğunu görüyoruz. Burada margin ve padding kavramı devreye giriyor.

CSS Box model dediğimiz kutu modeli diye birşey var. CSS, verdiğimiz uygun olan html taglerini kutu olarak algılamaya meğillidir. Bu ne demek. İçine bir yazı ya da resim koyduğumuz div, section, aside gibi etiketleri sınırları belli olan bir dikdörtgen olarak algılar demek.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/box_model.gif"><img class="alignright size-full wp-image-544" alt="box_model" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/box_model.gif" width="400" height="400" /></a>

Dikdörtgen bi kutu düşününün. margin'e vereceğiniz piksel boyu, dışındaki boşluğu, border'e vereceğiniz özellik kutunun sınırını belirleyen çizgiyi, padding ise kutunun içine uzanan boşluğu belirtir. Yani yazıların resimlerin birbirine değmemesi için bu 3 özellikten sıkça yararlanırız.

En önce font büyüklükleriyle işe başlayalım. Aslında HTML5 ve semantik web'de çok kulanılan etketlerden başlık etiketi foundation da önceden tanımlanmış fakat, biz kendi font özelliklerimizi kullanmak istiyoruz. h1, h2, h3, h4, h5, h6 olarak bilinen başlık etiketleri çok önemli. Google örneğin, sayfada h1 etiketinin bir tane olmasını çok önemsiyor. Daha sonra konuların önem sıralarına göre h2, h3 etc etiketlerini başlıkta kullanıyoruz.
<pre><code>
h1,h2,h3,h4,h5,h6{
    font-family: 'akzidenz-grotesk_bqmedium' !important;
}

h1
{
    font-size:11px !important
}

h2
{
    font-size:11px !important
}

h3
{
    font-size:10px !important
}

h4
{
    font-size:9px !important
}

</code></pre>
Şimdilik başlıklarımız için kullanacağız CSS kodlarımız bunlar. Bir sonraki adımımız kenar boşluklarını ve iç boşlukları ayarlamak. Bunlar için etiketlerde kullandığımız id ve tag özelliklerinden yararlanacağız.
<pre><code>

/*  BOŞLUKLAR  */
#main-slider
{
    margin-top:63px;
}

#summary-nav
{
    margin-top:77px;
}

#visible-header
{
    margin-top:63px;
}

#detail-nav
{
    margin-top:29px;
}

#main-content
{
    margin-top:92px;
}

#summary-footer
{
    margin-top:34px;
}

#detail-footer
{
    margin-top:92px;
}

</code></pre>
Burada row, yani satır olarak yazdığımız ve sütunlara ayırdığımız bütün bölümlerin üst boşluklarını belirledik. İlk etapta bunu görmek önemli, daha sonra istersek sağ sol ve alttan dış boşluklar da belirlememiz gerekirse, bu değeri azaltıp, tek margin değeri de ekleyebiliriz tag'lerin (etiketlerin) içine.

Süslemeye devam etmeden önce listeleri şekillendirmeliyiz. Dikkat edersek sitemizdeki navigasyonlar sıklıkla yatay. Bir navigasyonu yatay yapmanın en kolay yolu her alt öğesini sola yaslamak. ul elemamanları içindeki li etiketlerine "display:inline;" (yani tek satır içerisinde göster) veya "float:left;" dediğimizde listemiz dikeyden yatay hale gelir. Peki yan taraftaki noktacıkları nasıl yok edeceğiz? Orada da kullandığımız ul etiketi için "list-style-type:none;" tanımlamalıyız ki, noktacıklar çıkmasın. İlk navigasyonumuzu yapalım.
<pre><code>
#summary-nav
{
    margin-top:77px;
    font-size:16px !important;
    font-family: 'akzidenz-grotesk_bqmedium' !important;
}

#summary-nav ul
{
    list-style-type:none;
    margin:0;
    padding:0;
}

#summary-nav li
{
    display:inline;
    padding:20px;
}

#summary-nav li:not(:last-child){
    margin-right:77px;
}

</code></pre>
Kodumuzu adım adım incelediğimizde, font boyunu ayarlamışız, ul nin otomatik sağa kaydırma özelliğini kapatmak için margin ve padding'leri sıfırlamışız. li etiketlerini de li yatay göstermek için display:inline; kullanmışız. "#summary-nav li:not(:last-child){" dikkatinizi çekmiştir. Burada son eleman olmayan tüm elemanlar seçiliyor. Bu tarz css seçicileri, "sözde seçiciler" olarak adlandırılır. Bunları kullanarak kurallara göre seçim yaparız. Burada her elemana 77px sağ boşluk bıraktık, ancak son elemanın bu boşluğa sahip olmasını istemiyoruz. Bu yüzden son elemanı bundan çıkardık.

Bir de yine bu sözde seçicileri kullanarak son elemanın yanına küçük bir üçgen yerleştirebiliriz. Eni ve boyu 0 olan bir elemanın dış yüzey çizgilerinin sağdan soldan yukarıdan ve aşağıdan oranlarını değiştirdiğimizde farklı şekiller elde edebiliyoruz. Şimdilik bize lazım olan şey minik bi üçgen, ancak konu ile ilgili daha çok merak ettiğiniz şey varsa şu adrese bakabilirsiniz:

<a href="http://www.css3shapes.com/">http://www.css3shapes.com/</a>

<pre><code>
#summary-nav li:last-child:after{
    content: '';
    position: absolute;
    top: 50%;
    right: 3em;
    margin-top: -3px;
    height: 0;
    width: 0;
    border: 5px solid transparent;
    border-top-color: #dFeEFF;
    border-top-color: black;
}
</code></pre>

Bu üçgeni de bu şekilde yerleştirdikten sonra bir sonraki yazıda css işlerinin kalan işlerini halledeceğiz.