# Custom Properties
Custom properties, also known as CSS variables, are a powerful feature in CSS that allow you to define your own reusable values that can be used throughout your stylesheet. They provide a way to store and reuse values, making your CSS more maintainable and flexible. Custom properties are denoted by names that start with two hyphens (e.g., `--my-color`), and you can assign values to them. Here's a detailed explanation of custom properties in CSS:

### Defining Custom Properties

To define a custom property, you use the `--` prefix followed by a name and then assign a value to it. This is typically done within a CSS selector like this:

```css
:root {
  --main-color: #3498db;
  --font-size: 16px;
}
```

In this example, we've defined two custom properties, `--main-color` and `--font-size`, and assigned them values of `#3498db` (a shade of blue) and `16px`, respectively. The `:root` selector is commonly used to define custom properties because it sets the global scope for these variables, making them accessible throughout the entire stylesheet.

### Using Custom Properties

Once you've defined custom properties, you can use them anywhere in your CSS by referencing them with the `var()` function. Here's how you might use the custom properties defined above:

```css
body {
  background-color: var(--main-color);
  font-size: var(--font-size);
}
```

In this example, we've used `var(--main-color)` to set the `background-color` of the `body` element to the value of `--main-color`, which is `#3498db`. Similarly, we've used `var(--font-size)` to set the `font-size` of the `body` element to the value of `--font-size`, which is `16px`.

### Benefits of Custom Properties

Custom properties offer several advantages in CSS:

1. **Reusability**: You can use custom properties to store values that are used repeatedly in your stylesheet, making it easier to update those values later. This promotes consistency and reduces redundancy.

2. **Maintainability**: When you need to change a value that's used throughout your stylesheet, you only need to update it in one place (the custom property definition), rather than searching for and updating every instance of that value.

3. **Scoped Variables**: Custom properties can be scoped to specific elements or selectors, not just at the global level. This allows you to have different values for the same custom property in different parts of your stylesheet.

4. **Dynamic Values**: Custom properties can be changed dynamically using JavaScript. This enables you to create themes, respond to user interactions, or implement other dynamic behaviors in your stylesheets.

5. **Readability**: Custom properties can make your CSS more self-documenting by giving meaningful names to values, making your code more understandable for both you and others who work on the project.

### Cascading and Inheritance

Custom properties follow the same cascading and inheritance rules as other CSS properties. If a custom property is defined within a selector, its value will be inherited by its child elements, unless overridden. If multiple rules define the same custom property, the one with the most specific selector takes precedence.

### Fallback Values

You can provide fallback values within the `var()` function in case the custom property is undefined or not supported by the browser. For example:

```css
p {
  font-size: var(--font-size, 14px); /* Fallback to 14px if --font-size is undefined */
}
```

---
### Knowledge Check

**Q1.** How would you declare a custom property with a name of text-color?

**A1.**
 ```css
:root {
  --text-color: value;
}
```

**Q2.** How would you access a custom property with a name of background-color?

**A2.**
```css
.element {
  background: var(--background-color);
}
```

**Q3.** Where would you declare a custom property to have its scope be global and accessible by all other selectors?

**A3.** To have a custom property with a global scope, declare the custom property on `:root`.

**Q4.** Where would you declare a custom property so that a user’s theme setting from their OS or browser was taken into account?

**A4.** We can declare our custom properties on `:root.dark` and `:root.light`. When the user's theme setting changes, and the class on the HTML element changes accordingly (e.g., from light to dark), the CSS properties throughout the stylesheet that depend on these custom properties will update accordingly, effectively changing the theme of the website based on the user's preference.