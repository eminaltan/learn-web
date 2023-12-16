# BEFORE YOU START

This guide supposed you known basic terms of CSS. (Like **_rule set, selectors, declarations, rules, property and property of values._**)

Sometimes two or more rule sets wants to style one element in the CSS. When it happens rule sets will be conflict and in this situation only one rule set apply on the element.

Firstly CSS will solve the conflict then will be style the element. The CSS have some mechanisms while resolve to conflict.

These mechanisms split 3 main categories. These are listed below;

1. Cascade,

2. Specificity,

3. Inheritance

**In this chapter we'll discuss _*cascade*_ mechanism.**

Let's little bit dive in...

## CASCADE MECHANISM ON CSS

If two rule sets have **same weights [^1]** last rule set will apply on the element and other rule set not. This mechanism is called **_cascade_**.

**Example**

```css
p {
  color: orange;
}

p {
  color: purple;
}
```

In above example, two rule sets wants to style `<p>` element but which rule set will apply on element? In this situation **_cascade_** come to help us for resolve to conflict. According to **_cascade_** mechanism last selector rule set will apply on element so, color of `<p>` element will be `purple` in this situation.

💡 Tip: Keep in mind in the **_cascade_** mechanism always closest rules of `</body>` tag will apply to the element.

Think of we have three styles and these styles wants to change font size of `<p>` element. Let's say one of three styles become external style sheet and linked to our document with `<link>` element. Suppose this is rule set called as `p.external`, another one rule set used between in `<style>` element this is called as `p.element-style` and lastly one rules will apply inline style with `style` tag like a `<p style="font-size:26px">`.

Which rule set will apply to the `<p>` element? Certainly inline styles will apply to the element.

**Example**

```css
/* External from external.css file */

p.external {
  font-size: 18px;
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
    class="external element-style "
  >
    Element of <code>font-size</code> value will be 26px. Because this is lastly
    defined and higher specificity (Weight) than others. Remember
    <strong>cascade</strong> mechanism always closest rules of &#60;body&#62;
    tag will apply to element.
  </p>
</body>
```

While removed inline style in `<p>` element which one style will apply to the element?

**[Let's you try with this link.]**[1]

Same rules also applies to CSS declarations. (`property: value` combination) If two declarations wants to style one element last declarations wins out in normal circumstances.

Let's say we have two declarations in one selector. One of them become shorthand property a like `font` and another more specific property like a `font-weight` which property will be use?

⚠️ Generally developers uses shorthand properties as a fallback mechanisms. So, if you want to use shorthand properties to be ensure before declarations of values included from shorthand version.

**Example**

```css
.example {
  font-size: 20px;

  font-weight: light;

  /* If remove to bold value of font-weight property font weight of document will be reset and return to initial value of user agent style. So, upper font-weight declaration won't apply. */
  font: small-caps bold 40px Arial, Helvetica, sans-serif;
}
```

### `!important` Keyword Usage

When two rule set conflict then if which declaration property has a `!important` KW it's applies to the element even though defined firstly.

❗ We'll mention **why must less use `!important` keyword** when define declarations.

[Let's back to the example and try this][2]

```css
/* External from external.css file */

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
    specificity (We'll examine in chapter two) values to selector.
  </p>
</body>
```

### Importance of Rules and Origins

#### Importance of Rules

Not all properties are the same. So, some properties most important than others. These are listed below from least important to most important:

1. Regular properties like a `background`, `font-weight`, `line-height`.

2. `animation` property type.

3. `!important` keyword rules.

4. `transition` property type.

#### Importance of Origins

CSS styles split by origins below. These are sorted by importance low to high.

1. User Agent Styles: AKA browser defined styles. If user or author won't define styles on element the user agent base styles applies to the element as a default. Each browser has a own user agent styles. So, user agent style maybe appear differently to each other.

2. User Based Styles: These styles defined in operation system level like a font-size styles. Also some browser extension affect these styles.

3. Author Based CSS styles: These styles defined by developers like a above examples.

4. Author `!important` Based CSS styles: If you're use `!important` KW in styles this style defined as Author `!important` Based CSS styles.

5. User `!important` Based Styles: If an element defined with `!important` KW in operation system level called as User `!important` Based Styles.

6. User Agent `!important` Styles: Any `!important` KW defined in the User Agent Styles.

These origin illustrated below

![Sort of origin styles](https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/zPdaZ6G11oYrgJ78EfF7.svg "Sort of origin styles")

In the next chapter we'll discuss term of **_specificity_**

[^1]: Weight: Weight of selector or rule set. Think of kilos.

[1]: https://codepen.io/eminaltan/pen/xxmzOMq
[2]: https://codepen.io/eminaltan/pen/rNoKGjr
