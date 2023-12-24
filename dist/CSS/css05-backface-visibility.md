## CSS `backface-visibility` Property

Merhaba arkadaşlar bugün CSS3 property'lerinden olan `backface-visibility` property'sine değineceğim.

`backface-visibility` property elementin arka tarafı döndürüldüğü sırada elementin arka kısmının ziyaretçi tarafından görünüp/görünmeyeceğini belirlemek için kullanılan bir
property'dir. Bu nedenle `backface-visibility` genellikle 2D veya 3D CSS veya JavaScript animasyonlarında kullanılır.

**⚠️ Property'nin varsayılan değeri `visible` olması sebebi ile CSS veya JavaScript ile oluşturduğumuz 2D/3D animasyonlarında elementin arka tarafı görülecektir. Elementin arka kısmı, ön kısmında bulunan içeriğin aynalaması şeklinde ile oluşturulur.**

Majör tarayıcılar 2022 yılının 1.çeyreğinden itibaren `backface-visibility` property'i desteklemektedirler.


`backface-visibility` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                |
| ----------------------- | ----------------------------------------------------------- |
| Varsayılan değer:       | visible                                                     |
| Inherit özeiiği:        | Hayır, parent elementten property değerleri miras alınamaz. |
| CSS animasyon özelliği: | Hayır, CSS animasyon property'lerini desteklemez.           |
| CSS versiyonu:          | CSS3                                                        |
| JavaScript syntax:      | **_object.style.backfaceVisibility="hidden"_**              |


🖱️ Örnek çalışmaya [linke](https://codepen.io/eminaltan/pen/yLZPpVN) tıklayarak ulaşabilirsiniz arkadaşlar.


Umarım faydası olmuştur.

