---
ID: 73
post_title: >
  İnternet Programlamaya Giriş Yapalım
  (php nedir? xampp kurulumu)
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/internet-programlamaya-giris-yapalim-php-nedir-xampp-kurulumu/
published: true
post_date: 2012-10-13 18:34:25
---
<pre>Asla bedavaya internet sitesi yapmayın.</pre>
Kendi facebook'unuzu yazmak istemez miydiniz? Ya da internette çalışan programlar yapmak? İşte <a href="http://www.bilisimcalisanlari.net">BİÇDA</a> olarak bu eğitimi verdik. Şimdi de bu eğitimin notlarını sunuyorum sizlere:

Öncelikle internet uygulamaları yapmamız için bilmemiz gereken birkaç şey var. Bir <strong>KULLANICI </strong>internet tarayıcısına bizim sunucumuzun adresini girecek. Burada sunucu adresi örneğin <strong><a href="http://www.facebook.com/index.php">http://www.facebook.com/index.php</a> </strong>Burada taksim işaretine kadar olan kısım, sunucumuzun domain name'i ya da özel ismi. index.php ise sunucu üzerinde bizim php ile yazdığımız programlama dosyası.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-9.18.22-PM.png"><img class="alignnone size-full wp-image-74" title="Screen Shot 2012-10-13 at 9.18.22 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-9.18.22-PM.png" height="280" width="385" /></a>

Peki nedir bu PHP?

PHP bir script dilidir. Script dilleri C++ veya C gibi derlenerek makine koduna dönüştürülmezler. Derleyicileri(Compiler) yoktur. Bunun yerine, yazılan kaynak kodunu satır satır okuyarak girilen komutları işleyen bir yorumlayıcıya sahiptirler. Yorumlayıcı her satır için ayrı kaynak kodu üreterek bilgisayara komut verir. Bu metod bize kodlarımıza daha hızlı müdahele edebilme, daha kolay çalıştırma (derleme zamanı için beklemek yoktur.), kodu daha kolay dağıtma şansı verir. Yüksek seviyeli bir programlama dili olması bakımından, okuması ve öğrenmesi de görece zor değildir.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/imgres-1.jpeg"><img class="alignnone size-medium wp-image-17" title="PHP" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/imgres-1.jpeg?w=300" height="157" width="300" /></a>

Bu yazı serisini sadece bir PHP veya teknik kodlama makaleleri olarak düşünmeyin. Bu seri aslında hayallerimizi gerçekleştirmemizde yardımcı olacak bir araç. Bilgisayar Mühendisi olmanıza da gerek yok. Örneğin bir iş yaptırmak isteyen bir yöneticiyseniz, bu makalelerdeki bilgiler sizin o işin nasıl doğru bir şekilde yapılacağını bilmenizi sağlayacaktır. PHP internet programlamada kullandığımız güçlü araçlardan birisi. Örneğin sayfamızda dinamik bir veri göstermek istiyorsak... PHP Jquery Ajax CSS3, HTML5 gibi teknolojilere yeri geldikçe değinecek ve ihtiyacımız oldukça kullanacağız.

Bilgisayarımızda kolayca php ve mysql gibi ayrıntısına daha sonra gireceğimiz teknolojileri kullanmamız için önce Xampp'i indirip kurmamız gerekiyor. Kurulumu çok basit. Next, Next, Next.

<img class="alignright" title="Screen Shot 2012-10-13 at 9.22.32 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-9.22.32-PM.png?w=300" height="287" width="300" />

PHP, Apache, MySQL vs. tek başına da kurulabilir, ancak şu an için en kolay ve kodlamaya en çabuk başlayabileceğimiz araç budur. Sonuçta daha ileri seviyelerde ihtiyacınız olacak ek özellikler için bu işlemleri yapmayı gösteren bir çok kaynak mevcut. Ancak bizim amacımız uygulayarak öğrenmek olduğu için bazı detayları size bırakmayı daha uygun görüyorum. Üstelik örneğin her kitapta anlatılan ve her yerde karşımıza çıkan dil yapılarını sırayla anlatmak yerine, örneklerde karşımıza çıktıkları anda anlatmayı daha uygun buldum.

Öncelikle örnek dosyalarımızın bulunduğu

<a href="https://github.com/mtkocak/mtkocakPhpEgitimi/zipball/master">https://github.com/mtkocak/mtkocakPhpEgitimi/zipball/master </a>

doyasını internetten indirelim.

Xampp'ın içinde htdocs diye bir klasör vardır. Bu web sayfaları orda bulunur. Xampp'i yükledikten sonra C:/ dizininin altında XAMPP diye bir klasör oluşur. Bu klasörün altında htdocs olması lazım. Htdocs'un altına indirdiğimiz mtkocakPhpEgitimi1.zip dosyasını açıp koymamız gerekiyor.
<pre>C:/Xampp/htdocs/</pre>
Bunun altına zip dosyasını açıyoruz.

Xampp kontrol paneli çalıştıralım. Windows'ta şu şekilde görünmesi lazım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/4103.jpeg"><img class="alignnone size-full wp-image-76" title="4103" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/4103.jpeg" height="352" width="446" /></a>

Şimdilik Apache'ye start diyelim ve web sunucusunu başlatalım.

Dikkat Apache başlamıyorsa ya da hata veriyorsa, büyük bir ihtimalle Skype veya başka bir mesajlaşma programı açıktır. Kapatalım. Apache web sunucusu bilgisayarımızın 80 numaralı portunu yani kapısını kullanır. Eğer bu port önceden başka bir program tarafından işgal edildiyse, Apache başlamaz hata verir.

Apache bir web sunucusu. Xampp ile birlikte PHP, mysql, apache web sunucusu gibi bir çok teknoloji de hızlıca kuruluyor. Daha sonra bir tarayıcı penceresi açıyoruz.

Xampp çalışıyorsa http://localhost/ veya 127.0.0.1 IP adresinden kendi bilgisayarımızda bulunan, tarayıcıya 80 nolu porttan yanıt veren web sunucumuzun adresine gidiyoruz. Her şey sorunsuz ise, Xampp'ın hoşgeldiniz ekranı karşımıza çıkacak.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-9.31.35-PM.png"><img class="alignnone size-full wp-image-77" title="Screen Shot 2012-10-13 at 9.31.35 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-9.31.35-PM.png" height="522" width="580" /></a>

Şimdilik bu kadar. Daha sonra eğitim dosyalarımızı tek tek inceleyeceğiz. İsterseniz siz de açıp kurcalamaya başlayabilirsiniz. Eğer zip dosyasını doğru bir şekilde çıkardıysanız tarayıcınızdan <a href="http://127.0.0.1/mtkocakPhpEgitimi/">http://127.0.0.1/mtkocakPhpEgitimi/ </a>adresini açın.

Dayanışmayla!
Meraklı Bilişimci