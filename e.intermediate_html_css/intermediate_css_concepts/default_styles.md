# Default Styles
The "default styles" employed by web browsers refers to the built-in, predefined set of styles that browsers apply to HTML elements when rendering web pages. These default styles ensure that web content is displayed in a readable and visually consistent manner, even if the web page does not specify any custom styling through Cascading Style Sheets (CSS). The default styles are designed to provide a basic level of formatting and layout to HTML elements.

Here are some common characteristics of the default styles:

1. **Font styles:** Browsers typically specify default fonts for different types of text elements, such as headings, paragraphs, and lists. These fonts are usually sans-serif for headings and serif for paragraphs.

2. **Text size and spacing:** Default font sizes and line heights are set to make text legible. Margins and padding around elements like paragraphs and headings are also predefined to create spacing between them.

3. **Link styles:** Links are usually displayed in blue and underlined to distinguish them from regular text. Visited links often change color to indicate that they have been previously clicked.

4. **List styles:** Unordered and ordered lists are typically styled with bullet points or numbers, and default spacing is applied to list items.

5. **Box model:** Elements have a default display mode (e.g., block or inline), which affects their positioning and layout. Default margin and padding values may also be set.

While default styles serve as a helpful starting point for web rendering, they can sometimes cause inconsistencies in the appearance of web pages across different browsers. To create a more consistent and controlled visual design for a website, web developers often use CSS to override these default styles and apply custom styling.

### CSS Reset
A CSS reset is a technique used by web developers to reset or neutralize the default styles applied by different web browsers. The goal of a CSS reset is to create a consistent baseline for styling across browsers, ensuring that web developers have a clean slate to work with when designing their websites. CSS resets essentially remove any default margins, padding, font styles, and other browser-specific styles, allowing developers to start from scratch with their own CSS rules.

A common example of a CSS reset rule is to set the margin and padding of all elements to zero:

```css
* {
    margin: 0;
    padding: 0;
}
```

However, it's important to note that CSS resets can be quite aggressive, and they may require developers to explicitly style many elements that would otherwise have default styles applied. Some developers prefer to use a "CSS normalize" approach instead of a reset. CSS normalize styles aim to make default styles more consistent across browsers without completely removing them.

In summary, the "default styles" employed by web browsers provides basic styling for HTML elements, while a CSS reset is a technique used by web developers to neutralize these defaults and create a consistent starting point for custom styling using CSS.

---

### [The default style sheet used by Chrome to render HTML](https://chromium.googlesource.com/chromium/blink/+/refs/heads/main/Source/core/css/html.css)

### [browserdefaultstyles.com](https://browserdefaultstyles.com/)

### [The Meyer Reset](https://meyerweb.com/eric/tools/css/reset/)
The Meyer Reset is almost certainly the most popular. It’s very simple and basically removes every default style.

### [normalize.css](https://nicolasgallagher.com/about-normalize-css/)
CSS normalize styles aim to make default styles more consistent across browsers without completely removing them. [Github repo of normalize.css](https://github.com/necolas/normalize.css)

---
### Knowledge Check

**Q1.** Why would you want to use a CSS reset?

**A1.** Though it was a bigger problem before, default styles might be inconsistent across browsers. A css reset, resets nearly all default styles applied by browsers and provides a clean base to start styling the webpage. On the other hand, as a more modern approach, normalize.css aim to make default styles more consistent accross browsers without completely removing them.