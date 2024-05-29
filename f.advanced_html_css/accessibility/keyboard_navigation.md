# Keyboard Navigation
Some users aren’t able to use a mouse to navigate or operate their computer, and by extension the websites they visit. These users may instead rely on using a keyboard or another assistive technology that can simulate keyboard inputs, such as voice recognition software. Other users may even just prefer using a keyboard over a mouse, or may use a mix of both. These users require proper keyboard navigation, something that can easily be overlooked when developing a website.

## Focusability and Event Handling for Keyboard
For keyboard users, interactive elements must have two essential characteristics:

1. **Focusability**: Interactive elements should be focusable using keyboard navigation. This means users should be able to tab through the interactive elements on a webpage using the Tab key or another appropriate keyboard shortcut.

2. **Event handling**: Interactive elements should have event handling for keyboard interactions. This ensures that keyboard users can trigger actions associated with the interactive element using keyboard events, such as pressing Enter or Spacebar. For example, pressing Enter or Spacebar on a focused button should trigger its associated action, such as clicking the button or submitting a form.

Ensuring both focusability and event handling for keyboard users is crucial for making web content accessible and usable for individuals who rely on keyboard navigation due to motor disabilities or other accessibility needs.

From the accessibility perspective, an another issue with using `<div>` and `<span>` elements is that, by default, they aren’t **focusable** and they don’t have any **event handling** by default. For example, in order to fix non-semantic code for keyboard users, we would need to take some extra steps, similar to the below code snippet:

```html
<!-- The `tabindex` attribute makes the `<div>` elements focusable. -->
<div class='button-container'>
  <div class='rock button' tabindex='0'>Rock</div>
  <div class='paper button' tabindex='0'>Paper</div>
  <div class='scissors button' tabindex='0'>Scissors</div>
</div>
```

```js
// We also need to manually add in event handling for both mouse and keyboard events.
const buttons = document.querySelectorAll('.button');

function nameAlerter(e) {
  if (e.type === 'click' || e.key === ' ' || e.key === 'Enter') {
    alert(e.target.textContent);
  }
}

buttons.forEach(button => {
  button.addEventListener('click', nameAlerter)
  button.addEventListener('keydown', nameAlerter)
})
```

Of course, this example then makes it less understandable for screen reader users (remember, these “buttons” won’t provide any context). Instead, not only does using the `<button>` element provide the context screen reader users need, but **they’re focusable and have event handling for keyboards by default:** pressing the Space or Enter keys on a keyboard when a `<button>` has focus will trigger the “click” event.

The point is that you need to make sure that any interactive elements are focusable by and have event handling for keyboards. Using the correct semantic HTML can make this a lot easier of a goal to accomplish, but if you ever need to use an element that isn’t focusable or doesn’t have any event handling by default, then you need to add both of those functionalities in manually.

## Focus Styles
Another aspect of focusable elements is their focus styles, which are usually an outline or border surrounding the element when it receives focus. One of the things you may have done, or may still do, is completely remove these focus styles by using CSS rules similar to the example below:

```css
*:focus {
  outline: none;
  border: none;
}
```

You probably assume that you’re about to be told not to do this. Well… **You should never completely remove focus styles**. You should either leave these default focus styles alone, or you should replace them with your own focus styles. Whether it’s adding a `transform: scale()` CSS property to a button, adding an outline to a link, or increasing the border width and opacity on an input, adding your own focus styles is the only alternative you should consider to the default focus styles.

Why? Completely removing focus styles can make a page impossible for keyboard users to navigate and operate, as they have no visual indication what element actually has focus. It would force them to have to manually keep track of how many times they’ve pressed the Tab key while also trying to guess what elements are actually focusable. Imagine trying to browse a website with an invisible cursor and without any visual indication of when the cursor was hovering over interactive elements like links or buttons. Doesn’t sound too fun, does it?

## Tab Order
Tab order refers to the sequence in which elements on a webpage receive keyboard focus when a user navigates through them using the Tab key on their keyboard. When a user presses the Tab key, the focus moves from one focusable element to the next in the tab order.

The tab order is determined by the document's source order by default, meaning elements are focused in the order they appear in the HTML code. However, the tab order can be modified using the `tabindex` attribute. Elements with a `tabindex` attribute are included in the tab order, and their order is determined by the values of the `tabindex` attribute:

- Elements with a `tabindex` value greater than 0 are placed at the beginning of the tab order, in ascending numerical order.
- Elements with a `tabindex` value of 0 are placed in the tab order based on their position in the document's source order.
- Elements with a `tabindex` value less than 0 are programmatically focusable but are not included in the tab order.

```html
<!-- This element is first in the tab order. -->
<div tabindex='0'>This is the first element listed in the HTML.</div>

<!-- This element is second in the tab order. -->
<div tabindex='0'>This is the second element listed in the HTML.</div>
```

It's important to note that while modifying the tab order can be useful for improving accessibility and usability, it should be done judiciously to avoid confusing users. In most cases, relying on the default tab order based on the document structure is sufficient for providing a logical and intuitive navigation experience for keyboard users.

