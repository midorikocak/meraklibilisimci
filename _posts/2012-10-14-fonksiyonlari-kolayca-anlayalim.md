---
ID: 151
post_title: Fonksiyonları kolayca anlayalım
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/fonksiyonlari-kolayca-anlayalim/
published: true
post_date: 2012-10-14 00:10:02
---
Fonksiyon; belli bir kod bloğunu tekrar tekrar kullanmak amacıyla kullanılır. İsterse bir değer alır ve verebilir. Mesela verdiğimiz doğum tarihine göre ne kadar gün, ay, yıl gerekitğini hesaplayan bir kod bloğumuz olabilir. Bu kod bloğunu her doüum tarihi gördüğümüz yerde tekrar tekrar yazmamak için fonksiyon kullanabiliriz. Bunun basit örneklerini daha sonraki örneklerde de göreceğiz. Aldığı numarayı ikiyle çarpan bir fonksiyon örneği verelim:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.18-PM.png"><img title="Screen Shot 2012-10-13 at 10.04.18 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.18-PM.png" height="189" width="405" /></a>

Htdocs klasörü içinde mtkocakPhpEgitimi klasörümüzün altında bulunan 3-fonksiyon.php dosyasında doğum yılı ve içinde bulunduğumuz yılı vereceğimiz ve bize yaşımızı döndüren basit bir fonksiyonu şu şekilde tanımlamışız:
<pre>&lt;?php
/**  
*                    Merakli Bilişimci
*                   meraklibilisimci.com
**/

// Bu örnekte Fonksiyonları anlayacağız.

// Girilen doğum yılından yaş hesaplayan bir fonksiyon yazalım.

function yasHesapla($dogumYili,$gecerliYil) 
{
    $sonuc = $gecerliYil-$dogumYili;
    return $sonuc;
}</pre>
Görüldüğü gibi function ifadesiyle PHP yorumlayıcısıne fonksiyon tanımlayacağımızı haber verdik, daha sonra fonksiyonun adını belirttik ve parantez açarak fonksiyonun alacağı girdi değişkenlerini tanımladık. Mesela, fonksiyonumuz girdi almıyorsa; parantezin açini boş bıraka bilirdik. Süslü parantezleri kullanarak da fonksiyonun içinde kullanacağımız kodumuzu tanımladık. Gördüğümüz gibi fonksiyon yazmak gayet kolay, eğlenceli ve güzel birşey. Bu arada bir not aklımıza takılan bir şey olursa, bölümü, kodu ve kod yorumlarını tekrar okumaktan şekinmeyelim. Çok küçük adımlarla öğrenirsek yere sağlam basarız. Tekrar okurken o sırada anlamadığımız bir şeyi çözmemiz ve aklımızda lambanın yanması daha muhtemel.

<a href="http://127.0.0.1/mtkocakPhpEgitimi/3-fonksiyon.php">http://127.0.0.1/mtkocakPhpEgitimi/3-fonksiyon.php</a> adresinden dosyamızı çağırdığımızda, karşımıza şöyle bir görüntü gelecek:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-3.02.48-AM.png"><img class="alignnone size-full wp-image-133" title="Screen Shot 2012-10-14 at 3.02.48 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-14-at-3.02.48-AM.png" height="120" width="440" /></a>

Burada fonksiyon; $dogumYili, $gecerliYil degişkenlerini alır ve $yas adlı degiskeni hesaplar. Daha sonra da $sonuc degiskenini deger olarak döndürür. Değer döndürme dediğimiz zaman, eğer "return" ifadesiyle bir fonksiyonun değerini döndürüyorsak, bu değeri şu şekilde başka bir değişkende kullanabiliriz:

$yas = yasHesapla(1984,2012);

Buradan elde ettiğimiz $yas degiskenini;

echo $yas diyerek ekrana basarsak; 28 sayısını görürüz.
<pre>echo "Merhaba, ".$yas." yaşındasınız."; // Sonuçları bu şekilde ekrana yansıtıyoruz.</pre>
Biz de örneğimizde bu şekilde değişkenimizi çağırmışız. Ancak;
<pre>echo "Merhaba, ".yasHesapla(1984,2012)." yaşındasınız."; // Sonuçları bu şekilde ekrana yansıtıyoruz.</pre>
Fonksiyonumuzdaki return ifadesinden dolayı bu şekilde de ifadeyi çağırabilirdik.

PHP'de fonksiyonların kullanımı C++ veya Java'ya çok benziyor. En önemli farklardan birisi fonksiyonların döndürdükleri değeri başında belirtememe gerek olmaması. Nasıl değişken tanımlarken bu işlemi yapmıyorsam, fonksiyon tanımlarken de bunu yapmama gerek yok.

Burada sadece karakterlerden oluşan değişkenlerin kullanımıyla ilgili hata yapmaya çok müsait bir konuyu daha da detaylandıralım ve Php'de Debugging'den bahsedelim.

Nasıl $toplam = $sayi1 + $sayi2; diyerek sayı içerek değişkenleri toplayabiliyorsak; sadece karakter içeren değişkenleri de birbirinin ucuna eklemek için

$adi = "Mutlu";
$gobekAdi = "";
$soyadi = "Koçak";

$tamAdi = $adi.$gobekAdi.$soyadi;

ifadesini kullanabiliriz.

echo $tamAdi;

dediğimizde karşımıza çıkan sonuç MutluKoçak olacaktır. Bu kelimelerin arasına da boşluk karakterlerini de şu şekilde yerleştirebiliriz.

$tamAdi = $adi." ".$gobekAdi." ".$soyadi;

Bu noktalar ve tırnakların sırasına özellikle çok ama çok dikkat etmemiz gerekiyor. Eğer IDE kullanmıyorsanız, yapacağınız bir hatanın nerede olduğunu bulmak başınızı çok ağrıtabilir. Aynı zamanda bu özellik parantexz için de geçerli, parantezleri her zaman kapatmaya dikkat edelim. Bir de işlem sırası olayı var, herhangi bir matematiksel ya da mantıksal işlemi yaparken, parantezin içindeki bölümün her zaman önceliği vardır. Bunu da unutmamak, parantezleri kapatmaya, satır sonlarındaki noktali virgülleri unutmamaya dikkat edersek, sorun yaşamaz, binlerce sotır kod arasında böcek ayıklama tabir edilen debugging işlemini yapmamıza gerek olmaz.

Ekstra bilgi debugging: Bilgisayarların ilk zamanlarında, cihazlar oda büyüklüğünde ve lamba ile çalıştıkları için, kapıyı açıp kapatmak bile bilgisayar odasının ısısını değiştirebildiği ve sistemin açılıp kapanmasına neden olabildiği zamanlarda, herşey iyi programlandığı halde, ısı durumları da iyiyken, bilgisayarın sürekli hata vermesi üzerine, tüm bilgisayarı arayan programcıların bulduğu küçük bir böcek yüzünden, kodların arasında hata arama işlemine ingilizce böceksizleştirme yani debugging, türkçede ise hata ayıklama deniyor. Bu bulunan ilk böcek, aynı zamanda seloteyple bilgisayarın hata defterine de işlenmiş. :) Bu hata defteri ve küçük böcek şimdi müzede meraklıların ilgisini çekiyor.

İşte yaş örneğimizde ekrana yazı yazarken kullandığımız ifade de bu boşluk karakterlerini içeriyor.

Buraya kadar fonksiyonun neden kullanıldığını ve nasıl tanımlanacağını anlamış bulunuyoruz.

Dayanışmayla!
Meraklı Bilişimci