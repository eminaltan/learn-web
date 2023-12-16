## INHERITANCE MECHANISM IN CSS

Before the start I suggest to understand term of parent-child relation in SW development. May be you're want to quick glance for **_cascade_** mechanism therefore **[I put a link here][1]**. Also you find more information about **_specificity_** mechanism **[in this link][2]**

### What's the Means Inheritance

Let's define what's the means of **_inheritance_**. To understand this mechanism we're use a metaphor like a dog and dog's puppy relationship.

**Think of like a dog as black color, red eyes (A space dog 🙂) and big head. The puppy inherited some features from parents like eyes and color. But some feature(s) can't inherited from parents like a head. In the CSS _*inheritance*_ mechanism similarly works. We're determine which properties will be inherit from parent HTML element or which are not. That's it simple!**

### Inheritance Types

CSS styles will be inherit from parent HTML element with two methods. These methods are named as implicitly and explicitly Let's examine them.

⚠️ In the normal circumstances **_inheritance_** mechanism works downward direction **except `<body>` element. So, `<html>` element styles will be inherit from `<body>` element.** Meanwhile when we'll style to `<body>` element we'll also style to the HTML document. So **_inheritance_** mechanism will work upward direction between two elements.

**Example**

```html
<html lang="en">
  <style>
    body {
      /* Background color of <html> element will be orange */
      background-color: orange;
    }
  </style>

  <body>
    <p>Lorem ipsum dolor sit amet.</p>
  </body>
</html>
```

#### Implicitly Inheritance

As you know each HTML elements has parent-child or ancestor-descendant relationship. Therefore a child element will inherit CSS styles from closest parent element in the normal circumstances. This behavior named as **_implicitly inheritance_** mechanism.

**Example**

```html
<style>
  .parent {
    color: red;
  }
</style>

<body>
  <div class="parent">
    This is parent element and color is red.
    <p>This is a child element and color red too.</p>
  </div>
</body>
```

As you can see above to example **_implicitly inheritance_** shows effect on the `<p>` element.

But while some CSS properties will be inherit from parent element some CSS properties aren't. So, which CSS properties inheritable and which aren't? Each property hold this information in specification table. If you wonder one property inheritable or not you can check property specification table on the internet. (Like a [MDN][3]).

Let's look at an example for `width` property is inheritable or not.

