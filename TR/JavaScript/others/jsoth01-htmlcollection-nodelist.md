# HTMLCollection ve NodeList Kavramları

Merhaba arkadaşlar bugün HTMLCollection ile NodeList konularına değineceğim.

Yazıda:

- HTMLCollection ve NodeList kavramına
- Aralarındaki benzerliklere ve farklara
- **_live collection_** ve **_static collection_** terimlerine
- Koleksiyonlara erişim yöntemlerine
- Koleksiyonların döngülerde kullanımına
- Neye göre koleksiyonları kullanacağımıza

Değineceğim.

İyi okumalar dilerim.


## HTML Collection Nedir?

Belirlediğimiz bir kritere göre DOM elementlerinden bir liste oluşturabiliriz. Bu listeye HMTLCollection adı verilir. Liste spesifik bir içerikten (child elementlerden), aynı tag'a sahip veya aynı class ismini kullanan HTML elementlerinden oluşabilir.

**Örnek**

Aşağıdaki örnekte üç tane `<button>` elementinde `btn` class'ı tanımlanmış. Bu elementleri `getElementsByClassName()` metoduyla HTML DOM'dan seçiyor ve HTMLCollection haline getiriyoruz.

```html
<button class="btn">First button</button>
<button class="btn">Second button</button>
<button class="btn">Third button</button>

<script>
  const buttonElements = document.getElementsByClassName("btn");
  console.log(buttonElements);
</script>
```

![a HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-04-at-8.10.41-AM.png)

Dönen değer görünürde array veri türüne benzer ancak bir HTMLCollection array veri türü özelliğine sahip değildir.


## NodeList Nedir?

Bir node list DOM ağacındaki bağımsız bir elementtir. Bu elementler attribute veya text içeriklerinden oluşabilir.

**Örnek**

Aşağıdaki örnekte `querySelectorAll()` metodu ile HTML ağacındaki `btn` class'ına sahip elementleri seçerek NodeList şeklinde liste döndürüyoruz.

```html
<button class="btn">First button</button>
<button class="btn">Second button</button>
<button class="btn">Third button</button>

<script>
  const buttonElements = document.querySelectorAll(".btn");
  console.log(buttonElements);
</script>
```

![a NodeList](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-04-at-8.33.08-AM.png)


## HTMLCollection ile NodeList Arasındaki Benzerlikler

Her ikisi de array türünde görünse de aslında array özelliğine sahip değillerdir.

Array veri türlerinde olduğu gibi liste içerisindeki öğelere index değerleri ile erişebiliriz ve `length` property'sini kullanabiliriz. Böylece bir koleksiyonun ne kadar uzun olduğunu öğrenebiliriz.

**Örnek**

Aşağıdaki örnekte `<div>` elementi üç tane `<p>` elementinden oluşuyor. Bu elementler `paragraph` adında bir class'a sahip. Elementlerden ilkine ulaşalım ve içeriğini konsola yazdıralım. İşlemi gerçekleştirirken elementleri HTMLCollection şeklinde listede tutalım.

```html
<div>
  <p class="paragraph">First paragraph</p>
  <p class="paragraph">Second paragraph</p>
  <p class="paragraph">Third paragraph</p>
</div>

<script>
  // getElementsByClassName() metodu HTMLCollection listesi döndürecektir.
  const paragraphs = document.getElementsByClassName("paragraph");

  // paragraphs değişkeninin içeriği HTMLCollection şeklinde konsola yazdırılacaktır.
  console.log(paragraphs);

  // İlk paragrafı konsola yazdırıyoruz.
  let firstParagraph = paragraphs[0];
  console.log(firstParagraph);

  // paragraphs değişkeninin uzunluğunu konsola yazdırıyoruz.
  console.log(paragraphs.length);
</script>
```

![a HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-04-at-9.38.09-AM.png)


**Örnek**

Aynı örneği şimdi NodeList için yapalım. İşlemi gerçekleştirirken `getElementsByClassName()` metodu yerine `querySelectorAll()` metodunu seçtiğimize dikkat edin.

