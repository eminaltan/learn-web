# JavaScript'te Set'ler <a id='toc0_'></a>

Merhaba arkadaşlar serinin bu bölümünde JavaScript'te **_Set_** kavramını inceleyeceğiz.

Yazıda:

- [JavaScript'te Set Kavramı](#toc1_1_)
- [Set Veri Türünde Sık Kullanılan Metotlar](#toc1_2_)
  - [`add()` Metodu](#toc1_2_1_)
  - [`delete()` Metodu](#toc1_2_2_)
  - [`has()` Metodu](#toc1_2_3_)
  - [`forEach()` Metodu](#toc1_2_4_)
  - [`values()` Metodu](#toc1_2_5_)
- [`size` Property'sinin Kullanımı](#toc1_3_)
- [Özet](#toc1_4_)

Değineceğim.

İyi okumalar dilerim.

If you want to read English version of this article please visit [this link](js20-sets.md).

<!-- vscode-jupyter-toc-config
	numbering=false
	anchor=true
	flat=false
	minLevel=1
	maxLevel=6
	/vscode-jupyter-toc-config -->
<!-- THIS CELL WILL BE REPLACED ON TOC UPDATE. DO NOT WRITE YOUR TEXT IN THIS CELL -->

## <a id='toc1_1_'></a>[JavaScript'te Set Kavramı](#toc0_)

**JavaScript **_Set_** kavramını array veri türüne benzetebiliriz. Arraylar'dan farklı olarak:**

- Set'ler içerisindeki elementler **unique** olma özelliği taşır. Yani aynı element bir Set içerisinde tekrar edilemez. Bundan ötürü Set'ler benzersiz değerleri depolamak için kullanılırlar.

- Set elementine erişmek için metotlar kullanılır. Hatırlayacağınız üzere array'da elementlere erişim için index'leri kullanıyorduk.

Bir Set oluşturmak için `new Set()` constructor metodu kullanılır.

**Örnek**

```javascript
const arry = [2, 2, 4, 5, 6, 6];

const set1 = new Set([2, 2, 4, 5, 6, 6]);

console.log(`arry değişkenin elementleri: ${arry}`);
console.log(`set1 değişkenin elementleri: ${[...set1]}`);

console.log(`arry değişkeninin boyutu: ${arry.length}`);
console.log(`set1 değişkeninin boyutu: ${set1.size}`);
```

    arry değişkenin elementleri: 2,2,4,5,6,6
    set1 değişkenin elementleri: 2,4,5,6
    arry değişkeninin boyutu: 6
    set1 değişkeninin boyutu: 4

Yukarıdaki örnekte `new Set()` metodunu kullanarak yeni bir Set oluşturmuş olduk.

Görüleceği üzere `arry` ve `set1` değişkenleri içerisinde `2` ve `6` elementlerinden 2 tane bulunmakta, her iki değişken içeriğini konsola yazdırdığımızda `set1` içerisindeki `2` ve `6` elementlerinin konsola sadece 1 kere yazdırıldığını görüyoruz.

**⚠️ Bir Set içerisine birden fazla aynı değişken veya değer depolanmak istendiğinde veri listesinin ilk başındaki değişken veya değer referans alınarak işlem gerçekleştirilir.**

`arry` ve `set1` değişkenlerinin boyutuna baktığımızda sayısal olarak aynı olmasına rağmen `set1` değişkeninin boyutunun aslında 4 olduğunu görürüz. Bunun sebebi bir Set, benzersiz elementleri içinde sadece bir kez tutar. Bu nedenle, Set'in boyutu, içindeki benzersiz eleman sayısına eşittir.

Verilerin depolanmasının yanında Set'ler; iki değişken içeriğinin birleştirerek, kesiştirerek veya farkının alınması yöntemiyle benzersiz bir liste oluşturmak için de kullanılabilir.

**Örnek**

```javascript
let set1 = new Set([1, 2, 3]);
let set2 = new Set([2, 3, 4]);

/**
 * union değişkeninin içeriği iki setin birleşmesinden oluşacaktır. İçerik oluşturulurken tekrarlı değerler 1
 * kez kullanılacaktır.
 */
let union = new Set([...set1, ...set2]);

// set1 ve set2 değişkenleri içerisindeki ortak elementleri buluyoruz.
let intersection = new Set([...set1].filter((x) => set2.has(x)));

// set1 ve set2 değişkenleri içerisindeki ortak olmayan! elementleri buluyoruz.
let difference = new Set([...set1].filter((x) => !set2.has(x)));

console.log(`Birleştirme işleminin sonucu: ${[...union]}`);

console.log(`Kesiştirme işleminin sonucu: ${[...intersection]}`);

console.log(`Fark alma işleminin sonucu: ${[...difference]}`);
```

    Birleştirme işleminin sonucu: 1,2,3,4
    Kesiştirme işleminin sonucu: 2,3
    Fark alma işleminin sonucu: 1

Yukarıdaki örnekte iki set için birleştirme, kesiştirme ve fark alma işlemleri yapılıyor.

Set özellikli yeni değişken tanımlanarak işlemlerin gerçekleştirildiğine dikkat edelim.

**💡 Bazen array özellikli bir değişkenin benzersiz veri listesinden oluşmasını isteyebiliriz. Bu durumda array özellikli değişkeni `new Set()` metodu içerisine yerleştirilerek benzersiz elementlerden oluşan bir Set haline getirebiliriz.**

**Örnek**

```javascript
const arry = [2, 2, 2, 2, 2, 3, 4, 5, 6, 7, 7];

// arry değişkeni içerisinde tekrarlı veriler kaldırılacaktır.
const set1 = new Set(arry);

console.log(`set1 değişkeninin elementleri: ${[...set1]}`);
```

    set1 değişkeninin elementleri: 2,3,4,5,6,7

## <a id='toc1_2_'></a>[Set Veri Türünde Sık Kullanılan Metotlar](#toc0_)

Buraya kadar Set kavramını ve özelliklerini gördük şimdide sık kullanılan Set metotlarına değinelim.

### <a id='toc1_2_1_'></a>[`add()` Metodu](#toc0_)

Bir Set'e yeni bir element eklemek için kullanılır.

**Örnek**

```javascript
// İçeriği boş Set oluşturuyoruz.
const set1 = new Set();

// add() metodu kullanımı
set1.add("Emin");
set1.add("Hasan");
set1.add("Murat");

console.log(`set1 değişkeninin elementleri: ${[...set1]}`);
```

    set1 değişkeninin elementleri: Emin,Hasan,Murat

Yukarıdaki örnekte görüleceği gibi eklemek istediğimiz değeri argüman olarak `add()` metodu içerisine yazıyoruz.

### <a id='toc1_2_2_'></a>[`delete()` Metodu](#toc0_)

Bir Set içerisinden belirlediğimiz elementi siler.

**Örnek**

```javascript
const names = ["Emin", "Hasan", "Murat"];

const set1 = new Set(names);

// set1 içerisinden Hasan elementi kaldırılacaktır.
set1.delete("Hasan");

console.log(`set1 değişkeninin elementleri: ${[...set1]}`);

// Orijinal Set içeriği bozulmadı.
console.log(`names değişkeninin elementleri: ${[...names]}`);
```

    set1 değişkeninin elementleri: Emin,Murat
    names değişkeninin elementleri: Emin,Hasan,Murat

Yukarıdaki örnekte görüleceği gibi silmek istediğimiz değeri argüman olarak `delete()` metodu içerisine yazıyoruz.

Dikkat ederseniz iççerik bakımından `set1` ve `names` değişkenleri birbirine eşit olmasına rağmen `set1` içerisinden silinen değer `names` değişkeninin içeriğini bozmadı.

Silme işleminde index değerlerini de kullanabiliriz.

**Örnek**

```javascript
const names = ["Emin", "Hasan", "Murat"];

const set1 = new Set(names);

// set1 içerisindeki 2.elemente erişilecek ve bu değer silinecek.
set1.delete(names[1]);

console.log(`set1 değişkeninin elementleri: ${[...set1]}`);
```

    set1 değişkeninin elementleri: Emin,Murat

Yukarıdaki örnekte Set içerisinde 2 numaralı elemente erişiyor ve siliyoruz. `delete(names[1])` ifadesi `set1` değişkeni içerisindeki 2 numaralı elemente erişilmesini ve bu elementin silinmesini sağlar.

### <a id='toc1_2_3_'></a>[`has()` Metodu](#toc0_)

Bir değerin veya değişkenin Set içerisinde olup/olmadığını kontrol etmek isteyebiliriz. Bu durumda `has()` metodundan faydalanırız.

`has()` metodu boolean veri tipinde sonuç dönderir. Set içerisinde element var ise sonuç `₺rue` aksi durumda sonuç `false` olacaktır.

**Örnek**

```javascript
const names = ["Emin", "Hasan", "Murat"];

const set1 = new Set(names);

// Hasan elementini set1 içerisinde varlığını kontrol edecektir.
console.log(
  `Sonuç: ${
    set1.has("Hasan")
      ? "Aranan element Set içerisinde bulunuyor."
      : "Aranan element Set içerisinde bulunmuyor."
  }`
);

// Derya elementini set1 içerisinde varlığını kontrol edecektir.
console.log(
  `Sonuç: ${
    set1.has("Derya")
      ? "Aranan element Set içerisinde bulunuyor."
      : "Aranan element Set içerisinde bulunmuyor."
  }`
);
```

    Sonuç: Aranan element Set içerisinde bulunuyor.
    Sonuç: Aranan element Set içerisinde bulunmuyor.

Yukarıdaki örnekte `has()` metodu içerisine varlığını kontrol etmek istediğimiz elementi argüman olarak yazdık. `true` değer dönmesi halinde elementin Set içerisinde bulunduğunu `false` olarak dönmesi halinde elementin Set içerisinde bulunmadığını anlarız.

### <a id='toc1_2_4_'></a>[`forEach()` Metodu](#toc0_)

Bazen Set içerisinde her bir element için belli bir işlemi yaptırmak isteyebiliriz. Böyle bir durumda `forEach()` metodundan faydalanırız.

**Örnek**

```javascript
const set1 = new Set([1, 2, 3, 4, 5, 6]);

let arry = [];

// Her bir elementin değeri +1 artırılacaktır.
set1.forEach((val) => arry.push(val + 1));

console.log(`arry değişkeninin elementleri: ${arry}`);
```

    arry değişkeninin elementleri: 2,3,4,5,6,7

Yukarıdaki örnekte `forEach()` metodu yardımıyla `set1` değişkeni içerisindeki her bir elemente ulaşıyor ve element değerini +1 artırıyoruz ve elde ettiğimiz sonucu `arry` değişkeninin içerisine depoluyoruz.

### <a id='toc1_2_5_'></a>[`values()` Metodu](#toc0_)

Set içerisindeki elementleri bir nesnenin property'si gibi kullanmak isteyebiliriz. Bu durumda `values()` metodundan faydalanırız. `values()` metodu Set içerisindeki elementler için bir iterable türünde değişken oluşturmaya yarar. Böylece Set içerisindeki elementlere erişim sağlanır ve Set içerisindeki elementler arasında gezinmek mümkün hale gelir.

**Örnek**

```javascript
let set1 = new Set([1, 2, 3, 4, 5, 6]);

// values() metoduyla bir iterable oluşturulur.
let setValues = set1.values();

// Iterable üzerinde forEach kullanarak Set elemanlarına erişilir.
setValues.forEach((element) => console.log(element));
```

## <a id='toc1_3_'></a>[`size` Property'sinin Kullanımı](#toc0_)

Set'lerde normalde property bulunmaz. Aslında `size` bir property değil, bir metodun özelliğidir. `size` property'si Set'in içindeki benzersiz eleman sayısını verir.

Konuya ilk girişteki örneğe geri dönelim ve `size` property'sini inceleyelim.

**Örnek**

```javascript
const set1 = new Set([2, 2, 4, 5, 6, 6]);

console.log(`set1 değişkeninin boyutu: ${set1.size}`);
```

    set1 değişkeninin boyutu: 4

Yukarıda görüldüğü üzere `size` property'si `set1` değişkeninin boyutunu verdi.

## <a id='toc1_4_'></a>[Özet](#toc0_)

JavaScript'te Set kavramı, benzersiz değerleri depolamak için kullanılan bir veri türüdür. Array'lerden farklı olarak, Set'lerde her bir element sadece bir kez bulunabilir. Set oluşturmak için `new Set()` constructor'ını kullanabiliriz.

Set'ler, benzersiz veri listeleri oluşturmak ve eleman ekleme, silme, kontrol etme gibi işlemler için kullanışlıdır. Özellikle benzersiz değerlerle çalışmak istendiğinde Set'leri tercih edebiliriz.
