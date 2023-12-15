# JavaScript'de Math Nesnesi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de Math nesnesini inceleyeceğiz.

Yazıda:

- Math nesnesinin özelliklerine

- Math nesnenin içerisindeki property ve metotlara eriş sağlayarak kullanmayı

- Math nesnesi içerisindeki property ve metotların ne işe yaradıklarına

Değineceğim.

İyi okumalar dilerim.

## JavaScript Math Nesnesine Giriş

Math nesnesi JavaScript içerisinde hali hazırda bulunan ve bir takım matematiksel işlemleri yapmamızı sağlayan property ve metotlardan oluşan bir nesne türüdür.

Math nesnesindeki property'leri veya metotları kullanmak için diğer nesnelerde olduğu gibi bir constructor (veya constructor function) tanımlamamıza gerek yoktur. İhtiyaç duyduğumuz property veya metodu Math nesnesi içerisinden direkt çağırıp kullanabiliriz.

Math nesnesi içerisinde ihtiyaç duyduğumuz bir property'i kullanmak için `Math.propertyName` pattern'ini kullanırız. Buradaki `propertyName` kullanmak istediğimiz property'nin ismini ifade eder. Şayet ihtiyaç duyduğumuz bir metot ise `Math.methodName()` pattern'ini kullanırız. Buradaki `methodName()` kullanmak istediğimiz metodun ismini ifade eder.

Math nesnesi içerisindeki tüm property'ler sabit özelliklidir. Örneğin `Math.PI` property'si PI değerini ifade eder ve bu değer değiştirilemezdir.

**Örnek**

```javascript
%%javascript

// Math.PI property'sini çağıyoruz.
console.log(`Math nesnesi içerisindeki Math.PI property'sinin değeri = ${Math.PI}'dür.`);

// Math.max() metodunu çağırıp kullanıyoruz.
console.log(`Değerler arasındaki en büyük rakam = ${Math.max(3, 4, 5, 67, 90)}'dır.`);

```

    Math nesnesi içerisindeki Math.PI property'sinin değeri = 3.141592653589793'dür.
    Değerler arasındaki en büyük rakam = 90'dır.

Gerekli tanımlamaları yaptıktan sonra Math nesnesi içerisinde hali hazırda bulunan property'lere ve metotlara değinelim.

## Math Nesnesinin Metotları

Şimdilik en çok kullanılan bir takım metotlara değineceğim. Dokümanın içeriğini güncelledikçe tüm Math nesnesi metotlarına yer vermiş olacağız.

### `Math.round()` Metodu

Ondalıklı bir değeri kendisine yakın bir tam sayıya yuvarlamak için kullanılır.

**Örnek**

```javascript
%%javascript

// Aşağıdaki değerler 5 tam sayısına yuvarlanacaktır.
console.log(Math.round(4.9));
console.log(Math.round(4.5));

// Aşağıdaki değer 4 tam sayısına yuvarlanacaktır.
console.log(Math.round(4.4));
```

    5
    5
    4

### `Math.ceil()` Metodu

Ondalıklı bir değeri kendisinden **bir üst değere** tam sayı olarak yuvarlamak için kullanılır.

**Örnek**

```javascript
%%javascript

// Aşağıdaki değerler 5 tam sayısına yuvarlanacaktır.
console.log(Math.ceil(4.9));
console.log(Math.ceil(4.5));
console.log(Math.ceil(4.4));

// Negatif değerlerde Math.ceil() metodu kullanımı.
console.log(Math.ceil(-4.9));

```

    5
    5
    5
    -4

### `Math.floor()` Metodu

Ondalıklı bir değeri kendisinden **bir alt değere** tam sayı olarak yuvarlamak için kullanılır.

**Örnek**

```javascript
%%javascript

// Aşağıdaki değerler 4 tam sayısına yuvarlanacaktır.
console.log(Math.floor(4.9));
console.log(Math.floor(4.5));
console.log(Math.floor(4.4));

// Negatif değerlerde Math.floor() metodu kullanımı.
console.log(Math.floor(-4.9));

```

    4
    4
    4
    -5

### `Math.trunc()` Metodu

Ondalıklı bir değerin tam sayı kısmını geri döndürür.

**Örnek**

```javascript
%%javascript

// Aşağıdaki değerler 4 tam sayısına yuvarlanacaktır.
console.log(Math.trunc(4.9));


