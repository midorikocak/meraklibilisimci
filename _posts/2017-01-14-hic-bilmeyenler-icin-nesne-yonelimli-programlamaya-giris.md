---
ID: 111
post_title: >
  Hiç Bilmeyenler İçin Nesne Yönelimli
  Programlamaya Giriş
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/hic-bilmeyenler-icin-nesne-yonelimli-programlamaya-giris/
published: true
post_date: 2017-01-14 10:47:55
---


<p><strong>Uyarı:</strong> Bu serideki kod örnekleri ve yazılar, seri tamamlanana kadar değişebilmektedir.</p>
<p>Nesne Yönelimli Programlama’yı duydunuz. Kendinizi geliştirmek için öğrenmek zorunda olduğunuzu öğrendiniz. Ancak nereden başlamak gerektiğini bilmiyorsunuz. Bi kaç kitap açtınız, kafanız karıştı, kitabı yatağın üzerine fırlattınız ve spagetti kod yazmaya, müşterinize böyle uygulamalar sunmaya devam ettiniz. İçten içe bir suçluluk duyuyorsunuz ama yapacak birşey yok deyip hayatınıza devam ettiniz. Artık buna bir dur demenin zamanı geldi.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/79086-1klmhbnlpfwbq0pm7hi5uiq.jpeg">
</figure><p>Bildiğiniz gibi ben kuru kuruya kavramları anlatmayı sevmiyorum. İnternetten bulduğu slayttan ders anlatan hocalar gibi ezberden kavram sıralamayı doğru bulmuyorum. Piyasada çok güzel kaynaklar, detaylı kapsamlı kullanım klavuzları var ama ben kavramları anlatmak için Hayvan sınıfı, Memeliler sınıfı, At sınıfı ve Eşşek sınıfı gibi hayatınızda hiçbir yazacağınız programda olmayacak kavramları da kullanmayı sevmiyorum. Detaylı kaynakları konunun mantığını kavradıktan sonra satın alıp, gerçek, profesyonel uygulamalar geliştirirken açıp bakarsınız. Mesela Rıza Hoca’nın <a href="http://www.seckin.com.tr/9789750225932" target="_blank">A-dan Z-ye PHP</a> kitabı vardır. Tavsiye ederim. Ama konuyu hiç bilmiyorsanız, kendinizi bana bırakacak, önce minik adımlarla, masal dinler gibi beni dinleyeceksiniz.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/d6beb-1-mardgna7eob7d_y3qhf4q.jpeg">
</figure><h4>Neden nesne yönelimli programlama öğreneyim ki?</h4>
<ol>
<li>Çünkü bir sonraki aşamaya, yani düzenli, temiz, dünyadaki standartlara uygun, tekrar kullanılabilir, kodu açtığımızda profesyonel birine göstermeye utanmayacağımız kodlar yazmak istiyoruz.</li>
<li>Bizden sonra spagetti karman çorman kodumuz üzerinde çalışacak gariban yazılımcının edeceği küfürler yüzünden kulaklarımızın çınlamasını istemiyoruz. Kodumuz okunabilir oluyor. Karmaşa azalıyor.</li>
<li>Minik minik, kendi projelerimize ait kütüphane oluşturup, yeni projelerde bunları modüler olarak kullanabilmek istiyoruz. Tıpkı Lego gibi. Kodumuz yeniden kullanılabilir oluyor.</li>
<li>Ben zamanında spagetti kod yazarken, kendi kodumu okuyamadığım oluyordu, sonra kendime küfrediyordum, bunun da olmasını istemiyoruz.</li>
<li>Nesne yönelimli programlamanın temel kavramlarını öğrendiğimiz zaman, diğer nesne yönelimli programlama dillerini kolayca kavrayabiliyoruz ve o dilleri kolayca öğrenebiliyoruz.</li>
<li>İyi okunabilen kodlarda, karmaşa daha az olduğu için, hataları yakalamak daha kolay oluyor.</li>
<li>Test edilebilen kodlar yazabiliyoruz. Bu sayede daha sonra ortaya çıkabilecek hataları önceden yakalayabiliyoruz.</li>
</ol>
<h4>Nesne yönelimli programlama öğrenmek istiyorum. Peki nereden başlamalıyım?</h4>
<p>Hiç kod yazmaya girmeden önce kavramları, yani konunun mantığını anlamamız gerekiyor. “Nedir bu nesne kavramı? Ne işe yaradığını az çok anlattık ama tam olarak nedir? Hocam, gerçek hayatta bu ne işime yarayacak?” diye lisede, zavallı öğretmenlerimize ergen kafasıyla ukala ukala sorduğumuz soruların cevabını önce kendimiz verebilecek hale gelmemiz gerekiyor. Yani nesne yönelimli programlayı öğrenmek ve anlamak biraz da bilinç meselesi. Bilinçli, yani ne yaptığımızın farkında olarak çalıştığımızda, üreteceğimiz eserlerin iyi veya kötü, kaliteli veya kalitesiz olup olmadığını kendimiz bilirsek, o zaman kendimize güvenimiz de, başkalarının da bize olan güveni de otomatik olarak artıyor.</p>
<h4>Peki nedir bu Allahın belası Nesne kavramı?</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/b9896-1y3pm4ryy3ivzlyzsvnw3bq.jpeg">

