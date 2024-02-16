# JavaScript'e Giriş<a id='toc0_'></a>

Bu kılavuz JavaScript öğrenmek isteyen arkadaşlar için hazırlanmıştır. JavaScript'in ne zaman veya hangi amaçla ortaya çıktığı gibi bilgileri es geçiyorum. Muhtemelen bunları araştırmışsınızdır. Bana kalırsa işin felsefesini öğrenmekte fayda var benzer bilgilere kılavuzda yer vermeyeceğim.

Kılavuz temel HTML bilgisi gerektirir.

Yazının bu bölümünde JavaScript'e giriş yapacağız ve JavaScript'in yapısını inceleyeceğiz.

Yazıda:

- [`<script>` Elementi](#toc1_1_)
- [JavaScript Kullanım Şekilleri](#toc1_2_)
- [JavaScript Çıktıları](#toc1_3_)
  - [`innerHTML` Property](#toc1_3_1_)
  - [`document.write()` Metodunun Kullanımı](#toc1_3_2_)
  - [`window.alert()` Metodu](#toc1_3_3_)
  - [`console.log()` Metodu](#toc1_3_4_)
  - [JavaScript'te Print Özelliği](#toc1_3_5_)
- [Özet](#toc1_4_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of this article please visit [this link](js01-introduction.md).

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[`<script>` Elementi](#toc0_)

JavaScript kodları `<script></script>` elementleri arasına yerleştirilir.

**💡 Eski tarayıcıların JavaScript kodlarını yorumlaması için `type` attribute'un tanımlı olması gerekir. Bu bağlamda `<script type="text/javascript">` gibi bir ifade ile karşılaştığınızda web sayfasının eski tarayıcılar için hazırlandığını anlayabilirsiniz. Modern tarayıcılarda `type` attribute'un tanımlı olmasına gerek yoktur.**

JavaScript kodları `<head></head>` veya `<body></body>` elementleri arasına yerleştirilir.

**Örnek**

```html
<!DOCTYPE html>
<html>
  <head>
    <script>
      /* Örnekte JavaScript kodları <head></head> elementleri arasına yerleştirilmiş */
      console.log("test");
    </script>
  </head>
  <body>
    <h2>JavaScript Örneği</h2>
  </body>
</html>

<!DOCTYPE html>
<html>
  <head>
    <body>
      <script>
        /* Örnekte JavaScript kodları <body></body> elementleri arasına yerleştirilmiş */
        console.log("test");
      </script>
      <h2>JavaScript Örneği</h2>
    </body>
  </head>
</html>
```

**💡 JavaScript kodlarının `</body>` tag'ına yakın olması kodların daha hızlı yorumlanması ve çalışmasını sağlar.**

**Örnek**

```html
<!DOCTYPE html>
<html>
  <head>
    <body>
      <h2>JavaScript Örneği</h2>
      <script>
        /* JavaScript kodları </body> tag'ına yakın olması sebebi ile daha hızlı çalışacaktır. */
        console.log("test");
      </script>
    </body>
  </head>
</html>
```

## <a id='toc1_2_'></a>[JavaScript Kullanım Şekilleri](#toc0_)

JavaScript kodlarını `<script></script>` elementleri arasında kullanabileceğimiz gibi harici bir dosyadaki JavaScript kodlarını da kullanabiliriz.

**Harici JavaScript kodlarını kullanmak bize bir takım avantajlar sağlar:**

- HTML ve JavaScript kodları birbirinden ayrılacağı için dokümanın okunması, anlaşılması ve yönetilmesi kolaylaşır.

- Aynı kodları başka sayfalarda da kullanabiliriz. Böylece aynı kodları tekrar tekrar yazmamış oluruz. Buna **_DRY_**[^1] prensibi adı verilir.

- JavaScript kodları cache'leneceği için sayfanın hızlı şekilde yüklenilmesi sağlanır.

Aşağıdaki örnekte harici JavaScript dosyalarının web sayfasına yüklenilmesi görülüyor.

**Örnek**

```javascript
<script src="script1.js"></script>
<script src="script2.js"></script>
```

## <a id='toc1_3_'></a>[JavaScript Çıktıları](#toc0_)

**JavaScript'te çıktı almak için 4 yöntem kullanılır:**

- HTML elementinin içerisine çıktı almak için `innerHTML` property.

- HTML dokümanı içerisinde çıktı almak için `document.write()` metodu.

- Mesaj çıktısı alabilmek için `window.alert()` metodu.

- Konsolda kullanabilmek için `console.log()` metodu.

Bunlara yüzeysel bakalım, süreç içerisinde detaylara yer vereceğim.

### <a id='toc1_3_1_'></a>[`innerHTML` Property](#toc0_)

Bazen yaptığımız bir işlemin sonucunu HTML elementinin içerisinde çıktı olarak kullanmak isteyebiliriz. Böyle durumlarda genel olarak `innerHTML` property'sini kullanırız.

**Örnek**

```html
<!DOCTYPE html>
<html>
  <body>
    <p id="content"></p>
    <script>
      /* Örnekte #content id'sini barındıran HTML elementi bulunacak ve içerisine "test" ifadesi yazdırılacaktır. */
      document.getElementById("content").innerHTML = "test";
    </script>
  </body>
</html>
```

### <a id='toc1_3_2_'></a>[`document.write()` Metodunun Kullanımı](#toc0_)

`document.write()` metodu genelde test amaçlı kullanılır.

**❗ HTML sayfasının yüklenilmesinin ardından `document.write()` metodunun başka bir metot ile çağrılması durumunda sayfa içeriği silinir.**

Aşağıdaki örnekte HTML sayfasının içeriği **silinir ve "Test" string'i doküman içerisinde kullanılır.**

**Örnek**

```html
<!DOCTYPE html>
<html>
  <body>
    <p>onClick HTML event handler ile document.write() metodu çağrılıyor.</p>

    <!-- Buton tıklanıldığında document.write() metodu çalışacaktır. -->
    <button
      type="button"
      onclick="document.write(`Test`)"
    >
      Tıkla
    </button>
  </body>
</html>
```

Aşağıdaki örnekte HTML sayfasının içeriği silinmez.

**Örnek**

```html
<!DOCTYPE html>
<html>
  <body>
    <p>
      Doküman içeriği silinmeyecektir çünkü document.write() metodu çağrılmıyor.
    </p>
    <script>
      document.write("Test");
    </script>
  </body>
</html>
```

### <a id='toc1_3_3_'></a>[`window.alert()` Metodu](#toc0_)

Bazen Windows'daki gibi mesaj kutuları oluşturmak isteyebiliriz. Bu durumda `window.alert()` metodundan faydalanılır.

**⚠️ JavaScript'te `window` keyword'ü _global_ scope nesnesini ifade eder. Bunun anlamı JavaScript'te tanımlanan tüm variable'lar, property'ler ve metotlar varsayılan olarak `window` nesnesidir. `window` keyword'ü opsiyondur. Yani kullanımda es geçilebilir.**

**Örnek**

```javascript
/* Her iki statement da aynı anlama gelir. */
window.alert("Test");

alert("Test");
```

### <a id='toc1_3_4_'></a>[`console.log()` Metodu](#toc0_)

`console.log()` metodu genelde debug işlemlerinde kullanılır. JavaScript konsolunda çıktı almak için bu metodu kullanılırız. Konsola erişmek için tarayıcının inspector'unu kullanabiliriz.

![Console](https://wd.imgix.net/image/admin/ET1JJFtUIXvaoPCGQ94C.png?auto=format, "Şeklide tarayıcı konsolu görünüyor.")

**Örnek**


```javascript

/* Kod, konsola Test string'ini yazdıracaktır. */
console.log("Test");
```

    Test

### <a id='toc1_3_5_'></a>[JavaScript'te Print Özelliği](#toc0_)

JavaScript'te sadece `window.print()` metodu bulunmaktadır. Bu sayede tarayıcı ekranındaki içerik hard copy veya soft copy olarak çıktı alınır.

**Örnek**

```html
<!DOCTYPE html>
<html>
  <body>
    <!-- Tarayıcıdan içeriğini çıktı olarak almamıza yardımcı olur. -->
    <button onclick="window.print()">Ekranı yazdır</button>
  </body>
</html>
```

## <a id='toc1_4_'></a>[Özet](#toc0_)

Bu bölümde JavaScript'te kısaca giriş yapmış olduk. JavaScript kodlarının kullanımına, performansı etkileyen faktörlere ve debug işlemlerinde kullanılan bir takım JavaScript metotlarına değindik.

[^1]: DRY Don't Repeat Yourself'in kısaltması olup aynı kodları tekrar tekrar yazmamayı amaçlayan bir yaklaşımdır.
