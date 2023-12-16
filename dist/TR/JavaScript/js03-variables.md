# JavaScript'de Değişkenler

Merhaba arkadaşlar bu yazıda JavaScript'de değişkenlere değineceğiz.

Yazıda:

- Değişken tanımlama yöntemlerine.
- Veri tiplerine.
- Değişken tanımlanmasına.
- Aynı değişkenin tekrar tanımlanması yani re-declaring işlemine.
- `$` ve `_` işaretlerinin kullanımına.
- Block scope kavramına.
- Hoist kavramına.

Değineceğim.

İyi okumalar dilerim.


## JavaScript Değişken Tanımlama Yöntemleri

Değişkenler veri depolamak için kullanılır . Bu kısımda değişken tanımlama yöntemlerini inceleyeceğiz.

JavaScript'de bir değişken 4 yöntemle tanımlanabilir:

1. Otomatik olarak.

2. `var` keyword'u kullanarak.

3. `let` keyword'u kullanarak.

4. `const` keyword'u kullanarak.

Otomatik olarak tanımlanan değişkenlerin başında bir **keyword bulunmaz.** Dolayısıyla bir değişkenin otomatik olarak tanımlandığını bu şekilde anlarız. Otomatik olarak tanımlanan değişkenler matematiksel işlemlerde de kullanılabilirler.

**Örnek**



```javascript
%%javascript
    x = 4;
    y = 5;
    c = x + y;

    // Konsola 9 rakamı yazdırılır.
    console.log(c);
```

    9


**💡 Değişkenleri daima JavaScript dokümanının veya bulunduğu **_scope_**'un[^1] başında tanımlamak olası problemlerin önüne geçecektir. Buna [JavaScript Hoist](#javascript-hoist) başlığı altında değineceğim.**

**💡 1995-2015 arasında değişken tanımlamak için `var` keyword'u kullanılırdı, 2015'de değişken tanımlamak için JavaScript'e ek olarak `let` ve `const` keyword'leri de eklenmiştir. Böylece bir dokümanın içeriğine bakarak modern veya eski tarayıcılar için hazırlandığını anlayabiliriz.**


### `var`, `let` ve `const` Keyword Kullanım Sıralaması

Değişkenler dokümanın veya bulunduğu scope'un başında tanımlanmalıdır. Genel olarak değişken oluştururken aşağıdaki sıralamanın izlenmesi tavsiye edilir:

1. Otomatik değişken kullanılmaması tavsiye edilir.

2. Eğer bir değişkenin içeriği sabitse yani değişmeyecekse daima `const` keyword'u kullanılarak tanımlanması tavsiye edilir.

3. Array ve object türündeki değişkenlerin içeriği sabitse yani değişmeyecekse daima `const` keyword'u kullanılarak tanımlanması tavsiye edilir.

4. `const` keyword'nun kullanılamadığı durumlarda `let` keyword'u kullanılarak değişken tanımlanması tavsiye edilir.

5. Şayet eski browser'lar için script yazacak isek `var` keyword'unun kullanılması tavsiye edilir.


## JavaScript Veri Türleri

Diğer programlama dillerinde olduğu gibi JavaScript'de de bir çok veri türü bulunmaktadır. Veri türlerine örnek verirsek string'ler ve numerik değerler JavaScript içerisinde en fazla kullanılan veri türleridir. Şimdilik ihtiyacımız kadarına değiniyorum.

**⚠️ String veri türleri `""` veya `''` işaretleri arasında kullanılırlar. Bir sayısal ifade `""` veya `''` işaretleri arasında kullanılıyorsa bu onun _*numerik string*_ olarak ifade edildiğini gösterir.**

**Örnek**



```javascript
%%javascript
// str1 string türünde bir değişkendir.
var str1 = "Test";

// str2 numerik string türünde bir değişkendir.
var str2 = "4";

// str3 numerik string türünde bir değişkendir.
var str3 = `3`;

// str3 numerik türünde bir değişkendir.
var str4 = 4;

// str4 string türünde bir değişkendir.
var str4 = `Text`;
```

