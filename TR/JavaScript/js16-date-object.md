# JavaScript'de Tarih Nesnesi

Merhaba arkadaşlar serinin bu bölümünde JavaScript'de tarih özellikli nesneleri inceleyeceğiz.

Yazıda:

- Tarih özellikli nesne oluşturmaya yöntemlerine

- Tarih standartlarına

- Tarih metotlarına

- Tarihlerin kıyaslanmasına

- Tarih nesnesi oluştururken bazı ipuçlarına

Değineceğim.

İyi okumalar dilerim.


## JavaScript Tarih Nesnesi Oluşturma

JavaScript'de tarih türünde nesneler oluşturabiliriz. Tarih türünde bir nesne oluşturmak için `new Date()` constructor metodunu kullanırız.

Varsayılan olarak tarih nesnesi browser'ın time zone bilgisini kullanacak ve string bir değer şeklinde sonucu gösterecektir.

**Örnek**



```python
%%script node

const whatIsTheDate = new Date();

// Varsayılan olarak browser'ın time zone bilgisini kullanarak bir tarih nesnesi oluşturmuş olduk.
console.log(whatIsTheDate);
```

    [35m2023-12-10T18:15:53.104Z[39m


Tarih nesnesini 4 yöntemden biriyle oluşturabiliriz:

- `new Date()`

- `new Date(tarih string)`

- `new Date(yıl, ay, gün, saat, dakika, saniye, mili saniye)`

- `new Date(mili saniye)`

Şimdi bu yöntemlere değinelim.


### `new Date()` Yöntemi ile Tarih Oluşturma

Parametre kullanmadan `new Date()` constructor metodunu kullandığımızda varsayılan olarak bulunduğumuz zaman ve tarih için tarih türünde nesne oluşturulur.

Tarih bilgisi yıl, ay, gün, saat, dakika, saniye ve mili saniye bilgileri kullanarak oluşturulur.

**Örnek**



```python
%%script node

const whatIsTheDate = new Date();

// Şu anki tarihi ve zamanı konsola yazdırıyoruz.
console.log(whatIsTheDate.toString());

```

    Sun Dec 10 2023 21:16:35 GMT+0300 (GMT+03:00)


### `new Date(tarih string)` Yöntemi ile Tarih Oluşturma

Oluşturmak istediğimiz tarihi string şekilde `new Date()` constructor metodu içerisinde kullanabiliriz.

**Örnek**



```python
%%script node

const stringDate = new Date("October 13, 2014 11:13:00");

// Belirlediğimiz tarihi konsola yazdırıyoruz.
console.log(stringDate.toString());
```

    Mon Oct 13 2014 11:13:00 GMT+0300 (GMT+03:00)


### `new Date(yıl, ay, gün, saat, dakika, saniye, mili saniye)` Yöntemi ile Tarih Oluşturma

Bir tarihi ve zamanı belirlediğimiz parametrelere göre oluşturabiliriz. Bu durumda `new Date()` constructor metodunda 7 parametreden ihtiyacımıza uygun olanı kullanabiliriz.

**Örnek**



```python
%%script node

// Yıl ve ay parametreleri ile tarih türünden bir nesne oluşturuluyor.
const date = new Date(2018, 4);

// Yıl, ay, gün, saat, dakika ve saniye parametreleri ile tarih türünden bir nesne oluşturuluyor.
const date2 = new Date(2020, 0, 6, 3, 20, 58);

console.log(date.toString());

console.log(date2.toString());
```

    Tue May 01 2018 00:00:00 GMT+0300 (GMT+03:00)
    Mon Jan 06 2020 03:20:58 GMT+0300 (GMT+03:00)


**⚠️ JavaScript ay aralığını 0 ile 11 rakamları arasında değerlendirir. 0 rakamı Ocak ayına denk gelirken 11 rakamı Aralık ayına denk gelir.**

**Örnek**



```python
%%script node

const date = new Date(2018, 0);
const date2 = new Date(2018, 11);

// Dikkat ederseniz ay kısmı Ocak olarak belirlendi.
console.log(date.toDateString());

// Dikkat ederseniz ay kısmı Aralık olarak belirlendi.
console.log(date2.toDateString());
```

    Mon Jan 01 2018
    Sat Dec 01 2018


**⚠️ Ay değerinin 11'den fazla olması durumunda JavaScript herhangi bir hata mesajı döndürmez fakat 11'den fazla olan kısım yıl değerine devredilir ve değerlendirilir.**

**Bu durum gün için de geçerlidir. Şayet gün değeri 31'den fazla ise artan kısım ay değerine değerine devredilir ve değerlendirilir.**

**Örnek**



```python
%%script node

const date = new Date(2018, 12);
const date2 = new Date(2018, 10,32);

// Dikkat ederseniz yıl kısmı 2019 olarak belirlendi.
console.log(date.toDateString());

// Dikkat ederseniz ay kısmı Aralık olarak belirlendi. Halbuki Kasım olarak değerlendirilmesini beklerdik.
console.log(date2.toDateString());

```

    Tue Jan 01 2019
    Sun Dec 02 2018


**⚠️ JavaScript Ocak 1 1970 tarihinden bu yana geçen zamanı mili saniye olarak değerlendirir. Bir gün 86 400 000 mili saniyeden oluşur.**

**Bir tarih nesnesi sadece yıl parametresinden oluşuyorsa bu durumda JavaScript bu değeri de mili saniye olarak değerlendirir.**

**Örnek**



```python
%%script node

const date = new Date(2020);

console.log(date.toString());
```

    [33m20[39m


#### Tek veya İkili Notasyon Kullanımı

Yıl için tek veya ikili notasyon kullanıldığında JavaScript yıl değerini **_19xx_** formatında değerlendirir.

**Örnek**



```python
%%script node

const date = new Date(98, 11, 5);
const date2 = new Date(8, 11, 5);

// Yıl bölümü 1998 şeklinde oluşturuldu.
console.log(date.getFullYear());

// Yıl bölümü 1908 şeklinde oluşturuldu.
console.log(date2.getFullYear());
```

    [33m1998[39m
    [33m1908[39m


**⚠️ Kısa tarih veya ISO standart formatı kullanılarak tarih nesnesi oluşturulacaksa ay ve gün kısımları için ikili notasyon kullanılması tavsiye edilir. Şayet kullanılmazsa bazı tarayıcılar tarih nesnesini doğru yorumlayamaz ve hatalı sonuç üretir.**

**Örnek**

```javascript
// Dikkat ederseniz ay için tekli notasyon kullandık. ISO standardına bağlı kalarak oluşturulmuş date nesnesi bazı browser'larda hatalı sonuç döndürülmesine neden olacaktır.
const date = new Date("2015-3-25");
```


### `new Date(mili saniye)` Yöntemi ile Tarih Oluşturma

`new Date()` constructor metodunda parametre olarak number veri türü özellikli bir değer kullandığımızda JavaScript bu değeri mili saniye olarak yorumlar ve mili saniye değerini tarihe çevirir.

**⚠️ Mili saniye olarak değer kullandığımızda JavaScript başlangıç tarihi olarak Ocak 01, 1970 00:00:00 UTC değerini referans alır.**

**Örnek**



```python
%%script node

// Number veri türü özellikli değer tarih değerine çevrilecek.
const date = new Date(200000000000);

// Negatif mili saniye değerleri kullanabiliriz.
const date2 = new Date(-200000000000);


console.log(date.toDateString());
console.log(date2.toDateString());
```

    Mon May 03 1976
    Sat Aug 31 1963


## Tarih Standartları

JavaScript'de 3 tür tarih standardı vardır:

- ISO tarih standardı

- Kısa tarih standardı

- Uzun tarih standardı

Şimdi bunlara değinelim.


### ISO Tarih Standardı

JavaScript'in varsayılan olarak kullandığı tarih standardıdır. ISO standardı tüm tarayıcılar tarafından aynı şekilde yorumlandığından bir tarih nesnesi tüm tarayıcılara aynı şekilde oluşturulur ve görüntülenir.

**⚠️ Diğer standartlar tarayıcılar tarafından farklı şekillerde yorumlanabilir ve tarih nesnesini farklı şekillerde oluşturup gösterebilir. Bu bakımdan ISO tarih standardına bağlı kalınarak tarih nesnesi oluşturulması tavsiye edilir.**

Tarih ve zaman değerleri **_T_** harfi ile birbirlerinden ayrılırlar. **_Z_** harfi ise UTC değerini ifade eder.

**_UTC (Universal Time Coordinated)_** kavramı ile **_GMT (Greenwich Mean Time)_** kavramı eş değerdir. Her ikisi de aynı anlama gelir.

ISO standardında bir tarih nesnesi varsayılan olarak **_YYYY-MM-DD_** pattern'i kullanarak oluşturulur.

**Örnek**



```python
%%script node

// date tarih nesnesi YYYY-MM-DD pattern'ine göre oluşturuluyor.
const date = new Date("2015-03-20");
const date2 = new Date(2015, 3, 20);

console.log(date);
console.log(date2);

```

    [35m2015-03-20T00:00:00.000Z[39m
    [35m2015-04-19T21:00:00.000Z[39m


İsteğe bağlı olarak farklı pattern türleri kullanılabilir. Aşağıdaki örnekte **_YYYY-MM_** pattern'i ile bir tarih nesnesi oluşturulmuş.

**Örnek**



```python
%%script node

// date tarih nesnesi YYYY-MM pattern'ine göre oluşturuluyor.
const date = new Date("2015-03");

console.log(date.toDateString());
```

    Sun Mar 01 2015


### Kısa Tarih Standardı

Bir tarih nesnesi **_MM/DD/YYYY_** pattern'i kullanılarak belirlenmişse kısa tarih standardına uygun olarak oluşturulmuştur.

**Örnek**



```python
%%script node

// date nesnesini kısa tarih standardına göre oluşturduk.
const date = new Date("03/25/2015");

console.log(date.toString());
```

    Wed Mar 25 2015 00:00:00 GMT+0200 (GMT+03:00)


### Uzun Tarih Standardı

Bir tarih nesnesi **_MMM DD YYYY_** pattern'i kullanılarak belirlenmişse uzun tarih standardına uygun olarak oluşturulmuştur.

**Örnek**



```python
%%script node

// date nesnesini uzun tarih standardına göre oluşturduk.
const date = new Date("Mar 25 2015");

console.log(date.toString());
```

    Wed Mar 25 2015 00:00:00 GMT+0200 (GMT+03:00)


## Tarih Metotları

Tarih özellikli bir nesne oluşturduktan sonra tarih metotlarını kullanabiliriz.


### `toDateString()` Metodu

Varsayılan olarak tarih türünde bir nesne oluşturduğumuzda JavaScript `toString()` metodunu kullanarak nesneyi string formata dönüştürür. Bu durumdaki tarih özellikli nesnede varsayılan olarak saat, dakika, saniye GMT bilgisi ve mili saniye değerleri yer alır.

Tarih nesnesini daha okunabilir ve anlaşılabilir hale getirmek için `toDateString()` metodu kullanılır. `toDateString()` metodu yıl, ay ve gün şeklinde değer döndürür.

**Örnek**



```python
%%script node

// İkili notasyon kullanarak tarih nesnesi oluşturuyoruz.
const date = new Date(98, 11, 5);

console.log(date.toString());

// toDateString() metodu ile date değişkenini daha okunabilir hale getirdik. 
console.log(date.toDateString());
```

    Sat Dec 05 1998 00:00:00 GMT+0200 (GMT+03:00)
    Sat Dec 05 1998


### `toUTCString()` Metodu

Tarih nesnesini UTC standardına göre biçimlendirir. Bu türdeki bir tarih nesnesinde Yıl, ay, gün,saat, dakika, saniye bilgileri ile birlikte UTC standardına da yer verilir.

**Örnek**



```python
%%script node

const date = new Date();

// toUTCString() metodu ile date değişkeninde UTC standardına de yer verdik.
console.log(date.toUTCString());
```

    Sun, 10 Dec 2023 09:35:16 GMT


### `toISOString()`

Tarih nesnesini ISO standardına dönüştürür.

**Örnek**



```python
%%script node

const date = new Date();

// toISOString() metodu ile date değişkeni ISO standardına dönüşür.
console.log(date.toISOString());
```

    2023-12-10T09:35:16.964Z


### `getFullYear()` Metodu

Bir tarih nesnesinin yıl kısmını sonuç olarak döndürür.

**Örnek**



```python
%%script node

// Şu an ki tarih ve zaman değerini kullanıyoruz.
const date = new Date();

// date nesnesinin yıl kısmını sonuç olarak döndürür.
console.log(date.getFullYear());

```

    [33m2023[39m


**❗ `getYear()` Metodu ile de aynı sonuç elde edilebilir. Fakat `getYear()` metodunun deprecated olması sebebi ile kullanılmaması tavsiye edilir.**


### `getMoth()` Metodu

Bir tarih nesnesinin ay kısmını sonuç olarak döndürür. Döndürülen değer 0 ile 11 rakamları arasında olacaktır. 0 rakamı Ocak ayını ifade ederken 11 rakamı Aralık ayını ifade eder.

**Örnek**



```python
%%script node

// Şu an ki tarih ve zaman değerini kullanıyoruz.
const date = new Date();

// date nesnesinin ay kısmını sonuç olarak döndürür. 11 rakamı Aralık ayına denk gelir.
console.log(date.getMonth());

```

    [33m11[39m


**💡 Ay değerlerini array içerisinde tanımlayabilir ve kullanabiliriz.**

**Örnek**



```python
%%script node

const months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];

const date = new Date();
let month = months[date.getMonth()];

console.log(date.toDateString());
```

    Sun Dec 10 2023


### `getDate()` Metodu

Bir tarih nesnesindeki aya ait günleri sonuç olarak döndürür. Döndürülen değer 1 ile 31 rakamları arasında olacaktır.

**Örnek**



```python
%%script node

const date = new Date();

// Bugünü sayısal olarak konsola yazdırdık.
console.log(date.getDate());
```

    [33m10[39m


### `getHours()` Metodu

Bir tarih nesnesindeki saat kısmını sonuç olarak döndürür. Döndürülen değer 0 ile 23 rakamları arasında olacaktır.

**Örnek**



```python
%%script node

const date = new Date();

// Şu an ki saat sayısal olarak konsola yazdırdık.
console.log(date.getHours());
```

    [33m19[39m


### `getMinutes()` Metodu

Bir tarih nesnesindeki dakika kısmını sonuç olarak döndürür. Döndürülen değer 0 ile 59 rakamları arasında olacaktır.

**Örnek**



```python
%%script node

const date = new Date();

// Şu an ki dakikayı sayısal olarak konsola yazdırdık.
console.log(date.getMinutes());
```

    [33m2[39m


### `getSeconds()` Metodu

Bir tarih nesnesindeki saniye kısmını sonuç olarak döndürür. Döndürülen değer 0 ile 59 rakamları arasında olacaktır.

**Örnek**



```python
%%script node

const date = new Date();

// Şu an ki saniyeyi sayısal olarak konsola yazdırdık.
console.log(date.getSeconds());
```

    [33m22[39m


### `getMilliseconds()` Metodu

Bir tarih nesnesindeki salise kısmını sonuç olarak döndürür. Döndürülen değer 0 ile 999 rakamları arasında olacaktır.

**Örnek**



```python
%%script node

const date = new Date();

// Şu an ki saliseyi sayısal olarak konsola yazdırdık.
console.log(date.getMilliseconds());
```

    [33m786[39m


### `getDay()` Metodu

Bir tarih nesnesindeki haftanın çalışma gününü sonuç olarak döndürür. Döndürülen değer 0 ile 6 rakamları arasında olacaktır.

**❗ JavaScript'de varsayılan olarak çalışma günü 0'dan başlar bu da Pazar gününe denk gelir.**

**Örnek**



```python
%%script node

const date = new Date();

/** 
 * Bugün Pazar olması sebebi ile 0 değeri konsola yazdıracaktır. Pazar olduğunu gösterir. JavaScript'de Pazar 
 * günü varsayılan olarak haftanın ilk çalışma günüdür.
 */
console.log(date.getDay());
```

    [33m0[39m


**💡 Haftanın günlerini array olarak oluşturabiliriz. Bu durumda `getDay()` metodu ile çalışma gününe ait sayısal değeri string şeklinde geri döndürebiliriz.**

**Örnek**



```python
%%script node

// Çalışma günlerinden bir array oluşturuyoruz.
const worOfTheDays = ["Pazartesi", "Salı", "Çarşamba", "Perşembe", "Cuma", "Pazar"];

const date = new Date();

/** 
 * workOfTheDays değişkeni içerisinde şu an ki çalışma gününe ait sayısal değerin karşılığı aranır ve bulunan 
 * string değer konsola yazdırılır.
 */
console.log(worOfTheDays[date.getDay()]);
```

    Pazartesi


### `getTime()` Metodu

`newDate()` constructor metodu içerisinde parametre kullanılmışsa Ocak 1 1970 tarihinden bu yana geçen zamanı mili saniye olarak döndürür.

**Örnek**



```python
%%script node

const date = new Date("1988-10-10");

// getTime() metodu ile date değişkeni mili saniye olarak geri döndürülecektir.
console.log(date.getTime());

```

    [33m592444800000[39m


### `setFullYear()` Metodu

Boş bir tarih nesnesi oluşturulduktan sonra `setFullYear()` metodu ile tarih nesnesine ait yıl değeri ayarlanabilir.

**Örnek**



```python
%%script node

const date = new Date();

// setFullYear() metodu ile date değişkeni içerisinde yıl tanımlıyoruz.
date.setFullYear(2020);

console.log(date.getFullYear());

```

    [33m2020[39m


**💡 `setFullYear()` metodunda opsiyonel olarak ay ve gün bilgileri kullanılabilir.**

**Örnek**



```python
%%script node

const date = new Date();

// setFullYear() metodu içerisinde ay ve gün değerlerine de yer verdik.
date.setFullYear(2020,11,3);

console.log(date.toDateString());

```

    Thu Dec 03 2020


### `setMonth()` Metodu

Boş bir tarih nesnesi oluşturulduktan sonra `setMonth()` metodu ile tarih nesnesine ait ay değeri ayarlanabilir. Değer 0 ile 11 arasında bir rakam olmalıdır.

**Örnek**



```python
%%script node

const date = new Date();

// setMonth() metodu ile date değişkeni içerisinde ay tanımlıyoruz.
date.setMonth(10);

console.log(date.getMonth());

```

    [33m10[39m


### `setDate()` Metodu

Boş bir tarih nesnesi oluşturulduktan sonra `setDate()` metodu ile tarih nesnesine ait gün değeri ayarlanabilir. Değer 0 ile 31 arasında bir rakam olmalıdır.

**Örnek**



```python
%%script node

const date = new Date();

// setDate() metodu ile date değişkeni içerisinde gün tanımlıyoruz.
date.setDate(31);

console.log(date.getDate());

```

    [33m31[39m


**💡 `setDate()` metodu ile bir tarih nesnesine gün ekleyerek tarihi değiştirebiliriz.**

**Örnek**



```python
%%script node

const date = new Date("2023-11-5");

/** 
 * date değişkeni içerisinden tarihi alıyor ve 90 gün ekliyoruz. Bunu var olan tarihe 3 ay eklemek şeklinde 
 * düşünebiliriz.
 */
date.setDate(date.getDate()+90);

console.log(date.toDateString());

```

    Sat Feb 03 2024


### `setHours()` Metodu

Boş bir tarih nesnesi oluşturulduktan sonra `setHours()` metodu ile tarih nesnesine ait saat değeri ayarlanabilir. Değer 0 ile 23 arasında bir rakam olmalıdır.

**Örnek**



```python
%%script node

const date = new Date();

// setHours() metodu ile date değişkeni içerisinde saat tanımlıyoruz.
date.setHours(5);

console.log(date.getHours());

```

    [33m5[39m


### `setMinutes()` Metodu

Boş bir tarih nesnesi oluşturulduktan sonra `setMinutes()` metodu ile tarih nesnesine ait dakika değeri ayarlanabilir. Değer 0 ile 59 arasında bir rakam olmalıdır.

**Örnek**



```python
%%script node

const date = new Date();

// setMinutes() metodu ile date değişkeni içerisinde dakika tanımlıyoruz.
date.setMinutes(58);

console.log(date.getMinutes());

```

    [33m58[39m


### `setSeconds()` Metodu

Boş bir tarih nesnesi oluşturulduktan sonra `setSeconds()` metodu ile tarih nesnesine ait saniye değeri ayarlanabilir. Değer 0 ile 59 arasında bir rakam olmalıdır.

**Örnek**



```python
%%script node

const date = new Date();

// setMinutes() metodu ile date değişkeni içerisinde dakika tanımlıyoruz.
date.setSeconds(30);

console.log(date.getSeconds());

```

    [33m30[39m


## JavaScript'de Tarihlerin Kıyaslanması

Tarih özellikli iki nesne birbirleri ile kıyaslanabilir.

**Örnek**



```python
%%script node

const now = new Date();
const future = new Date();

// future tarih değişkenine yıl, ay ve gün şeklinde yeni değer atıyoruz.
future.setFullYear(2025, 11, 10);

/** 
 * Ternary (?) operatörü if...else anlamına gelir. Eğer future tarih nesnesi now tarih nesnesinden büyük olursa 
 * ilk ifade tersi durumda : işaretinden sonraki ifade çalışır.
 */
future > now ? console.log("future değişkeni büyüktür.") : console.log("future değişkeni küçüktür.");


```

    future değişkeni büyüktür.

