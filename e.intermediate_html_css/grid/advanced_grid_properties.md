# Advanced Grid Properties
## `repeat()`
`repeat()` is a CSS function available to the CSS Grid template properties that allows us to define a number of rows or columns and the size we want them to be without having to manually type out each individual track’s size.

```css
.grid-container {
  grid-template-rows: repeat(2, 150px);
  grid-template-columns: repeat(5, 150px);
}
```

## Fractional unit (`fr`)
Now that we know how to quickly create many grid tracks, it’s time to learn how to start making them dynamic. Dynamic, in this context, simply means “flexible” or “responsive in some way.” The opposite of dynamic is static, or fixed at a certain defined height or width, like 150px, which we used in the setup of above grid.

The most basic way to make our grid items dynamic is by using fractional units, also known as `fr`.

The fr unit is a way of distributing whatever remaining space is left in the grid. For example, if we have a four-column grid with a total width of 400px and four grid items each on a column track assigned 1fr as their size, all of the grid items should be given one fraction of that 400px of space, which is 100 pixels.

```css
.grid-container {
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(5, 1fr);
}
```

We can also tell our grid items to distribute the remaining space disproportionately. For example, if we divide the 5 columns up by giving the first two a track size of 2fr and the remaining three a track size of 1fr, the first two tracks will be given twice as much remaining space as the others.

You can also mix static units (like px) and dynamic units (like fr).

## Defining minimum and maximum track sizes: `min()` and `max()`
When we resize our grid super small, it is reassuring to know that the browser will stop the item from shrinking beyond the `min-content` value. However, we really don’t want to rely on that most of the time. It’s much better for you to explicitly decide as a developer how small and large your content should be, even in the most extreme situations.

We learned about min() and max() in our previous lesson on CSS functions, but a bit of review can’t hurt. Both of these functions will return a value based on the arguments you supply them. min() will return the smallest of all the values passed in, and max() will return the largest. For example, min(100px, 200px) will return a value of 100px every time, while max(100px, 200px) will return a value of 200px every time.

You can supply as many arguments to these functions as you want.

Of course, it’s silly to give these functions static units because the calculation is meaningless: the smallest or largest value will always be returned. But when we provide a dynamic value as one of these arguments, we unlock the real potential of these functions, especially in the context of Grid:

```css
.grid-container {
  grid-template-rows: repeat(2, min(200px, 50%));
  grid-template-columns: repeat(5, max(120px, 15%));
}
```

## Dynamic minimum and maximum sizes
### `minmax()`
minmax() is a CSS function that is specifically used with Grid. It can only be used with the following CSS properties:

+ grid-template-columns
+ grid-template-rows
+ grid-auto-columns
+ grid-auto-rows

It is a relatively straightforward function that only takes in two arguments:<br>
The minimum size the grid track can be<br>
The maximum size the grid track can be

Unlike min() and max(), it can make sense to use static values for both arguments.

```css
.grid-container {
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(5, minmax(150px, 200px));
}
```

### `clamp()`
Unlike minmax(), clamp() is a CSS function that can be used anywhere, not just within a grid container. As with min() and max(), we learned about clamp() in a previous lesson too, but let’s do a quick review. The syntax is as follows:

`clamp(minimum-size, ideal-size, maximum-size)`

What this does is allow our item to resize itself until it reaches one of the minimum or maximum threshold values.

Since clamp()’s purpose is to create a flexibly sized track with constraints, we want to use a dynamic value for the “ideal size” argument, and typically a static size for the minimum and maximum size, although it is possible to use a dynamic value here too.

```css
.grid-container {
  grid-template-columns: repeat(5, clamp(150px, 20%, 200px));
}
```

Using clamp() and minmax() are fantastic methods for making grids more responsive while ensuring we don’t hit critical breakpoints that make our website look bad. This is imperative when using images and elements that may have a tendency to overflow or render in undesirable ways when pushed to extreme sizes.

## `auto-fit` and `auto-fill`
These two values are actually a part of the repeat() function specification, but they were saved for the end of the lesson because their usefulness is not apparent until after you understand the minmax() function. Here’s the use case: You want to give your grid a number of columns that is flexible based on the size of the grid. For example, if our grid is only 200px wide, we may only want one column. If it’s 400px wide, we may want two, and so on. Solving this problem with media queries would be a lot of typing. Thankfully, auto-fit and auto-fill are here to save the day!

According to the W3 specification on auto-fill and auto-fit, both of these functions will return “the largest possible positive integer” without the grid items overflowing their container. Here is a simple example:

```css
.simple-example {
  display: grid;
  width: 1000px;
  grid-template-columns: repeat(auto-fit, 200px);
}
```