**⚠️ Numerik özellikli string değerler dışındaki diğer string değerleri matematiksel işlemlerde sonuca katkıda bulunmazlar. Şayet bir string matematiksel ifade içerisinde kullanılırsa işlem sonucunun veri tipi string olacaktır. Bu durum string'in bulunduğu yere göre sonucu etkiler. Numerik özellikli string değerler için durum biraz daha farklıdır. Daha detaylı bilgi almak için [JavaScript Numerik Özellikli String Değerler](js07-numeric-data-type.ipynb#javascript-numerik-özellikli-string-değerler) başlığına bakabilirsiniz.**

<!-- [#1](https://github.com/eminaltan/learn-web/issues/1) -->

**JavaScript'de expression'lar (ifadeler) soldan sağa şekilde değerlendirilir. Yani Javascript ifadenin nerede string olacağını bu pattern'e göre belirler.**

**Örnek**



```javascript
%%javascript

var x = 4 + 3 + "1";

// Konsola "71" yazdırılacaktır.
console.log("Konsola "+ x + " yazdırılacaktır.")

var y = "1" + 4 + 3;

// Konsola "143" yazdırılacaktır.
console.log("Konsola "+ y + " yazdırılacaktır.")

// Konsola "8" yazdırılacaktır.
y = "9" - 4 + 3;
console.log("Konsola "+ y + " yazdırılacaktır.")
```

    Konsola 71 yazdırılacaktır.
    Konsola 143 yazdırılacaktır.
    Konsola 8 yazdırılacaktır.


Matematiksel operatörlerden `+` işareti string veri tiplerinde kullanılabilir. Bu durumda string'ler birbirine eklenir. String veri tipleri için `+` işareti **_ekleme operatörü_** olarak isimlendirilir.

**Örnek**



```javascript
%%javascript
let x = "Emin" + " " + "Altan";

// Konsola "Emin Altan" yazdırılacaktır.
console.log("Konsola " + x + " yazdırılacaktır.");
```

    Konsola Emin Altan yazdırılacaktır.


## JavaScript'de Değişken Tanımlama

Bir değişken oluşturulma işlemine JavaScript'de **_declaration_** adı verilir. Değişken deklarasyonu yapılırken en çok `const` ve `let` keyword'lerinden faydalanılır.

Bir değişken içeriğine değer atanmadan deklarasyonu yapılabilir. Bu durumdaki değişkenin içeriği `undefined` olarak belirlenir. **Bu durum `const` ile tanımlanan değişken için geçerli değildir. `const` keyword'u kullanılarak deklarasyonu yapılacak olan değişkene aynı satırda değer atanması şarttır.**

**💡 `undefined` aynı zamanda bir keyword olup özellikle _*conditional statement*_'lar[^2] oluştururken bazen faydalı olabilir.**

**Örnek**



```javascript
%%javascript
// x değişkenine değer atamadan oluşturduk bu durumdaki değişken içeriği undefined olarak belirlenir.
var x;

// ❌ const keyword'u kullanılarak tanımlanan değişkenin bu şeklide kullanımı uygun değildir.
const firstName;
firstName ="Murat";

// ✔️ const keyword'u ile gerçekleştirilen deklarasyon tek satırda tanımlanmış olmalıdır.
const firstName2="Sinan";
```

**💡 Aynı tipteki değişkenleri tek bir satırda tanımlayabiliriz, bu bize zamandan kazandırır. Bu durumda değişkenler arasına `,` işareti yerleştirilir.**

**Örnek**



```javascript
%%javascript
let firstName = "Emin", surname = "Altan", id = 500;
// Konsola "Emin" yazdırılacaktır.
console.log (firstName)
```

    Emin


**❗ JavaScript'de değişken isimleri aslında referans işlevi görür. Yani bir değerin ifade edilmesi için referans olarak kullanılırlar. `const` keyword'unu bu perspektiften incelediğimizde aslında sabit bir değişken tanımlamak için değil sabit bir değer için referans oluşturmak amacıyla kullanılır. Bu ayrımın anlaşılması object ve array türündeki verilerin `const` keyword'u ile birlikte kullanılması açısından önemlidir. Bunu bir örnek ile inceleyelim. Yazımın ilerleyen dönemlerinde array ve object türlerine değineceğim.**

**Örnek**



```javascript
%%javascript
// Array türünde değerlerimizi  const ile tanımlanmış cities adında değişkene depoluyoruz.
const cities = ["Bursa", "İzmir", "Ankara"];

// cities array türündeki verinin ilk elementini (yani Bursa) değerini konsola yazdırıyoruz.
console.log(cities[0]);

// cities array türündeki verinin ilk elementini (yani Bursa) yeni bir değer ile yer değiştiriyoruz.
cities[0] = "İstanbul";

// cities referansının ilk değerini konsola yazdırıyoruz. Bu durumda ilk değer Bursa değil, İstanbul olacaktır.
console.log(cities[0]);

// ❌ cities referansına yeni bir değer atayamayız.
cities = ["Tekirdağ", "Samsun", "Sinop"];

```


    <IPython.core.display.Javascript object>


## JavaScript Aynı Değişkenin Tekrar Tanımlanması

JavaScript'de bir değişken `var` keyword'u ile tekrar tanımlanabilir. Bu işleme **_re-declaring_** adı verilir. Bu durumdaki değişkene yeni veri atanmadığı sürece depolanmış verisini korur.

**Örnek**



```javascript
%%javascript
var firstName = "Emin";

/**
 *  firstName  değişken  deklarasyonu tekrarlanmış. firstName değişkenine yeni bir değer atanmadığı sürece 
 * depoladığı bilgiyi koruyacaktır.
 */
var firstName;

// Konsola "Emin" ifadesi yazdırılır.
console.log("Konsola "+ firstName + " ifadesi yazdırılır.");

firstName = "Murat";

// firstName değişkeninin yeni değeri Murat olacak ve konsola "Murat" ifadesi yazdırılacaktır.
console.log("firstName değişkeninin yeni değeri Murat olacak ve konsola " + firstName + " ifadesi yazdırılacaktır.");
```

    Konsola Emin ifadesi yazdırılır.
    firstName değişkeninin yeni değeri Murat olacak ve konsola Murat ifadesi yazdırılacaktır.


**⚠️ `let` ve `const` ile tanımlanmış bir değişken tekrar tanımlanamaz. Bir değişkenin tekrar tanımlanabilme özelliği sadece `var` keyword'u için geçerlidir.**


## JavaScript `$` Simgesinin Kullanılması

**💡 Genelde `$` simgesi değişken tanımlamak için kullanılmaz. Bir javascript kütüphanesi içerisindeki metoda _*alias*_[^3] vermek için kullanılır. Mesela `$` işareti JQuery kütüphanesindeki tüm `<a>` elementlerini seçmek için kullanılabilir. `$("a")` gibi.**


## JavaScript `_` Simgesinin Kullanılması

**💡 Genelde JavaScript'de `_`(underscore) işareti bir değişkenin private olduğunu ifade etmek için kullanılır.**


## Block Scope Kavramı

2015'den (ES6) önce JavaScript'de 2 tür scope kavramı bulunmaktaydı bunlar **_global scope_**[^4] ve **_function scope_**[^5] kavramları idi. ES6 ile `let` ve `const` keyword'leri JavaScript'e entegre olmuştur. **Bu keyword'ler kullanılarak oluşturulan bir değişken bulunduğu scope dışından erişilemez ve kullanılamaz.** Bu ifade **_block scope_** kavramını oluşturur.

**⚠️ `var` keyword'una bulunduğu scope dışından erişilebilir ve kullanılabilir.**

**Örnek**



```javascript
%%javascript
{
  let x = 5;
  var y = 10;
}

// ❌ x değişkenine erişilemez ve kullanılamaz. Konsola "ReferenceError: x is not defined" ifadesi yazdırılır.
console.log(x);

// y değişkenine erişilebilir ve kullanılabilir. Konsola 10 rakamı yazdırılır.
console.log(y);
```


    <IPython.core.display.Javascript object>


## JavaScript Hoist

Bazen bir değişkene değer atar sonrasında tanımlarız. Bu durumda JavaScript değişkeni bulunduğu scope içerisinde en üst satıra taşıyacak ve kodları çalıştıracaktır. Kısaca buna hoist adı verilir. Hoist (kaldırma) kelimesinin anlamından ne işe yaradığını aklınızda tutabilirsiniz.

**⚠️ Hoist kavramı `var` keyword'u ile tanımlanan değişkenler için tam anlamıyla çalışır. `let` ve `const` ile tanımlanan bir değişken hoist edilir fakat initialize edilemezler. Bunun anlamı `let` veya `const` ile tanımlanan bir değişken scope içerisinde en üst satıra taşınır fakat deklarasyonu yapılamadan kullanılamazlar. Şayet hoist özelliğini kullanırsak `ReferenceError` hatası ile karşılaşırız. değişken _*temporal dead zone*_'a[^6] düşer. Bu durumdaki değişkenler deklarasyonu yapılıp veri depolandıktan sonra kullanılabilir.**

**❗ JavaScript'de hoist özelliğini şahsen kullanılmamasını tavsiye ederim. Çünkü bu bazen hangi verinin nereden geldiğinin zor anlaşılmasına neden olur. İdeal olan bir değişkeni ile depolayacağı veriyi aynı satırda deklarasyonunu yapmak olacaktır.**



```javascript
%%javascript
// Örnekte önce değişkeni kullanıyoruz ikinci satırda tanımlamasını yapıyoruz. Buna hoist adı verilir.
carName = "Lada";
var carName;

// Konsola "Lada" ifadesi yazılır.
console.log(carName);

// ❌ let veya const ile tanımlanan değişkenlerde hoist özelliğini kullanılması durumunda ReferenceError hatası ile karşılaşırız.
model = "Niva";
let model;

```

[^1]: Scope bir değişkenin erişebilir olduğu alanı ifade etmek için kullanılan terimdir.
[^2]: Conditional statement JavaScript'de bir takım çıktılara göre programın akışını değiştirmek isteyebiliriz bu durumda `if else else if` gibi ifadelerden faydalanırız. Bunlara conditional statement adı verilir.
[^3]: JavaScript'de bir değişkeninin içeriği başka bir değişkene kopyalanabilir. Genel olarak bu tanım alias kavramını oluşturur. Alias'lar anlaşılabilir ve semantic kodlar yazmamızı sağlarlar. Örneğin `let x=5; var aliasVariable=x;` şeklindeki bir ifade de `x` ile `aliasVariable` aynı değeri paylaşırlar. `x` referans olarak ifade edilirken, `aliasVariable` alias olarak ifade edilir.
[^4]: Bunu bir metafor üzerinden açıklayacağım. Matematikte evrensel küme kavramını biliriz. Evrensel küme diğer kümeleri kapsaması gibi JavaScript'de global scope içerisinde tanımlanmış değişken veya metotları (fonksiyonları) kapsar ve script'in her yerinden erişilebilir kılar. Yani global scope burada evrensel küme olarak ifade edilebilir. Bu anlamda geneldirler.
[^5]: Bir metot (fonksiyon) içerisindeki tanımlanan değişkenleri veya başka metotları ifade eder. Function scope içerisindeki değişkenler dışarıdan erişilip kullanılamaz sadece tanımlandığı scope içerisinde kullanılabilir. Bu anlamda özeldirler.
[^6]: Hoisting için kullanılan bu kavram, bir değişkenin ulaşılamaz ve kullanılamaz olduğunu ifade etmek için kullanılır. Ta ki değişkeni tanımlandıktan sonra kullanılana kadar.

