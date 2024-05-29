# The Box Model
The most important skills you need to master with CSS are positioning and layout. Changing fonts and colors is a crucial skill, but being able to put things exactly where you want them on a webpage is even more crucial.

## The Box Model
Every single thing on a webpage is a rectangular box. These boxes can have other boxes in them and can sit alongside one another. You can get a rough idea of how this works by sticking a border on every item on the page like this:

```
* {
  border: 2px solid red;
}
```

The only real complication here is that there are many ways to manipulate the size of these boxes, and the space between them, using padding, margin, and border.

+ **padding** increases the space between the border of a box and the content of the box.

+ **margin** increases the space between the borders of a box and the borders of adjacent boxes.

+ **border** adds space (even if it’s only a pixel or two) between the margin and the padding.

![Box Model](../../img/box-model.png "Box Model")


+ Important!: In the box model, "margin" collapses between two elements that are next to each other. If two elements are next to each other and they both have a margin property, whichever margin value is greatest is going to be used.

### **box-sizing:**
The `box-sizing` CSS property sets how the total width and height of an element is calculated.

By default in the CSS box model, the width and height you assign to an element is applied only to the element's content box. If the element has any border or padding, this is then added to the width and height to arrive at the size of the box that's rendered on the screen. This means that when you set width and height, you have to adjust the value you give to allow for any border or padding that may be added. For example, if you have four boxes with width: 25%;, if any has left or right padding or a left or right border, they will not by default fit on one line within the constraints of the parent container.

The box-sizing property can be used to adjust this behavior:

- content-box gives you the default CSS box-sizing behavior. If you set an element's width to 100 pixels, then the element's content box will be 100 pixels wide, and the width of any border or padding will be added to the final rendered width, making the element wider than 100px.

- **border-box** tells the browser to account for any border and padding in the values you specify for an element's width and height. If you set an element's width to 100 pixels, that 100 pixels will include any border or padding you added, and the content box will shrink to absorb that extra width. This typically makes it much easier to size elements. `box-sizing: border-box` is the default styling that browsers use for the \<table>, \<select>, and \<button> elements, and for \<input> elements whose type is radio, checkbox, reset, button, submit, color, or search.

Note: It is often useful to set box-sizing to border-box to lay out elements. This makes dealing with the sizes of elements much easier, and generally eliminates a number of pitfalls you can stumble on while laying out your content. 

---

# MDN (Mozilla Developer Network) "The Box Model" Lesson

[The Box Model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)

Everything in CSS has a box around it, and understanding these boxes is key to being able to create more complex layouts with CSS, or to align items with other items. In this lesson, we will take a look at the CSS Box Model.

## Block and inline boxes

In CSS we have several types of boxes that generally fit into the categories of **block boxes** and **inline boxes**. The type refers to how the box behaves in terms of page flow and in relation to other boxes on the page. Boxes have an **inner display type** and an **outer display type**.

##  Outer display type
If a box has an outer display type of **block**, then:

+ The box will break onto a new line.
+ The width and height properties are respected.
+ Padding, margin and border will cause other elements to be pushed away from the box.
+ If width is not specified, the box will extend in the inline direction to fill the space available in its container. In most cases, the box will become as wide as its container, filling up 100% of the space available.

Some HTML elements, such as \<h1> and \<p>, use block as their outer display type by default.

If a box has an outer display type of **inline**, then:

+ The box will not break onto a new line.
+ The width and height properties will not apply.
+ Top and bottom padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.
+ Left and right padding, margins, and borders will apply and will cause other inline boxes to move away from the box.

Some HTML elements, such as \<a>, \<span>, \<em> and \<strong> use inline as their outer display type by default.

## Inner display type
Boxes also have an inner display type, which dictates how elements inside that box are laid out.

Block and inline layout is the default way things behave on the web. By default and without any other instruction, the elements inside a box are also laid out in normal flow and behave as block or inline boxes.

### The key thing to remember for now is: Changing the value of the display property can change whether the outer display type of a box is block or inline. This changes the way it displays alongside other elements in the layout.

## What is the CSS box model?
The CSS box model as a whole applies to block boxes and defines how the different parts of a box — margin, border, padding, and content — work together to create a box that you can see on a page. Inline boxes use just some of the behavior defined in the box model.

To add complexity, there is a standard and an alternate box model. By default, browsers use the standard box model.

### Parts of a box
Making up a block box in CSS we have the:

+ Content box: The area where your content is displayed; size it using properties like inline-size and block-size or width and height.
+ Padding box: The padding sits around the content as white space; size it using padding and related properties.
+ Border box: The border box wraps the content and any padding; size it using border and related properties.
+ Margin box: The margin is the outermost layer, wrapping the content, padding, and border as whitespace between this box and other elements; size it using margin and related properties.

The below diagram shows these layers:


![Box Model](../../img/box-model2.png "Box Model")

### The standard CSS box model
In the standard box model, if you give a box an inline-size and a block-size (or width and a height) attributes, this defines the inline-size and block-size (width and height in horizontal languages) of the **content box**. Any padding and border is then added to those dimensions to get the total size taken up by the box.

