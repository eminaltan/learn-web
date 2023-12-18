## JavaScript'de Conditional Statement Kavramı

Bazen belirlediğimiz bir koşulun veya matematiksel ifadenin sonucuna göre program içerisinde akışı değiştirmek ve farklı işlemler yapmak isteyebiliriz. Bu gibi durumlarda conditional statement'ları kullanırız.

**Örnek**

```javascript
%%script node

const age = 18;

/**
 * Örnekte yaşın 18 rakamına eşit veya büyük olması durumunda alkol satışına izin verildiği
 * görülüyor.
 *
 * age değişkeninin içeriğini değiştirerek sonuçları gözlemleyebilirsiniz.
 *
 * 💡 ? (Ternary operatörünü kullandık.)
 */
console.log(`Alkol satışı yapılabilir mi?: ${18 <= age ? "Evet alkol satışı yapılabilir." : "Hayır alkol satışı yapılamaz."}`);
```

    Alkol satışı yapılabilir mi?: Evet alkol satışı yapılabilir.

Yukarıda `age` değişkeninin 18 rakamına eşit veya büyük olması halinde alkol satışı yapılabileceğini gösteren kod bloğu örneğini görüyoruz.

JavaScript'de aşağıdaki conditional statement'ları kullanabilir ve program akışını değiştirebiliriz:

- `if`

- `else`

- `else if`

- `switch`

Şimdi bunları inceleyelim.

### `if` Statement

`if` statement'ı içerisinde oluşturduğumuz koşulun gerçekleşmesi halinde `if` bloğuna ait kodlar çalışacaktır.

**Prototype:**

```javascript
if (condition1) {
  // If statement'ı condition1 ile uyumlu ise buradaki kod bloğu çalışır.
}
```

Bir önceki örneği `if` statement'ı ile oluşturalım.

**Örnek**

```javascript
%%script node

const age = 18;

/**
 * age değeri 18 rakamına eşit olduğundan if statement'ı içerisindeki koşul gerçekleşmiş olacak ve if bloğuna ait
 * kodlar çalıştırılacaktır.
 */
if (18 <= age) {
    console.log("Evet alkol satışı yapılabilir.");
}

```

    Evet alkol satışı yapılabilir.

`age` değişkeninin değerini 14 yapalım ve sona `console.log("Hayır alkol satışı yapılamaz.")` statement'ını ekleyelim.

**Örnek**

```javascript
%%script node

const age = 14;

// if statement'ı içerisindeki koşul gerçekleşmediği için if bloğuna ait kodlar çalışmayacaktır.
if (18 <= age) {
    console.log("Evet alkol satışı yapılabilir.");
}

console.log("Hayır alkol satışı yapılamaz.");
```

    Hayır alkol satışı yapılamaz.

Görüleceği üzere `age` değişkeni 18'den küçük olduğu için `if` statement'ı içerisindeki koşulu sağlamıyor. Bu sebeple `if` bloğuna ait kodlar çalışmayacaktır. JavaScript çalışmaya devam edecek ve "Hayır alkol satışı yapılamaz." ifadesi konsola yazdırılacaktır.

**❗ Şayet koşul sağlansaydı `if` statement'dan sonra gelen kodlar yine çalıştırılacaktı.**

**Örnek**

```javascript
%%script node

const age = 18;

if (18 <= age) {
    console.log("Evet alkol satışı yapılabilir.");
}

console.log("Hayır alkol satışı yapılamaz.");
```

    Evel alkol satışı yapılabilir.
    Hayır alkol satışı yapılamaz.

Birden fazla koşul gerektiren durumlarda `else, else if` veya `switch` statement'larından faydalanırız. Yazının ilerleyen bölümlerinde her birine değineceğiz.

### `else` Statement

`if` statement'ı içerisinde oluşturduğumuz koşulun **gerçekleşmemesi** halinde `else` bloğunun içerisindeki kodlar çalışacaktır.

**Prototype:**

```javascript
if (condition1) {
  // If statement'ı condition1 ile uyumlu ise buradaki kod bloğu çalışır.
} else {
  // If statement'ı condition1 ile uyumlu değilse buradaki kod bloğu çalışır.
}
```

