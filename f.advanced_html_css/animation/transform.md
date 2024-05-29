# `transform`
The `transform` property in CSS allows you to apply various transformations to an element. These transformations include translation (moving), rotation, scaling (resizing), and skewing. It's a powerful tool for creating dynamic and visually appealing web designs without the need for complex animations or scripting.

The transform property takes in one or more CSS transform functions as its values, with those functions taking in their own value, usually an angle or a number.

Almost all elements can have the transform property applied to it, with the exceptions being \<col>, \<colgroup>, and non-replaced inline elements. “Non-replaced” refers to elements whose content is contained within the HTML document (\<span>, \<b>, and \<em>, for example), as opposed to a “replaced” element’s content being contained outside of the document (\<a>, \<iframe>, and \<img>, for example). You do not need to memorize every element that is non-replaced, but rather keep this knowledge in mind should you try to apply the transform property to an element and aren’t sure why it isn’t working.

Here's a breakdown of the `transform` property:

1. **Translation (`translate()`):**
   Translation moves an element from its current position on the screen along the X and Y axes. You can specify the distance to move horizontally and vertically. For example:
   ```css
   transform: translate(50px, 100px);
   ```

2. **Rotation (`rotate()`):**
   Rotation rotates an element clockwise or counterclockwise around a fixed point. You specify the angle of rotation in degrees. For example:
   ```css
   transform: rotate(45deg);
   ```

3. **Scaling (`scale()`):**
   Scaling increases or decreases the size of an element along the X and Y axes. You specify the scaling factor for each axis. For example:
   ```css
   transform: scale(1.5, 2);
   ```

4. **Skewing (`skew()`):**
   Skewing tilts an element along the X and/or Y axes. You specify the angle of skewing in degrees. For example:
   ```css
   transform: skew(30deg, 0);
   ```

5. **Combining Transformations:**
   You can combine multiple transformations by separating them with spaces. The transformations are applied in the order specified. For example:
   ```css
   transform: translate(50px, 50px) rotate(45deg) scale(1.5);
   ```

6. **Transform Origin:**
   By default, transformations occur relative to the center of an element. However, you can change the origin point using the `transform-origin` property. This property allows you to specify where the transformation should originate from. For example:
   ```css
   transform-origin: top left;
   ```

7. **3D Transformations:**
   The `transform` property also supports 3D transformations, allowing you to manipulate elements in three dimensions. This includes translations, rotations, scalings, and skewings in the Z-axis. For example:
   ```css
   transform: translate3d(50px, 50px, 0) rotateY(45deg);
   ```

8. **Perspective:**
   When working with 3D transformations, you can use the `perspective` property to define a perspective view for an element and its child elements. This property affects the appearance of 3D transforms by determining the distance between the viewer and the z=0 plane. For example:
   ```css
   perspective: 1000px;
   ```

## Two-dimensional transforms
CSS transforms allow you to rotate, scale, skew and move elements.

In this section, we’ll go through 2D transforms with the following transform functions: `rotate()`, `scale()`, `skew()`, and `translate()`.

### `rotate()`
This is the transform function value to rotate an element on a 2D plane:

```css
.element {
  transform: rotate();
}

.rotate-by-deg {
  transform: rotate(45deg);
}

.rotate-by-rad {
  transform: rotate(-1rad);
}

.rotate-by-turn {
  transform: rotate(0.3turn);
}
```

When rotating an object, its coordinate system is transformed along with the object.

### `scale()`
These are the transform function values to scale an element on a 2D plane:

```css
.element {
  transform: scaleX();
  transform: scaleY();
  transform: scale();
}

.scaleX {
  transform: scaleX(0.25);
}

.scaleY {
  transform: scaleY(1.5);
}

.scaleXY {
  transform: scale(0.25, 1.5);
}

.scale {
  transform: scale(0.5);
}
```

### `skew()`
These are the transform function values to skew an element on a 2D plane:


```css
.element {
  transform: skewX();
  transform: skewY();
  transform: skew();
}

.skewX {
  transform: skewX(45deg);
}

.skewY {
  transform: skewY(-0.5rad);
}

.skewXY {
  transform: skew(45deg, -0.5rad);
}

.skew {
  /* single value behaves the same as skewX */
  transform: skew(45deg);
}
```

