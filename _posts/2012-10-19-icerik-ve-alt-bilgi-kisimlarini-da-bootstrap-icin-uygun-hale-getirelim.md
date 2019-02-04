---
ID: 256
post_title: >
  İçerik ve alt bilgi kısımlarını da
  Bootstrap için uygun hale getirelim
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/icerik-ve-alt-bilgi-kisimlarini-da-bootstrap-icin-uygun-hale-getirelim/
published: true
post_date: 2012-10-19 08:25:56
---
Genellikle bu tarz şirket sayfalarında ürünleri ya da hizmetleri gösteren 940 piksel genişliğinde bir ana resim bulunur. Bizim de elimizde şöyle bir resim olsun:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/anaresim.jpg"><img class="alignnone size-medium wp-image-257" title="anaResim" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/anaresim.jpg?w=300" height="108" width="300" /></a>

Bu resmi icerik adlı section etiketimizin hemen altına anaResim adlı div kutusunun içine yerleştireceğiz ki ilk mesajımızın hemen üstünde ama üs kısımın da hemen altında bulunsun.
<pre><code>&lt;div id="anaResim"&gt;&lt;img src="anaResim.jpg" alt="Ana Resim"/&gt;&lt;/div&gt;</code></pre>
Daha sonra mesaj kısmının olduğu yeri ve altında bulunan bilgi kısmındaki article'ları yerleştirmemiz gerekiyor. Geniş mesajımız tüm sayfayı kaplasın, ürünlere göz atın linkimiz de hemen altında yeralsın. Daha önce yaptığımız gibi satırları oluşturalım.
<pre><code>&lt;div id="mesaj"&gt;
    &lt;div class="row"&gt;
        &lt;div class="span12"&gt;
            &lt;h1&gt;&lt;strong&gt;İstanbul'daki en hızlı, en kaliteli ve en uygun fiyatlı matbaayı mı arıyorsunuz?&lt;/strong&gt;&lt;/h1&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div class="row"&gt;
        &lt;div id="inceleyin" class="span4 offset8"&gt;
            &lt;a class="btn btn-primary btn-large"  href="urunler.html"&gt;Ürünlerimizi inceleyin&lt;/a&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/div&gt;
</code></pre>
Gördüğümüz gibi mesaj kısmının boyu 12 birim. Yani tüm sayfayı kaplıyor. Ürünleri inceleyin kısmının boyu ise 4 birim. Ancak burada yeni bir şey var. offset8. Yani kaydırma. Yine 4 birim olan bir kutu yaptık. Ama bu sefer bu kutuyu en sağa kadar getirdik. Linkle alakalı yeni bir özellik daha var. "btn btn-primary btn-large" sınıflarıyla linkimizi büyük bir buton haline getirdik.

Son durum:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.00.12-AM.png"><img class="alignnone size-medium wp-image-258" title="Screen Shot 2012-10-19 at 11.00.12 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.00.12-AM.png?w=300" height="152" width="300" /></a>

Mesaj kısmı biraz daha anaResim'den uzak dursa iyi olur. Bunu da custom.css dosyasını değiştirerek yapacağız. Ama şimdilik devam edelim.

