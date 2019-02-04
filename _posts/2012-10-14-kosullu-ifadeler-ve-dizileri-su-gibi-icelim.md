---
ID: 152
post_title: >
  Koşullu İfadeler ve Dizileri su gibi
  içelim
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/kosullu-ifadeler-ve-dizileri-su-gibi-icelim/
published: true
post_date: 2012-10-14 00:36:40
---
if-else; yani bilgisayara eğer böyleyle böyle yap, şöyleyse şöyle yap demek gibi kısaca anlatabiliriz; daha ayrıntılı tanımlamak gerekirse belirli kod parçalarını belirli koşullar altında çalıştırmak için gerekli olan programlama yapısı.

Örneğin yolda birini gördünüz, eğer karşınızdaki kişiyi tanıyorsanız (if) merhaba diyerek onu selamlarsınız, eğer tanımıyorsanız (else) yürümeye devam edersiniz, eğer tanımıyorsanız ama yine de gözünüz bir yerden ısırıyorsa (else if), sizi gözüm bi yerden ısırıyor dersiniz.

Mesela en basit örneğimizde; 4, 5'ten büyükse ekrana 4 5'ten büyüktür yazdırıyorum, değilse değildir yazan bir programcık oluşturalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.12-PM.png"><img class="alignnone size-full wp-image-136" title="Screen Shot 2012-10-13 at 10.04.12 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.12-PM.png" height="237" width="399" /></a>

Koşullu ifadelerde birden fazla koşula göre işlem yapmak mümkündür, iki veya daha fazla koşulu birbiriyle karşılaştırırken, mantıksal ve matematiksel operatörler de kullanabiliriz. Şimdilik bize en çok gerekli olanlar == eşitlik, &amp;&amp; her iki koşul doğruysa doğru veren operatörler, bu operatörlerden başlıcalarını görelim:

== eşitlik
!= eşitsizlik
&lt; küçüklük
&lt;= küçük eşitlik
&gt; büyüklük
&gt;= büyük eşitlik
&amp;&amp; iki koşul da doğruysa
|| iki koşuldan biri doğruysa
^ koşulların ikisi de yanlışsa

bunlardan başka operatörler de var ama biz işin başında olduğumuzdan bizim için en gerekli olanları bilmemiz yeterli. Bu makalelerin amacı PHP için teknik referans vermek olmaığından ve pratik uygulama geliştirmeyi anlattığından, en önemli artı olarak, karşılaştığınız sorunlar için kullanacağınız yapıları araştırmanız en iyi yetenek olacaktır.

Şimdi yine htdocs klasörünün aldında bulunan mtkocakPhpEgitimi klasöründeki 4-kosul.php dosyamızı açalım ve incelemeye başlayalım.

Asıl örneğimizi incelersek; Bu örneğimizde ilk olarak karşımıza çıkan yapı <strong>dizi</strong>. Diziler birden çok değişkeni bir arada tutmaya yarayan başka bir değişkendir. Birbiriyle bir şekilde bağlantısı olan verileri kolayca bir arada tutmaya, erişmeye ve default (önceden tanımlanmış) fonksiyonlarla işlem yapmaya yarayan bir yapıdır.
<pre>&lt;?php
/**  
*                    Merakli Bilişimci
*                   meraklibilisimci.com
**/
// Bu örnekte koşula bağlı çalışan ifadeleri ve dizileri anlayacağız.
// Dizi bir çok değişkeni bir arada tutan veri tipidir. Çekmeceye benzetebiliriz.

$ogrenciler = array('Mahir', 'Deniz', 'Yusuf', 'Hüseyin', 'Cevahir', 'Sinan', 'Erdal', 'Ulaş');</pre>
Örneğin birden fazla öğrenci ismini bir arada tutmak istediğimizi düşünelim. 10 öğrencinin herbiri için ayrı ayrı değişken yazmak hem zor, hem de zahmetli olurdu. Değişkeni içinde bilgiler olan bir çekmece gibi de düşünebiliriz. Yukarıdaki örneğimizde de 8 tane öğrencimiz var.

