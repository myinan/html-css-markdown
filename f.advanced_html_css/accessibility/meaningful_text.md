# Meaningful Text
Meaningful text is pretty straight forward: when a user reads text or has it announced to them, they should be able to immediately understand what it means even without any surrounding context. A lack of meaningful text can affect all users, but especially those who rely on assistive technologies.

## Links
Meaningful text contributes to the accessibility of web links:

1. **Screen reader compatibility**: Screen readers are software programs that interpret and read aloud the content of a webpage to users who are visually impaired. When encountering a hyperlink, screen readers typically announce the link text to the user. Meaningful text provides context and clarity about the destination or purpose of the link, enabling users to make informed decisions about whether to follow the link or not.

2. **Keyboard navigation**: Many users navigate websites using only a keyboard, without a mouse. Meaningful link text allows keyboard users to quickly identify and select links without relying on mouse hover or contextual cues. Clear and descriptive link text enhances navigation efficiency and usability for keyboard users.

3. **Cognitive accessibility**: Meaningful link text improves cognitive accessibility for all users, including those with learning disabilities or cognitive impairments. Descriptive links help users understand the purpose of the link and predict where it will take them, reducing cognitive load and facilitating smoother navigation through the content.

4. **Search engine optimization (SEO)**: Meaningful link text not only benefits users but also improves the search engine optimization of web content. Search engines use link text to understand the context and relevance of linked pages. Descriptive and relevant link text can enhance the visibility and ranking of webpages in search results, ultimately driving more traffic to the site.

5. **Clarity and usability**: Clear and descriptive link text enhances the overall clarity and usability of web content for all users. Meaningful links provide explicit information about the linked resource, helping users decide whether to click on the link based on their interests or needs. Vague or ambiguous link text can lead to confusion and frustration among users trying to navigate the website.

In summary, meaningful link text plays a crucial role in improving the accessibility, usability, and overall user experience of web content for all users, including those with disabilities.

## Forms
Meaningful text contributes to the accessibility of web forms, particularly concerning form labels, instructions, and error handling:

1. **Form Labels**:
   - Meaningful labels associated with form fields provide context and guidance to users, including those who rely on screen readers or keyboard navigation. Properly labeled form fields allow screen reader users to understand the purpose of each field and provide relevant input.
   - When a form field lacks a label or has a vague label (such as "Untitled" or "Field 1"), it becomes challenging for users to understand the required information. This can be particularly problematic for individuals with visual impairments who depend on screen readers to navigate and complete forms.

2. **Instructions**:
   - Clear and concise instructions help all users understand how to fill out the form correctly. This is especially important for users with cognitive disabilities or limited literacy skills who may require additional guidance.
   - Providing instructions in accessible formats, such as plain language or through visual cues, ensures that users of all abilities can comprehend and follow them effectively. Instructions should be positioned close to the related form fields and presented in a consistent format to aid comprehension.
   - For instructions that are unique to an input, they should be placed alongside the input itself. Instructions that are more global across the form, such as indicating which inputs are required, should either be placed at the top of the form (“* indicates a required field”), or placed alongside the input or its label (“Name (required)”).

3. **Error Handling**:
   - Meaningful error messages play a critical role in guiding users when they make mistakes while filling out a form. Clear error messages should describe the issue and provide instructions on how to correct it.
   - When errors occur, it's essential to associate them with specific form fields, indicating where the problem lies. This assists users in locating and addressing the errors efficiently.
   - Providing suggestions or examples alongside error messages can further clarify the required format or information, assisting users in resolving issues promptly.


```html
<!-- Example 1: Huh? -->
<div class='input-error'>Error: Invalid input.</div>

<!-- Example 2: That makes more sense. -->
<div class='input-error'>Error: Email is invalid.</div>

<!-- Example 3: Even better! -->
<div class='input-error'>Error: 'JohnSmith@@test.com' is not valid. Example of a valid email: example@yourdomain.com.</div>
```

In summary, meaningful text in web forms, including labels, instructions, and error messages, is vital for ensuring accessibility and usability for all users. By incorporating clear and descriptive text elements, web developers can enhance the user experience and enable individuals with disabilities to interact with forms effectively. Additionally, adhering to accessibility standards and guidelines, such as the Web Content Accessibility Guidelines (WCAG), helps ensure that web forms are inclusive and accessible to diverse user populations.