Alkol örneğimizden devam ederek `else` statement'ı oluşturalım. `age` değerini 14 olarak değiştirdiğimizde koşulumuz `if` statement'ı ile uyuşmayacak dolayısıyla `if` bloğuna ait kodlar çalışmayacaktır. JavaScript `else` bloğuna ait kodları çalıştıracaktır.

**Örnek**

```javascript
%%script node

// age değişkenin değerini değiştirerek sonuçları gözlemleyebilirsiniz.
const age = 14;

// 18 <= 14 ifadesi false olduğundan if bloğuna ait kodlar çalışmayacaktır.
if (18 <= age) {
    console.log("Evet alkol satışı yapılabilir.");
}

// if statement'ının boolean olarak değeri false olduğu için else bloğuna ait kodlar çalışacaktır.
else {
    console.log("Hayır alkol satışı yapılamaz.");
}

```

    Hayır alkol satışı yapılamaz.

**💡 Koşulumuz bir satırdan oluşuyorsa `?` (Ternary) operatörünü kullanabiliriz. `?` operatörü genelde bir satıdan oluşan koşullar için değişkene değer atamada kullanılır. Bu sayede kodlarımızı sadeleştirmiş oluruz.**

Bir önceki örneği `?` operatörü ile birlikte yapalım.

**Örnek**

```javascript
%%script node

const age = 14;

// Ternary operatör ile birlikte backtick karakterini kullanarak kodlarımızı sadeleştiriyoruz.
console.log(
  `Alkol satışı yapılabilir mi?: ${
    18 <= age
      ? "Evet alkol satışı yapılabilir."
      : "Hayır alkol satışı yapılamaz."
  }`
);

```

    Alkol satışı yapılabilir mi?: Hayır alkol satışı yapılamaz.

Bazen ikiden fazla koşula sahip olabiliriz bu gibi durumlarda `else if` veya `switch` statement'ları kullanılır.

### `else if` Statement

İkiden fazla koşula sahipsek `else if` statement'ını kullanırız. `if` statement'ı içerişindeki koşulun gerçekleşmemesi halinde `else if` statement'ı kontrol edilir. Koşulun gerçekleşmesi halinde ilgili statement'a ait kod bloğu çalışır, uyuşmuyorsa bir sonraki `else if` statement'ı için aynı işlem gerçekleştirilir. Şayet hiçbir statement koşul ile uyuşmuyorsa `else` kod bloğu çalışır.

**Prototype:**

```javascript
if (condition1) {
  // If statement'ı condition1 ile uyumlu ise buradaki kod bloğu çalışır.
} else if (condition2) {
  // If statement'ı condition1 ile uyumlu değilse fakat condition2 ile uyumluysa buradaki kod bloğu çalışır.
} else {
  // Statement'ların hiçbiri koşul ile uyuşmaz ise else statement'ı içerisindeki kod bloğu çalışır.
}
```

**Örnek**

```javascript
%%script node

const car = "Lada";

if (car == "Mercedes") {
    console.log(`Arabanın markası: ${car}`);
}

else if (car == "Audi") {
    console.log(`Arabanın markası: ${car}`);
}

else if (car == "BMW") {
    console.log(`Arabanın markası: ${car}`);
}

// car değişkeni koşul ile uyuştuğundan buradaki else if bloğuna ait kodlar çalışacaktır.
else if (car == "Lada") {
    console.log(`Arabanın markası: ${car}`);
}

else {
    console.log(`Araba markası belirlenen koşullar ile uyuşmuyor.`);
}
```

    Arabanın markası: Lada

Yukarıdaki örnekte `if` statement'ı içerisindeki koşul `false` olduğu için `if` bloğuna ait kodlar çalışmayacaktır.

JavaScript bu durumda bir sonraki satıra geçecek ve `else if` statement'ını kontrol edecektir. Fakat koşul yine `false` olduğu için kod bloğu çalışmayacaktır. Bu işlem tüm statement'lar için tekrarlanacaktır. Ta ki belirlediğimiz koşula uygun `else if` statement'ı bulunana kadar.

Koşula uygun bir `else if` statement'ı bulunduğunda ilgili kod bloğu çalıştırılacak ve bu kod bloğu içerisindeki sonuç geri döndürülecektir.

Şayet koşul hiçbir statement ile uyuşmaz ise `else` kod bloğu çalıştırılacaktır.

**Örnek**

