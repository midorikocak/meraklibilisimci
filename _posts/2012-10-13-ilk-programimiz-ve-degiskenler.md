---
ID: 149
post_title: İlk Programımız ve Değişkenler
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/ilk-programimiz-ve-degiskenler/
published: true
post_date: 2012-10-13 22:48:53
---
Önecelikle PHP'nin sistemimizde çalışıp çalışmadığını anlamamız gerekiyor. Bunun için Xampp'i daha önce belirttiğimiz şekilde çalıştırdıktan sonra, C:\Xampp\htdocs altında info.php isminde bir dosya oluşturalım. Dosyayı herhangi bir tex editör veya ide yardımıyla açalım ve içine:
<pre>&lt;?
phpinfo();
?&gt;</pre>
yazalım ve kaydedelim. Daha sonra tarayıcımızdan http://127.0.0.1/info.php linkini çağıralım. Karşımıza şöyle bir sayfa geldiyse, bilgisayarımızda apache sunucusu ve php çalışıyor demektir.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-1.23.48-AM.png"><img class="alignnone size-full wp-image-115" title="Screen Shot 2012-10-14 at 1.23.48 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-1.23.48-AM.png" height="347" width="628" /></a>

İlk konumuz <strong>Değişkenler</strong>. Eğer bir programlama dili biliyorsanız bunlara aşinasınızdır ama bilmiyorsanız hiç sorun değil, çok kolay. Programlama dillerinde değişken diye bir olay var. İlk öğrenmemiz gereken kavram bu. <strong>Değişken</strong> benim hafızamda açtığım bir <strong>çekmece</strong> gibi birşey. Yani ben şehir, isim veya soyad adlı bir değişken oluşturabilirim, ve bunlara istediğim değerleri verebilirim. Mesela şehir, istanbul; isim, deniz; soyad da inan değerlerini alabilirler. Ve ürettiğim bu değişkenleri de istediğim şekilde kullanırım istersem de şu şekilde ekrana yazdırabilirim.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.28-PM.png"><img class="alignnone size-full wp-image-116" title="Screen Shot 2012-10-13 at 10.04.28 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.28-PM.png" height="114" width="315" /></a>

Şimdi burada bilmemiz gereken bir olay var. Not defteri, TextMate, Notepad++ veya herhangi bir ide yazdığımız tüm php dosyalarının uzantıları .php olmak zorunda. PHP yorumlayıcısının bu dosyaları php olarak tanıması için bu gereklidir. (Eğer başka dosyaları da sunucuya php olarak tanıtmak isterseniz bunun da yöntemleri var.)

PHP script dili olduğundan, PHP yorumlayıcısı, bizim yazdığımız kodları satır satır okur ve sırayla verdiğimiz komutları çalıştırır. (Script dilinin tanımı da tam olarak bu, bu arada :)

PHP yorumlayıcısı <strong>&lt;?</strong> veya <strong>&lt;?php</strong> karakterlerini ardarda gördüğü anda dosyayı okumaya başlar. <strong>?&gt;</strong> karakterlerine ulaştığı anda da komutları uygulamayı geçer ve dosyanın kalanını görmezden gelir. Ayrıca PHP yorumlayıcısı, kod içinde <strong>//, #</strong> ile başlayan, veya <strong>/* ve */</strong> karakterleri arasındaki satırların da yorum olduğunu düşünür. Kodlarımızın okunaklı, anlaşılabilir olmasını istiyorsak, bu yorum olayına da çok dikkat etmemiz gerekiyor arkadaşlar. Yazdığımız PHP kodunun dışındaki alana istersek html, istersek de javascript kodu da yazabilirz. PHP öylesine kullanışlı bir dildir ki, isterseniz PDF üretip bu PDF dosyası üzerinde Javascript dahi çalıştırabilirsiniz. (PDF nedir diye soran varsa: Adobe programının ürettiği doküman formatıdır.)

Şimdi ilk örneğimize bakalım. Daha önce örneklerimizi htdocs altında mtkocakPhpEgitimi klasörüne kaydetmiştik. Buradaki 1-merhaba.php dosyasını açalım ve inceleyelim.

Dosyanın ilk satırlarında karşımıza şu şekilde bir kod çıkacak:
<pre>&lt;?php

// PHP Derleyicisine Programın başladığını bildirir.
// Değişik türleri de vardır. 

/**  
*                    Merakli Bilişimci
*                   meraklibilisimci.com
*   
**/

//Örnek 1 - Merhaba Dünya

// Yorumlar istenirse bu şekilde girilirse PHP derleyicisi tarafından okunmazlar.

/*

    Ya da bu şekilde girilirse PHP  Derleyicisi tarafından okunmazlar

*/</pre>
Burada önceden belirttiğimiz gibi yorumların nasıl yapıldığını görüyoruz.

Bütün değişkenler dolar işaretiyle başlıyor. Değişkenlerin isimlerinde türkçe karakter kullanmıyoruz. Değişkeni oluşturan kelimeler kısaltılmadan yazılıyor ve ilki dışında hepsi birleşik ve büyük harfle başlıyorlar. $enSevdigimDegisken gibi. Böylelikle hangi değişkenin ne işe yaradığını unutmuyoruz.

Örneğimizi incelemeye devam edelim:
<pre>$degisken ="Merhaba Dayanışma!"; // Bu bir değişkendir. Bellekte geçici olarak veri tutar. Program çalışıp bittiğinde hafızadan temizlenir. 

echo $degisken; // echo komutu değişkenin program tarafından ekrana yansıtılmasına yarar.

