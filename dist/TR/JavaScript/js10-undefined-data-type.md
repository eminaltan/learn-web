# JavaScript Undefined Veri Türü ve Veri Tipi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_undefined_** veri türünü ve veri tipini inceleyeceğiz.

Yazıda:

- Undefined veri türüne ve veri tipine.
- Undefined veri tipine sahip bir değişkenin boolean olarak sahip olduğu değere.
- Undefined ile empty ve null arasındaki farklara.

Değineceğim.

İyi okumalar dilerim.


## JavaScript Undefined Veri Türü

JavaScript'de **_undefined_** veri türü bir değişkenin tanımlanmamış olduğunu veya değişkene bir değerin atanmamış olduğunu ifade eder.

Undefined veri türü primitive özelliklidir ve **_immutable_** yapıdadırlar yani değiştirilemezler.

JavaScript'de bir değişken deklarasyonu yapılırken içeriğine değer depolanmamış ise varsayılan olarak undefined değeri depolanacaktır.

`undefined` keyword'u kullanılarak da undefined veri tipine sahip bir değişken oluşturulabilir.

**Örnek**



```javascript
%%javascript

// x değişkeni varsayılan olarak undefined değerine sahip olacaktır.
let x;

// Aynı zamanda undefined keyword'u kullanarak da undefined veri türüne sahip değişken  oluşturabiliriz.
let y=undefined;

// Her iki değişken için de "undefined" ifadesi konsola yazdırılır.
console.log (x);
console.log (y);
```

    [90mundefined[39m
    [90mundefined[39m


**❗ Undefined identifier (değişken ismi) olarak kullanılabilir fakat bu durumda kodları anlamak veya debug işlemlerinde zorluklar ortaya çıkar.**

**Örnek**



```javascript
%%javascript

// Global scope içerisinde iki tane fonksiyonumuz var.

// İlk fonksiyonumuzun parametresi yok.
(() => {

  // undefined isminde bir değişken tanımlanıyor ve içeriğine "foo" string'i depolanıyor.
  const undefined = "foo";

  // undefined değişkeninin depoladığı veri tipi string olacak ve konsola "foo, string" ifadesi yazdırılacaktır.
  console.log(undefined, typeof undefined); 
})

// İlk fonksiyonumuz çağrılıyor.
();


// İkinci fonksiyonumuzun undefined isminde bir parametresi var.
((undefined) => {

  // Konsola undefined parametresinin depoladığı veri ve veri tipi yazdırılacaktır.
  console.log(undefined, typeof undefined); 
})

// İkinci fonksiyona "EA" adında bir string gönderdik.
("EA");

```

    foo string
    EA string


Yukarıda görüldüğü gibi kodları analiz etmek zorlaştı.

Undefined veri türüne sahip bir değişkenin boolean değeri `false` olacaktır. Detaylı bilgi almak için [Sonucu Daima false Olan İfadeler](js09-boolean-data-type.ipynb#sonucu-daima-false-olan-i̇fadeler) başlığınız ziyaret edebilirsiniz.

**Örnek**



```javascript
%%javascript

let x;

/** 
 * Boolean() fonksiyonu kullanarak bir değişkenin boolean olarak tuttuğu değeri öğrenebiliriz.
 * Konsola "false" yazdırılacaktır.
 */
console.log(Boolean(x));


```

    [33mfalse[39m


Bir metotta (fonksiyonda) `return` keyword'u açıkça ifade edilmemişse metot varsayılan olarak undefined ifadesini geri döndürür.



```javascript
%%javascript

function drive(){
    // Metot bir statement döndürmüyor.
}

// Konsola "undefined" yazdırılacaktır.
console.log(drive())


function swim(){
    return "swim performed"
}
// Konsola "swim performed" yazdırılacaktır.
console.log(swim())
```

    [90mundefined[39m
    swim performed


**➖ Undefined ile Null Arasındaki Fark**

1.  Undefined özellikli değişkenin varsayılan olarak depoladığı değer yine undefined'dır. Null değeri depolayan değişken herhangi bir değere sahip değildir. Bu bakımdan null ile undefined birbirlerinden ayrılırlar.

2.  Undefined özelliğine sahip değişkenin veri tipi undefined'dır, null özellikli bir değişkenin veri tipi object'dir.

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

// "object" iletisi konsola yazdırılır, null özellikli variable'ın veri tipi object'dir.
console.log(typeof y);

```

    [90mundefined[39m
    [1mnull[22m
    undefined
    object


**➖ Undefined ile Empty Arasındaki Fark**

Empty özellikli bir değişkenin veri tipi string özelliklidir. undefined özellikli bir değişkenin veri tipi ise object özelliklidir.

**Örnek**



```javascript
%%javascript

let x;

let y="";

// x değişkeni undefined, y değişkeni ise string veri tipine sahiptir. Konsola sırasıyla "undefined" ve "string" ifadesi yazdırılacaktır.
console.log(typeof(x))
console.log(typeof(y))

// x ve y değişkenleri depoladığı değer bakımından da farklıdır. Konsola "false" ifadesi yazdırılır.
console.log(x==y);

```

    undefined
    string
    [33mfalse[39m


## JavaScript Undefined Veri Tipi

Undefined veri türü özellikli değişkenlerin veri tipleri de undefined olacaktır.

**Örnek**



```javascript
%%javascript

let value;

let value2 = undefined;

console.log("value'un veri türü " + value + " 'dır.")
console.log("value2'nin veri türü " + value2 + " 'dır.");
```

    value'un veri türü undefined 'dır.
    value2'nin veri türü undefined 'dır.


Undefined veri tipine sahip bir değişken aritmetiksel işlemlerde kullanıldığında expression'un sonucu `NaN` (Not a Number) olacaktır. Çünkü işlem sonucu sayısal veya rakamsal bir değerden oluşmayacaktır. **_NaN_** teriminin kullanımı için [JavaScript `NaN` Not a Number Terimi](js07-numeric-data-type.ipynb#javascript-nan-not-a-number-terimi) başlığına bakabilirsiniz.


```javascript
%%javascript

let x;

let y =x+1;

// Konsola "NaN" ifadesi yazdırılır. Çünkü x+undefined'ın matematiksel bir karşılığı yoktur.
console.log(y);

// Buna rağmen sonucun veri tipi number'dır. Konsola "number" yazdırılır.
console.log(typeof(y))
```

    [33mNaN[39m
    number

