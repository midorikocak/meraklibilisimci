---
ID: 746
post_title: >
  Programlama nasıl öğrenilir? İlk
  adımlar
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/programlama-nasil-ogrenilir-rehber/
published: true
post_date: 2014-09-01 05:59:55
---
<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/1328811341794666_b.jpg"><img class="alignnone size-full wp-image-747" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/1328811341794666_b.jpg" alt="1328811341794666_b" width="400" height="240" /></a>

Programlama öğreneceğim diyorsanız, internette bir sürü kaynak var evet. Ama önce bilmemiz gereken, atmamız gereken bir sürü ilk adım var ve ben bunların genelde atılmadığını görüyorum. Belli bir uzmanlık seviyesine gelen insanların dahi bu ipuçlarını bilmedikleri oluyor. Bina temelden sallanınca, üst katlar daha çok sallanıyor ne yazık ki. Gelelim kurallara:
<h2>1. İyi yürekli olun</h2>
Süper müthiş bir uzmanlık, herşeyi bilmek mümkün değil. Ben PHP'ye başlayalı 13 sene oldu. Gittim bilgisayar mühendisliği okudum, algoritma kavramlarını, nesne yönelimli programlamayı vs. bir sürü şeyi öğrendim. Öğrendikçe bilmediğim bir dünya şey olduğunu gördüm. Etrafıma baktığımda bir sürü uzman tipindeki insanın ukala tavırlar içerisinde olduğunu gördüm. (Buna bazen ben de dahilim) Ama bir an geliyor, 13 - 14 yaşında bir çocuk gelip öyle dahiyane bir şey getiriyor ki karşınıza, o ukalalık çöpe gidiyor ve kalıyorsun.
<h2>2. Başlayın</h2>
Önce işin en başından başlayın. Kocaman adımlar atmaya çalışıp hevesinizi kaçırmayın. Bu iş zor değil. Önce küçük küçük adımlar atın, kod örneklerini deneyin, olayın mantığını kavramaya çalışın. Piyasadaki kitaplar genelde kullanım kılavuzu tadında oldukları için insanın gözü korkabiliyor. Ben de bunu çok yaşadım. Faydalı şeyler yapın. Önce kendi sitenizi yapın mesela.

Burdan buyrun: <a href="http://meraklibilisimci.wordpress.com/egitim-konulari-kurs/">http://meraklibilisimci.com/egitim-konulari-kurs/</a>
<h2>3. Paylaşın</h2>
Bilgiyi paylaşın arkadaşlar. meraklibilisimci.com nasıl ortaya çıktı biliyor musunuz? Bilişim çalışanları dayanışma ağı'na PHP konusunda eğitim önerdim. Sonuçta bildiğim konu. Makine mühendisleri odasında eğitimi verdim. Sunum hazırladım, video'ya çekildi, örnekler hazırladım. Video'nun dökümünü yazıya geçme fikri aklımdan geçti. Sonuçta 1997 senesinde 13 yaşındayken bütün istanbuldaki kitapçıları linux kitabı bulacağım diye aradığımı biliyorum. Zar zor, Görkem Çetin'in linux kitabını bulmuştum. Eğitim verirken bilmediğiniz, ya da eksik bildiğiniz şeyler ortaya çıkıyor. Hem de üzerinde uğraştığınız kod örneklerini açık kaynaklı paylaştığınız zaman, herkes sizinle öğrenebiliyor.

<a href="http://www.laravel.io/bin">http://www.laravel.io/bin</a> sitesi kodlarınızı düzgünce paylaşmanızı sağlar. Ekran resminden eciş bücüş okumak yerine, diğer insanlar daha rahat okurlar kodlarınızı.

Biraz daha üst düzey bi konu ama github öğrenin derim. <a href="http://meraklibilisimci.com/2012/10/13/acik-kaynak-yazilimcisinin-yapmasi-gereken-ilk-sey-github-kurulumu/">http://meraklibilisimci.com/2012/10/13/acik-kaynak-yazilimcisinin-yapmasi-gereken-ilk-sey-github-kurulumu/</a>
<h2>4. Boşluk bırakın ve yorum yapın</h2>
Hangisinin okunması daha kolay? Bu mu?

[code language="php"]
&lt;?php
$ogrenciler = array('Mahir', 'Deniz', 'Yusuf', 'Hüseyin', 'Cevahir', 'Sinan', 'Erdal', 'Ulaş');
$ogrenciSayisi = sizeof($ogrenciler);

if($ogrenciSayisi &lt;= 10)
{
for($i=0;$i&lt;$ogrenciSayisi;$i = $i+1)
{
echo $ogrenciler[$i].&quot;&lt;br/&gt;&quot;;
}
}
else
{
echo &quot;Ogrencilerin sayisi 10'dan büyüktür.&quot;;
}

?&gt;
[/code]

<strong>Yoksa bu mu?</strong>

[code language="php"]
&lt;?php
/**
*                    Merakli Bilişimci
*                   meraklibilisimci.com
**/
// Bu örnekte koşula bağlı çalışan ifadeleri ve dizileri anlayacağız.
// Dizi bir çok değişkeni bir arada tutan veri tipidir. Çekmeceye benzetebiliriz.

$ogrenciler = array('Mahir', 'Deniz', 'Yusuf', 'Hüseyin', 'Cevahir', 'Sinan', 'Erdal', 'Ulaş');

$ogrenciSayisi = sizeof($ogrenciler); // Bu default fonksiyon bize dizinin boyutunu verir, PHP'de bunun gibi bir çok default fonksiyonlar vardır. Biz bu eğitim son örneğinde zaman fonksiyonlarını kullanacağız.

if($ogrenciSayisi &lt;= 10)
{
    // For döngüsünde $i adında bir sayaç oluşturduk. Portakalı soydum gibi :)
    // İlk değer sayacın başlangıcını
    // İkinci değer sayacın ulaşacağı değeri
    // Üçüncü değer ise sayacın kaçar kaçar artacağını söyler. Eğer tek tek artırmak istersek $i++ da yazabilirdik.
    // Benzer işlermi yapan while ve do while döngüleri de vardır.
    for($i=0;$i&lt;$ogrenciSayisi;$i = $i+1)
    {
        echo $ogrenciler[$i].&quot;&lt;br/&gt;&quot;;
    }
}
else
{
    echo &quot;Ogrencilerin sayisi 10'dan büyüktür.&quot;;
}

?&gt;
[/code]

Yani kodlarınızda boşluk ve yorumlara dikkat edin, hem başkası anlasın hem de aylar sonra baktığınızda kendiniz anlayın. Bir de $tur $cur diye değişken ismi olmaz arkadaşlar. Düzeltmem için elime gelen proje vardı. Böyle değişkenler yazan arkadaşa baya küfür etmiştim. $degiskenNeIsıYapiyosaOnuUsenmedenYazin Değişken ne işi yapıyosa onu üşenmeden yazın. Bi de bi zahmet değişken isimleri ingilizce olsun. Hakkaten ascii turkcesi çok amatör duruyor kodlarda.
<h2>5. Durmayın</h2>
Ben işlerimi hallediyorum, oldum ben, ne gerek var OOP'ye NYP'ye demeyin. Patlarsınız. Asla tam uzmanlık yok. Bilen biri gelir, sizi işinizden eder. Her zaman yeni şeyler öğrenmeye çalışın, her zaman daha yapabilecek bir sürü şey olduğunu bilin.

Şimdilik bu kadar. Dayanışmayla