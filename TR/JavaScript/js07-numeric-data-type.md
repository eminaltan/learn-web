# JavaScript Number Veri Türü ve Veri Tipi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_number_** veri türlerini ve veri tiplerini inceleyeceğiz.

Yazıda:

- Number veri türüne ve veri tipine.
- Exponential notation kavramına.
- Precision kavramı ve türlerine.
- Numerik özellikli string değerlere.
- `NaN` kavramına.
- Infinity kavramına.
- Hexadecimal değerlere ve aritmetiksel işlemlere.
- Object tipindeki number türlerine.

Değineceğim.

İyi okumalar dilerim.


## JavaScript Number Veri Türü

JavaScript'de iki sayısal veri türü vardır. Bunlardan biri **_BigInt_** diğeri ise **_Number_** veri türüdür. Bu kısımda number veri türünü inceleyeceğiz.

Number veri türü primitive özelliklidir ve **_immutable_** yapıdadırlar yani değiştirilemezler.

JavaScript'de number veri tipine sahip değerler ondalıklı veya tam sayı olarak ifade edilebilirler.

**Örnek**



```javascript
%%javascript

// Her iki değişkenin depoladığı değer ve veri tipi bakımından aynıdır.
let x = 20.0;
let y = 20;

// Konsola true ifadesi yazdırılacaktır.
console.log(x === y);

```

    [33mtrue[39m


**⚠️ Bir çok programlama dilinde sayısal değerler byte (8-bit), short (16-bit), int (32-bit), long (64-bit) olarak kategorize edilir.**

**JavaScript'de sayısal değerler daima double (64-bit floating point) özelliktedirler.**


### Exponential Notation

Çok büyük sayısal değerler bilimsel olarak ifade edilebilir.

**Örnek**



```javascript
%%javascript

let y = 123e5;

// 12300000 değeri konsola yazdırılır.
console.log(y);

let z = 123e-5; // 0.00123

// 0.00123 değeri konsola yazdırılır.
console.log(z);

```

    [33m12300000[39m
    [33m0.00123[39m


**⚠️ Matematiksel bir expression'a (ifadeye) numerik özellikli string değer dahil olduğunda sonuç veri tipinin string türünde oluşacağını unutmayın.**

**Bu durum sayısal string değerlerin kullanım yerlerine ve operatör türüne göre değişiklik gösterir. Detaylı bilgi almak için [JavaScript Numerik Özellikli String Değerler](#javascript-numerik-özellikli-string-değerler) başlığını ziyaret edebilirsiniz.**

**Örnek**



```javascript
%%javascript

let x = 10;
let y = 20;
let z = "Sonuç: " + x + y;

// Sonuç 1020 şeklinde ifade konsola yazdırılacaktır.
console.log(z);

```

    Sonuç: 1020


### JavaScript Precision Kavramı ve Türleri

JavaScript'de **_precision_**, sayıların ondalık basamaklarındaki hassasiyeti veya kesirli sayıların kaç basamakla temsil edildiğini belirtmek için kullanılan bir terimdir. Bu terim, özellikle hassasiyet gerektiren sayılarla yapılan matematiksel işlemlerde önemlidir.

JavaScript'de 2 tür precision vardır:

1. Integer

2. Floating

Şimdi bunları inceleyelim.


#### Integer Precision

Integer veri türleri ondalıklı veya bilimsel değer ile ifade edilmedikleri sürece 15 haneye kadar sayısal doğruluğa sahiptirler.

**Örnek**



```javascript
%%javascript

let x = 999999999999999;

// Konsola 999999999999999 değeri yazdırılır.
console.log(x);

let y = 9999999999999999;

// Konsola 10000000000000000 değeri yazdırılır.
console.log(y);

```

    [33m999999999999999[39m
    [33m10000000000000000[39m


Decimal değerlerinde maksimum ulaşabileceği hane sayısı 17'dir.


#### Float Precision

Ondalıklı değerler için kullanılır.

**❗ Ondalık sayılarla yapılan aritmetiksel işlemlerin sonucu %100 doğru olmayabilir.**

**Örnek**



```javascript
%%javascript

let x = 0.2 + 0.1;

// 0.30000000000000004 değer konsola yazdırılacaktır.
console.log(x);

/**
 * Bu sorunu çözmek için ondalıklı sayı tam sayıya çevrilir
 * aritmetiksel işlem gerçekleştirilir ve son olarak elde edilen değer
 * hangi sayısal sistemde kullanılacaksa o sayıya bölünür.
 */

// Ondalık sayılar 10'luk sisteme çevriliyor.
let y = (0.2 * 10 + 0.1 * 10) / 10;

// 0.3 değeri konsola yazdırılacaktır.
console.log(y);

```

    [33m0.30000000000000004[39m
    [33m0.3[39m


### JavaScript Numerik Özellikli String Değerler

String veri türleri rakamlardan oluşabilir. Bu durumdaki string değerler **_numerik özellikli string_** olarak ifade edilir.

**❗ Numerik özellikli string değerler number veri tipine dönüştürülür ve aritmetiksel operatörler kullanılarak matematiksel işlemler gerçekleştirilebilir. Sonucun veri tipi number olacaktır.**

**Bu durum `+` operatörü için geçerli değildir. `+` operatörünün string değerler için ekleme fonksiyonunu gerçekleştirdiğini hatırlayınız.**

**Örnek**



```javascript
%%javascript

let x = "100";
let y = "10";

// 10 rakamı konsola yazdırılacaktır.
console.log("Sonuç= "+ (x / y)+ " işlem sonucunun veri tipi "+typeof (x/y)+" 'dır." );

// 1000 rakamı konsola yazdırılacaktır.
console.log("Sonuç= "+ (x * y)+ " işlem sonucunun veri tipi "+typeof (x*y)+" 'dır." );

// 90 rakamı konsola yazdırılacaktır.
console.log("Sonuç= "+ (x - y)+ " işlem sonucunun veri tipi "+typeof (x-y)+" 'dır." );

// ⚠️ 10010 rakamı konsola yazdırılacaktır. İşlem sonucunun veri tipinin string olduğuna dikkat edelim.
console.log("Sonuç= "+ (x + y)+ " işlem sonucunun veri tipi "+typeof (x+y)+" 'dir." );

```

    Sonuç= 10 işlem sonucunun veri tipi number 'dır.
    Sonuç= 1000 işlem sonucunun veri tipi number 'dır.
    Sonuç= 90 işlem sonucunun veri tipi number 'dır.
    Sonuç= 10010 işlem sonucunun veri tipi string 'dir.


### JavaScript `NaN` Not a Number Terimi

`NaN` değeri JavaScript'de rezerv edilmiş bir keyword olup author tanımı işlemlerde kullanılamaz. (Örneğin bir değişken ismi `NaN` ile başlayamaz.)

`NaN` değeri aritmetiksel işlem sonucunun sayısal veya rakamsal bir sonuç üretmediğini ifade etmek için kullanılır.

**Örnek**



```javascript
%%javascript

/**
 * NaN ifadesi konsola yazdırılacaktır.
 * Çünkü 10/Kamyon expression'un sonucu sayısal veya rakamsal bir değer değildir.
 */
console.log(10 / "Kamyon");

```

    [33mNaN[39m


**⚠️ Bu durum string değerin numerik özellikli olması durumunda değişir ve işlem sonuç verir.**

**Örnek**



```javascript
%%javascript

// 5 rakamı konsola yazdırılır.
console.log(100 / "20");

```

    [33m5[39m


Sonucu `NaN` olan bir ifade ile aritmetiksel işlem yaptığımızda sonuç yine `NaN` olacaktır.

**Örnek**



```javascript
%%javascript

let x = NaN;

let y = 10;

let z = x + y;

// Konsola NaN ifadesi yazdırılacaktır.
console.log(z);

```

    [33mNaN[39m


`NaN` ifadesinin tipi number'dır. Eğer `typeOf()` metodunu `NaN` için kullanırsak konsola "number" ifadesi yazılır.

**Örnek**



```javascript
%%javascript

// Konsola number ifadesi yazdırılacaktır.
console.log(typeof NaN)

```

    number


Bir expression'un sonucunun `NaN` olup/olmadığını `isNaN()` metodu ile sorgulayabiliriz.

Expression sonucu `NaN` değerini depolamışsa `isNaN()` fonksiyonu `true` aksi durumda `false` değerini geri dönderir.

**Örnek**



```javascript
%%javascript

// İşlemin sonucu NaN olarak sonuçlanacak ve NaN değer z değişkeninin içerisine depolanacaktır.
let z = 20 / "Kalem";

/**
 * z değişkeninin NaN özellikli olup/olmadığını isNaN() metodu ile sorgularız.
 * z değişkeni NaN özellik olması sebebi ile sonuç true olarak konsola yazdırılacaktır.
 */
console.log(isNaN(z));

let m = "10" / 5;

// Konsola false ifadesi yazdırılacaktır. Çünkü işlemin sonucu bir değer üretiyor.
console.log(isNaN(m));

```

    [33mtrue[39m
    [33mfalse[39m


### JavaScript Infinity

Bir değerin maksimum veya minimum alabileceği değeri ifade etmek için kullanılır.

`infinity` keyword'u özellikle çıkış koşulunu tam olarak belirleyemediğimiz `while` döngülerinde faydalı olabilir.

**Örnek**



```javascript
%%javascript

let myNumber = 2;

/**
 * Sonuç infinity yani sonsuz değer olana kadar döngü çalışır.
 * Sonuç infinity olduğunda döngü sonlanır.
 */

while (myNumber != Infinity) {
  myNumber = myNumber * myNumber;
  console.log(myNumber);
}

```

    [33m4[39m
    [33m16[39m
    [33m256[39m
    [33m65536[39m
    [33m4294967296[39m
    [33m18446744073709552000[39m
    [33m3.402823669209385e+38[39m
    [33m1.157920892373162e+77[39m
    [33m1.3407807929942597e+154[39m
    [33mInfinity[39m


### JavaScript Hexadecimal Değerler

**_Hexadecimal_**[^1] değerler JavaScript'de number özellikli veri türlerindendir.

Hexadecimal değer otomatik olarak sayısal değere dönüştürülmeye çalışılır.

**Örnek**



```javascript
%%javascript

// 255 rakamı konsola yazdırılır.
console.log(0xff);

```

    [33m255[39m


**💡 Hexadecimal değerler arasında aritmetik operatörler kullanılabilir.**

**Örnek**



```javascript
%%javascript

// 204 rakamının karşılığı
let x = 0xcc;
console.log(parseInt(x, 10))

// 188 rakamının karşılığı
let y = 0xbc;
console.log(parseInt(y, 10))

// Konsola 16 rakamı yazılır.
console.log(x - y);


// Konsola 392 rakamı yazılır.
console.log(x + y);

// Konsola 38352 rakamı yazılır.
console.log(x * y);

// Konsola 1.0851063829787233 rakamı yazılır.
console.log(x / y);

```

    [33m204[39m
    [33m188[39m
    [33m16[39m
    [33m392[39m
    [33m38352[39m
    [33m1.0851063829787233[39m


**⚠️ Hexadecimal değerleri kullanırken `0` rakamından sonra sayısal bir değer kullanılmaması tavsiye edilir. (`07` gibi) Çünkü bazı JavaScript yorumlayıcıları bu durumda ifadeyi hexadecimal format olarak değil de **_octal_**[^2] format olarak yorumlar.**


## JavaScript Number Veri Tipi

Number veri türü özellikli değişkenlerin veri tipleri de number olacaktır.

**Örnek**



```javascript
%%javascript

const x = 5;

console.log("x'in veri tipi " + typeof x + " 'dır.");

const y = "5";

// ⚠️ y'nin veri tipine dikkat edelim.
console.log("y'nin veri tipi " + typeof y + " 'dir.");
```

    x'in veri tipi number 'dır.
    y'nin veri tipi string 'dir.


## JavaScript Object Veri Tipinde Number Veri Türleri

Bildiğimiz üzere JavaScript'de number özellikli değişkenler normalde **_immutable_**, ilkel ve string veri tipine sahip veri türleridir.

Ancak `new` keyword'u kullanılarak object veri tipinde number veri türleri oluşturulabilir.

**⚠️ Object veri tipinde oluşturulan number özellikli bir değişken ile normal yöntem kullanılarak oluşturulan number özellikli değişkenin veri tipi birbirinden farklıdır.**

**Örnek**



```javascript
%%javascript

// number değişkeni nesne özellikli olup veri tipi object'dir.
let number = new Number(20)

console.log("number = "+number)
console.log("number değişkeninin veri tipi "+typeof number+ "' dir.")

let number2 = 20;

console.log("number2= "+number2)
console.log("number2 değişkeninin veri tipi " + typeof number2 + "' dir.")
```

    number = 20
    number değişkeninin veri tipi object' dir.
    number2= 20
    number2 değişkeninin veri tipi number' dir.


**❗ Object veri tipinde number kullanılması tavsiye edilmez. Özellikle mantıksal operatörlerin kullanıldığı expression'larda beklenmedik sonuçlar ile karşılaşabiliriz.**

**Ek olarak kodları komplike hale getireceği için kod bloklarının yavaş çalışmasına neden olacaktır.**

**Object veri tipindeki iki değişkenin kıyaslanması durumunda sonuç daima `false` olarak geri döner.**

**Örnek**



```javascript
%%javascript

const number = new String("Candan");
const number2 = new String("Murat");

/** 
 * Her iki değişken türü object veri tipine sahip olsa da tür bakımından kıyaslandıklarında birbirine eşit değildirler. 
 * Çünkü object veri tipine sahip değişkenler unique olma özelliği taşır.
 */
console.log(number===number2)

```

    [33mfalse[39m


## JavaScript Number Metotları

Bazen bir number değeri string ifadeye dönüştürmek veya bir string değeri number veri türüne dönüştürmek isteyebiliriz. JavaScript bize benzeri işlemleri yapmamızı sağlayan ön tanımlı metotlar sunar. Bu bölümde number değerler üzerinde işlemlerimizi kolaylaştıran sıkça kullanılan bir takım metotlara değineceğiz


### `toString()` Metodu

Number veri türündeki bir değeri string veri türüne çevirir.

**Örnek**



```javascript
%%javascript

const num = 5;

// num değişkeni string veri türüne çevrilecek ve veri tipi konsola yazdırılacaktır.
console.log(typeof(num.toString()))
```

    string


### `toExponential()` Metodu

Bir sayıyı üstel göstermek için kullanılır. Bu durumdaki değer bilimsel notasyonda temsil edilir. Sayı taban ve üst olmak üzere iki kısımdan oluşur.

**💡 Bu metot, özellikle büyük veya küçük sayıları daha kısa ve anlamlı bir formatta göstermek için kullanılır. Özellikle bilimsel ve matematiksel hesaplamalarda, büyük sayıları veya çok küçük sayıları daha okunabilir bir formatta temsil etmek amacıyla sıklıkla kullanılabilir.**

**Örnek**



```javascript
%%javascript

let num = 123456;

// Bilimsel notasyonda sayı 10 üzeri 5'i temsil eder. (1.23456 x 10^5) 
let bilimselNot = num.toExponential();
console.log(bilimselNot);
```

    1.23456e+5


`toExponential()` metodu bir parametre ile birlikte kullanılabilir. Bu durumda parametre ondalık basamak sayısını ifade edecektir.

**Örnek**



```javascript
%%javascript

let num = 123456;

// Ondalık basamak sayısı 2 olduğu için, sonuçtaki ondalık basamak sayısı 2 olacaktır.
let bilimselNot = num.toExponential(2);
console.log(bilimselNot);

// ⚠️ toExponential() metodu string veri tipinde sonuç döndürür.
console.log(typeof bilimselNot)
```

    1.23e+5
    string


### `toFixed()` Metodu

Ondalık değere sahip bir sayısal değerin ondalık kısmını yuvarlamak için kullanılır. Metodun döndüreceği veri tipi string olacaktır.



```javascript
%%javascript

const num = 5.1934;

// Değişkenin tam sayı kısmı döndürülecektir.
console.log(num.toFixed(0));

// Değişkenin ondalık bölümü 1 hane olacak şekilde yuvarlanır.
console.log(num.toFixed(1));

/** 
 * Değişkenin ondalık bölümü 2 hane olacak şekilde yuvarlanır.
 * ⚠️ Dikkat ettiyseniz ondalık değer kullanımı artırdıkça hassasiyette artıyor.
 */
console.log(num.toFixed(2));

// Ondalık kısmı 3 haneye yuvarlanan num değişkeninin veri tipini konsola yazdırıyoruz.
console.log(typeof(num.toFixed(3)))
```

    5
    5.2
    5.19
    string


### `toPrecision()` Metodu

Parametrede kullanılan değeri referans alarak bir sayının toplam basamak sayısını geri döndürür.

`toPrecision()` metodunun aldığı parametre, toplam basamak sayısını belirtir. Bu sayede, hem ondalık hem de tam kısım dahil olmak üzere sayının genel hassasiyetini kontrol edebiliriz. Eğer sayının tam kısmındaki basamak sayısı yetersizse, ondalık kısım daha fazla basamağa yayılabilir.

Şayet ondalıklı sayılarda kullanılırsa basamak sayısına ulaşmak için gerekirse sayıyı yuvarlar.

Bu metot, özellikle sayıların bir belirli bir hassasiyetle ifade edilmesi gereken durumlarda kullanışlıdır. Ancak, yine de dikkatli olmalıyız çünkü bu metot, sayının yuvarlanmasına neden olabilir ve bu durum, hesaplamalarda istenmeyen sonuçlara yol açabilir.

`toPrecision()` metodu string veri tipinde sonuç döndürür.

**Örnek**



```javascript
%%javascript

const num = 9.656;

// num değişkeni olduğu gibi konsola yazılır.
console.log(num.toPrecision())

// num değişkeninin ilk 2 hanesi konsola yazılır. ⚠️ Dikkat ederseniz virgülden sonraki kısım 9.7 olarak yuvarlandı.
console.log(num.toPrecision(2))

// num değişkeninin ilk 4 hanesi konsola yazılır.
console.log(num.toPrecision(4))

/** 
 * num değişkeninin ilk 6 hanesi konsola yazılır. 
 * num değişkeni 4 haneden oluşuyor. 6 basamaklı notasyona dönüştürülmek için son hanenin yanına 
 * gerekli sayısa 0 rakamı konur.
 */  
console.log(num.toPrecision(6))

```

    9.656
    9.7
    9.656
    9.65600


### `valueOf()` Metodu

Bir sayısal değerin primitive değerini geri döndürmek için kullanılır.

**Örnek**



```javascript
%%javascript

// Object veri tipinde number veri türü tanımlıyoruz.
const num = new Number(80);

// num değişkenin primitive veri türünü konsola yazdırır.
console.log(typeof num.valueOf())
```

    number


### Değerleri Number Veri türüne Dönüştürülmesi

Bir değişkeni number veri türüne çevirmek için 3 method kullanılır:

1. `Number()` metodu

2. `parseFloat()` metodu

3. `parseInt()` metodu

Bu metotları inceleyelim.


#### `Number()` Metodu

`Number()` metodu içerisinde kullanılan parametre number veri türüne dönüştürülür. Verilen parametre **numerik string olmaması durumunda `NaN` olarak geri döndürülür.**

**Örnek**



```javascript
%%javascript

// true boolean değerinin number veri türünde karşılığı 1'dir.
console.log(Number(true))

// true boolean değerinin number veri türünde karşılığı 0'dır.
console.log(Number(false))

// Normalda "10" değeri string veri tipindedir. Number() metodu ile number veri tipine çevriliyor.
console.log(Number("10"))

console.log(Number("10.33"))

// Convert işlemi sonrasında white space karakterlerin kaldırıldığına dikkat edelim.
console.log(Number("  10"))

// Bilal ifadesi sayısal bir değere denk gelmediğinden dönen değer NaN olacaktır.
console.log(Number("Bilal"))

/** 
 * 10 rakamı ile 33 rakamı arasında white space karakter olması nedeniyle statement tümü sayısal özelliği olmayan 
 * string değer olarak yorumlanır ve NaN değeri geri döndürülür.
 */
console.log( Number("10 33"))

```

    1
    0
    10
    10.33
    10
    NaN
    NaN


`Number()` metodu aynı zamanda tarih özellikli bir veriyi mili saniye cinsinden number türüne ve veri tipine dönüştürür.

**Örnek**



```javascript
%%javascript

const bornDate = new Date("1986-10-14")

// bornDate number veri türüne çevrilir ve tarih değerinin mili saniye karşılığı konsola yazdırılır.
console.log(Number(bornDate))

// bornDate ilk baş number veri türüne dönüştürülür sonrasında veri tipi konsola yazdırılır.
console.log(typeof Number(bornDate))
```

    529632000000
    number


**⚠️ `Date()` metodu 1.1.1970 tarihinden beri mili saniye olarak sonuç döndürür.**

**Örnek**



```javascript
%%javascript

const bornDate = new Date("1970-01-02")

console.log(Number(bornDate))
```

    86400000


#### `parseInt()` Metodu

`parseInt()` metodu verilen string parametreyi parçalarına ayırır ve string içerisindeki **tam sayı** kısmı geri döndürür. Parametre içerisinde white space karakterlerin kullanılmasına izin verilir.

**Örnek**



```javascript
%%javascript

// 10.33 değerinin tam sayı kısmı konsola yazdırılır.
console.log(parseInt(10.33))

// 10 6 değerinin ilk tam sayı kısmı konsola yazdırılır.
console.log(parseInt(8 6))

```

    10
    8


**⚠️ Sayısal olmayan string değer ile birlikte numerik özellikli string bir ifade `parseInt()` metoduna parametre olarak geçirildiğinde şayet string değerin ilk bölümü numerik özellik ise bu değer geri döndürülür aksi durumda `NaN` ifadesi geri döndürülecektir.**

**Örnek**



```javascript
%%javascript

const text = "10 adet kalem"

// string ifadenin başındaki tam sayı kısım konsola yazdırılır.
console.log(parseInt(text))

const text2 = "kalem sayısı 10 adet"

// NaN değeri konsola yazdırılır.
console.log(parseInt(text2))

```

    10
    NaN


#### `parseFloat()` Metodu

`parseFloat()` metodu verilen string parametreyi parçalarına ayırır ve string içerisindeki **sayı** kısmını geri döndürür. Sayı kısmı **ondalık olabilir.** Parametre içerisinde white space karakterlerin kullanılmasına izin verilir.

**Örnek**



```javascript
%%javascript

const num = 3.14;

// parseInt() metodu değerin tam sayı kısmını geri döndürür.
console.log(parseInt(num))

// parseFloat() metodu değeri tam sayı ve ondalık kısmıyla birlikte geri döndürür.
console.log(parseFloat(num))
```

    3
    3.14


Değer içerisinde sayısal kısım bulunmaz ise `NaN` değeri geri döndürülür.

**Örnek**



```javascript
%%javascript

console.log(parseFloat("Telefon"))

```

    NaN


### Number Nesnesi İçerisindeki Metotların Kullanımı

Bu kısımda number nesnesi içerisindeki bir takım metotların kullanımına değineceğim.

**⚠️ Başlamadan önce number nesnesi içerisinde kullanılan metotların syntax dizilimi şu ana kadar kullandığımız metotların syntax diziliminden farklı olduğunu belirtmeliyim. Number nesnesi içerisindeki metotları kullanmak istediğimizde `Number.functionName(variable)` şeklinde syntax tanımlarız. Buradaki `Number` number nesne sınıfını, `functionName()` kullanılacak metodu ve `variable` işleme sokulacak değeri ifade eder.**

**Hatırlarsak daha önce bir değişken için metot kullanılırken `variable.functionName()` şeklinde bir syntax kullanıyorduk.**


#### `Number.isInteger()` Metodu

Bir değerin number veri türünde oluşturulup/oluşturulmadığını sınar. Şayet değer number veri türü özellikli ise dönen değer `true` aksi halde `false` olacaktır.

**Örnek**



```javascript
%%javascript
// Number nesnesi içerisindeki isInteger() metoduna ulaşıp 65 rakamını parametre olarak geçiriyoruz.
console.log(Number.isInteger(65))

// deneme ifadesi number veri türünde olmadığı için false sonucu konsola yazdırılır.
console.log(Number.isInteger("deneme"))

```

    true
    false


#### `Number.isSafeInteger()` Metodu

Bu metot, belirtilen değerin güvenli tam sayı aralığında olup olmadığını kontrol eder. Eğer değer güvenli tam sayı aralığında bir tam sayıysa `true`, değilse `false` döner.

**💡 Bu metot, genellikle büyük sayıların güvenli tam sayı aralığında olup olmadığını kontrol etmek için kullanılır, özellikle sayısal hataların önlenmesi veya işlemlerin beklenen sınırlar içinde olup olmadığının kontrol edilmesi amacıyla kullanılır.**



```javascript
%%javascript

console.log(Number.isSafeInteger(42)); 

console.log(Number.isSafeInteger(9007199254740992));

console.log(Number.isSafeInteger(-9007199254740992));
```

    true
    false
    false


#### `Number.parseFloat()` Metodu

Verilen string bir parametreyi parçalarına ayırır ve string içerisindeki **sayı** kısmını geri döndürür. Sayı kısmı **ondalık olabilir.** Parametre içerisinde white space karakterlerin kullanılmasına izin verilir.

Parametre içerisindeki ifade convert edilmez ise `NaN` değeri geri döndürülür.

**Örnek**



```javascript
%%javascript

// Ondalık sayısal değer olduğu gibi deri döndürülür.
console.log(Number.parseFloat("10.33"))

// ilk sayısal ifadenin geri döndürüldüğüne dikkat edelim. 
console.log(Number.parseFloat("10 20 30"))

// String değer ayıklanacak ve sayısal kısım geri döndürülecektir.
console.log(Number.parseFloat("10 years"))

// NaN değeri geri döndürülür.
console.log(Number.parseFloat("years 10"))
```

    10.33
    10
    10
    NaN


#### `Number.parseInt()` Metodu

Verilen string bir parametreyi parçalarına ayırır ve string içerisindeki **tam sayı** kısmı geri döndürür. Parametre içerisinde white space karakterlerin kullanılmasına izin verilir.

Parametre içerisindeki ifade convert edilmez ise `NaN` değeri geri döndürülür.



```javascript
%%javascript

// Değerin tam sayı kısmı konsola yazdırılır.
console.log(Number.parseInt("3.14"))

// Değerin tam sayı kısmı konsola yazdırılır.
console.log(Number.parseInt("360 derece"))

// String convert edilmez ise NaN değeri geri döndürülür.
console.log(Number.parseInt("Derece 360"))
```

    3
    360
    NaN


[^1]: 16'lık sayı sistemine verilen isimdir.
[^2]: 8'lik sayı sistemine verilen isimdir.

