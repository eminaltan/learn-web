# JavaScript Scope<a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'te **_scope_** kavramını inceleyeceğiz.

Yazıda:

- [JavaScript Scope Kavramı](#toc1_1_)
  - [Block Scope](#toc1_1_1_)
  - [Function Scope](#toc1_1_2_)
  - [Global Scope](#toc1_1_3_)
- [Local Scope](#toc1_2_)
- [Özet](#toc1_3_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of article please [visit](js23-scope-concept.md) this link.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript Scope Kavramı](#toc0_)

JavaScript'te **_scope_** kavramı bir değişkenin tanımladığı ve erişilebildiği alanı ifade eder. Bu alan bir döngü, koşul veya metottan oluşabilir.

Bir scope `{}` işaretleri arasında oluşturulur.

**Örnek**

```javascript
const x = 5;

if (x == 5) {
  // If koşulunda scope bu alanı ifade eder.
}

for (let i = 0; i < x; i++) {
  // for döngüsü için scope bu alanı ifade eder.
}

function myFunction() {
  // myFunction() fonksiyonu için scope bu alanı ifade eder.
  console.log(x);
}
```

**JavaScript'te 3 türde scope bulunur:**

- Block scope

- Function scope

- Global Scope

Şimdi de bu scope türlerini inceleyelim.

### <a id='toc1_1_1_'></a>[Block Scope](#toc0_)

2015'den (ES6) önce JavaScript'te 2 tür scope kavramı bulunmaktaydı bunlar **_global scope_** ve **_function scope_** kavramları idi. ES6 ile `let` ve `const` keyword'leri JavaScript'e entegre olmuştur. **Bu keyword'ler kullanılarak oluşturulan bir değişken bulunduğu scope dışından erişilemez ve kullanılamaz.** Bu ifade **_block scope_** kavramını oluşturur.

**❗Block scope'lar aynı zamanda local scope özelliklidir. Yani JavaScript, block scope içerisindeki kodları çalıştırmaya başladığında block scope içerisinde değişkenler bellekte tanımlanmaya başlanır ve JavaScript block scope içerisindeki çalışmayı sonlandırdığında block scope içerisindeki değişkenler bellekten silinir.**

**Örnek**

```javascript
{
  /**
   * {} işaretleri arası scope olarak ifade edilir. const veya let ile tanımlanan her değişken block scope
   * özelliğine sahiptir.
   */
  const studentName = "Betül";

  console.log(`studentName değişkeninin değeri:${studentName}`);
}
```

    studentName değişkeninin değeri:Betül

Yukarıdaki örnekte `studentName` block scope değişken özelliği taşır. Bu değişkene bulunduğu scope içerisinden erişilebilir ve kullanılabilir. Örnekte local scope içerisinde `studentName` değişkenin depoladığı değeri yazdırıyoruz.

Şayet değişkene bulunduğu scope dışarısından ulaşmak istersek hata mesajı ile karşılaşırız.

**Örnek**

```javascript
{
  const studentName = "Betül";
}

try {
  /**
   * studentName değişkenine bulunduğu scope'un dışından erişip kullanmaya çalışıyoruz. Erişemediğimiz için
   * catch mekanizması çalışacak ve hata mesajı konsola yazdırılacaktır.
   */
  console.log(`studentName değişkeninin değeri:${studentName}`);
} catch (error) {
  console.log(error.name + ":" + error.message);
}
```

    ReferenceError:studentName is not defined

Yukarıdaki örnekte `studentName` değişkenine bulunduğu scope dışarısından erişmeye ve kullanmaya çalıştık. Bu durumda JavaScript `studentName` değişkeninin tanımlanmadığını varsayacak ve "ReferenceError:studentName is not defined" hata mesajını geri döndürecektir.

**💡 Block scope'lar aynı isimdeki değişkene farklı türde veriler depolamamıza imkan tanır.**

**Örnek**

```javascript
{
  // 1.Scope
  const x = "Şenay";
  console.log(`x değişkeninin içeriği:${x}`);
}

{
  // 2.Scope
  const x = "279";
  console.log(`x değişkeninin içeriği:${x}`);
}
```

    x değişkeninin içeriği:Şenay
    x değişkeninin içeriği:279

Yukarıda görüleceği üzere 1.Scope içerisindeki `x` değişkeni ile 2.Scope içerisindeki `x` değişkeninin içeriği farklıdır.

### <a id='toc1_1_2_'></a>[Function Scope](#toc0_)

JavaScript'de bir değişkeni metot içerisinde tanımlayabiliriz. Bu durumdaki değişken sadece tanımlı olduğu metot içerisinde geçerli olur yani değişkene tanımlı olduğu metot dışarısından erişemeyiz.

**❗Function scope'lar aynı zamanda local scope özelliklidir. Yani JavaScript, function scope içerisindeki kodları çalıştırmaya başladığında function scope içerisinde değişkenler bellekte tanımlanmaya başlanır ve JavaScript function scope içerisindeki çalışmayı sonlandırdığında function scope içerisindeki değişkenler bellekten silinir.**

**⚠️ Normalde `var` keyword'ü kullanarak tanımlanan bir değişken global scope özelliğine sahiptir. Ancak bir metot içerisinde `var` keyword'ü kullanılarak tanımlanan değişken function scope özelliği taşır. Böyle bir değişkene tanımladığı metot dışarısından ulaşılamaz.**

**Örnek**

```javascript
function myFunction() {
  var studentName = "Şenay";

  console.log(`studentName değişkeninin değeri:${studentName}`);
}

myFunction();
```

    studentName değişkeninin değeri:Şenay

Yukarıdaki örnekte `studentName`, `var` keyword'ü kullanarak tanımlanmasına rağmen local scope özelliği taşır. Yani `studentName` değişkenine `myFunction()` dışarısından erişmeye çalıştığımızda hata mesajı alırız.

**Örnek**

```javascript
function myFunction() {
  var studentName = "Şenay";
}

try {
  // studentName değişkenine ulaşmaya çalışıyoruz.
  console.log(`studentName değişkeninin değeri:${studentName}`);
} catch (error) {
  console.log(error.name + ":" + error.message);
}
```

    ReferenceError:studentName is not defined

Yukarıda görüleceği üzere `studentName` değişkenine `myFunction()` dışından erişmeye çalıştığımızda "ReferenceError:studentName is not defined" hata mesajını aldık.

Function scope ile block scope arasındaki ayrım `var` keyword'ünun kullanım şeklidir. Function scope içerisinde `var` keyword'ü ile tanımlanan bir değişkene scope dışarısından erişilemez iken block scope içerisinde `var` keyword'ü ile tanımlanan değişkene scope dışarısından erişilebilir.

**Örnek**

```javascript
{
  // Block scope
  var carName = "Volvo";
}

function myFunction() {
  // Function scope
  var carModel = "S70";
}

// ✔️ carName block scope özellikli olması sebebi ile bulunduğu scope dışarısından erişilebilir.
console.log(`Aracın markası: ${carName}`);

// ❌ carModel function scope özellikli olması sebebi ile bulunduğu scope dışarısından erişilemez.
console.log(`Aracın modeli: ${carModel}`);
```

Yukarıdaki örnekte değişkenler `var` keyword'ü kullanılarak tanımlanmıştır. `carName` değişkenine scope dışarısından erişebilirken `carModel` değişkenine scope dışarısından erişilemez.

**⚠️ Bir değişken function scope içerisinde `var`, `let` veya `const` keyword'leri kullanılarak tanımlanması halinde bulunduğu scope içerisinden erişilemez hale gelir.**

**Örnek**

```javascript
function myFunction() {
  var carName = "Volvo"; // Function Scope
}

function myFunction() {
  let carName = "Volvo"; // Function Scope
}

function myFunction() {
  const carName = "Volvo"; // Function Scope
}
```

3 metot dışarısından da `carName` değişkenine ulaşılamaz.

**⚠️ Bir metodun parametreleri function scope özelliğine sahiptir.**

**Örnek**

```javascript
// myFunction() içerisinde tanımlanan param1 ve param2 değişkenleri function scope özelliklidir.
function myFunction(param1, param2) {
  console.log(`param1'in değeri = ${param1}`);
  console.log(`param2'nin değeri = ${param2}`);
}
```

### <a id='toc1_1_3_'></a>[Global Scope](#toc0_)

Bir değişken metodun dışında tanımlanması halinde global değişken özelliği kazanır. Değişkenin bulunduğu scope global scope olarak ifade edilir. Bu türdeki değişkene program içerisinde her yerden ulaşabiliriz.

**Bir değişken function scope haricinde** `var` keyword'ü kullanılarak tanımlandığında global değişken özelliği kazanır.

**Örnek**

```javascript
{
  var studentName = "Şenay";
}

console.log(`studentName değişkeninin değeri: ${studentName}`);
```

    studentName değişkeninin değeri: Şenay

Yukarıdaki örnekte `studentName`, `var` keyword'ü kullanılarak tanımlanmasından ötürü global değişken özelliği taşımaktadır. Bu değişkenin bulunduğu scope global scope olarak ifade edilir. **Aynı değişkeni bir metot içerisinde tanımlamış olsaydık function scope özelliği gösterecekti. Bu durumdaki değişken ise local scope özelliğine sahip olacaktı.**

Encapsulation yöntemiyle `let` veya `const` keyword'lerinden biri kullanılarak tanımlanan bir değişken bulunduğu scope içerisinde global değişken özelliği sergiler.

**Örnek**

```javascript
{
  // Ana scope
  const studentName = "Şenay";

  {
    // Alt scope
    console.log(`studentName değişkeninin değeri: ${studentName}`);
  }
}

/**
 * studentName değişkenine buradan erişim sağlayamayız. ReferenceError: studentName is not defined hatası ile
 * karşılaşırız. console.log kısmını comment out yapın ve sonucu gözlemleyin.
 */
// console.log(`studentName değişkeninin değeri: ${studentName}`);
```

    studentName değişkeninin değeri: Şenay

Yukarıda görüleceği üzere `studentName` ana scope içerisinde tanımlanmıştır. Bu durumda alt scope(lar) için `studentName` değişkeni global değişken özelliği kazanacak ve alt scope'lar içerisinden ulaşılabilir hale gelecektir. Ancak aynı değişkene üst scope'dan ulaşmak istediğimizde hata mesajı ile karşılaşırız.

**💡 `var` keyword'ü kullanılarak oluşturulan bir değişken HTML'de window nesnesine ait olacaktır. Buna rağmen encapsulation yöntemi ile `let` veya `const` keyword'ü kullanılarak oluşturulan global özellikli bir değişken window nesnesine ait olmaz. Çünkü window nesnesinde `let` ve `const` keyword'lerinin kullanımı tanımlanmamıştır.**

**Örnek**

```javascript
var carName = "Volvo";

// carName değişkenine ulaşmak için window.carName söz dizimi kullanılabilir.
document.getElementById("demo").innerHTML = "I can display " + window.carName;
```

Yukarıdaki `carName` değişkeninin tanımlanmasını `let` veya `const` keyword'lerinden biri ile yapmış olsaydık `undefined` hata mesajını alırdık.

**Örnek**

```javascript
let carName = "Volvo";

/**
 * carName değişkenine ulaşmak için window.carName söz dizimi kullanamayız. Çünkü let keyword'ü window nesnesinde
 * tanımlı değildir.
 */
document.getElementById("demo").innerHTML =
  "I can not display " + window.carName;
```

Bunlara ek olarak bir değişken `var`, `let` veya `const` keyword'leri ile tanımlanmadan değer atanırsa (yani tanımsız bir değişken oluşturulursa) bu değişken de global değişken özelliği kazanır.

**Örnek**

```javascript
function myFunction() {
  carName = "Volvo";
}

myFunction();

console.log(`carName değişkeninin içeriği:${carName}`);
```

    carName değişkeninin içeriği:Volvo

Yukarıdaki örnekte `carName` değişkenine tanımlanmadan değer atanmıştır. Bu durumda `carName` değişkeni tanımsız değişken özelliği kazanır ve değişken içeriğine erişmek için ilgili metodu çağırıp sonrasında `carName` değişkenine erişebiliriz.

**⚠️ İstisna olarak JavaScript strict modda tanımsız (undeclared) değişkenler otomatik olarak global değişken olarak işlem görmez.**

Bir değişken tanımlanmadan değer atanarak kullanılması önerilmez, çünkü değişkenin kapsamı belirsiz olabilir ve bu, beklenmedik hatalara neden olabilir. Mümkünse, değişkenleri uygun bir şekilde `var`, `let` veya `const` ile tanımlayarak kapsamlarını belirtmek daha iyi bir uygulamadır.

## <a id='toc1_2_'></a>[Local Scope](#toc0_)

Bir değişken bulunduğu scope dışarısında kullanılamaması ifadesi local scope terimini ifade eder. Bu bağlamda block scope ve function scope local scope özelliği taşır. Çünkü bu scope türleri içerisinde tanımlanan bir değişkene dışarıdan erişmek mümkün değildir.

**Local scope kullanmamızın nedenleri:**

- Bazen değişkenlerin veya verilerin güvenlik açısından korunması ve başka yerlerden ulaşılmaması gerekir. Yani değişken veya değer private olmak zorundadır. Bu durumda local scope'ları kullanırız.

- Bu şekilde değişkenlerin izolasyonunu sağlarız. Böylece programımızın hatasız çalışmasına katkı sağlarız.

- Local scope'lar aynı değişken isimlerinin kullanılmasına izin verir. Böylece aynı isime sahip değişkenlerin çakışma olasılığı azalır.

- Hata durumlarında, local scope'lar hataların kapsam içinde izole edilmesine yardımcı olur, böylece hata ayıklama ve düzeltme süreçleri kolaylaşır.

- Bir local scope içinde tanımlanan bir değişken için bellekte bir adres oluşturulur ve bu değişken, o scope'un yaşam süresi boyunca kullanılabilir. JavaScript programı local scope dışına çıktığında değişkenin çalışma süresi tamamlanır ve bellekteki adresi silinir. Böylece işlevi sona eren değişken bellekte boşuna adres kaplamaz ve JavaScript programımızın daha hızlı çalışmasını sağlar.

## <a id='toc1_3_'></a>[Özet](#toc0_)

Bu bölümde JavaScript'te **_scope_** kavramını inceledik. JavaScript'te **_scope_**, bir değişkenin tanımlandığı ve erişilebildiği alanı belirtir. Üç temel scope türü bulunur: Block Scope, Function Scope ve Global Scope.

- **Block Scope:** `let` ve `const` ile tanımlanan değişkenler, sadece bulundukları blok içinde geçerlidir. Bu, local ve izole bir kapsam sağlar.

- **Function Scope:** Bir değişken, bir fonksiyon içinde tanımlandığında, sadece bu fonksiyon içinde geçerli olur ve dışarıdan erişilemez. Function scope da local bir kapsam sunar.

- **Global Scope:** Bir değişken metodun dışında tanımlandığında global değişken özelliği kazanır ve program içinde her yerden erişilebilir. Ancak, `var` keyword'ü kullanılmadan tanımsız bir değişken oluşturulduğunda ve bu değişken daha önce tanımlanmamışsa, bu durumda bu değişken otomatik olarak global değişken olarak işlem görür. Yani, `var` kullanılmadan tanımsız bir değişken oluşturulduğunda, JavaScript bu değişkeni global scope'a ekler.

Bu scope türleri, değişkenlerin güvenlik, izolasyon ve hata yönetimi açısından düzenli kullanılmasını sağlar. Scope'lar, kodun anlaşılırlığını artırır ve beklenmedik hataları önler.
