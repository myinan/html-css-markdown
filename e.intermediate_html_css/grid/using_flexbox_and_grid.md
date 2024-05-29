# Using Flexbox and Grid
Some may tell you there is a debate on the use of Grid vs. Flexbox and whether or not one is superior to the other. The reality is much simpler - these are complementary tools that can work together, and each has its own place in the world of CSS.

## Content first vs layout first design
A way to decide between Grid and Flexbox is to consider if your design starts from the content, or from the layout.

In Content First Design, you begin with clarity of how the content should be, and the layout follows. This is a great opportunity to use Flexbox. Its flexible nature gives you control of the behavior of items through logical rules. How they grow, shrink, their ideal size and position in relation to each other, all make the layout dynamic. While Flexbox gives you control over its content, the final layout is only a consequence. Depending on the dimensions of the flex container, the general layout can change a lot.

In Layout First Design, you decide how you want the pieces arranged, then fill in the content. That is when Grid shines. Defining grid row and column tracks gives you full control of layout. Content in a grid can only fill the spaces of explicit or implicit tracks. So, when you have an idea of how the big picture of a container should look like, Grid is the clear choice.

## Combining flexbox and grid
If you have one-dimensional content, Flexbox can make it easier to control how that content is positioned in a Flex container. If, on the other hand, you want to accurately place content on a complex layout in two-dimensions, Grid can be simpler to use.

Say you want your overall layout to be a grid, but you want the grid items to act as flex parents. This way, the grid items can be moved around using the precise two-dimensional placement Grid allows for, while also allowing the content inside the grid items to be capable of freely moving around using Flex.

---
### Questions when deciding which to use: grid or flexbox?:
1.a- **Do I only need to control the layout by row OR column?** – use Flexbox.<br>
1.b- **Do I need to control the layout by row AND column?** – use Grid.<br>

2.a- **Content first design?** – Use Flexbox. Flexbox works from the content out. You let the size of the content decide how much individual space each item takes up.<br>
2.b- **Layout first design?** – Use Grid. Grid works from the layout in. When you use CSS Grid Layout you create a layout and then you place items into it, or you allow the auto-placement rules to place the items into the grid cells according to that strict grid.

**REMEMBER**, you can always use flexbox and grid, or other layout methods, together. These layout methods are not exclusive to each other.

---
### `display: contents;` property
**display: contents** causes an element's children to appear as if they were direct children of the element's parent, ignoring the element itself. This can be useful when a wrapper element should be ignored when using CSS grid or CSS flexbox, as this property is available for both layout methods(though browser support is still lacking for `display: contents`).

---

### Knowledge Check

**Q1.** When might you use Flexbox over Grid?

**A1.** If we only need to control the layout by row OR column, or we have a "content first" design approach; we should use flexbox.

**Q2.** When might you use Grid over Flexbox?

**A2.** If we need to control the layout by row AND column, or we have a "layout first" design approach; we should use grid.

**Q3.** When might you use the two of these tools together?

**A3.** If we have one-dimensional content, Flexbox can make it easier to control how that content is positioned in a Flex container. If, on the other hand, we want to accurately place content on a complex layout in two-dimensions, Grid can be simpler to use.

Say, we want our overall layout to be a grid, but we want the grid items to act as flex parents. This way, the grid items can be moved around using the precise two-dimensional placement Grid allows for, while also allowing the content inside the grid items to be capable of freely moving around using Flex.