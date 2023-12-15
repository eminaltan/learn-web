# JavaScript Null Veri Türü ve Özellikleri

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_null_** veri türünü inceleyeceğiz.

Yazıda:

- Null veri türüne.
- JavaScript'de Null veri türünün kullanımına.
- Null veri türüne sahip bir değişkenin boolean olarak sahip olduğu değere.
- Matematiksel işlemlerde null özellikli bir değişkenin sonuca etkisine.
- Null ile empty ve undefined arasındaki farklara.

Değineceğim.

İyi okumalar dilerim.


## JavaScript Null Veri Türü

JavaScript'de null veri türü değişkende değer olmadığını ancak gelecekte bir değer atanabileceğini gösterir.

null veri türüne sahip bir değişken tanımlamak için `null` keyword'u kullanılır.

`null` keyword'u depolayan bir değişken expression içerisinde kullanıldığında JavaScript değişkenin değerini 0 rakamına dönüştürür.

`null` keyword'u JavaScript'in kullanımı için rezerv edilmiştir. Yani bir değişken veya metot ismi `null` ile başlayamaz.

Null veri türü primitive özelliklidir ve **_immutable_** yapıdadırlar yani değiştirilemezler. **Buna rağmen veri tipi object özelliğine sahiptir.**

**Örnek**



```javascript
%%javascript

let x =null;

// Konsola "object" ifadesi yazdırılacaktır.
console.log(typeof(x));

// x variable 0 rakamına dönüştürülecektir. 
let y=x+1;

// Konsola 1 rakamı yazdırılacaktır.
console.log(y);

```

    object
    [33m1[39m


Null veri türüne sahip bir değişkenin boolean değeri `false` olacaktır. Detaylı bilgi almak için [Sonucu Daima false Olan İfadeler](js09-boolean-data-type.ipynb#sonucu-daima-false-olan-i̇fadeler) başlığını ziyaret edebilirsiniz.

**Örnek**



```javascript
%%javascript

let x =null;

// Konsola "false" ifadesi yazdırılır. Boolean() fonksiyonu ile bir değişkenin boolean olarak türünü öğrenebiliriz.
console.log(Boolean(x))

```

    [33mfalse[39m


**➖ Null ile Undefined Arasındaki Farklar**

1. Null özellikli değişken herhangi bir değere sahip değildir. Hatırlarsanız undefined özellikli değişkenin varsayılan olarak taşıdığı değer yine undefined'di. Bu bakımdan null ile undefined birbirlerinden ayrılırlar.

2. Null özellikli bir değişkenin veri tipi object'dır, undefined özelliğine sahip değişkenin veri tipi undefined'dır.

**Örnek**



```javascript
%%javascript
// x'in varsayılan değeri undefined olacaktır.
let x;

// x' in depoladığı değer undefined'dır. Konsola "undefined" yazdırılır.
console.log(x);

// y değişkeni herhangi bir değere sahip değildir.
let y = null;

// y 'nin depoladığı herhangi bir değer yoktur. Bunu belirtmek için konsola "null" ifadesi yazdırılır.
console.log(y);

// "undefined" iletisi konsola yazdırılır, x'in veri tipi undefined'dır.
console.log(typeof x);

// "object" iletisi konsola yazdırılır, null özellikli değişkenin veri tipi object'dir.
console.log(typeof y);

```

    [90mundefined[39m
    [1mnull[22m
    undefined
    object


**➖ Null ile Empty Arasındaki Fark**

Empty özellikli bir değişkenin veri tipi string özelliklidir. null özellikli bir değişkenin veri tipi ise object özelliklidir.



```javascript
%%javascript
let x = null;

let y ="1";

// Konsola "false" ifadesi yazdırılacaktır. Çünkü x'in veri tipi object, y'nin veri tipi ise string'dir.
console.log(x===y);

// "object" ifadesi konsola yazdırılır.
console.log (typeof(x))

// "string" ifadesi konsola yazdırılır.
console.log (typeof(y))
```

    [33mfalse[39m
    object
    string