```html
<div>
  <p class="paragraph">First paragraph</p>
  <p class="paragraph">Second paragraph</p>
  <p class="paragraph">Third paragraph</p>
</div>

<script>
  // querySelectorAll() metodu NodeList listesi döndürecektir.
  const paragraphs = document.querySelectorAll(".paragraph");
  console.log(paragraphs);

  // İlk paragrafı konsola yazdırıyoruz.
  let firstParagraph = paragraphs[0];
  console.log(firstParagraph);

  // paragraphs değişkeninin uzunluğunu konsola yazdırıyoruz.
  console.log(paragraphs.length);
</script>
```

![a NodeList](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-04-at-9.55.22-AM.png)


## HTMLCollection ile NodeList Arasındaki Farklılıklar

Element node'ları bir HTML elementinden (mesela `<p>`) oluşabileceği gibi attribute veya elementin içeriğinden de oluşabilir.

**❗ Bir HMTLCollection yalnızca element node'larından oluşurken NodeList diğer node türlerinden de oluşabilir.**

**Örnek**

Aşağıdaki örnekte `<div>` elementi üç tane `<p>` node'undan ve çeşitli text node'larından oluşmuş.

`<div>` içerisindeki element özellikli (`<p>`) node'ları HTMLCollection olarak listelenirler.

`<div>` elementi içerisindeki tüm node'lar (text'ler ve HTML elementleri) NodeList olarak listelenirler.

```html
<div>
  This is a text
  <p class="paragraph">First paragraph</p>
  <p class="paragraph">First paragraph</p>
</div>

<script>
  const divElement = document.querySelector("div");

  console.log(divElement.children); // HTMLCollection listesi döndürecektir.
  console.log(divElement.childNodes); // NodeList listesi döndürecektir.
</script>
```

![a collection of all types](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-04-at-10.59.18-AM.png)


### Live Collections ve Static Collections

**_live collection_** ve **_static_ collection** kavramları bir HTML dokümanın içeriğine yeni bir element ekleme, çıkarma gibi işlemler sonucunda veya güncelleme yapıldığında ne şeklide tepki vereceğini ifade eder.

live collection'lar HTML dokümanının yapısında bir değişiklik olduğunda otomatik güncellenirken static collection'lar güncellenmez.

HTMLCollection'lar live collection özelliğine sahiptir.

**Örnek**

Aşağıdaki örnekte HTML DOM tree'ye yeni bir `<p>` elementi ekleniyor. HTMLCollection otomatik güncellenecektir.

```html
<p>Paragraph One</p>
<p>Paragraph Two</p>
<p>Paragraph Three</p>

<script>
  // HTMLCollection geri döndürür.
  const paragraphs = document.getElementsByTagName("p");

  console.log("BEFORE UPDATE: ", paragraphs);

  const newParagraph = document.createElement("p");
  document.body.appendChild(newParagraph);

  console.log("AFTER UPDATE: ", paragraphs);
</script>
```

Güncelleme öncesi HTMLCollection üç tane `<p>` elementinden oluşuyordu. Yeni element eklendikten sonra HTMLCollection otomatik olarak güncellenecektir ve HTMLCollection listesi dört öğeden oluşacaktır.

![a HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-06-at-9.04.10-AM.png)


NodeList'ler genelde static collection özelliklidir fakat duruma göre live collection olarak da kullanılabilir. Bir NodeList'i static collection olarak oluşturmak için `querySelectorAll()` metodundan faydalanırız.

**💡 Bir NodeList'in live collection şeklinde oluşmasını istiyorsak `getElementByName()` metodunu kullanırız.**

**Örnek**

```html
<p>Paragraph One</p>
<p>Paragraph Two</p>
<p>Paragraph Three</p>

<script>
  // HTMLCollection geri döndürür.
  const paragraphs = document.getElementsByTagName("p");

  console.log("BEFORE UPDATE: ", paragraphs);

  const newParagraph = document.createElement("p");
  document.body.appendChild(newParagraph);

  console.log("AFTER UPDATE: ", paragraphs);
</script>
```

Güncelleme öncesi NodeList üç tane `<p>` elementinden oluşuyordu. Yeni element eklendikten sonra NodeList güncellenmeyecektir.

![a NodeList](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-06-at-9.09.42-AM.png)


