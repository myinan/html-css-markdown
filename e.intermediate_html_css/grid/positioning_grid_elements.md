# Positioning Grid Elements
## Positioning Grid items
Whenever we create grid tracks, grid lines are created implicitly. This is important. Grid lines are only created after our grid tracks have been defined. We can not explicitly create grid lines.

Every track has a start line and an end line. The lines are numbered from left to right and top to bottom starting at 1. So, for example, a 3x3 grid has vertical lines for columns ranging from 1 to 4 and horizontal lines for rows ranging from 1 to 4.

Grid lines are what we use to position grid items.

Once you've defined the structure of your grid using `grid-template-rows` and `grid-template-columns`, the next step is to position individual grid items within this grid. This is where the `grid-row-start`, `grid-row-end`, `grid-column-start`, and `grid-column-end` properties come into play.

- `grid-row-start` and `grid-row-end`: These properties allow you to specify the starting and ending row lines for a grid item. The grid row lines are numbered from top to bottom, starting with 1. For example, `grid-row-start: 1` means the item starts at the first row line, and `grid-row-end: 2` means it ends at the second row line.

- `grid-column-start` and `grid-column-end`: Similar to rows, these properties define the starting and ending column lines for a grid item. Column lines are numbered from left to right, starting with 1. For instance, `grid-column-start: 1` indicates the item starts at the first column line, and `grid-column-end: 3` means it ends at the third column line.

- Shorthand `grid-row` and `grid-column` properties: You can streamline the process of defining both the start and end positions of a grid item by using these shorthand properties. For example, `grid-row: 1 / 3` indicates that the item starts at row line 1 and ends at row line 3, effectively spanning two row tracks. Similarly, `grid-column: 2 / 5` signifies that the item starts at column line 2 and ends at column line 5, spanning three column tracks.

**Example:**

```css
.item1 {
  grid-row-start: 1;
  grid-row-end: 2;
  grid-column-start: 1;
  grid-column-end: 3;
}
```

In this example, `.item1` is positioned to start at the first row line and end at the second row line (spanning one row track) and start at the first column line and end at the third column line (spanning two column tracks).

**Default span**: If an item only spans one track you can omit the `grid-column-end` or `grid-row-end` value. Grid defaults to spanning one track.

Now, let's look at the shorthand example:

```css
.item2 {
  grid-row: 1 / 3; /* Starts at row line 1 and ends at row line 3 */
  grid-column: 2 / 4; /* Starts at column line 2 and ends at column line 4 */
}
```

In this shorthand approach, `.item2` is placed to span from row line 1 to row line 3 (two row tracks) and from column line 2 to column line 4 (two column tracks), making it a more concise and readable way to define grid item placement.

**Counting backwards**: We can also count backwards from the block end and inline end of the grid, for English that would be the final row line and right-hand column line. These lines can be addressed as -1, and you can count back from there; so the second last line is -2. It is worth noting that the final line is the final line of the explicit grid, the grid defined by grid-template-columns and grid-template-rows, and does not take into account any rows or columns added in the implicit grid outside of that.

#### Using the "span" keyword
In addition to specifying the start and end lines by number, you can specify a start line and then the number of tracks you would like the area to span.

```html
<div class="wrapper">
  <div class="box1">One</div>
  <div class="box2">Two</div>
  <div class="box3">Three</div>
  <div class="box4">Four</div>
</div>
```

```css
.box1 {
  grid-column: 1;
  grid-row: 1 / span 3;
}
.box2 {
  grid-column: 3;
  grid-row: 1 / span 2;
}
.box3 {
  grid-column: 2;
  grid-row: 1;
}
.box4 {
  grid-column: 2 / span 2;
  grid-row: 3;
}
```



## `grid-area` property
You now know how to position your grid items using row and column lines. But there are other ways to position items.

There is an even shorter shorthand for positioning grid items with start and end lines. You can combine `grid-row-start / grid-column-start / grid-row-end / grid-column-end` into one line using `grid-area`.

In our following example,

```html
<div class="container">
  <div class="room" id="living-room">Living Room</div>
  <div class="room" id="kitchen">Kitchen</div>
  <div class="room" id="bedroom">Bedroom</div>
  <div class="room" id="bathroom">Bathroom</div>
  <div class="room" id="closet">Closet</div>
</div>
```
`#living-room` can be styled as following:

```css
.container {
  display: inline-grid;
  grid-template: 40px 40px 40px 40px 40px / 40px 40px 40px 40px 40px;
  background-color: lightblue; 
}

.room {
  border: 1px solid;
  font-size: 50%;
  text-align: center;
}

#living-room {
  grid-area: 1 / 1 / 3 / 6;
}
```

But `grid-area` can also refer to a few different things.

