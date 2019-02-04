---
ID: 147
post_title: 'Github&#8217;da paket oluşturmak'
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/githubda-paket-olusturmak/
published: true
post_date: 2012-10-13 18:01:45
---
Github kurulumunu yaptıktan ve bilgisayarımızla anlaştırdıktan sonra sıra geldi yeni bir paket oluşturmaya.

Mesela yeni bir proje oluşturmak istiyoruz. Projemiz basit bir adres defteri olsun. Henüz projemize başlamadık ama github paketimizi oluşturalım. Hem herkes görsün hem de katkı sağlayabilsin. Adı da openContacts olsun. Açık iletişim gibi.

İlk olarak github hesabımıza giriş yaptıktan sonra sağ üst köşedeki <a href="https://github.com/new">Create a New Repo</a> linkine tıklayalım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.16.33-PM.png"><img class="alignnone size-full wp-image-59" title="Screen Shot 2012-10-13 at 8.16.33 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.16.33-PM.png" height="360" width="298" /></a>

Daha sonra karşımıza şöyle bir sayfa çıkacak. Onu da şekilde görüldüğü gibi dolduralım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.18.32-PM.png"><img class="alignnone size-full wp-image-60" title="Screen Shot 2012-10-13 at 8.18.32 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.18.32-PM.png" height="352" width="628" /></a>

Burada description kısmını istersek doldurmayabiliriz ama biz doldurmayı tercih ettik. Eğer paketimizi başarıyla oluşturduysak karşımıza şöyle bir ekran çıkacak:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.20.06-PM.png"><img class="alignnone size-full wp-image-61" title="Screen Shot 2012-10-13 at 8.20.06 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.20.06-PM.png" height="350" width="628" /></a>

Şimdi burada aşağıda gördüğümüz komutları kendi bilgisayarımızda uygulayacağız. İlk komutlar bilgisayarımızda yepyeni ve taptaze ve hatta bomboş bir paket ortamı oluşturmak istiyorsak yazacağımız kodları belirtiyor.

Burada Window$ kullanıyorsak Git-Bash veya Linux veya mac kullanıyorsak terminal programı kullanarak yazacağımız kodlar belirtilmiş. Öncelikle herhangi bir yerde openContacts klasörü oluşturalım ve klasöre girelim. (Not: linux altında pwd komutu o sırada hangi klasörde olduğumuzu gösterir.)

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.26.04-PM.png"><img class="alignnone size-full wp-image-62" title="Screen Shot 2012-10-13 at 8.26.04 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.26.04-PM.png" height="105" width="368" /></a>

Klasörü oluşturup içine de girdikten sonra sıra geldi GitHub'a paketimizin burada olduğunu söylemeye:
<pre>Mutlus-MacBook-Pro:openContacts mtkocak$ touch README.md
Mutlus-MacBook-Pro:openContacts mtkocak$ git init
Initialized empty Git repository in /Users/mtkocak/openContacts/.git/</pre>
Burada touch ile yeni bir boş dosya oluşturduk. Bu github tarafından tanınan benioku dosyasıdır. Paketi başarıyla eklediğimizde bu dosyanın içeriği doğrudan paketimizin GitHub sayfasında çıkar.

Daha sonra bu dosyayı add komutuyla paketimizin içine ekleyelim. Ekleme işlemini yaptıktan sonra da tırnak içinde başlığıyla ilk versiyon işlemimizi(commit) yapalım.
<pre>Mutlus-MacBook-Pro:openContacts mtkocak$ git add README.md 
Mutlus-MacBook-Pro:openContacts mtkocak$ git commit -m "ilk commit"
[master (root-commit) d62d303] ilk commit
 0 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md</pre>
Paket içeriğimiz değişti. Gördüğümüz gibi artık paketimizde yaptığımız değişiklikleri başlıklarıyla yönetebilir, değiştirebilir hatta geri alabiliriz.

