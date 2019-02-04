---
ID: 659
post_title: >
  SQL ile bişiler yapmaya devam. SQL-4
  Farklı tablolardan veri çekmek ve
  birleştirmek.
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/sql-ile-bisiler-yapmaya-devam-sql-4-farkli-tablolardan-veri-cekmek-ve-birlestirmek/
published: true
post_date: 2014-08-09 23:03:48
---
Geçen yazıdan kalan işlerimize bi göz atalım neler vardı?
<ol>
	<li>Yazılara eklenecek dosyaları yönetmek. Silmek ve düzenlemek.</li>
	<li>Tüm yazıların başlıklarının olduğu bir liste göstermek.</li>
	<li>Kategori eklemek, silmek, düzenlemek.</li>
	<li>Kategori içindeki yazıları göstermek</li>
	<li>Ayrıca yazı başlıklarını gösterirken, sayfalama yapmak, her sayfada 20 yazı göstermek, 2. sayfada bir sonraki 20 yazıyı yani 20 ile 40 arası yazıları göstermek</li>
	<li>Arama yapmak</li>
</ol>
1. maddedeki ekleme silme düzenleme kısımlarını siz yapabilirsiniz. Tüm yazı başlıklarının olduğu liste işi de çok kolay. SELECT posts.title FROM posts; dediğiniz anda o iş tamam. 3. maddedeki de ekleme düzenleme silme. 4. maddedeki iş biraz değişik örneğin SELECT * from posts WHERE category_id=3 diyebiliriz. Ancak istediğimiz kategorinin id'sini bilmezsek ve sadece ismini biliyorsak ne olacak? Bu durumda önce isim girip id öğreneceğiz, ve bu id bilgisini kullanıp yazılar tablosunda sorgu yapacağız. Bunu yapabilmek için üç yöntemimiz var. Birincisi Birleştirme işlemi, diğeri iç içe sorgu, üçüncüsü ise tek sorguda birden fazla alan kullanmak.

Birleştirme yani basit inner JOIN işlemine bir göz atalım:
<pre>SELECT *
FROM posts
INNER JOIN categories
ON posts.category_id=categories.id WHERE categories.title = 'PHP'
</pre>
Bunu sql olarak girdiğimizde şöyle bir sonuçla karşılaşacağız:

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-10-at-01.08.20.png"><img class="alignnone size-full wp-image-663" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-10-at-01.08.20.png" alt="Screen Shot 2014-08-10 at 01.08.20" width="474" height="199" /></a>

Join işlemleri kullanışlıdır ancak eziyettir. Bunun yerine kullanımı daha kolay olan iç içe sorguyu da öneririm. Ancak şöyle bir durum var. İç içe sorgu yaptığımızda, sonuç döngüsünde kategori ismi ve id'si çıkmayacak. Aralarındaki tek fark bu. Ayrıca RIGHT ve LEFT yani sağdan ve soldan birleştirme işlemleri vardır ki, onları da araştırmayı sizin merakınıza bırakıyorum.
<pre>SELECT * FROM posts WHERE category_id IN (SELECT id FROM categories WHERE title='PHP')
</pre>
Sonuç olarak gelen sorgu cevabı da şu şekilde;

<a href="https://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-10-at-01.08.20.png"><img class="alignnone size-full wp-image-663" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/screen-shot-2014-08-10-at-01.08.20.png" alt="Screen Shot 2014-08-10 at 01.08.20" width="474" height="199" /></a>

Dikkat edeceğiniz gibi, sonuçlarda kategori bilgisi yok. Ve iki sorgu da sonuç olarak aynı süreyi almış.

Bir diğer yöntem ise aynı sorgu içerisinde birden fazla alan kullanmak, verdiği sonuç JOIN işlemiyle aynı, yani her iki tablonun verileri birleşip dönecek:

<pre>
SELECT * FROM posts,categories WHERE posts.category_id=categories.id AND categories.title='PHP'
</pre>

İşte aynı işlemi yapacileceğimiz üç farklı yöntem. Mantığını anladığımız sürece, ihtiyaç duyduğumuz yerde, istediğimizi kullanabiliriz.

Şimdilik bu kadar. Kalan adımları da yeni yazılarda irdeleyeceğiz.