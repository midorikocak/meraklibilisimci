---
ID: 390
post_title: >
  FTP ile internet sitesi yayınlama ve
  Son sözler
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/ftp-ile-internet-sitesi-yayinlama-ve-son-sozler/
published: true
post_date: 2012-10-25 13:52:19
---
<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/filezilla.png"><img class="size-medium wp-image-391 alignnone" title="filezilla" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/filezilla.png?w=300" height="300" width="300" /></a>Sitemizi hazırladık. Tüm dosyalarımız hazır. Şimdi sıra geldi FTP istemcisi kullanarak bu dosyaları sunucuya yüklemeye. Eğer web sitenizi internette yayınlamak istiyorsanız öncelikle size bir hosting yani barındırma hizmeti lazım. Bunun için hosting firmalarından hizmet alabilirsiniz. Ben genellikle Mediatemple kullanıyorum. Yerli firmaları tercih etmedim ama yerli ve bu işi iyi yapan büyük ve kurumsal firmalar da var. Size tavsiyem sorun yaşamak istemiyorsanız, sunucu hizmeti veren şirketin referanslarına bakmanız. Bu işlerde fiyat sizin için avantaj olmasın. Sonra binbir emekle yaptığınız internet sitesinin dosyaları veya veritabanı oratadan kayboldursa, binlerce dolarlık zararın telafisi mümkün olmaz ve bir özür alırsınız. Biz PHP ile geliştirme yapacağımız için Linux sunucu almamız gerekiyor. Sunucumuzu satın aldıktan sonra 3 tane bilgiye ihtiyacımız olacak.
<ol>
	<li><strong>Sunucu adresi:</strong> Sunucumuza ftp istemcisi kullanarak erişmemizi sağlayacak adres.</li>
	<li><strong>Kullanıcı adı: </strong>Sunucu üzerinde ftp ile oturum açmamıza yaran kullanıcı ismi.</li>
	<li><strong>Kullanıcı şifresi: </strong>Oturum açarken kullanacağımız parola.</li>
