# Alignment

## justify-content

`justify-content` property positions items across the main axis. The default value for `justify-content` is `flex-start` `(justify-content: flex-start;)`.

## align-items

`align-items` property positions items across the cross axis. The default value for `align-items` is `stretch` `(align-items: stretch;)`.

## align-self
Unlike justify-content and align-items, `align-self` is applied to the **child element**, not the container. It allows us to change the alignment of a specific child along the cross axis.

## gap
One very useful feature of flex is the `gap` property. Setting gap on a flex container simply adds a specified space between flex items, similar to adding a margin to the items themselves. gap is a new property so it doesn’t show up in many resources yet, but it works reliably in all modern browsers, so it is safe to use and very handy!

## flex-wrap: wrap
When we set `flex-wrap: wrap`, items won't shrink below their hypothetical size. At least, not when wrapping onto the next row/column is an option!

With flex-wrap: wrap, we no longer have a single primary axis line that can skewer each item. Effectively, each row acts as its own mini flex container.

But then, How does `align-items` work, now that we have multiple rows? The cross axis could intersect multiple items now! In that case, we should think of each row as its own mini Flexbox environment. align-items will move each item up or down within the invisible box that wraps around each row.

But what if we want to **align the rows themselves**? We can do that with the `align-content` property.

# Typical use cases of flexbox

## Navigation
A common pattern for navigation is to have a list of items displayed as a horizontal bar. This pattern, as basic as it seems, was difficult to achieve before flexbox. It forms the most simple of flexbox examples, and could be considered the ideal flexbox use case.

When we have a set of items that we want to display horizontally, we may well end up with additional space. We need to decide what to do with that space, and have a couple of options. We either display the space outside of the items — therefore spacing them out with white space between or around them — (`justify-content`) or we absorb the extra space inside the items and therefore need a method of allowing the items to grow and take up this space (`flex-grow/shrink/basis`).

**Split Navigation**: A useful way to align items on the main axis is to use **auto margins**. This enables the design pattern of a navigation bar where one group of items are aligned left and another group aligned right. 

The items are aligned on the main axis with flex-start as this is the initial behavior of flexbox. The gap property can be used to create gaps between items. And,for example, we can align the last item to the right by giving it a left margin of auto.

## Center item
Before flexbox, developers would joke that the hardest problem in web design was vertical centering. This has now been made straightforward using the alignment properties in flexbox.

```
.flex-container {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

In the future we may not need to make a container a flex container just to center a single item, as the Box Alignment properties will ultimately be implemented in Block layout. For now however, if you need to properly center one thing inside another, flexbox is the way to do it.

## Card layout pushing footer down
Whether you use flexbox or CSS Grid to lay out a list of card components, these layout methods only work on direct children of the flex or grid component. This means that if you have variable amounts of content, the card will stretch to the height of the grid area or flex container. Any content inside uses regular block layout, meaning that on a card with less content the footer will rise up to the bottom of the content rather than stick to the bottom of the card.

Flexbox can solve this. We make the card a flex container, with flex-direction: column. We then set the content area to flex: 1, which is the shorthand for flex: 1 1 0 — the item can grow and shrink from a flex basis of 0. As this is the only item that can grow, it takes up all available space in the flex container and pushes the footer to the bottom. 

## Media objects
The media object is a common pattern in web design — this pattern has an image or other element to one side and text to the right. Ideally a media object should be able to be flipped — moving the image from left to right.

We see this pattern everywhere, used for comments, and anywhere we need to display images and descriptions. With flexbox we can, for example, allow the part of the media object containing the image to take its sizing information from the image, and then the body of the media object flexes to take up the remaining space.

### Flipping the media object
To switch the display of the media object so that the image is on the right and the content is on the left we can use the flex-direction property set to row-reverse.

## Form controls
Flexbox is particularly useful when it comes to styling form controls. Forms have lots of markup and lots of small elements that we typically want to align with each other. A common pattern is to have an \<input> element paired with a \<button>, perhaps for a search form or where you want your visitor to enter an email address.

Flexbox makes this type of layout easy to achieve.

![Flexbox Form](../../../img/flexbox-form.png "Flexbox Form")

---

## Flex and grid — what's the difference?
A common question is to ask what the difference is between Flexbox and CSS Grid Layout — why do we have two specifications that sometimes appear to be doing the same thing?

The most straightforward answer to this question is defined in the specifications themselves. Flexbox is a one-dimensional layout method whereas Grid Layout is a two-dimensional layout method.

Flex items can be allowed to wrap but, once they do so, each line becomes a flex container of its own. When space is distributed flexbox does not look at the placement of items in other rows and tries to line things up with each other. If we create a similar layout using Grid, we can control the layout in both rows and columns.

Also , in Grid Layout you do the majority of sizing specification on the container, setting up tracks and then placing items into them. In flexbox, while you create a flex container and set the direction at that level, any control over item sizing needs to happen on the items themselves.

In some cases you could happily use either layout method, but as you become confident with both you will find each one suiting different layout needs, and you will end up with both methods in your CSS. There is rarely a right or wrong answer.

As a ground rule, if you are adding widths to flex items in order to make items in one row of a wrapped flex container line up with the items above them you really want two-dimensional layout. In this case it is likely that the component would be better laid out using CSS Grid Layout. It isn't the case that you should use flexbox for small components and grid layout for larger ones; a tiny component can be two dimensional, and a large layout can be represented better with layout in one dimension.

---

**odin-css-exercises-fork/flex --) all practices (1-7) are completed.**

---

### Knowledge Check

**Q1.** What is the difference between justify-content and align-items?

**A1.** `justify-content` positions flex-items on the main axis, while `align-items` positions flex-items on the cross-axis.

**Q2.** How do you use flexbox to completely center a div inside a flex container?

**A2.** In order to completely center a flex-item inside a flex-container we can use the following css on the flex-container:
```
.flex-container {
  justify-content: center;
  align-items: center;
}
```

**Q3.** What’s the difference between justify-content: space-between and justify-content: space-around?

**A3.** `justify-content: space-between` distributes the available space in the flex-container between the flex-items, effectively creating gaps between the items. Items at the edges will sit at the border (if there are no margin or padding values declared).

`justify-content: space-around` on the other hand while creating spaces between items, also puts space between the border and the item most close to it.

