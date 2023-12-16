# JavaScript'in Temelleri

Merhaba arkadaşlar bu yazıda JavaScript'in temellerine bakış atacağız.

Yazıda:
- Statement kavramına.
- White space karakter kullanımına.
- Kod bloklarına.
- Keyword'lere.
- Syntax kavramına.
- Immutable ve mutable kavramlarına.
- Veri Türlerine ve veri tiplerine.
- Temel matematiksel operatörlere.
- Expression kavramına.
- Identifiers oluşturmaya.

Kısaca değineceğim. ilerleyen süreç içerisinde başlıkları detaylandıracağım.

İyi okumalar dilerim.


## JavaScript Statement Kavramı

Bir bilgisayar programı, bilgisayar tarafından çalıştırılacak ifadeleri oluşturur. Programlama dilinde buna **_statement_** adı verilir. Bir JavaScript uygulaması statement listesinden oluşmaktadır.

JavaScript'de statement'lar; değişkenler, değerler,operatörler, expressions, keywords ve comment'lerden oluşabilir.

**Örnek**



```javascript
%%javascript
/* Aşağıdaki satır statement özelliği taşır. */
var x;
```

Javascript statement'ları yazılış sırasına göre çalışırlar.

**Örnek**



```javascript
%%javascript
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
%%javascript
/* Aşağıda 3 statement'in tek bir satırda oluşturulduğu görülüyor.*/
console.log("1.Statement"); console.log("2.Statement"); console.log("3.Statement");
```

    1.Statement
    2.Statement
    3.Statement


## JavaScript White Space Kullanımı

JavaScript white space karakterleri yok sayar. Yani tek bir satırda yazılan statement'lar ile birden fazla satırda oluşturulan statement'lar aynı anlamı taşır.

💡 Kodların okunabilir olmasını sağlamak için her statement'in ayrı satırda yazılması tavsiye edilir. Her satırın ortalama 80 karakter olması okunabilirliği artıracaktır.

**Örnek**



```javascript
%%javascript
let x = 3; let y = 4;

/* Yukarıdaki ifade aşağıdaki gibi de yazılabilir. */
let x = 3;
let y = 4;
```

## JavaScript Kod Blokları

JavaScript'de kodları gruplandırmak için `{}` işaretinden faydalanılır. Gruplandırılan kod blokları **_metot_** veya **_fonksiyon_** olarak ifade edilirler.

**Örnek**



```javascript
%%javascript
function drive() {
  console.log("Sürelim George");
}

// Konsola "Sürelim George" ifadesi yazdırılır.
drive();
```

    Sürelim George


## JavaScript Keyword Kullanımı

JavaScript ifadeleri sıklıkla bir keyword ile başlar.

**❗ Keyword isimleri değişken veya metot ismi tanımlanmasında kullanılamaz. Çünkü bu keyword'ler JavaScript'te rezerve edilmişlerdir.**

**Örnek**



```javascript
%%javascript
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

Yeri geldikçe terimlere ve kullanım türlerine değineceğim arkadaşlar, `var`, `const`, `let` gibi keyword'lerin ne işe yaradıklarını ve farklılıklarını süreç içerisinde anlatacağım.


## JavaScript Syntax Kavramı

Syntax'lar JavaScript'de kodların söz dizimini belirler. Bu kuralları bir dilin yazım kılavuzu yani grameri olarak düşünebiliriz.

**⚠️ Yanlış söz dizimleri olması halinde program veya kod blokları çalışmayacaktır.**

**Örnek**



```javascript
%%javascript
//  Örnekte değişken oluşturmak için kullanılacak söz dizimini görüyoruz.
var x;
var y;

"Osman"=let z;

