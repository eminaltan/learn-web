# JavaScript BıgInt Veri Türü ve Veri Tipi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_BıgInt_** veri türlerini ve veri tiplerini inceleyeceğiz.

Yazıda:

- BıgInt veri türüne ve veri tipine.
- Kullanım alanlarına **_number_** veri tipinden farkına.
- Aritmetiksel operatörlerin kullanımına.

Değineceğim.

İyi okumalar dilerim.


## JavaScript BigInt Veri Türü

JavaScript'de iki sayısal veri türü vardır. Bunlardan biri **_BigInt_** diğeri ise **_Number_** veri türüdür. Bu kısımda BigInt veri türünü inceleyeceğiz.

BıgInt veri türü primitive özelliklidir ve **_immutable_** yapıdadırlar yani değiştirilemezler.

JavaScript'de BıgInt değerler ondalıklı olarak ifade **edilemezler.**

JavaScript BigInt türündeki değişkenler büyük tam sayı türündeki değerleri depolamaya yarar. JavaScript'de tam sayı değerlerin hassasiyeti 15 haneye kadardır.

BigInt veri tipi ES2020 JavaScript'e dahil olmuştur. Bu sebeple 2020 öncesi release edilen tarayıcılarda çalışmayabilir.

BigInt türünde bir değer oluşturmak için `BigInt()` metodu veya değerinin sonuna `n` ifadesi yerleştirilir.

**Örnek**



```javascript
%%javascript

// bigint1 değişkeninin veri türü BigInt'dir.
let bigint1 = 9999999999999999n;

// BigInt() metodunu kullanarak da BigInt veri türünde değer tanımlayabiliriz.
let bigint2 = BigInt(1234567890123456789012345);

```

**⚠️ BigInt veri türünde `/` operatörü dışında diğer aritmetiksel operatörler kullanılabilir. `/` operatörünün kullanılmamasının nedeni BigInt veri türünün ondalıklı sayıları desteklememesidir.**

**Şayet BigInt özellikli bir değişken için `/` operatörü kullanılacaksa değişken number özellikli veri türüne dönüştürülür sonra işlem yapılır.**

**Örnekler**

Aşağıdaki örnekte iki bigint özellikli değişken için çarpma işlemi yapılıyor.



```javascript
%%javascript

let x = 9007199254740995n;
let y = 9007199254740995n;
let z = x * y;

// 81129638414606735738984533590025n ifadesi konsola yazılır.
console.log(z);

```

    [33m81129638414606735738984533590025n[39m



```javascript
%%javascript

let x = 5n;

/**
 * BigInt veri tipine sahip x değişkeni ilk baş number veri türüne dönüştürülüyor
 * sonra işlem yapılıyor ve elde edilen sonuç y değişkenine depolanıyor.
 * 
 * ⚠️ y değişkenin veri tipi number olduğuna dikkat edelim.
 */
let y = Number(x) / 2;

console.log(y);
console.log(typeof y)
```

    [33m2.5[39m
    number


**➖ BigInt türündeki bir değer number türündeki bir değere convert edildiğinde (dönüştürüldüğünde) veri kayıpları söz konusu olabilir. Bunun sebebi number veri türünün en fazla 15 haneden oluşmasıdır. Bu ifade BıgInt ile number veri türüne sahip değer arasındaki farklı oluşturur.**

BigInt veri türleri hexadecimal, octal veya binary notasyonu ile ifade edilebilirler.

**Örnek**



```javascript
%%javascript

// Hexadecimal kullanımı
let hexadecimal = 0x20000000000006n;

// Octal kullanımı
let octal = 0o400000000000000006n;

// Binary kullanımı
let binary = 0b100000000000000000000000000000000000000000000000000011n;

console.log("Hexadecimal değerin BigInt karşlığı = "+ hexadecimal)
console.log("octal değerin BigInt karşlığı = "+ octal)
console.log("binary değerin BigInt karşlığı = "+ binary)
```

    Hexadecimal değerin BigInt karşlığı = 9007199254740998
    octal değerin BigInt karşlığı = 9007199254740998
    binary değerin BigInt karşlığı = 9007199254740995


## JavaScript BıgInt Veri Tipi

BıgInt veri türü özellikli değişkenlerin veri tipleri de bigint olacaktır.

**Örnek**



```javascript
%%javascript

let bigint1 = 9999999999999999n;

let bigint2 = BigInt(1234567890123456789012345);

console.log("bigint1'in veri tipi "+typeof bigint1+" 'dir." )
console.log("bigint2'nin veri tipi "+typeof bigint2+" 'dir." )
```

    bigint1'in veri tipi bigint 'dir.
    bigint2'nin veri tipi bigint 'dir.



```javascript
%%javascript

let x = 5n;

let y = x / 2;

// TypeError: Cannot mix BigInt and other types, use explicit conversions hatası ile karşılaşırız.
console.log(y);
```


    <IPython.core.display.Javascript object>

