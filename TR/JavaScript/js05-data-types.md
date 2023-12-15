# JavaScript Veri Türleri ve Tipleri

Merhaba arkadaşlar bu yazıda JavaScript'de veri türlerine ve veri tiplerine değineceğiz. Veri türlerinin ve veri tiplerinin neden önemli olduğu, şayet bir değişken için doğru veri türü veya veri tipini kullanmadığımızda ne gibi sorunlar ile karşılaşacağımıza değineceğiz. **Yazının sonraki bölümlerinde her bir veri türünü ve veri tipini ayrı ayrı inceleyeceğiz.**

Yazıda:

- Immutable ve Mutable kavramına.
- Veri türü ve veri tipi kavramına.
- Primitive ve Object veri türlerine.

Değineceğim.

İyi okumalar dilerim.


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


## JavaScript'de Veri Türü ve Veri Tipi Kavramı

JavaScript'de veri türleri ve veri tipleri önemli kavramlardır. Değişkenler ile çalışabilmemiz için veri türlerini ve tiplerini bilmemiz gerekir.

Veri türünü veya tipini bilmeksizin bir bilgisayar programı denklemi tam anlamıyla çözemez yanlış sonuçlar geri döndürür.

**Örnek**



```javascript
%%javascript
let x = 20 + "Otobüs";

console.log("Konsola " + x+ " ifadesi yazdırılır.");

```

    Konsola 20Otobüs ifadesi yazdırılır.


Yukarıdaki işlemi matematiksel anlamda düşünürsek mantıklı değildir. Çünkü 20 rakamı ile "Otobüs" değerinin toplamı sonuç olarak bir şey ifade etmez.

**⚠️ Doğru sonuçlar elde edebilmemiz için değişkenlerin aynı veri tipine sahip olması gerekir.**

**Örnek**



```javascript
%%javascript
let x = 20 + "8";

console.log("Konsola " + x+ "string'i yazdırılacaktır. Eğer 28 rakamını elde etmek istiyorsak '8' numerik özellikli string değerinin veri tipini number'a dönüştürmemiz gerekir.");

```

    Konsola 208string'i yazdırılacaktır. Eğer 28 rakamını elde etmek istiyorsak '8' numerik özellikli string değerinin veri tipini number'a dönüştürmemiz gerekir.


### JavaScript'de Veri Türleri

JavaScript'de iki veri türü vardır:

1. Primitive (İlkel veri türleri)

2. Object (Referans veri türleri)

Şimdide bunları sınıflandıralım arkadaşlar.


#### Primative Veri Türleri

JavaScript'de primitive (ilkel) veri türleri, karmaşık yapılardan oluşmayan ve doğrudan değerleri temsil eden temel veri türleridir.

JavaScript'teki ilkel veri türleri, temel veri işlemleri ve değerlerin temsilinde kullanılır ve programların temel yapı taşlarını oluştururlar. İlkel veri türleri, karmaşık nesnelerin ve veri yapılarının temelini oluşturan yapı taşlarıdır.

Özellikleri:

- **İmmutability (Değiştirilemezlik):** İlkel veri türleri, bir kez oluşturulduktan sonra değiştirilemezler. Yani, bir ilkel veri türünün değeri atandıktan sonra, o değer değiştirilemez. Bu, verilerin güvenliğini artırabilir ve beklenmeyen yan etkilere karşı koruma sağlar.

- **Değer Tipi (Value Type):** İlkel veri türleri, değerlerin kendilerini temsil eder, yani değerler doğrudan bellekte saklanır. İlkel veri türleri, diğer değişkenlere atanırken kopyalanır, bu nedenle bir değişkenin değeri değişse bile diğer değişkenler üzerinde herhangi bir etkisi olmaz.

- **Hafızada Sabit Boyut:** İlkel veri türleri, sabit bir bellek boyutuna sahiptir. Örneğin, bir sayı her zaman aynı boyutta bellekte saklanır. Bu, bellek yönetimi açısından daha etkili olmalarını sağlar.

- **Kolay Kullanım:** İlkel veri türleri, basit ve hızlı bir şekilde kullanılabilir. İşlemler ve karşılaştırmalar ilkel veri türleri üzerinde hızlı ve verimli bir şekilde gerçekleştirilir.

- **Belirli Değer Aralıkları:** Her ilkel veri türü belirli bir değer aralığını temsil eder. Örneğin, **_Number_** veri türü, JavaScript'in en yaygın kullanılan ilkel veri türü olup tam sayılar ve ondalık sayıları temsil eder.

