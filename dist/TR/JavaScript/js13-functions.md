# JavaScript'de Fonksiyonlar

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de **_fonksiyonları (metotları)_** inceleyeceğiz.

Yazıda:

- Fonksiyonların faydalarına.
- Fonksiyonun bölümlerine.
- `return` ve `()` işaretinin kullanımına.
- Local ve global değişkenlere.
- Değişken özellikli fonksiyonlara.

Değineceğim.

İyi okumalar dilerim.


## JavaScript'de Fonksiyonun Özellikleri

Fonksiyonlar kod bloklarından oluşurlar ve bu kod blokları arasındaki belirli görevleri yerine getirirler.

Değişken isimi oluşturmada kullanılan kurallar fonksiyon ismi oluşturmada kullanılan isim için de geçerlidir. Hatırlamak için [JavaScript Identifiers Kavramı](js02-basics-of-js.ipynb#javascript-identifiers-kavramı) başlığını ziyaret edebilirsiniz.

Fonksiyonlar temelde bize aşağıdaki faydaları sağlar.

1. Tekrar kullanılabilir kod blokları oluşturabiliriz. Böylece programın farklı bölümlerinde aynı işlevi gerçekleştirmek için fonksiyonu çağırmak yeterli olur, kodları yeniden yazmamış oluruz. Bu ilkeye **_DRY_**[^1] adı verilir.

2. Fonksiyon içerisindeki farklı argümanları kullanarak farklı sonuçlar elde edebiliriz.

Fonksiyonların yapıları object özelliklidir.

**Örnek**



```javascript
%%javascript

function myFunction() {
    return "Bu bir fonksiyondur."
}

// instanceof operatörünü bir değişken ile object arasındaki ilişkiyi anlamada kullanıyoruz. 
console.log (myFunction instanceof Object )

```

    [33mtrue[39m


## JavaScript Fonksiyonun Bölümleri

Şimdi de bir fonksiyonun bölümlerini inceleyelim.

![part-of-function](https://savvy.co.il/wp-content/uploads/2022/03/javascript-function.webp, "fonksiyonun kısımları")

Bir fonksiyon oluşturmak için `function` keyword'unden faydalanırız. `function` keyword'unu sırasıyla fonksiyon ismi, `()` ve `{}` işareti takip eder.

Fonksiyonda kullanılabilecek değişkenler`()` işaretleri arasında da oluşturulabilir. Buna fonksiyonun parametresi veya argümanları adı verilir. Parametreler birbirlerinden `,` işareti ile ayrılırlar.

`{}` işaretleri arasına çalıştırılacak kodlar yazılır. Bu kodlara **_function statement_** adı verilir.

Kodlar çalıştıktan sonra üretilen değer `return` keyword'u ile geri döndürülür. `return` keyword'unun yeri `{}` işaretleri arasındadır.

Bir fonksiyon `return` keyword'una ulaştıktan sonra çalışmayı sonlandırır ve sonrasındaki kodları çalıştırılmaz. Fonksiyon çağrıldığı yere sonuç döndürülür.

**Örnek**



```javascript
%%javascript

/** 
 * Fonksiyon ismi myFunction
 * 
 * Fonksiyonun argumanları parameter1 ve parameter2'dir.
 */
function myFunction (parameter1,parameter2){

  let result = parameter1 + parameter2
  
  /** 
  * return keyword'una ulaşıldığında fonksiyon çalışmayı 
  * durduracak ve aşağıdaki result değişkenine ait değeri 
  * geri döndürecektir.
  */
  return result;

// Aşağıdaki kod parçası çalışmayacaktır.
let result2 =parameter1/parameter2
}

// parameter1=2 ve parameter2=5 olacaktır.
console.log("Fonksiyonun sonucu " + myFunction(2, 5) + " 'dir.")
```

    Fonksiyonun sonucu 7 'dir.


## JavaScript `return` Keyword'u ve `()` İşaretlerinin Kullanımı

Aşağıdaki örnekte `return` keyword'u kullanılmamış bir fonksiyon görülüyor. Bu durumdaki fonksiyon çağrıldığında **_undefined_** değerini geri döndürür.

**Örnek**



```javascript
%%javascript

function myFunction() {
    let a, b = 2;
    a + b;
}

console.log(myFunction())
```

    [90mundefined[39m


Fonksiyonu çağırırken `()` işaretleri kullanmazsak fonksiyonun içeriği ekrana yazdırılır.

**💡 Bu özellikle bug/debug işlemleri için faydalı olabilir.**

**Örnek**



```javascript
%%javascript

function myFunction(){
    let result = 10 + 20;
    return result;
}

// Konsola function myFunction(){let result = 10+20; return result;} ifadesi yazdırılır.
console.log(myFunction);
```

    UsageError: Cell magic `%%` not found.


## JavaScript Fonksiyonlar İçerisindeki Local ve Global Değişkenler

Bir fonksiyon içerisinde tanımlanan değişkenler **_local değişkenler_** olarak ifade edilir. Bu değişkenlere fonksiyonun dışarısından ulaşılamaz.

**❗ `var` keyword'u kullanılarak oluşturulan bir değişken için bu durum geçerli değildir. `var` ile oluşturulan bir değişken global özelliğe sahiptir. Program içerisinde her yerden erişilebilir.**



```javascript
%%javascript

function myFunction(parameter1, parameter2) {
    let value = 5;
    const value2 = 10;
    var value3 = 20;
}

/** 
 * ReferenceError: value is not defined ifadesi konsola yazdırılır.
 *  const ve le ile oluşturulan bir değişken bulunduğu scope'un dışında kullanılamaz.
 */
console.log(value)
console.log(value2)

/** 
 * value3 değişkeni var keyword'u kullanarak tanımlandığı için global özelliğe sahip oldu.
 *  Yani tanımlandığı scope dışarısından erişilip kullanılabilir. Konsola 20 rakamı yazdırılır.
 */
console.log(value3)
```


    <IPython.core.display.Javascript object>


## JavaScript Değişken Özellikli Fonksiyonlar

Bir değişkenin depoladığı değer fonksiyon olabilir. Bu durumdaki değişkenin içeriği konsola yazdırıldığına aslında konsola fonksiyona ait içerik yazdırılır.

Ek olarak değişken özellikli fonksiyonlar matematiksel işlemlere sokulabilir.

**Örnek**



```javascript
%%javascript

function myFunction() {
    return 10 + 20;
}

let result = myFunction();

// result değişkeni myFunction() referans gösteriyor.
console.log("myFunction() fonksiyonun sonucu " + result + " 'dur");

console.log ("myFunction() fonksiyonu matematiksel işlemlere sokulabilir. Örnekte ifadesinin sonucu olan  "+ (result+10)+" değeri konsola yazdırılır.")
```

    myFunction() fonksiyonun sonucu 30 'dur
    myFunction() fonksiyonu matematiksel işlemlere sokulabilir. Örnekte ifadesinin sonucu olan  40 değeri konsola yazdırılır.


Footnotes

[^1]: "DRY" JavaScript kod yazma prensibi, "Kendini Tekrarlama Yapma" olarak adlandırılır. Bu prensip, kodunuzu tekrarlanan veya aynı işlevi yerine getiren kod parçalarını minimize ederek ve kodun yeniden kullanılabilirliğini teşvik ederek yazmanızı teşvik eder.