Sıra bilgilerimizi tutan article etiketlerini düzenlemeye geldi. Bunların da her biri için önce bir satır kutusu açalım ve boylarını sırayla 4 birim, 3 birim ve 4 birim olarak ayarlayalım. Bir kutunun boyunu küçük tutmamızın sebebi yine alt satıra düşmelerini engellemek.
<pre><code>&lt;div id="bilgiler" class="row"&gt;
    &lt;article id="neyapiyoruz" class="span4"&gt;
        &lt;h3&gt;Ne yapıyoruz?&lt;/h3&gt;
        &lt;p&gt;İstanbul'dasınız, davetiye, broşür, poster veya el ilanı'na ihtiyacınız var. Hem de 3 günde. Fiyatı da biraz uygun olsun ama sonuçlar temiz mi olsun? O zaman doğru yere geldiniz.&lt;/p&gt;
    &lt;/article&gt;   
    &lt;article id="neredeyiz" class="span3"&gt;
        &lt;h3&gt;Neredeyiz?&lt;/h3&gt;
        &lt;p&gt;İstanbul'un tarihi merkezi Sirkeci'deyiz. Ama mesafeler sorun değil. Siz bize gelemezseniz, biz size geliriz. Siparişim ayağıma gelsin diyorsanız, o da olur. &lt;/p&gt;
    &lt;/article&gt;  
    &lt;article id="farkımız" class="span4"&gt;
        &lt;h3&gt;Bizim farkımız&lt;/h3&gt;
        &lt;p&gt;Kesin kalite garantisine ihtiyacınız varsa, ücretsiz motorsikletli kuryeyle baskı işlerim gönderilsin diyorsanız, fiyatlar uygun olsun ama fazla da gecikmesin 3 gün içinde elimde olsun istiyorsanız, aradığınız yer burası. &lt;/p&gt;
    &lt;/article&gt;  
&lt;/div&gt;</code></pre>
Bilgiler kısmını da bu şekilde düzenledik.

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.04.28-AM.png"><img class="alignnone size-medium wp-image-259" title="Screen Shot 2012-10-19 at 11.04.28 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.04.28-AM.png?w=300" height="57" width="300" /></a>

Şimdilik iyi ama daha yapmamız gereken çok şey var. CSS ile düzeltmeler yapalım. Burası biraz karışık gibi gözüküyor ama değil ve çok kolay aslında:
<pre><code>
#mesaj
{
    /*Her yünden 20 piksellik boşluk bıraktık*/
    margin: 20px;
}