## Hidden Content
Sometimes you may want to hide some content until a specific event occurs, such as a user clicking on a button to open a menu or a modal box. When you want to hide content for this sort of purpose, you need to make sure the content is not only visually hidden, but also hidden from assistive technologies until that content is meant to be visible.

If you don’t properly hide such content, then keyboard users would be able to tab into that content before they’re meant to, but in doing so they would lose track of any visual focus on the page. These users would be left confused or even frustrated when they’re trying to tab through a page, only for their focus indicator to disappear into that hidden content.

One way to prevent this frustrating behavior is to give each individual item in that hidden content a tabindex value of -1, since that prevents an element from receiving focus via the keyboard (though you can still give it focus with JavaScript’s focus() method). While this fixes the issue for keyboard users, other assistive technologies would still have access to and could still announce this hidden content.

A better solution is giving the container for the hidden content itself either the display: none or visibility: hidden CSS property when it’s hidden, and removing or overriding that property when it’s meant to be visible. This not only removes the menu items from the tab order, but it also prevents assistive technologies from announcing them.

## WCAG and Web Content Accessibility with Keyboard
WCAG sets spesific rules regarding the topics we have discussed so far in **WCAG Principle 2 – Operable (User interface components and navigation must be operable.)**

---
### Knowledge Check

**Q1.** What are two things that interactive elements must have for keyboard users?

**A1.** For keyboard users, interactive elements must have two essential characteristics:

1. **Focusability**: Interactive elements should be focusable using keyboard navigation. This means users should be able to tab through the interactive elements on a webpage using the Tab key or another appropriate keyboard shortcut.

2. **Event handling**: Interactive elements should have event handling for keyboard interactions. This ensures that keyboard users can trigger actions associated with the interactive element using keyboard events, such as pressing Enter or Spacebar. For example, pressing Enter or Spacebar on a focused button should trigger its associated action, such as clicking the button or submitting a form.

Ensuring both focusability and event handling for keyboard users is crucial for making web content accessible and usable for individuals who rely on keyboard navigation due to motor disabilities or other accessibility needs.

**Q2.** What are focus styles?

**A2.** "Focus styles" refer to the visual changes that occur when an element on a webpage gains focus. This typically happens when a user interacts with an element using the keyboard (e.g., tabbing through form fields) or when an element is selected with a mouse click.

Focus styles are crucial for accessibility because they help users who navigate the web using keyboard-only or assistive technologies to understand which element currently has keyboard focus. Without proper focus styles, it can be difficult for users to track their position on a webpage, leading to usability issues.

Focus styles often include changes in outline, border, or background color to visually highlight the focused element. Web developers need to ensure that these focus styles are sufficiently visible and distinct from surrounding elements to accommodate users with different visual impairments or preferences.

**Q3.** Why should you never completely remove focus styles from an element?

**A3.** **You should never completely remove focus styles**. You should either leave these default focus styles alone, or you should replace them with your own focus styles. Whether it’s adding a `transform: scale()` CSS property to a button, adding an outline to a link, or increasing the border width and opacity on an input, adding your own focus styles is the only alternative you should consider to the default focus styles.

Why? Completely removing focus styles can make a page impossible for keyboard users to navigate and operate, as they have no visual indication what element actually has focus. It would force them to have to manually keep track of how many times they’ve pressed the Tab key while also trying to guess what elements are actually focusable.

**Q4.** What is the tab order?

**A4.** Tab order refers to the sequence in which elements on a webpage receive keyboard focus when a user navigates through them using the Tab key on their keyboard. When a user presses the Tab key, the focus moves from one focusable element to the next in the tab order.

The tab order is determined by the document's source order by default, meaning elements are focused in the order they appear in the HTML code. However, the tab order can be modified using the `tabindex` attribute. Elements with a `tabindex` attribute are included in the tab order, and their order is determined by the values of the `tabindex` attribute:

- Elements with a `tabindex` value greater than 0 are placed at the beginning of the tab order, in ascending numerical order.
- Elements with a `tabindex` value of 0 are placed in the tab order based on their position in the document's source order.
- Elements with a `tabindex` value less than 0 are programmatically focusable but are not included in the tab order.

```html
<!-- This element is first in the tab order. -->
<div tabindex='0'>This is the first element listed in the HTML.</div>

<!-- This element is second in the tab order. -->
<div tabindex='0'>This is the second element listed in the HTML.</div>
```

It's important to note that while modifying the tab order can be useful for improving accessibility and usability, it should be done judiciously to avoid confusing users. In most cases, relying on the default tab order based on the document structure is sufficient for providing a logical and intuitive navigation experience for keyboard users.

**Q5.** What is the best way to hide hidden content from assistive technologies?

**A5.** A better solution is giving the container for the hidden content itself either the `display: none` or `visibility: hidden` CSS property when it’s hidden, and removing or overriding that property when it’s meant to be visible. This not only removes the menu items from the tab order, but it also prevents assistive technologies from announcing them.