// ❌ z değişkeninin söz dizimi yanlıştır. Konsola "SyntaxError: Invalid left-hand side in assignment" ifadesi yazdırılır.
console.log (z);
```

## JavaScript Immutable ve Mutable Kavramları

JavaScript'de değişkenler veri türlerine göre göre iki gruba ayrılırlar:

1. Immutable (Sabit değerler)

2. Mutable (Değişken değerler)

Sabit değerler aynı zamanda **_Literals_** olarak isimlendirilirler. Atanan her değer bellekte (RAM'de) yeni bir adrese sahip olur ve atanan değerin içeriği bellekte değiştirilemez.

**💡 Sabit değerleri genelde orijinal verinin korunmasını istediğimiz yerlerde kullanırız. Örneğin orijinal veri birden fazla yerde kullanıyor olabilir. Değeri korunmayan veriler program içerisinde istenmeyen sonuçlara neden olabilir.**

**⚠️ Sabit değerli bir değişkene her yeni değer atanması durumunda bellekte verinin depolanması için yeni bir yer ayrılır. Bu da bellek ile ilgili sorunlara neden olacaktır. Bu sebeple performans öncelliğimiz ise sabitleri daha az kullanmalıyız.**

Değişken değerler aynı zamanda **_variables_** olarak isimlendirilirler. Atanan değer bellekte bir adrese sahip olur ve atanan verinin içeriği değiştirilebilir. **Bu sebeple referans olma özelliğine sahiptirler. Değişken değerli bir değişkene her veri atamasında bellekte yeni bir alan kullanılmaz. O verinin depolandığı ilgili referans adres bulunur ve eski veri overwrite edilerek yeni veri referans adrese kayıt edilir.**

**💡 Değişken özellikli değerler veriler için referans adresleri kullanmaları sebebi ile bellekte sabitler gibi yer kaplamazlar. Dolayısıyla performans önceliğimiz ise bu veri türünü kullanabiliriz.**

**Örnek**

Aşağıda immutable özelliği görülüyor


```javascript
%%javascript

// studentName değişkeni immutable özelliklidir.
let studentName = "Emin";

console.log("studentName değişkenin içeriği "+ studentName +" dir.") 

// personName değişkenimizin içeriğine studentName değişkeninin içeriğini depoluyoruz.
let personName = studentName;

// studentName değişkenimizin içeriğine yeni bir değer depoluyoruz. Bu durumda Hasan için RAM'de yeni bir adres açılacaktır.
studentName = "Hasan";

console.log("Buraya dikkat edelim. personName değişkenin depoladığı değer "+ personName+ "'dir.");
console.log(studentName);
```

    studentName değişkenin içeriği Emin dir.
    Buraya dikkat edelim. personName değişkenin depoladığı değer Emin'dir.
    Hasan


Aşağıda mutable özelliği görülüyor.

**Örnek**



```javascript
%%javascript

// vehicle değişkenimiz mutable özelliklidir.
let vehicle = { type: "car", color: "orange" };

console.log(vehicle["type"]+ " ifadesi konsola yazdırılır.");

// bus adında bir değişken oluşturuyoruz ve depoladığı değeri vehicle değişkeni referans gösterecek şekilde belirliyoruz.
let bus = vehicle;

// bus değişkenin type key'ıne ulaşıp yeni bir veri depoluyoruz.
bus["type"] = "long bus";


console.log("Konsola "+bus["type"]+ " ifadesi yazdırılır.")

/** 
 * ⚠️ Buraya dikkat edelim. vehicle[type]'ın  depoladığı değer "long bus" ile overwrite
 * edilecek ve konsola "long bus" ifadesi yazdırılacaktır.
 * 
 * Çünkü bus değişkeninin içeriğini değiştirdiğimizde aynı zamanda bellekte veriyi tutan referans 
 * adresindeki içeriği de değiştirdik. 
 */
console.log(vehicle["type"]);

```

    car ifadesi konsola yazdırılır.
    Konsola long bus ifadesi yazdırılır.
    long bus


## JavaScript'de Veri Türleri ve Veri Tipleri

JavaScript'de iki veri türü vardır:

1. Primitive (İlkel veri türleri)

2. Object (Referans veri türleri)

Primitive veri türleri **_number, string, boolean, undefined, null, Symbol_ ve BigInt** veri türlerinden oluşur. **Null** veri türü hariç Bunlar aynı zamanda **immutable** özelliğine sahiptirler.

Object veri türleri **_object(nene), array, date, function_** veri türlerinden oluşur. Bunlar aynı zamanda **mutable** özelliğe sahiptirler.


## JavaScript Değişkenler

Programlama dilinde değişkenler veri depolamak için kullanılırlar. Javascript'de değişken tanımlanması `var`, `const` veya `let` keyword'leri ile gerçekleşir.

**Örnek**



```javascript
%%javascript
// x değişkenine 4 rakamını depoladık.
var x = 4;

