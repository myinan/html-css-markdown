# Fonts and Text Styling
## Fonts
1. ### The System Font Stack
If you use the font-family property to change to a font like impact or Times New Roman, and those fonts do not happen to be installed on your user’s computer, then a fallback font will be displayed. If you have not defined a fallback, then the default HTML font will be used, which is often somewhat ugly. For this reason, it’s common to see somewhat long stacks of fonts listed on projects.

One popular stack is this ‘system font’ stack.

```css
body {
  font-family: system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```

Defaulting to the system font of a particular operating system can boost performance because the browser doesn’t have to download any font files, it’s using one it already had. That’s true of any “web safe” font, though. The beauty of “system” fonts is that it matches what the current OS uses, so they can be a comfortable look.

The obvious limitation here is that you have to call that long list of fonts each time you want to apply it to an individual element. Over time, that could become cumbersome and make your code more bloated than it ought to be. Instead, you might consider making a CSS variable for it:

```css
:root {
  --system-ui: system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}

.element {
  font-family: var(--system-ui);
}
```

This is certainly easier to read but is also more maintainable if the stack ever needs updating. Change it once and it applies everywhere.

2. ### Online Font Libraries
One popular and easy method to get fonts that are **not** installed on a user’s computer is to use an online font library like [Google Fonts](https://fonts.google.com/ "Google Fonts"), Font Library or the premium, but non-free Adobe Fonts.

To use a font from one of these libraries, go to the website, select a font and then copy a snippet from the website to import that font from their server into your website. You’ll be given either a `<link>` tag to put in your HTML like so…

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
```

… or an `@import` at-rule that can be dropped at the top of a CSS file.

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
```

Either method will import that font and make it available for you to use in your CSS:

```css
body {
  font-family: 'Roboto', sans-serif;
}
```

Keep in mind that it’s important to add a fallback font. If you’re linking to an external API, you have no guarantee that the URL won’t change, or that the external API won’t go down at some point. Having a reasonable fallback means that if something goes wrong, at least your site won’t look completely broken.

3. ### Downloaded Fonts
It is also possible to use a font that you have downloaded from the web. In your CSS file, you import and define a custom font using the `@font-face` rule, and then use as you would any other font-family. There are multiple types of font file formats, most popular ones being TrueType Fonts (TTF), OpenType Fonts (OTF), The Web Open Font Format (WOFF), and The Web Open Font Format (WOFF 2.0).

In the `@font-face` rule; first define a name for the font (e.g. my-cool-font) and then point to the font file. To use the font for an HTML element, refer to the name of the font (my-cool-font) through the `font-family` property:

```css
@font-face {
  font-family: my-cool-font;
  src: url(../fonts/the-font-file.woff);
}

h1 {
  font-family: my-cool-font, sans-serif;
}
```

This method _may_ be more reliable than relying on a third-party font API, but it is always wise to include a fallback.

## Text Styles (CSS Text Styling Rules)
Text styling is a fundamental aspect of web design, and CSS provides a wide range of rules and properties to control how text appears on a web page.

1. **Font Properties:**

   - `font-family`: Specifies the font family for text. You can define a specific font or a list of fonts to provide fallback options. For example:
   
     ```css
     font-family: "Arial", sans-serif;
     ```

   - `font-size`: Sets the size of the text. You can use various units such as pixels (`px`), ems (`em`), percentages (%), or keywords like `small`, `medium`, `large`, etc. For example:
   
     ```css
     font-size: 16px;
     ```

   - `font-weight`: Determines the thickness or boldness of the text. Common values are `normal`, `bold`, `bolder`, and numeric values from 100 to 900. For example:
   
     ```css
     font-weight: bold;
     ```

   - `font-style`: Sets the style of the font, such as `normal`, `italic`, or `oblique`. For example:
   
     ```css
     font-style: italic;
     ```

2. **Text Color:**

   - `color`: Specifies the color of the text using various formats like color names, hex codes, RGB values, etc. For example:
   
     ```css
     color: #333;
     ```

3. **Text Alignment:**

   - `text-align`: Controls the horizontal alignment of text within its container. Options include `left`, `right`, `center`, and `justify`. For example:
   
     ```css
     text-align: center;
     ```

4. **Text Decoration:**

   - `text-decoration`: Adds decorative elements to text, such as underlines, overlines, and line-throughs. Common values are `none`, `underline`, `overline`, `line-through`. For example:
   
     ```css
     text-decoration: underline;
     ```

5. **Text Transform:**

   - `text-transform`: Changes the capitalization of text. Options include `uppercase`, `lowercase`, and `capitalize`. For example:
   
     ```css
     text-transform: uppercase;
     ```

6. **Line Height:**

   - `line-height`: Sets the height of a line of text. It can be specified as a unitless number or with units like `em` or `px`. For example:
   
     ```css
     line-height: 1.5;
     ```

7. **Letter Spacing:**

   - `letter-spacing`: Adjusts the space between characters in text. It can be specified in units like `em` or `px`. For example:
   
     ```css
     letter-spacing: 2px;
     ```

8. **Word Spacing:**

   - `word-spacing`: Controls the space between words in text. It can be specified in units like `em` or `px`. For example:
   
     ```css
     word-spacing: 4px;
     ```

9. **Text Shadow:**

   - `text-shadow`: Adds a shadow effect to text. It takes three values: horizontal offset, vertical offset, and color. For example:
   
     ```css
     text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
     ```

10. **Text Overflow:**

    - `text-overflow`: Defines how text should behave when it overflows its container. Common values include `ellipsis`, which adds an ellipsis (...) at the end of overflowing text, and `clip`, which simply hides the overflow. For example:
    
      ```css
      text-overflow: ellipsis;
      ```

11. **White Space:**

    - `white-space`: Controls how white space inside an element is handled. Options include `normal`, `nowrap` (prevents text from wrapping), and `pre` (preserves whitespace). For example:
    
      ```css
      white-space: nowrap;
      ```

12. **Text Justification:**

    - `text-justify`: Defines how text should be justified within its container. It can be used to control the spacing between words and letters when justifying text. For example:
    
      ```css
      text-justify: inter-word;
      ```

---
### Knowledge Check

**Q1.** What are the 2 ways to add fonts that are not installed on a user’s computer?

**A1.** We can use online font libraries and make api calls to their servers or download the font we want to use on our server and apply that font to the elements we want. The latter solution might prove to be more reliable in the long run.

**Q2.** What is the ‘system font stack’ and why would you want to use it?

**A2.** "System font stack" is a stack of fonts we use as values to the `font-family` property, usually as a fallback. These fonts are already installed on users computers so if our custom font can't be implemented for whatever reason these system fonts will be used instead, ensuring a pleasing look for our webpage.

**Q3.** Which property would you use to increase or decrease the space between letters in a word?

**A3.** In order to increase or decrease spacing between letters in a word, we use the `word-spacing` CSS property.

**Q4.** Which property would you use to increase or decrease the space between lines in a paragraph?

**A4.** In order to increase or decrease the space between lines in a paragraph, we use the `line-height` CSS property.

---
We can set the optimal line height of a paragraph using the `ex` unit, as well as set a paragraph’s width using the `ch` unit(range of 60-70 recommended), in order to respect the user’s preferred browser settings for font size and family. We can use `variable fonts` to adjust the spacing between letters and words, and we can manipulate the stroke of glyphs to increase contrast, helping readers with visual impairments and dyslexia. We can even automatically adjust text contrast using CSS variables, giving the user their preferred theme.