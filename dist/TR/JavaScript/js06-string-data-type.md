# JavaScript String Veri Türü ve Tipi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_string_** veri türlerini ve veri tiplerini inceleyeceğiz.

Yazıda:

- String veri türüne ve veri tipine.

- Numerik özellikli string değerlere.

- String veri türünün matematiksel işlemlerde kullanılmasına.

- (`\`) Escape karakterinin kullanılmasına.

- Object tipindeki string türlerine.

- Template literal'lerin string veri türleri ile kullanımına.

- Sıkça kullanılan string metotlarına.

- String ifade için arama metotlarına.

Değineceğim.

İyi okumalar dilerim.


## JavaScript String Veri Türü

Karakterlerden veya dizi karakterlerinden oluşan veri türlerine string adı verilir. String veri tipleri tırnak işaretleri arasında kullanılırlar. Tırnak işareti çift veya tek tırnak şeklinde olabilir.

**Örnek**



```javascript
%%javascript

// Çift tırnak işareti ile kullanımı
const car1 = "Lada";

// Tek tırnak işareti ile kullanımı
const car2 = `Opel`;

// Çift ve tek tırnak işaretleri birlikte kullanılabilirler.
let text1 = "Doktor `gel` dedi.";
let text2 = `Doktor "gel" dedi.`;

console.log(car1)
console.log(car2)
console.log(text1)
console.log(text2)
```

    Lada
    Opel
    Doktor `gel` dedi.
    Doktor "gel" dedi.


String veri türleri primitive özelliklidir ve **_immutable_** yapıdadırlar yani değiştirilemezler.

**Örnek**



```javascript
%%javascript

let student = "Hasan";

 /** 
  * person değişkeni için RAM'de yeni bir adres açılacaktır ve student değişkeninin
  * değeri person değişkenine kopyalanacaktır.
  */ 
let person = student;

// Konsola Hasan ifadesi yazdırılacak.
console.log("Konsola " + person + " ifadesi yazdırılacak")

// student değişkeninin depoladığı veriyi değiştirdiğimizde yeni değer için bellekte yeni bir adres oluşturulacaktır.
student = "Murat"

// Konsola Murat ifadesi yazdırılır.
console.log("Konsola "+ student +" ifadesi yazdırılır.");


```

    Konsola Hasan ifadesi yazdırılacak
    Konsola Murat ifadesi yazdırılır.


Hatırlarsak object veri tipine sahip değişkenlerde bellekteki adres bulunup depoladığı değer güncelleniyordu.

Aynı örneği şimdi object veri tipine sahip veri türleri için yapalım.

**Örnek**



```javascript
%%javascript

let student = { firstName: "Hasan", surName: "Taş" };

let person = student;

// person değişkeninin firstName key'i ile depolanan değere ulaşıp veriyi değiştiriyoruz.
person["firstName"] = "Murat";

// Konsola Murat ifadesi yazdırılacaktır.
console.log(person["firstName"]);

// ⚠️ student değişkenin de güncellendiğini ve konsola Murat ifadesi yazdırıldığına dikkat edin.
console.log(student.firstName)

```

    Murat
    Murat


### JavaScript Sayısal Özellikli String Değerler

String veri türleri rakamlardan oluşabilir. Bu durumdaki string'ler **_numerik özellikli_** string değerler olarak ifade edilir.

**⚠️ Numerik özellikli string değerler dışındaki diğer string değerleri matematiksel işlemlerde sonuca katkıda bulunmazlar. Şayet bir string matematiksel ifade içerisinde kullanılırsa işlem sonucunun veri tipi string olacaktır. Bu durum string'in bulunduğu yere göre sonucu etkiler. Numerik özellikli string değerler için durum biraz daha farklıdır. Daha detaylı bilgi almak için [JavaScript Numerik Özellikli String Değerler](js07-numeric-data-type.ipynb#javascript-numerik-özellikli-string-değerler) başlığına bakabilirsiniz.**

<!-- [#1](https://github.com/eminaltan/learn-web/issues/1) -->

**JavaScript'de expression'lar (ifadeler) soldan sağa şekilde değerlendirilir. Yani Javascript ifadenin nerede string olacağını bu pattern'e göre belirler.**

**Örnek**



```javascript
%%javascript
// + işareti ile string'ler birbirine ekleniyor.

// Konsola 71 yazdırılacaktır.
var x = 4 + 3 + "1";
console.log(x);

// Konsola 143 yazdırılacaktır.
var y = "1" + 4 + 3;
console.log(y);

// Konsola 8 yazdırılacaktır. ⚠️ Expression değerlendirilirken soldan sağa işlemin gerçekleştiğine dikkat edin.
var z = "9" - 4 + 3;
console.log(z);

let m = "Emin" + " " + "Altan";

// Çıktı Emin Altan olacaktır.
console.log(m);

```

    71
    143
    [33m8[39m
    Emin Altan


### `\` Escape Karakterinin Kullanımı

**⚠️ String ifadeyi oluştururken kullandığımız tırnak işareti ile string ifade içerisinde alıntı yapmak için kullandığımız tırnak işaretinin benzer olması halinde sorunlar ortaya çıkar.**

**Örnek**



```javascript
%%javascript
/** 
 * Javascript string'in nerede başladığını ve bittiğini bilemediği için problemlere neden olacaktır. 
 * SyntaxError: Unexpected identifier 'Moğollar' ifadesi konsola yazdırılır.
 */
let text = "Biz onları "Moğollar" olarak çağırırdık."
console.log(text)

```

    Unexpected identifier 'Moğollar'


Bu tarz sorunların önüne geçmek için **_backslash escape character_**[^1] kullanılır.

**❗ `\` karakterinin kullanılması tavsiye edilmez. Çünkü bazı browser'lar `\` karakterini desteklemez.**

Backslash escape character'leri listelersek:

| **Kod** | **Sonuç** | **Açıklama**        |
| ------- | --------- | ------------------- |
| `\'`    | '         | Tek tırnak işareti  |
| `\"`    | "         | Çift tırnak işareti |
| `\\`    | \         | Slash işareti       |

**Örnek**



```javascript
%%javascript

// Yukarıdaki örnek için backslash kullandığımızda sorun çözülür.

let text1 = "Biz onları \`Moğollar\` olarak çağırırdık.";

// Biz onları `Moğollar` olarak çağırırdık. ifadesi konsola yazılır.
console.log(text1);

let text2 = 'Biz onları \"Moğollar\" olarak çağırırdık.';

// Biz onları "Moğollar" olarak çağırırdık. ifadesi konsola yazılır.
console.log(text2);

// Bir string'e backslash karakteri eklemek istersek `\\` karakterlerinden faydalanırız.
text2 = "\\ Karakteri backslash olarak tanımlanır.";

// \ Karakteri backslash olarak tanımlanır. ifadesi konsola yazılır.
console.log(text2);

```

    Biz onları `Moğollar` olarak çağırırdık.
    Biz onları "Moğollar" olarak çağırırdık.
    \ Karakteri backslash olarak tanımlanır.


Bunların dışında bir kaç tür daha backslash escape character mevcuttur fakat bunlara değinmeye gerek görmüyorum arkadaşlar.


## JavaScript String Veri Tipi

String veri türü özellikli değişkenlerin veri tipleri de string olacaktır.

**Örnek**



```javascript
%%javascript

let x = "Hasan";

let y = "5";

// Konsola değişkenleri veri tipleri yazılır.
console.log("x'in veri tipi " + typeof x+ " 'dir.")
console.log("y'nin veri tipi "+ typeof y+ " 'dir.")
```

    x'in veri tipi string 'dir.
    y'nin veri tipi string 'dir.


## JavaScript Object Veri Tipinde String Veri Türleri

Bildiğimiz üzere JavaScript'de string özellikli değişkenler normalde **_immutable_**, ilkel ve string veri tipine sahip veri türleridir.

Ancak `new` keyword'u kullanılarak object veri tipinde string veri türleri oluşturulabilir.

**⚠️ Object veri tipinde oluşturulan string özellikli bir değişken ile normal yöntem kullanılarak oluşturulan string özellikli değişkenin veri tipi birbirinden farklıdır.**

**Örnek**



```javascript
%%javascript

// student değişkeni nesne özellikli olup veri tipi object'dir.
let student = new String("Candan")

console.log("student= "+student)
console.log("student değişkeninin veri tipi "+typeof student+ "' dir.")

let student2 = "Murat";

console.log("student2= "+student2)
console.log("student2 değişkeninin veri tipi " + typeof student2 + "' dir.")
```

    student= Candan
    student değişkeninin veri tipi object' dir.
    student2= Murat
    student2 değişkeninin veri tipi string' dir.


**❗ Object tipinde string veri tiplerinin kullanılması tavsiye edilmez. Özellikle mantıksal operatörlerin kullanıldığı expression'larda beklenmedik sonuçlar ile karşılaşabiliriz.**

**Ek olarak kodları komplike hale getireceği için kod bloklarının yavaş çalışmasına neden olacaktır.**

**Object veri tipindeki iki değişkenin kıyaslanması durumunda sonuç daima `false` olarak geri döner.**

**Örnek**



```javascript
%%javascript

const student = new String("Candan");
const student2 = new String("Murat");

/** 
 * Her iki değişken türü object veri tipine sahip olsa da tür bakımından kıyaslandıklarında birbirine eşit değildirler. 
 * Çünkü object veri tipine sahip değişkenler unique olma özelliği taşır.
 */
console.log(student===student2)
```

    [33mfalse[39m


## JavaScript Template Literals

JavaScript'de ` `` ` karakterleri template literals veya back-ticks olarak ifade edilir. Template literals'ler özellikle **_interpolation_**[^2] işlemlerinde sıkça kullanılır. Bir template literals ile string veri türüne sahip bir değişken tanımlanabilir. Fakat bu yöntem nadiren kullanılır.

**⚠️ Template literal'ler Internet Explorer tarafından desteklemezler.**

**Örnek**


```javascript
%%javascript

const text =`Bu Hasan'nın bisikleti. Hasan bisikletine "Canavar" lakabını takmış.`

console.log(text)
```

    Bu Hasan'nın bisikleti. Hasan bisikletine "Canavar" lakabını takmış.


Template literal olarak tanımlanmış string ifadeler birden fazla satırdan oluşabilir. Back-ticks içerisindeki string ifade olduğu gibi kullanılır.

**Örnek**


```javascript
%%javascript

const text = `
Bu Hasan'nın bisikleti. 
Hasan bisikletine "Canavar" lakabını 
takmış.`
console.log(text)
```

    
    Bu Hasan'nın bisikleti. 
    Hasan bisikletine "Canavar" lakabını 
    takmış.


Aşağıdaki örnekte template literal ile interpolation kullanımı görülüyor. Interpolation işlemi gerçekleştirmek için `${}` karakterlerinden faydalanılır.

**Örnek**


```javascript
%%javascript

const student = { studentName: "Emin", studentSurName: "Altan" }

console.log(`Öğrencinin adı ${student["studentName"]}'dir. Soyadı ${student.studentSurName}'dir.`)
```

    Öğrencinin adı Emin'dir. Soyadı Altan'dir.


Aşağıdaki örnekte HTML elementleri için interpolation yöntemi bir döngü içerisinde kullanılmış.

**Örnek**


```javascript
%%javascript

const header = "Template Literal Örneği"

const kelimeler = ["template", "literal", "javascript", "es6"]

let html = `<h2>${header}</h2><ul>`


for (const x of kelimeler) {
html+=`<li>${x}</li>`
}

html += `<ul>`

console.log(html)
```

    <h2>Template Literal Örneği</h2><ul><li>template</li><li>literal</li><li>javascript</li><li>es6</li><ul>


## JavaScript String Metotları

Bazen bir string değeri belli kriterlere göre parçalamak, birleştirmek veya bazı durumlarda string değeri oluşturan karakterleri küçük harfe çevirmek isteyebiliriz. JavaScript bize benzeri işlemleri yapmamızı sağlayan ön tanımlı metotlar sunar. Bu bölümde string değerler üzerinde işlemlerimizi kolaylaştıran sıkça kullanılan bir takım metotlara değineceğiz.

### `length` Metodu

Bir string ifadedeki karakter sayısını öğrenmemize yardımcı olur.

**Örnek**


```javascript
%%javascript

const uluTurk = "Atatürk";

// Atatürk ifadesindeki karakter sayısı konsola yazdırılır.
console.log(uluTurk.length)
```

    [33m7[39m


### String İfadelerin Parçalara Ayrılması

String ifadeler 3 metot kullanarak parçalara ayrılabilir:

1. `slice()` metoduyla

2. `substring()` metoduyla

3. `substr()` metoduyla

Şimdi bunları tek tek inceleyelim.

#### `slice()` Metodu

`slice()` metodu bir string ifadeyi parçalarına ayırır. Ayrılan parça yeni bir string değer olarak geri döndürülür.

Metodun kullanımında iki parametre vardır. Bunlar başlangıç ve bitiş parametreleridir. Bu parametreler birbirlerinden `,` işareti ile ayrılırlar. Bitiş parametresinin kullanılması isteğe bağlıdır. Kullanılması halinde başlangıç parametresi ile bitiş parametresi arasındaki kısım string ifadeden ayrılır. Kullanılmadığı durumlarda başlangıç için belirtilen parametreden string ifadenin sonuna kadar işlem gerçekleştirilir.

**⚠️ String ifade içerisindeki ilk karakterin index değeri 0 olarak hesaplanır.** 

**Örnek**



```javascript
%%javascript

const text = "Mehmet Emin Altan"

// İlk 7 karakter string ifadeden atılır ve kalan string ifade geri döndürülür.
const part = text.slice(7)

console.log(part)

// 7 ile 11 arasındaki karakterleri konsola yazar.
const part2=text.slice(7,11)

console.log(part2)

```

    Emin Altan
    Emin


**💡 Parametrelerde negatif değerler kullanılabilir. Bu durumda string ifadenin sonundan işlem yapılmaya başlanır.**

**Örnek**


```javascript
%%javascript

const text = "Mehmet Emin Altan"
// Ayırma işlemine sondan başlanacak ve 10 karakter geri döndürülecektir.
const part = text.slice(-10)

console.log(part)

// Sondan başlayarak 5 ile 10 arasındaki karakterleri konsola yazar.
part2 = text.slice(-10, -5)

console.log(part2)
```

    Emin Altan
    Emin 


####  `substring()` Metodu

Kullanımı `slice()` metoduna benzerdir. Aradaki fark parametreler için negatif değer kullanıldığında `substring()` metodu bu parametreleri 0 rakamı olarak yorumlar.

**Örnek**


```javascript
%%javascript

const text = "Mehmet Emin Altan"
/** 
 * -10 rakamı negatif olması sebebiyle substring() metodu tarafından 0 olarak yorumlanacak 
 * ve string ifade baştan sona kadar konsola yazdırılacaktır. 
 */
const part = text.substring(-10)

console.log(part)

```

    Mehmet Emin Altan


####  `substr()` Metodu
Kullanımı `slice()` metoduna benzerdir. Aradaki fark ikinci parametrenin kullanım şeklidir. 

`substr()` metodunun iki parametreli kullanılması durumunda ilk parametrenin string değerde kaçıncı karaktere denk geldiği bulunur sonrasında bu karakter referans alınarak ikinci parametrenin kaçıncı karaktere denk geldiği hesaplanır.

Hatırlarsak `slice()` metodunda belirtilen iki parametre **arasında** işlem yapılıyordu. 

**Örnek**


```javascript
%%javascript

const text = "Mehmet Emin Altan"
/** 
 * 6. karakterin denk geldiği harf bulunacak ve bu karakter referans alacak ardından 
 * üzerine 5 rakamını sayılıp elde edilen sonucu konsola yazdıracaktır.
 */
const part = text.substr(6,5)

console.log(part)

```

     Emin


Şayet ikinci parametre kullanılmaz ise ilk parametre sayısı kadar string değerden karakter eksiltilerek elde edilen sonuç kullanılır.

**Örnek**


```javascript
%%javascript

const text = "Mehmet Emin Altan"
/** 
 * İlk 6 karakter string değerden eksiltilecek ve elde edilen sonuç konsola yazdırılacaktır.
 */
const part = text.substr(6)

console.log(part)

```

     Emin Altan


**❗`substr()` metodu gelecekte web standardından çıkarılması düşünüldüğünden bu metodun kullanılmaması tavsiye olunur.**

`substr()` metodunda negatif değerler kullanılabilir. Eğer ilk parametrede negatif değer kullanılırsa işlemler sondan başa doğru gerçekleştirilir.

**Örnek**


```javascript
%%javascript

const text = "Mehmet Emin Altan"

// Sondan 5 karakter  konsola yazdırılacaktır.
const part = text.substr(-5)

console.log(part)

```

    Altan


### `replace()` Metodu

`replace()` metodu ile string ifadenin bir kısmını başka bir string ifade ile değiştirebiliriz. İşlem yapılan string ifadenin yapısı bozulmaz. Elde edilen ifade yeni bir string şeklinde oluşturulur. Bunun sebebi string veri türünün immutable olmasından kaynaklıdır.

`replace()` metodunda iki parametre kullanılır. ilk parametre değiştirilmek istenen string ifadeyi belirlerken ikinci parametre ise değiştirilecek ifadeyi belirler.

**Örnek**


```javascript
%%javascript

const text = "Bugün hava çok güneşli."

// text değişkeni içerisindeki güneşli kısmı yağmurlu olacak şekilde değiştirilecektir.
console.log(text.replace("güneşli","yağmurlu"))
```

    Bugün hava çok yağmurlu.


**⚠️ `replace()` metodu case-sensitive özelliğe sahiptir. Bir önceki örnek üzerinden konuşursak `GÜNEŞLİ` işe `güneşli` aynı anlama gelmez.**

**Örnek**


```javascript
%%javascript

const text = "Bugün hava çok güneşli."

// replace() metodu case-sensitive olması nedeniyle herhangi bir değişikli yapmadan sonucu geri döndürecektir.
console.log(text.replace("GÜNEŞLİ","yağmurlu"))
```

    Bugün hava çok güneşli.


**⚠️ String ifade içerisinde değiştirilmek istenen kısımlar birden fazla olabilir. Varsayılan kullanımda `replace()` metodu ilk uyuşan kısımda işlevini yerini getirir. Diğer kısımlardaki içerik değiştirilmez. Bunu gerçekleştirmek için `replace()` metodunun *_regular expression_*'lar[^3] ile birlikte kullanmamız gerekir.**

**Örnek**


```javascript
%%javascript

const text ="Ahmet yolda gidiyordu. Ahmet yolda para buldu. Ahmet sonrasında parayı  sahibine iade etti."

// String ifade içerisindeki Ahmet kısmı, Gözde ile değiştirilecektir.
console.log(text.replace(/Ahmet/g, "Gözde"));
```

    Gözde yolda gidiyordu. Gözde yolda para buldu. Gözde sonrasında parayı  sahibine iade etti. 


Örnekte `g` parametresi global olarak tanımlanır. Yani `Ahmet` kısmı string ifadenin **tümünde** aranacak ve bulunduğu yerde `Gözde` string ifadesi ile yer değiştirecektir.

### `replaceAll()` Metodu

 String ifade içerisinde değiştirilmek istenen kısımlar birden fazla olabilir. Bu durumda `replaceAll()` metodu kullanılabilir.
 
**⚠️ `replaceAll()` metodu 2021 yılında JavaScript'e dahil olmuştur ve Internet Explorer bu metodu desteklemez.**

**Örnek**



```javascript
%%javascript

const text ="Ahmet yolda gidiyordu. Ahmet yolda para buldu. Ahmet sonrasında parayı  sahibine iade etti."

// replaceAll() metodu ile regular expression kullanmamıza gerek kalmadı.
console.log(text.replaceAll("Ahmet", "Gözde"));
```

    Gözde yolda gidiyordu. Gözde yolda para buldu. Gözde sonrasında parayı  sahibine iade etti. 


### `toUpperCase()` Metodu

`toUpperCase()` metodu ile bir string ifadenin karakterleri büyük harflere çevrilebilir.

**Örnek**


```javascript
%%javascript

const text ="ömer altan"

console.log(text.toUpperCase())
```

    ÖMER ALTAN


### `toLowerCase()` Metodu

`toLowerCase()` metodu ile bir string ifadenin karakterleri küçük harflere çevrilebilir.

**Örnek**


```javascript
%%javascript

const text ="Ömer Altan"

console.log(text.toLowerCase())
```

    ömer altan


### `concat()` Metodu

`concat()` metodu ile birden fazla string ifade birbirine eklenebilir. `concat()` metodu string veri türlerinde `+` operatörü ile aynı işlevi görür.

**Örnek**


```javascript
%%javascript

const text = "Bahçede"

const text1 = "kedi gördüm"

console.log(text.concat(" bir ",text1))
```

    Bahçede bir kedi gördüm


### `trim()` Metodu

`trim()` metodu ile bir string ifadenin başındaki ve sonundaki white space karakterleri kaldırabiliriz.

**Örnek**


```javascript
%%javascript

const text = "      Bahçede       " 

// text değişkeni white space karakterler ile birlikte 20 karakterden oluşuyor.
console.log(text.length)

// trim() metodu ile white space karakterleri temizliyoruz böylece karakter sayısı 7'ye inmiş oluyor.
console.log(text.trim().length)
```

    [33m20[39m
    [33m7[39m


### `trimStart()` Metodu

Bazen bir string ifadenin başındaki white space karakterleri kaldırmak isteyebiliriz. Bu durumda `trimStart()` metodunu kullanabiliriz.

**⚠️ `trimStart()` metodu 2019 yılında JavaScript'e dahil olmuştur. Modern tarayıcılar 2020 yılından itibaren bu metodu desteklemektedirler.**

**Örnek**


```javascript
%%javascript

const text = "      Bahçede       " 

// text değişkeni white space karakterleri ile birlikte 20 karakterden oluşuyor.
console.log(text.length)

// trimStart() metodu ile baştaki white space karakterleri temizliyoruz böylece karakter sayısı 14'e inmiş oluyor.
console.log(text.trimStart().length)
```

    [33m20[39m
    [33m14[39m


### `trimEnd()` Metodu

Bazen bir string ifadenin sonundaki white space karakterleri kaldırmak isteyebiliriz. Bu durumda `trimEnd()` metodunu kullanabiliriz.

**⚠️ `trimEnd()` metodu 2019 yılında JavaScript'e dahil olmuştur. Modern tarayıcılar 2020 yılından itibaren bu metodu desteklemektedirler.**

**Örnek**


```javascript
%%javascript

const text = "      Bahçede       " 

// text değişkeni white space karakterler ile birlikte 20 karakterden oluşuyor.
console.log(text.length)

// trimEnd() metodu ile sondaki white space karakterleri temizliyoruz böylece karakter sayısı 13'e inmiş oluyor.
console.log(text.trimEnd().length)
```

    [33m20[39m
    [33m13[39m


### `padStart()` Metodu

`padStart()` metodu ile string ifadenin karakter sayısı belirlediğimiz değere ulaşıncaya kadar bir string ifadeye başka bir string ifadeyi tekrar tekrar ekler.

Ekleme işlemi string ifadenin başından başlayarak yapılır.

İki parametre alır. İlk parametre tekrar sayısını belirler. İkinci parametre ise eklenecek string ifadeyi temsil eder.

**💡 Telefon veya kredi kartı numarası gibi gizliliğini korumak istediğimiz verilerde kullanılabilir.**

**Örnek**


```javascript
%%javascript

const cardNumber="21587458974123"

// slice() metodu ile string ifadenin son 4 karakteri kullanıma ayrılıyor.
const slicedText = cardNumber.slice(-4)

// slicedText değişkeninin başına 10 karakter olacak şekilde * işaretini ekler.
const pattern = slicedText.padStart(10, "*")

console.log(pattern)
```

    ******4123


**⚠️ `padStart()` metodu 2017 yılında JavaScript'e dahil olmuştur.**

**⚠️ `padStart()` bir string metodudur. Bu nedenle işlem yapılacak değer şayet string veri türü değilse ilk baş string veri türüne dönüştürülmesi gerekir.  `padStart()` metodunu Internet Explorer desteklemez.**

**Örnek**


```javascript
%%javascript

// num değişkeni number veri türündedir.
const num = 5;

// toString() metodu ile num değişkeni string veri türüne dönüştürülüyor.
const text = num.toString()

// text değişkeninin depoladığı değer 3 karakter uzunluğa erişene kadar 0 rakamını depolanan değerin başına ekleyecektir.
console.log (text.padStart(3,"0"))
```

    005


### `padEnd()` Metodu

`padStart()` mantığıyla çalışır. Aradaki fark string ifade sona eklenir.

**Örnek**


```javascript
%%javascript

const text = "5"

// text değişkeninin depoladığı değer 8 karakter uzunluğa erişene kadar 0 rakamını depolanan değerin sonuna ekleyecektir.
console.log(text.padEnd("8","0"))
```

    50000000


### String İfade Üzerinde Karakter Bazlı İşlemler

Bazen string bir ifadeyi oluşturan karakterler üzerinde işlemler yapmak isteyebiliriz Bu durumda iki metottan faydalanırız:

1. `charAt()`metoduyla

2. `charCodeAt()` metoduyla

Şimdi de bunlara değinelim.

#### `charAt()` Metodu

Metot içerisinde belirlenen index değerinin string ifade içerisindeki karakter karşılığını verir.

**Örnek**


```javascript
%%javascript

const text = "Deneme"

// String ifadenin 2. karakteri konsola yazdırılır.
console.log(text.charAt(2))
```

    n


**❗Dikkat ettiyseniz 2. karakter `n` harfine denk geldi. Çünkü string metotlarının tümünde ilk karakterin index değeri daima 0'dır.**

##### Property Access Yöntemi ile Karaktere Erişim

2009 yılından itibaren index değeri `[]` işaretlerinin kullanılmasına izin verilmiştir.

**Örnek**


```javascript
%%javascript

const text = "Deneme"

console.log(text[0])

```

    D


**⚠️ Property access yöntemi ile karaktere erişim yapılmaması tavsiye edilir. Nedenlerine değinirsek:**

1. Kullanım şekli sebebi ile array veri türüne erişimi anımsatır. 

2. Eğer `[]` arasındaki index değeri string ifade içerisinde bulunmazsa geri döndürülecek değer `undefined` olacaktır. `charAt()` metodunda geriye boş string döndürülür.

3. `[]` işaretinin içerisindeki index değeri ile string ifadenin karakterine yeni bir değer atanamaz. Şayet atama yapılırsa hata mesajı alınmaz fakat statement çalışmayacaktır.

**Örnek**


```javascript
%%javascript

const text = "Deneme"

// String ifade 10 karakterden oluşmadığı için 10. karaktere ait bir veri de olmayacaktır. undefined olarak sonuç geri döner.
console.log(text[10])

// Boş string değer döndürülür.
console.log(text.charAt(10))

// text değişkeninin depoladığı Deneme ifadesindeki D karakterini A olarak değiştirmeye çalışıyoruz.
text[0] = "A"

// Fakat Deneme ifadesindeki ilk karakter değişmeyecektir. Bunun sebebi string veri türlerinin immutable olmasıdır.
console.log(text)

```

    [90mundefined[39m
    
    Deneme


#### `charCodeAt()` Metodu

Metot içerisinde belirlenen index değerinin string ifadedeki karakter karşılığı UTF-16 karakter setine göre verilir.

**Örnek**


```javascript
%%javascript

const text = "Deneme"

// String ifadenin 1 karakteri olan e harfinin UTF-16 karakter setindeki karşılığını konsola yazılacaktır.
console.log(text.charCodeAt(0))
```

    [33m68[39m


### `split()` Metodu

Bazen bir string ifadeyi belirleyeceğimiz bir parametreye göre parçalara ayırıp her bir parça üzerinde işlem yapmak isteyebiliriz. Bu durumda `split()` metodunu kullanılır ve her bir parça array veri türünü çevrilir.

**Örnek**

Bir string ifadenin hem kullanıcı adından hem de şifresinden oluştuğunu varsayalım. String ifadenin kullanıcı adı ve şifre kısmına erişmek istiyoruz diyelim. Bunu en kolay `split()` metoduyla gerçekleştirebiliriz.



```javascript
%%javascript

const user = "Ömer Altan 123456";

// String ifadenin parçalanması için white space karakteri kullandık.
const splittedUser = user.split(" ");

// 0 index değeri konsola yazdırılır.
console.log(splittedUser[0])

// 2. index değeri konsola yazdırılır.
console.log(splittedUser[2])
```

    Ömer
    123456


### String Arama Metotları

Bazen bir string ifade içerisinde başka bir string ifadeyi aramak isteyebiliriz. Bu gibi durumlarda string arama metotları kullanılır.

Başlıca string arama metotlarını listelersek:

1. `IndexOf()` metodu

2. `lastIndexOf()` metodu

3. `search()` metodu

4. `match()` metodu

5. `matchAll()` metodu

6. `includes()` metodu

7. `startsWith()` metodu

8. `endWith()` metodu.

Şimdi de bunlara değinelim arkadaşlar.

#### `indexOf()` Metodu

String ifade içerisinde başka bir string ifadeyi arar ve bulması halinde string ifadenin index değerini geri döndürür. **Arama işlemi aranan değerin bulunması durumunda sonlanacak ve string ifadenin geri kalanına bakılmayacaktır.**

**Örnek**


```javascript
%%javascript

const text = "Lütfen ödemeyi kasaya yapınız ve kasadan fiş isteyiniz."

/** 
 * kasa kelimesi string ifadede 15. karaktere denk geliyor. Yani kasa kelimesinin index değeri 15'dir. 
 * Kelime bulunduktan sonra arama işlemi son bulacaktır.
 */
console.log(text.indexOf("kasa"))
```

    [33m15[39m


#### `lastIndexOf()` Metodu

`indexOf()` metodu gibi çalışır. Aradaki fark string ifade içerisinde uyuşan en son kısmın index değerini geri döndürecektir.

**Örnek**


```javascript
%%javascript

const text = "Lütfen ödemeyi kasaya yapınız ve kasadan fiş isteyiniz."

//String ifadenin sonunda bulunan kasa kelimesinin index değeri 33'dür.
console.log(text.lastIndexOf("kasa"))
```

    [33m33[39m


Şayet parametre içerisindeki değer string ifade içerisinde bulunamaz ise sonuç olarak `-1` rakamı geri döndürülür. Bu durum `indexOf()` metodu için de geçerlidir.

**Örnek**


```javascript
%%javascript

const text = "Lütfen ödemeyi kasaya yapınız ve kasadan fiş isteyiniz."

// Saadet kelimesi string ifade içerisinde olmadığında -1 değeri geri döndürülür.
console.log(text.lastIndexOf("Saadet"))
```

    [33m-1[39m


`lastIndexOf()` metodunda 2.parametre kullanılabilir. Bu durumda arama işleminin kaçıncı karakterden itibaren yapılacağı belirtilmiş olunur. Bu durum `indexOf()` metodu için de geçerlidir.

**⚠️ `indexOf()` metodu ile arama işlemi string ifadenin başından yapılırken, `lastIndexOf()` metodu ile arama işlemi string ifadenin sonundan başlayarak yapılır.**

**Örnek**


```javascript
%%javascript

const text = "Lütfen ödemeyi kasaya yapınız ve kasadan fiş isteyiniz."

// Arama işlemi baştan 18. karakterden sonra başlayacaktır.
console.log(text.indexOf("kasa", 18))


// Arama işlemi sonran 21. karakterden sonra başlayacaktır.
console.log(text.lastIndexOf("kasa", 21))
```

    [33m33[39m
    [33m15[39m


#### `search()` Metodu


`indexOf()` metodu gibi çalışır aradaki fark `indexOf()` metodunda 2. parametre kullanılabilirken `search()` metodunda 2. parametre kullanılamaz. Bu duruma ek olarak `search()` metodu regular expression'ları destekler iken `indexOf()` metodu regular expression'ları desteklemez.

**❗ Regular expression'ları desteklemesi sebebi ile `search()` metodu string ifadeleri aramada oldukça etkili bir metottur.**

**Örnek**


```javascript
%%javascript

const text = "Lütfen ödemeyi kasaya yapınız ve kasadan fiş isteyiniz."

// String ifade içerisinde kasa kelimesi ile ilk uyuşan kısma ait index değeri geri döndürülür.
console.log(text.search(/kasa/))
```

    [33m15[39m


#### `match()` Metodu

String ifade içerisinde başka bir string ifadeyi arar ve bulması durumunda işlem sonlanır, string ifadenin geri kalan kısmına bakılmaz ve sonuç array veri türü şeklinde geri döndürülür.

`match()` metodu regular expression'lar ile birlikte kullanılabilir.  `g` flag'ı ile birlikte kullanılması durumunda string ifadenin tümüne bakılır.

**Örnek**


```javascript
%%javascript

const text = "Merhaba benim adım Hasan";


const result = text.match("Hasan");

// Hasan ifadesi string ifade içerisinde aranacak bulunması halinde array veri türü şeklinde özet bilgileri konsola yazdırılacak.
console.log(result);

```

    [
      [32m'Hasan'[39m,
      index: [33m19[39m,
      input: [32m'Merhaba benim adım Hasan'[39m,
      groups: [90mundefined[39m
    ]


Aşağıdaki örnekte `g` flag'ı ile birlikte kullanımı görülüyor.

**Örnek**


```javascript
%%javascript

const text = "Bugün hava güneşli ve ben güneşli havalardan hoşlanırım."

const result = text.match(/güneşli/g);

/** 
 * güneşli ifadesi string ifade içerisinde aranacak bulunması halinde array veri türü şeklinde özet bilgileri konsola 
 * yazdırılacak. Arama işlemi string ifadenin sonuna kadar yapılacak. 
 */
console.log(result);

```

    [ [32m'güneşli'[39m, [32m'güneşli'[39m ]


#### `matchAll()` Metodu

`match()` metodu gibi çalışır aradaki fark `match()` metodu sadece ilk eşleşmeyi döndürürken,`matchAll()` metodu tüm eşleşmeleri döndürür.

**⚠️ `matchAll()` metodu 2020 yılında JavaScript'e dahil olmuştur ve Internet Explorer'da çalışmamaktadır.**

**Örnek**


```javascript
%%javascript

const text = "Bugün hava güneşli ve ben güneşli havalardan hoşlanırım."

const result = text.matchAll("güneşli");

/** 
 * güneşli ifadesi string ifade içerisinde aranacak bulunması halinde array veri türü şeklinde özet bilgileri konsola 
 * yazdırılacak. Arama işleminden elde edilen tüm sonuçlar konsola yazdırılacak.
 */
console.log(Array.from(result));

```

    [
      [
        [32m'güneşli'[39m,
        index: [33m11[39m,
        input: [32m'Bugün hava güneşli ve ben güneşli havalardan hoşlanırım.'[39m,
        groups: [90mundefined[39m
      ],
      [
        [32m'güneşli'[39m,
        index: [33m26[39m,
        input: [32m'Bugün hava güneşli ve ben güneşli havalardan hoşlanırım.'[39m,
        groups: [90mundefined[39m
      ]
    ]


#### `includes()` Metodu

Bazen bir string ifade içerisinde başka bir string ifadenin olup/olmadığını öğrenmek isteriz. Bu durumda `includes()` metodundan faydalanırız. Şayet aradığımız içerik string ifade içerisinde varsa sonuç `true` yoksa `false` olarak geri döndürülür.

**⚠️ `includes()` metodu case-sensitive özelliğe sahiptir. ES6 ile birlikte JavaScript'e dahil olmuştur. Interne Explorer bu metodu desteklemez.**

**Örnek**


```javascript
%%javascript

const text = "Hasan bugün okula gidecek mi?"

// Hasan string ifadesi string ifade içerisinde bulunması sebebi ile sonuç true olarak geri döndürülecektir.
console.log(text.includes("Hasan"))

// Samed string ifadesi string ifade içerisinde bulunmaması sebebi ile sonuç false olarak geri döndürülecektir.
console.log(text.includes("Samed"))
```

    [33mtrue[39m
    [33mfalse[39m


#### `endsWith()` Metodu

Bazen bir string ifadenin sonunu istediğimiz içerikle bitip/bitmediğini öğrenmek isteriz. Bu durumda `endsWith()` metodu kullanılır. Eğer string ifadenin sonu belirlediğimiz parametre ile bitiyorsa sonuç `true` olarak geri döndürülür. Aksi durumda sonuç `false` olarak geri döndürülecektir.

**Örnek**


```javascript
%%javascript

const text = "Hasan bugün okula gidecek mi?"

// String ifadenin sonu mi? ile bittiğinden sonuç true olarak geri döndürülür.
console.log(text.endsWith("mi?"))

// String ifadenin sonu Hasan ile bitmediğinden sonuç false olarak geri döndürülür.
console.log(text.endsWith("Hasan"))

```

    [33mtrue[39m
    [33mfalse[39m


#### `startsWith()` Metodu

`endsWith()` metodu ile aynı mantıkta çalışır. Aradaki fark işlemin string ifadenin başından başlayarak yapılmasıdır.

**Örnek**


```javascript
%%javascript

const text = "Hasan bugün okula gidecek mi?"

// String ifadenin başı mi? ile bitmediğinden sonuç false olarak geri döndürülür.
console.log(text.startsWith("mi?"))

// String ifadenin başı Hasan ile bittiğinden sonuç true olarak geri döndürülür.
console.log(text.startsWith("Hasan"))

```

    [33mfalse[39m
    [33mtrue[39m


**⚠️ `startsWith()` ve `endsWith()` metotları ES6 ile birlikte JavaScript'e dahil olmuştur. Her iki metot case-sensitive özelliğe sahip olup Internet Explorer tarafından desteklenmez.**

[^1]: JavaScript'de ters eğik çizgi (backslash) karakteri (\), özellikle metin (string) dizileri içerisinde özel karakterleri veya kontrol dizilerini temsil etmek için kullanılır. Ters eğik çizgi, ardışık karakterlerin veya özel anlamları olan karakterlerin kaçış (escape) dizilerini oluşturur.

[^2]: JavaScript'te "interpolation", genellikle bir dizede değişken veya ifadelerin değerlerini içine yerleştirmek anlamına gelir. Bu, dize oluştururken bir dize içinde değişken veya ifadelerin değerlerini dinamik olarak eklemenizi sağlar. Template literals (şablon dizgileri), bu tür bir değer yerleştirme (interpolation) için ES6 ile birlikte JavaScript'e eklenmiştir. Template literals içinde, süslü parantez içindeki ifadeler veya değişkenler, dize içinde değerleriyle yer değiştirir.

[^3]: Düzenli ifadeler (Regular Expressions veya Regex), metinle ilgili desenleri tanımlamak için kullanılan bir dildir. Bu desenler, metin içinde belirli karakterleri bulma, değiştirme, eşleştirme veya çıkarma gibi işlemleri gerçekleştirmek için kullanılır. Regex, metin madde analizi, veri madenciliği, metin ve dizge işleme gibi birçok uygulama alanında yaygın olarak kullanılır.

