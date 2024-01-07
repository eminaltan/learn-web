# JavaScript'te Map'ler<a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'te **_Map_** kavramını inceleyeceğiz.

Yazıda:

- [JavaScript'te Map Kavramı](#toc1_1_)
  - [Map Elementleri Doğrudan Iterable Edilebilir](#toc1_1_1_)
  - [`size` Property'sine Sahiptir](#toc1_1_2_)
  - [Key Kısmı Herhangi Bir Veri Tipinden Oluşabilir](#toc1_1_3_)
  - [Map Objelerinde Elementler Eklenme Sırasına Göre Sıralanır](#toc1_1_4_)
  - [Map Objeleri Değer Eşitliğine Dayanır](#toc1_1_5_)
- [Map Veri Türünde Sık Kullanılan Metotlar](#toc1_2_)
  - [`set()` Metodu](#toc1_2_1_)
  - [`get()` Metodu](#toc1_2_2_)
  - [`delete()` Metodu](#toc1_2_3_)
  - [`has()` Metodu](#toc1_2_4_)
  - [`forEach()` Metodu](#toc1_2_5_)
  - [`entries()` Metodu](#toc1_2_6_)
- [Özet](#toc1_3_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of article please [visit](js21-maps.md) this link.

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript'te Map Kavramı](#toc0_)

JavaScript **_Map_** kavramını nesne veri türüne benzetebiliriz. Map özellikli bir değişkenin elementleri nesnelerde olduğu gibi **_key-value_** eşleşmesinden oluşur.

Bir Map oluşturmak için `new Map()` constructor metodunu kullanırız.

**Örnek**

```javascript
const maps = new Map([
  [625, "Murat"],
  [276, "Emin"],
  [198, "Hasan"],
]);

console.log(`maps değişkeninin içeriği: ${[...maps]}`);

console.log(`276 numaralı öğrencinin ismi: ${maps.get(276)}`);
```

    maps değişkeninin içeriği: 625,Murat,276,Emin,198,Hasan
    276 numaralı öğrencinin ismi: Emin

Yukarıdaki örnekte `maps` adında bir değişken oluşturduk ve `new Map()` constructor metodu ile depolamak istediğimiz değerleri array şeklinde `maps` değişkeni içerisine yerleştirdik `get()` metodunu kullanarak numarasını bildiğimiz bir öğrencinin adını konsola yazdırdık.

**Map'ler Nesnelerden farklı olarak:**

- Nesne property'leri doğrudan iterate edilemezken, Map elementleri doğrudan iterate edilebilir.

- Nesnede `size` property'si bulunmazken, Map içerisinde `size` property'si bulunmaktadır.

- Bir nesnede property'nin key bölümü string veya symbol veri tipinden oluşurken, Map elementlerindeki key bölümü için böyle bir sınırlama yoktur. key kısmı herhangi bir veri tipinden oluşabilir.

- Nesne property'leri arasındaki sıralama farklılık gösterebilir. Map objelerinde elementler eklenme sırasına göre sıralanır ve bu sıra korunur.

- Nesneler referans eşitliğine dayanır, Map'ler değer eşitliğine dayanır.

Şimdide her bir farka göz atalım.

### <a id='toc1_1_1_'></a>[Map Elementleri Doğrudan Iterable Edilebilir](#toc0_)

Nesnelerden farklı olarak `for...of` döngüsü veya `forEach` gibi iterable fonksiyonlar kullanarak Map özellikli değişkenin elementlerine doğrudan erişim sağlayabiliriz.

**Örnek**

```javascript
const student = {
  studentName: "Sibel",
  studentLastName: "Özel",
  studentNumber: 219,
};

// for...of döngüsü nesne üzerinde çalışmaz, hata verir.
try {
  for (const [key, value] of student) {
    console.log(`${key}: ${value}`);
  }
} catch (error) {
  console.error(`Hata mesajı: ${error.message}`);
}
```

    Hata mesajı: student is not iterable

Yukarıdaki örnekte `student` nesnesi için `for...of` döngüsünü doğrudan kullandığımızda hata mesajı alırız. Çünkü nesne property'leri doğrudan iterable özelliğe sahip değildirler.

Aynı örneği Map özellikli bir değişken oluşturarak gerçekleştirelim.

**Örnek**

```javascript
const student = new Map([
  ["studentName", "Sibel"],
  ["studentLastName", "Özel"],
  ["studentNumber", 219],
]);

// for...of döngüsü kullanarak Map elementlerine erişim
for (const [key, value] of student) {
  console.log(`student değişkeninin key kısmı: ${key} | value kısmı: ${value}`);
}
```

    student değişkeninin key kısmı: studentName | value kısmı: Sibel
    student değişkeninin key kısmı: studentLastName | value kısmı: Özel
    student değişkeninin key kısmı: studentNumber | value kısmı: 219

Görüleceği üzere `student` içerisindeki anahtar ve değerlere doğrudan erişim sağlayarak `for...of` döngüsünü kullandık.

### <a id='toc1_1_2_'></a>[`size` Property'sine Sahiptir](#toc0_)

Nesnelerden farklı olarak Map özellikli bir değişkenin boyutunu öğrenmek için `size` property'sinden faydalanırız.

**Örnek**

```javascript
const student = new Map([
  ["studentName", "Sibel"],
  ["studentLastName", "Özel"],
  ["studentNumber", 219],
]);

const student2 = {
  studentName: "Batuhan",
  studentLastName: "Akar",
  studentNumber: 50,
};

const student2Size = Object.entries(student2).length;

console.log(`student değişkeninin boyutu: ${student.size}`);
console.log(`student2 değişkeninin boyutu: ${student2Size}`);
```

    student değişkeninin boyutu: 3
    student2 değişkeninin boyutu: 3

Yukarıda `size` property'sini kullanarak `student` değişkeninin boyutunu öğreniyoruz.

**`student2` nesne özellikli değişkeninin boyutunu öğrenebilmek için:**

1. Örnekte görüleceği gibi `Object` nesnesi içerisindeki `entries()` metodu ile `student2` içerisindeki `key-value` eşleşmesinden oluşan array türünde bir içerik oluşturuyoruz.

2. Oluşturduğumuz içeriğin boyutunu `length` property'si ile öğreniyoruz.

3. Boyutun sonucunu `student2Size` adında bir değişkene aktarıyoruz.

Görüleceği üzere Map özellikli `student` değişkeninin boyutunu öğrenmek daha kolay oldu.

### <a id='toc1_1_3_'></a>[Key Kısmı Herhangi Bir Veri Tipinden Oluşabilir](#toc0_)

Hatırlarsak bir nesnenin key kısmı string veya symbol veri tipinden oluşmak zorundaydı. Map özellikli bir değişkenin key kısmı için böyle bir sınırlama yoktur key kısmı herhangi bir veri tipinden oluşabilir.

Mesela bir veri tabanından ID kısmını referans alarak personel id ve isimlerinden oluşan bir liste oluşturmak istiyoruz. Böyle bir durumda Map veri türünden faydalanılabilir.

**Örnek**

```javascript
const personal = new Map([
  [1, "Emin"],
  [2, "Murat"],
  [3, "Hasan"],
  [4, "Barçın"],
]);

for (const [key, value] of personal) {
  console.log(`Personelin ID'si: ${key} | Personelin Adı: ${value}`);
}
```

    Personelin ID'si: 1 | Personelin Adı: Emin
    Personelin ID'si: 2 | Personelin Adı: Murat
    Personelin ID'si: 3 | Personelin Adı: Hasan
    Personelin ID'si: 4 | Personelin Adı: Barçın

Yukarıdaki örnekte görüleceği üzere `personal` değişkeninin key kısımı number veri tipinden oluşmuştur.`for...of` döngüsünü kullanarak Personellerin ID ve isim bilgilerini konsola yazdırdık.

### <a id='toc1_1_4_'></a>[Map Objelerinde Elementler Eklenme Sırasına Göre Sıralanır](#toc0_)

JavaScript'teki nesnelerde, property'ler genellikle belirli bir sıralamaya sahip değildir. Nesne property'leri, eklendikleri sıraya göre sıralanmazlar. JavaScript'te nesne özellikleri key-value çiftleri şeklinde bulunur ve bu çiftlerin sıralanması spesifik bir düzeni takip etmez.

Ancak Map'lerde bu durum söz konusu değildir. Map içerisine eklenen bir element en sona depolanır.

**💡 Sıralamanın önemli olduğu durumlarda Map veya array veri türünden faydalanabiliriz.**

**Örnek**

```javascript
const personal = new Map([
  [1, "Emin"],
  [2, "Murat"],
  [3, "Hasan"],
  [4, "Barçın"],
]);

// personal değişkeni içerisine Burak adında bir çalışan ekliyoruz.
personal.set(5, "Burak");

for (const [key, value] of personal) {
  console.log(`Personelin ID'si: ${key} | Personelin Adı: ${value}`);
}
```

    Personelin ID'si: 1 | Personelin Adı: Emin
    Personelin ID'si: 2 | Personelin Adı: Murat
    Personelin ID'si: 3 | Personelin Adı: Hasan
    Personelin ID'si: 4 | Personelin Adı: Barçın
    Personelin ID'si: 5 | Personelin Adı: Burak

Yukarıdaki örnekte görüldüğü gibi `set()` metodu ile `personal` değişkeni içerisine "Burak" adında yeni bir çalışan ekledik. Listeyi sıraladığımızda "Burak" listenin sonuna yerleştirildi.

### <a id='toc1_1_5_'></a>[Map Objeleri Değer Eşitliğine Dayanır](#toc0_)

Nesne özellikli iki farklı değişkenin içeriği birbirleriyle aynı olsa bile, aynı referansa sahip değillerse birbirinden farklı kabul edilirler.

Map'lerde bu durum söz konusu değildir. İki Map aynı key-value çiftlerine sahipse, bu Map'ler birbirine eşit kabul edilir.

**Örnek**

```javascript
const obj1 = { firstName: "Hasan" };
const obj2 = { firstName: "Hasan" };

const map1 = new Map([
  ["Emin", "Altan"],
  ["Hasan", "Taş"],
]);

const map2 = new Map([
  ["Emin", "Altan"],
  ["Hasan", "Taş"],
]);

console.log(`obj1 ile obj2 birbirine eşit midir?: ${obj1 === obj2}`);
console.log(
  `map1 ve map2 birbirine eşit midir?: ${
    [...map1.keys()][0] === [...map2.keys()][0]
  }`
);
```

    obj1 ile obj2 birbirine eşit midir?: false
    map1 ve map2 birbirine eşit midir?: true

Yukarıdaki örnekte `obj1` ve `obj2` key-value eşleşmesi aynı olsa bile farklı bir değişken olarak kabul edilir. Çünkü nesne veri tipleri referans özelliklidir. **Referans eşitliği olmadığı sürece her iki değişken için bellekte ayrı iki adres kullanılır. Dolayısıyla `obj1` ve `obj2` değişkenlerinin kıyaslanması veri türüne ve depoladığı veriye değil bellekteki tutulduğu adrese göre yapılır. Şayet bu değişkenler aynı bellek adresini paylaşıyor olsaydı yani referans özellikli bir değişken kullanılarak kıyaslama yapılsaydı sonuç `true` olarak dönerdi.**

Map özellikli değişkenlerin kıyaslanmasında değişkenlerin key-value eşleşmesi ve bu eşleşmeye ait değerlerin aynı olması sonucun `true` olarak dönmesi için yeterlidir.

## <a id='toc1_2_'></a>[Map Veri Türünde Sık Kullanılan Metotlar](#toc0_)

Buraya kadar Map kavramını ve özelliklerini gördük şimdide biraz Map metotlarına değinelim.

### <a id='toc1_2_1_'></a>[`set()` Metodu](#toc0_)

Bir Map içerisine yeni element eklemeye yarar.

**Örnek**

```javascript
const student = new Map();

// set() metodu ile key-value'dan oluşan elementleri student içerisine depoluyoruz.
student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

for ([key, value] of student) {
  console.log(`student değişkeninin elementleri: ${key} ${value}`);
}
```

    student değişkeninin elementleri: 1 Emin
    student değişkeninin elementleri: 2 Murat
    student değişkeninin elementleri: 3 Can

Yukarıda `new Map()` constructor metodu ile `student` adında içeriği boş bir Map oluşturuyoruz ve `set()` metoduyla oluşturduğumuz değişkenin içerisine elementler depoluyoruz.

`for...of` döngüsü ile depoladığımız elementleri konsola yazdırıyoruz.

### <a id='toc1_2_2_'></a>[`get()` Metodu](#toc0_)

Map içerisindeki bir element için key kısmına denk gelen value kısmını geri döndürür.

**Örnek**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

// Map içerisinde 1 numaralı key'e denk gelen değere ulaşıyoruz.
console.log(student.get(1));
```

    Emin

Yukarıdaki örnekte `get()` metodu içerisinde kullandığımız argümana denk gelen key, Map içerisinde bulunacak ve key'e ait değer geri döndürülecektir.

Bir önceki örneğe geri dönelim ve `get()` metodu ile key değeri `1` olan Map içerisindeki elementin değerlerine ulaşalım.

**Örnek**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

for ([key, value] of student) {
  // get() metoduna key değişkenini argüman olarak geçirdik ve Map içerisindeki key kısımlarına ulaştık.
  console.log(`student değişkeninin elementleri: ${key} ${student.get(key)}`);
}
```

    student değişkeninin elementleri: 1 Emin
    student değişkeninin elementleri: 2 Murat
    student değişkeninin elementleri: 3 Can

### <a id='toc1_2_3_'></a>[`delete()` Metodu](#toc0_)

Map içerisinden element silmeye yarar.

**Örnek**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

// key değeri 2 olan elementi Map içerisinden siliyoruz.
student.delete(2);

for ([key, value] of student) {
  console.log(`student değişkeninin elementleri: ${key} ${student.get(key)}`);
}
```

    student değişkeninin elementleri: 1 Emin
    student değişkeninin elementleri: 3 Can

Yukarıda görüldüğü üzere `delete()` metoduna verilen argümana denk gelen key Map içerisinde bulunacak ve silinecektir.

### <a id='toc1_2_4_'></a>[`has()` Metodu](#toc0_)

Bir elementin Map içerisinde olup/olmadığını kontrol etmek isteyebiliriz. Bu durumda `has()` metodundan faydalanırız.

`has()` metodu boolean veri tipinde sonuç döndürür. Map içerisinde element var ise sonuç `₺rue` aksi durumda sonuç `false` olacaktır.

**Örnek**

```javascript
const student = new Map();

student.set(1, "Emin");
student.set(2, "Murat");
student.set(3, "Can");

// id'si 2 olan elementin varlığı student değişkeni içerisinde kontrol edilecektir.
console.log(
  `Sonuç: ${
    student.has(2)
      ? `id'si 2 olan element Map içerisinde bulunuyor. Öğrencinin ismi: ${student.get(
          2
        )}`
      : `id'si 2 olan element Map içerisinde bulunmuyor.`
  }`
);

// id'si 4 olan elementin varlığı student değişkeni içerisinde kontrol edilecektir.
console.log(
  `Sonuç: ${
    student.has(4)
      ? `id'si 4 olan element Map içerisinde bulunuyor. Öğrencinin ismi: ${student.get(
          4
        )}`
      : `id'si 4 olan element Map içerisinde bulunmuyor.`
  }`
);
```

    Sonuç: id'si 2 olan element Map içerisinde bulunuyor. Öğrencinin ismi: Murat
    Sonuç: id'si 4 olan element Map içerisinde bulunmuyor.

### <a id='toc1_2_5_'></a>[`forEach()` Metodu](#toc0_)

`forEach()` metodu ile Map içerisindeki her bir element için belirlediğimiz bir işlemi otomatik olarak çalıştırabiliriz. Böylece her element için tek tek işlem yapmamış olur ve zamandan kazanırız.

`forEach()` metodu içerisinde bir metot oluşturulması haline bu metot her Map elementi için tekrar tekrar çağrılıp kullanılacağı için buna **_callback function_** adı verilir.

**Örnek**

```javascript
const personal = new Map([
  [1, { name: "Emin", lastName: "Altan", salary: 5000 }],
  [2, { name: "Murat", lastName: "Taş", salary: 6000 }],
  [3, { name: "Sinan", lastName: "Can", salary: 7000 }],
  [4, { name: "Barçın", lastName: "Aktaş", salary: 8000 }],
]);

personal.forEach((value, key) => {
  console.log(
    `Personelin ID'si: ${key} | Personelin Adı: ${
      value.name
    } | Personelin Yeni Maaşı: ${value.salary + 1000}$`
  );
});
```

    Personelin ID'si: 1 | Personelin Adı: Emin | Personelin Yeni Maaşı: 6000$
    Personelin ID'si: 2 | Personelin Adı: Murat | Personelin Yeni Maaşı: 7000$
    Personelin ID'si: 3 | Personelin Adı: Sinan | Personelin Yeni Maaşı: 8000$
    Personelin ID'si: 4 | Personelin Adı: Barçın | Personelin Yeni Maaşı: 9000$

Yukarıdaki örnekte `personal` adında bir Map oluşturduk. Map içerisindeki elementlerin value kısmını nesne türünden oluşturduk. `forEach()` metodu ile her personelin `salary` key'ine ulaşıyor ve key'e denk gelen değeri 1000 artırıp yeni maaşı personel ile birlikte konsola yazdırıyoruz.

### <a id='toc1_2_6_'></a>[`entries()` Metodu](#toc0_)

Map içerisindeki elementler için bir iterable değişken oluşturur. Genelde `for...of` gibi döngülerde elementler arasında gezinmemizi sağlar.

**Örnek**

```javascript
const personal = new Map([
  [1, "Emin"],
  [2, "Murat"],
  [3, "Hasan"],
  [4, "Barçın"],
]);

for (const iterator of personal.entries()) {
  console.log(`Personel ID'si: ${iterator[0]}`);
  console.log(`Personel Adı: ${iterator[1]}`);
}
```

    Personel ID'si: 1
    Personel Adı: Emin
    Personel ID'si: 2
    Personel Adı: Murat
    Personel ID'si: 3
    Personel Adı: Hasan
    Personel ID'si: 4
    Personel Adı: Barçın

Yukarıdaki örnekte `entries()` metodunu kullanarak `personal` değişkeni içerisindeki elementleri `iterator` değişkenine kopyaladık.

1. `iterator[0]` ifadesi ile iterator değişkeni içerisinde tutulan key-value eşleşmesinde key kısmına ulaştık ve o anki depolanan değeri konsola yazdırdık.

2. `iterator[1]` ifadesi ile iterator değişkeni içerisinde tutulan key-value eşleşmesinde value kısmına ulaştık ve o anki depolanan değeri konsola yazdırdık.

## <a id='toc1_3_'></a>[Özet](#toc0_)

JavaScript'te Map kavramı, key-value eşleşmelerini depolamamıza olanak tanıyan güçlü bir veri yapısıdır. Bu özellik, nesnelerden farklı avantajlar sunarak programcılara daha esnek bir veri depolama ve işleme yöntemi sunar.

Map'ler, elementlerin sıralanması, iterable olmaları ve değer eşitliğine dayanmaları gibi özellikleriyle nesnelerden ayrılır. Bu özellikler, belirli durumlarda daha etkili ve güvenilir bir veri yönetimi sağlar.

Map metotları, element ekleme, silme, kontrol etme ve her bir element için belirli bir işlemi otomatik olarak uygulama gibi işlevselliği içerir. Bu metotlar, kodun daha temiz, okunabilir ve performanslı olmasına katkıda bulunur.

JavaScript'te Map kullanımı, özellikle birden çok değeri depolamamız ve bu değerlere daha rahat erişim sağlamamız gereken durumlarda oldukça yararlıdır. Öğrenci listeleri, personel bilgileri veya benzeri veri yapıları için Map'leri kullanarak kodumuzu daha düzenli ve etkili hale getirebiliriz.

Sonuç olarak, Map kavramı, JavaScript programlamada güçlü ve esnek bir veri yapısı sağlayarak, daha karmaşık uygulamalarda veri yönetimini kolaylaştırır ve geliştiricilere avantajlar sunar.
