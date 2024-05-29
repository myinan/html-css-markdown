# Creating a Grid (Basic Concepts of Grid Layout)
CSS Grid is a powerful layout system that allows you to create complex two-dimensional grid-based layouts in web development. It enables precise control over the placement and sizing of elements within a container, making it an essential tool for building responsive and visually appealing web designs.

### Grid Container and Grid Items
A **grid container** is an HTML element that becomes a grid when you apply CSS Grid properties to it. You can make any element a grid container by setting its `display` property to `grid` or `inline-grid`.

The children of a grid container are known as **grid items**. These are the elements that you want to arrange within the grid. It's important to remember that only the direct children of a grid container will become grid items. But, a grid item can also be a grid container itself, making nested grids possible.

### Grid Lines and Grid Tracks
A grid is composed of horizontal and vertical lines called **grid lines**. Grid lines divide the grid into rows and columns.

The spaces between two adjacent grid lines are called **grid tracks**. Grid tracks can be rows or columns, depending on whether the grid is horizontal or vertical.

### Defining the Grid Structure (Rows and Columns)
You can specify the number of rows and columns in the grid with properties `grid-template-rows` and `grid-template-columns`. You can use various units like pixels, percentages, or the `fr` unit (fractional unit) to define track sizes.

**IMPORTANT:** It should be noted that when we define a grid we define the grid tracks, not the lines. Grid then gives us numbered lines to use when positioning items. For example, in a three column, two row grid we would have four column lines.

### Explicit Grid and Implicit Grid
When we use the grid-template-columns and grid-template-rows properties, we are explicitly defining grid tracks to lay out our grid items. But when the grid needs more tracks for extra content, it will implicitly define new grid tracks. Additionally, the size values established from our grid-template-columns or grid-template-rows properties are not carried over into these implicit grid tracks. But we can define values for the implicit grid tracks.

If you place items outside the explicitly defined grid (i.e., beyond the specified rows and columns), CSS Grid automatically creates new rows and columns in what is called the **implicit grid**.

You can control the sizing and behavior of the implicit grid using properties like `grid-auto-rows` and `grid-auto-columns`.

By default, CSS Grid will add additional content with implicit rows. This means the extra elements would keep being added further down the grid in a vertical fashion. It would be much less common to want extra content added horizontally along the grid, but that can be set using the `"grid-auto-flow: column"` property and those implicit track sizes can be defined with the `grid-auto-columns` property.

#### Track sizing with minmax:
When setting up an explicit grid or defining the sizing for automatically created rows or columns we may want to give tracks a minimum size, but also ensure they expand to fit any content that is added. For example, I may want my rows to never collapse smaller than 100 pixels, but if my content stretches to 300 pixels in height, then I would like the row to stretch to that height.

Grid has a solution for this with the `minmax()` function. In this next example we are using `minmax()` in the value of grid-auto-rows. This means automatically created rows will be a minimum of 100 pixels tall, and a maximum of `auto`. Using `auto` means that the size will look at the content size and will stretch to give space for the tallest item in a cell, in this row.

```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(100px, auto);
}
```

### Grid Cells
A grid cell is the smallest unit on a grid. It is the space between two adjacent row and two adjacent column grid lines. Conceptually it is like a table cell. Once a grid is defined as a parent, the child items will lay themselves out in one cell each of the defined grid.

### Grid Areas
Items can span one or more cells both by row or by column, and this creates a `grid area`. Grid areas must be rectangular – it isn't possible to create an L-shaped area, for example.

### Gap
The gap between grid rows and columns is known as the gutter or alley. Gap sizes can be adjusted separately for rows and columns using the `column-gap` and `row-gap` properties. Furthermore, we can use a shorthand property called `gap` to set both row-gap and column-gap. If you only give one value for `gap` it will apply to both column and row gaps. If you specify two values, the first is used for `row-gap` and the second for `column-gap`.

