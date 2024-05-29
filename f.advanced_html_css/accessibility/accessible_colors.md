# Accessible Colors
## Contrast ratio
"Contrast ratio" refers to the difference in luminance or color between the foreground (typically text or graphics) and the background against which it is viewed. It's commonly used to measure the readability and visibility of text or images, especially in digital design, including web design.

In the context of web accessibility, contrast ratio plays a crucial role in ensuring that content is easily readable for all users, including those with visual impairments. People with low vision, color blindness, or other visual disabilities may have difficulty discerning text or graphics if there isn't enough contrast between the foreground and background colors.

The contrast ratio is typically calculated using luminance values of the two colors being compared. Luminance is a measure of the brightness of a color and is often represented on a scale from 0 to 1, where 0 represents black and 1 represents white.

To calculate the contrast ratio between two colors, you first need to determine the relative luminance of each color. This can be done using a formula that converts the color values into luminance values. For example, in the case of standard RGB colors, you might use the formula:

L = 0.2126 * R + 0.7152 * G + 0.0722 * B

Where R, G, and B are the red, green, and blue components of the color, respectively.

Once you have the luminance values for both colors, you can calculate the contrast ratio using the formula:

contrast ratio = (L1 + 0.05) / (L2 + 0.05)

Where L1 is the relative luminance of the lighter color, and L2 is the relative luminance of the darker color. The addition of 0.05 to each luminance value is to prevent the contrast ratio from approaching infinity when one of the colors has a luminance value of 0.

For example, if you have white text on a white background, both colors have a relative luminance of 1.0, so the contrast ratio would be (1.0 + 0.05) / (1.0 + 0.05) = 1.05 / 1.05 = 1:1.

If you have black text on a white background, the relative luminance of black is 0.0 and the relative luminance of white is 1.0, so the contrast ratio would be (1.0 + 0.05) / (0.0 + 0.05) = 1.05 / 0.05 = 21:1.

Web Content Accessibility Guidelines (WCAG) provides specific requirements for contrast ratios to ensure that content is accessible to people with varying degrees of visual acuity.

## WCAG Contrast Ratio Requirements
    Principle 1 – Perceivable (Information and user interface components must be presentable to users in ways they can perceive.)

      Guideline 1.4 – Distinguishable (Make it easier for users to see and hear content including separating foreground from background.)

### Text Contrast
There are two different conformance levels for contrast ratios, both of which have rules for normal text and large text. **Normal text** is defined as text with a font size that’s less than 18 points/24px (or less than 14 points/18.66px for bold text), and **large text** is defined as text with a font size that is at least 18 points/24px (or at least 14 points/18.66px for bold text).

1. **Level A, Level AA (minimum)** requires a contrast ratio of at least 4.5:1 for normal text and 3:1 for large text. *(Guideline Rule 1.4.3)*

2. **Level AAA (enhanced)** requires a contrast ratio of at least 7:1 for normal text and 4.5:1 for large text. *(Guideline Rule 1.4.6)*

Contrast ratios refer to both normal text as well as images of text.

Both conformance levels have exceptions that don’t need to follow the contrast ratio rules:

+ Incidental text, such as text that just happens to be within an image that has other significant visual content, or text that is purely decorative.
+ Text that is part of an inactive or disabled user interface component, such as a button that is disabled and has a lowered opacity.
+ Text that is part of a logo or brand name.

### Non-text Contrast
**Level A, Level AA (minimum)** *(Guideline Rule 1.4.11)* :The visual presentation of the following have a contrast ratio of at least 3:1 against adjacent color(s):

+ **User Interface Components:** Visual information required to identify user interface components and states, except for inactive components or where the appearance of the component is determined by the user agent and not modified by the author;

+ **Graphical Objects:** Parts of graphics required to understand the content, except when a particular presentation of graphics is essential to the information being conveyed.

**Note: [**WebAIM Contrast Checker**](https://webaim.org/resources/contrastchecker/ "webaim.org/resources/contrastchecker/") is a great tool for checking contrast ratios. Just enter the HEX code of the foreground and background colors and it calculates what conformance levels, if any, the contrast ratio passes.**

## Conveying information
    Principle 1 – Perceivable (Information and user interface components must be presentable to users in ways they can perceive.)

      Guideline 1.4 – Distinguishable (Make it easier for users to see and hear content including separating foreground from background.)

**Level A (minimum) *(Guideline Rule 1.4.1)* : Color should not be used as the only visual means of conveying information, indicating an action, prompting a response, or distinguishing a visual element.**

Let’s look at an example. Let’s say you want to create a form that has an instruction stating that required fields are indicated by red text. If a user is color blind or otherwise has difficulty telling some colors apart, having to rely solely on the color of this text can make it difficult or even impossible to perceive or operate the form. Instead of only using color, your form could indicate all required fields with red text and also an asterisk.

---
### Knowledge Check

**Q1.** What is a contrast ratio?

**A1.** "Contrast ratio" refers to the difference in luminance or color between the foreground (typically text or graphics) and the background against which it is viewed. It's commonly used to measure the readability and visibility of text or images, especially in digital design, including web design.

In the context of web accessibility, contrast ratio plays a crucial role in ensuring that content is easily readable for all users, including those with visual impairments. People with low vision, color blindness, or other visual disabilities may have difficulty discerning text or graphics if there isn't enough contrast between the foreground and background colors.

**Q2.** What are two ways you can check a contrast ratio using your dev tools?

**A2.** In Chrome DevTools, you can check the contrast ratio of text against its background in two main ways:

1. **Using the "Elements" Panel**:
   - Right-click on the element (text) whose contrast ratio you want to check and select "Inspect".
   - In the "Elements" panel, navigate to the "Styles" tab on the right side.
   - Look for the CSS properties affecting the text color (`color`) and background color (`background-color`) of the element.
   - Next to these properties, you should see a color preview box. Click on it.
   - A contrast ratio will be displayed, indicating how accessible the text is against its background. Chrome will show this ratio as "AA" or "AAA" to indicate whether it meets the accessibility standards.

2. **Using the "Accessibility" Panel**:
   - Open Chrome DevTools by right-clicking on any element on the webpage and selecting "Inspect", or by pressing `Ctrl+Shift+I` (or `Cmd+Option+I` on Mac).
   - In the DevTools panel, click on the "Audits" tab.
   - Select the "Accessibility" checkbox and click "Run audits".
   - After the audit is complete, scroll down to the "Contrast ratio" section. Here you will find a list of elements with their corresponding contrast ratios. This section may also provide suggestions on how to improve accessibility.

These methods allow you to easily check the contrast ratio of text elements on a webpage, helping ensure better accessibility for users with visual impairments.

**Q3.** What should you avoid when conveying information to users?

**A3.** Color alone, should not be used to convey information to users.