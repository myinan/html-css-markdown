# Block and Inline
We can modify the box calculation by changing the display property. CSS has two box types: block and inline boxes, which determine element behavior and interaction. The display property controls how HTML elements appear on the webpage.

## Block vs Inline
By default, block elements will appear on the page stacked atop each other, each new element starting on a new line.

Inline elements, however, do not start on a new line. They appear in line with whatever elements they are placed beside. A clear example of an inline element is a link, or \<a> tag.

### The middle ground inline-block
Inline-block elements behave like inline elements, but with block-style padding and margin. display: inline-block is a useful tool to know about, but in practice, you’ll probably end up reaching for flexbox more often if you’re trying to line up a bunch of boxes. Flexbox will be covered in-depth in the next lesson.

## Divs and Spans
We can’t talk about block and inline elements without discussing divs and spans. All the other HTML elements we have encountered so far give meaning to their content. For example, paragraph elements tell the browser to display the text it contains as a paragraph. Strong elements tell the browser which texts within are important and so on. Yet, divs and spans give no particular meaning to their content. They are just generic boxes that can contain anything.

Having elements like this available to us is a lot more useful than it may first appear. We will often need elements that serve no other purpose than to be “hook” elements. We can give an id or class to target them for styling with CSS. Another use case we will face regularly is grouping related elements under one parent element to correctly position them on the page. Divs and spans provide us with the ability to do this.

**Div** is a block-level element by default. It is commonly used as a container element to group other elements. Divs allow us to divide the page into different blocks and apply styling to those blocks.

**Span** is an inline-level element by default. It can be used to group text content and inline HTML elements for styling and should only be used when no other semantic HTML element is appropriate.

---

## Normal Flow
Normal flow is the way that webpage elements lay themselves out if you haven't changed their layout.

### How are elements laid out by default?
The process begins as the boxes of individual elements are laid out in such a way that any padding, border, or margin they happen to have is added to their content. This is what we call the box model.

By default, a block-level element's content fills the available inline space of the parent element containing it, growing along the block dimension to accommodate its content. The size of inline-level elements is just the size of their content. You can set width or height on some elements that have a default display property value of inline, like \<img>, but display value will still remain inline.

If you want to control the display property of an inline-level element in this manner, use CSS to set it to behave like a block-level element (e.g., with display: block; or display: inline-block;, which mixes characteristics from both).

That explains how elements are structured individually, but how about the way they're structured when they interact with one another? The normal layout flow is the system by which elements are placed inside the browser's viewport. By default, block-level elements are laid out in the block flow direction, which is based on the parent's writing mode (initial: horizontal-tb). Each element will appear on a new line below the last one, with each one separated by whatever margin that's been specified. In English, for example, (or any other horizontal, top to bottom writing mode) block-level elements are laid out vertically.

Inline elements behave differently. They don't appear on new lines; instead, they all sit on the same line along with any adjacent (or wrapped) text content as long as there is space for them to do so inside the width of the parent block level element. If there isn't space, then the overflowing content will move down to a new line.

If two vertically adjacent elements both have a margin set on them and their margins touch, the larger of the two margins remains and the smaller one disappears. This is known as margin collapsing. Collapsing margins is only relevant in the vertical direction.

## HTML Block and Inline Elements
Every HTML element has a default display value, depending on what type of element it is.

There are two display values: block and inline.

### Block-level Elements
A block-level element always starts on a new line, and the browsers automatically add some space (a margin) before and after the element.

A block-level element always takes up the full width available (stretches out to the left and right as far as it can).

Two commonly used block elements are: \<p> and \<div>.

The \<p> element defines a paragraph in an HTML document.

The \<div> element defines a division or a section in an HTML document.

Here are the block-level elements in HTML:

```
<address> <article> <aside> <blockquote> <canvas> <dd> <div> <dl> <dt> <fieldset> <figcaption> <figure> <footer> <form> <h1>-<h6> <header> <hr> <li> <main> <nav> <noscript> <ol> <p> <pre> <section> <table> <tfoot> <ul> <video>
```

### Inline Elements
An inline element does not start on a new line.

An inline element only takes up as much width as necessary.

Here are the inline elements in HTML:

```
<a> <abbr> <acronym> <b> <bdo> <big> <br> <button> <cite> <code> <dfn> <em> <i> <img> <input> <kbd> <label> <map> <object> <output> <q> <samp> <script> <select> <small> <span> <strong> <sub> <sup> <textarea> <time> <tt> <var>
```

---

Exercises “01-margin-and-padding-1” and “02-margin-and-padding-2” are completed (odin-css-exercises-fork/margin-and-padding directory).

---

### Knowledge Check

**Q1.** What is the difference between a block element and an inline element?

**A1.** A block element always starts on a new line and takes up the full width of its container element by default. Height, width, padding, and margin values are respected on a block element.

An inline element, on the other hand, does not start on a new line and sits within the same line as the elements around it. Inline elements do not respect width and height values directly; instead, they typically adjust their dimensions based on their content. Padding and margin values are respected on inline elements, but the top and bottom margins and paddings do not cause surrounding elements to move.

**Q2.** What is the difference between an inline element and an inline-block element?

**A2.** An inline element behaves as described in the above answer. An inline-block element on the other hand, sits on the same line like an inline element but it's width,height, margin and padding values are respected as they are with a block element.

**Q3.** Is an h1 block or inline?

**A3.** "h1" is a block element by default.

**Q4.**Is button block or inline?

**A4.**"button" is an inline element by default.

**Q5.** Is div block or inline?

**A5.** "div" is a block element by default.

**Q6.** Is span block or inline?

**A6.**"span" is an inline element by default.