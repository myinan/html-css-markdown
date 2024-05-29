# Intro to CSS
CSS(Cascading Style Sheets) is a styling language used to describe the presentation and formatting of a document written in HTML(Hypertext Markup Language) or XML(eXtensible Markup Language). ıt allows webp developers to control the visual appearance of web pages, including layout, colors, fonts, and other design elements.
CSS works by defining rules that specify how different elements in an HTML or XML document should be displayed. These rules consist of selectors and declarations. Selectors target spesific HTML elements, while declarations define the style properties and their values.

Like HTML, CSS s not a programming language; it lacks logic. CSS is a styling language.

In the previous lesson, you learned how to write the HTML that determines how a web page is structured. The next step is to make that structure look good with some style, which is exactly what CSS is for. In the next few lessons, we’re going to focus on what we believe are some foundational CSS concepts, things that everyone should know from the beginning — whether they are just starting out or simply need a refresher.

## Basic Syntax
At the most basic level, CSS is made up of various rules. These rules are made up of a selector and a semi-colon separated list of declarations, with each of those declarations being made up of a property:value pair.

A CSS rule:

![CSS Rule](../../img/css-rule.jpg "CSS Rule")

```
Note:
A <div> is one of the basic HTML elements. It is simply an empty container. In general, it is best to use other tags such as <h1> or <p> for content in your projects, but as we learn more about CSS you’ll find that there are many cases where the thing you need is just a container for other elements. Many of our exercises use plain <div>s for simplicity. Later lessons will go into much more depth about when it is appropriate to use the various HTML elements.
```

## Selectors
Selectors simply refer to the HTML elements to which CSS rules apply; they’re what is actually being “selected” for each rule. The following subsections don’t cover every selector available, but they’re by far the most common and the ones you should get comfortable using first.

### Universal Selector
The universal selector will select elements of any type, hence the name “universal”, and the syntax for it is a simple asterisk. In the example below, every element would have the color: purple; style applied to it.

```
* {
  color: purple;
}
```

### Type Selectors
A type selector (or element selector) will select all elements of the given element type, and the syntax is just the name of the element:

```
/* styles.css */

div {
  color: white;
}
```

### Class Selectors
Class selectors will select all elements with the given class, which is just an attribute you place on an HTML element. Here’s how you add a class to an HTML tag and select it in CSS:

```
<!-- index.html -->

<div class="alert-text">Please agree to our terms of service.</div>
```

```
/* styles.css */

.alert-text {
  color: red;
}
```

Note the syntax for class selectors: a period immediately followed by the case-sensitive value of the class attribute. Classes aren’t required to be specific to a particular element, so you can use the same class on as many elements as you want.

Another thing you can do with the class attribute is to add multiple classes to a single element as a space-separated list, such as class="alert-text severe-alert". Since whitespace is used to separate class names like this, you should never use spaces for multi-worded names and should use a hyphen instead.

### ID Selectors
ID selectors are similar to class selectors. They select an element with the given ID, which is another attribute you place on an HTML element:

```
<!-- index.html -->

<div id="title">My Awesome 90's Page</div>
```

```
/* styles.css */

#title {
  background-color: red;
}
```

Instead of a period, we use a hash immediately followed by the case-sensitive value of the ID attribute. A common pitfall is people overusing the ID attribute when they don’t necessarily need to, and when classes will suffice. While there are cases where using an ID makes sense or is needed, such as taking advantage of specificity or having links redirect to a section on the current page, you should use IDs sparingly (if at all).

The major difference between classes and IDs is that an element can only have one ID. An ID cannot be repeated on a single page, and the ID attribute should not contain any whitespace at all.

### The Grouping Selector
What if we have two groups of elements that share some of their style declarations?

```
.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: black;
  /* several unique declarations */
}
```

Both our .read and .unread selectors share the color: white; and background-color: black; declarations, but otherwise have several of their own unique declarations. To cut down on the repetition, we can group these two selectors together as a comma-separated list:

```
.read,
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

Both of the examples above (with and without grouping) will have the same result, but the second example reduces the repetition of declarations and makes it easier to edit either the color or background-color for both classes at once.

### Chaining Selectors
Another way to use selectors is to chain them as a list without any separation.
Let’s say we had the following HTML:

```
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

We have two elements with the subsection class that have some sort of unique styles, but what if we only want to apply a separate rule to the element that also has header as a second class? Well, we could chain both the class selectors together in our CSS like so:

```
.subsection.header {
  color: red;
}
```

What .subsection.header does is it selects any element that has both the subsection and header classes. Notice how there isn’t any space between the .subsection and .header class selectors. This syntax basically works for chaining any combination of selectors, except for chaining more than one type selector.

This can also be used to chain a class and an ID, as shown below:

```
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection" id="preview">
    This is where a preview for a post might go.
  </p>
</div>
```

You can take the two elements above and combine them with the following:

```
.subsection.header {
  color: red;
}

.subsection#preview {
  color: blue;
}
```

In general, you can’t chain more than one type selector since an element can’t be two different types at once. For example, chaining two type selectors like div and p would give us the selector divp, which wouldn’t work since the selector would try to find a literal \<divp> element, which doesn’t exist.

### Descendant Combinator
Combinators allow us to combine multiple selectors differently than either grouping or chaining them, as they show a relationship between the selectors. There are four types of combinators in total, but for right now we’re going to only show you the descendant combinator, which is represented in CSS by a single space between selectors. A descendant combinator will only cause elements that match the last selector to be selected if they also have an ancestor (parent, grandparent, etc) that matches the previous selector.

So something like .ancestor .child would select an element with the class child if it has an ancestor with the class ancestor. Another way to think of it is child will only be selected if it is nested inside of ancestor, no matter how deep. 

```
<!-- index.html -->

<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"></div>
<!-- D -->
```

```
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```

In the above example, the first two elements with the contents class (B and C) would be selected, but that last element (D) wouldn’t be. 

There’s really no limit to how many combinators you can add to a rule, so .one .two .three .four would be totally valid. This would just select an element that has a class of four if it has an ancestor with a class of three, and if that ancestor has its own ancestor with a class of two, and so on. You generally want to avoid trying to select elements that need this level of nesting, though, as it can get pretty confusing and long, and it can cause issues when it comes to specificity.

## Declarations
Declarations are used to define the style properties and their values in key-value pairs. Each declaration consists of a property and a value seperated by a colon. Multiple declarations are seperated by semicolons. For example:

color: blue;

font-size: 16px;

### Property and Value
CSS provides a wide range of properties that control various aspects of an element's appearance.
Some common properties include:
+ 'color': Sets the text color.
+ 'font-size': Sets the size of the font.
+ 'background-color': Sets the background color of an element.
+ 'margin', 'padding': Sets the spacing around an element.
+ 'border': Sets the border properties.

## Cascading
CSS follows the cascading principle, which means that multiple style rules can apply to an element, and the final style is determined by a combination of factors, including specificity, inheritance, and order of appearance. Styles defined closer to the target element take precedence.

In the context of Cascading Style Sheets (CSS), the "cascading principle" refers to the set of rules that determine how styles are applied and resolved when multiple style declarations target the same element. CSS follows a cascading order, which means that styles can be inherited, overridden, or combined in a specific sequence to determine the final appearance of elements on a web page.

The cascading principle in CSS consists of three main components: specificity, inheritance, and the order of appearance.

1. **Specificity**: Specificity is a measure of how specific a style declaration is in targeting an element. It determines which styles take precedence when multiple rules target the same element. CSS assigns a specificity value to each selector based on its components, such as element type, class, ID, and inline styles. The more specific a selector, the higher its specificity value. When conflicting styles apply to an element, the rule with the higher specificity takes precedence.

    The order of specificity rules in CSS, listed in descending order of specificity:

    1.1. Inline styles: Inline styles have the highest specificity. They are defined directly within the HTML element using the `style` attribute ( Specificity: 1,0,0,0).

    1.2. IDs: Selectors with IDs have the second highest specificity. They are defined using the `#` symbol followed by the ID name ( Specificity: 0,1,0,0).

    1.3. Classes, attributes, and pseudo-classes: Selectors with classes, attributes, or pseudo-classes have the third highest specificity. They are defined using the `.` symbol for classes, `[attribute]` for attributes, or `:pseudo-class` for pseudo-classes ( Specificity: 0,0,1,0).

    1.4. Elements and pseudo-elements: Selectors with elements and pseudo-elements have the lowest specificity. They are defined using the element name (e.g., `div`, `p`, `h1`) or the `::pseudo-element` notation for pseudo-elements ( Specificity: 0,0,0,1).

    Note: The universal selector (`*`) has no specificity value (0,0,0,0).<br>
    Note: The `!important` value appended a CSS property value overrides even inline styles from the markup. The only way an !important value can be overridden is with another !important rule declared later in the CSS and with equal or great specificity value otherwise.


2. **Inheritance**: In CSS, certain properties are inherited by child elements from their parent elements. When a parent element has a specific style applied, its child elements will also inherit those styles unless explicitly overridden. For example, if you set a font color on the `body` element, the text color of all the child elements within the `body` will inherit that color unless a different color is specified for those child elements.

   However, not all properties are inherited. Some properties, such as border or padding, do not propagate to child elements by default. Each CSS property has its own inheritance behavior, which is specified in the CSS standard.

3. **Order of Appearance**: When multiple conflicting styles are applied to the same element and have the same specificity, the order in which they appear in the CSS file matters. The styles that appear later in the file will override the earlier styles. This principle allows for the flexibility of overriding or modifying styles applied earlier in the stylesheet.

