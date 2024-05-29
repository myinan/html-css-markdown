# Advanced Selectors

**[Advanced Selectors Explained](https://learn.shayhowe.com/advanced-html-css/complex-selectors/ "Advanced Selectors")**

## Combinator selectors
In CSS, combinators are used to define relationships between different HTML elements when selecting them for styling. There are several combinators available in CSS, each serving a specific purpose. Here are the main CSS combinators:

### 1. **Descendant combinator (space) - ` `:**
   - Selects all elements that are descendants of a specified element, regardless of how deeply nested they are.
   - Example: `div p` selects all `<p>` elements that are descendants of `<div>` elements.

### 2. **Child combinator (>) - `>`:**
   - Selects all elements that are a direct child of a specified element.
   - Example: `ul > li` selects all `<li>` elements that are direct children of `<ul>` elements.

### 3. **Adjacent sibling combinator (+):**
   - Selects an element that is immediately preceded by a specified element.
   - Example: `h2 + p` selects the `<p>` element that directly follows an `<h2>` element.

### 4. **General sibling combinator (~):**
   - Selects all elements that are siblings of a specified element, sharing the same parent, and appearing after the specified element.
   - Example: `h2 ~ p` selects all `<p>` elements that are siblings of an `<h2>` element with the same parent.

## Pseudo-selectors
### 1. Pseudo-class selectors:
In CSS, a pseudo-class is a special keyword that allows one to target and style elements based on their state or position in the HTML document. Pseudo-classes are preceded by a colon (:) and are used to define styles for elements that cannot be targeted with simple element selectors (e.g., `div`, `p`, `a`). Pseudo-classes add interactivity and dynamic behavior to web pages by selecting elements based on user interactions or other conditions.

Pseudo-classes are an essential part of creating responsive and interactive web designs. They are commonly used for styling links, targeting form elements, creating hover effects, and more. Let's delve into the details of pseudo-classes in CSS:

**Syntax:**
   Pseudo-classes are added to the end of a CSS selector, following the colon (:). Here's the basic syntax:

   ```css
   selector:pseudo-class {
       /* CSS properties and values */
   }
   ```

**Common Pseudo-classes:**

   - **:hover**: Used to style an element when the mouse cursor is placed over it. For example, we can change the color of a button when a user hovers over it.

   ```css
   button:hover {
       background-color: #FF5733;
   }
   ```

   - **:active**: Targets an element while it is being activated, such as when a button is clicked.

   ```css
   button:active {
       background-color: #3366FF;
   }
   ```

   - **:focus**: Styles an element when it receives focus, typically used for form inputs. It's useful for providing visual feedback to users when they interact with a form.

   ```css
   input:focus {
       border-color: #00FF00;
   }
   ```

   - **:nth-child()**: Selects elements based on their position within a parent element. We can specify numerical values or formulas to target specific child elements.

   ```css
   ul li:nth-child(odd) {
       background-color: #EFEFEF;
   }
   ```

   - **:not()**: Selects elements that do not match a specified selector. This can be useful when we want to exclude certain elements from styling.

   ```css
   p:not(.special) {
       font-style: italic;
   }
   ```

   - **:first-child** and **:last-child**: Target the first and last child elements of a parent element.

   ```css
   li:first-child {
       font-weight: bold;
   }

   li:last-child {
       font-style: italic;
   }
   ```

   - **:nth-of-type()**: Similar to `:nth-child()`, but it selects elements based on their type (e.g., `div`, `p`, `span`) within a parent element.

   ```css
   div:nth-of-type(2n) {
       background-color: #FFFF99;
   }
   ```

**Pseudo-classes and Link Styling:**

   Pseudo-classes are commonly used to style links in web pages. There are several link-related pseudo-classes:

   - **:link**: Styles unvisited links.
   - **:visited**: Styles visited links.
   - **:hover**: Styles links when hovered.
   - **:active**: Styles links when clicked.

   ```css
   a:link {
       color: #3366CC;
   }

   a:visited {
       color: #6633CC;
   }

   a:hover {
       text-decoration: underline;
   }

   a:active {
       color: #FF0000;
   }
   ```

**Combining Pseudo-classes:**

   We can combine multiple pseudo-classes in a single selector to create more specific and complex styles.

   ```css
   button:hover:active {
       background-color: #FF0000;
   }
   ```

**Browser Compatibility:**

   It's important to note that browser support for pseudo-classes can vary, especially when dealing with older browsers. Always check compatibility or provide alternative styles for unsupported browsers if necessary.

**[MDN Docs Pseudo-class selectors complete reference page](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)**

Note: The difference between the `:root` pseudo-class selector and the `html` tag: 1- `:root`, being a pseudo-class, has a higher spesificity than the `html` tag, 2- CSS is used to style "structured documents", so it's not only used to style HTML documents but also SVG AND XHTML documents, for example. That is the reason why a seperate pseudo-class `:root` exist to target the root element of a document that is being styled.

### 2. Pseudo-element selectors:
Pseudo-element selectors in CSS are used to target and style specific parts of an HTML element's content or layout that cannot be targeted with regular class or ID selectors. They allow you to create and apply styles to elements that do not exist in the HTML markup but are generated by the browser or are part of the element's intrinsic structure. Pseudo-elements are denoted by a double colon (::) followed by a keyword that represents the specific part of the element you want to style.

Here's an in-depth explanation of pseudo-element selectors in CSS:

1. **Syntax**: Pseudo-elements are written using a double colon (::) followed by the keyword representing the pseudo-element. In practice, a single colon (:) can also be used, but it's recommended to use the double colon (::) to avoid potential conflicts with pseudo-classes (such as `:hover`).

2. **Common Pseudo-elements**:
   - `::before`: This pseudo-element allows you to insert content before the content of the selected element. It's often used for decorative purposes or to add icons or labels before an element's content.
   - `::after`: Similar to `::before`, this pseudo-element inserts content after the selected element's content.
   - `::first-line`: This pseudo-element targets the first line of text within an element. It's commonly used to style the initial line of text in paragraphs or headings.
   - `::first-letter`: This pseudo-element targets the first letter of text within an element, making it useful for creating drop caps or applying special styling to the first letter of a paragraph.
   - `::selection`: This pseudo-element allows you to style the portion of text that a user has selected with their cursor.

3. **Targeting Elements**: Pseudo-elements are typically applied to specific HTML elements using the element's selector followed by the pseudo-element. For example:

   ```css
   p::first-line {
     font-weight: bold;
   }
   ```

   In this example, the `::first-line` pseudo-element is used to target the first line of text within all `<p>` elements.

4. **Content Insertion**: The `::before` and `::after` pseudo-elements are commonly used for inserting content into an element. You can specify the content to be inserted using the `content` property. For example:

   ```css
   p::before {
     content: "★ ";
   }
   ```

   This code will insert a star (★) before the content of all `<p>` elements.

   The use of the `::before` and `::after` pseudo-elements along with the `content` property is referred to as "Generated Content" in CSS, and we can often see this technique being used for various tasks on the web.

5. **Styling**: You can apply various CSS properties to pseudo-elements just like you would with regular elements. This includes properties for text formatting, positioning, background, border, and more.

6. **Inheritance**: Pseudo-elements inherit some properties from their parent elements, while others are not inherited. It's important to be aware of the inheritance behavior when styling pseudo-elements.

7. **Compatibility**: Pseudo-elements are supported in modern web browsers and have been part of CSS for a long time. However, it's essential to consider browser compatibility when using more advanced or less common pseudo-elements.

8. **Use Cases**: Pseudo-elements are useful for adding decorative elements, icons, or labels to your content, as well as for fine-tuning the styling of specific parts of text, such as the first line or letter. They are especially valuable for creating aesthetically pleasing designs and improving the user experience.

**[MDN Docs Pseudo-element selectors complete reference page](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)**

## Attribute selectors
Attribute selectors in CSS allow you to target HTML elements based on the presence of specific attributes and their values. They are a powerful tool for styling and selecting elements in your web pages. Attribute selectors are enclosed in square brackets and consist of three main parts:

1. Attribute name: The name of the HTML attribute you want to target.

2. Operator: The operator defines the relationship between the attribute and the value you want to match. There are different operators available, including:

   - `[attr]`: Selects elements that have the specified attribute, regardless of its value.
   - `[attr=value]`: Selects elements that have the specified attribute with an exact matching value.
   - `[attr~=value]`: Selects elements that have the specified attribute with a value containing the given word.
   - `[attr|=value]`: Selects elements that have the specified attribute with a value starting with the specified string, followed by a hyphen.
   - `[attr^=value]`: Selects elements that have the specified attribute with a value that starts with the specified string.
   - `[attr$=value]`: Selects elements that have the specified attribute with a value that ends with the specified string.
   - `[attr*=value]`: Selects elements that have the specified attribute with a value containing the specified substring.

3. Attribute value: The value you want to match against the attribute. This can be a specific value, word, substring, or a pattern depending on the operator used.

Here's a detailed explanation and examples for each of the operators:

### 1. `[attr]` - Select elements with a specific attribute:

This selector targets elements that have a specified attribute, regardless of its value. For example:
```css
input[type] {
  border: 1px solid #ccc;
}
```
In this example, all `input` elements with any type attribute will have a gray border.

### 2. `[attr=value]` - Select elements with a specific attribute value:

This selector targets elements that have a specified attribute with an exact matching value. For example:
```css
a[href="https://www.example.com"] {
  color: blue;
}
```
This rule selects all anchor (`<a>`) elements with an `href` attribute equal to "https://www.example.com" and sets their text color to blue.

### 3. `[attr~=value]` - Select elements with a specific attribute value containing a word:

This selector targets elements that have an attribute with a value containing the specified word. For example:
```css
[data-tags~="important"] {
  font-weight: bold;
}
```
Here, elements with a `data-tags` attribute containing the word "important" (e.g., `data-tags="urgent important"`) will have their text set to bold.

### 4. `[attr|=value]` - Select elements with a specific attribute value starting with a string:

This selector targets elements that have an attribute with a value that starts with the specified string followed by a hyphen. For example:
```css
[lang|="en"] {
  color: blue;
}
```
This rule selects elements with a `lang` attribute starting with "en" (e.g., `lang="en-US"`) and changes their text color to blue.

### 5. `[attr^=value]` - Select elements with a specific attribute value starting with a string:

This selector targets elements that have an attribute with a value that starts with the specified string. For example:
```css
[src^="https://cdn.example.com"] {
  border: 2px solid green;
}
```
This rule selects elements with a `src` attribute starting with "https://cdn.example.com" and adds a green border to them.

### 6. `[attr$=value]` - Select elements with a specific attribute value ending with a string:

This selector targets elements that have an attribute with a value that ends with the specified string. For example:
```css
[href$=".pdf"] {
  background-color: yellow;
}
```
This rule selects anchor elements with an `href` attribute ending with ".pdf" and sets their background color to yellow.

### 7. `[attr*=value]` - Select elements with a specific attribute value containing a substring:

This selector targets elements that have an attribute with a value containing the specified substring. For example:
```css
[data-username*="john"] {
  text-decoration: underline;
}
```
This rule selects elements with a `data-username` attribute containing "john" anywhere within the value and underlines their text.

In summary, attribute selectors in CSS provide a versatile way to target and style elements based on their attributes and attribute values. They are particularly useful for applying styles to specific elements with certain attributes, making your CSS more dynamic and adaptable to different situations on your web pages.

---
### Knowledge Check

**Q1.** What is the difference between the child combinator and the descendant combinator?

**A1.** Child combinator (>)(eg: article>p) selects the direct children of an element, while the descendant combinator ([space]) (eg: div p) selects all the children of that particular element whether they are a direct children or not.

**Q2.** How does the syntax of pseudo-classes and pseudo-elements differ?

**A2.** pseudo-classes are prefixed with `:` while pseudo-elements are prefixed with `::` though `:` for pseudo-elements are still supported by browsers (except for the ::selection pseudo-element) for continuity reasons.

**Q3.** Do pseudo-classes exist somewhere in HTML? Do pseudo-elements?

**A3.** Pseudo-classes and pseudo-elements do not exist in the HTML markup.

**Q4.** Name two ways you could select every second child of an element, starting with the first.

**A4.** 1- We could use the `nth-child(n)` pseudo-class selector with a formula: `parent>child:nth-child(2n+1)` OR 2- We could use the `nth-child(n)` psuedo-class selector with the keyword "even": `parent>child:nth-child(even)`.

**Q5.** What is the difference between div:first-child and div:last-child? What will each select?

**A5.** `div:first-child` will select the first child of the parent div while `div:last-child` will select the last child of the parent div.

**Q6.** What selector would you use to style a button a user is currently hovering over? How about one that is currently being clicked on?

**A6.** To style a button that is currently being hovered over we would use the `button:hover` pseudo-class selector, while to style a button that is being clicked on we would use the `button:active` pseudo-class selector.

**Q7.** How could you select all input elements with a type of text?

**A7.** In order to select all input elements with a type of text we would use the following selector: `input[type="text"]`.

**Q8.** How could you select all classes that begin with thunder?

**A8.** In order to select all classes that begin with thunder we would use the following selector: `[class^="thunder"]`.