Daha sonra yerel git paketimize GitHub hesabımızı tanıtalım:
<pre>Mutlus-MacBook-Pro:openContacts mtkocak$ git remote add origin https://github.com/meraklibilisimci/openContacts.git</pre>
Daha sonra da kullanıcı adı ve şifre girerek yerelde yaptığımız değişiklikleri, GitHub hesabımızdaki paketimizle eşitleyelim:
<pre>Mutlus-MacBook-Pro:openContacts mtkocak$ git push -u origin master
Username:
Password:
Counting objects: 3, done.
Writing objects: 100% (3/3), 223 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/meraklibilisimci/openContacts.git
* [new branch] master -&gt; master
Branch master set up to track remote branch master from origin.
Mutlus-MacBook-Pro:openContacts mtkocak$</pre>
Eğer herşeyi başarıyla tamamladıysak, paketimize README.md dosyamız eklenmiş olacak ve GitHub ekranı şu şekilde görünecek:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.40.00-PM.png"><img class="alignnone size-full wp-image-63" title="Screen Shot 2012-10-13 at 8.40.00 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.40.00-PM.png" height="331" width="628" /></a>

Tebrikler, ilk paketinizi yarattınız ve başarıyle yüklemenizi yaptınız. Fakat bu iş için daha güzel bir aracımız daha var. Onu da ilk yazıda yüklemiştik. GitHub GUI programı.

Bu program otomatik olarak yaptığımız değişiklikleri görüyor ve görsel arayüzü sayesinde tek tıklamayla eşitleme işlemlerini yapmamızı sağlıyor.

GitHub GUI programını çalıştıralım. Programa ilk giriş yaparken bize github hesabımızda kullandığımız e-posta adresimizi ve şifremizi sorar. Kullanmak istediğimiz paketleri de seçebiliriz. Eğer herşeyi doğru yaptıysak karşımıza şöyle bir ekran gelecek: (Ben Mac kullandığım için Mac versiyonu görünüyor)

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.44.20-PM.png"><img class="alignnone size-full wp-image-64" title="Screen Shot 2012-10-13 at 8.44.20 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.44.20-PM.png" height="440" width="628" /></a>

Şimdi openContacts klasöründeki README.md dosyasını açalım ve içini şu şekilde değiştirip kaydedelim.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.47.16-PM.png"><img class="alignnone size-full wp-image-65" title="Screen Shot 2012-10-13 at 8.47.16 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.47.16-PM.png" height="163" width="535" /></a>

GitHub programına geri dönelim, openContacts'ın yanındaki ok işaretine tıklayalım ve SÜRPRİZ! Şimdi Uncommitted Changes yazısının altındaki Commit Summary bölümüne "readme'yi değiştirdik" yazalım. Başka bir açıklamamız veya yorumumuz varsa, Extended Description kısmına "Buraya istersek açıklama da koyabiliriz." yazalım. Bu yaptığımız açıklamalar daha sonra yaptığımız işlemlere geri dönüp baktığımızda hem bize hem de kod üzerinde çalışan başkalarına da faydalı olacak.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.49.59-PM.png"><img class="alignnone size-full wp-image-66" title="Screen Shot 2012-10-13 at 8.49.59 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.49.59-PM.png" height="331" width="628" /></a>

Yazdıktan sonra Commit butonuna tıklayalım. Unutmayalım Commit işlemini yapmak sadece yerelde yani bilgisayarımızda bulunan paketi değiştiriyordu. Bu nedenle Sync yani eşitleme işlemi de yapmak için commit yaptıktan önce unsynced commits kısmında sync tuşuna da tıklayalım:<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.53.17-PM.png"><img class="alignnone size-full wp-image-67" title="Screen Shot 2012-10-13 at 8.53.17 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.53.17-PM.png" height="327" width="628" /></a>

Eğer herşey yolunda gittiyse GitHub programı şu şekilde görünecektir.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.58.48-PM.png"><img class="alignnone size-full wp-image-68" title="Screen Shot 2012-10-13 at 8.58.48 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.58.48-PM.png" height="417" width="483" /></a>

Son olarak da eğer herşeyi başarıyla hallettiysek GitHub'daki paketimize geri döndüğümüzde, yapığımız değişiklik karşımıza çıkar:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.59.06-PM.png"><img class="alignnone size-full wp-image-69" title="Screen Shot 2012-10-13 at 8.59.06 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-8.59.06-PM.png" height="339" width="628" /></a>

Gördüğümüz gibi artık paket oluşturmayı üzerinde değişiklik yapmayı öğrenmiş bulunuyoruz. Şimdi bundan sonra internet programlamayı öğrenirken de her adımda github'u kullanacağız.

Dayanışmayla!
Meraklı Bilişimci