### `translate()`
These are the transform function values to translate(move) an element on a 2D plane:


```css
.element {
  transform: translateX();
  transform: translateY();
  transform: translate();
}

.translateX {
  transform: translateX(20px);
}

.translateY {
  /* percent values are of the element's width */
  transform: translateY(-33%);
}

.translateXY {
  transform: translate(20px, -33%);
}
```

## Chaining multiple transforms
Chaining multiple transforms involves applying more than one transformation to an element using the `transform` property. When you chain transforms, they are applied sequentially in the order specified. Each subsequent transformation is applied relative to the result of the previous transformation.

1. **Order of Transformations:**
   The order in which you specify the transformations matters because each transformation builds upon the previous one. For example, if you first translate an element and then rotate it, the rotation will be relative to the translated position.

2. **Example:**
   Let's say you want to translate an element, then rotate it, and finally scale it. You can chain these transformations in the following manner:
   ```css
   transform: translate(50px, 50px) rotate(45deg) scale(1.5);
   ```
   In this example:
   - `translate(50px, 50px)` moves the element 50 pixels to the right and 50 pixels down.
   - `rotate(45deg)` rotates the element 45 degrees clockwise around its center.
   - `scale(1.5)` scales the element to 150% of its original size.

3. **Using Matrix Transformation:**
   Behind the scenes, browsers represent transformations using a matrix. When you chain multiple transforms, the browser combines them into a single matrix transformation for performance reasons. This matrix combines all the individual transformations and applies them in one step, which can improve rendering performance.

4. **Effects of Transform Order:**
   The order of transformations can significantly affect the final result. For example, if you first scale an element and then rotate it, the rotation will occur relative to the scaled size, which may produce a different visual effect compared to rotating the element first and then scaling it.

5. **Perspective and 3D Transforms:**
   When dealing with 3D transforms, the order of transformations becomes even more critical. The perspective view and the positioning of elements in 3D space can affect how transformations are perceived. When working with 3D transforms, unlike other transform function values, `perspective` must be declared first (leftmost) when there are multiple transform function values.

## Three-dimensional transforms
The `rotate`, `scale`, and `translate` transform functions aren’t limited to just 2D planes, they also work for 3D planes as well. However, to perceive a 3D effect on these function values, `perspective` is required.

### `perspective`
In CSS, the `perspective` property is used to give an illusion of depth to 3D-transformed elements. It's particularly useful when working with CSS 3D transforms. 

Here's a breakdown of how it works:

1. **Basic Usage**: The `perspective` property is applied to the **parent element** of the transformed elements. It accepts a length value, which represents the distance from the viewer to the z=0 plane (where 3D transformations are projected). The smaller the value, the more pronounced the perspective effect will be.

2. **Syntax**: The syntax for the `perspective` property is as follows:
   ```css
   perspective: length|none|initial|inherit;
   ```

   - `length`: Specifies the depth of the perspective. It could be any valid length value like pixels (px), ems (em), or percentages (%).
   - `none`: No perspective is applied. It's the default value.
   - `initial`: Sets the property to its default value.
   - `inherit`: Inherits the property from its parent element.

3. **Example**:
   ```css
   .container {
       perspective: 1000px; /* Sets the perspective to 1000 pixels */
   }
   ```

4. **Effect**: Once the perspective is set, any child elements that are transformed using 3D transforms (`rotateX`, `rotateY`, `rotateZ`, `translateX`, `translateY`, `translateZ`, `scaleX`, `scaleY`, `scaleZ`, `skewX`, `skewY`) within this container will appear to have depth, as if they are being viewed from a certain distance.

5. **Browser Compatibility**: The `perspective` property is supported in modern browsers, but for older versions, you might need to use vendor prefixes like `-webkit-perspective` for WebKit browsers (Chrome, Safari) and `-moz-perspective` for Firefox.

6. **Considerations**: The `perspective` property only affects 3D-transformed children of the element to which it's applied. If you want to apply a perspective to the whole scene, you would apply it to the outermost container.

7. **Nested Perspectives**: If you apply `perspective` to nested elements, it creates a stacked perspective effect where each child's transformation is based on its immediate parent's perspective.

