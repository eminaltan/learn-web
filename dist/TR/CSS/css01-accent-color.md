## CSS `accent-color` Property

Merhaba arkadaşlar bu kısa yazıda CSS4 specification'larından olan `accent-color` property'sinine değineceğim.

Bazen **_HTML form elementlerini_**[^1] web sayfamıza göre biçimlendirmek isteyebiliriz. Bu durumda `accent-color` property bu işlemi gerçekleştirmek için alternatif bir yöntem olabilir. Bu yazıyı yazdığım sırada `accent-color` property Global olarak tarayıcılar tarafından 2022 yılının 3.çeyreğinden beri %91 oranında desteklenmektedir.

⚠️ `accent-color` property şimdilik aşağıdaki türdeki HTML form elementlerinde kullanılabilir:

1. `<input type="checkbox">`

2. `<input type="radio">`

3. `<input type="range">`

4. `<progress>`


`accent-color` property karakteristik özelliklerini incelersek:

| **Özellik**             | **Açıklama**                                                 |
| ----------------------- | ------------------------------------------------------------ |
| Varsayılan değer:       | `auto`                                                       |
| Inherit özelliği:       | Evet, parent elementten property değerleri miras alınabilir. |
| CSS animasyon özelliği: | Hayır, CSS animasyon property'lerini desteklemez.            |
| CSS versiyonu:          | CSS4                                                         |
| JavaScript syntax:      | **_object.style.accentColor_**                               |


**Örnek**

```css
/* Tipi checkbox olan <input> elementinin rengini turuncu yapacaktır. */
input[type="checkbox"] {
  accent-color: orange;
}
```

```html
<label>
  <input type="checkbox" />
  Checkbox'u seçtiğinizde kutunun içerisi turuncu olacaktır.
</label>
```
Bence web sayfamızdaki form elementlerinin ziyaretçinin temasını biçimlendirmek için kullanabiliriz. 

🖱️ [Aklınıza daha iyi oturması için isterseniz linki inceleyebilirsiniz.](https://codepen.io/eminaltan/pen/dywdKMX)  

Umarım faydası olmuştur.


[^1]: HTML form elementleri `<input>, <select>, <option>, <label>` gibi yani kısaca form içerisinde kullandığımız HTML elementlerinin gruplandırılmasından oluşur.
