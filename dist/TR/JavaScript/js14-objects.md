# JavaScript'de Nesneler

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_nesneleri (object)_** inceleyeceğiz.

Yazıda:

- Nesne kavramına.
- Nesnenin bölümlerine.
- **_property_**, **_key_**, **_value_** ve **_window_** ifadelerine.
- Nesne içerisinde nesne kullanılmasına.
- `this` keyword'une ve kullanım türlerine.
- **_Function Borrowing_** ve **_Function Binding_** kavramına.

Değineceğim.

İyi okumalar dilerim.


## JavaScript'de Nesne Anlayışı

JavaScript'de nesnelere incelemeden önce programlamada nesne kavramının üzerinde durmak isterim. Böylece JavaScript'de nesneleri anlamak kolay olacaktır.

Programlamadaki nesneleri dünyamızdaki nesnelere benzetebiliriz. Mesela bir otomobili ele alalım.

Otomobil dünyamızda doğal olarak bir nesnedir. Bir otomobilin markası, modeli, ağırlığı ve rengi gibi özellikleri vardır. Ek olarak otomobilin çalışmasını, fren yapmasını veya durmasını sağlayan bir takım eylemleri de vardır.

Programlamadaki nesne mantığı da aynı şekildedir. Nesne türündeki bir değişkenin özellikleri ve bir takım görevleri çalıştırması için metotları (fonksiyonları) vardır.

Bu zamana kadar bir değişkenin sadece bir değeri depoladığını gördük. Bir değişken aynı zamanda nesneye ait bir çok özellik ve metottu içerisinde depolayabilir. Bu sebeple nesne yaklaşımlı programlama anlayışı sıklıkla tercih edilir.


## JavaScript Nesnenin Bölümleri

Şimdi de JavaScript'de nesne türündeki bir değişkenin kısımlarını inceleyelim.

