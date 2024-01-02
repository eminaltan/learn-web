# JavaScript'de Döngüler <a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de döngü kavramını ve türlerini inceleyeceğiz.

- [Döngü Kavramı ve Türleri](#toc1_1_)
  - [`for` Döngüsü](#toc1_1_1_)
    - [`for` Döngüsünde Scope'ların Kullanımı](#toc1_1_1_1_)
  - [`for...in` Döngüsü](#toc1_1_2_)
  - [`for...of` Döngüsü](#toc1_1_3_)
  - [`while` Döngüsü](#toc1_1_4_)
  - [`do...while` Döngüsü](#toc1_1_5_)
  - [ Döngüde `break` ve `continue` Statement'ların Kullanımı](#toc1_1_6_)
- [JavaScript'de Etiketlerin Kullanımı](#toc1_2_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of article please [visit](js19-loops.md) this link.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[Döngü Kavramı ve Türleri](#toc0_)

Bazen verilerimizi bilgisayar ortamında işlemek ve saklamak isteyebiliriz. Sayılı bir kaç tane veri için bu işlemi elle gerçekleştirmek kolay olacaktır. Fakat elimizde yüzlerce veriden oluşan bir liste olduğunu düşünürsek bu işlem zor olacağı gibi emek ve zaman kaybına da neden olacaktır.

Bu gibi durumlarda programlamada döngü kavramı yardımımıza yetişir ve **tekrarlı** işlemleri otomatik hale getirerek işimizi kolaylaştırır.

Döngüler özellikle array veri türlerinde oldukça sık kullanılırlar.

**JavaScript'de sık kullanılan döngü türlerini listelerek:**

- `for`

- `for...in`

- `for...of`

- `while`

- `do...while`

Şimdi de bu döngü türlerine değinelim.

### <a id='toc1_1_1_'></a>[`for` Döngüsü](#toc0_)

Belirleyeceğimiz bir koşula göre bir takım işlemleri otomatik olarak yapmak isteyebiliriz bu durumda `for` döngüsünü kullanabiliriz.

**Prototype:**

```javascript
for (exp1; exp2; exp3) {
  // for döngüsü kod bloğu. Çalıştırılacak kodlar buraya yazılır.
}
```

Yukarıda `for` döngüsünün yapısını görüyoruz. `for` döngüsünde 3 tane expression kullanılır. Expression'lar `;` işareti ile birbirlerinden ayrılırlar.

**Expression'lara değinecek olursak:**

- `exp1`: Genelde döngüde kullanılacak değişkenler ve değerler bu bölümde tanımlanır. `for` döngüsüne ait kod bloğu çalıştırılmadan önce 1 kereye mahsus çalıştırılır.

- `exp2`: Döngü koşulu bu bölümde oluşturulur. Döngü koşulunun sonucu `true` olduğu sürece `for` döngüsüne ait kod bloğu çalıştırılır. Koşulun `false` olduğu durumda döngü sonlanır.

- `exp3`: Döngüyü iterate etmek için bu bölüm kullanılır. Döngü koşulunun `true` olması halinde bu kısım çalışacaktır.

**Örnek**

```javascript
for (i = 0; i < 5; i++) {
  console.log(`i'nin değeri: ${i}`);
}
```

    i'nin değeri: 0
    i'nin değeri: 1
    i'nin değeri: 2
    i'nin değeri: 3
    i'nin değeri: 4

**Yukarıdaki `for` döngüsünü açıklayacak olursak:**

1. Döngüde `exp1` ifadesi `i = 0` bölümüne denk gelmektedir. `i` değişkenine 0 değerini atadık. Döngü çalışmaya başladığında 1 kereye mahsus bu expression çalışacaktır.

2. Döngüde `exp2` ifadesi `i < 5` bölümüne denk gelmektedir. Burada döngü koşulumuzu belirledik. `i` değişkeni 5 rakamından küçük olduğu sürece döngü `true` sonucunu döndürecek ve çalışmaya devam edecektir. `false` olduğu durumda döngü sonlanacaktır.

3. Döngüde `exp3` ifadesi `i++` bölüme denk gelmektedir. Döngü koşulu `true` sonucunu döndürdüğü sürece `i` değişkeninin değeri +1 artırılacak ve döngünün tekrarlanmasını sağlayacaktır.

**Örnek**

```javascript
const cars = ["Lada", "Tata", "BMW", "Audi", "Mercedes"];

// exp1 kısmında birden fazla değişkeni aynı anda tanımlayabiliriz.
for (let i = 0, len = cars.length, text = ""; i < len; i++) {
  text += cars[i] + " ";

  console.log(`Arabanın markası: ${text}`);
}
```

    Arabanın markası: Lada
    Arabanın markası: Lada Tata
    Arabanın markası: Lada Tata BMW
    Arabanın markası: Lada Tata BMW Audi
    Arabanın markası: Lada Tata BMW Audi Mercedes

Yukarıda örnekte görüleceği üzere `exp1` kısmı için birden fazla değişlen tanımladık. Değişkenleri `,` işareti yardımıyla birbirlerinden ayırdık.

`exp1` kısmının `for` döngüsü içerisinde kullanılması opiyoneldir. Döngü dışında `exp1` kısmını tanımlayabilir böylece `for` içerisinde `exp1` kısmına yer vermeyebiliriz.

**Örnek**

```javascript
// exp1 kısmına denk gelen i değişkenini for stament'ı dışında tanımladık.
let i = 0;

for (; /* exp1 kısmını es geçtik. */ i < 5; i++) {
  console.log(`i'nin değeri: ${i}`);
}
```

    i'nin değeri: 0
    i'nin değeri: 1
    i'nin değeri: 2
    i'nin değeri: 3
    i'nin değeri: 4

`exp2` kısmının (döngü koşulunun) `for` döngüsü içerisinde kullanılması opiyoneldir.

**⚠️ Döngü koşulu belirlenmeyecekse döngü içerisinde `break` statement'ına yer verilmelidir. Aksi durumda döngü sonlanmayacağı için program çökecektir.**

**Örnek**

```javascript
for (i = 0 /* exp2 kısmını es geçtik. */; ; i++) {
  console.log(`i'nin değeri: ${i}`);

  // i değerinin 5 olması halinde döngü sonlanacaktır.
  if (i == 5) {
    break;
  }
}
```

    i'nin değeri: 0
    i'nin değeri: 1
    i'nin değeri: 2
    i'nin değeri: 3
    i'nin değeri: 4
    i'nin değeri: 5

Yukarıda `break` statement'ının kullanımı görülüyor. Şayet `break` statement'ını kullanmasaydık kodlar sonsuz döngüye girecek ve program çökecekti.

**💡 Döngünün sona erme koşulunu henüz belirleyemediğimiz ancak kodlama süreci içerisinde döngünün sonlanması gereken koşulun ortaya çıkacağı durumlarda `break` statement'ından faydalanabiliriz.**

`exp3` kısmının (iterate değerinin) `for` döngüsü içerisinde kullanılması opiyoneldir. Bu durumda `exp3` kısmı `for` döngüsü içerisinde tanımlanır.

**Örnek**

```javascript
for (i = 0; i < 5 /* exp3 kısmını es geçtik. */; ) {
  console.log(`i'nin değeri: ${i}`);

  // exp3 kısmını döngü içerisinde tanımladık.
  i++;
}
```

    i'nin değeri: 0
    i'nin değeri: 1
    i'nin değeri: 2
    i'nin değeri: 3
    i'nin değeri: 4

Yukarıda örnekte görüldüğü gibi `for` döngüsünü oluşturan bölümlerden `exp3` kısmını kullanmadık. Bunun yerine iterate değerini kod bloğu içerisinde kullandık.

#### <a id='toc1_1_1_1_'></a>[`for` Döngüsünde Scope'ların Kullanımı](#toc0_)

Bir değişken `var` keyword'u kullanarak **tanımlanmadığı** sürece `for` döngüsü içerisinde değişkenin değeri değiştirilirse bu durumda değişkenin değeri bulunduğu scope içerisinde geçerli olur. Bir üst scope'da ki değişkenin değeri aynı kalır.

**Örnek**

```javascript
let i = 5;

for (let i = 0; i < 10; i++) {
  console.log(`i'nin for scope içerisindeki değeri: ${i}`);
}

console.log(
  `i'nin döngü dışındaki değeri: ${i}'dir. i değişkeninin değeri aynı kaldı.`
);
```

    i'nin for scope içerisindeki değeri: 0
    i'nin for scope içerisindeki değeri: 1
    i'nin for scope içerisindeki değeri: 2
    i'nin for scope içerisindeki değeri: 3
    i'nin for scope içerisindeki değeri: 4
    i'nin for scope içerisindeki değeri: 5
    i'nin for scope içerisindeki değeri: 6
    i'nin for scope içerisindeki değeri: 7
    i'nin for scope içerisindeki değeri: 8
    i'nin for scope içerisindeki değeri: 9
    i'nin döngü dışındaki değeri: 5'dir. i değişkeninin değeri aynı kaldı.

Bunun nedeni `let` keyword'unun block scope özelliğine sahip olmasıdır. Aynı örneği `var` keyword'u ile yapsaydık `i` değişkenin depoladığı değer güncellenecekti. Çünkü `var` keyword'u global scope özelliğine sahiptir. <!-- Konuyu daha iyi anlamak için [Block Scope Kavramı](js03-variables.ipynb#block-scope-kavramı) başlığına bakabilirsiniz. -->

**Örnek**

```javascript
// i değişkenin değeri döngü sonrası 10 olacak.
var i = 5;

for (var i = 0; i < 10; i++) {
  console.log(`i'nin for scope içerisindeki değeri: ${i}`);
}

console.log(
  `i'nin döngü dışındaki değeri: ${i}'dur. i değişkeninin değeri güncellendi.`
);
```

    i'nin for scope içerisindeki değeri: 0
    i'nin for scope içerisindeki değeri: 1
    i'nin for scope içerisindeki değeri: 2
    i'nin for scope içerisindeki değeri: 3
    i'nin for scope içerisindeki değeri: 4
    i'nin for scope içerisindeki değeri: 5
    i'nin for scope içerisindeki değeri: 6
    i'nin for scope içerisindeki değeri: 7
    i'nin for scope içerisindeki değeri: 8
    i'nin for scope içerisindeki değeri: 9
    i'nin döngü dışındaki değeri: 10'dur. i değişkeninin değeri güncellendi.

### <a id='toc1_1_2_'></a>[`for...in` Döngüsü](#toc0_)

Genelde nesne özellikli bir değişkenin property değerlerine ulaşmak için kullanılır.

**Prototype:**

```javascript
for (keys in object) {
  // for...in döngüsü kod bloğu. Çalıştırılacak kodlar buraya yazılır.
}
```

Yukarıda `for...in` döngüsünün yapısını görüyoruz. `for...in` döngüsü 2 değişkenden oluşur. Bunlar `keys` ve `object` değişkenlerdir.

**Bu değişkenlere değinecek olursak:**

- `object`: `for...in` döngüsünde kullanılacak nesneyi temsil eder.

- `keys`: Nesnenin property'sindeki key kısmını ifade eder.

**Örnek**

```javascript
const cars = { carName: "Lada", carModel: 1200, carColor: "white" };

var stringHolder;

// cars değişkenindeki property'lerin key kısmı keys değişkenine kopyalanır.
for (keys in cars) {
  /**
   * switch condtion'u ile o anki key değerine göre stringHolder değişkeninin değerini
   * belirliyoruz.
   */
  switch (keys) {
    case "carName":
      stringHolder = "Arabanın markası";
      break;
    case "carModel":
      stringHolder = "Arabanın modeli";
      break;

    default:
      stringHolder = "Arabanın rengi";
  }

  console.log(`${stringHolder}: ${cars[keys]}`);
}
```

    Arabanın markası: Lada
    Arabanın modeli: 1200
    Arabanın rengi: white

**Yukarıdaki `for...in` döngüsünü açıklayacak olursak:**

1. `for...in` döngüsü `cars` nesnesindeki her property için tekrarlanacaktır. (Ör.: `carName: Lada`)

2. Her tekrarda property içerisindeki key kısmı döngüde bulunan `keys` değişkenine kopyalanacaktır.

3. O anki `keys` değişkeninin değerine göre `switch` condition'u içerisinde `stringHolder` değişkeninin değerini belirliyoruz. Sonrasında bu değişkeni property değerlerini yazdırırken kullanacağız.

4. Döngüde o anda bulunan `keys` değişkeni içerisindeki değer kullanılarak `cars` property'si içerisindeki değerlere (yani `Lada, 1200` ve `white`) değerlerine ulaşım sağlanacaktır. Ulaşım `cars[keys]` syntax'ı ile yapılır. Property içerisindeki değerler `stringHolder` değişkeni ile birlikte kullanılarak konsola yazdırılır.

`for...in` döngüsü array veri türüne sahip değişkenin elementlerine erişmek için de kullanılabilir.

**Örnek**

```javascript
const cars = ["Lada", "Audi", "BMW", "Tata"];

for (keys in cars) {
  console.log(`Aracın markası: ${cars[keys]}`);
}
```

    Aracın markası: Lada
    Aracın markası: Audi
    Aracın markası: BMW
    Aracın markası: Tata

**❗ `for...in` döngüsü array özellikli değişkenlerde kullanılması tavsiye edilen bir döngü türü değildir. Bunun nedeni döngü içerisinde array metotlarını kullanmak istediğimizde index kaynaklı bir takım sorunlara neden olmasıdır. `for...in` yerine `for`, `for...of` döngüsünden veya `Array.forEach()` metodundan faydalanılabilir.**

**Örnek**

```javascript
const cars = ["Lada", "Audi", "BMW", "Tata"];

// Call back metodu olarak arrow function kullandık.
cars.forEach((i) => console.log(`Arabanın markası: ${i}`));
```

    Arabanın markası: Lada
    Arabanın markası: Audi
    Arabanın markası: BMW
    Arabanın markası: Tata

Yukarıdaki örnekte `Array.forEach()` metodundan faydalandık. `cars` array değişkeni içerisindeki her bir element için `forEach()` metodu çalışacak ve elementin değeri `i` değişkenine aktarılarak konsola o anki elementin değeri yazdırılacaktır.

### <a id='toc1_1_3_'></a>[`for...of` Döngüsü](#toc0_)

Değeri iterable olan değişkenlerde kullanılır. Bu tür değişkenlerin veri türü Array, String, Maps, NodeList vb. veri türlerinden her hangi biri olabilir.

**Prototype:**

```javascript
for (iterator of object) {
  // for...of döngüsü kod bloğu. Çalıştırılacak kodlar buraya yazılır.
}
```

Yukarıda `for...of` döngüsünün yapısını görüyoruz. `for...of` döngüsü 2 değişkenden oluşur. Bunlar `iterator` ve `object` değişkenleridir.

**Bu değişkenlere değinecek olursak:**

- `iterator`: Döngünün her tekrarlanmasında `object` değişkeninin değeri veya içeriği `iterator` değişkenine kopyalanır.

- `object`: Iterable özellikli bir değeri ifade eder. Bu değerin veri türü array, string, maps, NodeList gibi değerlerden biri olabilir.

**Örnek**

```javascript
const cars = ["Lada", "Audi", "BMW", "Tata"];

/**
 * cars değişkeninin elementleri iterator değişkeni içerisine kopyalanacak ve her bir
 * element için döngü çalışacaktır.
 */
for (const iterator of cars) {
  console.log(`Arabanın markası: ${iterator}`);
}
```

    Arabanın markası: Lada
    Arabanın markası: Audi
    Arabanın markası: BMW
    Arabanın markası: Tata

`for...of` döngüsünün çalışma mantığı `for...in` döngüsüne benzer.

`cars` değişkeninin her bir elementi `iterator` değişkenine kopyalanacak ve döngü `true` olduğu sürece `iterator` değişkeninin değeri konsola yazdırılacaktır.

String veri tipine sahip bir değişken için `for...of` döngüsünü oluşturalım.

**Örnek**

```javascript
const message = "Selam";

/**
 * message değişkeninin her bir karakteri iterator değişkenine kopyalanacak ve bu değer
 * konsola yazdırılacaktır.
 */
for (const iterator of message) {
  console.log(iterator + " ");
}
```

    S
    e
    l
    a
    m

Yukarıdaki örnekte `message` değişkenin her bir karakteri `iterator` değişkenine kopyalanacak ve o anki `iterator` değişkeninin değeri konsola yazdırılacaktır.

### <a id='toc1_1_4_'></a>[`while` Döngüsü](#toc0_)

`for` döngüsüne benzerdir. `while` döngüsü içerisinde kullanılan koşul sağlandığı sürece döngüye ait kod bloğu çalışacaktır. Koşulun `false` değer döndürmesi durumunda döngü sonlanacaktır.

**Prototype:**

```javascript
while (condition) {
  /**
   * while döngüsüne ait kod bloğu. Koşul sağlandığı sürece buradaki kodlar
   * çalıştırılacaktır.
   */
}
```

**Örnek**

```javascript
let i = 0;

while (i < 5) {
  /**
   * i değişkenin değeri 5'den küçük olduğu sürece döngü çalışacak ve konsola i
   * değişkeninin değeri yazdırılacaktır.
   */
  console.log(`i değişkeninin şu anki değeri: ${i}`);

  /**
   * Her döngüde i değişkeninin değeri +1 artırıyoruz ki döngüyü tekrar edip while
   * içerisindeki koşulun sınanmasını sağlayabilelim.
   */
  i++;
}
```

    i değişkeninin şu anki değeri: 0
    i değişkeninin şu anki değeri: 1
    i değişkeninin şu anki değeri: 2
    i değişkeninin şu anki değeri: 3
    i değişkeninin şu anki değeri: 4

**⚠️ `while` döngüsü içerisinde koşulu tekrar sınamak için ve döngüye girmek için (iterate denir.) `i` değişkenin değerini `i++` syntax'ı ile +1 olarak artırıyoruz. Böylece koşul her seferinde `i` değişkenin depoladığı değeri kontrol ediliyor. Şayet `i` değişkeninin değerini artırmasaydık `while` döngüsü kısır döngüye girecek ve JavaScript programımızın çökmesine neden olacaktı.**

Yukarıdaki örneği `for` döngüsü ile yapmış olsaydık:

**Örnek**

```javascript
for (i = 0; i < 5; i++) {
  console.log(`i değişkeninin şu anki değeri: ${i}`);
}
```

    i değişkeninin şu anki değeri: 0
    i değişkeninin şu anki değeri: 1
    i değişkeninin şu anki değeri: 2
    i değişkeninin şu anki değeri: 3
    i değişkeninin şu anki değeri: 4

### <a id='toc1_1_5_'></a>[`do...while` Döngüsü](#toc0_)

`while` döngüsüne benzer şekilde çalışır. Aralarındaki fark `while` döngüsü koşulu önce sınar sonrasında çalıştırırken `do...while` döngüsü önce çalışır sonra koşulu sınar. Bu sebeple `do...while` için oluşturulan koşulun sonucu `false` olsa bile döngü 1 kere çalıştırılacaktır.

**Prototype:**

```javascript
do {
  /**
   * do...while döngüsüne ait kod bloğu. Koşul false olsa bile 1 kereye mahsus buradaki
   * kodlar çalıştırılır.
   */
  /**
   *  Daha sonda condition sınanır. condition sonucu true ise döngü tekrar çalışmaya
   * başlar. Aksi durumda döngü sonlanır.
   */
} while (condition);
```

**Örnek**

```javascript
let i = 0;

// Döngü ilk baş çalıştırılacaktır.
do {
  console.log(`i değişkeninin şu anki değeri: ${i}`);
  i++;
} while (
  // Sonrasında döngü koşulu sınanacaktır.
  i < 5
);
```

    i değişkeninin şu anki değeri: 0
    i değişkeninin şu anki değeri: 1
    i değişkeninin şu anki değeri: 2
    i değişkeninin şu anki değeri: 3
    i değişkeninin şu anki değeri: 4

**⚠️ `do...while` döngüsü içerisinde koşulu tekrar sınamak için ve döngüye girmek için (iterate denir.) `i` değişkenin syntax'ı ile `i++` ifadesi ile +1 olarak artırıyoruz. Böylece koşul her seferinde `i` değişkenin depoladığı değeri kontrol ediliyor. Şayet `i` değişkeninin değerini artırmasaydık `do...while` döngüsü kısır döngüye girecek ve JavaScript programımızın çökmesine neden olacaktı.**

### <a id='toc1_1_6_'></a>[Döngüde `break` ve `continue` Statement'ların Kullanımı](#toc0_)

Bazen bir döngünün belirli bir koşulu sağlaması durumunda sonlanmasını veya bir kereliğine mahsus döngünün çalışmamasını isteyebiliriz. Bu gibi durumlarda `break` ve `continue` statement'ları kullanılır.

`break` statement'ını kullanırsak belirlenen koşul sağlandığında döngü sonlanacaktır.

`continue` statement'ını kullanırsak belirlenen koşulun sağlanması halinde döngü bir kereye mahsus çalışmayacak ve sonuç döndürmeyecektir.

**Örnek**

```javascript
const studentNames = ["Emin", "Murat", "Ömer", "Hasan"];

for (const iterator of studentNames) {
  // iterator değişkeninin içeriği Ömer olması durumunda döngü sonlanacaktır.
  if (iterator === "Ömer") {
    break;
  }

  console.log(`Öğrencinin ismi: ${iterator}`);
}
```

    Öğrencinin ismi: Emin
    Öğrencinin ismi: Murat

**Yapılacak işlemleri açıklayacak olursak:**

1. Yukarıdaki örnekte `studentNames` isimli array türündeki değişkenin elementleri `iterator` değişkenine kopyalanıyor.

2. Döngünün her çalışmasında `if` condition içerisinde belirtilen koşul test ediliyor. Eğer koşul sağlanırsa `if` bloğundaki `break` statement'ı çalışacak ve döngü sonlanacaktır.

3. Kopyalanan değer konsola yazdırılıyor.

Yukarıdaki örneği `continue` statement'ı ile yapmış olsaydık koşulun sağlanması halinde döngü bir kereliğine durdurulacak ve sonra tekrar çalışmaya devam edecekti. Yani "Ömer" değeri konsola yazdırılmayacaktı.

**Örnek**

```javascript
const studentNames = ["Emin", "Murat", "Ömer", "Hasan"];

for (const iterator of studentNames) {
  // iterator değişkeninin içeriği Ömer olması durumunda döngü sonlanacaktır.
  if (iterator === "Ömer") {
    continue;
  }

  console.log(`Öğrencinin ismi: ${iterator}`);
}
```

    Öğrencinin ismi: Emin
    Öğrencinin ismi: Murat
    Öğrencinin ismi: Hasan

**⚠️ `break` ve `continue` statement'ları JavaScript'de blok dışına çıkabilen tek statement türüdür.**

## <a id='toc1_2_'></a>[JavaScript'de Etiketlerin Kullanımı](#toc0_)

Bazen döngü içerisinde belirlediğimiz koşulun (`if` gibi) sağlanması halinde döngünün sonlanmasını ve programın belirlediğimiz bir yerinden çalışmaya devam etmesini isteyebiliriz. Bunu yapabilmek için `break` ve `continue` statement'ları ile birlikte etiketleri kullanılırız. Böylece belirleyeceğimiz koşulun sağlanması halinde döngüye ait kod bloğunun dışına çıkabilir programın akışını istediğimiz yerden devam ettirebiliriz.

Etiketler özellike iç içe döngülerde kullanılır.

**Örnek**

```javascript
// scores adında array veri türü özellikli bir değişken tanımlıyoruz.
let scores = [];

// scores değişkeni içerisine elementleri tanımlıyoruz.
scores[0] = 5;
scores[1] = 10;
scores[2] = 15;
scores[3] = 20;
/** scores[4] = 25;
 *
 * Array içerisindeki 3. elementi comment'e dönüştürelim. Böylece array içerisinde undefined veri tipine sahip
 * bir empty element oluşacaktır.
 */
scores[5] = 30;

/**
 * total değişkeni array elementlerinin toplam sonucunu tutacak. result değişkenini
 * döngünün devam ettiğini anlamak için kullanacağız.
 */
let total = 0,
  result = false;

// example adında bir label'ımımız var. Bu label if bloğuna denk geliyor.
example: if (scores.length > 0) {
  // score değişkeni içerisindeki tüm elementlere ulaşmak için for döngüsünden faydalanıyoruz.
  for (let i = 0; i < scores.length; i++) {
    /**
     * isNaN() metodu ile scores değişkeni içerisindeki her bir elementin sayısal bir değere sahip olup/olmadığı
     * kontrol ediliyor.
     *
     * Eğer değer sayısal özellikli değilse döngü/koşul sonlanacak ve programı example etiketine denk gelen
     * yerden çalışmaya devam ettireceğiz.
     */
    if (isNaN(scores[i])) {
      break example;
    } else {
      total = total + scores[i];
    }
  }

  // Döngünün sorunsuz şekilde sonlanması halinde result değişkeninin değerini true olarak belirliyoruz.
  result = true;
}

result
  ? console.log(`Toplama işleminin sonucu: ${total}`)
  : console.log(
      "Toplama işlemi tamamlanamadı. Toplamaya dahil edilmeyen array elementleri var."
    );
```

    Toplama işlemi tamamlanamadı. Toplamaya dahil edilmeyen array elementleri var.

Yukarıda `example` label'ı ile `break` statement'ını birlikte kullandık. `if (isNaN(scores[i]))` koşunun sonucu `true` olması halinde döngü sonlanacak ve program başlangıç noktası olarak `example` label'ına geri döndürülerek **çalışmaya bir sonraki satırdan** devam edecektir.

Bir örnekte `continue` statement'ı için yapalım.

**Örnek**

```javascript
const studentNames = ["Emin", "Murat", "Ömer", "Hasan"];

example: for (let i = 0; i < studentNames.length; i++) {
  // studentNames element değerlerinden biri Ömer olması halinde döngü 1 kereye mahsus atlanacaktır.
  if (studentNames[i] == "Ömer") {
    continue example;
  } else {
    console.log(`Elementin şu anki değeri: ${studentNames[i]}`);
  }
}
```

    Elementin şu anki değeri: Emin
    Elementin şu anki değeri: Murat
    Elementin şu anki değeri: Hasan

## Özet

JavaScript'teki döngü yapıları, belirli görevleri tekrarlamak ve veri üzerinde gezinmek için kullanılır. Bu döngüler, farklı ihtiyaçlara ve senaryolara uygun bir dizi seçenek sunar.

- **`for` Döngüsü:** Sayısal değerler üzerinde belirli bir koşula göre tekrarlamak için kullanılır. Genellikle belirli bir aralıktaki sayılar üzerinde dolaşmak için kullanılır.

- **`for...in` Döngüsü:** Nesne özelliklerine erişmek için kullanılır. Bir nesnenin key'leri üzerinde dolaşmak için kullanışlıdır.

- **`for...of` Döngüsü:** Iterable nesneler üzerinde dolaşmak için kullanılır. Array, String gibi veri türlerinde kullanılabilir.

- **`while` Döngüsü:** Belirli bir koşul sağlandığı sürece bir kod bloğunu tekrarlamak için kullanılır. Koşul baştan sağlanmazsa hiçbir kez çalışmayabilir.

- **`do...while` Döngüsü:** Koşul kontrolü döngü bloğunun sonunda yapılır. Bu nedenle en az bir kere döngü bloğu çalışır.

Döngüler, programlamada önemli bir araçtır ve tekrarlı işlemleri daha etkili ve düzenli bir şekilde gerçekleştirmemizi sağlar. Ancak, döngülerin sonsuz döngülere veya istenmeyen durumlara neden olabileceği unutulmamalıdır. Bu nedenle, döngüler kullanılırken dikkatli olunmalı ve uygun koşul kontrolü sağlanmalıdır.
