---
ID: 146
post_title: >
  Açık kaynak yazılımcısının
  yapması gereken ilk şey (Github
  kurulumu)
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/acik-kaynak-yazilimcisinin-yapmasi-gereken-ilk-sey-github-kurulumu/
published: true
post_date: 2012-10-13 16:23:12
---
<a href="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/image7-53.jpeg"><img class="size-full wp-image-55 alignright" title="Github" src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/image7-53.jpeg" alt="" width="300" height="450" /></a>

Yazılım geliştirme işine meraklıysak hiçbirşey öğrenmeden önce yapmamız gereken bir tek şey var. O da git öğrenmek. Peki git nedir?

Git bir versiyon kontrol aracıdır. Ne demek peki versiyon kontrolü? Ve onunla ne yapabilirz?

Örneğin bir projemiz var. Değişik dosyalar üzerinde sürekli değişiklikler yapıyoruz. Bir yerden sonra yaptığımız değişikliğin hatalı olduğunu farkedersek ne yapacağız? Text editörü veya IDE'de geri al tuşuna basmak bir yere kadar.

Ya da yanlışlıkla bir dosyayı sildiysek onu nasıl geri getirebiliriz?

Veya birden çok kişinin üzerinde değişiklik yaptığı bir klasörde kimin neyi değiştirdiğiniz görmek istersek?

İşte bunların hepsinin çözümünü git sağlıyor. Git açık kaynaklı bir versiyon kontrolü yazılımıdır. Github ise, git ile versiyon kontrolü yaptığımız paketlerimizi, açık kaynaklı ise bedava, kapalı kaynaklı ise aylık cüzi bir miktara hem barınmasını hem de bir çok geliştirici tarafından aynı anda geliştirilirken yönetilmesini sağlıyor.

Ha ben tek başına yapıyorum herşeyi derseniz bile, github ve git kullanımı yukarıda saydığım gerekçelerden dolayı çok önemli.

Peki Git ve Github'a nasıl başlayacağız. Öncelikle gerekli programları şu adreslerden indirip kuralım: (Eğer burada kurumla ilgli spesifik bir sorunuz olursa lütfen yorum yapın.) Ben mac kullanıdğım için direk mac versiyonunu indirmemi tavsiye ediyor site. Sizde de işletim sisteminize göre uygun sürümü söyleyecektir.

Önce <a href="http://git-scm.com/downloads">http://git-scm.com/downloads</a> adresinden Git'i indirip kuralım:

<a href="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.46.13-PM.png"><img class="aligncenter size-large wp-image-34" title="Git yükleme" src="https://www.meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.46.13-PM.png?w=1024" alt="" width="1024" height="471" /></a>

Sonra github üyelğimiz yoksa <a href="https://github.com/signup/free">https://github.com/signup/free</a> adresinden ücretsiz üyelik edinelim. Dediğim gibi açık kaynaklı yazılımlar için github hizmeti tamamen ücretsiz. Daha sonra eğer kendi projeleriniz olursa, bunlar için farklı ücretli paketler de var, ama şimdilik bizim buna ihtiyacımız yok.

<a href="https://github.com/signup/free"><img class="aligncenter size-full wp-image-35" title="Screen Shot 2012-10-13 at 6.49.03 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.49.03-PM.png" alt="" width="628" height="387" /></a>

Üye olduktan sonra karşımıza şöyle bir sayfa gelecek:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.52.07-PM.png"><img class="aligncenter size-full wp-image-36" title="Screen Shot 2012-10-13 at 6.52.07 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13 at-6.52.07-PM.png" alt="" width="628" height="374" /></a>

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.53.16-PM.png"><img class="alignleft" title="Screen Shot 2012-10-13 at 6.53.16 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.53.16-PM.png" alt="" width="232" height="234" /></a>Buradan <a href="https://help.github.com/articles/set-up-git">Set Up Git</a> linkini tıklayalım. Karşımıza gelecek olan sayfadan turuncu Download GitHub for Mac veya Download GitHub for Windows'u tıklayarak bu yazılımı da bilgisayarımıza indirip kuralım. Dediğim gibi şu anda bende mac olduğu için çok fazla yükleme sorunu yaşamadım, direk ileri ileri ileri düye yükledim. Ama mesela windows kullanan arkadaşların yükleme ile ilgili soruları olursa buraya yorum yaparlarsa yanıtlarım.
İndirme linkinin olduğu sayfa da bu şekilde:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.53.09-PM.png"><img class="alignleft size-full wp-image-38" title="Screen Shot 2012-10-13 at 6.53.09 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-6.53.09-PM.png" alt="" width="628" height="478" /></a>Programı kurduk ve yükledik ama bitti mi? Hayır. Bilgisayarımızla github hesabımızın anlaşması için bir güvenlik anahtarı oluşturmamız gerekiyor. Bunun için windows kullanan arkadaşların Git-Bash programını, Linux ya da Mac kullanan arkadaşların ise terminal programını çalıştırmaları gerekiyor. İngilizce olarak bu güvenlik anahtarının oluşturulma işlemini <a href="https://help.github.com/articles/generating-ssh-keys">şu sayfa</a> anlatıyor. Ama ben yine de burada anlatacağım.

