## CSS `block-size` Property

Merhaba arkadaşlar bugün CSS3 property'lerinden olan `block-size` property'sine değineceğim.

Giriş yapmadan önce **_block direction_** terimini anlamamız gerekiyor.

Metin içeriği olan her HTML elementinin yazım yönü vardır. Yazım yönü İngilizce gibi dillerde yukarıdan aşağıya ve sağdan sola şeklinde oluşturulur. Aslında bu bizim gündelik hayatta kağıda yazı yazarken kullandığımız pattern'dir de. Bir paragrafı soldan sağa ve yukarıdan aşağıya doğru yazarız. Yukarıdan aşağıya ifadesi burada block direction terimini ifade eder. Yeri gelmişken soldan sağa ise **_inline direction_** terimini ifade eder. 

block direction terimini açıkladıktan sonra artık `block-size` property'sinin ne işe yaradığına değinebiliriz. 

Bir HTML elementinin block direction'daki boyutunu `block-size` property'si ile belirleyebiliriz. Bir element için `block-size` property'sini kullandığımızda boyutu yukarından aşağı doğru olacaktır yani elementin yüksekliğine etki edecektir. 

"Elementin boyutunu `height` property'si ile değiştiriyorduk. `block-size` property'sininin `height` property'sinden farkı ne?" şeklinde aklınıza bir soru gelebilir.

**➖ `block-size` ile `height` Arasındaki Fark**

**`block-size` property'si `writing-mode` property'sinin kullanımına bağlı olarak farklı etki gösterir arkadaşlar. `block-size` property'si normalde elementin yüksekliğine etki ederken `writing-mode:vertical-tb` şeklinde yapılan bir deklarasyonda `block-size` property'si elementin genişliğine etki eder.**

Aklınıza `writing-mode` property'sinin ne işe yaradığına dair soru gelebilir. Kısaca buna da değinelim. 

`writing-mode` property ile bir elementin yazım yönünü ayarlarız. Varsayılan olarak değeri `horizontal-tb`'dir.Yani varsayılan durumda bir elementin içeriği yatay eksende ve yukarıdan aşağı şeklinde oluşturulur. Söz gelimi `writing-mode` property'sinin değeri `vertical-tb` olduğunda elementin içeriği dikey eksende yukarıdan aşağı şeklinde oluşturulur. Örneğin İngilizce ve Çince içerikli bir sitemiz var. Çince'yi seçtiğimizde metin içerikli ögelerin dikey eksende oluşturulması gerekir. Bu durumda `writing-mode` property'sini kullanabiliriz.

Aşağıdaki imajlarda `writing-mode` property'sinin kullanım durumuna `block-size` property'sinin ne şekilde etkilendiğini görebiliriz.

![horizontal mode](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flow_layout/Block_and_inline_layout_in_normal_flow/mdn-horizontal.png)

`writing-mode:horizontal-tb`

![vertical mode](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flow_layout/Block_and_inline_layout_in_normal_flow/mdn-vertical.png)

`writing-mode:vertical-lr`

**💡 Peki bu property'i nerede kullanabiliriz şeklinde bir soru aklınıza gelebilir arkadaşlar. `block-size` property'yi genişliği veya yüksekliği yazım yönüne bağlı olmasını istediğimiz elementlerdsadas için kullanabiliriz diye düşünüyorum.** 

**⚠️ `width` veya `height` property'lerini kullanmamız durumunda `block-size` property'si geçersiz hale gelir.**




`block-size` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                |
|-------------------------|-------------------------------------------------------------|
| Varsayılan değer:       | auto                                                        |
| Inherit özeiiği:        | Hayır, parent elementten property değerleri miras alınamaz. |
| CSS animasyon özelliği: | Evet, CSS animasyon property'lerini destekler.              |
| CSS versiyonu:          | CSS3                                                        |
| JavaScript syntax:      | **_object.style.blockSize="100px"_**                        |


🖱️ Örnek çalışmaya [linke](https://codepen.io/eminaltan/pen/mdvxgLM) tıklayarak ulaşabilirsiniz arkadaşlar.


Umarım faydası olmuştur.