/*id'si bilgiler olan etiketin içindeki article etiketlerini seçtik*/
#bilgiler &gt; article
{
    /*Yazılar için her yünden 10 piksellik boşluk bıraktık*/
    padding: 10px;

    /*1 piksellik kesintizik #e8e8e8 renginde kenar çizgisi oluşturduk*/
    border: 1px solid #e8e8e8;

    /*5 piksel çapında yuvarlak kenar elde ettik*/
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;

    /*Kutumuza gölge ekledik*/
    -webkit-box-shadow: 0 0 5px #efefef;
    -moz-box-shadow: 0 0 5px #efefef;
    box-shadow: 0 0 5px #efefef;

    /*Kutunun arka planı için gradient yani renk geçişi kullandık*/
    background: -webkit-gradient(linear, left top, left bottom, from(#fff), to(#efefef));
    background: -moz-linear-gradient(top, #fff, #efefef);

    /*Kutu boyunu da 242 piksel olarak ayarladık*/
    height:242px;
}

#bilgiler
{
    /*Yazılar için alttan ve üsttem 20 piksellik boşluk bıraktık ki yapışmasın*/
    padding-bottom: 20px;
    padding-top: 20px;
}
</code></pre>
Yorum kısmında yaptığımız işlemler için açıklamalar yaptık. Burada yeni olan iki özellik şu. Birincisi #id &gt; article yani bir id ismine sahip olan etiketin içinde yer alan article adındaki tüm etiketleri bu şekilde seçiyoruz. Diğeri ise gradient yani renk geçişli arka plan. Bu da CSS3 ile gelen yeni bir özellik.

Bunları yaptıktan sonra bilgiler kısmının son görüntüsü şu şekile geldi:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.13.32-AM.png"><img class="alignnone size-medium wp-image-260" title="Screen Shot 2012-10-19 at 11.13.32 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.13.32-AM.png?w=300" height="143" width="300" /></a>

Çok daha güzel.

Son olarak da alt bilgi kısmını düzeltelim. Onu da bir satır haline getirelim ve içindekileri teker teker boyutlandıralım.
<pre><code>
&lt;footer&gt;
    &lt;div id="footer-content"&gt;
        &lt;div class="row"&gt;
            &lt;nav class="span2 offset3"&gt;
                &lt;h4&gt;Bağlantılar&lt;/h4&gt;
                &lt;ul id="altListe"&gt;
                    &lt;li&gt;&lt;a href="anaSayfa.html"&gt;Ana Sayfa&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="hakkimizda.html"&gt;Hakkımızda&lt;/a&gt;&lt;/li&gt;
                    &lt;li&gt;&lt;a href="kurumsal.html"&gt;Kurumsal&lt;/a&gt;&lt;/li&gt;
                &lt;/ul&gt;
            &lt;/nav&gt;
            &lt;div id="iletişim"&gt;
                &lt;div id="adres" class="span2"&gt;
                    &lt;h4&gt;Adres:&lt;/h4&gt;
                    Kızılyıldız Matbaacılık A.Ş.
                    Denizler Mah.
                    Eren Sok. No:68
                    Sireci, Fatih 34110
                    İstanbul TÜRKİYE
                &lt;/div&gt;
                &lt;div id="telefon" class="span2"&gt;
                    &lt;h4&gt;Telefon&lt;/h4&gt;
                    Tel: +90 212 444 19 17
                    Fax: +90 212 444 19 05
                &lt;/div&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;div id="footer-floor"&gt;
        &lt;div id="copyright"&gt;Her Hakkı Saklıdır. 2012 Kızılyıldız Matbaacılık A.Ş.&lt;/div&gt;
    &lt;/div&gt;
&lt;/footer&gt;
</code></pre>
Alt bilgide yapacaklarımız ise şöyle. Alt bilginin arkaplan renklerinin koyu gri ve siyah, başlık ve yazılarının ise beyaz ve açık gri olmasını istiyoruz. Yine boşluklara ve yapışmalar dikkat ederek tablomuzu tamamlayalım:
<pre><code>
/*Burada pek öğrenmediğimiz birşey kalmadı aslında*/
#footer-content
{
    background: #252525;
    color: #999;
    padding:10px;
}

/*Footer içinde tüm seviyelerde yer alan h4 etiketlerinin rengini beyaz yaptık*/
footer h4
{
    color: #fff;
}

/*Footer içinde tüm seviyelerde yer alan linklerin rengini beyaz yaptık*/
footer a
{
    color:#fff;
}

/*Listenin başındaki noktacıkları yokettik*/
#altListe
{
    list-style:none;
}

/*Text-align özelliği ile yazıları sağa yasladık*/
#footer-floor {
    color: #999;
    background: #1b1b1b;
    padding: 10px;
    text-align:right;
}

/*Bu etiketler için yazıtipini değiştirdik*/
p, ul, ol, dl {
font-family: "Droid Sans","Helvetica Neue",Helvetica,Arial,sans-serif;
}</code></pre>
Burada farklı olan bir şey yok. Tek fark "footer h4" seçimi. Bunun "footer &gt; h4" ten ne farkı var dersek, footer h4, footer içindeki tüm h4'leri seviyesine bakmadan seçerken, footer &gt; h4, footerin hemen altında yer alan h4 etiketlerini seçecek.

Ana sayfamızı düzenlemeyi nihayet bitirdik. Sonuçta elimizde profesyonel ve heryerde uyumlu çalışabilecek, estetik bir sayfa oluştu:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.22.58-AM.png"><img class="alignnone size-full wp-image-261" title="Screen Shot 2012-10-19 at 11.22.58 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.22.58-AM.png" height="380" width="628" /></a>

Bu da alt kısım:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.23.05-AM.png"><img class="alignnone size-full wp-image-262" title="Screen Shot 2012-10-19 at 11.23.05 AM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-19-at-11.23.05-AM.png" height="301" width="628" /></a>

Eğer buraya kadar örnekleri uygulayarak geldiyseniz, artık internet arayüzü yapmayı %85 - %90 oranında öğrendiniz demektir. Tebrik ediyorum.

Bir sonraki yazıda, sitemizin diğer bölümlerini oluşturacağız.

Dayanışmayla!
Meraklı Bilişimci