```javascript
%%script node

const car = "Lada";

if (car == "Mercedes") {
    console.log(`Arabanın markası: ${car}`);
}

else if (car == "Audi") {
    console.log(`Arabanın markası: ${car}`);
}

else if (car == "BMW") {
    console.log(`Arabanın markası: ${car}`);
}

else if (car == "Fiat") {
    console.log(`Arabanın markası: ${car}`);
}

// Hiçbir koşul car değişkeni ile uyuşmadığından else kod bloğu çalışacaktır.
else {
    console.log(`Araba markası belirlenen koşullar ile uyuşmuyor.`);
}
```

    Araba markası belirlenen koşullar ile uyuşmuyor.

### `switch` Statement

**Prototype:**

İkiden fazla koşula sahipsek `else if` yöntemine alternatif olarak `switch` statement'ını kullanabiliriz.

```javascript
switch (expression) {
  case x:
    // expression, x değeri ile uyuşursa buradaki kod bloğu çalıştırılır.
    break;
  case y:
    // expression, y değeri ile uyuşursa buradaki kod bloğu çalıştırılır.
    break;
  default:
  // expression hiçbir değer ile uyuşmuyorsa varsayılan olarak buradaki kod bloğu çalıştırılır.
}
```

`switch` statement'ının çalışma mantığına incelediğimizde ilk önce expression sonucu hesaplanır. Elde edilen sonuç her bir koşul ile kıyaslanır. Sonuç ile uyuşan koşul bulunduğunda koşula ait kod bloğu çalıştırılır. Şayet sonuç ile uyuşan kod bloğu bulunamaz ise varsayılan olarak `default` keyword'una ait kod bloğu çalıştırılır.

Araba örneğimizi `switch` statement'ı ile oluşturalım.

**Örnek**

```javascript
%%script node

const car = "Lada";

switch (car) {
    case "Mercedes":
        console.log(`Aracın: markası ${car}`);
        break;

    case "Audi":
    console.log(`Aracın: markası ${car}`);
        break;

    case "BMW":
    console.log(`Aracın: markası ${car}`);
        break;

    // expression sonucu yani car değişkeni koşul ile uyuşmasından ötürü buradaki kod bloğu çalıştırılacaktır.
    case "Lada":
    console.log(`Aracın: markası ${car}`);
        break;

    default:
        console.log(`Araba markası belirlenen koşullar ile uyuşmuyor.`);
}

```

    Aracın: markası Lada

Yukarıdaki örnekte `switch` içerisindeki expression her bir koşul ile kıyaslanacak ve uyuşan koşula ait kod bloğu çalıştırılarak sonuç döndürülecektir.

Şayet expression hiçbir koşul ile uyuşmazsa `default` keyword'una ait kod bloğu çalıştırılacak ve sonuç döndürülecekti.

**Örnek**

```javascript
%%script node

const car = "Lada";

switch (car) {
    case "Mercedes":
        console.log(`Aracın: markası ${car}`);
        break;

    case "Audi":
    console.log(`Aracın: markası ${car}`);
        break;

    case "BMW":
    console.log(`Aracın: markası ${car}`);
    break;

    case "Fiat":
        console.log(`Aracın: markası ${car}`);
        break;

    /**
     * expression sonucu yani car değişkeni hiçbir koşul ile uyuşmamasından ötürü default kod bloğu
     * çalıştırılacaktır.
     */
    default:
        console.log(`Araba markası belirlenen koşullar ile uyuşmuyor.`);
}

```

    Araba markası belirlenen koşullar ile uyuşmuyor.

`default` keyword'u `switch` statement'ı içerisinde herhangi bir yerde kullanılabilir.

**⚠️ Şayet `default` keyword'u `switch` statement'ının herhangi bir yerinde kullanılacaksa kod bloğu içerisinde `break` keyword'unun de tanımlı olması gerekir.**

**Örnek**

```javascript
%%script node

const car = "Lada";

switch (car) {
    // default keyword'u başta kullanılmış.
    default:
        console.log(`Araba markası belirlenen koşullar ile uyuşmuyor.`);
        break;

    case "Mercedes":
        console.log(`Aracın: markası ${car}`);
        break;

    case "Audi":
    console.log(`Aracın: markası ${car}`);
        break;

    case "BMW":
    console.log(`Aracın: markası ${car}`);
    break;

    case "Fiat":
        console.log(`Aracın: markası ${car}`);
}
```

    Araba markası belirlenen koşullar ile uyuşmuyor.