The cascading principle enables developers to control the visual presentation of web content effectively. By leveraging specificity, inheritance, and the order of appearance, CSS allows for fine-grained control over the styles applied to elements, ensuring consistency and flexibility in designing web pages.

## Properties to Get Started With

### Color and Background-Color
The color property sets an element’s text color, while background-color sets the background color of an element.

Both of these properties can accept one of several kinds of values. A common one is a keyword, such as an actual color name like "red" or the "transparent" keyword. They also accept HEX, RGB, and HSL values.

### Typography Basics and Text-Align
<b>font-family</b> can be a single value or a comma-separated list of values that determine what font an element uses. Each font will fall into one of two categories, either a “font family name” like "Times New Roman" (we use quotes due to the whitespace between words) or a “generic family name” like sans-serif (generic family names never use quotes).

If a browser cannot find or does not support the first font in a list, it will use the next one, then the next one and so on until it finds a supported and valid font. This is why it’s best practice to include a list of values for this property, starting with the font you want to be used most and ending with a generic font family as a fallback, e.g. font-family: "Times New Roman", sans-serif;

<b>font-size</b> will, as the property name suggests, set the size of the font. When giving a value to this property, the value should not contain any whitespace, e.g. font-size: 22px has no space between “22” and “px”.

<b>font-weight</b> affects the boldness of text, assuming the font supports the specified weight. This value can be a keyword, e.g. font-weight: bold, or a number between 1 and 1000, e.g. font-weight: 700 (the equivalent of bold). Usually, the numeric values will be in increments of 100 up to 900, though this will depend on the font.

<b>text-align</b> will align text horizontally within an element, and you can use the common keywords you may have come across in word processors as the value for this property, e.g. text-align: center.

### Image Height and Width
Images aren’t the only elements that we can adjust the height and width on, but we want to focus on them specifically in this case.

By default, an \<img> element’s height and width values will be the same as the actual image file’s height and width. If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the height property and adjust the width value:

```
img {
  height: auto;
  width: 500px;
}
```

For example, if an image’s original size was 500px height and 1000px width, using the above CSS would result in a height of 250px.

It’s best to include both of these properties for <img> elements, even if you don’t plan on adjusting the values from the image file’s original ones. When these values aren’t included, if an image takes longer to load than the rest of the page contents, the image won’t take up any space on the page at first, but will suddenly cause a drastic shift of the other page contents once it does load in. Explicitly stating a height and width prevents this from happening, as space will be “reserved” on the page and will just appear as a blank space until the image loads.

## Adding CSS to HTML
CSS can be applied in different ways:
+ <ins>Inline CSS:</ins> Styles are directly added to individual HTML elements, using the "style" attribute.
+ <ins>Internal CSS:</ins> Styles are defined within the \<style> tag in the `<head>` section of an HTML element.
+ <ins>External CSS:</ins> Styles are defined in a seperate CSS file and linked to the HTML document, using the \<link> tag.

---

Assignment "odin-css-exercises-fork -) foundations -) 1 to 5" completed, committed and pushed to github repository.

---

### Knowledge Check

**Q1.** What is the syntax for class and ID selectors?

**A1.** We use "." for class selectors. Example: .css-class { ... }
For ID selectors we use "#". Example: #id-select { ... }

**Q2.** How would you apply a single rule to two different selectors?

**A2.** In order to apply a single rule to two different selectors, we can group selectors. Example:
```
.class-first,
.class-second {
  background-color: black;
  color: white;
}
```

**Q3.** Given an element that has an id of title and a class of primary, how would you use both attributes for a single rule?

**A3.** In order to accomplish this, we can chain selectors. Example:
```
 #title.primary {
  ... some css declarations here..
 }
```

**Q4.** What does the descendant combinator do?

**A4.** Descendant combinator is used to apply css rules to an element which is a descendant of an another element. Example:
```
ul li {
  text-align: center;
}
```
OR

```
.parent .child {
  background-color: yellow;
}
```

**Q5.** What are the names of the three ways to add CSS to HTML?

**A5.** 
+ External CSS
+ Internal CSS
+ Inline CSS

**Q6.** What are the main differences between the three ways of adding CSS to HTML?

**A6.** 
+ External CSS: CSS rules applied to the HTML page are contained in a different file. This is the recommend way of applying CSS to HTML. This way we can avoid bloating the HTML page and keep HTML and CSS seperately. Keeping HTML and CSS seperately also makes it possible to apply the same CSS rules to different HTML pages. To link a seperate "style.css" file to our HTML page we use "\<link rel="stylesheet" href="./path/style.css">".

+ Internal CSS: We declare our CSS rules inside of our HTML page's \<head> tag, further inside the \<style> tag.

+ Inline CSS: We apply CSS directly to the HTML element using the "style" attribute. This type of CSS rules has the most specificity and can be used to overwrite other CSS rules applied to the element. Inline CSS is not recommended since this way our HTML page can quickly become bloated and keeping track of all the CSS rules applied to each element becomes much harder.