<figcaption class="wp-caption-text">Aristo abimiz. Yakışıklıymış da.</figcaption></figure><p>Kitabı yazmaya başlarken, nesne kavramını çok iyi anladığını sanan ben, konuyu araştırmaya başladığımda olayın yazdığımız salak programları “class” bloklarının içine sokmaktan daha derin olduğunu gördüm. Programlama konusunun temeline indiğimde orada matematikle karşılaştım. Matematiği anlamaya çalıştığımda, aslında çabalarımızın felsefeden başka bir şey olmadığını gördüm. Yani, uğraştığımız şey, dünyadaki olayları anlamak, bunun bir şekilde yorumlamak ve elle tutulur bir değişim yaratacak bir sonuca ulaşma çabası göstermekten ibaret. Yazacağımız programlar, yaptığımız işler görülebilir bir değişiklik yaratmak üzerine. Tam da bu noktada programlamadan çıkıp gerçek hayata geçiyoruz ve anlıyoruz ki nesne dediğimiz varlık sadece basit bir programlama kavramı değil.</p>
<h4>Nasıl yani?</h4>
<p>Yanisi şöyle. Nesne kavramının, dilbilimde (hani özne-nesne, tümleç, yüklem falan var ya.), fizikte (belirli bir yükseklikten, belirli hızda düşen, kütlesi olan nesne), psikolojide (algıladığımız nesneler) yeri var. Biz bilgisayarlarla ilgili olduğumuzdan, bilgisayarlar da düşünen elektronik beyinler olduğundan kavramın düşünce ile ilgili olan tanımına bakalım.</p>
<blockquote>
<strong>nesne</strong> <em>İng.</em> object</blockquote>
<blockquote>(Lat. objectum = karşıda bulunan, karşıya konan) : 1. (Genellikle) Karşımızda bulunan şey. 2. Öznenin bağlılaşık kavramı olarak, özne ediminin, bilincin kendisine yöneldiği şey: a. Kendisine yönelinen, düşünülen, tasarlanan nesne, kendisine yönelen bir edim olmadan var olmayan şey; bilinçte, düşünme nesnesi (konu) olarak düşünme olayının karşısında bulunan şey; düşüncel (ideal) nesne. b. Özne ediminden, bilinçten, bağımsız olan gerçek (real) nesne; gerçeklik olarak, dışdünyanın bir parçası olarak bilincin karşısında duran şey.</blockquote>
<blockquote>
<em>BSTS / Felsefe Terimleri Sözlüğü</em> 1975</blockquote>
<p>Şey diye bitirmiş. Peki şey nedir? Ona da bakalım.</p>
<blockquote>
<strong>şey</strong> <em>İng.</em> thing</blockquote>
<blockquote>(Günlük dilde) Herhangi bir düşünce konusunu göstermeğe yarayan belirsiz terim. (Felsefede) 1. Düşünen bilincin konusu olabilen, gerçekte var olmayıp da yalnızca düşünülmüş olan her şey. Bu anlamda: düşünce nesnesi = ens rationis. 2. Kişiye karşıt olarak: Bilinçten yoksun varlık. 3. Gerçek olan, bilincin dışında, kendi başına var olan tek nesne (ens reale). Böyle bir var olan, tek nesne olarak niteliklerin taşıyıcısı töz diye de anlaşılır. 4. Duyularla kavranabilen cisimsel nesne.</blockquote>
<blockquote>
<em>BSTS / Felsefe Terimleri Sözlüğü</em> 1975</blockquote>
<p>Bu tanımdan şunu anlıyoruz. Birşeyin nesne olabilmesi için belirli kurallar var.</p>
<ol>
<li>Düşünen aklımızın, yani zihnimizin dışında olacak.</li>
<li>Düşüncemizin konusunu oluşturacak, yani düşüncemize yakıt oluşturacak.</li>
<li>İsmi varsa nesne, ismi yoksa şey olarak adlandırılacak.</li>
</ol>
<p>İnsanlar olarak bizim, evrim sürecinde, hayvanlardan farklılaşmamızın en büyük ayırt edici özelliği, düşünebilmemizdir. Düşüncenin dil kavramının insanlarda ortaya çıkmasıyla başladığını biliyoruz. <a href="http://sbard.org/pdf/sbard/013/Fikri%20G%C3%BCl%20son%2065-76.pdf" target="_blank">Kaynak</a></p>
<p>Peki düşünce nedir? Nasıl başlar? Düşünce algı ile başlar. Kendi dışımızdaki ortamda algıladığımız sinyaller, önce beynimize gider. Bu kısaca 3 saattir aradığın, önünde duran ama görmediğin ve salak salak aradığın anahtara baktığın aşama oluyor. O şeyin anahtar olduğunu anladığın anda, algı sürecin tamamlanıyor.</p>
<p>Daha sonra bu algılar ile belirli sonuçlar üretmemiz gerekiyor ki düşünme eylemimiz amacına ulaşsın. Burada, bilgisayar programları veya algoritmaları ile varolan benzerlik dikkatinizi çekti mi? Bilgisayar programları ile biz belirli girdiler kullanarak belirli sonuçlara ulaşmaya çalışıyoruz. Girdi-İşleme-Sonuç adımlarıyla programları çalıştırıyoruz. Düşünce kavramında da, girdiler algılanmış nesnelere, işlem düşünceye ve sonuçlar yani çıktılar, çıkarımlara denk geliyor. Bizim bilgisayarlardan farkımız, benlik bilincine sahip olmamız ve etraftaki kendimizden farklı olan nesnelerin bizim dışımızda olduğunu idrak etmemizden kaynaklanıyor. (Bu konuyu, özellikle yapay sinir ağları konusunu daha derinlemesine araştırırsanız bundan bir 5 sene sonra zengin olacağınızı garanti ediyorum.) Yani nesne, düşüncemizin konusu olan soyut ya da somut varlıkları, önce kendimizden daha sonra birbirlerinden ayırt etmemizi sağlıyor. (Burada da mantık konularına giriyoruz. Üniversite ders kitabı falan yazarsam bu kavramlara derinlemesine ineceğim söz.)</p>
<h4>Gerçek olan ne?</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/fdf7c-1wcvkni6oqqii1uyvbhzq9w.jpeg">