Any space used by gaps will be accounted for before space is assigned to the flexible length fr tracks, and gaps act for sizing purposes like a regular grid track, however you cannot place anything into a gap. In terms of line-based positioning of items, the gap acts as if the line has gained extra width. Anything starting at that line starts after the gap and you cannot address the gap or place anything into it. If you want gutters that act more like regular tracks you can of course define a track for the purpose instead.

Gaps only appear between tracks of the grid, they do not add space to the top and bottom, left or right of the container. 

### Nesting grids
A grid item can become a grid container.

The children of a grid item are not direct children of the grid container thus they do not participate in grid layout and display in a normal document flow.

**Nesting without subgrid:** If we set a grid item to `display: grid`, we can give it a track definition and it too will become a grid. It's children then lay out on this new grid. In this case the nested grid has no relationship to the parent. This grid will not inherit the gap of the parent and the lines in the nested grid will not align to the lines in the parent grid.

**Subgrid:** In addition to regular grids, subgrid let us create nested grids that use the track definition of the parent grid.

```css
.parent-grid {
  display: grid;
  grid-template-columns: repeat(9, 1fr);
}
.grid-item {
  grid-column: 2 / 7;

  display: grid;
  grid-template-columns: subgrid;
}
.child-of-grid-item {
  /* gets to participate on parent grid! */
  grid-column: 3 / 6;
}
```

### Layering items with z-index
Grid items can occupy the same cell, and in this case we can use the z-index property to control the order in which overlapping items stack.

#### Overlapping without z-index
In our below example, we make two items overlap without using the z-index property.

```html
<div class="wrapper">
  <div class="box box1">One</div>
  <div class="box box2">Two</div>
  <div class="box box3">Three</div>
  <div class="box box4">Four</div>
  <div class="box box5">Five</div>
</div>
```

```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 100px;
}

.box1 {
  grid-column-start: 1;
  grid-column-end: 4;
  grid-row-start: 1;
  grid-row-end: 3;
}

.box2 {
  grid-column-start: 1;
  grid-row-start: 2;
  grid-row-end: 4;
}
```

The item box2 is now overlapping box1, it displays on top as it comes later in the source order.

#### Controlling the order
We can control the order in which items stack up by using the `z-index` property - just like positioned items. If we give box2 a lower z-index than box1 it will display below box1 in the stack.

---
### Knowledge Check

**Q1.** How does an HTML element become a grid item?

**A1.** When we set the rule `display: grid` on the parent element containing said HTML element, that HTML element will become a grid item.

**Q2.** What is the space between lines on the grid?

**A2.** On a grid, the space between two adjacent row and two adjacent column grid lines is a `grid cell`.<br>The spaces between two adjacent grid lines are called `grid tracks`. Grid tracks can be rows or columns, depending on whether the grid is horizontal or vertical.<br>Also, items can span one or more cells both by row or by column, and this creates a `grid area`.

**Q3.** How do you set gutters (also known as alleys) in the grid?

**A3.** The gap between grid rows and columns is known as the gutter or alley. Gap sizes can be adjusted separately for rows and columns using the `column-gap` and `row-gap` properties. Furthermore, we can use a shorthand property called `gap` to set both row-gap and column-gap.

**Q4.** Describe what happens when you have more content than defined tracks.

**A4.** When we define tracks on a grid, we create an "explicit grid". If we place items outside the explicitly defined grid (i.e., beyond the specified rows and columns), CSS Grid automatically creates new rows (or columns) in what is called the **implicit grid**.

**Q5.** How could you change the size for those undefined tracks?

**A5.** We can control the sizing and behavior of the implicit grid using properties like `grid-auto-rows` and `grid-auto-columns`.

By default, CSS Grid will add additional content with implicit rows. This means the extra elements would keep being added further down the grid in a vertical fashion. It would be much less common to want extra content added horizontally along the grid, but that can be set using the `"grid-auto-flow: column"` property and those implicit track sizes can be defined with the `grid-auto-columns` property.

