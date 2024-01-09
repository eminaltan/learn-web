# Javascript Error Handling<a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'te **_Error Handling_** kavramına; `try`, `catch`, `throw` ve `finally` keyword'lerini inceleyeceğiz.

Yazıda:

- [JavaScript Error Handling Kavramı](#toc1_1_)
- [`try` ve `catch` Keywords](#toc1_2_)
  - [JavaScript `Error` Nesnesi ve Property'leri](#toc1_2_1_)
    - [`RangeError`](#toc1_2_1_1_)
    - [`ReferenceError`](#toc1_2_1_2_)
    - [`SyntaxError`](#toc1_2_1_3_)
    - [`TypeError`](#toc1_2_1_4_)
    - [`URIError`](#toc1_2_1_5_)
- [`throw` Keyword](#toc1_3_)
- [finally Keyword](#toc1_4_)
- [Özet](#toc1_5_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of article please [visit](js22-try-catch.md) this link.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript Error Handling Kavramı](#toc0_)

JavaScript'de "error handling" (hata işleme) terimi, bir programın çalışma sırasında oluşan hataları tanımlama, ele alma ve yönetme sürecini ifade eder. Hatalar, bir uygulamanın beklenmeyen durumlarla karşılaştığı zaman ortaya çıkar. Bu hatalar, kullanıcı giriş hataları, ağ bağlantı sorunları, dosya bulunamama gibi durumları içerebilir.

Error handling sayesinde kullanıcıya anlamlı hata mesajları gösterilir ve hataları daha iyi anlamaları sağlanabilir.

JavaScript'te error handling genellikle `try`, `catch`, `finally`, ve `throw` anahtar kelimelerini içeren bir yapı ile gerçekleştirilir.

Şimdide bu keyword'lere değinelim.

## <a id='toc1_2_'></a>[`try` ve `catch` Keywords](#toc0_)

`try` ve `catch` keyword'leri birlikte kullanılır arkadaşlar. `try` bloğuna çalışmasını veya
kontrol edilmesini istediğimiz kodları yazarız. Program herhangi bir sorunla karşılaşmadığı sürece `try` bloğu içerisindeki kodlar çalışacaktır.

`catch` bloğuna ise bir hata oluşması durumunda çalıştırılacak kodlar yazılır. Genelde bloğun içeriği hata mesajı hakkında kullanıcıya bilgi verir.

**Örnek**

Yukarıda bir `try-catch` bloğu örneği görüyoruz. Hata olmadığı sürece `try` bloğu içerisindeki kodlar çalıştırılır.

`try` bloğu içerisindeki kodlarımızda bir hata oluşması durumunda `try` bloğunun çalışması duracaktır ve `catch` bloğu içerisindeki kodlar çalıştırılmaya başlanacaktır. İşlemin sonunda kullanıcıya bir hata mesajı döndürülecektir.

**Örnek**

```javascript
try {
  let num = 0;

  // x değişkenini tanımlamadığımız için "ReferenceError: x is not defined" hata mesajını alırız.
  num = num + x;
  console.log(`Sonuç:${num}`);
} catch (error) {
  console.log(error);
}
```

Yukarıda görüleceği üzere `x` değişkenini program içerisinde **tanımlamadık** fakat buna rağmen `num =  num + x` expression içerisinde `x` değişkenini kullandık. Bu durumda JavaScript `try` bloğu içerisindeki kodların çalışmasını sonlandıracak , `catch` bloğu içerisindeki kodları çalıştırılacak ve "ReferenceError: x is not defined" mesajını konsola yazdıracaktır.

### <a id='toc1_2_1_'></a>[JavaScript `Error` Nesnesi ve Property'leri](#toc0_)

JavaScript'te ön tanımlı hata mesajları `Error` nesnesi içerinde tanımlanmıştır. Bir önceki örnekte hata mesajını oluşturmak için JavaScript içerisindeki ön tanımlı hata mesajlarından `ReferenceError` kullanıldı. `ReferenceError` değeri ile birlikte JavaScript içerisinde 6 tane daha değer bulunur.

Bunları listelersek:

| **Error Name**   | **Description**                                               |
| ---------------- | ------------------------------------------------------------- |
| `EvalError`      | Fonksiyonundan kaynaklanan bir hata olduğunu ifade eder.      |
| `RangeError`     | Sayısal bir değerin limit dışında kaldığını belirtir.         |
| `ReferenceError` | Bir değer için referansın geçerli olmadığı anlamına gelir.    |
| `SyntaxError`    | Syntax hatası oluştuğu anlamına gelir.                        |
| `TypeError`      | Bir değerin beklenen türde olmadığı durumu temsil eder        |
| `URIError`       | URL adresinin geçerli olmadığını ifade etmek için kullanılır. |

Şimdi de bu değerlere değinelim.

**❗ `EvalError` deprecated olmuştur. Modern JavaScript dilinde pek kullanılmaz. Bu nedenden ötürü `EvalError` değerini es geçiyorum.**

#### <a id='toc1_2_1_1_'></a>[`RangeError`](#toc0_)

`RangeError` sayısal bir değerin belirli bir aralık dışında olduğunu ifade eder.

**Örnek**

```javascript
let num = 1;

try {
  /**
   * num değişkeni 500 hane hassasiyetinde biçimlendirilmeye çalışılıyor, fakat bu mümkün olmadığı için catch
   * bloğu çalışacaktır. error.name property'si ile hata mesajının türünü konsola yazdırıyoruz.
   */
  num.toPrecision(500);
} catch (error) {
  console.log(error.name);
}
```

    RangeError

#### <a id='toc1_2_1_2_'></a>[`ReferenceError`](#toc0_)

`ReferenceError` bir değişken referansının geçerli olmadığı durumları ifade eder.

**Örnek**

```javascript
try {
  let num = 0;

  // x değişkenini tanımlamadığımız için ReferenceError mesajını alırız.
  num = num + x;
  console.log(`Sonuç:${num}`);
} catch (error) {
  console.log(error.name);
}
```

    ReferenceError

#### <a id='toc1_2_1_3_'></a>[`SyntaxError`](#toc0_)

Bir ifadenin söz dizimi eksik veya yanlış olduğu durumlarda `SyntaxError` hata mesajı ile karşılaşırız.

**Örnek**

```javascript
try {
  // eval metodu içerisinde argümanın hatalı olması sebebi ile "SyntaxError" hata mesajı ile karşılaşırız.
  let invalidCode = eval("2 +");
} catch (error) {
  console.log(error.name);
}
```

    SyntaxError

#### <a id='toc1_2_1_4_'></a>[`TypeError`](#toc0_)

Bir değişken için kullandığımız expression'un uygun olmaması durumunda `TypeError` hata mesajı ile karşılaşırız.

**Örnek**

```javascript
let num = 1;

try {
  // num değişkeni için toUpperCase() metodu kullanılamayacağı için TypeError hata mesajı alırız.
  num.toUpperCase();
} catch (error) {
  console.log(error.name);
}
```

    TypeError

#### <a id='toc1_2_1_5_'></a>[`URIError`](#toc0_)

Bir URL adresi içerisinde illegal karakterler bulunması durumunda `URIError` hata mesajı ile karşılaşırız.

**Örnek**

```javascript
try {
  // %%% karakterleri URL geçersiz olduğu için "URIError" hata mesajı ile karşılaşırız.
  decodeURI("%%%");
} catch (error) {
  console.log(error.name);
}
```

    URIError

Yukarıda belirtilen `Error` nesnesine ait property'lerin dışında Mozilla ve Microsoft'un belirlediği bir takım property'ler vardır.

**Bunlar:**

- fileName (Mozilla)

- lineNumber (Mozilla)

- columnNumber (Mozilla)

- stack (Mozilla)

- description (Microsoft)

- number (Microsoft)

**❗Yukarıdaki property'lerin kullanılması önerilmez. Çünkü bu property'lerın cross-browser desteği bulunmaz bu sebeple her tarayıcıda çalışmaz.**

## <a id='toc1_3_'></a>[`throw` Keyword](#toc0_)

Şimdiye kadar JavaScript içerisinde ön tanımlı `Error` nesnesine ait property'leri inceledik. Hata mesajlarını daha anlamlı hale getirmek için bazen geliştirici temelli hata mesajları oluşturmak isteyebiliriz bu durumda `throw` keyword'unu kullanırız.

**Örnek**

```javascript
let x;

try {
  // throw keyword'u ile geliştirici tanımlı bir hata mesajı oluşturduk.
  if (x === undefined) throw "x değeri tanımlı değil.";
} catch (error) {
  console.log(error);
}
```

    x değeri tanımlı değil.

Yukarıdaki örnekte `let x` statement'ı ile `undefined` veri tipine sahip `x` değişkeni tanımladık. `try` bloğunda `if` statement'ı yardımıyla `x` değişkenini veri tipini kontrol ettik ve `x` değişkenini veri tipi `undefined` olması durumunda `throw` keyword'unu kullanarak geliştirici tanımlı bir hata mesajı oluşturduk. Oluşturulan hata mesajını `catch` bloğundaki `error` parametresine geçirdik ve sonucu konsola yazdırdık.

Teknik anlamda bu işleme **_throw error_** veya **_throw exception_** adı verilir.

## <a id='toc1_4_'></a>[finally Keyword](#toc0_)

`finally` keyword'u ile `try-catch` bloğundan bağımsız olarak programımızın ek bir sonuç döndürmesini sağlayabiliriz. Genellikle, kaynakların serbest bırakılması veya temizlenmesi gibi işlemler bu blokta gerçekleştirilir.

Örneğin `try-catch` bloğu yardımıyla bir formun yanlış doldurulduğu durumda kullanıcıya hata mesajı verilmesini sağlayabilir ve `finally` keyword'u ile ilgili form elementinin içeriği tekrar kullanıma hazır hale getirmek için temizleyebiliriz.

**Örnek**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <link
      rel="stylesheet"
      href="test.css"
    />
    <title>try-catch-finally keywords of JavaScript Kitchen</title>

    <style>
      body {
        font-family: Arial, sans-serif;
      }

      form {
        width: 300px;
        margin: 20px;
      }

      label {
        display: block;
        margin-bottom: 5px;
      }

      input {
        width: 100%;
        padding: 5px;
        margin-bottom: 10px;
      }

      button {
        padding: 8px;
        background-color: #4caf50;
        color: #fff;
        border: none;
        cursor: pointer;
      }
    </style>
  </head>
  <body>
    <label for="inputField">Enter Your Text:</label>
    <input
      type="text"
      id="js-inputField"
      name="js-inputField"
      required
    />

    <button id="js-button">Send</button>

    <p id="js-message"></p>
    <script>
      const jsInputField = document.getElementById("js-inputField");
      const jsButton = document.getElementById("js-button");
      const jsMessage = document.getElementById("js-message");

      jsButton.addEventListener("click", () => {
        try {
          if (jsInputField.value.includes("pen")) {
            jsMessage.innerHTML = "'pen' string found in entered text.";
          } else {
            throw "Can't find the 'pen' string in the entered text.";
          }
        } catch (error) {
          jsMessage.innerHTML = error;
        } finally {
          // finally bloğunu silin ve formdaki text alanındaki durumu gözlemleyin.
          jsInputField.value = "";
        }
      });
    </script>
  </body>
</html>
```

Yukarıdaki kodları boş bir HTML sayfasına kopyalayın. İçeriğinde "pen" ifadesi geçen ve geçmeyen metinler için ayrı ayrı formu doldurun ve "Send" butonuna basarak form içeriğini gözlemleyin.

Aynı işemi `finally` bloğunu silerek gerçekleştirin ve farkı gözlemleyin.

**🖱️ Çalışan örneğe [linke](https://codepen.io/eminaltan/pen/vYPKWjQ) tıkayarak ulaşabilirsiniz.**

## <a id='toc1_5_'></a>[Özet](#toc0_)

JavaScript'te **error handling**, programın çalışma sırasında ortaya çıkabilecek hataları kontrol altına almak ve kullanıcıya anlamlı geri bildirimler sunmak için önemli bir konsepttir. `try`, `catch`, `finally`, ve `throw` anahtar kelimeleri bu süreçte kullanılır.

- `try` bloğu içindeki kodlar, hata olup olmadığına bakılmaksızın normal bir şekilde çalışır.

- `catch` bloğu, `try` bloğu içinde bir hata oluştuğunda çalışır ve hatayı ele alır. Kullanıcıya anlamlı bir hata mesajı göstermek için burada işlemler yapılır.

- `finally` bloğu, `try-catch` bloğundan bağımsız olarak her durumda çalışır. Genellikle, kaynakların serbest bırakılması veya temizlenmesi gibi işlemler bu blokta gerçekleştirilir.

Ayrıca, geliştiricilerin kendi özel hata mesajlarını oluşturmak için `throw` keyword'ünü kullanma yeteneği vardır. Bu, özellikle belirli koşullar altında programın akışını kontrol etmek ve hata mesajlarını özelleştirmek için kullanışlıdır.

JavaScript'te yaygın olarak karşılaşılan hata türleri arasında `RangeError`, `ReferenceError`, `SyntaxError`, `TypeError`, ve `URIError` bulunur. Her biri farklı durumları temsil eder ve programcılara hatanın türüne göre özel işlemler yapma olanağı sağlar.

**Sonuç olarak**, error handling, bir JavaScript uygulamasının güvenilirliğini artırmak ve kullanıcı deneyimini iyileştirmek adına önemli bir pratiktir. İyi bir error handling stratejisi, hataların etkilerini en aza indirir ve kullanıcılara anlamlı geri bildirimler sunar.
