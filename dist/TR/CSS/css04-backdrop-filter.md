## CSS `backdrop-filter` Property

Merhaba arkadaşlar bazen sayfamızda bir takım içerikleri öne plana çıkartarak ziyaretçinin ilgisini istediğimiz bölümlere yönlendirmek isteriz. Dikkatinizi çektiyse özellikle e-ticaret sitelerinde sıkça yapılır ve böylece potansiyel müşteri kazanılmak istenir.

Bir sayfada içerikleri ön plana çıkarmanın değişik yöntemleri vardır. Mesela kontrasttan, metin özellikli içeriklerde tipografi farklılıklardan veya animasyon unsurlarından faydalanılabilir.

Bugün başka bir yöntemden daha bahsedeceğim Yazıda CSS3 specification'larından olan `backdrop-filter` property'sinine değineceğim.

Bir elementin arka planı (rengi veya imajı vs.) varsa ve arka plana sahip başka bir element üzerine yerleştirilmişse arka plan maniple edilerek elementin içeriği ön plana çıkartılabilir.

Daha iyi anlamak için aşağıdaki imaja bakalım.

![graphic-content](https://i.imgur.com/7yRfBne.png, "backdrop-filter örneği")

Mesele örnekte arka plan flu hale getirilmiş. Tahmin edeceğiniz üzere özellikle bir **_header_** component'i içerisinde bulunan buton sayesinde kullanıcı ile etkileşime geçmek için ziyadesiyle bu yöntemden faydalanılır. Yine örnekte "Show Me" butonu tıklandığında blur efekti kaldırılacak ve içerik görünecektir.

**💡 Aynı işlemi `filter` property'si ile de gerçekleştirebiliriz. Benzer işlemi yapsalar da birbirlerinden ayrılırlar. Bu konuya değineceğim.**

Temelde `backdrop-filter` property CSS metotlarını kullanır:

1. blur(): Elementin arka planı flu hale gelir.

2. brightness(): Elementin arka planının brightness seviyesini ayarlayabiliriz.

3. contrast(): Elementin arka planının contrast seviyesini ayarlayabiliriz.

4. drop-shadow(): Elementin arka planına shadow efekti verebiliriz.

5. grayscale(): Elementin arka planı gray scale tonda oluşturulur.

6. hue-rotate(): Elementin arka plan rengini renk tekerine göre döndürebiliriz. (Çarkı felek gibi düşünün.)

7. invert(): Elementin arka plan rengi ters çevrilir.

8. opacity(): Elementin arka planının opacity seviyesini ayarlayabiliriz.

9. sepia(): Elementin arka planına sepia özelliği ekleyebiliriz.

10. saturate(): Elementin arka planına saturasyon özelliği ekleyebiliriz.

`backdrop-fiter` property ikili veya daha fazla notasyonda kullanılabilir.

**Örnek**

```css
/* İki metot arasında white space koymak suretiyle ikili metodun özelliğini de kullanabiliriz. */
backdrop-filter: blur(10px) sepia(100%);
```

**➖ `backdrop-filter` ile `filter` Property Arasındaki Fark**

`backdrop-filter` property **elementin arka planına** uygulanırken, `filter` property **elementin içeriğine** uygulanır. Bu sebeple `filter` property genelde `<img>` özellikli HTML elementlerinde kullanılır.

Daha iyi anlamak için örneğe bakalım.

![backdrop-filter-vs-filter-property](https://i.stack.imgur.com/UkZqR.png, "backdrop-filter ile filter property arasındaki fark")

Sol taraftaki imaja `filter` property'si uygulanmışken, sağ taraftaki imaja `backdrop-filter` property'si uygulanmıştır.

`backdrop-filter` property majör tarayıcılarda 2022 yılının 3. çeyreğinden itibaren tam anlamıyla desteklenmesine rağmen **Chrome ve Firefox tarayıcılarında bir takım bug'lara neden olduğu rapor edilmiştir.**


`backdrop-filter` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                |
| ----------------------- | ----------------------------------------------------------- |
| Varsayılan değer:       | none                                                        |
| Inherit özeiiği:        | Hayır, parent elementten property değerleri miras alınamaz. |
| CSS animasyon özelliği: | Hayır, CSS animasyon property'lerini desteklemez.           |
| CSS versiyonu:          | CSS3                                                        |
| JavaScript syntax:      | **_object.style.backdropFilter="grayscale(100%)"_**         |


🖱️ Örnek çalışmaya [linke](https://codepen.io/eminaltan/pen/XWOpbeR) tıklayarak ulaşabilirsiniz arkadaşlar.


Umarım faydası olmuştur.