In summary, the `perspective` property in CSS provides a way to control the appearance of depth in transformed elements, enhancing the 3D visual effects on web pages.

### `perspective-origin`
The perspective-origin property allows you to specify the position of the vanishing point for the perspective effect created by the `perspective` property. It influences how the 3D-transformed child elements are perceived within the perspective view.

The `perspective-origin` property is set on the parent element.

Here's an explanation of the `perspective-origin` property:

1. **`perspective-origin: x-axis y-axis;`**:
   - The `perspective-origin` property accepts two values: one for the horizontal (x-axis) and one for the vertical (y-axis) perspective origin.
   - The default value is `50% 50%`, which means the perspective origin is at the center of the element.

2. **Horizontal (x-axis) and Vertical (y-axis) Values**:
   - The values for the `perspective-origin` property are specified using lengths or percentages. 
   - A percentage value represents the position relative to the width and height of the element. For example, `0%` would be the left edge, and `100%` would be the right edge.
   - Length values are specified in pixels or other CSS length units.

3. **Effect on 3D Transforms**:
   - The `perspective-origin` property determines the point from which the viewer appears to observe the 3D transformations applied to an element.
   - When an element is transformed in 3D space, such as being rotated or scaled, the perspective origin influences how the transformation appears relative to the viewer's perspective.

4. **Example**:
   ```css
   perspective-origin: 20px 30px;
   ```
   In this example:
   - The perspective origin is set to `20px` from the left edge of the element and `30px` from the top edge of the element.

5. **Effect of Changing Perspective Origin**:
   - Changing the perspective origin can alter the perceived depth and perspective of transformed elements. For example, moving the perspective origin closer to one edge of an element can make transformations appear more exaggerated from that perspective.

Here's a simple example to illustrate the effect of the `perspective-origin` property:

```css
.parent {
  perspective: 500px; /* Set perspective */
}

.child {
  transform: rotateY(45deg);
  perspective-origin: 20% 50%; /* Set perspective origin */
}
```

In this example:
- The `.parent` element has a perspective of `500px`.
- The `.child` element is rotated around the y-axis by `45deg`, and the perspective origin is set to `20%` from the left edge and `50%` from the top edge of the `.child` element.

By adjusting the `perspective-origin`, you can control how transformations are perceived in 3D space, allowing for more dynamic and visually appealing effects in your web design.

### `transform-style`
The `transform-style` property in CSS is used to specify how nested elements are rendered in 3D space when transformed. This property is particularly relevant when dealing with nested elements that have their own 3D transformations applied.

The `transform-style` property is applied to the parent element, and it specifies how nested elements are rendered in 3D space in relation to their parent.

Here's an explanation of the `transform-style` property:

1. **`transform-style: flat;`**:
   - This is the default value. It indicates that transformations should be rendered in a flat manner, meaning that nested elements are flattened into the plane of their parent element.
   - When `flat` is applied, child elements with 3D transformations will be rendered on the same plane as their parent element, essentially ignoring their own 3D transformations and appearing flat relative to their parent.

2. **`transform-style: preserve-3d;`**:
   - This value indicates that transformations should be preserved in 3D space, maintaining the hierarchy of nested elements.
   - When `preserve-3d` is applied, nested elements with 3D transformations will retain their position in 3D space relative to their parent element. This allows for more realistic 3D effects and maintains the visual hierarchy of the nested elements.

Here's a simple example to illustrate the difference between `flat` and `preserve-3d`:

```html
<div class="parent">
  <div class="child"></div>
</div>
```

```css
.parent {
  width: 200px;
  height: 200px;
  background-color: lightblue;
  transform-style: flat;
}

.child {
  width: 100px;
  height: 100px;
  background-color: pink;
  transform: rotateY(45deg);
}
```

In this example:
- When `transform-style: flat;` is applied to the parent element, the child element will be flattened and rendered on the same plane as the parent. So, the rotation applied to the child will not be visible, and it will appear as a flat pink square within the light blue square.
- When `transform-style: preserve-3d;` is applied to the parent element, the child element will retain its 3D transformation, and it will be rendered with the rotation applied relative to its parent. So, the child element will be displayed with a rotated perspective within the parent element.