</ol>
Bunlar sunucunuz için en önemli bilgiler. Size tavsiyem bu bilgileri gizli tutmanız ve şirfre belirlerken karakter, büyük harf ve sayı kullanmalı 10 haneden uzun bir şifre seçmenizdir. E-posta şifrenizde de aynı şeyi uygulayın. <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/fz3_osx_main-small.png"><img class="size-full wp-image-394 alignnone" title="fz3_osx_main-small" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/fz3_osx_main-small.png" height="259" width="300" /></a> Daha sonra bir ftp istemci programına ihtiyacımız var. Piyasada başka programlar da var ama bu konuda endüstri standardı FileZilla diyebiliriz. Hem açık kaynaklı, hem de ücretsiz, üstelik Türkçe. http://filezilla-project.org/download.php adresinden işletim sistemimize uygun sürümü indirdikten sonra programı açalım. Adres, kullanıcı adı ve parola bilgilerimizi girelim: <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.32.53-PM.png"><img class="alignnone size-full wp-image-395" title="Screen Shot 2012-10-25 at 4.32.53 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.32.53-PM.png" height="388" width="628" /></a> Hızlı bağlan ya da quickconnect tuşuna tıklayalım. Hata yoksa "Response: 230 User kullaniciadi logged in" gibi bir cevap alacaksınız ve kendi dizinlerinizin karşısında sunucunun dizinleri çıkacak. <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.33.33-PM.png"><img class="alignnone size-full wp-image-396" title="Screen Shot 2012-10-25 at 4.33.33 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.33.33-PM.png" height="371" width="275" /></a> Bu dizinlerden httpdocs genellikle yayında olan internet sayfalarını barındırır. Buraya hazırladığımız dosyaları istersek sağ tıklayıp, istersek sürükleyip bırakarak, istersek de çift tıklayara göndereceğiz. <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.34.49-PM.png"><img class="alignnone size-full wp-image-397" title="Screen Shot 2012-10-25 at 4.34.49 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.34.49-PM.png" height="362" width="628" /></a>Dosyalar düzgün bir şekilde gittiyse üst tarafta şöyle yazılar çıkması lazım:
<pre><code>
Status:	Starting upload of 
/html5css3egitim/urunler.html
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (216,70,99,60,185,211).
Command:	STOR urunler.html
Response:	150 Opening ASCII mode data connection for urunler.html
Response:	226 Transfer complete
Status:	File transfer successful, transferred 8,456 bytes in 1 second
Status:	Retrieving directory listing...
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (216,70,99,60,204,206).
Command:	MLSD
Response:	150 Opening ASCII mode data connection for MLSD
Response:	226 Transfer complete
Status:	Directory listing successful
</code></pre>
Bazen hata da olabilir ki bu gayet doğal ve muhtemel. Bu sizin moralinizi bozmasın. Genellikle hatalar firewall ayarlarından, sunucunun veya ağın durumundan, hatalı yapılandırmadan veya yanlış port adresinden ortaya çıkabilir. Bununla ilgili aldığınız hatanın kodunu internette araştırırsanız sorunu çözersiniz, çünkü o hatanın başına geldiği kişi -iyi ki de- sadece siz değilsiniz. Sitemizi sunucuya gönderdikten sonra kontrol etmemiz gerekiyor. Bir internet tarayıcısında adres çubuğuna http://www.adresiniz.com/ yazdığınızda karşınıza düzgün bir şekilde sayfa geliyorsa, başardınız demektir. Burada ben <a href="http://www.mtkocak.net/kizilyildiz">http://www.mtkocak.net/kizilyildiz</a> adresine yükleme yaptım. Adrese girdiğimde karşıma çıkan görüntü şu şekilde: <a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.44.15-PM.png"><img class="alignnone size-full wp-image-398" title="Screen Shot 2012-10-25 at 4.44.15 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-25-at-4.44.15-PM.png" height="389" width="628" /></a> Tebrikler. Artık HTML5 ve CSS3 ile ilgili teknolojileri biliyorsunuz. Profesyonel bir şekilde bir internet sayfası nasıl hazırlanır, en modern teknikleriyle öğrendiniz. Peki öğreneceklerimiz bitti mi? Hayır tabii ki. Daha sonraki bölümlerde JavaScript, jQuery, jQuery UI, jQuery Mobile, Veritabanları, XML, PHP gibi nefis ve birbirinden zevkli konularla devam edeceğiz. Sizden ricam kodları açıp kurcalamanız, orasını burasını değiştirip bozmanız ve anlamaya çalışmanız. En iyi öğrenme yöntemi yapmaktır. Öğrenmeye olan heves ve heyecanınız kaybolmasın. Kimsenin de bu hevesinizi kurmasına izin vermeyin. Kimsenin bir konuyu %100 oranında bilmesi mümkün değil. Bir de kibirli olmayın ve kibirli, çok bilmiş insanlardan uzak durun. Sizi geriletir ve yavaşlatırlar çünkü. Yaptıkça özgüveninizin arttığını göreceksiniz. Bir de kimseye referans olsun diye ucuza veya <strong>bedavaya site yapmayın</strong>. Sizin öğrendiğiniz bu teknikle yapacağınız 5 sayfalık internet sitesinin fiyatı 2012 ekim ayı itibariyle en azından 750 - 1000 TL olmalı. Pahalı mı? Hayır. Çünkü kalite olarak farklı. Tofaş ile Mercedesin ikisi de otomobil ama Mercedes 4 katı daha pahalı. En yeni teknolojiyi kullandınız. Öğrenmek için emek harcadınız. Bu emeğin karşılığını da talep etmek en doğal hakkınız. Piyasada 80 TL'ye iş yapan kişiler de var. Müşteri eğer onları örnek gösteriyorsa, bırakın gitsin onlara yaptırsın. Çünkü sizin azminiz, öğrenme isteğiniz hakkının karşılığını almayı hakediyor her zaman. Dayanışmayla! Meraklı Bilişimci