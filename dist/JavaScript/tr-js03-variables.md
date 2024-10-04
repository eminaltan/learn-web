# JavaScript'te Değişkenler<a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'te değişkenlere değineceğiz.

Yazıda:

- [JavaScript Değişken Kavramı ve Değişken Tanımlama Yöntemleri](#toc1_1_)
  - [`var`, `let` ve `const` Keyword Kullanım Sıralaması](#toc1_1_1_)
- [JavaScript Veri Türleri](#toc1_2_)
- [JavaScript'te Değişken Tanımlama](#toc1_3_)
- [JavaScript Aynı Değişkenin Tekrar Tanımlanması](#toc1_4_)
- [JavaScript `$` Simgesinin Kullanılması](#toc1_5_)
- [JavaScript `_` Simgesinin Kullanılması](#toc1_6_)
- [Block Scope Kavramı](#toc1_7_)
- [JavaScript Hoist](#toc1_8_)
- [Özet](#toc1_9_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of this article please visit [this link](js03-variables.ipynb).

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->


## <a id='toc1_1_'></a>[JavaScript Değişken Kavramı ve Değişken Tanımlama Yöntemleri](#toc0_)

Bir metafor üzerinden açıklarsak değişkenleri sıvı konulan bir kaba benzetebiliriz. Kaba koyduğumuz sıvıları değiştirebildiğimiz gibi değişkenlerin içerisine depoladığımız verileri de değiştirebiliriz.

**JavaScript'te bir değişken 4 yöntemden biri kullanılarak tanımlanabilir:**

- Otomatik olarak

- `var` keyword'ü kullanarak

- `let` keyword'ü kullanarak

- `const` keyword'ü kullanarak

Otomatik olarak tanımlanan değişkenlerin başında bir **keyword bulunmaz.** Dolayısıyla bir değişkenin otomatik olarak tanımlandığını bu şekilde anlarız. Otomatik olarak tanımlanan değişkenler matematiksel işlemlerde de kullanılabilirler.

**Örnek**



```python
%%script node

x = 4;
y = 5;
result = x + y;

// Konsola 9 rakamı yazdırılır.
console.log(`Sonuç: ${result}`);
```

    Sonuç: 9


**💡 Değişkenleri daima JavaScript dokümanının veya bulunduğu _scope_'un[^1] başında tanımlamak olası problemlerin önüne geçecektir. Buna [JavaScript Hoist](#javascript-hoist) başlığı altında değineceğim.**

**💡 1995-2015 arasında değişken tanımlamak için `var` keyword'ü kullanılırdı, 2015'de değişken tanımlamak için JavaScript'e ek olarak `let` ve `const` keyword'leri de eklenmiştir. Böylece bir dokümanın içeriğine bakarak modern veya eski tarayıcılar için hazırlandığını anlayabiliriz.**


### <a id='toc1_1_1_'></a>[`var`, `let` ve `const` Keyword Kullanım Sıralaması](#toc0_)

**Değişkenler dokümanın veya bulunduğu scope'un başında tanımlanmalıdır. Genel olarak değişken oluştururken aşağıdaki sıralamanın izlenmesi tavsiye edilir:**

1. Otomatik değişken kullanılmaması tavsiye edilir.

2. Eğer bir değişkenin içeriği sabitse yani değişmeyecekse daima `const` keyword'ü kullanılarak tanımlanması tavsiye edilir.

3. Array ve object türündeki değişkenlerin içeriği sabitse yani değişmeyecekse daima `const` keyword'ü kullanılarak tanımlanması tavsiye edilir.

4. `const` keyword'nün kullanılamadığı durumlarda `let` keyword'ü kullanılarak değişken tanımlanması tavsiye edilir.

5. Şayet eski browser'lar için script yazacak isek `var` keyword'ünün kullanılması tavsiye edilir.


## <a id='toc1_2_'></a>[JavaScript Veri Türleri](#toc0_)

Diğer programlama dillerinde olduğu gibi JavaScript'te de bir çok veri türü bulunmaktadır. Veri türlerine örnek verirsek string'ler ve numerik değerler JavaScript içerisinde en fazla kullanılan veri türleridir. Şimdilik ihtiyacımız kadarına değiniyorum.

**⚠️ String veri türleri `""` veya `''` işaretleri arasında kullanılırlar. Bir sayısal ifade `""` veya `''` işaretleri arasında kullanılıyorsa bu onun _numerik string_ olarak ifade edildiğini gösterir.**

**Örnek**

```javascript
// str1 string türünde bir değişkendir.
var str1 = "Test";

// str2 numerik string türünde bir değişkendir.
var str2 = "4";

// str3 numerik string türünde bir değişkendir.
var str3 = '3';

// str4 numerik türünde bir değişkendir.
var str4 = 4;

// str5 string türünde bir değişkendir.
var str5 = 'Text';
```


Ek olarak bakcticks ` `` ` işaretlerini kullanarak da string özellikli içerikler oluşturabiliriz. Genelde backticks işaretlerini bir değişken ile birlikte kullanırız. Böylece dinamik içerikli ifadeler oluşturabiliriz.

**Örnek**



```python
%%script node

var str5 = 8;

// Backticks yardımıyla string bir ifadenin değişken ile birlikte kullanılması.
console.log(`str5 değişkeninin içeriği: ${str5}`);
```

    str5 değişkeninin içeriği: 8


**⚠️ Numerik özellikli string değerler dışındaki diğer string değerleri matematiksel işlemlerde sonuca katkıda bulunmazlar. Şayet bir string matematiksel ifade içerisinde kullanılırsa işlem sonucunun veri tipi string olacaktır. Bu durum string'in bulunduğu yere göre sonucu etkiler. Numerik özellikli string değerler için durum biraz daha farklıdır. Daha detaylı bilgi almak için [JavaScript Numerik Özellikli String Değerler](tr-js07-numeric-data-type.ipynb#javascript-numerik-özellikli-string-değerler) başlığına bakabilirsiniz.**

<!-- [#1](https://github.com/eminaltan/learn-web/issues/1) -->

**JavaScript'te expression'lar (ifadeler) soldan sağa şekilde değerlendirilir. Yani Javascript ifadenin nerede string olacağını bu pattern'e göre belirler.**

**Örnek**



```python
%%script node

var x = 4 + 3 + "1";

// Konsola 71 yazdırılacaktır.
console.log(`Konsola ${x} yazdırılacaktır.`);

var y = "1" + 4 + 3;

// Konsola 143 yazdırılacaktır.
console.log(`Konsola ${y} yazdırılacaktır.`);

// Konsola 8 yazdırılacaktır.
y = "9" - 4 + 3;
console.log(`Konsola ${y} yazdırılacaktır.`);
```

    Konsola 71 yazdırılacaktır.
    Konsola 143 yazdırılacaktır.
    Konsola 8 yazdırılacaktır.


Matematiksel operatörlerden `+` işareti string veri tiplerinde kullanılabilir. Bu durumda string'ler birbirine eklenir. String veri tipleri için `+` işareti **_ekleme operatörü_** olarak isimlendirilir.

**Örnek**



```python
%%script node

let x = "Emin" + " " + "Altan";

// Konsola Emin Altan yazdırılacaktır.
console.log("Konsola " + x + " yazdırılacaktır.");
```

    Konsola Emin Altan yazdırılacaktır.


## <a id='toc1_3_'></a>[JavaScript'te Değişken Tanımlama](#toc0_)

Bir değişken oluşturulma işlemine JavaScript'te **_declaration_** adı verilir. Değişken deklarasyonu yapılırken en çok `const` ve `let` keyword'lerinden faydalanılır.

Bir değişken içeriğine değer atanmadan deklarasyonu yapılabilir. Bu durumdaki değişkenin içeriği `undefined` olarak belirlenir. **Bu durum `const` ile tanımlanan değişken için geçerli değildir. `const` keyword'ü kullanılarak deklarasyonu yapılacak olan değişkene aynı satırda değer atanması şarttır.**

**💡 `undefined` aynı zamanda bir keyword olup özellikle _conditional statement_'lar[^2] oluştururken bazen faydalı olabilir.**

**Örnek**

```javascript
// ✔️ x değişkenine değer atamadan oluşturduk bu durumdaki değişken içeriği undefined olarak belirlenir.
var x;

// ❌ const keyword'ü kullanılarak tanımlanan değişkenin bu şeklide kullanımı uygun değildir.
const firstName;
firstName = "Murat";

// ✔️ const keyword'ü ile gerçekleştirilen deklarasyon tek satırda tanımlanmış olmalıdır.
const firstName2 ="Sinan";
```


**💡 Aynı tipteki değişkenleri tek bir satırda tanımlayabiliriz, bu bize zamandan kazandırır. Bu durumda değişkenler arasına `,` işareti yerleştirilir.**

**Örnek**



```python
%%script node

let firstName = "Emin", surname = "Altan", id = 500;

// Konsola Emin yazdırılacaktır.
console.log(firstName);
```

    Emin


**❗ JavaScript'te değişken isimleri aslında referans işlevi görür. Yani bir değerin ifade edilmesi için referans olarak kullanılırlar. `const` keyword'ünü bu perspektiften incelediğimizde aslında sabit bir değişken tanımlamak için değil sabit bir değer için referans oluşturmak amacıyla kullanılır. Bu ayrımın anlaşılması object ve array türündeki verilerin `const` keyword'ü ile birlikte kullanılması açısından önemlidir. Bunu bir örnek ile inceleyelim. Yazımın ilerleyen dönemlerinde array ve object türlerine değineceğim.**

**Örnek**

```javascript
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


## <a id='toc1_4_'></a>[JavaScript Aynı Değişkenin Tekrar Tanımlanması](#toc0_)

JavaScript'te bir değişken `var` keyword'ü ile tekrar tanımlanabilir. Bu işleme **_re-declaring_** adı verilir. Bu durumdaki değişkene yeni veri atanmadığı sürece depolanmış verisini korur.

**Örnek**



```python
%%script node

var firstName = "Emin";

/**
 * firstName değişken deklarasyonu tekrarlanmış. firstName değişkenine yeni bir değer atanmadığı sürece 
 * depoladığı bilgiyi koruyacaktır.
 */
var firstName;

// Konsola Emin ifadesi yazdırılır.
console.log(`Konsola ${firstName} ifadesi yazdırılır.`);

firstName = "Murat";

// firstName değişkeninin yeni değeri Murat olacak ve konsola Murat ifadesi yazdırılacaktır.
console.log(`firstName değişkeninin yeni değeri Murat olacak ve konsola ${firstName} ifadesi yazdırılacaktır.`);
```

    Konsola Emin ifadesi yazdırılır.
    firstName değişkeninin yeni değeri Murat olacak ve konsola Murat ifadesi yazdırılacaktır.


**⚠️ `let` ve `const` ile tanımlanmış bir değişken tekrar tanımlanamaz. Bir değişkenin tekrar tanımlanabilme özelliği sadece `var` keyword'u için geçerlidir.**

**Örnek**

```javascript
let i = 5;
let i = 3;

// ❌ SyntaxError: Identifier 'i' has already been declared hata mesajını geri döndürecektir.
console.log(i);
```


## <a id='toc1_5_'></a>[JavaScript `$` Simgesinin Kullanılması](#toc0_)

**💡 Genelde `$` simgesi değişken tanımlamak için kullanılmaz. Bir JavaScript kütüphanesi içerisindeki metoda _alias_[^3] vermek için kullanılır. Mesela `$` işareti JQuery kütüphanesindeki tüm `<a>` elementlerini seçmek için kullanılabilir. `$("a")` gibi.**


## <a id='toc1_6_'></a>[JavaScript `_` Simgesinin Kullanılması](#toc0_)

**💡 Genelde JavaScript'te `_`(underscore) işareti bir değişkenin private olduğunu ifade etmek için kullanılır.**


## <a id='toc1_7_'></a>[Block Scope Kavramı](#toc0_)

2015'den (ES6) önce JavaScript'te 2 tür scope kavramı bulunmaktaydı bunlar **_global scope_**[^4] ve **_function scope_**[^5] kavramları idi. ES6 ile `let` ve `const` keyword'leri JavaScript'e entegre olmuştur. **Bu keyword'ler kullanılarak oluşturulan bir değişken bulunduğu scope dışından erişilemez ve kullanılamaz.** Bu ifade **_block scope_** kavramını oluşturur.

**Örnek**

```javascript
{
  let x = 5;

  /** 
   * ⚠️ `var` keyword'ü kullanılarak tanımlanmış bir değişkene scope dışarısından (function scope olmamak 
   * kaydıyla) erişilebilir ve kullanılabilir.
   */
  var y = 10;
}

// ❌ x değişkenine erişilemez ve kullanılamaz. Konsola ReferenceError: x is not defined ifadesi yazdırılır.
console.log(x);

// y değişkenine erişilebilir ve kullanılabilir. Konsola 10 rakamı yazdırılır.
console.log(y);
```

**💡 Scope kavramı hakkında daha fazla bilgi almak için [JavaScript Scope](tr-js23-scope-concept.ipynb) içeriğini ziyaret edebilirsiniz.**

## <a id='toc1_8_'></a>[JavaScript Hoist](#toc0_)

Bazen bir değişkene değer atar sonrasında tanımlarız. Bu durumda JavaScript değişkeni bulunduğu scope içerisinde en üst satıra taşıyacak ve kodları çalıştıracaktır. Kısaca buna hoist adı verilir. Hoist (kaldırma) kelimesinin anlamından ne işe yaradığını aklınızda tutabilirsiniz.

**⚠️ Hoist kavramı `var` keyword'ü ile tanımlanan değişkenler için tam anlamıyla çalışır. `let` ve `const` ile tanımlanan bir değişken hoist edilir fakat initialize edilemezler. Bunun anlamı `let` veya `const` ile tanımlanan bir değişken scope içerisinde en üst satıra taşınır fakat deklarasyonu yapılamadan kullanılamazlar. Şayet hoist özelliğini kullanırsak `ReferenceError` hatası ile karşılaşırız. değişken _temporal dead zone_'a[^6] düşer. Bu durumdaki değişkenler deklarasyonu yapılıp veri depolandıktan sonra kullanılabilir.**

**❗ Bir değişkenin kullanılacağı scope içerisinde en üst satırda tanımlanması tavsiye edilir. Aksi taktirde bazen hangi verinin nereden geldiğini anlayamayabiliriz.**

**Örnek**

```javascript
// Örnekte önce değişkeni kullanıyoruz ikinci satırda tanımlamasını yapıyoruz. Buna hoist adı verilir.
carName = "Lada";
var carName;

// Konsola Lada ifadesi yazılır.
console.log(carName);

/**
 * ❌ let veya const ile tanımlanan değişkenlerde hoist özelliğini kullanılması durumunda ReferenceError hatası 
 * ile karşılaşırız.
 */
model = "Niva";
let model;
```


## <a id='toc1_9_'></a>[Özet](#toc0_)

Bu bölümde JavaScript'te değişkenlerle ilgili temel konuları ele aldık. Değişkenler, veri depolamak için kullanılır ve farklı tanımlama yöntemleri bulunmaktadır. `var`, `let`, ve `const` keyword'leriyle değişkenler tanımlanabilir. Modern JavaScript uygulamalarında genellikle `let` ve `const` tercih edilir, ancak eski tarayıcılar için `var` da kullanılabilir.

Veri tipleri arasında string'ler ve numerik değerler önemli yer tutar. String ifadeler `""` veya `''` içinde tanımlanır, ve numerik özellikli string'ler matematiksel işlemlerde kullanılabilir.

Bazen bir string ifadeyi bir değer ile birlikte kullanmak isteyebiliriz. Bu gibi durumlarda backticks ` `` ` işaretlerinden faydalanırız.

Block scope kavramı, ES6 ile birlikte gelen `let` ve `const` keyword'leri sayesinde ortaya çıktı. Bu kavram, değişkenlerin sadece tanımlandıkları blok içinde erişilebilir olmalarını sağlar. Özellikle `const` ile tanımlanan değişkenlerin değerleri değiştirilemez.

JavaScript'te hoisting, `var` ile tanımlanan değişkenlerin deklarasyonlarının kodun en üstüne taşınması anlamına gelir. Ancak `let` ve `const` için hoisting, sadece deklarasyonu yukarı taşır, initialize etmez.

Bu temel konuların anlaşılması, JavaScript'te daha karmaşık uygulamalar geliştirmek için önemlidir. Veri tipleri, değişken tanımlama yöntemleri ve scope kavramları, kodun daha etkili ve anlaşılır olmasına katkı sağlar.


[^1]: Scope bir değişkenin erişebilir ve kullanılabilir olduğu alanı ifade etmek için kullanılan terimdir.
[^2]: Conditional statement yardımıyla JavaScript'te bir takım çıktılara göre programın akışını değiştirmek isteyebiliriz bu durumda `if, else` veya `else if` gibi ifadelerden faydalanırız. Bunlara conditional statement adı verilir.
[^3]: JavaScript'te bir değişkeninin içeriği başka bir değişkene kopyalanabilir. Genel olarak bu tanım alias kavramını oluşturur. Alias'lar anlaşılabilir ve semantic kodlar yazmamızı sağlarlar. Örneğin `let x = 5; var aliasVariable = x;` şeklindeki bir ifade de `x` ile `aliasVariable` aynı değeri paylaşırlar. `x` referans olarak ifade edilirken, `aliasVariable` alias olarak ifade edilir.
[^4]: Bunu bir metafor üzerinden açıklayalım. Matematikte evrensel küme kavramını biliriz. Evrensel küme diğer kümeleri kapsaması gibi JavaScript'te global scope içerisinde tanımlanmış değişken veya metotları (fonksiyonları) kapsar ve script'in her yerinden erişilebilir kılar. Yani global scope burada evrensel küme olarak ifade edilebilir. Bu anlamda geneldirler.
[^5]: Bir metot (fonksiyon) içerisindeki tanımlanan değişkenleri veya başka metotları ifade eder. Function scope içerisindeki değişkenler dışarıdan erişilip kullanılamaz sadece tanımlandığı scope içerisinde kullanılabilir. Bu anlamda özeldirler.
[^6]: Hoisting için kullanılan bu kavram, bir değişkenin ulaşılamaz ve kullanılamaz olduğunu ifade etmek için kullanılır. Ta ki değişkeni tanımlandıktan sonra kullanılana kadar.