Instead of using the grid lines to position all the items in a grid, we can create a visual layout of the grid in words. To do this we give each item on the grid a name using `grid-area`.

So our living room can be written just like this:

```css
#living-room {
  grid-area: living-room;
}
```

We could do this to all of our grid items and give each room a `grid-area` value as a name. Then we can map out the whole structure with the grid container using `grid-template-areas`.

```css
.container {
  display: inline-grid;
  grid-template: 40px 40px 40px 40px 40px / 40px 40px 40px 40px 40px;
  background-color: lightblue; 
  grid-template-areas:
    "living-room living-room living-room living-room living-room"
    "living-room living-room living-room living-room living-room"
    "bedroom bedroom bathroom kitchen kitchen"
    "bedroom bedroom bathroom kitchen kitchen"
    "closet closet bathroom kitchen kitchen"    
}

.room {
  border: 1px solid;
  font-size: 50%;
  text-align: center;
}

#living-room {
   grid-area:  living-room;
}

#kitchen {
  grid-area: kitchen;
}

#bedroom {
  grid-area: bedroom;
}

#bathroom {
  grid-area: bathroom;
}

#closet {
  grid-area: closet;
}
```

So now you know two very different ways of using `grid-area` on a grid item. You might also see that the term “grid area” refering to a group of cells. For example, all the grid cells of the living room together constitutes a grid area.

## Alignment and Justification
#### **Properties for the parent (grid container)**
### `align-items`
Aligns grid items along the block (column) axis (as opposed to `justify-items` which aligns along the inline (row) axis). This value applies to all grid items inside the container.

Values:

+ **stretch** – fills the whole height of the cell (this is the default).
+ **start** – aligns items to be flush with the start edge of their cell.
+ **end** – aligns items to be flush with the end edge of their cell.
+ **center** – aligns items in the center of their cell.
+ **baseline** – align items along text baseline. There are modifiers to baseline — first baseline and last baseline which will use the baseline from the first or last line in the case of multi-line text.

```css
.container {
  align-items: start | end | center | stretch;
}
```

This behavior can also be set on individual grid items via the `align-self` property.

There are also modifier keywords `safe` and unsafe (usage is like `align-items: safe end`). The safe keyword means “try to align like this, but not if it means aligning an item such that it moves into inaccessible overflow area”, while unsafe will allow moving content into inaccessible areas (“data loss”).

### `justify-items`
Aligns grid items along the inline (row) axis (as opposed to `align-items` which aligns along the block (column) axis). This value applies to all grid items inside the container.

Values:

+ **start** – aligns items to be flush with the start edge of their cell.
+ **end** – aligns items to be flush with the end edge of their cell.
+ **center** – aligns items in the center of their cell.
+ **stretch** – fills the whole width of the cell (this is the default).

```css
.container {
  justify-items: start | end | center | stretch;
}
```

This behavior can also be set on individual grid items via the `justify-self` property.

### `place-items`
`place-items` sets both the `align-items` and `justify-items` properties in a single declaration.

Values:

`<align-items>` / `<justify-items>` – The first value sets align-items, the second value justify-items. If the second value is omitted, the first value is assigned to both properties.

```css
.center {
  display: grid;
  place-items: center;
}
```

### `justify-content`
Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the inline (row) axis (as opposed to align-content which aligns the grid along the block (column) axis).

Values:

+ **start** – aligns the grid to be flush with the start edge of the grid container.
+ **end** – aligns the grid to be flush with the end edge of the grid container.
+ **center** – aligns the grid in the center of the grid container.
+ **stretch** – resizes the grid items to allow the grid to fill the full width of the grid container.
+ **space-around** – places an even amount of space between each grid item, with half-sized spaces on the far ends.
+ **space-between** – places an even amount of space between each grid item, with no space at the far ends.
+ **space-evenly** – places an even amount of space between each grid item, including the far ends.

```css
.container {
  justify-content: start | end | center | stretch | space-around | space-between | space-evenly;    
}
```

### `align-content`
Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the block (column) axis (as opposed to justify-content which aligns the grid along the inline (row) axis).

Values:

+ **start** – aligns the grid to be flush with the start edge of the grid container.
+ **end** – aligns the grid to be flush with the end edge of the grid container.
+ **center** – aligns the grid in the center of the grid container.
+ **stretch** – resizes the grid items to allow the grid to fill the full height of the grid container.
+ **space-around** – places an even amount of space between each grid item, with half-sized spaces on the far ends.
+ **space-between** – places an even amount of space between each grid item, with no space at the far ends.
+ **space-evenly** – places an even amount of space between each grid item, including the far ends.

```css
.container {
  align-content: start | end | center | stretch | space-around | space-between | space-evenly;    
}
```

### `place-content`
`place-content` sets both the `align-content` and `justify-content` properties in a single declaration.

Values:

`<align-content>` / `<justify-content>` – The first value sets align-content, the second value justify-content. If the second value is omitted, the first value is assigned to both properties.
All major browsers except Edge support the place-content shorthand property.

**IMPORTANT!:** When using `<align-content>`, `<justify-content>` or `place-content`, it is worth noting that using these space distribution values may cause items on your grid to become larger. If an item spans more than one grid track, as further space is added between the tracks, that item needs to become large to absorb the space (tracks which span more than one column/row track will gain extra space). We're always working in a strict grid. Therefore, if you decide to use these values, ensure that the content of your tracks can cope with the extra space, or that you have used alignment properties on the items, to cause them to move to the start rather than stretch.

---
#### **Properties for the children (grid items)**

### `justify-self`
Aligns a grid item inside a cell along the inline (row) axis (as opposed to `align-self` which aligns along the block (column) axis). This value applies to a grid item inside a single cell.

Values:

+ **start** – aligns the grid item to be flush with the start edge of the cell.
+ **end** – aligns the grid item to be flush with the end edge of the cell.
+ **center** – aligns the grid item in the center of the cell.
+ **stretch** – fills the whole width of the cell (this is the default).

```css
.item {
  justify-self: start | end | center | stretch;
}
```

To set alignment for all the items in a grid, this behavior can also be set on the grid container via the `justify-items` property.

### `align-self`
Aligns a grid item inside a cell along the block (column) axis (as opposed to `justify-self` which aligns along the inline (row) axis). This value applies to the content inside a single grid item.

Values:

+ **start** – aligns the grid item to be flush with the start edge of the cell.
+ **end** – aligns the grid item to be flush with the end edge of the cell.
+ **center** – aligns the grid item in the center of the cell.
+ **stretch** – fills the whole height of the cell (this is the default).

To align all the items in a grid, this behavior can also be set on the grid container via the `align-items` property.

### `place-self`
`place-self` sets both the align-self and justify-self properties in a single declaration.

Values:

+ **auto** – The “default” alignment for the layout mode.
+ `<align-self>` / `<justify-self>` – The first value sets align-self, the second value justify-self. If the second value is omitted, the first value is assigned to both properties.

```css
.item-a {
  place-self: center;
}
```

All major browsers except Edge support the place-self shorthand property.

---
### Knowledge Check

**Q1.** Explain the difference between a track and a line.

**A1.** Grid track is the area defined between two vertical or horizontal grid lines. A grid line is a line spans either horizontal or vertical direction, in a grid.

**Q2.** What is the smallest unit on a grid?

**A2.** The smallest unit on a grid is the grid cell. It's the area between two adjacent horizontal grid lines and two adjacent vertical grid lines.

**Q3.** What kind of value do we give to the grid-column-start or grid-column-end properties?

**A3.** `grid-column-start` and `grid-column-end` properties are used on grid items to define the area they will occupy on the grid. On these properties we use `line numbers` of our grid to define the area. Line numbers, in left-to-right writing mode, will begin with number 1 and span across from the leftmost line to the rightmost line, in the column/block direction. We can also use keywords on these properties such as `span` or `end`.

**Q4.** Which property can we use to combine all the start and end values for a grid item?

**A4.** The property `grid-area` can be used to define start and end values for a grid item on both column direction and vertical direction. We can combine `grid-row-start / grid-column-start / grid-row-end / grid-column-end` into one line using `grid-area`.

**Q5.** Which grid container property can map out a visual structure of grid items?

**A5.** `grid-template-areas` property can be used to map out a more visual grid structure when defining our grid.

Other than the usage above, `grid-area` can also be used in conjunction with grid-template-areas.

Instead of using the grid lines to position all the items in a grid, we can create a visual layout of the grid in words. To do this we give each item on the grid a name using `grid-area`.

Example:

```css
#living-room {
  grid-area: living-room;
}
```

We could do this to all of our grid items and give each room a `grid-area` value as a name. Then we can map out the whole structure with the grid container using `grid-template-areas`.

```css
.container {
  display: inline-grid;
  grid-template: 40px 40px 40px 40px 40px / 40px 40px 40px 40px 40px;
  background-color: lightblue; 
  grid-template-areas:
    "living-room living-room living-room living-room living-room"
    "living-room living-room living-room living-room living-room"
    "bedroom bedroom bathroom kitchen kitchen"
    "bedroom bedroom bathroom kitchen kitchen"
    "closet closet bathroom kitchen kitchen"    
}

.room {
  border: 1px solid;
  font-size: 50%;
  text-align: center;
}

#living-room {
   grid-area:  living-room;
}

#kitchen {
  grid-area: kitchen;
}

#bedroom {
  grid-area: bedroom;
}

#bathroom {
  grid-area: bathroom;
}

#closet {
  grid-area: closet;
}
```




