## CSS `aspect-ratio` Property

Merhaba arkadaşlar yazıda CSS3 specification'larından olan `aspect-ratio` property'sinine değineceğim.

`aspect-ratio` property elementin genişliğine göre yükseklik oranını ayarlamak için kullanılan bir property'dir. Bazen bir elementin genişliğine göre yüksekliğini otomatik olarak ayarlamak isteyebiliriz. Bu durumda `aspect-ratio` property'sinden faydalanırız. CSS rule set içerisinde `width` ve `aspect-ratio` property'leri tanımlanmışsa elementin yüksekliği otomatik boyutlandırılır.

Temelde `aspect-ratio: width/height` şeklinde tanımlaması yapılır. **Buradaki `width` ve `height` ifadeleri orantısal genişlik ve yüksekliği ifade eder. CSS'deki `width` ve `height` property'leri ile karıştırmayın.**

Orantısal genişlik ve yükseklik kavramlarını daha iyi anlayabilmek için aşağıdaki imaja göz atalım.

![aspect-ration-image](https://mvix.com/wp-content/uploads/2020/08/Aspect-Ratio-4-and-3-with-16-and-9.png, "aspect-ratio")

Örneğin 4:3 şeklinde ifade edilen bir çözünürlük değeri için genişlik 4 birimden yükseklik ise 3 birimden oluşur.

Mesela aspect-ratio değeri 4:3 olan 1200px genişliğindeki bir monitor için yükseklik çözünürlüğü 900px olarak hesaplanır.

Bunu formüle dökecek olursak:

- `height`: Elementi yükseklik değerini
- `width`: Elementin genişlik değerini
- `w`: `aspect-ratio` property'de kullanacağımız orantısal genişlik değerini
- `h`: `aspect-ratio` property'de kullanacağımız orantısal yükseklik değerini

ifade ettiğini düşünelim. Bu durumda elementin `height` property'sini hesaplayan formül **_height=(width/w)xh_** şeklinde olacaktır. Yani örneğe göre `height = (1200px/4)*3` formülünden `height` değeri 900px olarak hesaplanır.

Yazıyı oluşturduğum sırada majör browser'lar 2021 yılının 4.çeyreğinden beri `aspect-ratio` property'sini destekliyorlar.

**💡 Nerede kullanılır diye düşünürsek mesela bir siteye fotoğraf yükleyip fotoğrafın boyutunu çözünürlük değerine göre interaktif şekilde boyutlandırmak için kullanılabilir.**


`aspect-ratio` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                |
| ----------------------- | ----------------------------------------------------------- |
| Varsayılan değer:       | auto                                                        |
| Inherit özeiiği:        | Hayır, parent elementten property değerleri miras alınamaz. |
| CSS animasyon özelliği: | Evet, CSS animasyon property'lerini destekler.              |
| CSS versiyonu:          | CSS3                                                        |
| JavaScript syntax:      | **_object.style.aspectRatio="4/3"_**                        |


🖱️ Örnek çalışmaya [linke](https://codepen.io/eminaltan/pen/dyaMjRN) tıklayarak ulaşabilirsiniz arkadaşlar.


Umarım faydası olmuştur.