In summary, the `transform-style` property in CSS allows you to control how nested elements are rendered in 3D space when transformations are applied, providing flexibility in creating realistic 3D effects and maintaining the visual hierarchy of elements.

### `perspective()`
The `perspective()` function is a CSS transform function that allows you to define the perspective from which an element is viewed directly within a transformation function. It's different from the `perspective` property in that it allows you to define perspective for individual transformations rather than for an entire container.

```css
.element {
  transform: perspective();
}
```

**The `perspective()` transform function is part of the `transform` value applied on the element being transformed. This differs from the `perspective` and `perspective-origin` properties which are attached to the parent of a child transformed in 3-dimensional space.**

Here's how it works:

1. **Usage**: The `perspective()` function is used within a transform function like `rotate()`, `translate()`, `scale()`, etc., to specify the perspective point for the transformation.

2. **Syntax**: The syntax for the `perspective()` function is:
   ```css
   transform: perspective(value);
   ```

   - `value`: Specifies the depth of the perspective, just like in the `perspective` property. It could be any valid length value like pixels (px), ems (em), or percentages (%).

3. **Example**:
   ```css
   .element {
       transform: perspective(1000px) rotateY(45deg);
   }
   ```

   In this example, the `.element` is rotated around the Y-axis by 45 degrees with a perspective point set at 1000 pixels from the viewer.

4. **Effect**: Using the `perspective()` function within a transform function alters the perspective for that specific transformation. This means that you can apply different perspectives to different transformations within the same element.

5. **Combining with other transform functions**: You can combine the `perspective()` function with other transform functions like `rotate()`, `translate()`, `scale()`, etc., to create various 3D effects with a specified perspective.

6. **Multiple transformations**: If you're applying multiple transformations to an element, it's important to note that the order matters. The `perspective()` function should be applied before other transformations to ensure the desired perspective effect.

7. **Browser Compatibility**: The `perspective()` function is supported in modern browsers, but for older versions, you might need to use vendor prefixes like `-webkit-perspective()` for WebKit browsers (Chrome, Safari) and `-moz-perspective()` for Firefox.

In summary, the `perspective()` function in CSS allows you to specify the perspective point directly within a transformation function, enabling you to create various 3D effects with individual perspectives for different transformations within an element.

### `rotate in 3D`
These are the additional transform function values to **rotate** an element in a 3D space:

```css
.element {
  transform: rotateX();
  transform: rotateY();
  transform: rotateZ();
  transform: rotate3d();
}
```

The `rotateX()`, `rotateY()`, and `rotateZ()` functions are specific transformations that rotate an element around the X, Y, and Z axes respectively in a 3D space. Each of these functions takes an angle parameter in degrees, specifying the amount of rotation around the respective axis.

On the other hand, the `rotate3d()` function allows you to specify a rotation in a 3D space using a vector representation. It takes four parameters: `rotate3d(x, y, z, angle)`. The first three parameters (`x`, `y`, and `z`) represent the axis around which the rotation will occur, and the `angle` parameter specifies the amount of rotation. This function is more versatile than the individual `rotateX()`, `rotateY()`, and `rotateZ()` functions because it allows you to define rotations around any arbitrary axis in 3D space, rather than being limited to the X, Y, and Z axes.

Here's an example to illustrate the difference:

```css
/* Using rotateX(), rotateY(), rotateZ() */
.rotateXYZ {
  transform: rotateX(45deg) rotateY(30deg) rotateZ(15deg);
}

/* Using rotate3d() */
.rotate3D {
  transform: rotate3d(1, 1, 1, 45deg); /* Rotate around the vector (1, 1, 1) by 45 degrees */
}
```

In the example above, `.rotateXYZ` applies rotations around the X, Y, and Z axes separately, while `.rotate3D` applies a rotation around a vector defined by the values `(1, 1, 1)` using `rotate3d()`. The `rotate3d()` function provides more flexibility by allowing you to specify any arbitrary axis of rotation in 3D space.

### `scale in 3D`
These are the additional transform function values to **scale** an element in a 3D space:

```css
.element {
  transform: scaleZ();
  transform: scale3d();
}
```

