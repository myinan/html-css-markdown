# Growing and Shrinking

![Flex property](../../../img/flex-property.png "Flex property")

What actually happens when you put flex: 1 on a flex item?

## The "flex" Shorthand
The defining aspect of flex layout is the ability to make the flex items “flex”, altering their width/height to fill the available space in the main dimension. This is done with the flex property. A flex container distributes free space to its items (proportional to their flex grow factor) to fill the container, or shrinks them (proportional to their flex shrink factor) to prevent overflow.

A flex item is fully inflexible if both its flex-grow and flex-shrink values are zero, and flexible otherwise.

The `flex` property is actually a shorthand for 3 properties that you can set on a flex item. These properties affect how flex items size themselves within their container.

> Shorthand properties are CSS properties that let you set the values of multiple other CSS properties simultaneously. Using a shorthand property, you can write more concise (and often more readable) stylesheets, saving time and energy. For example, the different margins around a box can be defined using the margin shorthand.

In our case, `flex` is actually a shorthand for `flex-grow`, `flex-shrink` and `flex-basis`.

In the above screenshot, `flex: 1` equates to: `flex-grow: 1`, `flex-shrink: 1`, `flex-basis: 0`.

Very often you see the flex shorthand defined with only one value. In that case, that value is applied to flex-grow. So when we put `flex: 1` on our div, we are actually specifying a shorthand of `flex: 1 1 0`.

### flex-grow
`flex-grow` expects a single number as its value, and that number is used as the flex-item’s “growth factor”. When we apply flex: 1 to every div inside our container, we are telling every div to grow the same amount. The result of this is that every div ends up the exact same size. If we instead add flex: 2 to just one of the divs, then that div would grow to 2x the size of the others.

### flex-shrink
flex-shrink is similar to flex-grow, but sets the “shrink factor” of a flex item. flex-shrink only ends up being applied if the size of all flex items is larger than their parent container. For example, if 3 divs inside a .flex-container had a width declaration like: width: 100px, and .flex-container was smaller than 300px, our divs would have to shrink to fit.

The default shrink factor is flex-shrink: 1, which means all items will shrink evenly. If you do not want an item to shrink then you can specify flex-shrink: 0;. You can also specify higher numbers to make certain items shrink at a higher rate than normal.

An important caveat is that when you specify flex-grow or flex-shrink, flex items do not necessarily respect your given values for width. If all 3 divs in our previous example are given a width of 250px, if their parent is big enough, they will grow to fill it. Likewise, when the parent is too small, the default behavior is for them to shrink to fit. This is not a bug, but it could be confusing behavior if you aren’t expecting it.

>Note: The flex shrink factor is multiplied by the flex base size when distributing negative space. This distributes negative space in proportion to how much the item is able to shrink, so that e.g. a small item won’t shrink to zero before a larger item has been noticeably reduced.

### flex-basis
flex-basis simply sets the initial size of a flex item, so any sort of flex-growing or flex-shrinking starts from that baseline size. The shorthand value defaults to flex-basis: 0%.

Using `auto` as a flex-basis tells the item to check for a width declaration.

>Important Note About Flex-Basis:
There is a difference between the default value of flex-basis and the way the flex shorthand defines it if no flex-basis is given. The actual default value for flex-basis is auto, but when you specify flex: 1 on an element, it interprets that as flex: 1 1 0. If you want to only adjust an item’s flex-grow you can simply do so directly, without the shorthand. Or you can be more verbose and use the full 3 value shorthand flex: 1 1 auto, which is also equivalent to using flex: auto.

>What is flex: auto?
If you noticed, we mentioned a new flex shorthand flex: auto in the previous note. However we didn’t fully introduce it. flex: auto is one of the shorthands of flex. When auto is defined as a flex keyword it is equivalent to the values of flex-grow: 1, flex-shrink: 1 and flex-basis: auto or to flex: 1 1 auto using the flex shorthand. Note that flex: auto is not the default value when using the flex shorthand despite the name being “auto” which may be slightly confusing at first.

## flex property syntax

```
/* Keyword values */
flex: auto;
flex: initial;
flex: none;

/* One value, unitless number: flex-grow
flex-basis is then equal to 0. */
flex: 2;

/* One value, width/height: flex-basis */
flex: 10em;
flex: 30%;
flex: min-content;

/* Two values: flex-grow | flex-basis */
flex: 1 30px;

/* Two values: flex-grow | flex-shrink */
flex: 2 2;

/* Three values: flex-grow | flex-shrink | flex-basis */
flex: 2 2 10%;

/* Global values */
flex: inherit;
flex: initial;
flex: revert;
flex: revert-layer;
flex: unset;
```
> Authors are encouraged to control flexibility using the flex shorthand rather than with flex-longhands directly.

### Values

`initial`: The item is sized according to its width and height properties. It shrinks to its minimum size to fit the container, but does not grow to absorb any extra free space in the flex container. This is equivalent to setting "flex: 0 1 auto".

`auto`: The item is sized according to its width and height properties, but grows to absorb any extra free space in the flex container, and shrinks to its minimum size to fit the container. This is equivalent to setting "flex: 1 1 auto".

`none`: The item is sized according to its width and height properties. It is fully inflexible: it neither shrinks nor grows in relation to the flex container. This is equivalent to setting "flex: 0 0 auto".

> For most purposes, authors should set flex to one of the following values: auto, initial, none, or a positive unitless number.

---

### Knowledge Check

**Q1.** What are the 3 values defined in the shorthand flex property (e.g. flex: 1 1 auto)?

**A1.** Shorthand "flex" property actually defines 3 different properties. These properties are "flex-grow", "flex-shrink", and "flex-basis". "flex-grow" longhad property defines the grow rate of the flex-item relative to other flex-items in the flex-container. "flex-shrink" works the same but for shrinking items. "flex-basis" sets the basis width value for the flex-item. In our example "flex: 1 1 auto", we actually define "flex-grow" to 1, "flex-shrink" to 1 and "flex-basis" to auto (which means that flex-basis property will look for the defined height and width values for the flex-item.).

**Q2.** What are the 3 defined values for the flex shorthand flex:auto?

**A2.** "flex: auto" shorthand defines "flex-grow" to 1, "flex-shrink" to 1 and "flex-basis" to auto.