```

    4

### `Math.sign()` Metodu

Bazen bir değerin negatif, nötr veya pozitif olup/olmadığını öğrenmek isteriz. Bu işlemi farklı yöntemler ile gerçekleştirebiliriz. Bunlardan biri de `Math.sign()` metodudur.

`Math.sign()` metodu içerisinde kullanılan sayısal değer negatif ise -1, nötr ise 0 şayet değer pozitif ise 1 değeri döndürülür.

Metodun `NaN` (Not a Number) değer döndürdüğü durumda ise parametrenin sayısal bir özelliğe sahip olmadığını anlayabiliriz.

**Örnek**

```javascript
%%javascript

// Değerin pozitif olması sebebi ile dönecek olan değer 1'dir.
console.log(Math.sign(4.9));

// Değerin nötr olması sebebi ile dönecek olan değer 0'dır.
console.log(Math.sign(0));

// Değerin negatif olması sebebi ile dönecek olan değer -1'dir.
console.log(Math.sign(-4.9));

// Değer sayısal bir özelliğe sahip olmadığından NaN ifadesi geri döndürülür.
console.log(Math.sign("test"));
```

    1
    0
    -1
    NaN

### `Math.pow()` Metodu

Bir değerin kuvvetini almak için kullanılır. İki parametresi vardır. İlk parametre kuvveti alınacak değeri ifade ederken ikinci parametre kuvvet düzeyini ifade eder.

**Örnek**

```javascript
%%javascript

console.log(`8'in 2.kuvveti = ${Math.pow(8, 2)}'dür.`);

console.log(`5'in 3.kuvveti = ${Math.pow(5, 3)}'dir.`);
```

    8'in 2.kuvveti = 64'dür.
    5'in 3.kuvveti = 125'dir.

### `Math.pow()` Metodu

Bir değerin karekökünü almak için kullanılır.

**Örnek**

```javascript
%%javascript

console.log(`64'ün karekökü = ${Math.sqrt(64)}'dir.`);

console.log(`625'in karekökü = ${Math.sqrt(625)}'dir.`);

```

    64'ün karekökü = 8'dir.
    625'in karekökü = 25'dir.

### `Math.abs()` Metodu

Bir değerin mutlak değerini almak için kullanılır.

**Örnek**

```javascript
%%javascript

console.log(`-4.9'un mutlak değeri: ${Math.abs(-4.9)}'dur.`);
```

    -4.9'un mutlak değeri: 4.9'dur.

### `Math.min()` ve `Math.max()` Metotları

`Math.min()` metodu içerisinde kullanılan sayısal değerler arasındaki en küçük değeri geri döndürür.

`Math.max()` metodu içerisinde kullanılan sayısal değerler arasındaki en büyük değeri geri döndürür.

Değerler birbirlerinden **_,_** işareti ile ayrılırlar.

**Örnek**

```javascript
%%javascript

console.log(`Parametreler içerisindeki en küçük değer: ${Math.min(2, 4, 6, 8, -10)}'dur.`);

console.log(`Parametreler içerisindeki en büyük değer: ${Math.max(2, 4, 6, 8, -10)}'dir.`);
```

    Parametreler içerisindeki en küçük değer: -10'dur.
    Parametreler içerisindeki en büyük değer: 8'dir.

### `Math.random()` Metodu

0 ile 1 arasında rastgele ondalıklı sayı üretmek için kullanılır.

Üretilen değer 1 rakamından büyük olamaz.

**Örnek**

```javascript
%%javascript

console.log(`Şu an rastgele üretilen sayısal değer: ${Math.random()}`);
```

    Şu an rastgele üretilen sayısal değer: 0.5296522048265973

`Math.random()` metodu `Math.floor()` metodu ile birlikte kullanılarak random tam sayılar üretilebilir.

**Örnek**

```javascript
 %%javascript

/**
 * Örnekte Math.random() metoduyla üretilen sayı 10 ile çarpılacak, bulunan değer Math.floor() metoduyla
 * kendinden bir küçük tam sayıya yuvarlanacak ve değerin tam sayı kısmı alınarak konsola yazdırılacaktır.
 *
 * Örnek 0 ile 9 rakamı arasında random sayı üretecektir.
 */
console.log(`Random üretilen tam sayı: ${Math.floor(Math.random() * 10)}`);
```

    Random üretilen tam sayı: 9