For this grid, we have a set width of 1000px and we are telling it to fill in our columns with tracks of 200px each. As long as there are at least five grid items, this will result in a 5-column layout no matter what. In this case, auto-fill would actually do the same thing. We will get into the difference soon.

The real magic of auto-fit and auto-fill comes when we incorporate minmax() into the equation. With minmax(), we can tell our grid that we want to have as many columns as possible, using the constraints of our minmax() function to determine each column’s size, without it overflowing our grid. 

```css
.grid-container {
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
}
```

#### What about auto-fill?
In most cases, auto-fill is going to work exactly the same way as auto-fit. The difference is only noticeable when there are fewer items than can fill up the entirety of the grid row once. When the grid is expanded to a size where another grid item could fit, but there aren’t any left, auto-fit will keep the grid items at their max size. Using auto-fill, the grid items will snap back down to their min size once the space becomes available to add another grid item, even if there isn’t one to be rendered. They will continue their pattern of growing to max and snapping back to their min as the grid expands and more room becomes available for new grid tracks.

---
### Knowledge Check

**Q1.** How do you create several grid tracks of the same size without manually typing each one out?

**A1.** We can achieve this with the `repeat()` notation. Example:<br> 
```css
.contaner {
  display: grid;
  grid-template-columns: repeat(7, 200px);
}
```

**Q2.** What is the difference between a static and dynamic size value?

**A2.** In regarding to grid, a static value is a value that is fixed in size such as "px". A dynamic value is a value that is responsive to the avaliable space in the viewport, making the grid item smaller or bigger in size dynamically as the avaliable space changes. An example to the dynamic size value would be the "fr" value.

**Q3.** How can you assign a grid track a flexible value that changes depending on the remaining space available in the grid?

**A3.** We can use the "fr" value to achieve this. Example:<br>
```css
.container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
```

**Q4.** How can you assign grid tracks an uneven distribution of the remaining space in a grid?

**A4.** To achieve this, we can give our grid tracks varying "fr" values. Example:<br>
```css
.container {
  display: grid;
  grid-template-rows: 1fr 2fr 5fr;
}
```

**Q5.** Which CSS functions will return the smallest or largest value supplied to them?

**A5.** `min()` function returns the smallest value that is supplied to the function, effectively assigning a "maximum" allowed value to the property. `max()` function on the other hand, will return the largest value supplied to the function, effectively assigning a "minimum" allowed value to the property. These two CSS functions can be used on any CSS property which allows numeric values, not just grid properties.

**Q6.** Which CSS Grid-only function allows you to supply a minimum and maximum track size that is calculated in realtime?

**A6.** The `minmax()` function is only avaliable in CSS Grid spesification and this function allows us to assign minimum and maximum allowed track sizes to our grid tracks. An example of the usage:<br>
```css
.container {
  display: grid;
  grid-template-columns: repeat(5, minmax(200px, 1fr));
}
```

In the above code snippet, we give our column tracks a minimum of 200px value while they are 1fr a column, at maximum.

**Q7.** Which global CSS function allows you to supply a minimum, ideal, and maximum value that is calculated in realtime?

**A7.** The `clamp()` function is avaliable to achieve this. Example:<br>
```css
.container {
  display: grid;
  grid-template-rows: 200px 1fr 3rem clamp(100px, 200px, 300px);
}
```

In the above code snippet we create 4 rows tracks. The rightmost row track's value is defined with clamp() function. `clamp(100px, 200px, 300px)` means that that row track will have a 100px value as minimum and 300px as maximum, meanwhile it's ideal value will be 200px. The `clamp()` function is avaliable in CSS globally, not just in Grid.

**Q8.** What attribute of repeat() can be used to fill in as many grid tracks as possible, given certain constraints?

**A8.** We can create responsive grids that will create or remove tracks as the avaliable space changes, without using any media-queries. To achieve this we can use the `repeat()` function along with `auto-fit` or `auto-fill` keywords that are avaliable in CSS Grid spesification.Example:<br>
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

What the above `repeat(auto-fit, minmax(200px, 1fr));` function is going to do is that, the browser will automatically create a column with a minimum width of 200px, and if the avaliable space is greater than that, created column will grow in size until the point where it's possible to include another 200px column in the avaliable space. Then the browser will create another 200px column and it will continue this behaviour until there is no more avaliable space. `auto-fit` will stretch grid-items to occupy avaliable space, while `auto-fill` will create new columns, when space is available, even if those columns are empty(do not contain any grid items.) These columns created by this function, will be in explicid grid.

**Q9.** What is the difference between auto-fit and auto-fill?

**A9.** As answered above, `auto-fit` stretches grid-items as the avaliable space increases and there are no more avaliable grid-items to place, while `auto-fill` will create new columns when it's possible, even if those columns do not contain any grid items.