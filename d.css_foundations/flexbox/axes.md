# Axes
The orientation of items within a flex container can be controlled using the `flex-direction` property.

The default direction for a flex container is horizontal, or row, but you can change the direction to vertical, or column. The direction can be specified in CSS like so:

```
.flex-container {
    flex-direction: column;
}
```

## Axes
No matter which direction you’re using, you need to think of your flex-containers as having 2 axes: the main axis and the cross axis. It is the direction of these axes that changes when the flex-direction is changed. In most circumstances, flex-direction: row puts the main axis horizontal (left-to-right), and column puts the main axis vertical (top-to-bottom).

**Important Detail:** When we change the flex-direction to column from default(row), flex-basis then refers to height instead of width.

---

When working with flexbox you need to think in terms of two axes — the main axis and the cross axis. The main axis is defined by the flex-direction property, and the cross axis runs perpendicular to it. Everything we do with flexbox refers back to these axes, so it is worth understanding how they work from the outset.

### The main axis
The main axis is defined by flex-direction, which has four possible values:

+ row
+ row-reverse
+ column
+ column-reverse

Should you choose row or row-reverse, your main axis will run along the row in the inline direction.

Choose column or column-reverse and your main axis will run from the top of the page to the bottom — in the block direction.

### The cross axis
The cross axis runs perpendicular to the main axis, therefore if your flex-direction (main axis) is set to row or row-reverse the cross axis runs down the columns.

If your main axis is column or column-reverse then the cross axis runs along the rows.

### Start and end lines
Another vital area of understanding is how flexbox makes no assumption about the writing mode of the document. In the past, CSS was heavily weighted towards horizontal and left-to-right writing modes. Modern layout methods encompass the range of writing modes and so we no longer assume that a line of text will start at the top left of a document and run towards the right-hand side, with new lines appearing one under the other.

If the flex-direction is row and I am working in English, then the start edge of the main axis will be on the left, the end edge on the right.

If I were to work in Arabic, then the start edge of my main axis would be on the right and the end edge on the left.

In both cases the start edge of the cross axis is at the top of the flex container and the end edge at the bottom, as both languages have a horizontal writing mode.

![Flex Axes](../../../img/flex-container.png)

---

### Knowledge Check

**Q1.** How do you make flex items arrange themselves vertically instead of horizontally?

**A1.** The default value of `flex-direction` property of a .flex-container is `row`. If we want to change the flex direction to column ( e.g. make flex items arrange themselves vertically), then we would need to set `flex-direction: column;` declaration inside .flex-container.

**Q2.** In a column flex-container, what does flex-basis refer to?

**A2.** In a column flex-container, flex-basis refers to "height" of the flex items instead of "width".

**Q3.** In a row flex-container, what does flex-basis refer to?

**A3.** In a row flex-container, flex-basis refers to width of the flex items.

**Q4.** Why do the previous two questions have different answers?

**A4.** The previous two questions have different answers because the flex-direction property determines the main axis of a flex-container. In a column flex-container, the main axis is vertical, so flex-basis refers to the height of the flex items. In contrast, in a row flex-container, the main axis is horizontal, so flex-basis refers to the width of the flex items. The behavior of flex-basis is dependent on the flex-direction and the corresponding main axis orientation.