// y değişkenine "Hasan" ifadesini depoladık
let y = "Hasan"

// pi değişkenine 3.14 rakamını depoladık
const pi=3.14

console.log(x);
console.log(y);
console.log(pi);
```

    4
    Hasan
    3.14


### JavaScript'de Değişkenler Dinamik Özelliklidir

Javascript'de değişkenler dinamik özelliğe sahiptir. Bunun anlamı bir değişken farklı veri tiplerini tutmak için kullanılabilir.

**Örnek**



```javascript
%%javascript
// x değişkeninin  veri tipi undefined'dır..
let x;

// x değişkeninin veri tipi number'dır..
x = 5;

// x değişkeninin veri tipi string'dir.
x = "Sebile";

console.log(x);
```

    Sebile


## JavaScript Operatörleri

Temelde gündelik hayatta kullandığımız matematiksel ifadeleri JavaScript içerisinde kullanabiliriz. Bunlar `( + - * / )` ifadeleridir ve **_aritmetiksel operatörler_** olarak ifade edilirler.

**⚠️ JavaScript'de `=` işareti atama operatörü olarak görev yapar yani matematiksel anlamda eşittir anlamına gelmez. Bunun için `==` veya `===` operatörleri kullanılır.**

**Örnek**



```javascript
%%javascript
// x değişkeni 4 değerini atadık. x referansı 4 değerini depolamış bulunuyor.
let x = 4;

console.log(x);
```

    4


JavaScript'de bir çok operatör vardır. Yeri geldikçe değineceğim.


## JavaScript Expression Kavramı

JavaScript'de bir satırdaki işlemin hesaplanmasına **_expression_** adı verilir. Bir expression değişkenlerden, değerlerden ve operatörlerden oluşur.

**Örnek**



```javascript
%%javascript
var x = 4;
var y = 3;

// Expression
var z = 4 * 3;
```

## JavaScript Identifiers Kavramı

Identifiers'lar bir değişkene veya fonksiyona isim vermede kullanılırlar.

JavaScript'de değişkene isim vermede aşağıdaki maddelere dikkat etmemiz gerekir.

1. JavaScript'de identifier büyük veya küçük harf; `$` veya `_` işaretleri ile başlayabilir.

2. JavaScript identifier'ları **unique** özelliğe sahiptirler. Yani aynı isim başka bir değişken veya metot için kullanılamaz.

3. JavaScript case-sensitive özelliğe sahiptir. Yani `x` ile `X` farklı değişkenleri ifade eder.

4. Identifier tanımlanırken sayısal değerler ilk karakteri oluşturamaz fakat Identifier'ın başka bölümlerinde kullanılabilirler.

5. JavaScript'de rezerve edilmiş keyword'ler identifier olarak kullanılamazlar.

**Örnek**



```javascript
%%javascript
// ✔️ Doğru isim tanımlamaları, ⚠️ ilk iki satırdaki değişken isimleri aynı  olmasına rağmen farklı değişkenleri tanımlar.
var deneme;
var Deneme;
var DENEME01
var $deneme;
var _deneme;

// ❌ Yanlış isim tanımlamaları
var 1deneme

// let keyword'u değişken ismi olarak kullanılamaz.
var let;
```

## JavaScript Büyük Harf/Küçük Harf Ayrımı

JavaScript case-sensitive özelliğe sahiptir. Yani büyük harf küçük harf ayrımı yapar. `firstname` ile `firstName` aynı anlama gelmez.

⚠️ `-` karakteri JavaScript'de rezerve olması sebebi ile kullanılamaz.

