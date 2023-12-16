# JavaScript'de Array'lar

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_array_** veri türünü inceleyeceğiz.

Yazıda:

- JavaScript'de array veri türünün tanımına ve kullanımına.
- **_element_**, **_index_**, **_associative array_** ve **_isimlendirilmiş index_** kavramlarına.
- Array türünde literal ve nesne türünde değişken oluşturma yöntemlerine ve arasındaki farklara.
- Array türündeki bir değişkene element ekleme yöntemlerine.
- Sıkça kullanılan array metotlarına ve operatörlerine.

Değineceğim.

İyi okumalar dilerim.


## JavaScript Array Veri Türü

Veri türü array olan bir değişken koleksiyon şeklinde verileri gruplandırarak depolar. Bu bağlamda depolanan değerlerin organize edilerek kullanılmasını sağlayan veri türlerinden biridir. Özellikle veri koleksiyonu içerisinde gezinmemizi ve işlemler yapmamızı kolaylaştırır.

Aklımıza oturması için muspet bir örnek verelim. JavaScript'de değişken olarak tanımlanmış bir kaç tane araba markası olduğunu ve bu araba markalarını bir dosyaya kayıt etmek istediğimiz düşünelim. Her bir araba markası için ayrı ayrı işlem yapmak durumundayız. 3 veya 4 tane araba için bu durum belki sorun olmaz. Fakat 400 tane araba için aynı işlemi yapmak hem zaman hem de emek ister. Bu durumda array veri türü yardımımıza yetişir. Array veri türlerini JavaScript döngüleri ile birlikte kullanarak bu tarz işlemleri kolaylıkla çözebiliriz.

Konuyu detaylandırmadan önce aşağıdaki örnek üzerinden bir takım temel kavramlara yer verelim.

**Örnek**

```javascript
const cars = ["Lada", "Opel", "BMW"];
```

Bir array oluşturmak için genelde `[]` işaretini kullanırız. Değerler `[]` işaretleri arasına depolanır. Bu değerlere **_element_** adı verilir. Yukarıdaki örnek üzerinden gidersek `Lada` değeri bir element özelliği taşır. Elementler birbirlerinden `,` işareti ile ayrılırlar.

**❗ Array elementlerine genelde index değeri ile ulaşır ve işlem yaparız. Bir array içerisinde index değeri daima 0'dan başlar. Örneğin `cars` değişkeni içerisindeki `Lada` elementine ulaşmak istiyorsak `cars[0]` şeklinde syntax kullanmamız gerekir.**

**Örnek**



```python
%%script node

const cars = ["Lada", "Opel", "BMW"];

/** 
 * cars array'ın içerisindeki 0 numaralı index değerine sahip elemente ulaşıyoruz.
 * Lada 0 numaralı index değerine sahiptir.
 */
console.log(cars[0]);

```

    Lada


Array veri türü özel nitelikli object veri tipine sahiptir. Bunun anlamı array özellikli bir değişken farklı veri türlerini bir arada barındırabilir.

**Örnek**



