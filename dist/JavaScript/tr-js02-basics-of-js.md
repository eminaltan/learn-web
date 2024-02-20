# JavaScript'in Temelleri<a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'in temellerine bakış atacağız.

Yazıda:

- [JavaScript Statement Kavramı](#toc1_1_)
- [JavaScript White Space Kullanımı](#toc1_2_)
- [JavaScript Kod Blokları](#toc1_3_)
- [JavaScript Keyword Kullanımı](#toc1_4_)
- [JavaScript Syntax Kavramı](#toc1_5_)
- [JavaScript Immutable ve Mutable Kavramları](#toc1_6_)
- [JavaScript'te Veri Türleri ve Veri Tipleri](#toc1_7_)
- [JavaScript Değişkenler](#toc1_8_)
  - [JavaScript'te Değişkenler Dinamik Özelliklidir](#toc1_8_1_)
- [JavaScript Operatörleri](#toc1_9_)
- [JavaScript Expression Kavramı](#toc1_10_)
- [JavaScript Identifiers Kavramı](#toc1_11_)
- [JavaScript Büyük Harf/Küçük Harf Ayrımı](#toc1_12_)
- [Özet](#toc1_13_)

Kısaca değineceğim. ilerleyen süreç içerisinde başlıkları detaylandıracağım.

İyi okumalar dilerim.

If you want to read English version of this article please visit [this link](js02-basics-of-js.md).

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript Statement Kavramı](#toc0_)

Bir bilgisayar programı, bilgisayar tarafından çalıştırılacak ifadeleri oluşturur. Programlama dilinde ifadelere **_statement_** adı verilir. Bir JavaScript uygulaması statement listesinden oluşmaktadır.

JavaScript'te statement'lar; değişkenlerden, değerlerden,operatörlerden, expression'lardan, keyword'lerden ve comment'lerden oluşabilir.

**Örnek**

```javascript
/* Aşağıdaki satır statement özelliği taşır. */
var x;
```

JavaScript statement'ları yazılış sırasına göre çalışırlar.

**Örnek**

```javascript
console.log("İlk burası çalışacak.");
console.log("Sonra burası çalışacak.");
console.log("En son burası çalışacak.");
```

    İlk burası çalışacak.
    Sonra burası çalışacak.
    En son burası çalışacak.

Statement'ları birbirinden ayırmak için `;` işaretinden faydalanılır. Tek satır birden fazla statement'ı içerebilir.

**Örnek**

```javascript
/* Aşağıda 3 statement'in tek bir satırda oluşturulduğu görülüyor.*/
console.log("1.Statement"); console.log("2.Statement"); console.log("3.Statement");
```

    1.Statement
    2.Statement
    3.Statement

## <a id='toc1_2_'></a>[JavaScript White Space Kullanımı](#toc0_)

JavaScript white space karakterleri yok sayar. Yani tek bir satırda yazılan statement'lar ile birden fazla satırda oluşturulan statement'lar aynı anlamı taşır.

**💡 Kodların okunabilir olmasını sağlamak için her statement'in ayrı satırda yazılması tavsiye edilir. Her satırın ortalama 80 karakter olması okunabilirliği artıracaktır.**

**Örnek**

```javascript
let x = 3,
  y = 4;

/* Yukarıdaki ifade aşağıdaki gibi de yazılabilir. */
let x = 3;
let y = 4;
```

## <a id='toc1_3_'></a>[JavaScript Kod Blokları](#toc0_)

JavaScript'te kodları gruplandırmak için `{}` işaretinden faydalanılır. Gruplandırılan kod blokları **_metot_** veya **_fonksiyon_** olarak ifade edilirler.

**Örnek**

```javascript
function drive() {
  console.log("Sürelim George");
}

// Konsola Sürelim George ifadesi yazdırılır.
drive();
```

    Sürelim George

## <a id='toc1_4_'></a>[JavaScript Keyword Kullanımı](#toc0_)

JavaScript ifadeleri sıklıkla bir keyword ile başlar.

**❗ Keyword isimleri değişken veya metot ismi tanımlanmasında kullanılamaz. Çünkü bu keyword'ler JavaScript'te rezerve edilmişlerdir.**

**Örnek**

```javascript
/* ❌ Aşağıdaki değişken tanımlaması yanlıştır. */
let var = 5;

// "SyntaxError: Unexpected token 'var'" ifadesi konsola yazdırılacaktır.
console.log(var);
```

Sık kullanılan keyword'ler aşağıda listelenmiştir.

| **Keyword** | **Açıklama**                            |
| ----------- | --------------------------------------- |
| `var`       | Değişken oluşturur.                     |
| `let`       | Block türünde değişken oluşturur.       |
| `const`     | Block türünde sabit değişken oluşturur. |

Yeri geldikçe `var`, `const` ve `let` terimlerine; kullanım amaçlarına ve farklılıklarına süreç içerisinde değineceğim.

## <a id='toc1_5_'></a>[JavaScript Syntax Kavramı](#toc0_)

Syntax'lar JavaScript'te kodların söz dizimini belirler. Bu kuralları bir dilin yazım kılavuzu yani grameri olarak düşünebiliriz.

**⚠️ Yanlış söz dizimleri olması halinde program veya kod blokları çalışmayacaktır.**

**Örnek**

```javascript
// Örnekte değişken oluşturmak için kullanılacak söz dizimini görüyoruz.
var x;
var y;

"Osman" = let z;

/**
 * ❌ z değişkeninin söz dizimi yanlıştır. Konsola SyntaxError: Invalid left-hand side
 * in assignment ifadesi yazdırılır.
 */
console.log (z);
```

## <a id='toc1_6_'></a>[JavaScript Immutable ve Mutable Kavramları](#toc0_)

**JavaScript'te değişkenler veri türlerine göre göre iki gruba ayrılırlar:**

- Immutable (Sabit değerler)

- Mutable (Değişken değerler)

Sabit değerler aynı zamanda **_Literals_** olarak isimlendirilirler. Atanan her değer bellekte (RAM'de) yeni bir adrese sahip olur ve atanan değerin bellekteki adresi değiştirilemez.

**💡 Sabit değerleri genelde orijinal verinin korunmasını istediğimiz yerlerde kullanırız. Örneğin orijinal veri birden fazla yerde kullanıyor olabilir. Değeri korunmayan veriler program içerisinde istenmeyen sonuçlara neden olabilir.**

**⚠️ Sabit değerli bir değişkene her yeni değer atanması durumunda bellekte verinin depolanması için yeni bir yer ayrılır. Bu da bellek ile ilgili sorunlara neden olacaktır. Bu sebeple performans öncelliğimiz ise sabitleri daha az kullanmalıyız.**

Değişken değerler aynı zamanda **_variables_** olarak isimlendirilirler. Atanan değer bellekte **sürekli olarak aynı adreste tutulur ve atanan verinin içeriği değiştirilebilir. Bu sebeple referans olma özelliğine sahiptirler. Değişken değerli bir değişkene her veri atamasında bellekte yeni bir alan kullanılmaz. O verinin depolandığı ilgili referans adres bulunur ve eski veri overwrite edilerek yeni veri referans adrese kayıt edilir.**

**💡 Değişken özellikli değerler veriler için referans adresleri kullanmaları sebebi ile bellekte sabitler gibi yer kaplamazlar. Dolayısıyla performans önceliğimiz ise bu veri türünü kullanabiliriz.**

**Örnek**

Aşağıda immutable özelliği görülüyor.

```javascript
// studentName değişkeninin değeri immutable özelliğine sahiptir.
let studentName = "Emin";

console.log(`studentName değişkenin içeriği: ${studentName}`);

// personName değişkenimizin içeriğine studentName değişkeninin içeriğini depoluyoruz.
let personName = studentName;

/**
 * studentName değişkenimizin içeriğine yeni bir değer depoluyoruz. Bu durumda Hasan için RAM'de yeni bir adres
 * açılacaktır.
 */
studentName = "Hasan";

console.log(
  `Buraya dikkat edelim. personName değişkenin depoladığı değer: ${personName}`
);
console.log(`studentName değişkenin içeriği: ${studentName}`);
```

    studentName değişkenin içeriği: Emin
    Buraya dikkat edelim. personName değişkenin depoladığı değer: Emin
    studentName değişkenin içeriği: Hasan

Aşağıda mutable özelliği görülüyor.

**Örnek**

```javascript
// vehicle değişkenimizin değeri mutable özelliklidir.
let vehicle = { type: "car", color: "orange" };

console.log(`${vehicle["type"]} ifadesi konsola yazdırılır.`);

/**
 * bus adında bir değişken oluşturuyoruz ve depoladığı değeri vehicle değişkeni referans gösterecek şekilde
 * belirliyoruz.
 */
let bus = vehicle;

// bus değişkenin type key'ine ulaşıp yeni bir veri depoluyoruz.
bus["type"] = "long bus";

console.log(`Konsola ${bus["type"]} ifadesi yazdırılır.`);

/**
 * ⚠️ Buraya dikkat edelim. vehicle[type]'ın  depoladığı değer long bus ile overwrite edilecek ve konsola long
 * bus ifadesi yazdırılacaktır.
 *
 * Çünkü bus değişkeninin içeriğini değiştirdiğimizde aynı zamanda bellekte veriyi tutan referans adresindeki
 * içeriği de değiştirdik.
 */
console.log(`${vehicle["type"]} ifadesi konsola yazdırılır.`);
```

    car ifadesi konsola yazdırılır.
    Konsola long bus ifadesi yazdırılır.
    long bus ifadesi konsola yazdırılır.

## <a id='toc1_7_'></a>[JavaScript'te Veri Türleri ve Veri Tipleri](#toc0_)

**JavaScript'te iki veri türü vardır:**

- Primitive (İlkel veri türleri)

- Object (Referans veri türleri)

Primitive veri türleri **_number, string, boolean, undefined, null, symbol_** ve **_bigint_** veri türlerinden oluşur. **null** veri türü hariç bunlar aynı zamanda **immutable** özelliğine sahiptirler.

Object veri türleri **_object, array, date_** ve **_function_** veri türlerinden oluşur. Bunlar aynı zamanda **mutable** özelliğe sahiptirler.

## <a id='toc1_8_'></a>[JavaScript Değişkenler](#toc0_)

Programlama dilinde değişkenler veri depolamak için kullanılırlar. JavaScript'te değişken tanımlanması `var`, `const` veya `let` keyword'leri kullanılarak yapılır.

**Örnek**

```javascript
// x değişkenine 4 rakamını depoladık.
var x = 4;

// y değişkenine Hasan ifadesini depoladık.
let y = "Hasan";

// pi değişkenine 3.14 rakamını depoladık.
const pi = 3.14;

console.log(`x'in değeri: ${x}`);
console.log(`y'nin değeri: ${y}`);
console.log(`pi'nin değeri: ${pi}`);
```

    x'in değeri: 4
    y'nin değeri: Hasan
    pi'nin değeri: 3.14

### <a id='toc1_8_1_'></a>[JavaScript'te Değişkenler Dinamik Özelliklidir](#toc0_)

JavaScript'te değişkenler dinamik özelliğe sahiptir. Bunun anlamı bir değişken farklı veri tiplerini tutmak için kullanılabilir.

**Örnek**

```javascript
// x değişkeninin  veri tipi undefined'dir.
let x;

// x değişkeninin veri tipi number'dir.
x = 5;

// x değişkeninin veri tipi string'dir.
x = "Sebile";

console.log(`x değişkeninin şu anki değeri: ${x}`);
```

    x değişkeninin şu anki değeri: Sebile

## <a id='toc1_9_'></a>[JavaScript Operatörleri](#toc0_)

Temelde gündelik hayatta kullandığımız matematiksel ifadeleri JavaScript içerisinde kullanabiliriz. Bunlar `( + - * / )` ifadeleridir ve **_aritmetiksel operatörler_** olarak ifade edilirler.

**⚠️ JavaScript'te `=` işareti atama operatörü olarak görev yapar yani matematiksel anlamda eşittir anlamına gelmez. Eşitlik ifadeleri için `==` veya `===` operatörleri kullanılır.**

**Örnek**

```javascript
// x değişkenine 4 değerini atadık. x referansı 4 değerini depolamış bulunuyor.
let x = 4;

console.log(`x değişkeninin değeri: ${x}`);
```

    x değişkeninin değeri: 4

JavaScript'te bir çok operatör vardır. Yeri geldikçe değineceğim.

## <a id='toc1_10_'></a>[JavaScript Expression Kavramı](#toc0_)

JavaScript'te bir satırdaki işlemin hesaplanmasına **_expression_** adı verilir. Bir expression değişkenlerden, değerlerden ve operatörlerden oluşur.

**Örnek**

```javascript
var x = 4;
var y = 3;

// Expression
var z = 4 * 3;
```

## <a id='toc1_11_'></a>[JavaScript Identifiers Kavramı](#toc0_)

Identifiers'lar bir değişkene veya fonksiyona isim vermede kullanılırlar.

**JavaScript'te değişkene isim vermede aşağıdaki maddelere dikkat etmemiz gerekir.**

- JavaScript'te identifier büyük veya küçük harf; `$` veya `_` işaretleri ile başlayabilir.

- JavaScript identifier'ları **unique** özelliğe sahiptirler. Yani aynı isim başka bir değişken veya metot için kullanılamaz.

- JavaScript case-sensitive özelliğe sahiptir. Yani `x` ile `X` farklı değişkenleri ifade eder.

- Identifier tanımlanırken sayısal değerler ilk karakteri oluşturamaz fakat Identifier'ın başka bölümlerinde kullanılabilirler.

- JavaScript'te rezerve edilmiş keyword'ler identifier olarak kullanılamazlar.

**Örnek**

```javascript
/**
 * ✔️ Doğru isim tanımlamaları, ⚠️ ilk iki satırdaki değişken isimleri aynı  olmasına
 * rağmen farklı değişkenleri tanımlar.
 */
var deneme;
var Deneme;
var DENEME01;
var $deneme;
var _deneme;

// ❌ Yanlış isim tanımlamaları
var 1deneme;

// let keyword'u değişken ismi olarak kullanılamaz.
var let;
```

## <a id='toc1_12_'></a>[JavaScript Büyük Harf/Küçük Harf Ayrımı](#toc0_)

JavaScript case-sensitive özelliğe sahiptir. Yani büyük harf küçük harf ayrımı yapar. `firstname` ile `firstName` aynı anlama gelmez.

**⚠️ `-` karakteri JavaScript'te rezerve olması sebebi ile kullanılamaz.**

## <a id='toc1_13_'></a>[Özet](#toc0_)

Bu bölümde, JavaScript'in temellerini ele aldık. JavaScript ifadeleri, boşluk kullanımı, kod blokları, anahtar kelime kullanımı, sözdizimi, değişmez (immutable) ve değişken (mutable) kavramları, veri tipleri ve değişkenler gibi konuları inceledik. Ayrıca, JavaScript operatörleri, ifadeler, tanımlayıcılar ve büyük/küçük harf ayrımı konularına da değindik.

Gelecek bölümlerde her konuyu daha ayrıntılı bir şekilde ele alarak daha fazla açıklama ve örnek sunacağım.