1. `transform: scaleZ()`: This function applies a scaling transformation to the z-axis of an element in a 3D space. It essentially changes the size of the element along the z-axis, while leaving the x and y axes unchanged. This can be used to create effects such as perspective distortion or simulating depth.

   Example:
   ```css
   .element {
     transform: scaleZ(2);
   }
   ```

   This would make the element appear twice as tall or deep along the z-axis.

2. `transform: scale3d()`: This function also applies a scaling transformation, but it allows you to specify scaling factors for all three dimensions (x, y, and z) in a single declaration. It's essentially a shorthand for specifying scaling in all three dimensions simultaneously.

   Example:
   ```css
   .element {
     transform: scale3d(1.5, 1.5, 1);
   }
   ```

   This would scale the element by 1.5 times in both the x and y dimensions while leaving the z dimension unchanged.

In summary, `scaleZ()` allows you to specifically scale along the z-axis in a 3D space, while `scale3d()` allows you to specify scaling factors for all three dimensions at once.

### `translate in 3D`
These are the additional transform function values to **translate** an element in a 3D space:

```css
.element {
  transform: translateZ();
  transform: translate3d();
}
```

1. **translateZ()**: 
   - `translateZ()` is a translation function that moves an element along the z-axis only, meaning it moves the element closer or farther away from the viewer without affecting its position on the x and y axes.
   - It takes a single argument which specifies the distance to translate along the z-axis. Positive values move the element away from the viewer, while negative values move it closer.
   - Example: `transform: translateZ(50px);` will move the element 50 pixels away from the viewer.

2. **translate3d()**: 
   - `translate3d()` is a 3D translation function that allows you to move an element in all three dimensions: x, y, and z.
   - It takes three arguments: the distance to translate along the x-axis, y-axis, and z-axis respectively.
   - Example: `transform: translate3d(50px, 20px, 30px);` will move the element 50 pixels to the right, 20 pixels down, and 30 pixels away from the viewer.
   - When using `translate3d()`, the browser can optimize the rendering process by performing the translation in a single step, potentially leading to smoother animations or transitions compared to using separate transform functions for each axis.

In summary, `translateZ()` is limited to moving elements along the z-axis only, while `translate3d()` provides the flexibility to move elements in all three dimensions. Additionally, using `translate3d()` can sometimes result in better performance due to optimization by the browser.

### `matrix`
Matrix is a way of combining all transform functions into one. It is seldom used due to its poor readability, and almost never written by hand. Unless you have a very complex transformation to apply, you should use other transform function values instead.

Both `matrix()` and `matrix3d()` are CSS transform functions that allow you to apply 2D or 3D transformations to elements, respectively, using matrices. Matrices are mathematical structures that represent transformations like translation, rotation, scaling, and skewing.

Here's how they work:

1. **matrix()**:
   - The `matrix()` function allows you to apply a 2D transformation to an element using a 2x3 matrix.
   - It takes six arguments, representing the values of the matrix in the following order: `matrix(a, b, c, d, tx, ty)`.
     - `a` and `d` represent the horizontal and vertical scaling factors, respectively.
     - `b` and `c` represent the horizontal and vertical skewing factors, respectively.
     - `tx` and `ty` represent the horizontal and vertical translation amounts, respectively.
   - Example: `transform: matrix(1, 0, 0, 1, 100, 50);` will translate the element 100 pixels horizontally and 50 pixels vertically.

2. **matrix3d()**:
   - The `matrix3d()` function allows you to apply a 3D transformation to an element using a 4x4 matrix.
   - It takes 16 arguments, representing the values of the matrix in row-major order.
   - The values correspond to a 4x4 transformation matrix, where each row represents the transformation for one axis (x, y, z, and w).
   - Example: `transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 100, 50, 0, 1);` will translate the element 100 pixels along the x-axis and 50 pixels along the y-axis in 3D space.

In summary, `matrix()` allows for 2D transformations using a 2x3 matrix, while `matrix3d()` allows for 3D transformations using a 4x4 matrix. Matrices offer a concise way to represent complex transformations and can be useful for combining multiple transformations into a single matrix for efficiency.

## Rendering Performance and transform
Users notice if sites and apps don't run well, so optimizing rendering performance is crucial.

Users of today's web expect that the pages they visit will be interactive and smooth, and that's where you need to increasingly focus your time and effort. Pages shouldn't just load quickly, but also respond quickly to user input throughout their entire lifecycle. 