## Alternative Text for Images
Alternative text is a textual substitute for non-text content in web pages. This part is focused on images, but its principles also apply to multimedia and other non-text content.

Alternative text serves several functions:

+ Screen readers announce alternative text in place of images, helping users with visual or certain cognitive disabilities perceive the content and function of the images.
+ If an image fails to load or the user has blocked images, the browser will present the alternative text visually in place of the image.
+ Search engines use alternative text and factor it into their assessment of the page purpose and content.

Although technology is getting better at recognizing what an image depicts, algorithms alone cannot understand what an image means within the context of the overall page. A maple leaf might represent Canada, or it might just illustrate the leaf of a tree. Web page authors must provide alternative text that represents the content and function of their images.

Alternative text can be presented in two ways:

+ within the alt attribute of the \<img> element
+ within visible body text near the image, or when the text equivalent cannot be presented succinctly, alternative text can be presented on a separate page, linked from either the image or a text link adjacent to the image
Thus, alternative text is about more than just the alt attribute.

**Every image should have an alt attribute, even if it's alt="" (sometimes called "null" alternative text).**

The alt attribute should typically:

+ be accurate and equivalent in representing content and function.
+ be succinct. Content (if any) and function (if any) should be presented as succinctly as possible, without sacrificing accuracy. Typically, only a few words are necessary, though rarely a short sentence or two may be appropriate.
+ not be redundant or provide the same information as text near the image.
+ not include phrases like "image of ..." or "graphic of ...", etc. This would be redundant since screen readers already announce "graphic" along with the alt text. If the fact that an image is a photograph or illustration, etc. is important content, it may be useful to include this in alternative text.

**Decorative images should have alt="" .**

A "decorative" image is one that...<br>
+ does not present important content,
+ is used for layout or non-informative purposes, and
+ does not have a function (e.g., is not a link).

## WCAG and Meaningful Text
Issues and solutions to those issues that we have discussed here are present in WCAG as several rules regarding use of meaningful text in web content, especially in the section:
```
Principle 3 – Understandable
(Information and the operation of the user interface must be understandable.)
```

---
### Knowledge Check

**Q1.** What are three rules you should follow in order to provide meaningful links?

**A1.** When you add links to a page, there are a few rules you should be following:

+ Make sure that the text content of the \<a> element somehow indicates where the link redirects to and that it’s brief (around 100 characters). So avoid using phrases like “click here” or “this page”.
+ If a link would open or download a file, include text that tells the user what kind of file it is as well as the file size.
+ If a link would automatically open in a new tab or window with the target="_blank" attribute, you should indicate this to the user in some way.

```html
<!-- Example 1: Now the user is aware that this link will open or download a PDF file. -->
<a href='...'>2021 Sign Up Statistics (PDF, 1MB)</a>

<!-- Example 2: And now the user knows this link opens in a new tab! -->
<a href='...'>GitHub (opens in new tab)</a>
```

**Q2.** What information should you inform users of in order to provide meaningful error messages in forms?

**A2.** 

- Meaningful error messages play a critical role in guiding users when they make mistakes while filling out a form. Clear error messages should describe the issue and provide instructions on how to correct it.
- When errors occur, it's essential to associate them with specific form fields, indicating where the problem lies. This assists users in locating and addressing the errors efficiently.
- Providing suggestions or examples alongside error messages can further clarify the required format or information, assisting users in resolving issues promptly.


```html
<!-- Example 1: Huh? -->
<div class='input-error'>Error: Invalid input.</div>

<!-- Example 2: That makes more sense. -->
<div class='input-error'>Error: Email is invalid.</div>

<!-- Example 3: Even better! -->
<div class='input-error'>Error: 'JohnSmith@@test.com' is not valid. Example of a valid email: example@yourdomain.com.</div>
```

**Q3.** When should you use the empty string/null value for the alt attribute?

**A3.** **Decorative images should have alt="" .**

A "decorative" image is one that...<br>
+ does not present important content,
+ is used for layout or non-informative purposes, and
+ does not have a function (e.g., is not a link).