<figcaption class="wp-caption-text">Bakışlara dikkat. Descartes</figcaption></figure><p>Yani ben gerçekten varolduğumu nasıl anlıyorum? Bu konuda Rene Descartes 1637 “Cogito ergo sum” demiş. Yani “Düşünüyorum, o halde varım.” Düşünme eyleminin kendi zihnimizden bağımsız bir dünyanın varlığını gerektirdiğini biliyoruz. fMRI denen beyin taraması insana birşey gösterildiğinde, beynin hangi bölgelerine kan akışı olduğunu gösteriyor. Yeni bilimsel gelişmeler sayesinde, önce zihinden bağımsız varlığın, sonra algı kavramının düşünme kavramının öncülü olduğunu da öğrenmiş bulunuyoruz. Descartes abimizin haklı olduğunu bu sayede anlıyoruz. Yani nesne kavramını oluşturabilmemiz için önce bir içsel zihne (ya da bilgisayar programlarında, çalışan bir hesaplama ünitesine) daha sonra da algılara ihtiyacımız var. (Bu da bilgisayar programlarında girdilere denk geliyor.)</p>
<p>İnsanlar olarak mantıklı düşünmenin önemini biliyoruz. Konuya mantık açısından baktığımızda mantığın en temel kavramlarıyla da ilişki içinde olduğumuzu görmek kolay. <a href="http://www.sauport.sakarya.edu.tr/FileUploads/Modules/Lesson/Store/1/b697ce6a-f9c2-481a-b6ba-98f1419a10d7/7cb32eac-8bc4-4eda-a03a-88cf68781444/data/resources/1.%20UNITE.pdf?download=true" target="_blank">Kaynak</a></p>
<p>Mantığın 4 temel ilkesi diyor ki:</p>
<ol>
<li>A, A’dır. (Özdeşlik ilkesi)</li>
<li>A, A olmayan değildir. (Çelişmezlik ilkesi)</li>
<li>C, ya A’dır, ya da A olmayan’dır. (3. şıkkın imkansızlığı ilkesi)</li>
<li>Sonuç varsa, sebep vardır. (Yeter sebep ilkesi)</li>
</ol>
<p>Matematiğin bile temellerini oluşturan bu düşünsel ilkeler, nesne kavramı için de aynı şekilde geçerlidir. Nesneleri, kendimizden, düşünen zihnimizden ve diğer nesnelerden ayırt edebiliyorsak (1. ve 2. ilke), Nesnelere farklı isimler ile referanslar verebiliyorsak (3. ilke) ve düşünürken ya da programlar yazarken girdilerin, sonuçlar üretebileceğini biliyorsak (4. ilke), mantıklı düşünebiliyoruz demektir.</p>
<p>(Not: Kanıtı olmayan gerçekler kitabı’nda gerçekliğin fiziksel varlıklardan çok, bu varlıkların kendileri dışında yarattığı etkileri de içerdiği iddia ediliyordu. Yani, Mozart, eserleri ile birlikte yaşamaya, düşüncesindeki deseni farklı insanalara aktarmasıyla yaşamaya devam ediyor diye iddia ediliyordu. Bunu da yazayım da kafanız daha da karışsın.)</p>
<h4>Nesne yönelimli programlama nerden çıktı?</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/d2d2f-1gcs0mchqshyxdot10vdqca.jpeg">

