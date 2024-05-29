## CSS Units (CSS \<length> value type)
In CSS (Cascading Style Sheets), units are used to define the size and dimensions of various properties such as length, width, height, margin, padding, font size, and more. Units in CSS help you control the layout and appearance of web elements, ensuring that your web pages are visually appealing and responsive across different devices and screen sizes. CSS units can be broadly categorized into two types: absolute units and relative units.

1. ### **Absolute Units**:

    Absolute units are fixed and do not depend on the context or the size of the viewport. These units provide a consistent size regardless of the screen's resolution or user settings. Common absolute units include:

    - **Pixels (px)**: Pixels are the most common absolute unit. One pixel represents a single dot on the screen. Pixel values are not affected by user preferences for font size or display settings. For example:
    
        ```css
        font-size: 16px;
        width: 200px;
        ```

    - **Inches (in)**: Inches are a physical unit of measurement, and their size depends on the actual display. Typically, 1 inch is equivalent to 96 pixels. For example:
    
        ```css
        width: 2in;
        ```

    - **Centimeters (cm)**: Centimeters are another physical unit, and 1 centimeter is roughly equivalent to 37.8 pixels. For example:
    
        ```css
        height: 5cm;
        ```

    - **Millimeters (mm)**: Millimeters are smaller units than centimeters, and 1 millimeter is approximately equal to 3.78 pixels. For example:
    
        ```css
        margin-top: 10mm;
        ```

    - **Points (pt)**: Points are commonly used in print media and are roughly equivalent to 1/72 of an inch. They are not affected by screen resolution. For example:
    
        ```css
        font-size: 12pt;
        ```

    - **Picas (pc)**: A pica is a unit of measure used primarily in typography. It is equal to 12 points. For example:
    
        ```css
        line-height: 1.5pc;
        ```

    Most of these units are more useful when used for print, rather than screen output. For example, we don't typically use cm (centimeters) on screen. The only value that you will commonly use is px (pixels).

2. ### **Relative Units**:

    Relative units are more flexible and responsive because they depend on the context and can adapt to user settings. They are often used to create responsive web designs. Common relative units include:

    - **Percentage (%)**: Percentage units are relative to the parent element's size or the container's dimensions. For example, setting the width to 50% means the element will occupy half of its parent's width. 
    
        ```css
        width: 50%;
        ```

    - **Em (em)**: The "em" unit is relative to the font size of the parent element. If you set an element's font-size to 2em, it will be twice the size of its parent's font size.
    
        ```css
        font-size: 2em;
        ```

    - **Rem (rem)**: The "rem" unit is similar to "em," but it is relative to the root element's (usually the <html> element) font size. This makes it more predictable and less affected by nested elements.
    
        ```css
        font-size: 1.5rem;
        ```

    - **Viewport Units**: These units are relative to the size of the viewport (the visible area of the browser window). There are four main viewport units: vw (viewport width), vh (viewport height), vmin (the smaller of viewport width and height), and vmax (the larger of viewport width and height).
    
        ```css
        width: 50vw;
        height: 30vh;
        ```

    - **Ch**: The "ch" unit is based on the width of the character "0" in the current font. It can be used to create layouts based on characters' dimensions.
    
        ```css
        width: 20ch;
        ```

    - **Ex**: The "ex" unit is based on the height of the lowercase letter "x" in the current font. It is used less frequently but can be useful for vertical measurements.
    
        ```css
        line-height: 2ex;
        ```

Relative units are often preferred for responsive web design because they adapt to different screen sizes and user preferences, making your web pages more accessible and user-friendly. When choosing units in CSS, it's essential to consider the specific context and requirements of your web project to determine whether absolute or relative units are more appropriate.

## CSS Value Types
Every property used in CSS has a value type defining the set of values that are allowed for that property. Let's take a look at some of the most frequently used value types, and their most common values and units:

1. ### **Basic Value Types:**
    - **Length Units:** These value types define distances and sizes. Common length units include:
        - **px (pixels):** Represents a fixed-size pixel on the screen. It's a commonly used unit for specifying precise dimensions.
        - **em:** Relative to the font size of the element. For example, if the font size is 16px, 1em is equivalent to 16px.
        - **rem:** Relative to the root (html) element's font size. It provides a consistent scaling factor across the entire document.
        - **% (percentage):** Relative to a parent element's size. For example, setting width: 50% means the element will take up half of its parent's width.

    - **Color Values:** CSS supports various ways to specify colors, including:
        - **Named Colors:** Predefined color names like 'red', 'blue', 'green', etc.
        - **Hexadecimal Notation:** Using a combination of six or three hexadecimal digits (e.g., #RRGGBB or #RGB).
        - **RGB and RGBA:** Representing colors using the Red, Green, and Blue channels. RGBA includes an alpha channel for transparency.
        - **HSL and HSLA:** Defining colors based on their Hue, Saturation, Lightness, and Alpha (transparency).

2. ### **Positioning Value Types:**
    - **Length Units (again):** Length units can also be used to position elements. For example, you can set `top`, `left`, `right`, and `bottom` properties to position an element relative to its containing element.

3. ### **Text Value Types:**
    - **Strings:** You can specify text content or font family names using strings, enclosed in single or double quotes.
    - **Font Names:** Names of font families, which should be available on the user's device or specified in a `@font-face` rule.

4. ### **Numeric Value Types:**
    - **Integer and Float:** Numeric values can be integers (whole numbers) or floating-point numbers (decimal numbers). These are used for various properties, including dimensions, opacity, and more.

5. ### **Time Value Types:**
    - **Milliseconds and Seconds:** Time values can be specified in milliseconds (ms) or seconds (s). They are used for animations and transitions.

6. ### **Angle Value Types:**
    - **Degrees, Gradients, and Radians:** Angle values are used for properties like rotation and gradients. Common units include degrees (deg), gradians (grad), and radians (rad).

7. ### **Frequency Value Types:**
    - **Hertz (Hz):** Used for properties like audio or video playback speed.

8. ### **Resolution Value Types:**
    - **Dots per Inch (dpi) and Dots per Centimeter (dpcm):** Used for media queries and specifying image resolutions.

_Now, let's explore some frequently used values associated with these types:_

- **Length Values:** Common values include `0` (for no dimension), `auto` (letting the browser determine a dimension), and various pixel values (`1px`, `2px`, etc.).

- **Color Values:** Besides named colors, hexadecimal values like `#FF5733`, RGB values like `rgb(255, 87, 51)`, and HSL values like `hsl(9, 100%, 55%)` are frequently used.

- **Positioning Values:** `absolute`, `relative`, `fixed`, and `static` are used to define positioning schemes. For `top`, `left`, `right`, and `bottom`, values like `0`, `10px`, and `50%` are common.

- **Text Values:** Font names like `"Arial", sans-serif` and strings like `"Hello, CSS!"` are frequently used.

- **Numeric Values:** Numeric values like `1`, `2.5`, and `-10` are commonly used for various properties.

- **Time Values:** Time values like `1s` (1 second) and `500ms` (500 milliseconds) are often used for transitions and animations.

- **Angle Values:** Degrees (`45deg`), gradians (`50grad`), and radians (`0.7854rad`) are common for rotation and gradient definitions.

- **Frequency Values:** Hertz values like `60Hz` for animations or audio playback.

- **Resolution Values:** Dots per inch (`72dpi`) and dots per centimeter (`28.35dpcm`) are used for specifying image resolutions.

A value type in CSS is a way to define a collection of allowable values. This means that if you see `<color>` as valid you don't need to wonder which of the different types of color value can be used — keywords, hex values, rgb() functions, etc. You can use any available `<color>` values, assuming they are supported by your browser.

---
### Knowledge Check

**Q1.** Why would you want to use em or rem for font-size instead of px?

**A1.** Users might change their default font-size in their browser and it's important to respect their preferences. By using `rem` values for font-sizes we will use their preferred default font-size size since rem mean root-em.

**Q2.** What are some instances where you might want to use vh and vw?

**A2.** vh and vw are particularly useful when employing full-height heroes on our web pages, or if we are creating full-screen app-like interfaces.

**Q3.** What are some instances where you might want to use px instead of a relative unit?

**A3.** When declaring values for padding,margin,border etc, using px instead of relatives units like em or rem might make more sense because when using relative units, the end result when zoomed in our out might prove to be more dramatic whereas when px values are used it's more predictable.