While a major component of what makes a page feel snappy involves the amount of JavaScript you execute in response to user interactions, what users are anticipating are visual changes to the user interface. Visual changes to a user interface are the result of several types of work, often collectively referred to as rendering, and this work needs to happen as quickly as possible so that the user experience feels fast and reliable.

Most devices today refresh their screens 60 times a second. Each refresh produces the visual output you see, and is commonly known as a *frame*.

While a device's screen always refreshes at a consistent rate, applications that run on a device may not necessarily always be able to produce enough frames to match that refresh rate. For example, if there's an animation or transition running, the browser needs to match the device's refresh rate to produce one frame for each time the screen refreshes.

Given that a typical display refreshes 60 times per second, some quick math would reveal that the browser has 16.66 milliseconds to produce each frame. In reality, though, the browser has its own overhead for each frame, so all of your work needs to be completed inside 10 **milliseconds**. When you fail to meet this budget, the frame rate drops, and page contents judder on-screen. This phenomenon is often called *jank*.

### Browser's rendering/pixel pipeline
There are five major areas that you need to know about and be mindful of in your work as a web developer. These five areas are those that you have the most control over, and each represents a key point in the pixels-to-screen pipeline:

```
JS > Style > Layout > Paint > Composite
```

+ **JavaScript:** JavaScript is typically used to handle work that will result in visual changes to the user interface. For example, this could be jQuery's animate function, sorting a dataset, or adding DOM elements to the page. JavaScript isn't strictly necessary to trigger visual changes though; CSS animations, CSS transitions, and the Web Animations API are capable of animating page contents.

+ **Style calculations:** This is the process of figuring out which CSS rules apply to which HTML elements based on matching selectors. For example, .headline is an example of a CSS selector that applies to any HTML element with a class attribute value that contains a class of headline. From there, once rules are known, they are applied, and the final styles for each element are calculated.

+ **Layout:** Once the browser knows which rules apply to an element it can begin to calculate the geometry of the page, such as how much space elements take up, and where they appear on the screen. The web's layout model means that one element can affect others. For example, the width of the \<body> element typically affects the dimensions of its child elements all the way up and down the tree, so the process can be quite involved for the browser.

+ **Paint:** Painting is the process of filling in pixels. It involves drawing out text, colors, images, borders, shadows, and essentially every visual aspect of the elements after their layout on the page has been calculated. The drawing is typically done onto multiple surfaces, often called layers.

+ **Composite:** Since the parts of the page were potentially drawn onto multiple layers, they need to be applied to the screen in the correct order so that the page renders as expected. This is especially important for elements that overlap another, since a mistake could result in one element appearing over the top of another incorrectly.

Each of these parts of the pixel pipeline represents an opportunity to introduce jank in animations, or delay the painting of frames even for discrete visual changes to the user interface. It's therefore important to understand exactly which parts of the pipeline your code triggers, and to investigate if you can limit your changes to only the parts of the pixel pipeline that are necessary to render them.

You won't always necessarily touch every part of the pipeline on every frame. In fact, there are three ways the pipeline normally plays out for a given frame when you make a visual change, either with JavaScript, CSS, or the Web Animations API.

### 1. JS > Style > Layout > Paint > Composite
If you change a "layout" property, such as one that changes an element's geometry like width, height, or its position (such as the left or top CSS properties), the browser needs to check all other elements and "reflow" the page. Any affected areas will need to be repainted, and the final painted elements will need to be composited back together.

### 2. JS > Style > Paint > Composite
If you changed a "paint-only" property for an element in CSS—for example, properties such as background-image, color, or box-shadow—the layout step is not necessary to commit a visual update to the page. By omitting the layout step—where possible—you avoid potentially costly layout work that could have otherwise contributed significant latency in producing the next frame.

### 3. JS > Style > Composite
If you change a property that requires neither layout or paint, the browser can jump straight to the compositing step. This is the cheapest and most desirable pathway through the pixel pipeline for high pressure points in a page's lifecycle, such as animations or scrolling.

### `CSS Triggers`
CSS triggers, also known as layout triggers or rendering triggers, are specific actions or changes in the DOM (Document Object Model) that prompt the browser to recalculate the layout, repaint, or composite the webpage. Understanding CSS triggers is crucial for optimizing performance in web development, particularly when aiming to achieve smooth animations and fast page loading times.

