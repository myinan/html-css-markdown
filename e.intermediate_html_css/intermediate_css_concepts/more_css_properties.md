# More CSS Properties


### **background**:
   The `background` shorthand CSS property sets all background style properties at once, such as color, image, origin and size, or repeat method. Component properties not set in the `background` shorthand property value declaration are set to their default values.This property is a shorthand for the following CSS properties:

   + background-attachment
   + background-clip
   + background-color
   + background-image
   + background-origin
   + background-position
   + background-repeat
   + background-size

**Syntax:** 

```css
   /* Using a <background-color> */
background: green;

/* Using a <bg-image> and <repeat-style> */
background: url("test.jpg") repeat-y;

/* Using a <box> and <background-color> */
background: border-box red;

/* A single image, centered and scaled */
background: no-repeat center/80% url("../img/image.png");
```

**Initial value** (as each of the properties of the shorthand):

+ `background-image`: none
+ `background-position`: 0% 0%
+ `background-size`: auto auto
+ `background-repeat`: repeat
+ `background-origin`: padding-box
+ `background-clip`: border-box
+ `background-attachment`: scroll
+ `background-color`: transparent

One thing to note is that it is possible to use these sub-properties individually, and in some cases it might be easier and more clear to do that than defaulting to the `background` shorthand. This is in contrast to some other shorthand properties where it is almost always preferable to default to using the shorthand (flex, margin, padding etc.)   
   
### **border**:
   The `border` shorthand CSS property sets an element's border. It sets the values of `border-width`, `border-style`, and `border-color`.

**Syntax**:

```css
/* style */
border: solid;

/* width | style */
border: 2px dotted;

/* style | color */
border: outset #f33;

/* width | style | color */
border: medium dashed green;
```

The border property may be specified using one, two, or three of the values listed above (border-width, border-style, border-color). The order of the values does not matter.

Note: The border will be invisible if its style is not defined. This is because the style defaults to none.

As with all shorthand properties, any omitted sub-values will be set to their initial value.

**Formal Syntax**:

```
border = 
  <line-width>  ||
  <line-style>  ||
  <color>       

<line-width> = 
  <length [0,∞]>  |
  thin            |
  medium          |
  thick           

<line-style> = 
  none    |
  hidden  |
  dotted  |
  dashed  |
  solid   |
  double  |
  groove  |
  ridge   |
  inset   |
  outset  
```

### **border-radius**:
   The `border-radius` CSS property rounds the corners of an element's outer border edge.

   This property is a shorthand for the following CSS properties:

   + border-top-left-radius
   + border-top-right-radius
   + border-bottom-right-radius
   + border-bottom-left-radius

   **Syntax**:

```css
/* Radius is set for all 4 sides */
border-radius: 10px;

/* top-left-and-bottom-right | top-right-and-bottom-left */
border-radius: 10px 5%;

/* top-left | top-right-and-bottom-left | bottom-right */
border-radius: 2px 4px 2px;

/* top-left | top-right | bottom-right | bottom-left */
border-radius: 1px 0 3px 4px;
```


### **box-shadow**:
   The `box-shadow` CSS property adds shadow effects around an element's frame. You can set multiple effects separated by commas. A box shadow is described by X and Y offsets relative to the element, blur and spread radius, and color.

   The box-shadow property enables you to cast a drop shadow from the frame of almost any element. If a border-radius is specified on the element with a box shadow, the box shadow takes on the same rounded corners.

```css
   /* Keyword values */
box-shadow: none;

/* offset-x | offset-y | color */
box-shadow: 60px -16px teal;

/* offset-x | offset-y | blur-radius | color */
box-shadow: 10px 5px 5px black;

/* offset-x | offset-y | blur-radius | spread-radius | color */
box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);

/* inset | offset-x | offset-y | color */
box-shadow: inset 5em 1em gold;

/* Any number of shadows, separated by commas */
box-shadow:
  3px 3px red,
  -1em 0 0.4em olive;
```

**Specify a single box-shadow using**:

+ Two, three, or four \<length> values.
    - If only two values are given, they are interpreted as \<offset-x> and \<offset-y> values.
    - If a third value is given, it is interpreted as a \<blur-radius>.
    - If a fourth value is given, it is interpreted as a \<spread-radius>.
+ Optionally, the inset keyword.
+ Optionally, a \<color> value.

To specify multiple shadows, provide a comma-separated list of shadows.

**Values**:

`inset`: If not specified (default), the shadow is assumed to be a drop shadow (as if the box were raised above the content). The presence of the inset keyword changes the shadow to one inside the frame (as if the content was debossed inside the box). Inset shadows are drawn inside the border (even transparent ones), above the background, but below content.

`<offset-x>`: The \<length> value specifies the horizontal distance. Negative values place the shadow to the left of the element.

`<offset-y>`: The \<length> values specifies the vertical distance. Negative values place the shadow above the element.

If both \<offset-x> and \<offset-y> are set to 0, the shadow is placed behind the element (and may generate a blur effect if \<blur-radius> and/or \<spread-radius> is set).

