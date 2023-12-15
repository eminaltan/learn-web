## CSS `box-reflect` Property

Merhaba arkadaşlar bugün CSS3 property'lerinden olan `box-reflect` property'sine değineceğim.

Eskiden Photoshop'da tasarlanan web arayüzündeki imajların yansımalarını HTML'de oluşturmak için öncelikle yansımaları Photoshop'da slice tool vb. araçlar kullanılarak export ediliyor sonrasında JS kütüphaneleri veya CSS media query'leri ile birlikte HTML'de oluşturuyorduk. Responsive arayüz oluşturmak için aynı imajın farklı boyutlarındaki yansımalarında bu işlemi tekrarlardık. Tahmin edeceğiniz gibi bu işlem çok zaman alıyordu bir de buna iş bitmişken müşterinin imajları değiştirmek istemesi deyim yerindeyse pişmiş aşa su katıyor ve tüm işlemlere yeniden başlamak zorunda kalıyorduk. Bu da işi sıkıcı hale getiriyordu. Bu noktada Photoshop action'ları her ne kadar işimizi kolaylaştırsa da sistem kaynaklarını çok fazla tüketiyor zaman zaman PC'nin kilitlenmesine neden oluyordu.

Şimdilerde `box-reflect` property'si ile bu sorunu aşabilir durumdayız. Bu sayede bir imaja veya HTML elementine ait yansımayı dinamik olarak oluşturabiliriz. Böylece her imajın boyutu için tek tek çalışma yapmamıza gerek kalmaz ve zamandan kazanırız. Müşteri sonradan imajları değiştirmek mi istedi? Sorun değil `box-reflect` dinamik olarak yansımaları oluşturacağı için sadece imajı değiştirmemiz yeterli olacaktır.

**⚠️ `box-reflect` property'si yazıyı oluşturduğum tarihte henüz standart halini almadığı için _webkit_ prefix'ile kullanmamız gerekiyor.**

`box-reflect` property'si genelde tekli notasyon biçiminde kullanılır. Buna rağmen 3'lü notasyona da sahip olabilir. Şimdi de kullanım şekillerine göz atalım.

### `box-reflect` Property'sinde Notasyonların Kullanımı

### Tekli Notasyon Kullanımı

`box-reflect` property'sinde tek notasyon kullanılmışsa yansımınanın hangi yönde oluşacağını ifade eder.Notasyon 5 değerden birine sahip olabilir. Bunlar `none`, `above`, `below`, `right` veya `left` değerlerinden biridir. `box-reflect` property'sinin varsayılan değeri `none`'dur bu durumdaki bir HTML elementi için yasıma oluşturulmaz.

**Ör.:**

```css
div {
  /* <div> elementi için yasıma aşağı yönde oluşturulacaktır. */
  -webkit-box-reflect: below;
}
```

### İkili Notasyon Kullanımı

Şayet `box-reflect` property'si 2.notasyona sahip ise bu durumda 2.notasyon yansıma ile imaj arasındaki boşluğu ifade eder.

Boşluğu belirlemek için CSS unit'lerinden herhangi biri kullanılabilir.

**Ör.:**

```css
div {
  /* <div> elementi ile yansıması arasında 15px'lik bir mesafe olacaktır. */
  -webkit-box-reflect: below 15px;
}
```

### Üçlü Notasyon Kullanımı

`box-reflect` property'si içerisinde CSS gradient fonksiyonlarını kullanabiliriz. Böylece yansıma içerisinde geçişlerin yumuşak ve sert olmasını sağlayabiliriz. Şayet `box-reflect` property'si 3.notasyona sahip ise bu durumda 3.notasyon gradient fonksiyonunu ifade eder.

**Ör.:**

```css
div {
  /* <div> elementinin yansıması yukarından aşağı yönde ve opacity miktarı 0%'dan başlayarak 40%'a kadar oluşturulacaktır. */
  -webkit-box-reflect: below 15px linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.4));
}
```

`box-reflect` property'si Firefox hariç tüm majör tarayıcılar tarafından 2020 yılının 1.çeyreğinden itibaren desteklenmektedir.

`box-reflect` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                |
| ----------------------- | ----------------------------------------------------------- |
| Varsayılan değer:       | none                                                        |
| Inherit özelliği:       | Hayır, parent elementten property değerleri miras alınamaz. |
| CSS animasyon özelliği: | Hayır, CSS animasyon property'lerini desteklemez.           |
| CSS versiyonu:          | CSS3                                                        |
| JavaScript syntax:      | **_object.style.webkitBoxReflect="below"_**                 |

🖱️ Örnek çalışmaya [linke](https://codepen.io/eminaltan/details/jOdpdgR) tıklayarak ulaşabilirsiniz arkadaşlar.

Umarım faydası olmuştur.
