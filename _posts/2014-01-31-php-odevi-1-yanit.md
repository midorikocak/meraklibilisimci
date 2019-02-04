---
ID: 458
post_title: 'PHP Ödevi 1 &#8211; Doğum Günü Kutlama &#8211; Yanıt'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/php-odevi-1-yanit/
published: true
post_date: 2014-01-31 14:27:22
---
<p>"birisi" doğru cevabı bilmiş teşekkür ederiz!</p><p><a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/birthday_candles.jpg"><img class="alignnone size-medium wp-image-460" alt="Birthday_candles" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/birthday_candles.jpg?w=300" width="300" height="110" /></a></p><p>İlk olarak doğum günü kutlaması yapabilmemiz için dizi oluşturmamız gerekiyor. Bunu iki şekilde yapabiliriz. İç içe diziler kullanarak:</p><pre>&lt;?php
$arkadaslarim = array(
    array('Deniz Gezmiş', '27/2/1947'),
    array('Hüseyin İnan', '01/01/1949'),
    array('Yusuf Aslan','02/01/1947')
);</pre><p>İstersek array içinde özel anahtar da kullanabiliriz:</p><pre>&lt;?php
$arkadaslarim = array(
    array('adi'=&gt;'Deniz Gezmiş', 'dogum-tarihi'=&gt;'27/2/1947'),
    array('adi'=&gt;''Hüseyin İnan', 'dogum-tarihi'=&gt;''01/01/1949'),
    array('adi'=&gt;''Yusuf Aslan','dogum-tarihi'=&gt;''02/01/1947')
);</pre><p>Türkiye'de zaman hesabı yapacağımız için, timezone bilgisini istanbul olarak belirliyoruz.</p><pre>date_default_timezone_set('Europe/Istanbul');</pre><p>Bugünün tarihini alarak bir değişkene atamalıyız ki, arkadaşlarımızın doğum tarihlerini bu değişkenle karşılaştırabilelim</p><pre>$bugun = date('d/m/Y');</pre><p>Son olarak tüm dizi elemanları ile bugünün tarihini karşılaştıracağız ve karşılaştırma tutuyorsa, ekrana doğum günü kutlama mesajı yazdıracağız.</p><pre>foreach ($arkadaslarim as $arkadas)
{
if($arkadas['dogum-tarihi'] == $bugun)
    {
    echo 'Dogum günün kutlu olsun '.$arkadas['adi'];
    }
}</pre><p>Sonuç olarak tüm kodu görmek istersek:</p><pre>&lt;?php
// İlk olarak doğum günü kutlaması yapabilmemiz için dizi oluşturmamız gerekiyor. Bunu iki şekilde yapabiliriz. İç içe diziler kullanarak:
//İstersek array içinde özel anahtar da kullanabiliriz:

$arkadaslarim = array(
array('adi'=&gt;'Deniz Gezmiş', 'dogum-tarihi'=&gt;'27/2/1947'),
array('adi'=&gt;''Hüseyin İnan', 'dogum-tarihi'=&gt;''01/01/1949'),
array('adi'=&gt;''Yusuf Aslan','dogum-tarihi'=&gt;''02/01/1947')
);

//Türkiye'de zaman hesabı yapacağımız için, timezone bilgisini istanbul olarak belirliyoruz.
date_default_timezone_set('Europe/Istanbul');

//Bugünün tarihini alarak bir değişkene atamalıyız ki, arkadaşlarımızın doğum tarihlerini bu değişkenle karşılaştırabilelim

$bugun = date('d/m/Y');
//Son olarak tüm dizi elemanları ile bugünün tarihini karşılaştıracağız ve karşılaştırma tutuyorsa, ekrana doğum günü kutlama mesajı yazdıracağız.

foreach ($arkadaslarim as $arkadas)
{
if($arkadas['dogum-tarihi'] == $bugun)
{
echo 'Dogum günün kutlu olsun '.$arkadas['adi'];
}
}
?&gt;</pre><p>Şimdilik bu kadar. Php öntanımlı birçok farklı fonksiyon da mevcuttur. Bunları detaylı incelemenizi öneririm.</p><p>Bir sonraki ödeve kadar görüşmek üzere...</p>