- **Özel Metotlara Sahip Değil:** İlkel veri türleri, nesnelerin ve fonksiyonların aksine özel metotlara (methods) veya özelliklere (properties) sahip değildir. İlkel veri türlerinin üzerinde doğrudan işlem yapılabilir, ancak bunlarla ilgili özel işlemler için kullanılabilen global fonksiyonlar (örneğin, `parseInt, parseFloat, String`) vardır.

JavaScript'in altı ilkel veri türü bulunmaktadır:

1. String

2. Number

3. BigInt

4. Boolean

5. Undefined

6. Null

7. Symbol

**⚠️ BigInt veri türü bellekte yer değiştirilemez olması sebebi ile JavaScript'te bir ilkel (primitive) veri türüdür.**

**Örnek**



```javascript
%%javascript
// Aşağıdaki değişken türleri string özelliklidir.
let str1 = "Samet";
let str2 = "4";

// Aşağıdaki değişken türleri number özelliklidir.
let number1 = 10;
let number2 = 85.7;

// Aşağıdaki değişken türleri boolean özelliklidir.
let boolean1 = true;
let boolean2 = false;

// Aşağıdaki değişken türü undefined özelliklidir.
let undefined1;
let x = undefined;

// Aşağıdaki değişken türü null özelliklidir.
let null1 = null;

// Aşağıdaki değişken türü symbol özelliklidir.
let symbol1 = Symbol("mySymbol");

// Aşağıdaki değişken türleri bigint özelliklidir.
let bigint1 = 1234567890123456789012345n;
let bigint2 = BigInt(1234567890123456789012345);
```

#### Object Veri Türleri

JavaScript'de nesne (object) veri türü, karmaşık ve esnek veri yapılarını temsil etmek için kullanılan bir yapıdır. Nesneler, anahtar-değer (key-value) çiftlerini içeren veri yapılarıdır ve JavaScript programlamasında önemli bir rol oynarlar. Nesneler, `{}` süslü parantezler arasına yerleştirilen özelliklerin (properties) ve bu özelliklere atanan değerlerin bir koleksiyonunu temsil eder. Bir nesne `[]` işaretleri arasında da oluşturulabilir, bu durumdaki nesne array özelliği taşır.

Özellikleri:

- **Mutable (Değiştirilebilir)**: Nesne özellikli değişkenin bellekte adrese erişilebilir ve içeriği güncellenebilir. Örneğin nesne özellikli bir değişkene yeni değer atandığında yeni değer için bellekte bir adres oluşturulmaz yeni değer eski değerin üzerine yazılır.

- **Anahtar-Değer Çiftleri:** JavaScript nesneleri, anahtar-değer çiftlerini temsil eder. Bu çiftler, nesnenin özelliklerini ve değerlerini tanımlar. Özellikler (anahtarlar) dizge (string) türünde olmalıdır ve değerler herhangi bir veri türü olabilir.

- **Dinamik ve Genişletilebilir:** JavaScript nesneleri dinamiktir, yani nesne oluşturulduktan sonra özellikler (anahtarlar) ekleyebilir, değiştirebilir veya silebilirsiniz. Bu, nesneleri esnek kılar.

- **Özelliklere ve Metotlara Sahip:** JavaScript nesneleri hem özellikleri (anahtar-değer çiftleri) hem de metotları (fonksiyonları) içerebilir. Bu nedenle nesneler hem veri hem de işlevselliği temsil edebilirler.

- **Referans Tipi:** Nesneler referans tipli verilerdir. Yani, bir nesneyi başka bir değişkene atadığınızda, aslında referansın bir kopyasını oluşturursunuz ve her ikisi de aynı nesneyi paylaşır.

- **JSON (JavaScript Object Notation) ile Uyumlu:** JavaScript nesneleri, JSON formatında veri temsilini destekler. Bu, verileri paylaşmak ve veriyi dışarı aktarmak için yaygın olarak kullanılır.

- **Örnek Tabanlı:** JavaScript'de nesneler sınıf veya prototip tabanlıdır ve yeni nesneler oluşturmak için sınıf tanımlamaları veya prototipler kullanabilirsiniz.

Object özellikli veri türleri aşağıdaki gibidir:

1. Object (Nesne)

2. Function (Fonksiyon)

3. Array (Dizi)

4. Date (Tarih)

**Örnek**