<figcaption class="wp-caption-text">Ole-Johan Dahl ve Kristen Nygaard abilerimiz</figcaption></figure><p>Norveç’te 1961 yılının soğuk bir sonbahar akşamı, yani soğuk derken -25 falan, Ole-Johan Dahl ve Kristen Nygaard abilerimiz, Simula denen programlama dilini icat ediyorlar. <a href="http://folk.uio.no/veronahe/simula/HiNC1--Simula-history-2003.pdf" target="_blank">Kaynak</a> Amaçları, yazılan programların insanlar tarafından daha kolay anlaşılmasını ve gerçek hayatta varolan bilimsel olayların daha verimli bir şekilde simüle edilmesini sağlamak.</p>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/c4cc2-159ml4-ppm4i9lud0btrayg.jpeg">

<figcaption class="wp-caption-text">Alan Kay</figcaption></figure><p>Nesne yönelimli programlamayı yaygınlaştıran Alan Kay abimiz, 1971 yılında Amerika’da Smalltalk programlama dilini icat ediyor. Alan Kay abinin bu konudaki motivasyonu ise, kendisi biyoloji kökenli olduğundan, programları, birbiriyle konuşan, birbirinden bağımsız hücreler gibi düşünmesi. Yani kendisinin sahip olduğu biyoloji temeli bugünkü kullandığımız programlama dillerine de temel oluşturuyor. Daha çok merak edenler için <a href="http://worrydream.com/EarlyHistoryOfSmalltalk/" target="_blank">kaynak</a>.</p>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/25cd1-1xqiko1jra2ewufob1lexaq.png">
</figure><p>Burada Nesne Yönelimli programlamanın tarihçesine inmek istemiyorum. Araştırmanızı, okumanızı tavsiye ederim. Bu yazı ders kitabı haline gelirse bunu da yazarım.</p>
<h4>Özne-nesne ilişkisi</h4>
<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/3549e-1xt9065o6e1rmcjm4zh_wiw.jpeg">