![width property table](https://i.ibb.co/PhZf7Rg/Screenshot-from-2023-10-04-15-25-28.png)

Above the picture you can see **_inherited_** section in table. The value of "Inherited" section holds **_no_** information. So, implicitly inheritance mechanism can't work for `width` property. But sometimes we can do that by force.

❗ If a property not inheritable from parent element in this situation value of user agent style sheet [^2] will be use for this property.

#### Explicitly Inheritance

Sometimes we're want to inherit some properties from parent element but these properties can't derive with implicitly inheritance mechanism. (Remember to `width` property inheritance.) In this situation we can do that by force with some CSS keywords. This situation named as **_explicitly inheritance_** mechanism.

For use **_explicitly inheritance_** mechanism here is I'm listed some KW[^1] below.

###### `inherit` Keyword

If you want to inherit particular value of property from the parent, you can use `inherit` KW.

**Example**

```html
<style>
  * {
    margin: 0;
    padding: 0;
  }

  .parent {
    border: 1px solid red;
    padding: 20px;
  }

  .child {
    border: 1px solid;
    padding: inherit;
  }
</style>

<body>
  <div class="parent">
    This is a parent element and value of padding property will be 20px.
    <p class="child">
      This is a child element and computed value of padding property will
      inherit from parent elemenr. So, padding property value of child element
      will be 20px too.
    </p>
  </div>
</body>
```

❗ What does mean **_computed_** value? Let's discuss above example. Supposedly we're redefine `padding` property with `%` unit then define `width` property for the parent element. In this situation padding value of child element will be relate `width` property value of parent element. (**[According to MDN][4]** `padding` property takes reference width of the parent element.)

**Example**

```html
<style>
  * {
    margin: 0;
    padding: 0;
  }

  .parent {
    border: 1px solid red;
    padding: 10%;
    width: 300px;
  }

  .child {
    border: 1px solid;

    /* Value of padding property consist of 30px because computed value inherited from parent element (300x10% = 30px), not inherited 10 numeric value or 10% relative unit from the parent element. So, whenever change to width of the parent element also padding property value of child element will be change. */
    padding: inherit;
  }
</style>

<body>
  <div class="parent">
    This is a parent element and padding property value of element relates to
    browser width. Because parent of div element consist of browser window when
    use percentage unit for padding property then computed value of padding
    property takes reference width value of the parent element.
    <p class="child">
      This is a child element. Computed value of padding property will be
      inherit from parent element. So, child element padding value will be 30px.
    </p>
  </div>
</body>
```

###### `initial` Keyword

As the name suggests `initial` KW will return initial value of property. So, sometimes we don't want to inherit property value of parent element to child element. For a child element we want to return initial value of property. In this case `initial` KW come to help us.

**Example**

```html
<style>
  .parent {
    color: red;
    font-size: 25px;
  }

  .child {
    color: initial;
  }
</style>

<body>
  <div class="parent">
    This is a parent element and value of color property will be red.
    <p class="child">
      This is a child element and value of color property will return to initial
      value.
    </p>
  </div>
</body>
```

❗ In the normal circumstances `initial` KW returns to default value of property in CSS specification. **If value of property not defined in CSS specification then value of property returns to the user agent style sheet.**

**Example**

```html
<style>
  .parent {
    font-size: 25px;

    /* Remove the display property and observe the changes.*/
    display: initial;
    color: orange;
  }
</style>
<body>
  <body>
    <div class="parent">
      This is a div element. Generally div element defined as block level in
      user agent style sheet. For this element when we're define display:initial
      declaration then value of display property will returns to CSS
      specification. In this case value returns to inline. So, div element show
      us to an inline element.
    </div>
    <span>span element</span>
  </body>
</body>
```

###### `unset` Keyword

The `unset` KW has two functions these are listed below;

- If value of property inheritable in this case `unset` KW work like as `inherit`

**Example**

```html
<style>
  .parent {
    color: blue;
  }

  .child {
    color: unset;
  }
</style>
<body>
  <body>
    <div class="parent">
      This is a parent element and color will be blue.
      <p class="child">This is a child element and color will be blue too.</p>
    </div>
  </body>
</body>
```

- If value of property can't inheritable from parent element (`display` property e.g.) in this case `unset` KW work like as `initial` KW. So, value of property returns to CSS specification. If property value not defined in CSS specification in this situation value of property returns to user agent style sheet. (Like as works `revert` KW)

**Example**

```html
<style>
  .parent {
    display: block;
    color: rgb(196, 5, 5);
  }

  .child {
    /* unset KW will work like as initial. Remove the display:unset declaration then observe the changes. */
    display: unset;
    color: initial;
    margin-top: 20px;
  }
</style>

<body>
  <span class="parent"
    >This is a parent element. In the normal circumstances value of display
    property defined as inline level for the span element. But display:block
    declaration will change this behavior. So span element will be made of block
    level element. Also display property can't inheritable.

    <div class="child">
      This is a child element. In the normal circumstances value of display
      property defined as block level for the div element. But unset Kw returns
      to value in CSS specification. So, display property defined as inline in
      the CSS specification. Eventually this element will be made of inline
      element.
    </div>
  </span>
</body>
```

###### `currentColor` Keyword

Sometimes we'll defines `border` property for an element and we want to derive color of border from color of element. In this case `currentColor` KW come to help us. So, If we want to use color value of element with other properties like a `border-color`, we're use `currentColor` KW.

**Example**

```html
<style>
  .parent {
    color: blue;
  }

  .child {
    padding: 20px;

    /* 
      color of .child selector inherited from .parent selector. So, color of .class selector will blue and border color will be blue too. 
      Because color of border and element of color shares same value.
    
      Remove to currentColor KW then see changes. 
    */
    border: 2px solid currentColor;
  }
</style>

<body>
  <div class="parent">
    This is a parent element and color will be blue
    <p class="child">
      This is a child element and color of border property will blue too.
    </p>
  </div>
</body>
```

##### Color of System Keywords

We can also use system colors for an element in the user agent style sheet. I think if we're define colors for some properties with this method and when we'll change to web page color scheme (Like as light or dark) then color of elements automatically adapts to the theme.

So, no longer needed use custom properties or not required to define for each element light or dark theme colors. User agent stylesheet will do automatically for us.

If consider accessibility especially useful for this method.

⚠️ But don't forget each browser has own user agent style sheet. So, a page may appear different color scheme each browser. But you can redefine colors what do you want.

But we can use individually color of system keywords.

**Example**

```html
<style>
  .parent {
    color: linkText;
  }
</style>

<body>
  <div class="parent">
    Parent element color takes from linkText system keyword. So, color of p
    element like a HTML link color.
  </div>
</body>
```

##### `all` Property Usage

Sometimes we want to use any keywords for all properties. In this situation `all` property come to help us.

**Example**

```html
<style>
  .parent {
    color: blue;
  }

  .child {
    font-size: 20px;
  }

  .descendant {
    /* Remove to all property and observe the changes. */
    all: initial;
  }
</style>

<body>
  <div class="parent">
    This is a parent element and color of element will be blue.
    <div class="child">
      This is a child element and color of element inherited from parent
      element. Color of element will be blue and font-size will be 20px
      <div class="descendant">
        This is a descendant element all value of properties returns to the
        initial value.
      </div>
    </div>
  </div>
</body>
```

⚠️ `all` property can't work for `unicode-bidi` and `direction` properties.

### Conclusion

I think with **_inheritance_** mechanism when writes to code blocks we can spend less time for this operation. But should be use carefully **_inheritance_** mechanism because if we're use careless maybe we can have some cascade problems.

- If a property not inheritable from parent element in this situation value of user agent style sheet will use for this property.

- In the normal circumstances while some properties are inheritable some properties aren't. For not inheritable properties we can use explicitly Inheritance mechanism.

- **_Inheritance_** mechanism works downward except `<html>` and `<body>` elements. So, between these elements **_inheritance_** mechanism works upward.

- For a property `initial` KW returns to default value of CSS specification. If property value not defined in CSS specification in this case value of property returns to the user agent style sheet. (Like as works `revert` KW)

- When want to use color value of element with other color based properties (Like as `border-color`) the `currentColor` KW come to help us.

- We can use `all` property in inheritance mechanism. Especially useful to return determined value for some properties at the same time.

[^1]: KW: Abbreviation of keyword.
[^2]: Pre-defined set of CSS rules that are built into a web browser and applied to web pages automatically.

[1]: https://gist.github.com/eminaltan/eaafae25487ab44bd76aa718cd8162eb#before-you-start
[2]: https://gist.github.com/eminaltan/eaafae25487ab44bd76aa718cd8162eb#specificity-mechanism-in-css
[3]: https://developer.mozilla.org/en-US/
[4]: https://developer.mozilla.org/en-US/docs/Web/CSS/padding