### Koleksiyonlara Erişim Yöntemi

HTMLCollection listesi ile NodeList listesi içerisindeki öğelere erişim yöntemleri birbirinden farklılık gösterir.

HTMLCollection listesindeki öğelere:

- Elementin index değeri ile

- `id` attribute ile birlikte `indexItem()` metodunu birlikte kullanarak

- Herhangi bir attribute ile birlikte `indexItem()` metodunu birlikte kullanarak

**Örnek**

```html
<div id="container">
  <button
    id="btn1"
    name="first-name"
  >
    First Button
  </button>
  <button id="btn2">Second Button</button>
  <button id="btn3">Third Button</button>

  <script>
    const container = document.querySelector("#container");
    const buttons = container.children; // HTMLCollection geri döndürecektir.

    console.log(buttons[0]); // Index ile erişim yöntemi
    console.log(buttons.namedItem("btn1")); // id attribute ile erişim yöntemi
    console.log(buttons.namedItem("first-name")); // name attribute üzerinden erişim yöntemi
  </script>
</div>
```

![a HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-04-at-11.57.33-AM.png)


NodeList'deki bir elemente erişim sadece index değerini kullanarak yapılabilmektedir.

**Örnek**

```html
<div id="container">
  <button
    id="btn1"
    name="first-name"
  >
    First Button
  </button>
  <button id="btn2">Second Button</button>
  <button id="btn3">Third Button</button>

  <script>
    const container = document.querySelector("#container");
    const buttons = container.childNodes; // NodeList listesi döndürüyor.

    console.log(buttons[1]); // Index değeri ile NodeList içerisindeki ilk element konsola yazdırılır.
    console.log(buttons.namedItem("btn1")); // Hata mesajı döndürür.
    console.log(buttons.namedItem("first-name")); // Hata mesajı döndürür.
  </script>
</div>
```

![a NodeList](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-06-at-7.19.56-AM.png)


## Koleksiyonları Döngülerde Nasıl Kullanırız.

HTMLCollection'lar array veri türüne dönüştürülmediği sürece array metotları ile birlikte veya döngülerde kullanılamazlar.

Ancak NodeList'de `forEach()` metodu kullanılabilir. Diğer array metotlarını NodeList array veri türüne dönüştürülmediği sürece kullanamayız.

**Örnek**

HTMLCollection döngüde kullandığımızda hata mesajı alırız.

```html
<button class="btn">First button</button>
<button class="btn">Second button</button>
<button class="btn">Third button</button>

<script>
  // Sonuç HTMLCollection şeklinde döndürülecektir.
  const allButtons = document.getElementsByClassName("btn");

  // Hata mesajı ile karşılaşırız.
  allButtons.forEach((button) => console.log(button));
</script>
```

![an error HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-06-at-8.04.26-AM.png)


Aynı örneği NodeList için yapalım.

**Örnek**

```html
<button class="btn">First button</button>
<button class="btn">Second button</button>
<button class="btn">Third button</button>

<script>
  // Sonuç NodeList şeklinde döndürülecektir.
  const allButtons = document.querySelectorAll(".btn");

  // forEach() metodu NodeList için çalışacaktır.
  allButtons.forEach((button) => console.log(button));
</script>
```

![a HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-06-at-8.07.27-AM-1.png)


**💡 Eğer HTMLCollection'larını array veri türüne dönüştürmeden döngü içerisinde kullanmak istersek `for..of` statement'dan faydalanabiliriz.**

**Örnek**

```html
<button class="btn">First button</button>
<button class="btn">Second button</button>
<button class="btn">Third button</button>

<script>
  // Sonuç HTMLCollection şeklinde döndürülecektir.
  const allButtons = document.getElementsByClassName("btn");

  for (button of allButtons) {
    console.log(button);
  }
</script>
```

![a HTMLCollection](https://www.freecodecamp.org/news/content/images/2023/12/Screenshot-2023-12-06-at-8.07.27-AM-1.png)


## Sonuç

Eğer HTML dokümanının otomatik olarak güncellenmesini istiyorsak HTMLCollection kullanmalıyız. Şayet döküman içeriğini otomatik güncellenmesini istemiyorsak NodeList kullanmalıyız.