```javascript
%%javascript
function Test() { return "Function test"; }

// Aşağıdaki değişken türleri object özelliklidir.

// Nesne
let variable1 = { name: "Hasan", lastName: "Kaş" };

// Function

let variable2 = new Test();

// Array
let variable3 = ["Bursa", "Ankara", "İzmir"];

// Date
let variable4= new Date("2023-10-26");

```

### Javascript'de Veri Tipleri

JavaScript'de veri türlerine değindikten sonra şimdi de veri tiplerinde değinelim.

Özetle primitive veri türleri için her veri türü kendi isminde veri tipine sahiptir.

**Örnek**



```javascript
%%javascript

// Aşağıdaki değişkenlerin veri tipi string özelliklidir.
let str1 = "Samet";
let str2 = "4";

// Aşağıdaki değişkenlerin veri tipi number özelliklidir.
let number1 = 10;
let number2 = 85.7;

// Aşağıdaki değişkenlerin veri tipi boolean özelliklidir.
let boolean1 = true;
let boolean2 = false;

// Aşağıdaki değişkenin veri tipi undefined özelliklidir.
let undefined1;
let x = undefined;

// Aşağıdaki değişkenin veri tipi symbol özelliklidir.
let symbol1 = Symbol("mySymbol");

// Aşağıdaki değişkenlerin veri tipleri bigint özelliklidir.
let bigint1 = 1234567890123456789012345n;
let bigint2 = BigInt(1234567890123456789012345);

console.log("str1 değişkenin veri tipi " + typeof (str1) + " 'dir.")
console.log("str2 değişkenin veri tipi " + typeof (str2) + " 'dir.")
console.log("number1 değişkenin veri tipi " + typeof (number1) + " 'dır.")
console.log("number2 değişkenin veri tipi " + typeof (number2) + " 'dır.")
console.log("boolean1 değişkenin veri tipi " + typeof (boolean1) + " 'dır.")
console.log("boolean2 değişkenin veri tipi " + typeof (boolean2) + " 'dır.")
console.log("undefined1 değişkenin veri tipi " + typeof (undefined1) + " 'dır.")
console.log("symbol1 değişkenin veri tipi " + typeof (symbol1) + " 'dir.")
console.log("bigint1  değişkenin veri tipi " + typeof (bigint1) + " 'dir.")
console.log("bigint2  değişkenin veri tipi " + typeof (bigint2 ) + " 'dir.")
```

    str1 değişkenin veri tipi string 'dir.
    str2 değişkenin veri tipi string 'dir.
    number1 değişkenin veri tipi number 'dır.
    number2 değişkenin veri tipi number 'dır.
    boolean1 değişkenin veri tipi boolean 'dır.
    boolean2 değişkenin veri tipi boolean 'dır.
    undefined1 değişkenin veri tipi undefined 'dır.
    symbol1 değişkenin veri tipi symbol 'dir.
    bigint1  değişkenin veri tipi bigint 'dir.
    bigint2  değişkenin veri tipi bigint 'dir.


**⚠️ Bu durum _*Null*_ veri türü için geçerli değildir. Çünkü _*Null*_ veri türünün veri tipi object özelliği taşır.**

**Örnek**



```javascript
%%javascript

let variable = null;

console.log("variable değişkenin veri tipi "+ typeof(variable)+" 'dir.")
```

    variable değişkenin veri tipi object 'dir.


Nesneler veri türleri için veri tipi yine object şeklinde oluşturulur.

**Örnek**



```javascript
%%javascript
function Test() { return "Function test"; }

// Aşağıdaki değişkenlerin veri tipleri object özelliklidir.

let variable1 = { name: "Hasan", lastName: "Kaş" };

let variable2 = new Test();

let variable3 = ["Bursa", "Ankara", "İzmir"];

let variable4= new Date("2023-10-26");

console.log("variable1 değişkeninin veri tipi "+typeof variable1+" özelliklidir.")
console.log("variable2 değişkeninin veri tipi " + typeof variable2 + " özelliklidir.")
console.log("variable3 değişkeninin veri tipi " + typeof variable3 + " özelliklidir.")
console.log("variable4 değişkeninin veri tipi "+typeof variable4+" özelliklidir.")

```

    variable1 değişkeninin veri tipi object özelliklidir.
    variable2 değişkeninin veri tipi object özelliklidir.
    variable3 değişkeninin veri tipi object özelliklidir.
    variable4 değişkeninin veri tipi object özelliklidir.


**Yazının sonraki bölümlerinde her bir veri türünü ve veri tipini ayrı ayrı inceleyeceğiz.**