// PHP derleyicisine programın bittiğini bildirir
// Eğer karakterler bozuk görünüyorsa, browserin encoding ayarı UTF8'e çevirilecek
// Bunu daha sonra html kodlarıyla ayarlayacağız.

?&gt;</pre>
Gördüğümüz gibi yeni bir değişken tanımladık. Ve onu echo komutuyla ekrana yansıttık. Bu echo da neyin nesi diye soracak olan arkadaşlar için şöyle bir ek bilgi vereyim, PHP bir scripting dili olduğundan, eski bir unix komutu olan echo komutunu da almış. Echo ingilizce yankı demek. Bir herhangi bir terminal ekranına echo ile komut verdiğimizde echo, içindeki değeri aynen ekrana yansıtıyor. Burada biz değer verdiğimiz değişkeni echo ettiğimiz için de, echo programı değişkenin değerini ekrana yansıtmış oluyor aslında.

Bir diğer yazma yöntemi ve benim çok sıkıntı yaşadığım okunurluk problemi de indentasyon adını verdiğimiz tab kullanımı. Özellikle koşula bağlı veya fonksiyon içinde bulunan farklı bir kod grubu varsa bunları her zaman ekstra softtab (Yani ardarda 4 adet boşluk) ile satır başından ileride yazmak okunuruluğu kolaylaştırır, işe alınmanızı rahatlatır ve proje müdürüyle daha az kavga etmenizi sağlar. Aynen paragraflara başlamak gibi. Aşağıda örnek kodu görüyorsunuz, indentasyonlu ve indentasyonsuz. Birinin okunurluğu çok berbatken, diğerininki ise çok iyi. TextMate, Notepad++ veya diğer Ide'lerde bu indentasyon genellikle bir tıkla otomatik olarak yapılabiliyor.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-1.47.40-AM.png"><img class="size-full wp-image-121 alignright" title="Screen Shot 2012-10-14 at 1.47.40 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-1.47.40-AM.png" height="304" width="305" /></a>

Özellikle değişken isimlerinde kısaltma yapmaktan da kaçınalım arkadaşlar. Yazdığımız kodu başkası anlamasın istiyorsak o başka. Bir projede $mid, $tur, $cur gibi değişkenler yüzünden eski geliştiricinin kulaklarını bayağı çınlatmıştım. Üstelik eğer birşeyleri nasıl yaptığınızı unutur da eski kodlarınıza bakmak isterseniz de bu yöntem size çok yardımcı olacak.

Örneğin C++ dilinde kaynak kodu derlendikten sonra ortadan kaybolduğu için, kapalı kaynak kodlu yazılımlar için bir tercih sebebidir. PHP kodları eğer projeniz kendi sunucunuzda çalışacak ve servisi kiralayacaksanız açık olmasında bir sakınca olmamakla beraber, başkası için yazdığınız ve sadece kapora aldığınız programınız hain ellere geçmesin istiyorsanız bilmeniz gereken birşeyler var. PHP derlenmeden çalıştığı, (yani kaynak koduna çevrilmeden, yorumlayıcı tarafından komutları sırayla çağırılan bir script dili olduğu ) için kodlarımız anlaşılmasın istiyorsak da, bu işi piyasada yapan bir çok araç mevcut. (Bunları araştırmayı da size bırakıyorum.)

Yazdığımız programcığı çağırmak istediğimizde, eğer XAMPP açıksa ve Apache web sunucusu çalışıyorsa, tarayıcının adres çubuğuna kendi bilgisayarımızın IP adresi olan 127.0.0.1, ya da http://localhost/ yazdığımızda bilgisayarımızdaki sunucunun ana sayfasına ulaşırız. Mesela ilk örneğimizi çağırmak için 127.0.0.1/mtkocakPhpEgitimi/1-merhaba.php ya da http://localhost/mtkocakPhpEgitimi/1-merhaba.php yazarsak programımızı çalıştırmış oluruz. Programımızı çalıştırdığımız zaman karşımıza şöyle bir görüntü gelecek.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-1.44.16-AM.png"><img title="Screen Shot 2012-10-14 at 1.44.16 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-1.44.16-AM.png" height="190" width="440" /></a>

İlk örnek çok kolay, bir değişken adı belirledik, değişkene değer atadık, değişkenin değerini ekrana bastık. Bu klasik her programlama diline başlarken yazılan "Merhaba Dünya!" programı. Programımız dünyaya geldiği için, yani doğduğu için, dünyaya merhaba diyor :)

Eğer çıkan karakterler bozuk görünüyorsa, html kodlarını kullanarak, karakter kodlamasını UTF8'e çevirmediğimiz için tarayıcı türkçe karakterleri tanımayabilir. Tarayıcının varsayılan karakter kodlaması ayarını UTF8'e çevirebiliriz. Daha sonra html kodları yazmaya başladığımız zaman, bu karakter kodlamasını tarayıcıya tanıtan html kodunu kullanırsak, kodlama sorunu yaşamayız. Örneğin posta kutunuza düşen bazı html maillerinin karakterlerinin bozuk gözükmesinin sebebi de tamamen budur.

Bu konuyu daha sonra php kodlarımız içinde html kodları kullanmaya başladığımız zaman çözeceğiz.

İşte şimdi Php'de değişken mantığını anladık ve ilk programımızı yazmış olduk. Devamında yazı ve sayı tipleri konusunu inceleyeceğiz.

Şimdilik bu kadar.

Dayanışmayla!
Meraklı Bilişimci