<figcaption class="wp-caption-text">Ali Topu At</figcaption></figure><p>Nesnelerin zihnimizin, ya da bilgisayarımızın dışında varlıklar olduğunu ve kavramları birbirinden ve kendimizden ayırt etmemize yardımcı olduğunu anladık. Bunun dışında nesnelerin gerçek dünyaya referans verdiğini, gerçek dünyadaki kavramları temsil ettiğini de az çok biliyoruz. Peki nesneler birbirileriyle nasıl ilişkilere sahipler. Bir nesneyi kullanan, onun üzerinde etkisi olan nesneye, özne diyoruz. Dilbilimde, “Ali topu at!” derken, Ali’nin özne, topun nesne, atmak kelimesinin de yüklem, yani yaptığımız işlem olduğunu biliyoruz. Bilgisayar programlarında, özne, bir diğer nesneyi çağıran, ona mesaj gönderen, onu yaratan bir bilgisayar programıdır.</p>
<h4>Üyelik ilişkisi (IS-A)</h4>
<p>Nesneler belli bir grubun üyesi olabilirler, yani daha üst bir sınıfın özelliklerine sahip olabilirler. Bu sayede birden fazla nesne grubunu, başka gruplardan ayırt edebiliriz. Eski yunanda yaşayan en büyük düşünür Aristo abimiz, taksonomi bilimiyle, canlı varlıkları, ortak özelliklerine göre sınıflandırmış. Biz de nesneleri aynen bu şekilde sınıflandırabiliyor, birden fazla nesneyi ortak özelliklerine göre gruplandırıp onları tek tek belirtmeden, düşüncemizin konusu haline getirebiliyoruz. Yani, Ali, Ayşe, Ahmet, Mehmet demek yerine, “Gıcık insanlar” diyebiliriz mesela. Ayrıca bir grubun üyesi olmayan iki ayrı nesne, aynı eylem içinde birlikte yer alıyorlarsa, onlar da belirli bir grubun içinde kabul edilebilirler. Örneğin, “Ali ve Ayşe İstabul’a gittiler” dediğimizde, Ali ve Ayşe’nin gitme eylemini yapabilen türden varlıklar olduklarını anlayabiliriz. <a href="http://www.javatpoint.com/inheritance-in-java" target="_blank">Kaynak</a></p>
<h4>Nesneler farklı nesnelerin bir araya gelmesiyle oluşabilirler. (HAS-A)</h4>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/4cd8f-1it0rtrwsx3fwwbdz8ftjrw.jpeg">
</figure><p>Yukarıda verdiğimiz grup örneğinde, eğer oluşturduğumuz grubun kendisi de bir nesne olarak kullanılabiliyorsa buna, Toplama (yani Aggregation) diyoruz. Örneğin, bir etli türlü yapmak için, patlıcan, domates, bamya, tereyağı kullanıyoruz ve sonuç olarak etli türlü elde ediyoruz. Elde ettiğimiz sonuç yine bir nesne meydana getirebilir. <a href="http://www.javatpoint.com/aggregation-in-java" target="_blank">Kaynak</a></p>
<h4>Nesnelerin kendilerine ait özellikleri ve yapabildikleri vardır.</h4>
<figure>

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/06b18-1dtewo1kkfzvxgwdibi29jg.jpeg">
</figure><p>Örneğin Ahmet çok yemek yerse, kilo alır. Ahmet tutup dünyayı yiyip 101 kiloya çıkarsa mutsuz olur. Ahmetin nümerik kilo özelliği, onun şu anki duygu durumu özelliğini etkiler. Ahmetin yemek yiyebilmesi onun yapabildiği şeyleri gösterir. Ahmet kilosundan mutsuz olup kendini aç bırakırsa, akşam daha çok acıkıp, iki tane fırın sütlaç, iki prosiyon döner ve kaymaklı ekmek kadayıfı yer ve daha çok mutsuz olur.</p>
<h4>Nesneler birbirlerine mesaj gönderebilirler.</h4>
<p>Ahmet’i uzun zamandan sonra gören arkadaşı, “Baba sen napmışsın, acayip kilo almışsın yea.” diyebilir. Arkadaşı Ahmet’e mesaj göndermiş olur. Ahmet’de buna sinir olup 3 ay boyunca spor salonuna yazılıp iyi bir diyet ve egzersiz programı ile fit bir hale gelebilir. Yani, nesnelerin birbirlerine gönderdikleri mesajlar, nesnelerin eylemlerini tetikleyebilirler. Bu eylemler sonucunda nesneler kendi özelliklerini değiştirebilirler.</p>
<p>Şimdilik bu kadar. Umarım kavramlar kafanızda biraz oturmuştur. Yazı ile ilgili düzeltme ve yorumlarınızı, sorularınızı bekliyorum.</p>
<p>Serinin devam yazısına <a href="https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-2-fa6aa74b93f3#.eo6qlnt8z" target="_blank">şuradan</a> ilerleyebilirsiniz:</p>
[embed]https://medium.com/turkce/hi%C3%A7-bilmeyenler-i%CC%87%C3%A7in-nesne-y%C3%B6nelimli-programlamaya-giri%C5%9F-2-fa6aa74b93f3[/embed]
<hr>

<figure class="wp-caption">

<img src="https://meraklibilisimcihome.files.wordpress.com/2017/01/2886d-14uozfs7kywroi5ep-uyz5g.jpeg">

<figcaption class="wp-caption-text"><em>Projelerle PHP 7</em></figcaption></figure><p><em>Ben </em><a href="http://mynameismidori.com" target="_blank"><strong><em>Mutlu Koçak</em></strong></a><em>, Bilgisayar Mühendisiyim, ZCPE Sertifikasına sahibim ve “</em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>Hiç Bilmeyenler İçin İnternet Programlamaya Giriş — PHP 7</em></a><em>” adlı kitabın yazarıyım. Kitabım: </em><a href="https://www.seckin.com.tr/kitap/911934237" target="_blank"><em>https://www.seckin.com.tr/kitap/911934237</em></a><em><br>Özgeçmişim: </em><a href="http://represent.io/mtkocak.pdf" target="_blank"><em>http://represent.io/mtkocak.pdf</em></a><em> <br>Websitem: </em><a href="http://mynameismidori.com" target="_blank"><em>http://mynameismidori.com</em></a></p>