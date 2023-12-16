# JavaScript Operatörleri

Merhaba arkadaşlar bu yazıda JavaScript'de operatörlere ve en çok kullanılan operatör türlerine değineceğiz.

Yazıda:

- Operatör ve operand kavramına.

- JavaScript operatörlerine.

- Aritmetiksel (Arithmetic) operatörlere.

- Atama (Assignment) operatörlerine.

- Kıyaslama (Comparison) operatörlerine.

- String operatörlere.

- Mantıksal (Logical) operatörlere.

- Bit türündeki (Bitwise) operatörlere.

- Type operatörlerine.

- Operatör öncelliğine.

Değineceğim.

İyi okumalar dilerim.


## Operator ve Operand Kavramları

Bir JavaScript expression'da değerlere **_operand_** ve operand'lar arasında işlemler yapmamızı sağlayan işaretlere **_operator_** adı verilir.

![Operand ve operatör örneği](https://www.oreilly.com/api/v2/epubs/0596101104/files/httpatomoreillycomsourceoreillyimages108816.png "Operand ve operatörler")


## JavaScript Operatörleri

Operatörleri matematiksel işlemlerden bir script'in çalışma akışını değiştirmeye kadar çeşitli işlemlerde kullanırız. Diğer programlama dillerinde olduğu gibi JavaScript içerisinde bir çok operatör vardır.

JavaScript'de operatörler aşağıdaki gibi listelenebilir:

1. Aritmetik (Arithmetic) operatörleri.

2. Atama (Assignment) operatörleri.

3. Kıyaslama (Comparison) operatörleri.

4. String operatörler.

5. Mantıksal (Logical) operatörler.

6. Bit türündeki (Bitwise) operatörler.

7. Type operatörler.

Şimdi bunları tek tek inceleyelim arkadaşlar.


## JavaScript Aritmetik Operatörleri

Daha önce değindiğim gibi gündelik hayatta matematiksel işlemler için kullandığımız operatörleri JavaScript'de de kullanabiliriz.

Operatörlere ait işaretler ve anlamları aşağıdaki tablodaki gibidir:

| **Operator** | **Açıklama**                                                             |
| ------------ | ------------------------------------------------------------------------ |
| `+`          | Toplama işlemi yapmak için kullanılır.                                   |
| `-`          | Çıkarma işlemi için kullanılır.                                          |
| `* `         | Çarpma işlemi için kullanılır.                                           |
| `**`         | Üs alma operatörüdür. Üs alma işlemi için kullanılır.                    |
| `/ `         | Bölme işlemi için kullanılır.                                            |
| `%`          | Modul operatörü bölme işleminde kalanı almak için kullanılır.            |
| `++`         | Artırma işlemi için kullanılır. Bir değişkeni +1 olacak şekilde artırır. |
| `--`         | Çıkarma işlemi için kullanılır. Bir değişkeni -1 olacak şekilde azaltır. |

Aritmetiksel operatörlerde literal türündeki değerler de kullanılabilir.

**Örnek**



```javascript
%%javascript

// x değişkeni  sabit türündeki değerlerin toplamını depoluyor.
let x = 200 + 25;

// Konsola 225 yazdırılacaktır.
console.log(x);

```

    225


Şimdi de bazı aritmetiksel operatörlere değinelim. Örneklerde sıkça görebileceğiniz için toplama ve çıkarma gibi operatörleri es geçiyorum.


### `**` Üs Alma Operatörü

Bir sayının üssünü almak için kullanılır.

**Örnek**



```javascript
%%javascript

const x = 5;

// 5 rakamının karesini alacaktır.
let result = x ** 2;

// Konsola 25 değerini yazdıracaktır.
console.log(result);

// 5 rakamının küpünü alacaktır.
let result2 = x ** 3;

// Konsola 125 değerini yazdıracaktır.
console.log(result2);

```

    25
    125


### `%` Modul Operatörü

Bazen bir bölme işleminin sonucunda kalan değeri tam sayı olarak almak isteyebiliriz bu durumda modul operatörü kullanılır.

**Örnek**



```javascript
%%javascript

// 9'un 4'e bölümünden kalan değer konsola yazdırılır. Kalan değer 1'dir.
console.log(9 % 4);

```

    1


### `++` Operatörü

JavaScript' de bir değişkenin değerini +1 olarak artırma yöntemi olarak `++` operatörünü alternatif olarak kullanabiliriz.

**Örnek**



```javascript
%%javascript

let x = 5;

x++;

// x değişkeni yeni değer olarak 6 rakamını depolayacaktır.
console.log(x);

```

    6


### `--` Operatörü

JavaScript' de bir değişkenin değerini -1 olarak azaltma yöntemi olarak `--` operatörünü alternatif olarak kullanabiliriz.

**Örnek**



```javascript
%%javascript

let x = 10;
x--;

// x değişkeni yeni değer olarak 9 rakamını depolayacaktır.
console.log(x);

```

    9


### Operatör Öncelliği

JavaScript'de işlem öncelliği matematikte olduğu gibidir. **Bazen işlem önceliğini kendimiz ayarlamak isteriz bu durumda öncelik vermek istediğimiz expression'ları parantez içerisine alırız.**

**Örnek**



```javascript
%%javascript

// Normalde işlemin sonucu 80 olacaktır.
console.log(20 + 30 * 2);

/**
 * Bu durumda işlemin sonucu 100 olacaktır. Çünkü 20 ve 30 değerlerini parantez içinde tanımladık.
 * İşlem öncelliği buraya verilecektir.
 */
console.log((20 + 30) * 2);

```

    80
    100


**⚠️ Bir expression'da aynı seviyeden operatörler bulunması halinde işlem önceliği soldan sağa şeklinde olacak ve sonuç bu pattern'e göre oluşturulacaktır. Aynı zamanda bu JavaScript'in varsayılan davranışıdır.**

**Örnek**



```javascript
%%javascript

let x = 20 - 3 + 2;

// Sonuç 19 olacaktır.
console.log(x);

```

    19


## JavaScript Atama Operatörleri

Atama operatörleri bir değişkene veri atamak için kullanılır.

**⚠️ JavaScript'de temelde atama operatörü olarak `=` işareti kullanılır. Eşittir işareti olarak `==` veya `===` ifadelerinden faydalanırız. Bu ifadelerde [Javascript Kıyaslama Operatörleri](#javascript-kıyaslama-operatörleri) başlığı altında değineceğim çünkü bu operatörler kıyaslama işlemleri için kullanılırlar.**

JavaScript'deki atama operatörlerini listeleyecek olursak:

| **Operator** | **Örnek** | **Matematiksel Karşılığı** |
| ------------ | --------- | -------------------------- |
| `=`          | x = y     | x = y                      |
| `+=`         | x += y    | x = x + y                  |
| `-= `        | x -= y    | x = x - y                  |
| `*=`         | x \*= y   | x = x \* y                 |
| `/= `        | x /= y    | x = x / y                  |
| `%=`         | x %= y    | x = x % y                  |
| `**=`        | x \*\*= y | x = x \*\* y               |

Bir örnekle nasıl kullanıldığını görelim. Diğer operatörler de benzer mantıkla çalışır.

**Örnek**



```javascript
%%javascript

let x = 10;

let y = 5;

// Sonuç 18 olacaktır. x=x+8 yani x=10+8 ifadesinin matematiksel karşılığıdır.
console.log((x += 8));

// Sonuç 125 olacaktır y=y**3 yani y=5x5x5 ifadesinin karşılığıdır.
console.log((y **= 3));

let z;
z = "Selam" + " " + "Dostum";

// "Selam Dostum" string'i konsola yazılacaktır.
console.log(z);

```

    18
    125
    Selam Dostum


## JavaScript Kıyaslama Operatörleri

Kıyaslama operatörleri iki veya daha fazla değişkeni kıyaslamak için kullanılır. Özellikle conditional statement'ler ile birlikte iki veya daha fazla değişkenin birbiriyle durumunu sorgulayarak ve program akışını değiştirmek için kullanılır.

**⚠️ Kıyaslama operatörleri bir kıyaslama işleminin sonucu doğru ise `true`, yanlış ise `false` değerini döndürür.**

Kıyaslama operatörlerini listelersek:

| **Operator** | **Açıklama**                                 |
| ------------ | -------------------------------------------- |
| `==`         | Eşittir.                                     |
| `===`        | Değişken veri tipi ve içeriği eşittir.       |
| `!=`         | Eşit değildir.                               |
| `!==`        | Değişken veri tipi ve içeriği eşit değildir. |
| `>`          | Büyüktür.                                    |
| `<`          | Küçüktür.                                    |
| `>=`         | Büyük eşittir.                               |
| `<==`        | Küçük eşittir.                               |
| `?`          | Ternary operatör.                            |

Burada önemli olduğunu düşündüğüm operatörlere değineceğim. Diğer operatörleri örnekleri gördükçe ne işe yaradığını hemen anlayabilirsiniz.


**❗ Nasıl armut ile elmayı kıyaslayamıyorsak JavaScript'de de kıyaslanacak değişkenlerin aynı türde olması gerekir. Aksi taktirde kıyaslama sonucunda anlam veremediğimiz sorunlar ile karşılaşabiliriz. değişkenleri birbirine dönüştürmek için JavaScript bir takım metotları içerisinde barındırır fakat konu kapsamında olmadığından ötürü bu metotlara değinmiyorum.**

**İstisna olarak sayısal özelliğe sahip veri tipi string olan bir değişken ile number veri tipine sahip bir değişken kıyaslandığında JavaScript otomatik olarak string veri tipine sahip değişkeni sayısal değere çevirir ve kıyaslama işlemini gerçekleştirir.**

**Örnek**



```javascript
%%javascript

const x = 5;
const y = "5";

// Konsola "true" ifadesi yazdırılacaktır.
console.log(x == y);

```

    true


**⚠️ String değerler alfabetik olarak kıyaslanır. İki sayısal string kıyaslandığında bazen sonuç istediğimiz gibi üretilmez. Örnek üzerinden açıklayalım.**

**Örnek**



```javascript
%%javascript

/**
 * Konsola "false" ifadesi yazdırılacaktır.
 *
 * JavaScript string türde sayısal değer içeren iki değişkeni kıyaslarken 32 rakamının ilk rakamına
 * bakarak alfabetik şekilde değerlendirme yapacaktır.
 * 3 rakamı 4 rakamından küçük olduğu için sonuç false olacaktır.
 * 
 * Konsola "false" ifadesi yazdırılır.
 */
console.log("4" < "32");

```

    false


### `==` Operatörü

iki veya daha fazla değişkenin depoladığı verileri **içeriği** bakımından kıyaslar. **Kıyaslama sonucu doğru ise `true`, değilse `false` olacak şekilde değer döndürür.**

**Örnek**



```javascript
%%javascript

const x = 5;
const y = 5;

// x ile y değişkeni kıyaslanacak aynı veriyi depoladığı için konsola "true" ifadesi yazdırılacaktır.
console.log(x == y);

const m = 8;
const n = 7;

// m ile n değişkeni kıyaslanacak aynı veriyi depolamadığı için konsola "false" ifadesi yazdırılacaktır.
console.log(m == n);

```

    true
    false


### `===` Operatörü

iki veya daha fazla değişkenin depoladığı verileri **içeriği ve veri tipi** bakımından kıyaslar. **Kıyaslama sonucu doğru ise `true`, değilse `false` olacak şekilde değer döndürür.**

**Örnek**



```javascript
%%javascript

const x = 5;
const y = 5;

/** 
 * x ile y değişkeni kıyaslanacak aynı veriyi ve veri tipini depoladığı için konsola "true" ifadesi 
 * yazdırılacaktır.
 */
console.log(x === y);

const m = 8;

// ⚠️ n değişkeni string 8 değerini depoluyor.
const n = "8";

/**
 * m ile n değişkeni kıyaslanacak aynı veriyi depolamasına rağmen farklı  
 * veri tipine sahip oldukları için konsola "false" ifadesi yazdırılacaktır.
 */
console.log(m === n);

```

    true
    false


### `!=` Operatörü

iki veya daha fazla değişkenin depoladığı verileri **içeriği** bakımından kıyaslar. **Kıyaslama sonucu doğru ise `false`, değilse `true` olacak şekilde değer döndürür.**

**💡 Bunu şu şekilde aklınızda tutabilirsiniz. Sonucu `true` olan bir expression'ı `false`, sonucu `false` olsan bir expression'ı `true` olarak değerlendirir.**

**Örnek**



```javascript
%%javascript

const x = 5;
const y = 5;

// x ile y değişkenleri kıyaslanacak aynı veriyi depoladığı için konsola "false" ifadesi yazdırılacaktır.
console.log(x != y);

const m = 8;
const n = 7;

// m ile n değişkenleri kıyaslanacak aynı veriyi depolamadığı için konsola "true" ifadesi yazdırılacaktır.
console.log(m != n);

```

    false
    true


### `!==` Operatörü

iki veya daha fazla değişkenin depoladığı verileri **içeriği ve veri tipi** bakımından kıyaslar. **Kıyaslama sonucu doğru ise `false`, değilse `true` olacak şekilde değer döndürür.**

**💡 Bunu şu şekilde aklınızda tutabilirsiniz. Sonucu `true` olan bir expression'ı `false`, sonucu `false` olan bir expression'ı `true` olarak değerlendirir. `!=` operatörü ile arasındaki fark expression'ı içerik ve veri tipi olacak şekilde değerlendirir.**

**Örnek**



```javascript
%%javascript
const x = 5;
const y = 5;

/** 
 * x ile y değişkenleri kıyaslanacak aynı veriyi ve veri tipine depoladığı için konsola "false" ifadesi 
 * yazdırılacaktır.
 */
console.log(x !== y);

const m = 8;

// ⚠️ n değişkeni string 8 değerini depoluyor.
const n = "8";

/**
 * m ile n değişkenleri kıyaslanacak aynı veriyi depolamasına rağmen farklı veri tipini depoladığı için
 * konsola "true" ifadesi yazdırılacaktır. 
 */
console.log(m !== n);

```

    false
    true


### `?` Operatörü

JavaScript'de `?` işareti **_ternary_** operatör olarak isimlendirilir.

Ternary operatörü bir conditional operatördür. Yani bir condition'a göre işlemleri gerçekleştirir ve programın akışını değiştirir.

**➖ Ternary Conditional Operatörü ile `If` Conditional Statement Arasındaki Fark**

**Ternary ile oluşturulan kıyaslama işlemleri genelde tek satırdan oluşur ve iki değişkeni kıyaslamak için kullanılır. İkiden fazla durumunun kıyaslama yapılması halinde `if` keyword'u ile yapılan kıyaslama işlemleri tercih edilir. Bu sayede kodun daha kolay okunup yönetilmesi amaçlanır.**

**Örnek**



```javascript
%%javascript

const a = 4;
const b = 4;

// a ile b değişkenlerinin değerlerini kıyaslıyoruz ve sonucu result değişkenine depoluyoruz.
const result = a == b;

/**
 * Eğer result'ın depoladığı kıyaslama sonucu true ise "Evet..." ile başlayan metin
 * değilse "Hayır.." ile başlayan metin konsola yazdırılacaktır.
 * Değerleri değiştirin ve sonucu gözlemleyin.
 */
result
  ? console.log("Evet iki değişkenin depoladığı veri birbirine eşittir.")
  : console.log(
      "Hayır iki değişkenin depoladığı veri birbirine eşit değildir."
    );

```

    Evet iki değişkenin depoladığı veri birbirine eşittir.


## JavaScript String Operatörleri

JavaScript'de temelde 2 adet string operatör vardır bunlar:

| **Operator** | **Açıklama**                                                                                                       |
| ------------ | ------------------------------------------------------------------------------------------------------------------ |
| `+ `         | Ekleme operatörü. Bir string ifadeyi başka bir string değere ekler.                                                |
| `+= `        | Ekleme ve atama operatörü. Bir string ifadeyi başka bir string ifadeye ekler ve sonucu bir değişken içine depolar. |

Şimdi bunları inceleyelim arkadaşlar.


### `+` Ekleme Operatörü

String değişkenlerde `+` operatörü **ekleme operatörü olarak ifade edilir.** Yani iki sting değişken toplanmaz, birbirine eklenir.

**Örnek**



```javascript
%%javascript

// String veri tipindeki 5 değerini value1 isimi değişkene depoluyoruz.
const value1 = "5";

// String veri tipindeki 15 değerini value2 isimi değişkene depoluyoruz.
const value2 = "15";

//❗ Konsola "515" ifadesi yazdırıldığına dikkat edin.
console.log(value1 + value2);

```

    515


### `+=` Ekleme ve Atama Operatörü

Bir string ifadeye başka bir string ifadeyi ekledikten sonra elde edilen sonucu değişken içerisinde depolayabiliriz.



```javascript
%%javascript

let value1 = "Kemal";
let value2 = "Atatürk";

// Ekleme ve atama operatörü, örnekte value1=value1+value2 ifadesini denktir.
value1 += value2;

// Konsola "KemalAtatürk "yazdırılacaktır.
console.log(value1);

```

    KemalAtatürk


**⚠️ Numerik özellikli string değerler dışındaki diğer string değerleri matematiksel işlemlerde sonuca katkıda bulunmazlar. Şayet bir string matematiksel ifade içerisinde kullanılırsa işlem sonucunun veri tipi string olacaktır. Bu durum string'in bulunduğu yere göre sonucu etkiler. Numerik özellikli string değerler için durum biraz daha farklıdır. Daha detaylı bilgi almak için [JavaScript Numerik Özellikli String Değerler](js07-numeric-data-type.ipynb#javascript-numerik-özellikli-string-değerler) başlığına bakabilirsiniz.**

<!-- [#1](https://github.com/eminaltan/learn-web/issues/1) -->

**JavaScript'de expression'lar (ifadeler) soldan sağa şekilde değerlendirilir. Yani Javascript ifadenin nerede string olacağını bu pattern'e göre belirler.**

**Örnek**



```javascript
%%javascript

var x = 4 + 3 + "1";

// Konsola "71" yazdırılacaktır.
console.log(x);

var y = "1" + 4 + 3;

// Konsola "143" yazdırılacaktır.
console.log(y);

```

    71
    143


## JavaScript Mantıksal Operatörler

Mantıksal operatörler JavaScript'de özellikle kıyaslama işlemlerinde sıklıkla kullanılan operatör grubudur. Bu bakımdan anlaşılması önem taşır.

Mantıksal operatörleri listeleyecek olursak:

| **Operator** | **Açıklama**  |
| ------------ | ------------- |
| `&&`         | Mantıksal AND |
| `\|\|`       | Mantıksal OR  |
| `!`          | Mantıksal NOT |


### `&&` Mantıksal **_AND_** Operatörü

Expression içerisindeki ifadeleri kıyaslar **her ifadenin doğru olması durumunda tüm sonuç `true` olacaktır.**

**Herhangi bir ifadenin sonucunun `false` olması durumunda tüm sonuç `false` olacaktır.**



```javascript
%%javascript

let x = 10;
let y = 5;

/**
 * y 'nin 3'den büyük olması ve x'in 20'den küçük olduğunu biliyoruz.
 * Bu durumda ifadenin sonucu true olur.
 */
const result = 3 < y && x < 20;

// Konsola "true" ifadesi yazılacaktır.
console.log(result);

// x'e yeni değer depolayalım.
x = 30;

// Expression'un sonucunu result2 adında değişkene depolayalım.
const result2 = 3 < y && x < 20;

/**
 * Konsola "false" ifadesi yazılacaktır. Çünkü 30<20 ifadesi doğru değildir ve false değer döndürür
 * bu da tüm sonucu false yapar.
 */
console.log(result2);

```

    true
    false


### `||` Mantıksal **_OR_** Operatörü

Expression içerisindeki ifadeleri kıyaslar **herhangi bir ifadenin doğru olması durumunda tüm sonuç `true` olacaktır.**

**Şayet tüm ifadelerin sonucu `false` olursa tüm sonuç `false` olacaktır.**

**Örnek**



```javascript
%%javascript

// Tek satırda aynı tür değişkenleri tanımlayabildiğimizi hatırlayalım bu arada.
let x = 30, y = 5, z = 2;

/**
 * Son iki ifadenin sonucu false'dır.
 * Fakat ilk ifadenin sonucu true olması sebebi ile tüm sonuç true olarak değerlendirilir.
 */
const result = 3 < y || x < 20 || z == 0;

// Konsola "true" ifadesi yazdırılacaktır.
console.log(result);

// Tüm ifadelerin sonucu false olması sebebi ile tüm sonuç false olarak değerlendirilir.
result2 = 10 < y || x < 20 || z == 0;

// Konsola "false" ifade yazılır.
console.log(result2);

```

    true
    false


### `!` Mantıksal **_NOT_** Operatörü

Bir expression sonucunun tersini alır. Yani ifade `true` ise `false`, `false` ise `true` sonuçlanır.



```javascript
%%javascript

// x'e bir değer depolandığı için mantıksal olarak true özelliği taşır.
let x = 20;

/**
 * Normalde konsola true ifadesi yazılırdı. Fakat burada NOT operatörü kullanıldığı için true olan
 * sonucun tersi alınacaktır. Yani sonuç false olacak ve konsola "false" yazdırılacaktır.
 */
console.log(!(x < 50));

// y değişkeni undefined veri tipine sahiptir. Mantıksal olarak false değerine sahiptir.
let y;

// Konsola "false" ifadesi yazdırılacak.  Boolean() metodu ile değişkenin boolean türünden değerini öğrenebiliriz.
console.log(Boolean(y))

// y değişkenin depoladığı değerin tersini aldı. Yani false değerini true yaptı. Konsola "true" ifadesi yazılır.
console.log(!y);
```

    false
    false
    true


**❗ Mantıksal atama operatörlerinin, mantıksal operatörler ile ilişkisi olmakla birlikte aynı anlama gelmemektedir. Mantıksal atama operatörleri ES (2020) ile JavaScript'e dahil olmuştur. Bu bakımdan 2020 yılından önce release edilen tarayıcılarda çalışmayabilir.**

Mantıksal atama operatörlerini listelersek:

| **Operator** | **Örnek** | **Karşılığı**      |
| ------------ | --------- | ------------------ |
| `&&= `       | x &&= y   | x = x && (x = y)   |
| `\|\|=`      | x \|\|= y | x = x \|\| (x = y) |
| `??=`        | x ??= y   | x = x ?? (x = y)   |

Şimdi bu operatörleri tek tek inceleyelim.


### `&&=` Mantıksal **_AND_** Atama Operatörü

**Bir expression veya statement'ın sonucunun `true` olması durumunda ikinci değer değişkene atanır.**

**Örnek**



```javascript
%%javascript

let x = 35;

/**
 * x değişkeni kullanıcı tanımlı değer depoladığı için true mantıksal değerine sahiptir.
 * Bu durumda x değişkenine yeni bir değer (8) rakamı depolanır.
 */
x &&= 8;

// 8 rakamı konsola yazdırılacaktır.
console.log(x);

/**
 * y değişkeni kullanıcı tanımı bir depolamıyor. Varsayılan olarak değeri undefined'dir.
 * Bu da mantıksal anlamda false ifadesine denk gelir.
 */
let y;

// y değişkeni kullanıcı tanımlı bir değer depolamadığı için yeni değer sahip olmayacaktır.
y &&= 20;

// Konsola "undefined" mesajı yazılır.
console.log(y);

```

    [33m8[39m
    [90mundefined[39m


### `||=` Mantıksal **_OR_** Atama Operatörü

**Bir expression veya statement'ın sonucunun `false` olması durumunda ikinci değer değişkene atanır.**

**💡 `||=` operatörü ile `&&=` operatörü birbirine zıttır. Bu bağlamda birinin mantığını kavrarsanız diğerininkini de kavrayabilirsiniz.**

**Örnek**



```javascript
%%javascript

/**
 * y değişkeni kullanıcı tanımı bir değer depolamıyor. Varsayılan olarak değeri undefined'dir.
 * Bu da mantıksal anlamda false ifadesine denk gelir.
 */
let y;

// y değişkeni kullanıcı tanımlı bir değer depolamadığı için yeni değeri 20 olarak tanımlanacaktır.
y ||= 20;

// Konsola 20 rakamı yazılır.
console.log(y);

let x = 35;

/**
 * x değişkeni kullanıcı tanımlı değer depoladığı için true mantıksal değerine sahiptir.
 * Bu durumda x değişkenine yeni bir değer depolanmayacaktır.
 */
x ||= 8;

// 35 rakamı konsola yazdırılacaktır.
console.log(x);

```

    [33m20[39m
    [33m35[39m


### `??=` **_Nullish Coalescing Assignment_** Operatörü

**Bir değişkenin depoladığı verinin **_undefined_** veya **_null_** olması durumunda ikinci değer değişkene atanır.**

**Örnek**



```javascript
%%javascript

// x değişkeninin default değeri undefined'dır.
let x;

// x değişkeninin default değer undefined olması sebebi ile x'e 80 rakamı depolanacaktır.
x ??= "80";

// 80 rakamı konsola yazdırılır.
console.log(80);

```

    [33m80[39m


## JavaScript Bitwise Operatörler

**_Bit_**[^1] seviyesinde kıyaslama işlemleri için kullanılır. işlemler **_binary_**[^2] sayısal düzeninde gerçekleşir ve sonuç **_decimal_**[^3] olarak depolanır.

Önemli bir takım bitwise operatörleri listelersek:

| **Operator** | **Açıklama**                |
| ------------ | --------------------------- |
| `&`          | Bit düzeyinde mantıksal AND |
| `\|`         | Bit düzeyinde mantıksal OR  |
| `~`          | Bit düzeyinde mantıksal NOT |
| `^`          | Bit düzeyinde mantıksal XOR |

Şimdi bunları inceleyelim arkadaşlar.


### `&` **_Bitwise AND_** Operatörü

Bit düzeyinde mantıksal **_AND_** işlemi gerçekleştirmek için kullanılır. Decimal değeri binary sayısal düzenine çevirir sonrasında bit'leri kıyaslar ve elde edilen sonucu tekrar decimal sayı sistemine çevirir.

İşlem aşağıdaki tablo mantığına göre gerçekleşir:

| **x'in Bit Değeri** | **y'nin Bit Değeri** | **x & y Sonucu** |
| ------------------- | -------------------- | ---------------- |
| 0                   | 0                    | 0                |
| 0                   | 1                    | 0                |
| 1                   | 0                    | 0                |
| 1                   | 1                    | 1                |

**Örnek**



```javascript
%%javascript

// x değişkenin binary değeri 101'dir.
let x = 5;

// x değişkenin binary değeri 011'dir.
let y = 3;

/**
 *  x = x & y ifadesinin dengidir. Bit seviyesinde AND işlemi gerçekleştiriliyor.
 *  Sonuç 001 olacak ve değer x değişkenine aktarılacaktır.
 */
x &= y;

// 001 decimal  karşılığı 1'dir ve konsola 1 rakamı yazdırılacaktır.
console.log(x);

```

    1


### `|` **_Bitwise OR_** Operatörü

Bit düzeyinde mantıksal **_OR_** işlemi gerçekleştirmek için kullanılır. Decimal değeri binary sayısal düzenine çevirir sonrasında bit'leri kıyaslar ve elde edilen sonucu tekrar decimal sayı sistemine çevirir.

**İşlem her bit için ayrı ayrı gerçekleştirilir.**

İşlem aşağıdaki tablo mantığına göre gerçekleşir:

| **x'in Bit Değeri** | **\|x Sonucu** |
| ------------------- | -------------- |
| 0                   | 0              |
| 0                   | 1              |
| 1                   | 1              |
| 1                   | 1              |

**Örnek**



```javascript
%%javascript

// 38 rakamının karşılığı 100110'dir.
let x = 38;

// 45 rakamının karşılığı 101101'dir.
let y = 45;

// 101111 decimal  karşılığı 47'dir ve konsola 47 rakamı yazdırılacaktır.
x |= y;
console.log(x);

```

    47


### `~` **_Bitwise NOT_** Operatörü

Bit düzeyinde mantıksal **_NOT_** işlemi gerçekleştirmek için kullanılır. Decimal değeri binary sayısal düzenine çevirir sonrasında bit'leri kıyaslar ve elde edilen sonucu tekrar decimal sayı sistemine çevirir.

**İşlem her bit için ayrı ayrı gerçekleştirilir.**

İşlem aşağıdaki tablo mantığına göre gerçekleşir:

| **x'in Bit Değeri** | **~x Sonucu** |
| ------------------- | ------------- |
| 0                   | 1             |
| 1                   | 0             |

Kısaca bit değerlerini ters çevirir.

**Örnek**



```javascript
%%javascript

// 5 rakamının karşılığı 0101'dir.
let x = 5;

// 1010'un decimal karşılığı 10'dur ve konsola 10 rakamı yazdırılacaktır.
console.log(~x);
```

    10


### `^` **_Bitwise XOR_** Operatörü

Bit düzeyinde mantıksal **_XOR_** işlemi gerçekleştirmek için kullanılır. Decimal değeri binary sayısal düzenine çevirir sonrasında bit'leri kıyaslar ve elde edilen sonucu tekrar decimal sayı sistemine çevirir.

İşlem aşağıdaki tablo mantığına göre gerçekleşir:

| **x'in Bit Değeri** | **y'nin Bit Değeri** | **x ^ y Sonucu** |
| ------------------- | -------------------- | ---------------- |
| 0                   | 0                    | 0                |
| 0                   | 1                    | 1                |
| 1                   | 0                    | 1                |
| 1                   | 1                    | 0                |

**Örnek**



```javascript
%%javascript

// 20 rakamının binary karşılığı 10100'dır.
let x = 20;

// 28 rakamının binary karşılığı 11100'dır.
let y = 28;

// x=x^y ifadesine denktir.
x ^= y;

// 1000 binary değerinin decimal karşılığı 8'dir.
console.log(x);

```

    8


## JavaScript Type Operatörleri

JavaScript'de bir çok type operatörü vardır. Type operatörleri bir değişkeni başka bir değişkene dönüştürmek için veya değişkenin türünü ve veri tipini öğrenme gibi işlemler için kullanılır.

En çok kullanılan type operatörlerini listelersek:

1. `typeof()`

2. `instanceof `

Diğer type operatörlerine ayrı bir başlık altında değineceğim. Çünkü asıl konumuz operatörleridir. Type operatörleri aynı zamanda metot (fonksiyon) olma özelliği taşır.


### `typeOf` Operatörü/Metodu

Bir değişkenin depoladığı değere göre veri türünü öğrenmemizi sağlar.

**Örnek**



```javascript
%%javascript

const x = 4;

// "number" ifadesi konsola yazılır. x değişkeninin veri tipi sayısal özelliklidir.
console.log(typeof x);

const y = "deneme";

// "string" ifadesi konsola yazılır. y değişkeninin veri tipi string özelliklidir.
console.log(typeof y);

const z = false;
// "boolean" ifadesini konsola yazdırır. z değişkenin veri tipi boolean özelliklidir.
console.log(typeof z);

```

    number
    string
    boolean


### `instanceof` Operatörü/Metodu

Object veri türü özelliğine sahip değişkenlerde birden fazla kullanım yöntemi olmakla birlikte değişkenin veri türünü belirlemede, bir özelliğin nesne ile ilişkisini anlamada veya katılım izleme işlemlerini gerçekleştirmek için kullanılır.

**💡 Özellikle object veri türü özellikli değişkenlerde debug işlemleri için kullanışlı olabilir.**

**Örnekler**



```javascript
%%javascript

const student = { name: "Betül", surname: "Şavluk" };

/**
 * student  değişkeni nesne özellikli olup/olmadığı ternary operatör ile sınanıyor
 * sonuç result'a aktarılıyor.
 */
const result =
  student instanceof Object
    ? "Evet student nesne özellikli bir değişkendir."
    : "Hayır student nesne özellikli bir değişken değişkendir.";

// Konsola "Evet..." ile başlayan mesaj yazdırılacaktır.
console.log(result);

// Konsola "student değişkeninin veri tipi object'dir." mesajı yazılacaktır.
console.log("student değişkeninin veri tipi" + " " + typeof student + "'dir.");

```

    Evet student nesne özellikli bir değişkendir.
    student değişkeninin veri tipi object'dir.



```javascript
%%javascript

// Örnekte student değişkeni için object özellikleri sorgulanıyor.

function Student(studentName) {
  this.name = studentName;
}

const student = new Student();

// true değeri döndürür. Çünkü student değişkeni Student constructor'un örneğidir.
console.log(student instanceof Student);

// true değeri döndürür. Çünkü student değişkeni aynı zamanda Object örneğidir.
console.log(student instanceof Object);

// false değeri döndürür. Çünkü student değişkeni Array örneği değildir.
console.log(student instanceof Array);

```

    true
    true
    false


[^1]: "Bit," kısaltılmış haliyle "binary digit" kelimesinin baş harflerinden oluşan bir terimdir ve bilgisayar bilimlerinde temel bir kavramdır. Bit, en küçük veri birimi olarak bilinir ve yalnızca iki değere sahip olabilen bir elektronik veya dijital bilgi parçasını temsil eder. Bu iki değer 0 ve 1'dir.
[^2]: "Binary" terimi, bilgisayar bilimlerinde ve elektronikte oldukça yaygın olarak kullanılan bir terimdir ve ikili (2 temel değer) sayı sistemini ifade eder. İkili sistem, yalnızca iki sembol veya değer içeren bir sayı sistemidir. Bu iki sembol genellikle "0" ve "1" olarak temsil edilir.
[^3]: "Decimal," yaygın olarak ondalık sayı sistemini ifade eden bir terimdir. Ondalık sayı sistemi, 10 rakamdan oluşur ve her bir rakamın temsil ettiği değer 0 ila 9 arasında değişir. Ondalık sistemi kullanarak herhangi bir sayıyı ifade edebilirsiniz. Bu sistemde her haneli bir sayı, 10'un üssüne dayalı bir değer temsil eder.