Here are some common CSS triggers:

1. **Width and Height Changes**: Modifying the width or height of an element or its container can trigger layout recalculations.

2. **Positioning Changes**: Altering the position property (e.g., from static to relative, absolute, or fixed) or changing an element's position coordinates triggers layout recalculations.

3. **Display Property Changes**: Switching the display property (e.g., from block to inline, or vice versa) or toggling an element's visibility can affect layout calculations.

4. **Adding or Removing Elements**: Adding or removing elements from the DOM can trigger reflows and repaints, especially if they affect the layout of surrounding elements.

5. **Content Changes**: Updating text content or modifying inline styles (e.g., font-size, color) can trigger reflows and repaints.

6. **Box Model Changes**: Adjusting padding, margin, border, or box-sizing properties can affect the layout and trigger reflows.

7. **CSS Animations and Transitions**: Animating properties like width, height, opacity, or position can trigger repaints and composite updates.

8. **Flexbox and Grid Layouts**: Changes in flexbox or grid layout properties, such as flex-grow, flex-shrink, flex-basis, grid-template-columns, grid-template-rows, etc., can trigger layout recalculations.

9. **Pseudo-class and Pseudo-element Changes**: Applying or removing pseudo-classes (:hover, :active, :focus) or pseudo-elements (::before, ::after) can cause repaints and layout recalculations.

10. **Font Loading**: Initial rendering may be delayed until the necessary fonts are downloaded and applied, affecting the layout and visual appearance of the page.

Optimizing performance involves minimizing the frequency and impact of these triggers. Techniques such as batched updates, CSS transforms instead of layout-affecting properties, and lazy loading of resources can help mitigate their effects and improve the overall user experience.

###
Compositing is where the painted parts of the page are put together for displaying on screen.

There are two key factors in this area that affect page performance: the number of compositor layers that need to be managed, and the properties that you use for animations.

#### Use `transform` and `opacity` for animations:
The best-performing version of the pixel pipeline avoids both layout and paint, and only requires compositing changes.

In order to achieve this you will need to stick to changing properties that can be handled by the compositor alone. Today there are only two properties for which that is true - `transform`s and `opacity`.

![Compositing Props](../../../img/compositing-props.jpg "Compositing Props")

The caveat for the use of transforms and opacity is that the element on which you change these properties should be on its own *compositor layer*. In order to make a layer you must *promote* the element.

