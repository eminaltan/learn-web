## SPECIFICITY MECHANISM IN CSS

Before the start may be you're wants to quick glance of **_cascade_** mechanism therefore **[I put a link here][1]**.

### What's the Mean Specificity

Let's define what's the mean of **_specificity_**. **[According to the Mozilla][2]** specificity become that mean.

Specificity is the algorithm used by browsers to determine the CSS declaration that is the most relevant to an element, which in turn, determines the property value to apply to the element.

### Why Need Specificity and Where to Use?

1. Sometimes we're wants to apply determined rule set on HTML element(s) and others not with specificity mechanism we can do this. (Do you wonder "how does work of specificity?" you find more about in
   **[Calculation of Specificity](#calculation-of-specificity)** section.)

2. Sometimes two rule set conflict in this case we can use resolve to conflict use with this mechanism. Let's examine each scenario.

Let' say **when same weight[^1]** two rule sets conflict then styles of last rule set applies to the element in the normal circumstances. (Remember this mechanism called as **_cascade_**)

**So, What does if two rule set haven't same weight? How to resolve this conflict between them? Here is _*specificity*_ mechanism come to help us.**

**Example**

```css
p.success {
  color: green;
}

p {
  color: orange;
}
```

Which rule set win? Maybe you're suppose last rule set will be win. But not. Even though this rule set defined at last. So, why? **Because each selector type has a specificity value.** In normal circumstances specificity values will be change game of rules in the CSS.

### Specificity Types and Specificity Calculation

CSS specificity types splits four main categories. These are listed below picture. While right direction is imply to lower specificity left direction is imply to higher specificity.

![Image of CSS specificity](https://i.ibb.co/tK2jYKM/CSS-specificity.png "Image of CSS specificity")

Let's take a look each of them and examine to each group.

#### Element and Pseudo Element Selector Specificities

Both of them have 1 specificity point. **So, each element selector or pseudo-element selector will add total weight of rule set 1 point.**

**Example**

```css
/* Weight of rule set has consist 1 point*/
p {
  color: green;
}

/* Weight of rule set has consist 2 points*/
p:first-letter {
  color: orange;
}

/* Weight of rule set has consist 3 points*/
p ul a {
  color: red;
}

/* Weight of rule set has consist 4 points*/
p ul a:last-child {
  color: blue;
}
```

#### Class, Pseudo Class and Attribute Selector Specificities

All of them have 10 specificity points. **So, each class selector, pseudo-class selector or attribute selector will add total weight of rule set 10 points.**

**Example**

```css
/* Weight of rule set has consist 10 point*/
.success {
  font-size: 18px;
}

/* Weight of rule set has consist 20 points*/
.success:hover {
  font-size: 20px;
}

/* Weight of rule set has consist 30 points*/
.success .cool:hover {
  font-size: 18px;
  color: lightblue;
  border-radius: 1px;
}

/* Weight of rule set has consist 40 points*/
.success .cool .rounded[target] {
  font-size: 18px;
  color: lightblue;
  border-radius: 2px;
}
```

#### ID Selector Specificity

ID selector has 100 specificity point in the CSS. **So, ID selector will add the total weight of rule set 100 points.**

⚠️ A HTML element consist only one ID selector. So below example usage not appropriate.

```html
<p id="my-selector another-selector">A HTML element</p>
```

⚠️ Unlike class selector, ID selector can't use together for chaining method.

**Example**

```css
/* Weight of rule set has consist 100 points */
#my-selector {
  color: lightblue;
  border-radius: 2px;
}

/* Class selectors can use with chaining method */
.class1.class2.class3 {
  color: orange;
}

/* But ID selectors can't */
#first#second {
  color: orange;
}
```

#### Inline Specificity

If embedded CSS style(s) with `style` attribute on the element in this situation specificity point will be 1000 points.

**Example**

```html
<style>
  p.element-style {
    font-size: 22px;
  }
</style>

<body>
  <p
    style="font-size:26px;"
    class="element-style"
  >
    Element of <code>font-size</code> value will be 26px. Because this weight of
    <code>font-size</code> element has 1000 points.
  </p>
</body>
```

#### Calculation of Specificity

Above overall information let's examine how to works specificity calculation? Each selector specificity value will be add total weight of rule set. That's it. It's simple.

If we're explain each selector type count like `y`, each selector weight like `z` and total weight of rule set value like `result` this formula look like this;

`result=(yxz)+(yxz)+(yxz)...n`

⚠️ Universal selectors (`*`), combinator selectors can't increase specificity value. Also the `:not()` pseudo-class itself adds nothing to the specificity calculation. However, the selectors passed in as arguments do get added to the specificity calculation.

**Example**

```css
/* (1x100) + (1x10) + (1x1) = 111 */
#my-id .first-class p {
  color: red;
}

/* (1x100) + (2x10) + (1x1) = 121 */
#my-id .first-class .second-class p {
  color: blue;
}

/* (1x100) + (2x10) + (2x1) = 122 */
#my-id .first-class .second-class p::first-letter {
  color: orange;
}

/* (1x100) + (2x10) + (2x1) = 122 */
#my-id .first-class .second-class p::first-letter {
  color: orange;
}

/* (1x10) = 10 * selector can't add total weight */
.second-class: * {
  color: purple;
}

/* (1x10) + (1x1) = 11 * :not pseudo-class can't add total weight */
.second-class:not(div) {
  color: maroon;
}
```

💡 Use specificity mechanism as much as need. Because more specification also brings to complexity. So, when two or more rule conflicts in this case we have difficulty to resolve problem. In this situation may be use `!important` KW. but my opinion can't do that. I prefer to use **[BEM mechanism][3]**.

### Consideration of !important` KW usage

The `!important` KW[^2] add to 10.0000 points to the rule set. So this KW will be increase specificity of rule set. **if a declaration defined with `!important` KW in this situation styles can't override. Even though element styles defined as inline.**

[Let's back to the previous chapter example and try to `!important` KW what ever you want then observe the changes.][4]

```css
/* External.css file */
p.external {
  font-size: 18px !important;
}
```

```html
<link
  rel="stylesheet"
  href="external.css"
/>

<style>
  p.element-style {
    font-size: 22px;
  }
</style>

<body>
  <p
    style="font-size:26px;"
    class="element-style"
  >
    Element of <code>font-size</code> value will be 18px. Because
    <code>!important</code> keyword used and this KW added 10.000 points of
    specificity.
  </p>
</body>
```

⚠️ When two rule set conflicted some developers maybe use to apply to dedicated style(s) on the element with `!important` KW. But remember if you can this you will also increase specificity of rule set. So, whenever you wants to change styles of element with another rule set you can't. Because `!important` KW in the game.

I prefer to use selectors when want to change specificity of the rule set. Therefore specificity values gradually increases.

Let'say we have two rule set and we wants to change color of `<p>` element.In this case we're add more selectors to increase of specificity. So, if we wants to apply color of orange add selector of `<p>` element.

**Example**

```css
/* Normal circumstances */

/* (1x1)= 1 */
p {
  color: orange;
}

/* (1x10) + (1x1)= 11 */
p.rule-set1 {
  color: red;
}

/* <p> element color will be orange because we're added more selectors */

/* (2x10) + (1x1)= 21 */
p.rule-set1[title] {
  color: orange;
}

/* (1x10) + (1x1)= 11 */
p.rule-set1 {
  color: red;
}
```

In the next chapter we'll discuss term of **_inheritance_**
[^1]: Weight: Weight of selector or rule set. Think of kilos.
[^2]: Term of keyword

[1]: https://gist.github.com/eminaltan/eaafae25487ab44bd76aa718cd8162eb#before-you-start
[2]: https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity
[3]: https://getbem.com/
[4]: https://codepen.io/eminaltan/pen/rNoKGjr