`<blur-radius>`: This is a third \<length> value. The larger this value, the bigger the blur, so the shadow becomes bigger and lighter. Negative values are not allowed. If not specified, it will be 0 (the shadow's edge is sharp).

`<spread-radius>`: This is a fourth \<length> value. Positive values will cause the shadow to expand and grow bigger, negative values will cause the shadow to shrink. If not specified, it will be 0 (the shadow will be the same size as the element).

`<color>`: If not specified, it defaults to `currentcolor``.



### **overflow**:
   The `overflow` CSS shorthand property sets the desired behavior when content does not fit in the parent element box (overflows) in the horizontal and/or vertical direction.

**Syntax**:

```css
/* Keyword values */
overflow: visible;
overflow: hidden;
overflow: clip;
overflow: scroll;
overflow: auto;
overflow: hidden visible;
```

The overflow property is specified as one or two `<overflow>` keyword values. If only one keyword is specified, both overflow-x and overflow-y are set to the same value. If two keywords are specified, the first value applies to overflow-x in the horizontal direction and the second one applies to overflow-y in the vertical direction.

**`auto`**: Overflow content is clipped at the element's padding box, and overflow content can be scrolled into view. Unlike `scroll`, user agents display scroll bars only if the content is overflowing and hide scroll bars by default. If content fits inside the element's padding box, it looks the same as with `visible`.

### **opacity**:
   The `opacity` CSS property sets the opacity of an element. Opacity is the degree to which content behind an element is hidden, and is the opposite of transparency.

**Formal syntax**:

```
opacity = 
  <alpha-value>  

<alpha-value> = 
  <number>      |
  <percentage>  
```

`<alpha-value>`:<br>
A \<number> in the range 0.0 to 1.0, inclusive, or a \<percentage> in the range 0% to 100%, inclusive, representing the opacity of the channel (that is, the value of its alpha channel). Any value outside the interval, though valid, is clamped to the nearest limit in the range.

`0` means the element is fully transparent (that is, invisible).<br>
`Any <number> strictly between 0 and 1` means the element is translucent (that is, content behind the element can be seen).<br>
`1` (default value) means the element is fully opaque (visually solid).

Note: To change the opacity of a background only, use the background property with a color value that allows for an alpha channel. For example: 

```css
background: rgba(0, 0, 0, 0.4);
```

---
### Knowledge Check

**Q1.** Which property would you use to make an element transparent?

**A1.** In order to make an element transparent, we would set the `opacity` property to value `0`.

**Q2.** Which property would you use to make a background image tile?

**A2.** In order to create a "tiled" background image we can do the following:

Use the `background-image` property to set the URL of the image we want to use as the background.<br>
Use the `background-repeat` property and set it to `repeat`, which tells the browser to repeat the background image both horizontally and vertically to create a tiled effect.

We can also use other values for background-repeat if we want different tiling behavior:

`repeat-x`: Repeats the background image only horizontally.<br>
`repeat-y`: Repeats the background image only vertically.<br>
`no-repeat`: Does not repeat the background image, and it will only appear once.

**Q3.** Which property would you use to add scrollbars to an element?

**A3.** We can use either the `overflow: scroll` or `overflow: auto` CSS rules to add scrollbars to an element.

**Q4.** Which property would you use to add a shadow behind an element?

**A4.** The `box-shadow` CSS property adds shadow effects around an element's frame. We can set multiple effects separated by commas. A box shadow is described by X and Y offsets relative to the element, blur and spread radius, and color.

The box-shadow property enables us to cast a drop shadow from the frame of almost any element. If a border-radius is specified on the element with a box shadow, the box shadow takes on the same rounded corners.

```css
/* offset-x | offset-y | blur-radius | spread-radius | color */
box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
```

**Q5.** Which property would you use to create rounded corners on an element?

**A5.** The `border-radius` CSS property rounds the corners of an element's outer border edge.

   This property is a shorthand for the following CSS properties:

   + border-top-left-radius
   + border-top-right-radius
   + border-bottom-right-radius
   + border-bottom-left-radius

   **Syntax**:

```css
/* Radius is set for all 4 sides */
border-radius: 10px;

/* top-left-and-bottom-right | top-right-and-bottom-left */
border-radius: 10px 5%;

/* top-left | top-right-and-bottom-left | bottom-right */
border-radius: 2px 4px 2px;

/* top-left | top-right | bottom-right | bottom-left */
border-radius: 1px 0 3px 4px;
```

**Q6.** How would you use border-radius to make a circular element?

**A6.** To create a circular element using the `border-radius` CSS property, you need to set the `border-radius` property to half of the element's width and height. This will create a perfect circle. Here's an example of how you can do it:

```css
.circular-element {
  width: 100px; /* Adjust the width and height as needed */
  height: 100px; /* Adjust the width and height as needed */
  background-color: #3498db; /* Background color for the circular element */
  border-radius: 50%; /* Set the border-radius to 50% for a perfect circle */
}
```

In this example:

1. You define a CSS class called `.circular-element`.
2. You set the `width` and `height` properties to the same value to ensure that the element is a square (you can adjust these values to control the size of the circle).
3. You set the `background-color` to give the circular element a background color (you can change this color as desired).
4. The key part is setting `border-radius` to `50%`. This tells the browser to create rounded corners for the element with a radius equal to half of its width, resulting in a perfect circle.

You can then apply this class to an HTML element to make it circular:

```html
<div class="circular-element"></div>
```

This will create a circular element with the specified dimensions and background color. 