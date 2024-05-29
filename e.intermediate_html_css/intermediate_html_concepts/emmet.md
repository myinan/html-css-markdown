# Emmet
Emmet is a powerful toolkit designed to enhance the speed and efficiency of web development, primarily focused on HTML and CSS workflows. It allows developers to write code using shorthand notations that can be expanded into fully-formed HTML and CSS structures. This significantly speeds up the process of writing repetitive and verbose code, enabling developers to be more productive and focus on higher-level tasks.

At its core, Emmet provides a set of abbreviations and syntax that can be used to generate complex HTML and CSS code quickly. The abbreviations are designed to be intuitive and easy to remember, often mimicking the structure and hierarchy of the resulting code. For example, typing `ul>li*3>a` and expanding it using Emmet would result in the following HTML code:

```html
<ul>
    <li><a href=""></a></li>
    <li><a href=""></a></li>
    <li><a href=""></a></li>
</ul>
```

Emmet is integrated into various code editors and IDEs, making it readily available to developers. Some popular code editors that support Emmet include Visual Studio Code, Sublime Text, Atom, and more.

Let's delve into some of the most powerful tools and features that Emmet provides:

1. **Abbreviations and Multiplication**: Emmet allows you to use shorthand abbreviations and multiplication to quickly create repetitive code structures. As shown in the example above, `*3` is used to generate three `<li>` elements within the `<ul>`.

2. **Nesting and Hierarchy**: Emmet supports hierarchical notation that reflects the nested structure of HTML and CSS. You can use `>` to indicate child elements and `+` to indicate sibling elements. For instance, `div>ul>li*3` creates a `<div>` containing a nested `<ul>` with three `<li>` elements.

3. **Element Attributes**: You can include attributes and values in the shorthand notation. For example, `a[href="#"][target="_blank"]` generates an anchor element with `href` and `target` attributes.

4. **CSS Properties**: Emmet can also be used to generate CSS properties. Typing `p{font-size: 16px; color: #333;}` and expanding it will produce a `<p>` element with inline styles applied.

5. **Implicit Tag Names**: If you don't specify a tag name, Emmet will assume a default tag. For instance, typing `.container` will generate a `<div>` with the class "container".

6. **ID and Class Shortcuts**: You can use `#` for IDs and `.` for classes, making it easier to add these attributes to your elements.

7. **Mathematical Expressions**: Emmet supports basic mathematical expressions. For instance, `div.item-$*5` generates five `<div>` elements with class names "item-1" to "item-5".

8. **Placeholders**: You can use placeholders for dynamic content, which can be filled in after expanding the abbreviation. For instance, `img[src=$ alt=Image]` generates an image tag with placeholders for `src` and `alt` attributes.

9. **Custom Snippets**: Emmet allows you to create custom snippets and abbreviations to suit your project's needs, which can greatly enhance your workflow.

10. **Wrap with Abbreviation**: You can select existing code and wrap it with a specific abbreviation to quickly encapsulate it within a new structure.

## Emmet Documentation and Cheatsheet
[Emmet Documentation](https://docs.emmet.io/)

[Emmet Cheatsheet](https://docs.emmet.io/cheat-sheet/)

## Keyboard Shortcuts
### Emmet
![Emmet Keyboard Shortcuts](../../../img/emmet-keyboard-shortcuts.png "Emmet Keyboard Shortcuts")


### System

+ **CTRL + Left/Right Arrow** = Jump to the beginning/end of the previous/next word.

+ **SHIFT + Left/Right Arrow** = Select characters (one by one) to the left or right.

+ **CTRL + SHIFT + Left/Right Arrow** = Select words instead of characters to the left or right.

+ **CTRL + D** = Add the next occurance of the word to the selection.

+ **CTRL + NUMPAD_ADD** = Zoom in view.

+ **CTRL + NUMPAD_SUBTRACT** = Zoom out view.

---
### Knowledge Check

**Q1.** Why should you use Emmet?

**A1.** Emmet is a tool for writing HTML and CSS much more faster. Using predifened abbreviations and expanding them we can write multiple lines of code with only a couple of keystrokes, streamlining and accelarating our web development workflow.

**Q2.** What are some useful Emmet abbreviations?

**A2.** <br>">" is used to create child elements (Example: div.wrapper>p#paragraph).<br> "+" is used to create sibling elements (Example: div.first + div.second).<br> "()" is used to group abbrevations (Example: .wrap>(ul>li*5)+div.footer).

**Q3.** What syntax would you use to create this element `<p class="text"></p>`?

**A3.** `p.text`

**Q4.** What syntax expands to an element with a child element inside of it? For example: `<div><p></p></div>`

**A4.** `div>p`

**Q5.** What syntax would you use to create three elements that have the same class name?

**A5.** `(p.paragraphs)*3`