Öncelikle Git-Bash veya terminalde şu komutları çalıştıralım.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.25-PM.png"><img class="alignleft size-full wp-image-40" title="Screen Shot 2012-10-13 at 7.02.25 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.25-PM.png" alt="" width="628" height="66" /></a>

Burada daha önceden oluşturulmuş güvenlik anahtarı var mı yok mu kontrol ediyoruz. Eğer varsa yeni bir klasör yaratıp onları yedekleyeceğiz. Daha sonra silip yeni güvenlik anahtarımızı oluşturacağız.

Sırayla aşağıdaki komutları girelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.31-PM.png"><img class="alignleft size-full wp-image-41" title="Screen Shot 2012-10-13 at 7.02.31 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.31-PM.png" alt="" width="628" height="237" /></a>

Daha sonra your_email@youremail.com yazan yere github hesabı alırken kullandığımız e-posta adreslerini çift tırnaklarla beraber yazarak komutu çalıştıralım ve yeni güvenlik anahtarımızı oluşturalım.<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.37-PM.png"><img class="alignleft size-full wp-image-42" title="Screen Shot 2012-10-13 at 7.02.37 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.37-PM.png" alt="" width="628" height="102" /></a>

Bizden bir şifre isteyecek, daha sonra hatırlayacağımız bir şifre yazalım.
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.41-PM.png"><img title="Screen Shot 2012-10-13 at 7.02.41 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.41-PM.png" alt="" width="628" height="69" /></a>

Eğer herşey yolunda gittiyse karşımıza şöyle bir yazı çıkacak:<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.41-PM.png">
</a>

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.50-PM.png"><img class="alignleft size-full wp-image-44" title="Screen Shot 2012-10-13 at 7.02.50 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.50-PM.png" alt="" width="628" height="103" /></a>

Şimdi id_rsa.pub dosyasının içindekileri panoya kopyalamamız gerekiyor. Bunu Git-bash veya terminal altında şu şekilde yapabiliriz:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.55-PM.png"><img class="alignleft size-full wp-image-45" title="Screen Shot 2012-10-13 at 7.02.55 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.02.55-PM.png" alt="" width="628" height="66" /></a>

Ya da basitçe herhangi bir metin editörü yardımıyla id_rsa.pub doyasını açıp içindekileri panoya kopyalayın.

Daha sonra ana sayfada üst köşede bulunan: <a href="https://github.com/settings/profile">Account Settings</a> bölümüne tıklayalım.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/userbar-account-settings.png"><img class="size-full wp-image-46 alignnone" title="userbar-account-settings" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/userbar-account-settings.png" alt="" width="222" height="127" /></a>

Buraya tıkladıktan sonra karşımıza gelen ekrandan <a href="https://github.com/settings/ssh">SSH Keys</a> linkini tıklayalım.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/settings-sidebar-ssh-keys.png"><img class="alignnone size-full wp-image-47" title="settings-sidebar-ssh-keys" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/settings-sidebar-ssh-keys.png" alt="" width="281" height="155" /></a>

Daha sonra karşımıza gelen sayfada, sağ üstteki Add SSH Key linkine tıklayalım. <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ssh-add-ssh-key.png"><img class="alignnone size-full wp-image-48" title="ssh-add-ssh-key" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ssh-add-ssh-key.png" alt="" width="628" height="105" /></a>

Bu linke tıkladığımızda karşımıza şöyle bir form çıkacak, bu forma kopyaladığımız id_rsa.pub içindeki güvenlik anahtarımızı yapıştıralım ve kaydedelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ssh-key-paste.png"><img class="alignnone size-full wp-image-49" title="ssh-key-paste" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ssh-key-paste.png" alt="" width="628" height="367" /></a>

Add Key linkine tıklayarak kaydedelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/ssh-add-key.png"><img title="ssh-add-key" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/ssh-add-key.png" alt="" width="140" height="97" /></a>

Tebrikler, github artık bilgisayarınızı tanıyor ve bilgisayarınızdan paketlerinizi yönetebilir ve istediğiniz değişiklikleri yapabilirsiniz. Herşeyi kontrol etmek için terminal veya Git-bash ekranına geri dönüp, şunları yazalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.03.33-PM.png"><img class="alignnone size-full wp-image-51" title="Screen Shot 2012-10-13 at 7.03.33 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.03.33-PM.png" alt="" width="628" height="66" /></a>

Eğer herşey yolunda gittiyse karşımıza şöyle bir yazı çıkacak:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.03.37-PM.png"><img class="alignnone size-full wp-image-52" title="Screen Shot 2012-10-13 at 7.03.37 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.03.37-PM.png" alt="" width="628" height="80" /></a>

Hiçbir sorun yok, devamında da şöyle birşey çıkması lazım. Tabi username yerine sizin GitHub kullanıcı adınız yazacak:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.03.41-PM.png"><img class="alignnone size-full wp-image-53" title="Screen Shot 2012-10-13 at 7.03.41 PM" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-7.03.41-PM.png" alt="" width="628" height="62" /></a>

Tebrikler. Açık kaynak yazılımcısının yapması gereken ilk şeyi yaptınız. Github'u kurdunuz ve bilgisayarınızla bağlantıya geçirdiniz.

Bir sonraki yazıda da yeni paket oluşturmayı anlatacağım. Tabi sabredebilirseniz.

Dayanışmayla!

Meraklı Bilişimci