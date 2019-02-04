---
ID: 537
post_title: Spagetti kod nedir?
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/spagetti-kod-nedir/
published: true
post_date: 2014-03-07 01:07:59
---
Sıklıkla duyduğumuz spagetti kod bütün PHP geliştiricilerinin (ben dahil) içinden geçtiği bi aşamadır. Eğer "ben böyle iyiyim yeaa!" derseniz, içinde "OOP" geçen iş ilanlarından kaçarsınız. Ama doğru dürüst program yazacağım, kaliteli ve uzun ömürlü iş çıkarmak istiyorum diyorsanız, KENDİNİZİ GELİŞTİRECEKSİNİZ.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/italian-food-coding-spaghetti.jpg"><img class="alignright size-large wp-image-539" alt="Italian Food Coding Spaghetti" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/italian-food-coding-spaghetti.jpg?w=474" width="474" height="364" /></a>

Gelelim spaghettiye. Spaghetti kodun ilk özelliği, hiçbir sınıf veya daha açık bi şekilde nesne yönelimli programlama yapısına sahip olmamasıdır. Yani nesne yönelimli programlamanın avantajlarını kullanamazsınız. Aynı dosya içinde istediğiniz yerlere fonksiyonları tanımlarsınız ve html'nin bir köşesinde, js'nin içinde bu fonksiyonları gelişigüzel çağırırsınız.

Diyelim ki sık kullandığınız fonksiyonları grupladınız ve include etmeye başladınız, include '1.php'; include '2.php'; gidiyor. Hangi fonksiyon nerdeydi? Ya 600 fonksiyonunuz varsa, ya da farklı kütüphaneleri çekiyorsanız? Acaba fonksiyon isimleri çakışıyor mu? Kabus.

Mesela OOP, OOP diye duydunuz. Yazdığınız spagetti kodunun başına class yazmakla da olmuyo. Aşama aşama ilerleyelim. Haberler diye bi veritabanı tablonuz var, canavar gibi site yapıp satıcaksınız. Habergoster.php, haberekle.php, haberduzenle.php, haberlistele.php gibi bir sürü dosya oluşturmanız gerekiyor. Diyelim ki bunu yaptınız. Login.php diye bir dosyayı include ettiniz. Bir de database bağlantınız var, db.php'yi include ettiniz. sıra geldi mesela haber göstermeye.

db.php, dosyasından bağlantı ayarlarını aldınız, bağlantıyı açtınız, Login.php, logini doğruladı, sessiona bilgileri attınız, her dosyada bu session'u kontrol ediyorsunuz. bağlantıyı nerde kapattınız? Neyse bi yerde kapandı diyelim. Haberleri girmek istiyoruz. Napıcaz? Girişleri form ile alacağız. Bir de bu girişleri sql injection, html taglerinden ayırıp sanitize etmek lazım. Diyelim ki bilgiyi girerken haberekle.php içinde yaptınız. Her dosyada SQL komutlarıyla veritabanına bağlandınız. Haber gösterirken ayrı SQL, haber eklerken ayrı SQL, silerken ayrı, listelerken ayrı. Bir de tüm bu işlemler için php dosyasının başına fonksiyonlar tanımlamış olun. Bitti mi? Bitmedi. Yaptığınız tüm bilgi girişlerini de ayrıca kontrol etmeniz lazım. Bir de mesela daha beteri, haber listele sayfasında bazı div'lerin içinde style özelliği ile CSS'ler tanımlanmış olsun. Ayrı ayrı hem CSS dosyasında hem de HTML taglerinde CSS tanımlı. Bir de script taglerinin içinde js kodu yazdıysanız, bazı js dosyalarını da include ettiğiniz dosyalar olduysa, diyelim ki onları da çalıştırdınız. Sorunsuz çalışan sistem. Öyle mi değil.

En küçük bir php fonksiyonu hatasında, js çakışmasında, css bozulmasında, hatayı bulacağınız yer belli değil. Hatayı bulmak için aramak için arayacağınız süre x1500.

O yüzden asla ve asla ve asla, HTML, JS, CSS (hatta PHP!) kodlarını iç içe kullanmayın.

Öyle saçmalıklar gördüm ki, bir js slider jQuery 1.7.1 ile çalışıyor, sitenin başka bir yerindeki silder jQuery 1.8.3 ile çalışıyor diye iki kütüphaneyi include edip, birbirini ezdiren developer var. İşte spaghetti kafası budur.

Diyelim ki siz işinizi düzgün yaptınız. Kodun yerlerini canavar gibi biliyosunuz. Başka bir şirket size ben oracle kullanıyorum, ya da msSQL kullanıyorum dediği anda işiniz biter. Sizin iç içe geçmiş bilmem kaç bin satırlık SQL kodlarınızı baştan yazmanız yalan, dolan, iftira.

Diyelim ki database abstraction yaptınız, neyi nerde ne zaman kullanacağınız belli değil, onu include et, bunu include et daha sonra include cehennemi içinde kaybolmak sorun değil de, zavallı PHP makinesi, apache sunucusu ne yapsın, hem js göndericek, hem includları bağlıycak, sonra 20 saniyede açılan siteye kafasını kaşıyarak bakan developer olursunuz.

Gittiniz ben biliyorum diye abuk subuk değişken isimleri yazdınız, $kategoriAltBaşlık yazmak zor geldi $kaltb yazdınız, 10 ay sonra aynı koda baktığınızda unutacağınız garanti. indentasyona dikkat etmediniz, içiçe geçmiş kodlar, short_tag'ler kullandınız. Kodunuza bakan küfür eder.

Marifetmiş gibi aynı dosya içinde herşeyi yaparsanız, 1600 satırlık tek PHP dosyasını okumaya çalışan PHP makinesi size küfür eder bu sefer.

Veriyi serialize edip veya implode edip veritabanı tablosuna basmayın. Enum kullan bişey kullan. MVC'yi OOP'yi mahvetme arkadaşım. PHP veriyi çekecek, bir de gelen arrayi explode edecek, veya unserialize edicek, sonra lineer bi şekilde veriyi arayacak. Yahu o zaman niye veritabanı kullanıyosun ki, objeleri serialize et, dosyaya yaz. Bi şeyi insan niye icat etmiş, veritabanı neden var, avantajları nelerdir? Bi düşünün, bir sorgulayın yahu.

YAPMAYIN. OOP öğrenin arkadaşlar, araştırın. Araştırmadan, kendini geliştirmeden, insanlar sırf alıyor ediyor diye, hem genel kalite düşüyor, hem piyasa düşüyor, hem de yerinize gelen developer kulaklarınızı çınlatıyor.

Kaynak: http://www.w3schools.com/php/func_mysql_fetch_array.asp