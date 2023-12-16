# JavaScript Symbol Veri Türü ve Tipi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_symbol_** veri türlerini ve veri tiplerini inceleyeceğiz.

Yazıda:

- Symbol veri türüne ve veri tipine.
- Boolean olarak depoladığı değere.
- Bir nesne içerisinde **_key_**[^1] olarak kullanılmasına.
- Benzersiz sabit olarak kullanımına.
- Global hale getirilmesine.
- Veri güvenliğini için kullanımına.
- Object tipindeki symbol veri türüne.

Değineceğim.

İyi okumalar dilerim.


## JavaScript Symbol Veri Türü

Symbol veri türü primitive özelliklidir ve **_immutable_** yapıdadırlar yani değiştirilemezler.

Symbol veri türleri **unique** özelliğe sahiptirler. Bu sebeple nesne tanımlı değişken içerisinde **_key_**[^1] olarak kullanılır ve değerlere erişim sağlanır.

Yine unique olması sebebi ile program içerisinde **_API_**[^2] gibi sabit değerler için değişken oluşturmada sıklıkla symbol veri türlerinden faydalanılır.

Symbol veri türleri aynı zamanda bir verinin encapsulation ilkesine göre gizliliğini ve güvenliğini sağlar.

Symbol veri türü ES6 ile JavaScript'de dahil olmuştur.

Symbol veri türünde bir değişken oluşturmak için ` Symbol("Description")` metodundan faydalanılır. Buradaki `Description` terimi genelde symbol veri türünün hangi amaçla oluşturulduğunu ifade eder. Kullanılması isteğe bağlı opsiyoneldir.

**💡`Description` teriminin kullanılması tavsiye edilir. Böylece symbol'un ne amaçla oluşturulduğu bilinecektir. Kullanılması özellikle bug/debug işlemlerinde faydalı olacaktır.**

**Örnek**