#### Promote elements that you plan to animate:
You should promote elements that you plan to animate (within reason, don't overdo it!) to their own layer:

```css
.moving-element {
  will-change: transform;
}
```

Or, for older browsers, or those that don't support will-change:

```css
.moving-element {
  transform: translateZ(0);
}
```

**Do not promote elements unnecessarily.** Every layer you create requires memory and management, and that's not free. In fact, on devices with limited memory the impact on performance can far outweigh any benefit of creating a layer.

Lastly, it should be reminded that the key benefit of using `transform` is that it occurs during composition. This makes it cheaper to use compared to many other CSS properties.

---

### Knowledge Check

**Q1.** What are the four main functions of the transform property?

**A1.** `rotate()`, `scale()`, `skew()`, and `translate()`.

**Q2.** Which function can be used to move an object through space on the X, Y, or Z axis?

**A2.** `translate()`. The following transform function values can be used to translate(move) an element on a 2D plane:

```css
.element {
  transform: translateX();
  transform: translateY();
  transform: translate();
}

.translateX {
  transform: translateX(20px);
}

.translateY {
  /* percent values are of the element's width */
  transform: translateY(-33%);
}

.translateXY {
  transform: translate(20px, -33%);
}
```
The following are the additional transform function values to **translate** an element in a 3D space:

```css
.element {
  transform: translateZ();
  transform: translate3d();
}
```

1. **translateZ()**: 
   - `translateZ()` is a translation function that moves an element along the z-axis only, meaning it moves the element closer or farther away from the viewer without affecting its position on the x and y axes.
   - It takes a single argument which specifies the distance to translate along the z-axis. Positive values move the element away from the viewer, while negative values move it closer.
   - Example: `transform: translateZ(50px);` will move the element 50 pixels away from the viewer.

2. **translate3d()**: 
   - `translate3d()` is a 3D translation function that allows you to move an element in all three dimensions: x, y, and z.
   - It takes three arguments: the distance to translate along the x-axis, y-axis, and z-axis respectively.
   - Example: `transform: translate3d(50px, 20px, 30px);` will move the element 50 pixels to the right, 20 pixels down, and 30 pixels away from the viewer.
   - When using `translate3d()`, the browser can optimize the rendering process by performing the translation in a single step, potentially leading to smoother animations or transitions compared to using separate transform functions for each axis.


**Q3.** Which function can be used to make an object larger or smaller on the X, Y, or Z axis?

**A3.** `scale()`. The following are the transform function values to scale an element on a 2D plane:

```css
.element {
  transform: scaleX();
  transform: scaleY();
  transform: scale();
}

.scaleX {
  transform: scaleX(0.25);
}

.scaleY {
  transform: scaleY(1.5);
}

.scaleXY {
  transform: scale(0.25, 1.5);
}

.scale {
  transform: scale(0.5);
}
```

The following are the additional transform function values to **scale** an element in a 3D space:

```css
.element {
  transform: scaleZ();
  transform: scale3d();
}
```

1. `transform: scaleZ()`: This function applies a scaling transformation to the z-axis of an element in a 3D space. It essentially changes the size of the element along the z-axis, while leaving the x and y axes unchanged. This can be used to create effects such as perspective distortion or simulating depth.

   Example:
   ```css
   .element {
     transform: scaleZ(2);
   }
   ```

   This would make the element appear twice as tall or deep along the z-axis.

2. `transform: scale3d()`: This function also applies a scaling transformation, but it allows you to specify scaling factors for all three dimensions (x, y, and z) in a single declaration. It's essentially a shorthand for specifying scaling in all three dimensions simultaneously.

   Example:
   ```css
   .element {
     transform: scale3d(1.5, 1.5, 1);
   }
   ```

   This would scale the element by 1.5 times in both the x and y dimensions while leaving the z dimension unchanged.

**Q4.** What additional function is required for 3D transforms?

**A4.** The `perspective()` function is a CSS transform function that allows you to define the perspective from which an element is viewed directly within a transformation function. It's different from the `perspective` property in that it allows you to define perspective for individual transformations rather than for an entire container.

```css
.element {
  transform: perspective();
}
```

**The `perspective()` transform function is part of the `transform` value applied on the element being transformed. This differs from the `perspective` and `perspective-origin` properties which are attached to the parent of a child transformed in 3-dimensional space.**

Here's how it works:

1. **Usage**: The `perspective()` function is used within a transform function like `rotate()`, `translate()`, `scale()`, etc., to specify the perspective point for the transformation.

2. **Syntax**: The syntax for the `perspective()` function is:
   ```css
   transform: perspective(value);
   ```

   - `value`: Specifies the depth of the perspective, just like in the `perspective` property. It could be any valid length value like pixels (px), ems (em), or percentages (%).

3. **Example**:
   ```css
   .element {
       transform: perspective(1000px) rotateY(45deg);
   }
   ```

   In this example, the `.element` is rotated around the Y-axis by 45 degrees with a perspective point set at 1000 pixels from the viewer.

4. **Effect**: Using the `perspective()` function within a transform function alters the perspective for that specific transformation. This means that you can apply different perspectives to different transformations within the same element.

5. **Combining with other transform functions**: You can combine the `perspective()` function with other transform functions like `rotate()`, `translate()`, `scale()`, etc., to create various 3D effects with a specified perspective.

6. **Multiple transformations**: If you're applying multiple transformations to an element, it's important to note that the order matters. The `perspective()` function should be applied before other transformations to ensure the desired perspective effect.

7. **Browser Compatibility**: The `perspective()` function is supported in modern browsers, but for older versions, you might need to use vendor prefixes like `-webkit-perspective()` for WebKit browsers (Chrome, Safari) and `-moz-perspective()` for Firefox.

In summary, the `perspective()` function in CSS allows you to specify the perspective point directly within a transformation function, enabling you to create various 3D effects with individual perspectives for different transformations within an element.

