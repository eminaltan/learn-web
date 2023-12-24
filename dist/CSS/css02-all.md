## CSS `all` Property

Merhaba arkadaşlar bu kısa yazıda CSS3 specification'larından olan `all` property'sinine değineceğim.

Bazen istediğimiz HTML elementlerinin tüm veya belirli property değerlerini başlangıç veya **_user agent_**[^1] gibi bir takım değerlere geri döndürmek isteyebiliriz. Bu durumda `all` property'si imdadımıza yetişir.

⚠️ `all` property'sinin kullanmadan önce CSS keyword'lerini anlamakta fayda olacaktır. Çünkü `all` property'sinde keyword'ler kullanılır.

Kısaca değinirsek bunlar:

1. `initial`: Bir property değerini **_CSS specification_**'da[^2] başlangıç değerine geri döndürür. Eğer property'nin CSS specification tablosunda değeri yoksa property değeri user agent style sheet değerine döndürülür. Bu durumda `initial` keyword `revert` görevi görür.

2. `revert`: Bir property değerinin user agent style sheet içerisindeki tanımlanmış değere geri döndürür.

3. `inherit`: **_Inheritable property'ler_**[^3] için bir property değerinin parent elementten **zorla inherit** edilmesi sağlanır.

4. `unset`: Duruma göre iki tür sonuç üretir. Bir property'nin hem parent hem de child HTML elementinde tanımlandığını ve child elementte `unset` keyword'u kullanıldığını düşünelim. Bu durumda `unset` keyword'u `inherit` keyword'u gibi çalışır ve child element, parent elementten ilgili property değerini miras alır. Şayet parent elementte property tanımlı değilse bu durumda child elementteki `unset` keyword `initial` gibi çalışır.

💡 Peki `all` keyword'unu nerelerde kullanırız? Bazen yazdığımız CSS stilleri gerek cascade gerek inheritance veya specificity sebebi ile karmaşık bir hale gelebilir. Bir property değerinin nereden miras alındığını bulmak veya debug işlemi yapmak zor hale gelebilir bu gibi durumlarda `all` property'sinden faydalanırız ve ilgili property değerini ilk baş başlangıç değerine sonrada istediğimiz değere set edip kullanabiliriz.

Buna ek olarak web sayfasını cross browser hale getirmek için user agent stillerini reset'lemek veya normalize etmek gerekir. Bir çok yöntem olmakla birlikte `all` property'si bu işlemleri daha kolay hale getirmek için kullanılabilir.

⚠️ `all` property'si `unicode-bidi` ve `direction` property'leri için kullanılamaz.


`all` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                |
| ----------------------- | ----------------------------------------------------------- |
| Varsayılan değer:       | Belirsiz.                                                   |
| Inherit özeiiği:        | Hayır, parent elementten property değerleri miras alınamaz. |
| CSS animasyon özelliği: | Hayır, CSS animasyon property'lerini desteklemez.           |
| CSS versiyonu:          | CSS3                                                        |
| JavaScript syntax:      | **_object.style.all_**                                      |


**Örnek**

```css
div {
  color: blue;
  background-color: orange;
  padding: 30px;
  font-size: 48px;
  font-family: sans-erif;

  /* all property değerini silin ve değişiklikleri gözlemleyin. */
  all: initial;
}
```

```html
<div>div elementi</div>
```

Umarım faydası olmuştur.


[^1]: Her browser CSS yorumlamak için varsayılan olarak kullandığı bir stil dosyası vardır buna user agent style sheet adı verilir.

[^2]: CSS official dokümanını ifade eder. Bu doküman property'ler hakkında bilgileri barındırır.

[^3]: CSS'de bazı property değerleri inherit edilemezler. Hangi property'nin inherit edilip/edilemeyeceğine dair listeye https://www.codecademy.com/resources/docs/css/inheritance adresinden ulaşabilirsiniz.