![part-of-object](https://www.scaler.com/topics/images/objects-in-javascript_thumbnail.webp)

Nesne türündeki değişkenin deklarasyonu normal bir değişkenin deklarasyonu ile aynıdır. Nesne türündeki değişkenin ismi **_object name_** olarak ifade edilir.

Nesene içeriği `{}` işaretleri arasında yer alır ve nesne içerisindeki property'ler (özellikler) birbirlerinden `,` işareti ile ayrılırlar.

Nesne içerisindeki property'lere değer depolanır.

Bir property **_key:value_** eşleşmesinden meydana gelir. **_key_** program içerisinde property'nin değerine erişmeye yararken **_value_** kısmı property içerisindeki depolanan değerden oluşur.

Yani örneğe göre `firstName: "John"` ifadesi **_property_** termini, `fistName` **_key_** termini, ve `John` ifadesi ise **_value_** termini ifade eder.

Property'nin değeri metottan oluşabilir.

Nesene içerisindeki property'lere ulaşmak için iki yöntem vardır:

1. nesneIsmi.propertyName

2. nesneIsmi["propertyName"]

**❗2. yöntemin **_array_**[^1] şeklinde kullanıldığına dikkat edelim.**

**Örnek**



```javascript
%%javascript

const car = { carName: "Lada", model: 1300, weight: "900kg", color: "white" }

// Property değerlerini konsola yazdırıyoruz.
console.log("car nesnesindeki carName property'nin depoladığı değer " + car.carName + " 'dır.")
console.log("car nesnesindeki model property'nin depoladığı değer " + car.model + " 'dür.")
console.log("car nesnesindeki weight property'nin depoladığı değer " + car.weight + " 'dır.")
console.log ("car nesnesindeki color property'nin depoladığı değer "+car.color+" 'dır.")
```

    car nesnesindeki carName property'nin depoladığı değer Lada 'dır.
    car nesnesindeki model property'nin depoladığı değer 1300 'dür.
    car nesnesindeki weight property'nin depoladığı değer 900kg 'dır.
    car nesnesindeki color property'nin depoladığı değer white 'dır.


Aşağıdaki örnekte bir property değerinin metottan da oluşabileceği görülüyor.

**Örnek**



```javascript
%%javascript

// Bu arada property'ler örnekte görüldüğü gibi ayrı satırlardan oluşabilir.
const car = {
    carName: "Lada",
    model: 1300,
    weight: "900kg",
    color: "white",

    // Aşağıda property değeri bir metottan oluşuyor.
    drive: function driveCar() {
        return "Araba sürülüyor."
    }
}

// car nesnesindeki driveCar() metoduna drive key'i ile ulaştık. Bir property metottan da oluşabilir.
console.log(car.drive())
```

    Araba sürülüyor.


**⚠️ Yukarıdaki örnekte nesne içerisindeki metodu çağırırken `()` işaretlerini kullanmasaydık yani `console.log(car.drive)` şeklinde statement yazmış olsaydık. Ekrana fonksiyonun içeriği yazdıracaktı.**

Yani programın çıktısı aşağıdaki gibi olacaktı.

```javascript
function driveCar() {
  return "Araba sürülüyor.";
}
```


## JavaScript Nesne İçinde Nesne Kullanımı

Bir nesne içerisinde başka bir nesne kullanılabilir. Genelde bunu verileri kategorize etmek ve kodları daha anlaşılabilir hale getirmek için kullanırız.

**Örnek**



```javascript
%%javascript

const car = {
    // Arabanın genel bilgilerini tutan bir nesne oluşturuyoruz.
    generalInfo: {
        carName: "Lada",
        model: 1300,
        weight: "900kg",
        color: "white",
    },

    // Arabanın motor bilgilerini tutan bir nesne oluşturuyoruz.
     motorType:{
         horsePower: " 80hp",
         motorType: "1.5 valve",
         engineType: "Diesel engine"
    }

}
// Organize edilmiş değerler konsola yazdırılır.
console.log("Arabanın markası " + car.generalInfo.carName + " 'dır.")
console.log("Arabanın motor tipi "+ car.motorType.engineType+ " 'dir.")

```

    Arabanın markası Lada 'dır.
    Arabanın motor tipi Diesel engine 'dir.


## JavaScript `this` Keyword Kullanımı

`this` keyword'nun farklı kullanım amaçları vardır arkadaşlar. Fakat burada kapsam içerisinde kalacağım ve ihtiyacımız kadarına değineceğim. Sonrasında daha kapsamlı içerik oluşturup paylaşmayı düşünüyorum.

**❗ `this` keyword'u değişken özelliği taşımaz. Bu sebeple `this` keyword'u için deklarasyon tanımı oluşturamayız.**

**❗ `this` keyword'u nesnenin kendisini veya kullanıma bağlı olarak nesnenin bir bölümünü referans olarak verir.**

JavaScript'de `this` keyword'unun kullanım şekillerini listelersek:

1. Global nesneyi referans verir.

2. Developer tarafından oluşturulan nesnenin kendisini referans verir.

3. Function borrowing ve function binding işlemlerinde kullanılır.

Şimdi bu durumları ayrı ayrı inceleyelim.


#### Global Nesneyi Referans Olarak Verir

Konuya giriş yapmandan önce **_global nesne_** terimine biraz açıklık getirelim arkadaşlar. Böylece konunun kolay anlaşılması sağlayabiliriz.

JavaScript'de global nesne (veya global obje) en üst seviyede tanımlanan nesneyi ifade eder. Yani kullandığımız tüm property'ler, key'ler, değişkenler veya değerler global nesne içerisinde depolanır.

Global nesne çalıştığımız ortama göre değişiklik gösterir. Örneğin browser ortamında global nesne **_window_** iken NodeJS ortamında global nesne **_global_**'dir. Bütün property'ler veya değerlerin hepsi yani kısacası ne varsa bu global nesne içerisinde depolanır. Bu property veya değerlere her yerden ulaşılabilir. Yani bir scope içeriği tarafından sınırlandırılmaz.

Browser için kullanılan **_window_** nesnesi üzerinden bir örnek verelim.

**Örnek**



```javascript
%%javascript

// Her iki kullanım şekliyle de konsola deneme ifadesi yazılır.
console.log("deneme");
window.console.log("deneme");
```

    deneme
    deneme


Yukarıdaki örnekte `console.log("deneme)` ile `window.console.log ("deneme)` statement'ı aynı anlamı taşır. Buradan `console` deklarasyonunun `window` nesnesi (yani browser ortamındaki global nesne)  içerisinde yapıldığını anlayabiliriz.

Açıklamaları yaptıktan sonra `this` keyword'nun global nesne ile ilişkisine değinelim.

**❗ JavaScript'de `this` keyword'u global nesneyi referans verir.**

**Yani `this` keyword'u browser ortamında `window` nesnesini referans verecektir. Bu iki terim biriyle aynı anlama gelir.**

**Örnek**



```javascript
%%javascript
/** 
 * Her iki ifade de aynı anlama gelir. 
 * this keyword'u burada window nesnesini referans verir.
 */
window.console.log("deneme")
this.console.log("deneme")

// Her iki terim aynı olması sebebiyle konsola true ifadesi yazdırılır.
console.log(this===window)
```

    deneme
    deneme
    true


**❗ Yeri gelmişken `this` keyword'u nesneden bağımsız bir metot içerisinde tek kullanılırsa yine `window` nesnesini referans verir.**

**Örnek**



```javascript
%%javascript

function myFunction() {
    console.log(this)
}

// Konsola window nesnesine ait tüm property'ler yazdırılacaktır. Buraya çıktı vermiyorum çünkü içerik çok uzun.
myFunction();

```

#### Nesneyi Referans Olarak Verir.

`this` keyword'u **yalın olarak** bir nesnenin metodunda kullanılmışsa bu durumda nesenin kendisini referans verecektir.

**Örnek**



```javascript
%%javascript

const student = {
    firstName: "Ömer",
    lastName: "Altan",
    id: 4560,
    printStudent: function printStudentInfo() {
    
        // printStudent metodu student nesnesini referans verecektir, student nesnesinin içeriği konsola yazdırılacaktır.
        console.log(this);
    }
}

/** 
 * printStudent metodunu çağırıyoruz.
 * Konsola nesne yazdırılacaktır.
 * Bu durumda this keyword'u nesnenin kendisini referans verdi.
 */ 
student.printStudent()

```

    {
      firstName: [32m'Ömer'[39m,
      lastName: [32m'Altan'[39m,
      id: [33m4560[39m,
      printStudent: [36m[Function: printStudentInfo][39m
    }


`this` keyword'u nesneye ait metot içesinde bir property'nin key'i olarak kullanıldığında ilgili property'nin değerini verir.

**❗ Unutmayınız ki bir nesne içerisinde `this` keyword'u nesnenin kendisini referans verir.**

**Örnek**



```javascript
%%javascript

const student = {
    firstName: "Ömer",
    lastName: "Altan",
    id: 4560,
    printStudent: function printStudentInfo() {

        /** 
         * this keyword'u burada student nesnesini ifade ediyor. 
         * Developer tarafından oluşturulan nesne içerisinde kullanıldığında, nesnenin kendisini 
         * referans verdiğini hatırlayalım.
         * 
         * Mesela this.firstName stament'ı, student.firstName statement'ı ile aynı anlama gelir.
         */
        console.log("Öğrencinin adı " + this.firstName + " 'dir.")
        console.log("Öğrencinin soyadı " + this.lastName + " 'dır.")
        console.log ("Öğrencinin numarası "+ this.id+ " 'dur.")
    }
}

// student nesnesi içerisindeki printStudent metodunu çağırıyoruz. 
student.printStudent()

```

    Öğrencinin adı Ömer 'dir.
    Öğrencinin soyadı Altan 'dır.
    Öğrencinin numarası 4560 'dur.


**❗ Yeri gelmişken `this` keyword'u nesne dışında bir property'nin key'i olarak kullanıldığında `window` nesnesine ait değişkeni referans verir.**

**Unutmayınız ki nesne dışında kullanılan `this` keyword'u global tanımlı nesneyi ifade eder. Browser ortamında global nesne `window`'dur.**

**Örnek**



```javascript
%%javascript

this.ogrenci ="Banu Tekin"

/** 
 * Buradaki this, global nesneyi ifade eder. 
 * Yani window.ogrenci ile aynı anlama gelir.Dolayısıyla sonuc true olarak geri döndürülür.
 */
console.log(window.ogrenci === this.ogrenci)

// this.ogrenci ile aynı anlama geldiğinden ötürü Banu Tekin ifadesi konsola yazdırılır.
console.log(window.ogrenci)
```

    true
    Banu Tekin


**❗ `this` keyword'u nesneden bağımsız metot içerisinde bir property'nin key'i olarak kullanıldığında `window` nesnesine ait değişkeni referans verir.**

**Çünkü nesne dışındaki `this` keyword'u global nesneyi ifade eder. Browser ortamında global nesne `window`'dur.**

**Örnek**



```javascript
%%javascript

function myFunction() {
  // Aşağıdaki statement window.ogrenci ile aynı anlama gelir.
   console.log(this.ogrenci = "Banu Tekin")
   
// Her iki terim aynı olması sebebiyle konsola true ifadesi yazdırılır.
  console.log(this.ogrenci === window.ogrenci)
  
  // Banu Tekin ifadesi konsola yazdırılır.
  console.log (window.ogrenci)
}

// Metodumuzu çağırıyoruz.
myFunction();

```

    Banu Tekin
    true
    Banu Tekin


### Function Borrowing ve Binding İşlemleri

Bu konuyu bir metafor aracılığı ile açıklayalım.

Elimizde iki adet birbirinden bağımsız nesne olduğunu düşünelim. Bu nesnelerden bir tanesinin adı **_truck_** olsun diğer nesnenin adı **_car_** olsun.

Bazen car nesnesi içerisindeki property'ler ile truck nesnesi içerisindeki metotları birlikte kullanmak veya truck içindeki metotta car nesnesini arguman olarak kullanarak sonuç üretmek isteyebiliriz. Bu durumda yardımımıza function borrowing veya function binding yöntemleri yetişir.

Şimdi de bu iki kavramı biraz açalım.

#### Function Borrowing

Bir nesne içerisindeki metodun başka bir nesne için kullanılmasına **_function borrowing_** yöntemi adı verilir.

Yani bir nesnenin metodu başka bir nesnede kullanılmak için ödünç alınır.



```javascript
%%javascript

const truck = {
    printTruckProperties: function () {
         return console.log("Aracın türü= " + this.model)
    }
}

const car= {
    model: "Lada",
}


// car nesnesinin printCarProperties metodu truck nesnesinin printTruckProperties metodunu ödünç alıyor. Yani borrow yapıyoruz.
car.printCarProperties = truck.printTruckProperties;

car.printCarProperties()

```

    Aracın türü= Lada


Yukarıdaki örnekte truck nesnesinin `printTruckProperties()` metodunu car nesnesi için ödünç alıyoruz yani borrowing işlemini gerçekleştiriyoruz. `car.printCarProperties()` metodunu çağırdığımızda `printTruckProperties()` metodu çağrılacak ve bu metot içerisindeki `this.model` property'si `car.model` property'sini referans verecektir.

**`this` keyword'u truck nesnesi içerisinde kullanılmasına rağmen car nesnesi referans verdi. Hatırlarsak normalde truck içerisindeki `this` keyword'u yine nesenin kendisini referans veriyordu yani truck nesnesini.**


#### Function Binding

JavaScript'de bind etme yöntemi iki şekilde gerçekleştirilir arkadaşlar:

1. Implicit Binding (Örtük Bağlama)

2. Explicit Binding (Açık Bağlama)

Esasen buraya kadar olan kısma kadar `this` keyword'unu **_implicit binding_** yöntemi ile kullandık. Bu sebeple örtük bağlama yöntemini anlatmayacağım. **_explicit binding_** yöntemine değineceğim.

##### Explicit Binding

Bir nesnenin metodu içerisinde başka bir nesneyi argüman olarak kullanabilir ve bu statement'dan elde edilen sonucu bir değişken içerisinde depolayabiliriz.  Buna **_function binding_** adı verilir.

Function binding `call()`, `apply()` veya `bind()` metotları ile gerçekleştirilir.

`bind()` metottu için bir örnek verirsek.

**Örnek**



```javascript
%%javascript

const truck = {
    model: "IVECO",
    engine: "Dizel",
    wheelSize:"36 inç",
    
    /** 
     * printTruckProperties() metoduna başka bir nesne içerinden binding yöntemi ile erişildiğinde 
     * this.model statement'ı erişen nesenin property'sini referans verir.
     */
    printTruckProperties: function (argument) {
        return console.log(
            ("Aracın türü= " + this.model)
            +
            (" Aracın motoru= " + this.engine)
            +
            (" Aracın teker boyutu= " + this.wheelSize)
        )

    }
}

const car= {
    model: "Lada",
    engine:"Benzinli",
    wheelSize:"18 inç"
}

// printTruckProperties() metoduna car nesnesini argüman olarak gönderdik.
const printCar=truck.printTruckProperties.bind(car)
printCar()

//  printCar değişkeninin tipi fonksiyondur.
console.log(typeof printCar)


```

    Aracın türü= Lada Aracın motoru= Benzinli Aracın teker boyutu= 18 inç
    function


Yukarıdaki örnekte truck nesnesinin `printTruckProperties()` metoduna car nesnesini argüman olarak gönderiyoruz. Sonrasında dönen sonucu `printCar` adında bir değişkene depoluyoruz. Bu durumda `printCar` değişkenimiz metot özelliği kazanıyor. Yukarıda kısaca bahsettiğimiz gibi bu durumda **_function binding_** adı verilir.

Metodunu kullandığımız nesne içerisindeki `this` keyword'u argüman olarak gönderdiğimiz nesneyi referans verecektir. Yani `truck` nesnesi içerisindeki `this` keyword'u artık `car` nesnesi referans verir.

Dolayısıyla argümana ait property değerleri konsola yazdırılır.

Bunun dışında `this` keyword'u **_HTML event handler_**[^2] işlemlerinde kullanılır fakat konu kapsamında olmadığı için buna değinmiyorum. `this` keyword'u için ayrı bir içerik oluşturup değinmeyi düşünüyorum.

Umarım faydası olmuştur arkadaşlar. Kafanızda soru işareti olan yerler veya eksik kısımlar varsa dönüşlerinizi bekliyorum.

[^1]:JavaScript'te bir dizi (array), bir değişkenin içinde birden çok değeri depolamak için kullanılan bir veri türüdür. Diziler, sıralı bir şekilde indekslenmiş elemanlar içerir ve bu elemanlara erişmek için indeks numaraları kullanılır. 
[^2]:HTML event handler, HTML belgesinde gerçekleşen olayları (events) işleyen JavaScript fonksiyonlarıdır. HTML olayları, kullanıcı etkileşimleri veya tarayıcıda gerçekleşen diğer olaylar gibi belirli durumları temsil eder. Örneğin, bir düğmeye tıklanma, bir form gönderme veya bir fare üzerine gelme gibi olaylar HTML olaylarına örnektir.

Event handler'lar, belirli bir olay gerçekleştiğinde çalıştırılmak üzere tanımlanan JavaScript fonksiyonlarıdır. Bu, HTML ve JavaScript arasındaki etkileşimleri sağlar. Event handler'lar, HTML etiketleri içinde doğrudan kullanılabileceği gibi, JavaScript kodu içinde de tanımlanabilir. 