Dizileri basit bir şekilde şu şekilde tanımlıyoruz:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.06-PM.png"><img class="alignnone size-full wp-image-145" title="Screen Shot 2012-10-13 at 10.04.06 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.06-PM.png" height="104" width="599" /></a>

Yukarıdaki dizinin elemanlarına erişmek istediğimizde $dizi[0] şeklinde değişken olarak çağırmamız yeterli.

Bir diğer konu ve aslı örneğimizde kullandığımız olay şu: PHP'nin gücünü oluşturan en önemli özelliklerinden bir tanesi de öntanımlı (default) fonksiyonlar. Bu öntanımlı fonksiyonlar sayesinde birçok zaman, matematik, dizi, mantık, karşılaştırma, metin işlevlerini tekrar tekrar kod yazmamıza gerek kalmadan yerine getirebiliyoruz. Burada kullandığımız sizeof() fonksiyonu da oluşturduğumuz dizinin eleman sayısını bize veren öntanımlı fonksiyondur.
<pre>$ogrenciSayisi = sizeof($ogrenciler); // Bu default fonksiyon bize dizinin boyutunu verir, PHP'de bunun gibi bir çok default fonksiyonlar vardır. Biz bu eğitim son örneğinde zaman fonksiyonlarını kullanacağız.</pre>
Bu örneğimizde eğer öğrenci sayısı ondan küçük ve eşitse; süslü parantezlerle tanımlı olan kod bloğunu çalıştır. Burada gördüğünüz gibi ilk koşullu ifademizi tanımladık. Burada koşullu ifade, if'ten (eğer) sonra gelen parantezin içindeki ifadenin doüruluğunu kontrol ederek, eğer doğru ise devamında gelen kod bloğunu çalıştıracak. Eğer doğru değilse de, else (değilse)'den sonra gelen süslü parantezlerle ayrılmış kod bloğunu çalıştıracak.
<pre>if($ogrenciSayisi &lt;= 10)
{
    // For döngüsünde $i adında bir sayaç oluşturduk. Portakalı soydum gibi :)
    // İlk değer sayacın başlangıcını
    // İkinci değer sayacın ulaşacağı değeri
    // Üçüncü değer ise sayacın kaçar kaçar artacağını söyler. Eğer tek tek artırmak istersek $i++ da yazabilirdik.
    // Benzer işlermi yapan while ve do while döngüleri de vardır.
    for($i=0;$i&lt;=$ogrenciSayisi;$i = $i+2)
    {
        echo $ogrenciler[$i]."";
    }
}
else 
{
    echo "Ogrencilerin sayisi 10'dan büyüktür.";
}

?&gt;</pre>
Bu örneğimizi de <a href="http://127.0.0.1/mtkocakPhpEgitimi/4-kosul.php">http://127.0.0.1/mtkocakPhpEgitimi/4-kosul.php</a> adresinden çağıralım. Karşımıza şöyle bir görüntü gelecek:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-3.25.25-AM.png"><img class="alignnone size-full wp-image-137" title="Screen Shot 2012-10-14 at 3.25.25 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-3.25.25-AM.png" height="258" width="432" /></a>

Gördüğümüz gibi dizimizin içindeki herbir elemanı tek tek çağırdık ve ekrana bastık. Peki bunu nasıl yaptık?

Koşullu ifadenin içindeki bloğu incelediğimizde başka bir yapıyla karşılaşıyoruz:
<pre>    for($i=0;$i&lt;=$ogrenciSayisi;$i = $i+1)
    {
        echo $ogrenciler[$i]."";
    }</pre>
Burada for adı verilen ifade, ardından gelen süslü parantezlerle belirlenen kod bloğunun istenen sayıda ve sırada, istenen koşula bağlı olarak çalışmasını sağlar. Yani örneğin, öğrenciler listesindeki her bir öğrenciyi tek tek ekrana yazdırmak istersek. Her dizi elemanı için:
<pre>echo $ogrenciler[0];
echo $ogrenciler[1];
echo $ogrenciler[2];
echo $ogrenciler[3];
echo $ogrenciler[4];
echo $ogrenciler[5];
echo $ogrenciler[6];
echo $ogrenciler[7];</pre>
yazmak ne kadar yorucu ve gereksiz olacaktı. Üstelik elimizdeki dizinin eleman sayısını da bilmiyorsak ne olacak? İşte bunun için PHP'de bulunan sihirli kelime for.
<pre>    for($i=0;$i&lt;$ogrenciSayisi;$i = $i+1)
    {
        echo $ogrenciler[$i]."";
    }</pre>