```javascript
%%javascript

// Örnekte symbol veri türünün tanımlanması görülmektedir.

const pName = Symbol("Personel ismini tanımlar.");
const sName = Symbol();

/** 
 * Description tanımlanmış olması bir debug işleminde 
 * değişkenin hangi amaçla oluşturulduğunu belirlemede yardımcı olacaktır.
 */
console.log(pName)

// Symbol() ifadesi konsola yazdırılır.
console.log(sName)
```

    [32mSymbol(Personel ismini tanımlar.)[39m
    [32mSymbol()[39m


Symbol veri türü özellikli bir değişken boolean olarak daima `true` değerini tutar.



```javascript
%%javascript

const pName = Symbol("Personel ismini tanımlar.");
const sName = Symbol();

// Boolean() metodu ile değişkenleri boolean olarak tuttuğu veri türünü öğreniyoruz.
console.log(Boolean(pName))
console.log(Boolean(pName))
```

    [33mtrue[39m
    [33mtrue[39m


## JavaScript Symbol Veri Tipi

Symbol veri türü özellikli değişkenlerin veri tipleri de symbol olacaktır.

**Örnek**



```javascript
%%javascript

const sym = Symbol("Bir symbol veri türü örneği.")

console.log("sym değişkeninin veri tipi "+typeof sym+" 'dur.")
```

    sym değişkeninin veri tipi symbol 'dur.


Symbol veri türleri unique özelliklidir. aynı description'a sahip değişkenlerin türü ve veri tipi olarak birbirinden farklıdır.

Bunun nedeni primitive özellikli veri türleri için değişken tanımlama işleminde bellekte yeni bir adres ayrılmasıdır.



```javascript
%%javascript

const sym = Symbol("Symbol değeri")
const sym2 = Symbol("Symbol değeri");

// Hem veri türü hem de veri tipi olarak birbirinden farklıdırlar. Konsola false ifadesi yazılacaktır.
console.log(sym == sym2);
console.log(sym === sym2);
```

    [33mfalse[39m
    [33mfalse[39m


## JavaScript Symbol Veri Türünün Nesne içerisinde Kullanımı


Symbol veri türüne sahip olan değişkenler sıklıkla nesne içerisinde depolanan veriye ulaşmak için key olarak kullanılırlar.

Diyelim ki bir kod parçası farklı yerlerde veya programlarda kullanılsın. Bu durumda aynı key ismini kodun farklı bölümlerinde kullanabilir bu sayede kodun duplicate edilmesiyle oluşabilecek sorunların önüne geçebiliriz.

Bunu bir örnek ile açıklayalım.

**Örnek**



```javascript
%%javascript

// Aşağıda student değişkeni nesne özelliklidir ve id key'ine 276 değeri depolanmış.

let student = { firstName: "Emin" };
let id = Symbol("Öğrenci numarası");

student[id] = 276;

console.log(student[id]);
```

    [33m276[39m


`student` nesnesini başka bir programda kullandığımızı düşünelim. Program içerisinden orijinal kodlara erişip yeni bir **_property_**[^3] eklemek veya var olan property'i güncellemek mümkün değildir.

Bu durumda symbol özellikli veri türlerini kullanılarak orijinal kodları başka bir program için özelleştirebiliriz. Anlaşılacağı üzere bu bize kodlar üzerinde esneklik kazandırır. Farklı programlarda aynı key ismini kullanabilir ve depolanan değerleri değiştirebiliriz. Böylece depolanan değerin duplicate edilmesinden kaynaklanabilecek sorunların önüne geçebiliriz.

**Örnek**

Örnekte id key'in tuttuğu değer başka bir program için özelleştirilmiş.



```javascript
%%javascript

let student = { firstName: "Emin" };
let id = Symbol("Öğrenci numarası");

// Başka bir program içerisinde id key'ine ulaşıp 500 değerini depoluyoruz. 
student[id] = 500;

console.log(student[id]);
```

    [33m500[39m


Yukarıdaki program başka bir yerde kullanıldığında `id` key'in depoladığı değer overwrite edilebilir. Bu durumda `id` key'in depoladığı değer değişecektir.

**Örnek**



```javascript
%%javascript

let student = { firstName: "Emin" };

// Bir önceki programdan alınan değer.
student.id = 500;
console.log("Bir önceki programda student değişkeninin değeri = "+student.id); 

// Başka bir program tarafından id'ye ait değer overwrite ediliyor.
student.id = "800";

// student.id property'sinin yeni değeri 800 olacaktır.
console.log("Yeni programda student değişkeninin değeri = "+student.id); 

```

    Bir önceki programda student değişkeninin değeri = 500
    Yeni programda student değişkeninin değeri = 800


## JavaScript Symbol Veri Türünün Benzersiz Sabit Olarak Kullanılması

Symbol veri türünün unique olmasının getirdiği bir avantaj olarak program içerisinde **benzersiz sabit değerler** oluşturabiliriz. Özellikle bu yöntem **_API_** oluşturmada sıklıkla kullanılır.

**Örnek**

Aşağıdaki `Symbol()` metodu içerisinde nesne oluşturuluyor ve `const:true` property'si ile symbol'un constant olduğu ifade ediliyor.



```javascript
%%javascript

// Symbol içerisinde nesne oluşturulduğuna dikkat edelim.
const sym = Symbol("Unique özellikli bir sabit.", { const: true })

console.log(sym)
```

    [32mSymbol(Unique özellikli bir sabit.)[39m


## JavaScript Symbol Veri Türünün Global Hale Getirilmesi

Bazen bir symbol veri türü özellikli değişkeni programın her yerinden ulaşıp kullanmak isteriz. Bu durumda `global:true` property'sini kullanırız.

**Örnek**

Aşağıdaki `Symbol()` metodu içerisinde nesne oluşturuluyor ve `global:true` property'si ile symbol'un global olduğu ifade ediliyor.



```javascript
%%javascript

// Symbol içerisinde nesne oluşturulduğuna dikkat edelim.
let sym = Symbol("Unique özellikli bir sabit.", { global: true })

console.log(sym)
```

    [32mSymbol(Unique özellikli bir sabit.)[39m


## JavaScript Symbol Veri Türü ile Verinin Güvenliğinin Sağlanması

Bazen private değişkenler veya metotlar oluşturmak isteriz. Böylece verilerin dışarıdan erişilmesini engeller ve güvenliğini sağlarız. Böyle bir durumda symbol veri türü oldukça sık kullanılır. (Encapsulation İlkesi)

**Örnek**



```javascript
%%javascript

const id = Symbol("Personel id'si");

const person = { firstName: "Ömer", age: 25, [id]: 14533 };

// Konsol çıktısında id key'ine ait değer yazdırılmaz.
for (const key in person) {
  console.log(key)
}
```

    firstName
    age


## JavaScript Object Veri Tipinde Symbol Veri Türleri

Bildiğimiz üzere JavaScript'de symbol özellikli değişkenler normalde **_immutable_**, ilkel ve symbol veri tipine sahip veri türleridir.

**Ancak `Object()` metodu kullanılarak object veri tipinde symbol veri türleri oluşturulabilir.**

**⚠️ Object veri tipinde oluşturulan symbol özellikli bir değişken ile normal yöntem kullanılarak oluşturulan symbol özellikli değişkenin veri tipi birbirinden farklıdır.**

**Örnek**



```javascript
%%javascript

const personId = Symbol("Personel ID");

// personId değişkeninin veri tipini object veri tipine çevirmek için Object() metodundan faydalandık.
const objectPersonalId= Object(personId)


console.log("objectPersonalId değişkeninin veri tipi " + typeof (objectPersonalId) + " 'dir.");

```

    objectPersonalId değişkeninin veri tipi object 'dir.


Footnotes

[^1]:JavaScript nesnelerinde key (anahtar) kullanılmasının temel amacı, verileri organize etmek, erişmek ve işlemek için bir yapı sağlamaktır. 
[^2]:JavaScript'te "API" (Application Programming Interface), genellikle başka bir yazılım veya hizmet ile iletişim kurmak, veri alışverişi yapmak veya belirli işlevselliğe erişmek için kullanılan bir arayüzü ifade eder. 
[^3]:JavaScript'te bir nesnenin özelliklerini tanımlamak için kullanılan terim "property"dir. Nesneler, key-value çiftleri şeklinde özellikleri saklarlar ve bu özellikler "property" olarak adlandırılır. Bir nesnenin her bir property'si, nesnenin özelliklerini temsil eder ve bir key (anahtar) ile ilişkilendirilmiş bir değeri içerir.

