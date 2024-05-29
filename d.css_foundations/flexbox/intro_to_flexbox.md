# Introduction to Flexbox
Flexbox is a powerful CSS layout module that provides a flexible way to align and distribute elements within a container. It was introduced in CSS3 to make it easier to build responsive and dynamic web layouts.

At its core, flexbox operates on a parent-child relationship. The container, also known as the flex container, is created by setting the `display` property to `flex` or `inline-flex` on an element. This tells the browser that the container's children should be laid out using flexbox rules.

Once an element becomes a flex container, it can control the positioning and behavior of its child elements, referred to as flex items. The flex items are arranged along a main axis and can also wrap onto multiple lines if needed.

Here are some key concepts and properties associated with flexbox:

1. Main Axis and Cross Axis: Flexbox defines a main axis and a cross axis. The main axis represents the primary direction in which flex items are laid out, while the cross axis is perpendicular to the main axis.

2. Flex Direction: The `flex-direction` property controls the direction of the main axis. It can be set to `row` (default), `row-reverse`, `column`, or `column-reverse`. This determines the flow of flex items.

3. Justify Content: The `justify-content` property aligns flex items along the main axis. It controls the spacing and distribution between items. Values include `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, and `space-evenly`.

4. Align Items: The `align-items` property aligns flex items along the cross axis. It controls their vertical positioning within the container. Values include `flex-start`, `flex-end`, `center`, `baseline`, and `stretch`.

5. Flexbox Sizing: The `flex-grow`, `flex-shrink`, and `flex-basis` properties control the sizing and flexibility of flex items. By manipulating these properties, you can make certain items expand, shrink, or take up specific proportions of available space.

6. Flex Wrap: By default, flex items are displayed in a single line. The `flex-wrap` property allows items to wrap onto multiple lines if necessary. Values include `nowrap` (default), `wrap`, and `wrap-reverse`.

These are just a few of the fundamental properties used in flexbox. The flexibility and versatility of flexbox make it an excellent tool for creating responsive layouts, vertical alignments, equal-height columns, and much more.

---

## The Flex Container

An area of a document laid out using flexbox is called a flex container. To create a flex container, we set the value of the area's container's display property to flex or inline-flex. As soon as we do this the direct children of that container become flex items. As with all properties in CSS, some initial values are defined, so when creating a flex container all of the contained flex items will behave in the following way:

+ Items display in a row (the flex-direction property's default is row).
+ The items start from the start edge of the main axis.
+ The items do not stretch on the main dimension, but can shrink.
+ The items will stretch to fill the size of the cross axis.
+ The flex-basis property is set to auto.
+ The flex-wrap property is set to nowrap.

The result of this is that your items will all line up in a row, using the size of the content as their size in the main axis. If there are more items than can fit in the container, they will not wrap but will instead overflow. If some items are taller than others, all items will stretch along the cross axis to fill its full size.

---

### Knowledge Check

**Q1.** What’s the difference between a flex container and a flex item?

**A1.** In flexbox, a flex container and a flex item are two distinct entities that play different roles in the layout.

1. Flex Container: A flex container is an element that is designated as the parent element in which flex items are placed. It is created by applying the CSS property `display: flex` or `display: inline-flex` to an element. This property turns the element into a flex container, establishing a new flex formatting context. The flex container controls the layout and behavior of its child elements (flex items). It defines the main axis, cross axis, and various properties that affect the arrangement of flex items within it.

2. Flex Item: A flex item is a child element of a flex container. It is any element that is directly nested inside a flex container. Flex items are the individual elements that are arranged and positioned within the flex container. The flex container applies rules to the flex items, defining their behavior and positioning. Flex items can have their own properties that affect their sizing, flexibility, and alignment within the container.

To summarize, the flex container is the parent element that establishes the flex layout context, while the flex items are the child elements that are laid out and positioned within the container according to the flexbox rules set by the container. The container determines the layout and alignment of the items, and the items respond to these container rules to adapt their position and size accordingly.

Once an element becomes a flex container, it can control the positioning and behavior of its child elements, referred to as flex items.

**Q2.** How do you create a flex item?

**A2.** To create a flex item, we need to have a flex container in place. Once we have a flex container, we can designate any element within it as a flex item by including it as a child of the flex container element.

A flex item must be a direct child of the flex container to be considered as such. Any nested elements within a flex item do not automatically become flex items unless they are directly placed inside a flex container themselves.