Example:

```
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

The actual space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150 + 25 + 25 + 5 + 5).

Note: The margin is not counted towards the actual size of the box. The box's area stops at the border — it does not extend into the margin.

### The alternative CSS box model
In the alternative box model, any width is the width of the visible box on the page. The content area width is that width minus the width for the padding and border. No need to add up the border and padding to get the real size of the box.

To turn on the alternative model for an element, set `box-sizing: border-box;` on it:

```
.box {
  box-sizing: border-box;
  width: 350px;
  inline-size: 350px;
  height: 150px;
  block-size: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

Now, the actual space taken up by the box will be 350px in the inline direction and 150px in the block direction.

## Margins, borders and padding

### Margin
The margin is an invisible space around your box. It pushes other elements away from the box. Margins can have positive or negative values. Setting a negative margin on one side of your box can cause it to overlap other things on the page. Whether you are using the standard or alternative box model, the margin is always added after the size of the visible box has been calculated.

We can control all margins of an element at once using the margin property, or each side individually using the equivalent longhand properties:

+ margin-top
+ margin-right
+ margin-bottom
+ margin-left

#### Margin collapsing

Depending on whether two elements whose margins touch have positive or negative margins, the results will be different:

+ Two positive margins will combine to become one margin. Its size will be equal to the largest individual margin.

+ Two negative margins will collapse and the smallest (furthest from zero) value will be used.

+ If one margin is negative, its value will be subtracted from the total.

### Border
The border is drawn between the margin and the padding of a box. If you are using the standard box model, the size of the border is added to the width and height of the content box. If you are using the alternative box model then the size of the border makes the content box smaller as it takes up some of that available width and height of the element box.

For styling borders, there are a large number of properties — there are four borders, and each border has a style, width, and color that we might want to manipulate.

You can set the width, style, or color of all four borders at once using the border property.

To set the properties of each side individually, use:

+ border-top
+ border-right
+ border-bottom
+ border-left

To set the width, style, or color of all sides, use:

+ border-width
+ border-style
+ border-color

To set the width, style, or color of a single side, use one of the more granular longhand properties:

+ border-top-width
+ border-top-style
+ border-top-color
+ border-right-width
+ border-right-style
+ border-right-color
+ border-bottom-width
+ border-bottom-style
+ border-bottom-color
+ border-left-width
+ border-left-style
+ border-left-color

### Padding
The padding sits between the border and the content area and is used to push the content away from the border. Unlike margins, you cannot have a negative padding. Any background applied to your element will display behind the padding.

The padding property controls the padding on all sides of an element. To control each side individually, use these longhand properties:

+ padding-top
+ padding-right
+ padding-bottom
+ padding-left

### The box model and inline boxes
All of the above fully applies to block boxes. Some of the properties can apply to inline boxes too, such as those created by a \<span> element.

If a box has an outer display type of inline, then:

+ The box will not break onto a new line.
+ The width and height properties will not apply.
+ Top and bottom padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.
+ Left and right padding, margins, and borders will apply and will cause other inline boxes to move away from the box.

Some HTML elements, such as \<a>, \<span>, \<em> and \<strong> use inline as their outer display type by default.

## Using display: inline-block
display: inline-block is a special value of display, which provides a middle ground between inline and block. Use it if you do not want an item to break onto a new line, but do want it to respect width and height and avoid the overlapping described above.

An element with display: inline-block does a subset of the block things we already know about:

+ The width and height properties are respected.
+ padding, margin, and border will cause other elements to be pushed away from the box.

It does not, however, break onto a new line, and will only become larger than its content if you explicitly add width and height properties.

---

### Knowledge Check

**Q1.** From inside to outside, what is the order of box-model properties?

**A1.**  Content - Padding - Border - Margin

**Q2.** What does the box-sizing CSS property do?

**A2.** The `box-sizing` CSS property sets how the total width and height of an element is calculated.

**Q3.** What is the difference between the standard and alternative box model?

**A3.** With standard box model the height and width of an element is calculated as follows: content height/width + padding + border. 

But with the alternative box model (CSS rule `box-sizing: border-box;`), the content area width is declared width minus the width for the padding and border. No need to add up the border and padding to get the real size of the box.

**Q4.** Would you use margin or padding to create more space between 2 elements?

**A4.** Margin is used to create space between 2 different elements.

**Q5.** Would you use margin or padding to create more space between the contents of an element and its border?

**A5.** We would use padding to create more space between the content of an element and the element's border.

**Q6.** Would you use margin or padding if you wanted two elements to overlap each other?

**A6.** In order to overlap two elements onto each other, we would use the margin property and give it a negative value.

**Q7.** How do you set the alternative box model for all of your elements?

**A7.** 
```
* {
  box-sizing: border-box;
}
```

**Q8.** How do you center an element horizontally?

**A8.** To center an element horizontally, we can give the element a specified width value and then set the left and right margin properties' values to "auto".


