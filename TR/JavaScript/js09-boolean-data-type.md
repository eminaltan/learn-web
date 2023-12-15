# JavaScript Boolean Veri Türü ve Tipi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_boolean_** veri türünü ve veri tipini inceleyeceğiz.

Yazıda:

- Boolean veri türüne ve veri tipine

- Sonucu `false` olan ifadelere

- Object tipindeki boolean türlerine

Değineceğim.

İyi okumalar dilerim.

## JavaScript Boolean Veri Türü

Genelde mantıksal expression'larda kullanılır.

Bu sayede expression sonucuna göre programın akışını yönlendirilebilir.

Boolean ifadeler expression'un sonucuna göre değer döndürür. Expression sonucu doğruysa döndürülecek değer `true` yanlışsa `false` olacaktır.

**Örnek**

```javascript
%%javascript

let x = false;
let y = true;

console.log(`x'in değeri ${x}'dır.`);
console.log(`y'nin değeri ${y}'dur.`);

```

    x'in değeri false'dır.
    y'nin değeri true'dur.

**💡 Bazen bir statement'in boolean sonucunu merak edebiliriz. Bunun için `Boolean()` metodundan faydalanabiliriz.**

Bu özellikle debug işlemlerinde veya sonucunu tahmin edemediğimiz kompleks condition'lar yazarken faydalı olur.

**Örnek**

```javascript
%%javascript

// Konsola true ifade yazdırılır.
console.log(Boolean(8 > 4));

// Sadeleştirebiliriz yine konsola true ifadesi yazdırılacaktır.
console.log(8 > 4);

```

    true
    true

### Sonucu Daima `false` Olan İfadeler

Aşağıdaki ifadelerin hepsi boolean veri tipi göz önüne alınarak düşünüldüğünde `false` değerini üretir:

1. Değişkenin depoladığı değer `0` rakamı olduğunda.

2. Değişkenin depoladığı değer `-0` rakamı olduğunda. Çünkü `-0`'ın karşılığı yoktur.

3. Değişkenin depoladığı değer empty string olduğunda. Yani `""` arasında bir değere yer verilmediğinde.

4. Değişkene değer atanmadığında varsayılan olarak depolayacağı değer `undefined` olacaktır. Bu durumdaki değişkenin boolean değeri `false` olur.

5. Değişkenin değeri `null` olduğunda.

6. Değişkene `false` değeri depolandığında.

7. Aritmetiksel bir işlemin sonucu `NaN` olduğunda.

**Örnekler**

```javascript
%%javascript

let x = 0;

console.log(`x değerinin depoladığı değer: ${Boolean(x)}'dır.`);

let x2 = -0;

console.log(`x2 değerinin depoladığı değer: ${Boolean(x2)}'dır.`);

let x3 = "";

console.log(`x3 değerinin depoladığı değer: ${Boolean(x3)}'dır.`);

let x4;

console.log(`x4 değerinin depoladığı değer: ${Boolean(x4)}'dır.`);

let x5 = null;

console.log(`x5 değerinin depoladığı değer: ${Boolean(x5)}'dır.`);

let x6 = false;

console.log(`x6 değerinin depoladığı değer: ${Boolean(x6)}'dır.`);

let x7 = 10 / "Kalem";

console.log(`x7 değerinin depoladığı değer: ${Boolean(x7)}'dır.`);
```

    x değerinin depoladığı değer: false'dır.
    x2 değerinin depoladığı değer: false'dır.
    x3 değerinin depoladığı değer: false'dır.
    x4 değerinin depoladığı değer: false'dır.
    x5 değerinin depoladığı değer: false'dır.
    x6 değerinin depoladığı değer: false'dır.
    x7 değerinin depoladığı değer: false'dır.

## JavaScript Boolean Veri Tipi

Boolean veri türü özellikli değişkenlerin veri tipleri de boolean olacaktır.

**Örnek**

```javascript
%%javascript

let booleanData = false;
console.log(`booleanData değişkenin veri tipi ${typeof booleanData}'dir.`);
```

    booleanData değişkenin veri tipi boolean'dir.

## JavaScript Object Veri Tipinde Boolean Veri Türü

JavaScript'de boolean özellikli değişkenler normalde **_immutable_**, ilkel ve string veri tipine sahip veri türleridir.

Ancak `new Boolean()` metodu kullanılarak object veri tipinde boolean veri türleri oluşturulabilir.

**⚠️ Object veri tipinde oluşturulan boolean özellikli bir değişken ile normal yöntem kullanılarak oluşturulan boolean özellikli değişkenin veri tipi birbirinden farklıdır.**

**Örnek**

```javascript
%%javascript

// booleanData değişkeni nesne özellikli olup veri tipi object'dir.
let booleanData = new Boolean("true");

console.log(`booleanData değişkenin depoladığı değer: ${booleanData}'dur.`);
console.log(`booleanData değişkeninin veri tipi: ${typeof booleanData}'dir.`);

let booleanData2 = false;

console.log(`booleanData2 değişkenin depoladığı değer: ${booleanData2}'dur.`);
console.log(`booleanData2 değişkeninin veri tipi: ${typeof booleanData2}'dir.`);
```

    booleanData değişkenin depoladığı değer: true'dur.
    booleanData değişkeninin veri tipi: object'dir.
    booleanData2 değişkenin depoladığı değer: false'dur.
    booleanData2 değişkeninin veri tipi: boolean'dir.

**❗ Object tipinde boolean veri tiplerinin kullanılması tavsiye edilmez. Özellikle mantıksal operatörlerin kullanıldığı expression'larda beklenmedik sonuçlar ile karşılaşabiliriz.**

**Ek olarak kodları komplike hale getireceği için kod bloklarının yavaş çalışmasına neden olacaktır.**

**Object veri tipindeki iki değişkenin kıyaslanması durumunda sonuç daima `false` olarak geri döner.**

**Örnek**

```javascript
%%javascript

let x = false;
let y = new Boolean(false);

// x ve y değişkeni aynı veriyi depolamaları sebebi ile geri dönen değer true olacaktır.
console.log(x == y);

/**
 * x ve y değişkeni aynı veriyi depolamalarına  rağmen farklı veri tipine sahip
 * olduklarından geri dönen değer false olacaktır.
 */
console.log(x === y);

let m = new Boolean(false);
let n = new Boolean(false);

/**
 * m ve n her ikisi de aynı türde değeri ve aynı veri tipini tutmasına rağmen konsola false
 * değeri yazdırılacaktır. Çünkü object tipindeki değişkenler unique olma özelliği taşır.
 */
console.log(m === n);

```

    true
    false
    false