Dikkat ettiyseniz her `case` bloğu içerisinde `break` keyword'unu kullandık. `break` keyword'u ilgili koşula uygun `case` bloğunu sonlandırmak için kullanılır.

`switch` yapısında son `case` için `break` keyword'u tanımlamamıza gerek yoktur. JavaScript son `case`'e ulaştığında otomatik olarak `switch` statement'ı sonlandıracaktır.

**❗ `break` keyword'unu kullanmazsak koşul ile uyuşan `case` bloğu çalışacak ve ardından bir sonraki `case` bloğu çalşmaya devam edecektir. JavaScript `break` keyword'une ulaşana kadar bu durum devam edecektir. Bu bakımdan her `case` bloğunda `break` keyword'unun kullanılması gerekir.**

**Örnek**

```javascript
%%script node

const car = "Lada";

switch (car) {
    case "Lada":
        console.log(`Aracın: markası ${car}`);


    case "Mercedes":
    console.log(`Aracın: markası ${car}`);


    case "BMW":
    console.log(`Aracın: markası ${car}`);


    // JavaScript break keyword'una ulaşana kadar çalışmayı sürdürür.
    case "Audi":
    console.log(`Aracın: markası ${car}`);
        break;

    default:
        console.log(`Araba markası belirlenen koşullar ile uyuşmuyor.`);
}

```

    Aracın: markası Lada
    Aracın: markası Lada
    Aracın: markası Lada
    Aracın: markası Lada

**💡 Yapılacak işlem birden fazla koşul için ortaklanarak `switch` statement'ı içerisinde kullanılabilir.**

**Örnek**

```javascript
%%script node

const car = "Toyota";

switch (car) {
    case "Toyota":
    case "Honda":
        console.log(`Araba Japon üretimi. Arabanının markası: ${car}`);
        break;

    case "BMW":
    case "Audi":
    console.log(`Araba Alman üretimi. Arabanının markası: ${car}`);
        break;

    default:
        console.log(`Araba türü belirlenen koşullar ile uyuşmuyor.`);
}

```

    Araba Japon üretimi. Arabanının markası: Toyota

`switch` statement'ı strict özelliklidir. Yani expression içerisindeki ifade `case` ile tam uyuşmalıdır. Aksi durumda uyuşma sağlanmaz.

**Örnek**

```javascript
%%script node

const car = "Toy";

switch (car) {
    case "Toyota":
    case "Honda":
        console.log(`Araba Japon üretimi. Arabanının markası: ${car}`);
        break;

    case "BMW":
    case "Audi":
    console.log(`Araba Alman üretimi. Arabanının markası: ${car}`);
        break;

    default:
        console.log(`Araba türü belirlenen koşullar ile uyuşmuyor.`);
}

```

    Araba türü belirlenen koşullar ile uyuşmuyor.

Yukarıda görüleceği üzere car değişkeni içerisindeki karakterler "Toyota" string'indeki karakterler ile kısmen uyuşmasına rağmen ilgili `case`'a ait kod bloğu çalışmamaktadır. `case` bloklarının çalışması için tam eşleşme sağlanması şarttır.

**➖ `switch`, `else if` veya `if else` Yapıları Arasındaki Farklar**

- `else if` veya `if else` yapılarında bütün veri tipleri kullanılabilirken `switch` statement'ında yalnızca `number` veya `string` özellikli veri tipleri kullanılır.

- `else if` veya `if else` yapılarında koşula göre ya `if` ya da `else` bloğuna ait kodlar çalıştırılırken `switch` yapısında `break` keyword'una ulaşana kadar tüm case'ler çalıştırılır veya hiçbir koşul uyuşmazsa `default` keyword'u içerisindeki kodlar çalıştırılır.

- `switch` yapısında koşulu güncellemek, silmek veya yeni bir koşul oluşturmak kolay iken `else if` veya `if else` yapılarında zordur.

- Eğer ikiden fazla koşula sahipsek `else if` veya `if else` ile oluşturduğumuz koşulların çalışma hızı `switch` ile oluşturduğumuz yapıların hızından daha yavaş olacaktır.
