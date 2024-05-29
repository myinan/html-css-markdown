# CSS Functions
Similar to programming languages, functions in CSS are reusable pieces of code which perform specific tasks. Functions are passed “arguments” between parentheses, each of which is used by the function in a specific way. Some common examples are:

```css
color: rgb(0, 42, 255);
background: linear-gradient(90deg, blue, red);
```

Unlike programming languages you’ll use in The Odin Project, CSS does not allow us to create our own functions. Instead, the language comes bundled with a list of premade functions that will help you solve the most common styling problems.

Let’s go over a few of these functions:

## Mathematical CSS Functions

### 1.calc():
- The `calc()` function is a versatile tool for performing mathematical calculations within CSS property values.
- It can be used in any CSS property that accepts numeric values, such as widths, heights, margins, paddings, and more.
- The `calc()` function allows you to combine values with mathematical operators (+, -, *, /) to create dynamic styles based on the result of the calculation.
- It provides a way to mix different units of measurement, like pixels, percentages, ems, and more, in a single expression.

**Example 1: Using calc() for width calculation**
```css
.box {
    width: calc(50% - 20px);
}
```
In this example, the `.box` element's width will be set to 50% of its parent's width minus 20 pixels.

**Example 2: Using calc() for font size adjustment**
```css
p {
    font-size: calc(16px + 2vw);
}
```
Here, the font size of `<p>` elements will be calculated as 16 pixels plus 2% of the viewport width (vw).

### 2.min():
- The `min()` function allows you to set a CSS property to the minimum value among multiple values.
- It's particularly useful when you want to ensure that an element's property, like width or height, doesn't exceed a certain limit.

**Example using min():**
```css
.container {
    width: min(300px, 100%);
}
```
In this example, the `.container` element's width will be set to the minimum value between 300 pixels and 100% of its parent's width.

### 3.max():

- Conversely, the `max()` function sets a CSS property to the maximum value among multiple values.
- It's useful when you want to ensure that an element's property doesn't go below a certain threshold.

**Example using max():**
```css
h1 {
    font-size: max(24px, 5vw);
}
```
Here, the font size of `<h1>` elements will be set to the maximum value between 24 pixels and 5% of the viewport width (vw).

### 4.clamp():

- The `clamp()` function is a combination of `min()`, `max()`, and a fixed value.
- It takes three arguments: a minimum value, a preferred value, and a maximum value. It returns the preferred value if it falls within the range of the minimum and maximum values; otherwise, it clamps the value to the closest boundary.

**Example using clamp() for responsive font size:**
```css
p {
    font-size: clamp(16px, 4vw, 24px);
}
```
In this example, the font size of `<p>` elements will be responsive, ranging from a minimum of 16 pixels to a maximum of 24 pixels, with a preferred size of 4% of the viewport width (vw).

---

### # You can use calc() when you want an element to take up the most of the viewport height except the height of an another element:
For example, you may want something to take up most of the viewport height except the height of the navigation. For this purpose, you can mix units to pass a relative vh (view height) unit with an absolute pixel unit:

```css
.content {
  height: calc(100vh - 60px);
}
```

As the viewport resizes or a user visits on larger or smaller devices, the value of 100vh will dynamically update, and therefore so will the calculation.

### # You can use min() instead of declaring padding on an element:
The min() function allows nested basic math operations, which means we can flip to subtracting some space as a swap for defining left and right padding, as follows:

```css
.container {
  width: min(80ch, 100vw - 2rem);
}
```

On larger viewports, the element can grow to a max of 80ch, and once the viewport shrinks below that width, it will be allowed to grow to 100vw - 2rem. This definition effectively produces 1rem of "padding" on either side of the element.

In this example, you could also swap to 100% instead of vw to make the element width responsive within a parent container.

### # You can use min() to determine a maximum allowed background-size:
CSS math functions can be used in most properties that allow a numeric value. One unique place to use them is within background-size.

Why? Perhaps you're supplying a layered effect of a background color and an image. And rather than using the cover size value, which would make the image fill the space, you would like to cap the growth of the image. This is a perfect place to bring in min().

Consider an example where min() is used to ensure the image doesn't exceed 600px while being allowed to respond down with the element by also setting 100%. In other words, it will grow up to 600px and then resize itself down to match the element's width when it is less than 600px.

```css
.background-image {
  background: #1F1B1C url(https://example.com/image.png) no-repeat center;
  background-size: min(600px, 100%);
}
```

### # You can use max() for responsive margins:
The following piece of code allows relative growth for tall viewports and reduces distance for shorter viewports, which also applies to zoomed viewports.

```css
.element {
  margin-top: max(8vh, 2rem);
}
```

On the taller viewports, 8vh will be used, and on smaller or zoomed-in viewports, 2rem will be used.

### # You can use clamp() to ensure responsive width values for \<p> elements:
According to The Elements of Typographic Style by Robert Bringhurst, "anything from 45 to 75 characters is widely regarded as a satisfactory length of line for a single-column page set in a serifed text face in a text size."

To ensure that your text blocks are not narrower than 45 characters or wider than 75 characters, use clamp() and the ch (0-width character advance) unit:

```css
p {
  width: clamp(45ch, 50%, 75ch);
}
```

This allows for the browser to determine the width of the paragraph. It will set the width to 50%, unless 50% is smaller than 45ch, at which point 45ch will be selected, and visa versa for if 50% is wider than 75ch.

### # You can use clamp() for fluid typography:
In order to enable fluid typography, Mike Riethmeuller popularized a technique that uses the clamp() function to set a minimum font size, maximum font size, and allow for scaling from the min to the max.

With clamp(), you can write this more clearly. Rather than requiring a complex string, the browser can do the work for you. Set the minimum acceptable font size (for example, 1.5rem for a title, maximum size (i.e. 3rem) and ideal size of 5vw).

Now, we get typography that scales with the viewport width of the page until it reaches the limiting minimum and maximum values, in a much more succinct line of code:

```css
p {
  font-size: clamp(1.5rem, 5vw, 3rem);
}
```

**These are some of the examples where you can use CSS math functions to create responsive designs.**

---
### [MDN Complete List of all CSS functions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions "CSS Functions")
---
### Knowledge Check

**Q1.** What are the four CSS math functions we covered above?

**A1.** calc(), min(), max() and clamp().

**Q2.** How do we use CSS math functions in our CSS?

**A2.** CSS math functions can be used as a value for any CSS property that `<length>`, `<frequency>`, `<angle>`, `<time>`, `<percentage>`, `<number>`, or `<integer>` are allowed as values.

```css
selector {
  property: function([argument]? [, argument]!);
}
```

The value syntax starts with the name of the function, followed by a left parenthesis (. Next up are the argument(s), and the function is finished off with a closing parenthesis ). Functions can take multiple arguments.

**Q3.** How can CSS functions help make websites and applications more responsive?

**A3.** min(), max() and clamp() CSS math functions are particularly useful for responsive web design. For example, clamp() function can be used to determine the font-size responsively, scale the typography as the viewport width changes. We can also use clamp() to make sure that the width of our \<p> elements is between 45ch and 75ch, for example.


