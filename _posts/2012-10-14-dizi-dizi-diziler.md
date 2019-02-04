---
ID: 153
post_title: Dizi dizi diziler
author: Midori Kocak
post_excerpt: ""
layout: post
permalink: >
  https://www.meraklibilisimci.com/dizi-dizi-diziler/
published: true
post_date: 2012-10-14 01:14:43
---
Daha önceki örneğimizde dizilerden bahsetmiştik ancak dizilere daha ayrıntılı bir şekilde göz atmakta yarar ver. Diziyi şu şekilde tanımlar ve çağırırız:

<a href="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.06-PM.png"><img class="alignnone size-full wp-image-145" title="Screen Shot 2012-10-13 at 10.04.06 PM" alt="" src="http://meraklibilisimci.com/wp-content/uploads/2018/10/Screen-Shot-2012-10-13-at-10.04.06-PM.png" height="104" width="599" /></a>

PHP'nin çok güçlü olduğu alanlardan bir tanesi de dizi. Dizilerin elemanlarına istediğimiz anahtar değerlerini de verebiliriz mesela:

$anahtarliDizi = array('anahtar1'=&gt;'deger1','anahtar2'=&gt;'deger2');

bu dizinin elemanına da aşağıdaki şekilde kolayca erişebiliriz.

$eleman = $anahtarliDizi['anahtar1']; // Bu ifade bize deger1 metnini döndürecektir.

Bununla birlikte matris oluşturmamıza yarayan çok boyutlu diziler de tanımlayabiliriz.

$dizi[0][5] = 24;

Dizilerle ilgili ek detaylar da bunlar. Bir sonraki örneğimizde PHP'nin en zevkli konusu olan from ile veri girişi konusuna dalacağız.

Dayanışmayla!
Meraklı Bilişimci