```python
%%script node

/** 
 * Örnekte gördüğümüz gibi array özellikli personal değişkeni zaman, nesne ve bir string
 * şeklinde farklı veri türlerini barındırır.
 */
const personal = [Date.now(), privateInformation = { cardNumber: 10, phoneNumber:115}, "Mustafa"];

/** 
 * Date nesnesinin now() fonksiyonu çağırdık ve elde ettiğimiz zaman değerini mili
 * saniye olarak konsola yazdırdık.
 */
console.log(personal[0]);

// privateInformation adında bir nesnenin içeriğini konsola yazdırıyoruz.
console.log(personal[1].cardNumber + " " + personal[1].phoneNumber);

// Array içerisindeki Mustafa değerine ulaşıyoruz.
console.log(personal[2]);

// personal değişkeninin veri türü object'dir.
console.log(typeof personal);

```

    [33m1702051889738[39m
    10 115
    Mustafa
    object


## JavaScript Array Veri Türünde Değişken Oluşturma Yöntemleri

Array veri türünde bir değişken oluşturmak için 2 yöntemden biri kullanılır:

1. Literal yöntemi ile.

2. Nesne türünde tanımlayarak.

Konuya giriş yaparken 1.yönteme yani Literal yoluyla array özellikli bir değişken oluşturmaya değinmiş olduk Şimdi de nesne şeklinde array veri türü özellikli bir değişken oluşturmaya değinelim.


### Nesne Türündeki Array Veri Türleri

`new Array()` metodunu kullanılarak nesne şeklinde array veri türü özellikli bir değişken oluşturabiliriz.

**⚠️ `new Array()` metodu kullanılarak oluşturulan değişken ile literal yöntem kullanılarak oluşturulan değişkeninin veri tipi aynıdır. İkisi de object veri tipine sahiptir.**

**Örnek**



```python
%%script node

/**
 * new Array() metodu kullanılarak nesne türünde array oluşturulur.
 * Bu arada new Array() metodu constructor olarak ifade edilir.
 */
const cars = new Array("Lada", "Tata", "Fiat");
const cars2 = [];

// Konsola object ifadesi yazdırılacaktır. Her iki değişkenin veri tipi de object'dir.
console.log(cars);
console.log(typeof cars2);

```

    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'Fiat'[39m ]
    object


Yukarıdaki örnekte göreceğimiz gibi `cars` array veri türündeki değişkenin içeriği `Lada`, `Tata` ve `Fiat` string değerlerinden oluşuyor.

**💡 Aklınıza "Hangi durumda literal hangi durumda nesne şeklinde array veri türü özellikli bir değişken tanımlamalıyım?" şeklinde bir soru gelebilir. Bu durumda değişkene ait elementler string değerlerden oluşuyorsa nesne türündeki yaklaşımı, şayet değişkenin elementleri sayısal değerlerden oluşuyorsa literal yaklaşımını kullanarak array veri türünde değişken tanımlayabiliriz.**


## JavaScript Array Türündeki Değişkene Yeni Elementler Eklenmesi

Array özellikli bir değişkene 3 yöntemden birini kullanarak yeni bir element ekleyebiliriz:

1. `push()` metodunu kullanarak.

2. Index değerini kullanarak.

3. `length` property'sini kullanarak.

**Örnek**



```python
%%script node

const drinks = ["Çay", "Kahve", "Portakal suyu"];

/** 
 * drinks array özellikli değişkenine yeni bir element ekliyoruz.
 * Element, array içerisinde en sona yerleştirilir.
 * Bu durumda Portakal suyundan sonra Elma suyu gelecektir.
 */ 
drinks.push("Elma suyu");

// 3.index değeri 4.elemente yani Elma suyuna denk gelir.
console.log(drinks[3]);

console.log(drinks);
```

    Elma suyu
    [ [32m'Çay'[39m, [32m'Kahve'[39m, [32m'Portakal suyu'[39m, [32m'Elma suyu'[39m ]


Aşağıda ise index numarasını kullanarak array özellikli değişkenin içerisine element ekliyoruz.

Aynı zamanda array veri türüne sahip bir değişkeni aşağıdaki gibi boş tanımlayabiliriz. Genelde bu yöntem sonradan içeriği doldurulması düşünülen durumlarda kullanılır.

**Örnek**



```python
%%script node

// Array özellikli bir değişkenin elementleri olmayabilir.
const cars = [];

/** 
 * cars değişkeni içerisine 0.indeks numarası ile ulaşıp 1.elementine Lada string 
 * değerini depoluyoruz.
 */
cars[0] = "Lada";

// Konsola Lada ifadesi yazdırılacaktır.
console.log(cars[0]);

```

    Lada


**❗ Yeni bir değer depolama işleminde element sayısı göz önünde bulundurulmadan verilen index değeri array içerisinde boşluklara neden olacaktır. Bu sebeple yeni değer depolanırken değişken içerisindeki depolanmış element sayısına göre index değeri belirlenmesi tavsiye edilir.**

**Örnek**



```python
%%script node

const cars = ["BMW", "Saab", "Fiat"];

// cars referansının 10.indeksine ulaşıyor ve Ford değerini depoluyoruz.
cars[10] = "Ford";

// Yani arada 6 tane boş index ve element oluşturmuş olduk.
console.log(cars);

```

    [ [32m'BMW'[39m, [32m'Saab'[39m, [32m'Fiat'[39m, [90m<7 empty items>[39m, [32m'Ford'[39m ]


Aşağıda `length` property'sini kullanarak array veri türündeki bir değişkene yeni bir element ekliyoruz.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

// length property'sini kullanarak değişkenin sonuna yeni bir element ekliyoruz.
cars[cars.length] = "Mercedes";

// Değişkenin 3.index değeri array içerisinde 4.elemente denk gelecektir.
console.log(cars[3]);

console.log(cars);
```

    Mercedes
    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'Mercedes'[39m ]


## JavaScript'da Associative Özelliği

Normalde javascript'de associative özelliği bulunmaz arkadaşlar. Bunun anlamı normal şartlarda array özellikli değişken içerisinde depolanan bir değere ulaşmak için index numarası yerine string bir ifade kullanamayız. Array özellikli bir değişkenin depoladığı değerlere **index** numarası ile ulaşırız.

Ancak nesne türünde tanımlanmış bir değişkende associative özelliğini kullanabilir.

**Örnek**



```python
%%script node

const person = new Array();

// Associative index örneği. firstName, isimlendirilmiş index olarak ifade edilir.
person["firstName"] = "John";

console.log(person["firstName"]);
```

    John


**❗Şayet index numarası yerine bir string ifade kullanırsak JavaScript bu değişkeni nesne türünde array özellikli bir değişken olarak yorumlar.**



```python
%%script node

// Boş bir array oluşturuyoruz.
const person = [];

/**
 * Bu durumda person değişkeni nesne özellikli array veri türü halini alır.
 * firstName, isimlendirilmiş index olarak ifade edilir.
*/
person["firstName"] = "John";

console.log(person["firstName"]);
```

    John


**❗ Yeri gelmişken `new Array()` metodunu kullanarak oluşturduğumuz nesne türündeki array özellikli değişkenler kod bloklarının yavaş çalışmasına neden olacağı için kullanılması tavsiye edilmez. Basitlik, okunabilirlik ve kod bloklarının hızlı çalışması için literal yöntemle oluşturulan array özellikli değişkenlerin kullanılması tavsiye edilir.**

**Ayrıca `new Array()` metodu kullanılarak oluşturulan nesne türündeki array özellikli değişkenler bir takım sorunlara neden olabilir.**

**Örnek**



```python
%%script node

const numbers = [40];
const numbers2 = new Array(40);

/** 
 * numbers 40 değerini tutarken new Array() metodu ile oluşturduğumuz numbers2 değişkeni
 *  40 tane "," işareti üretecektir.
 */
console.log(numbers);

console.log(numbers2+ " ");

```

    [ [33m40[39m ]
    ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, 


Aşağıdaki örnekte `person` adında boş array veri türü özellikli bir değişken oluşturup içeriğini dolduruyoruz. `length()` metodu ile array içeriğin kaç tane elementten oluştuğunu konsola yazdırmak istediğimizde elde edeceğimiz değer 0 olacaktır.

**Örnek**



```python
%%script node

const person = [];
person["firstName"] = "Hasan";
person["lastName"] = "Bakıcı";
person["age"] = 39;

// person değişkenin kaç tane elementten oluştuğunu konsola yazdıralım.
console.log(person.length);

/** 
 * person değişkeninin 0.index değerine denk gelen elementi konsola yazdıralım. Dönen 
 * değer undefined olacaktır.
 */
console.log(person[0]);

```

    [33m0[39m
    [90mundefined[39m


Yukarıdaki örneği literal yöntemini kullanarak gerçekleştirelim.

**Örnek**



```python
%%script node

const person = [];
person[0] = "Hasan";
person[1] = "Bakıcı";
person[2] = 39;

// person değişkenin kaç tane elementten oluştuğunu konsola yazdıralım.
console.log(person.length);

/** 
 * person değişkeninin 0.index değerine denk gelen elementi konsola yazdıralım. Dönen 
 * değer "Hasan" olacaktır.
 */
console.log(person[0]);

```

    [33m3[39m
    Hasan


Yukarıda görüleceği üzere literal yöntemi ile oluşturulan array özellikli bir değişkene ait elementlerin değerlerini listeleyebiliyor ve metotları kullanabiliyoruz.

**➖ Görüleceği üzere literal yöntemle oluşturulan array değişkenlerde elementlere erişim index numaraları ile yapılırken nesne özellikli array değişkenlerinde isimlendirilmiş bir indeks ile sağlanmaktadır. Bu kullanım yöntemi iki tür arasındaki en büyük farkı oluşturur.**

**❗Nesne özellikli bir değişkende isimlendirmiş index yöntemini key olarak kullanıp key'e denk gelen değere ulaşabiliriz.**

**Örnek**



```python
%%script node

const person = { firstName: "Emin", lastName: "Altan" };

/** 
 * Array içerisinde firstName isimlendirilmiş index'i kullanarak person nesnesindeki 
 * firstName key'ine ait değere ulaşmış olduk.
 */ 
console.log(person["firstName"]);
```

    Emin


**⚠️ Burada şöyle bir soru aklımıza gelebilir. "İsimlendirilmiş index'i hem array veri türüne sahip değişkenlerde hem de nesne veri türüne sahip değişkenlerde birlikte kullanabiliyoruz. Bu durumda bir değişkenin array mı yoksa nesne mi olup/olmadığını nasıl anlayacağız?"**

**İsimlendirilmiş index kullanan bir değişkenin array veya nesne olup/olmadığını sınamanın en etkin yolu `Array.isArray()` metodudur arkadaşlar. Buna ek olarak `Instanceof` operatörü de kullanılabilir.**


## JavaScript Array Metotları, Operatörleri ve Property'leri


### `Array.isArray` Metodu

Bir değişkenin array veri türünde olup/olmadığını öğrenmek için kullanılan metottur. Eğer değişken array veri türünde ise sonuç olarak `true`, değilse `false` değerini geri döndürür.

`Array.isArray()` metodu ECMAScript 5 (JavaScript 2009) ile JavaScript'e dahil edilmiştir.

**Örnek**



```python
%%script node

const student = [];
const person = { firstName: "Emin", lastName: "Altan" };

/** 
 * İsimlendirilmiş index (firstName) kullanmamız sebebiyle student değişkeni nesne 
 * türünde array özelliğine sahip olacaktır.
 */
student["firstName"] = "Murat";

/** 
 * Görüldüğü üzere array özellikli student değişkeninde ve person değişkeninde 
 * isimlendirilmiş index kullanıyoruz. 
 * Düşünelim ki yoğun bir code base içerisinde çalışıyoruz student ve person 
 * değişkenlerinin veri türünü öğrenmek istiyoruz.
 * Bu durumda Array.isArray() metodunu kullandığımızda array veri türüne sahip 
 * değişkeni tespit edebiliriz.
 */
console.log(student["firstName"]);
console.log(person["firstName"]);

/** 
 * Görüleceği üzere student değişkeninden dönen değer true olduğu için student 
 * değişkeni array veri türü özelliği taşır.
 * 
 * person değişkeninden dönen değer false olduğu için bu değişkenin 
 * array veri türü özellikli olmadığını ve nesne türünden bir değişken olduğunu 
 * anlayabiliriz. 
 */
console.log(Array.isArray(student));
console.log(Array.isArray(person));
```

    Murat
    Emin
    [33mtrue[39m
    [33mfalse[39m


### `Instanceof` Operatörü

Object veri tiplerinde birden fazla kullanım yöntemi olmakla birlikte değişkenin türünü belirlemede, bir özelliğin object ile ilişkisini anlamada veya katılım izleme işlemlerini gerçekleştirmek için kullanılır.

**💡 Özellikle object özellikli değişkenlerde debug işlemleri için kullanışlı olabilir.**



```python
%%script node

const fruits = ["Banana", "Orange", "Apple"];

const cars = { carName: "Honda", carModel: "Jazz", productDate: "2005-01-02" };

/** 
 * true değerini geri döndürecektir. Çünkü fruits array veri türüne sahip bir 
 * değişkendir.
 */
console.log(fruits instanceof Array);

/** 
 * false değerini geri döndürecektir. Çünkü cars nesne veri türünde bir 
 * değişkendir.
 */
console.log(cars instanceof Array);

```

    [33mtrue[39m
    [33mfalse[39m


### `delete` Operatörü

Array içerisindeki elementler `delete` operatörü ile de kaldırılabilir. Element array içerisinden silinirse `true` silinemezse `false` değeri döndürür.

**⚠️ Ancak bu yöntem array içerindeki elementler arasında `undefined` tanımlı boşluklar oluşturacağı için kullanılması tavsiye edilmez.**

**Bunun yerine `pop()` veya `shift()` metotlarının kullanılması tavsiye edilir.**

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

/** 
 * Array içerisinden Lada elementi kaldırılacaktır. Kaldırılma işlemi başarılı yapıldığı 
 * için true sonucunu döndürülür.
 */
console.log(delete cars[0]);

// undefined ifadesi konsola yazdırılır. 
console.log(cars[0]);

// cars değişkenin mevcut element sayısı element kaldırılmasına rağmen halen 3'dür.
console.log(cars.length);

/** 
 * 0.index'e sahip Lada elementi kaldırılmasına rağmen array içerisinde hala 0.index'e 
 * ait bir değer tutuluyor. 
 */
console.log(cars);
```

    [33mtrue[39m
    [90mundefined[39m
    [33m3[39m
    [ [90m<1 empty item>[39m, [32m'Tata'[39m, [32m'BMW'[39m ]


### `...` (Spread) Operatörü

`...` (Spread) operatörünün bir çok işlevi bulunmaktadır. **Iterable** olan object veri tipi özellikli değişkenler başta olmak üzere array veya object türünde sonuç üreten işlemlerde sıklıkla kullanılır.

Bunlara tek tek göz atalım:


#### Değişkenlerin Birleştirilmesinde

Hatırlarsak iki veya daha fazla değeri birleştirirken `concat()` metodundan faydalanıyorduk. Birleştirme işlemini aynı zamanda `...` (Spread) operatörü ile de yapabiliriz.

**⚠️ Büyük veri yığınlarında verilerin birleştirilmesi için `...` (Spread) operatörünün kullanılması kod bloklarının yavaş çalışmasına neden olacaktır. Bunun yerine `concat()` metodunun kullanılması tavsiye edilir.**

**Örnek**



```python
%%script node

const prices = ["$2000", "$4000", "$6000"];

const cars = ["Lada", "Tata", "BMW"];

/**
 * İki array türündeki değişken birleştiriliyor ve mergedArrays değişkeni içerisine 
 * depolanıyor.
 */
const mergedArrays = [...cars, ...prices];


console.log(mergedArrays);

const student = {
    studentName: "Emin",
    studentLastName: "Altan",
};

const id = { 
    ID:1
 };


 // İki nesne türündeki değişken birleştiriliyor.
console.log({ ...student, ...id });
```

    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'$2000'[39m, [32m'$4000'[39m, [32m'$6000'[39m ]
    { studentName: [32m'Emin'[39m, studentLastName: [32m'Altan'[39m, ID: [33m1[39m }


### Kopyalama İşlemlerinde

Hatırlarsak array veya object özellikli bir değişkeni referans şeklinde kullanarak oluşturduğumuz yeni bir değişken içeriğine element eklediğimizde orijinal değişkenin içeriği de değişiyordu. Bunun sebebi array veya object veri türünün bellekte referans şeklinde depolanmasaydı.

`...` (Spread) operatörü ile orijinal değişkenin içeriği değiştirilmeden yeni değişkene elementler ekleyebiliriz.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

/** 
 * ... operatörü sayesinde yapacağımız değişiklikler cars değişkeninin içeriğini 
 * etkilemez. cars değişkeninin içeriği newCars'a kopyalanıyor ve değişken için 
 * hafızada yeni bir adres ayrılıyor.
 */
const newCars = [...cars];

newCars.push("Audi");

// Orijinal değişkenin içeriği korunuyor.
console.log(cars);

// newCars değişkeninin içeriğe yeni bir element eklendi.
console.log(newCars);

const student = {
    studentName: "Emin",
    studentLasName: "Altan"
};

/** 
 * person adındaki değişkenin içeriği student değişkeninin içeriği kopyalanarak 
 * oluşturuluyor.
 */
const person = { ...student };

// person değişkenine yeni bir property ekleniyor.
person.salary = "3000USD";

// Görüleceği üzere orijinal içerik korunuyor.
console.log(student);

// person değişkenin property'leri konsola yazdırılır.
console.log(person);
```

    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m ]
    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'Audi'[39m ]
    { studentName: [32m'Emin'[39m, studentLasName: [32m'Altan'[39m }
    { studentName: [32m'Emin'[39m, studentLasName: [32m'Altan'[39m, salary: [32m'3000USD'[39m }


### İçeriği Genişletme İşlemlerinde

Bazen bir değişkeninin içeriğini olduğu gibi başka bir array içerisinde kullanmak isteyebiliriz. Bu durumda `...` (Spread) operatöründen faydalanırız.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

/** 
 * cars değişkeni içerisindeki elementler location değişkeni içerisine dahil 
 * ediliyor.
 */
const locations = [...cars, "İzmir", "Bursa", "Ankara"];

console.log(locations);

const person = {
    personName: "Murat",
    personLastName: "Bakıcı",
};

const jobs = {
    jobsName: "Operator",
    jobsHour: "12H",

    // person nesnesi içerisindeki tüm property'ler jobs nesnesine dahil ediliyor.
    ...person
};

console.log(jobs);
```

    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'İzmir'[39m, [32m'Bursa'[39m, [32m'Ankara'[39m ]
    {
      jobsName: [32m'Operator'[39m,
      jobsHour: [32m'12H'[39m,
      personName: [32m'Murat'[39m,
      personLastName: [32m'Bakıcı'[39m
    }


### Ifadeyi Parçalara Ayırmada

Bir ifadeyi `...` (Spread) operatörü sayesinde parçalara ayırabilir ve array şeklinde bir sonuç elde edebiliriz.

**Örnek**



```python
%%script node

const personName = "Mehmet Akkoç";

console.log([...personName]);

console.log({ ...personName });
```

    [
      [32m'M'[39m, [32m'e'[39m, [32m'h'[39m, [32m'm'[39m,
      [32m'e'[39m, [32m't'[39m, [32m' '[39m, [32m'A'[39m,
      [32m'k'[39m, [32m'k'[39m, [32m'o'[39m, [32m'ç'[39m
    ]
    {
      [32m'0'[39m: [32m'M'[39m,
      [32m'1'[39m: [32m'e'[39m,
      [32m'2'[39m: [32m'h'[39m,
      [32m'3'[39m: [32m'm'[39m,
      [32m'4'[39m: [32m'e'[39m,
      [32m'5'[39m: [32m't'[39m,
      [32m'6'[39m: [32m' '[39m,
      [32m'7'[39m: [32m'A'[39m,
      [32m'8'[39m: [32m'k'[39m,
      [32m'9'[39m: [32m'k'[39m,
      [32m'10'[39m: [32m'o'[39m,
      [32m'11'[39m: [32m'ç'[39m
    }


### Metot İçinde Kullanma

Bir metoda veri seti şeklinde parametre gönderme veya alma işleminde `...` (Spread) operatörünün kullanımı işlerimizi oldukça kolaylaştırır.

**Örnek**



```python
%%script node

/** 
 * Set olarak gelen elementlerin her biri için map() metodu içeriği çağrılır ve elemente 
 * +1 değeri eklenerek sonuç geri döndürülür. Her bir element için map() metodu içeriği
 * çağrıldığı için callback function özelliği taşır.
 */
const additions = (...values) => values.map(num => num + 1);

/** 
 * additions metoduna set olarak değer gönderdik. Gönderdiğimiz setin iterable olduğuna 
 * dikkat edelim.
 */
console.log(additions(1, 2, 3, 4, 5, 6));
```

    [ [33m2[39m, [33m3[39m, [33m4[39m, [33m5[39m, [33m6[39m, [33m7[39m ]


### Destructuring İşlemlerinde

ES6 versiyonu ile birlikte Destructuring işlemi `...` (Spread) operatörü birlikte kullanılabilir hale gelmiştir.

**Örnek**



```python
%%script node

const person = {
    personName: "Lin",
    personSurName: "Wayne",
    personAge: 30,
    personID: 25,
    personAccount: "lin.wayne",
};

/** 
 * Destructuring işlemi ile personName ve personSurname dışındaki property'ler others 
 * içerisine depolanıyor.
 */
const { personName, personSurName, ...others } = person;

/** 
 * personName ve personSurName dışındaki tüm property'ler others içerisine 
 * depolanacaktır.
 */
console.log(others);

```

    { personAge: [33m30[39m, personID: [33m25[39m, personAccount: [32m'lin.wayne'[39m }


### NodeList Array'a Dönüştürme

`querySelectorAll()` metodu ile HTML DOM içerisindeki belirlediğimiz node list elementlerinin tümünü array şeklinde depolayıp kullanmak isteyebiliriz. Bu durumda `...` (Spread) operatöründen faydalanırız.

**Örnek**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <title>Document</title>
  </head>
  <body>
    <p>1.paragraf</p>
    <p>2.paragraf</p>
    <p>3.paragraf</p>

    <script>
      const nodeList = document.querySelectorAll("p");

      // HTML DOM tree'deki tüm <p> elementleri array içerisine depolanıyor.
      const array = [...nodeList];

      /**
       * Her bir <p> elementinin içeriği okunup konsola yazdırılıyor.
       *
       * Sonuç: (3) ['1.paragraf', '2.paragraf', '3.paragraf']
       */
      console.log(array.map((element) => element.innerHTML));
    </script>
  </body>
</html>
```


### `toString()` Metodu

Array özellikli bir değişkenin depoladığı verileri string veri türüne ve tipine dönüştürür. Değişkende depolanan değerler "," işareti ile birbirlerinden ayrılırlar.

Yeri gelmişken `toString()` metodu tüm JavaScript nesnelerinde ortak bir metottur.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

const convertedCars = cars.toString();

/** 
 * convertedCars değişkeni string veri türü ve tipine çevrilecektir.
 * Depolanan değerler "," işareti ile birbirlerinden ayrılırlar.
 */
console.log(convertedCars);

console.log(typeof convertedCars);
```

    Lada,Tata,BMW
    string


JavaScript, array içerisinde primitive veri türü ile karşılaştığında bunu otomatik olarak string veri türüne çevirir.

**Örnek**

Aşağıdaki örnekte `toString()` metodu kullanarak elde ettiğimiz sonuç ile kullanmadan elde ettiğimiz sonuç aynıdır.



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

console.log(cars);

console.log(cars.toString());
```

    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m ]
    Lada,Tata,BMW


### `join()` Metodu

`toString()` metodu gibi çalışır aradaki fark string değerleri ayırmak için kullanılan işareti belirleyebiliriz. `toString()` metodunda depolanan veriler "," işareti ile ayrılıyordu.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

const convertedCars = cars.join("*");

/** 
 * convertedCars değişkeni string veri türü ve tipine çevrilecektir.
 * Depolanan değerler "*" işareti ile birbirlerinden ayrılırlar.
 */
console.log(convertedCars);

console.log(typeof convertedCars);
```

    Lada*Tata*BMW
    string


### `pop()` Metodu

Array özellikli bir değişkenin en sonundaki elementi kaldırır.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

// Array içerisinden BMW elementi kaldırılacaktır.
console.log(cars.pop());

// cars değişkenin mevcut element sayısı 2'ye düşer.
console.log(cars.length);

// cars değişkeninin sahip olduğu elementler konsola yazdırılacak.
console.log(cars);
```

    BMW
    [33m2[39m
    [ [32m'Lada'[39m, [32m'Tata'[39m ]


### `push()` Metodu

Array özellikli bir değişkenin en sonuna yeni bir element ekler.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

// Array içerisinin sonuna Mercedes elementini ekliyoruz.
cars.push("Mercedes");

// cars değişkenin 3.index'i Mercedes elementine denk gelir.
console.log(cars[3]);

// cars değişkenin mevcut element sayısı 4'ye yükselir.
console.log(cars.length);

// cars değişkeninin sahip olduğu elementler konsola yazdırılacak.
console.log(cars);
```

    Mercedes
    [33m4[39m
    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'Mercedes'[39m ]


### `shift()` Metodu

`pop()` Metodu gibi çalışır aralarındaki fark `shift()` metodu değişkenin başından elementi kaldırır. Bu durumda tüm index değerleri bir rakam azalır.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

// Array içerisinden Lada elementi kaldırılacaktır.
console.log(cars.shift());

// cars değişkenin mevcut element sayısı 2'ye düşer.
console.log(cars.length);

// cars değişkeninin sahip olduğu elementler konsola yazdırılacak.
console.log(cars);

/** 
 * cars değişkeninin 0.index değeri artık Lada elementine denk gelmiyor.
 * Tata elementine denk geliyor.
 */
console.log(cars[0]);

```

    Lada
    [33m2[39m
    [ [32m'Tata'[39m, [32m'BMW'[39m ]
    Tata


### `unshift()` Metodu

`push()` Metodu gibi çalışır aralarındaki fark `unshift()` metodu değişkenin başına elementi ekler. Bu durumda tüm index değerleri bir rakam artar.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

// Array içerisinin başına Mercedes elementini ekliyoruz.
cars.unshift("Mercedes");

// cars değişkenin 0.index'i artık Lada değil, Mercedes elementi olacaktır.
console.log(cars[0]);

// cars değişkenin mevcut element sayısı 4'ye yükselir.
console.log(cars.length);

// cars değişkeninin sahip olduğu elementler konsola yazdırılacak.
console.log(cars);
```

    Mercedes
    [33m4[39m
    [ [32m'Mercedes'[39m, [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m ]


### `concat()` Metodu

Array değişkenleri birleştirerek tek bir array oluşturmamızı sağlar.

**⚠️ Var olan array içerikleri değişmez. Birleşme sonucu yeni bir array olarak geri döndürülür.**

**Örnek**



```python
%%script node

const array1 = ["Ahmet", "Mahmut", "Hüseyin"];

const array2 = ["Bilal", "Sevim", "Ayşe"];

/** 
 * array1 ile array2 değişkenlerini birleştiriyor 
 * sonucu newArray değişkeni içerisine depoluyoruz.
 */
const newArray = array1.concat(array2);

// newArray değişkenin içeriğini konsola yazdıralım.
console.log(newArray);

// array1 ve array2'ni elementlerinde bir değişim olmadı.
console.log(array1);
console.log(array2);
```

    [ [32m'Ahmet'[39m, [32m'Mahmut'[39m, [32m'Hüseyin'[39m, [32m'Bilal'[39m, [32m'Sevim'[39m, [32m'Ayşe'[39m ]
    [ [32m'Ahmet'[39m, [32m'Mahmut'[39m, [32m'Hüseyin'[39m ]
    [ [32m'Bilal'[39m, [32m'Sevim'[39m, [32m'Ayşe'[39m ]


`concat()` metoduyla birden fazla array özellikli değişkeni birleştirebiliriz. Bu durumda değişkenlerin arasına "," işareti konulur.

**Örnek**



```python
%%script node

const array1 = ["Ahmet", "Mahmut", "Hüseyin"];

const array2 = ["Bilal", "Sevim", "Ayşe"];

const array3 = ["Mine", "Betül", "Taner"]; 

/** 
 * array1, array2 ve array3 değişkenlerini birleştiriyor 
 * sonucu newArray değişkeni içerisine depoluyoruz.
 */
const newArray = array1.concat(array2, array3);

// newArray değişkenin içeriğini konsola yazdıralım.
console.log(newArray);
```

    [
      [32m'Ahmet'[39m,   [32m'Mahmut'[39m,
      [32m'Hüseyin'[39m, [32m'Bilal'[39m,
      [32m'Sevim'[39m,   [32m'Ayşe'[39m,
      [32m'Mine'[39m,    [32m'Betül'[39m,
      [32m'Taner'[39m
    ]


`concat()` metodu parametre olarak aynı zamanda string değer alır.

**Örnek**



```python
%%script node

const array1 = ["Ahmet", "Mahmut", "Hüseyin"];

/** 
 * array1 değişkenini Netice değeri ile birleştirdik. Elde ettiğimiz sonucu newArray 
 * içerisine depoladık.
 */
const newArray = array1.concat("Netice");

console.log(newArray);
```

    [ [32m'Ahmet'[39m, [32m'Mahmut'[39m, [32m'Hüseyin'[39m, [32m'Netice'[39m ]


### `splice()` Metodu

Array içerisindeki belirleyeceğimiz aralık dahilinde elementleri değiştirmeye, silmeye veya yeni elementler eklemeye yarar.

İki parametresi vardır. İlk parametre index değeridir işlemin hangi elementten itibaren başlanacağını ifade eder. İkinci parametre ise kaç tane element için işlemin yapılacağını ifade eder.

**⚠️ Hatırlarsak `delete` operatörü kullandığımızda array içerisinde boşluklar meydana geliyordu. `splice()` metodu ile element sildiğimizde bu tarz bir sorunla karşılaşmayız.**

**⚠️ `splice()` metodu array özellikli değişkenin yapısını değiştirir. Bunun anlamı yapılan değişiklik için yeni bir array oluşturulmaz, var olan array içeriğinde güncelleme yapılır.**

**Örnek**

Aşağıdaki örnekte belirlediğimiz kısımdan başlayarak istediğimiz elementleri başka elementler ile yer değiştiriyoruz.



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes","Lexus"];

/**
 * 1.index değerinden sonra gelen ilk 2 elementin içeriği ile 
 * OPEL ve TOYOTA ile yer değiştirecektir. 
 * (1.index değeri dahil)
 */
console.log(cars.splice(1, 2, "OPEL", "TOYOTA"));

// Güncel array içeriğini konsola yazdırıyoruz.
console.log(cars);
```

    [ [32m'Tata'[39m, [32m'BMW'[39m ]
    [ [32m'Lada'[39m, [32m'OPEL'[39m, [32m'TOYOTA'[39m, [32m'Mercedes'[39m, [32m'Lexus'[39m ]


**Örnek**

Aşağıdaki örnekte belirlediğimiz kısımdan başlayarak istediğimiz değer kadar elementi array içerisinden siliyoruz.



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes","Lexus"];

/** 
 * 1.index değerinden başlayarak ilk 2 elementi array içerisinden siler. 
 * (1.index değeri dahil)
 */
console.log(cars.splice(1, 2));

// Güncel array içeriğini konsola yazdırıyoruz.
console.log(cars);
```

    [ [32m'Tata'[39m, [32m'BMW'[39m ]
    [ [32m'Lada'[39m, [32m'Mercedes'[39m, [32m'Lexus'[39m ]


**Örnek**

Aşağıdaki örnekte belirlediğimiz kısımdan başlayarak istediğimiz değer kadar elementi array içerisine ekliyoruz.



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes","Lexus"];

/** 
 * 2.index değeri olarak OPEL ve 3.index değeri olarak 
 * TOYOTA markası cars değişkenine ekleniyor.
 */
cars.splice(2, 0, "OPEL", "TOYOTA");

// Güncel array içeriğini konsola yazdırıyoruz.
console.log(cars);
```

    [
      [32m'Lada'[39m,  [32m'Tata'[39m,
      [32m'OPEL'[39m,  [32m'TOYOTA'[39m,
      [32m'BMW'[39m,   [32m'Mercedes'[39m,
      [32m'Lexus'[39m
    ]


### `slice()` Metodu

Bazen array içerisinden belirlediğimiz aralıktaki elementleri kesmek ve bir takım işlemlerde kullanmak isteyebiliriz. Bu durumda `slice()` Metodu yardımımıza yetişir.

İki parametresi vardır. İlk parametre index değeridir işlemin hangi elementten itibaren başlanacağını ifade eder. İkinci parametre işlemin hangi elementte son bulacağını ifade eder. İşleme ilk parametre dahil edilirken ikinci parametre dahil edilmez.

**⚠️ `slice()` metodu var olan array değişkenin yapısını değiştirmez. Elde edilen sonuç yeni array olarak oluşturulur.**

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes", "Lexus"];

/** 
 * 1.index değerine dank gelen element ile 3.index değerine denk gelen element 
 * arasındaki elementler slicedCars değişkenine array veri türü şeklinde depolanıyor.
 *
 * Kesme işlemine 1.index değerine denk gelen element dahil edilirken 3.index değerine
 * denk gelen element dahil edilmez.
 */
const slicedCars = cars.slice(1, 3);

// slicedCars değişkeninin depoladığı elementler yazdırılır.
console.log(slicedCars);

// Görüleceği üzere cars array veri türü özellikli değişkenin yapısı değişmedi.
console.log(cars)
```

    [ [32m'Tata'[39m, [32m'BMW'[39m ]
    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'Mercedes'[39m, [32m'Lexus'[39m ]


### `sort()` Metodu

`sort()` metodu ile bir array içeriğini alfabetik olacak şekilde sıralayabiliriz. Sıralama pattern'i A-Z şeklinde gerçekleşir.

**⚠️ `sort()` metodu orijinal array içeriğindeki elementlerin yerlerini değiştirir.**

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes", "Lexus"];

/** cars değişkenin içeriği A'dan Z'ye olarak listelenir. */
console.log(cars.sort());

// Orijinal array içerisindeki elementlerin sıralaması da değişti.
console.log(cars)
```

    [ [32m'BMW'[39m, [32m'Lada'[39m, [32m'Lexus'[39m, [32m'Mercedes'[39m, [32m'Tata'[39m ]
    [ [32m'BMW'[39m, [32m'Lada'[39m, [32m'Lexus'[39m, [32m'Mercedes'[39m, [32m'Tata'[39m ]


### `sort()` Metodu İçinde Compare Metotlarının Kullanılması

Compare metotlar ile alternatif bir sıralama yöntemi oluşturabiliriz. Compare metodu üç değerden birini döndürür.Bunlar negatif, sıfır veya pozitif değerlerdir.

Bir compare metodu `function (a, b) {return a-b}` şeklinde oluşturulur.

`sort()` metodu iki değeri kıyaslarken bu değerleri compare metoduna gönderir compare metodunda üretilen sonuca göre `a` değerinin `b` değerinden büyük, küçük veya eşit olma durumu anlaşılır.

Formüle göre:

1. Eğer sonuç negatif olarak döndürülürse `a` değeri `b` değerinden küçük olacaktır. (60-100 = -40 Bu durumda `a<b` olur. `a` değeri `b` değerinden önce gelir.)

2. Eğer sonuç pozitif olarak döndürülürse `a` değeri `b` değerinden büyük olacaktır. (100-60 = 40 Bu durumda `a>b` olur. `b` değeri `a` değerinden önce gelir.)

3. Eğer sonuç 0 olarak döndürülürse `a` değeri `b` değerine eşit olacaktır. (100-100 =0 Bu durumda `a=b` olur. Herhangi bir değişiklik yapılmaz.)

**⚠️ Varsayılan olarak `sort()` metodu string değerleri listelemek için kullanılır. Sayısal değerlerin listelenmesi işleminde hatalı sonuçlar döndürür. Bu sorunun önüne geçmek için `sort()` metodu içerisinde _compare_ metotları oluşturulur ve kullanılır.**

**Örnek**



```python
%%script node

const numbers = [40, 100, 1, 5, 25, 10];

// Sayısal değerler için sort() metodu yanlış sonuç döndürecektir.
console.log(numbers.sort());

/** 
 * function(a,b) compare method olarak isimlendirilir. 
 * Sıralamada küçükten büyüğe doğru olacaktır.
 */
console.log(numbers.sort(function (a, b) { return a - b }));

// Şayet büyükten küçüğe sıralama yapmak istersek b-a formülünü kullanırız.
console.log(numbers.sort(function (a, b) { return b - a }));

```

    [ [33m1[39m, [33m10[39m, [33m100[39m, [33m25[39m, [33m40[39m, [33m5[39m ]
    [ [33m1[39m, [33m5[39m, [33m10[39m, [33m25[39m, [33m40[39m, [33m100[39m ]
    [ [33m100[39m, [33m40[39m, [33m25[39m, [33m10[39m, [33m5[39m, [33m1[39m ]


Compare metotlar özellikle array içeriği nesne şeklinde oluşturulmuş değişkenlerde kullanılır.

**Örnek**



```python
%%script node

const cars = [
  { type: "Volvo", year: 2016 },
  { type: "Saab", year: 2001 },
  { type: "BMW", year: 2010 }
];

// cars array içeriği olduğu gibi geri döndürülecektir.
console.log(cars.sort());

/** 
 * Şayet compare metot kullanırsak içeriğini istediğimiz gibi sıralayabiliriz.
 * Burada arrow function kullandık.
 */
console.log(cars.sort((a, b) => a.year - b.year));

// orijinal array içeriği değişti.
console.log(cars);
```

    [
      { type: [32m'Volvo'[39m, year: [33m2016[39m },
      { type: [32m'Saab'[39m, year: [33m2001[39m },
      { type: [32m'BMW'[39m, year: [33m2010[39m }
    ]
    [
      { type: [32m'Saab'[39m, year: [33m2001[39m },
      { type: [32m'BMW'[39m, year: [33m2010[39m },
      { type: [32m'Volvo'[39m, year: [33m2016[39m }
    ]
    [
      { type: [32m'Saab'[39m, year: [33m2001[39m },
      { type: [32m'BMW'[39m, year: [33m2010[39m },
      { type: [32m'Volvo'[39m, year: [33m2016[39m }
    ]


### `reverse()` Metodu

Bazen array içeriğini tersten sıralamak isteyebiliriz. Bu durumda `reverse()` metodunu kullanırız.

**⚠️ `reverse()` metodu orijinal array içeriğindeki elementlerin yerlerini değiştirir.**

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes", "Lexus"];

// cars değişkenin içeriği tersten listelenir.
cars.reverse();

// Orijinal array içerisindeki elementlerin sıralaması değişti.
console.log(cars);

```

    [ [32m'Lexus'[39m, [32m'Mercedes'[39m, [32m'BMW'[39m, [32m'Tata'[39m, [32m'Lada'[39m ]


### `forEach()` Metodu

`forEach()` metodu ile array içerisindeki her bir element için belirlediğimiz bir işlemi otomatik olarak çalıştırabiliriz. Böylece her element için tek tek işlem yapmamış olur ve zamandan kazanırız.

`forEach()` metodu içerisinde bir metot oluşturulması haline bu metot her array elementi için tekrar tekrar çağrılıp kullanılacağı için buna **_callback function_** adı verilir.

**⚠️ `forEach()` metodu orijinal array içeriğini değiştirebilir.**

**Örnek**



```python
%%script node

const numbers = [3, 4, 5, 6];

/** 
 * Arrow metodu callback function özelliği taşır ve number değişkeni içerisindeki 
 * elementlere +1 değeri eklenerek tek sayı haline dönüştürülür 
 * ve sonuç geri döndürülür.
 */
numbers.forEach((value) => console.log(value + 1));

```

    [33m4[39m
    [33m5[39m
    [33m6[39m
    [33m7[39m


### `map()` Metodu

`map()` metodu `forEach()` gibi çalışır ancak `map()` metodu sonucu yeni bir array olarak döndürürken `forEach()` metodu bu anlamda yeni bir değer döndürmez. Buna ek olarak `map()` metodu orijinal array içeriğini değiştirmez fakat `forEach()` metodu orijinal array içeriğini değiştirir.

Bu temel farklar göz önüne alındığında, hangi fonksiyonun kullanılacağı genellikle amaç ve gereksinimlere bağlıdır. Eğer sadece bir döngü içinde her eleman üzerinde bir işlem yapılması gerekiyorsa `forEach()` metodu, yeni bir dizi oluşturmak ve her eleman üzerinde bir işlem yapmak isteniyorsa `map()` metodu kullanılabilir.

**Örnek**



```python
%%script node

const numbers = [45, 4, 9, 16, 25];
const numbers2 = numbers.map(value => value * 2);

/** 
 * numbers1 değişkeninin içeriği 2 ile çarpılacak ve elde edilen sonuç 
 * numbers2 değişkenine yeni array oluşturularak depolanacaktır.
*/
console.log(numbers2);


```

    [ [33m90[39m, [33m8[39m, [33m18[39m, [33m32[39m, [33m50[39m ]


### `flatMap()` Metodu

`map()` metoduna benzer şekilde çalışır aradaki fark `map()` metodu yerine iç içe geçmiş array'lar üretirken `flatMap()` metodu sonuçları düzleştirerek değer üretir.

**⚠️ `flatMap()` metodu ES2019 ile JavaScript'e dahil edilmiştir. Modern tarayıcılar 2020 yılından beri `flatMap()` metodunu desteklemektedirler.**

**Örnek**



```python
%%script node

const numbers = [2, 4, 6, 8];

const numbers2 = numbers.map(value => [value * 2]);

const numbers3 = numbers.flatMap(value => [value * 2]);

// map() metodu iç içe geçmiş array'lar üretti.
console.log(numbers2);

// flatMap() metodu tek bir array içeriği üretti.
console.log(numbers3);

```

    [ [ [33m4[39m ], [ [33m8[39m ], [ [33m12[39m ], [ [33m16[39m ] ]
    [ [33m4[39m, [33m8[39m, [33m12[39m, [33m16[39m ]


### `filter()` Metodu

Bazen bir array içerisindeki verilerin belirlediğimiz kriterlere göre filtre edilmesini ve geri döndürülmesini isteyebiliriz bu durumda `filter()` metodu kullanılır.

`filter()` metodu yeni array oluşturur.



```python
%%script node

const numbers = [45, 4, 9, 16, 25];

/** 
 * Örnekte 18'den büyük değerler filtre edilerek numbers2 değişkenine
 * yeni bir array şeklinde depolanacaktır.
 */
const numbers2 = numbers.filter(value=> value > 18);

console.log(numbers2);

```

    [ [33m45[39m, [33m25[39m ]


### `reduce()` Metodu

`reduce()` metodu array içerisindeki her bir element için bir callback function çalıştırır ve array içeriği tek bir değer haline getirilir.

`reduce()` metodunu kullanmak, genellikle bir dizi üzerinde bir operasyonun sonucunu birleştirmek veya toplamak istediğimiz durumlar için uygun bir seçenektir. Ancak, fonksiyonel programlama prensiplerine uygun olarak kullanıldığında, genel olarak daha okunabilir ve sürdürülebilir bir kod elde edebiliriz.

**💡 `reduce()` metodu soldan sağa yönünde çalışmaktadır. Şayet sağdan solda doğru şeklinde bir işlem yaptırmak istersek `reduceRight()` metodunu kullanabiliriz.**

`reduce()` metodu orijinal array yapısını değiştirmez.

`reduce()` metodunun 4 tane parametresi vardır:

- Başlangıç değeri veya bir önceki elementten elde edilen sonucun değeri.

- Elementin değeri

- Elementin index değeri

- Array kendisi

**Örnek**



```python
%%script node

const numbers = [45, 4, 9, 16, 25];

/** 
 * numbers değişkeni içindeki her element için reduce() metodu içerisindeki callback 
 * fonksiyonu çalışacak ve sonunda tek bir değer üretecektir.
 */
const numbers2 = numbers.reduce((total, value) => total + value);

console.log(numbers2);

```

    [33m99[39m


`reduce()` metodu parametre olarak bir başlangıç değerine sahip olabilir.

**Örnek**



```python
%%script node

const numbers = [2, 4, 7, 8];

// 100 değer başlangıç değeridir.
const numbers2 = numbers.reduce(myFunction, 100);

function myFunction(total, value) {
    return total + value;
};

console.log(numbers2);

```

    [33m121[39m


`reduce()` metodunun nesne veri türlerinde kullanımı yaygındır. Bu sayede array içeriğini tek bir sonuç olarak döndürebiliriz.

**Örnek**



```python
%%script node

const student = [
  { key: 'name', value: 'John' },
  { key: 'age', value: 30 },
  { key: 'city', value: 'New York' }
];

const obj = student.reduce((accumulator, item) => {
  accumulator[item.key] = item.value;
  return accumulator;
}, {});

console.log (obj)
```

    { name: [32m'John'[39m, age: [33m30[39m, city: [32m'New York'[39m }


### `every()` Metodu

Bazen belirleyeceğimiz bir kriterin **tüm array elementleri** ile uyumlu olup/olmadığını kontrol etmek isteyebiliriz. Bu durumda `every()` metodunu kullanırız. Şayet array içerisindeki tüm elementler belirlediğimiz koşul ile uyuşursa `true` herhangi bir elementin belirlediğimiz koşul ile uyuşmaması durumunda `false` değeri geri döndürülür.

`every()` metodunun 3 parametresi vardır:

- Elementin değeri

- Elementin index değeri

- Array'ın kendisi

**Örnek**



```python
%%script node

const numbers = [2, 4, 6, 8];

/** 
 * Array içerisindeki tüm elementlerin 4'den büyük olması durumunda sonuç 
 * true olarak döndürülecektir.
 * 
 * every() metodu her bir element için metot çağırması (burada arrow metodu oluyor.) 
 * sebebi ile callback function özelliği taşır.
 */
const numbers2 = numbers.every(value => value > 4);

console.log(numbers2);
```

    [33mfalse[39m


### `some()` Metodu

Bazen belirleyeceğimiz bir kriterin **herhangi bir array elementi** ile uyumlu olup/olmadığını kontrol etmek isteyebiliriz. Bu durumda `some()` metodunu kullanırız. Şayet array içerisindeki herhangi bir element belirlediğimiz koşul ile uyuşursa sonuç `true` elementlerin tümü koşul ile uyuşmaması durumunda sonuç `false` değeri geri döndürülür.

`some()` metodunun 3 parametresi vardır:

- Elementin değeri

- Elementin index değeri

- Array'ın kendisi

**Örnek**



```python
%%script node

const numbers = [2, 4, 6, 8, 10];

/** 
 * Array içerisindeki herhangi bir elementin 4'den büyük olması durumunda sonuç 
 * true olarak döndürülecektir.
 * 
 * some() metodu her bir element için metot çağırması (burada arrow metodu oluyor.) 
 * sebebi ile callback function özelliği taşır.
 */
let numbers2 = numbers.some(value => value > 4);

console.log(numbers2);
```

    [33mtrue[39m


### `indexOf()` Metodu

Metot içerisinde kullanılan değerin array içerisindeki pozisyonunu geri dönderir.

**Örnek**



```python
%%script node 

const cars = ["Lada", "Tata", "BMW", "Mercedes", "Lexus"];

// BMW elementinin index değeri konsola yazdırılır.
console.log(cars.indexOf("BMW"));

```

    [33m2[39m


Şayet aranan değer array içerisinde bulunmazsa -1 değerini geri dönderir. Bu array içerisinde aranan değerini bulunamadığını ifade eder.

**Örnek**



```python
%%script node 

const cars = ["Lada", "BMW", "Mercedes", "Lexus"];

// Array içerisinde Audi bulunmadığı için -1 değeri konsola yazdırılır.
console.log(cars.indexOf("Audi"));

```

    [33m-1[39m


Aranan değer array içerisinden birden fazla yerde kullanılmışsa ilk değerin pozisyonu geri döndürülür.

**💡 Eğer elementin array içerisinde tüm index'leri gerekiyorsa, `indexOf()` yerine `reduce()` veya `map()` gibi diğer metotları kullanmak daha uygun olabilir.**

**Örnek**



```python
%%script node 

const cars = ["Lada", "Lada", "BMW", "Mercedes", "Lexus"];

// Array içerisindeki ilk "Lada" değerinin pozisyonu konsola yazdırılır.
console.log(cars.indexOf("Lada"));

```

    [33m0[39m


### `lastIndexOf()` Metodu

`indexOf()` metodu gibi çalışır aralarındaki fark şayet array içerisinde aynı elementten birden fazla varsa son elementin index değeri geri döndürülür.

**Örnek**



```python
%%script node 

const cars = ["Lada", "BMW", "Mercedes", "Lexus","Lada"];

// Array içerisindeki son "Lada" değerinin pozisyonu konsola yazdırılır.
console.log(cars.lastIndexOf("Lada"));

```

    [33m4[39m


### `find()` Metodu

Belirlediğimiz bir kritere göre array içerisindeki elementlerden kritere ilk uyan element üzerinde işlem yapmak isteyebiliriz bu durumda `find()` metodundan faydalanırız.

**Örnek**



```python
%%script node

const numbers = [4, 9, 16, 25, 29];

// first değişkenin depolayacağı değer kriter ile uyuşan ilk array elementi olacaktır.
let first = numbers.find(value => value > 18);

console.log(first);
```

    [33m25[39m


### `findIndex()` Metodu

Bazen belirlediğimiz kritere göre uyuşan ilk elementin index değerine ulaşmak isteyebiliriz. Bu durumda `findIndex()` metodunu kullanırız.

**Örnek**



```python
%%script node

const numbers = [4, 9, 16, 25, 29];

/** 
 * first değişkenin depolayacağı değer kriter ile uyuşan ilk array elementinin index 
 * değeri olacaktır.
 */
let first = numbers.findIndex(value => value > 18);

console.log(first);
```

    [33m3[39m


### `Array.from()` Metodu

Kullanılan parametrenin uzunluğuna ve içeriğine göre yeni bir array oluşturmak için kullanılır.

**💡 Özellikle bir string değerin her karakterini array olarak kullanmak istediğimizde `from()` metodundan faydalanabiliriz.**

**Aynı işlemi `...` (Spread) operatörü ile de gerçekleştirebiliriz.**

**Örnek**



```python
%%script node

console.log(Array.from("Lin Wayne"));
```

    [
      [32m'L'[39m, [32m'i'[39m, [32m'n'[39m,
      [32m' '[39m, [32m'W'[39m, [32m'a'[39m,
      [32m'y'[39m, [32m'n'[39m, [32m'e'[39m
    ]


### `keys()` Metodu

Bazen array içerisindeki index değerlerini yeni array içerisinde depolayarak kullanmak isteriz bu durumda `keys()` metodundan faydalanırız.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes", "Lexus"];

/** 
 * cars değişkenin içerisindeki elementlerin index değerleri array şeklinde oluşturulup 
 * konsola yazdırılır.
 */
console.log(Array.from(cars.keys()));

```

    [ [33m0[39m, [33m1[39m, [33m2[39m, [33m3[39m, [33m4[39m ]


### `entries()` Metodu

`entries()` metodu, bir array içindeki her elementin (değer ve index çiftinin) bir dizi içinde bulunduğu bir array nesnesi döndürür. Bu yöntem, bir array içindeki her bir elementin hem değeri hem de index'i (anahtarı) ile birlikte kullanılmasını sağlar.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW", "Mercedes", "Lexus"];

const entries = cars.entries();

/** 
 * Döngü yardımıyla cars değişkenin elementlerini ve index değerlerini konsola 
 * yazdırıyoruz.
 */
for (const entry of entries) {
  console.log(entry);
}
```

    [ [33m0[39m, [32m'Lada'[39m ]
    [ [33m1[39m, [32m'Tata'[39m ]
    [ [33m2[39m, [32m'BMW'[39m ]
    [ [33m3[39m, [32m'Mercedes'[39m ]
    [ [33m4[39m, [32m'Lexus'[39m ]


### `includes()` Metodu

Bazen bir değerin array içerisinde **tam olarak uyuşup/uyuşmadığını** merak edebiliriz. Bu durumda `includes()` metodunu kullanırız. Şayet metot içerisinde kullandığımız parametre ile array elementleri arasında tam bir uyuşma varsa sonuç `true` yoksa `false` olarak geri döndürülür.

`indexOf()` metodunun aksine `includes()` metodu `NaN` değerleri de kontrol eder.

**Örnek**



```python
%%script node

const personalNames = ["Ahmet", "Mehmet", "Can"];

/** 
 * "Ahmet" değeri array elementleri arasında olduğu için sonuç true olarak geri 
 * döndürülür.
 */ 
console.log(personalNames.includes("Ahmet"));

/** 
 * "Meh" değeri array elementleri arasında olduğu için sonuç false olarak geri 
 * döndürülür.
 */
console.log(personalNames.includes("Meh"))
```

    [33mtrue[39m
    [33mfalse[39m


### `length` Property Kullanımı

`length` property'si array özellikli bir değişkenin uzunluğunu sayısal olarak geri döndürür.

Hatırlarsa bu property daha önce array özellikli bir değişkene element eklemek için kullanmıştık.

**Örnek**



```python
%%script node

const cars = ["Lada", "Tata", "BMW"];

// Array özellikli cars değişkeninin uzunluğunu konsola yazdırır.
console.log(cars.length);

/** 
 * cars değişkenine Mercedes elementini ekliyoruz.
 * Eklenen element değişken içerisinde en sona yerleştirilecektir.
 */
cars[cars.length] = "Mercedes";

/** 
 * Yeni değer ekledikten sonra cars değişkeninin depoladığı 
 * elementleri konsola yazdırıyoruz.
 */
console.log(cars);
```

    [33m3[39m
    [ [32m'Lada'[39m, [32m'Tata'[39m, [32m'BMW'[39m, [32m'Mercedes'[39m ]