Buradaki $i değişkeni, sayaç için kullanacağımız değişken. $i yerine daha önce döngünün dışında tanımladığımız başka bir değişkeni de kullanabilirdik. İlk sayaç değişkenimizi ve başlangıç değerini verdik. İkinci bölümde devam etme koşulunu, üçüncü bölümde ise devam etme koşulu doğru olduğu sürece yapılacak işlemi belirttik.

Daha sonra ise süslü parantezler içerisinde yapılacak işlemi tanımladık. Burada süslü parantez içinde kullandığımız echo $ogrenciler[$i].""; ifadesi php yorumlayıcısı tarafından verdiğimiz koşula göre (yani dizinin eleman sayısından küçük olana kadar) tek tek değiştirildi ve artırılarak çağırıldı.

<aside>Ek bilgi olarak bir de goto ifadesinden bahsetmek istiyorum:PHP'de goto ifadesi var. PHP yorumlayıcısının başka bir satıra atlamasını sağlıyor. Ancak goto'yu kesinlikle kullanmayın. Hatta unutun. Goto bir zehirdir. Mantıksal programlamanın ahlakına aykırıdır arkadaşlar. Goto yüzünden başınıza bela gelmesini :) istemiyorsanız, başlangıç aşamasında goto'ya girmeyin. Yorumlayıcının kodun ileri bir bölümüne atlamasını istersek kullandığımız bir ifadedir. Goto sayesinde asla okunamayan berbat kodlar yazmanız mümkündür. Aynı alerjimiz switch case: döngüleri için de geçerlidir.</aside><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.00-PM.png"><img class="alignnone size-full wp-image-138" title="Screen Shot 2012-10-13 at 10.04.00 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.00-PM.png" height="208" width="435" /></a>

En basit 100'e kadar sayma örneğimize göz attığımızda, for'dan sonra gelen kod bloğundaki $i değişkeninin her yürütmede değişerek, aynı kod bloğunun tekrar tekrar çağırıldığını görüyoruz.

Asıl örneğimizde for ifadesinin üçüncü kısmında yer alan $i++ ifadesi $i = $i+1; yani $i değişkenini bir artır ifadesiyle aynı anlama gelir. Eğer, örneğin, $i değişkenini ikişer ikişer arıtrmak isteseydik, $i = $i+2; kullanmamız yeterli olacaktı. Mesela dizide 5'er 5'er, 100'er 100'er de işlem yapmak istersek, yine aynı yapı işimizi kolaylıkla görecektir.
<pre>    for($i=0;$i&lt;$ogrenciSayisi;$i = $i+2)
    {
        echo $ogrenciler[$i]."
";
    }</pre>
Şimdi de ikişer ikişer artırma işlemimizin sonucunu görelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-3.35.05-AM.png"><img class="alignnone size-full wp-image-139" title="Screen Shot 2012-10-14 at 3.35.05 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-3.35.05-AM.png" height="199" width="437" /></a>

Bir ek bilgi daha: Süslü parantezlerle ilgili söylemek istediğim birşey var. Neredeyse ayrık bir kod bloğunu belirtmek istediğimiz heryerde süslü parantezleri kullanıyoruz. Fonksiyonlarda, döngülerde, sınıflarda, yani neredeyse heryerde. Açıp kapatıyoruz. Aman kapatmayı unutmuyoruz. PHP yorumlayıcısı affetmiyor çünkü. Bir de her süslü parantez açtığımızda bir tab ya da 4 boşluk karakteri kadar boşluk bırakalım. Daha önce bahsettiğimiz indentasyon konusu ve okunabilirlik açısından bunu yapmamız gerekiyor.

Şu ana kadar koşullu ifadeleri, dizileri anladık. Bir sonraki örneğimizde dizilerle ilgili başka detaylara gireceğiz.

Dayanışmayla;
Meraklı Bilişimci Mtkocak