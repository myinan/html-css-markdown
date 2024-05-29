# Semantic HTML
Semantic HTML refers to the use of HTML markup that describes the meaning or purpose of its content, rather than just its presentation or appearance. In other words, semantic HTML provides context and structure to web content, making it more meaningful and accessible for both humans and machines (such as search engines or screen readers).

Here are some key points about semantic HTML:

1. **Meaningful Tags**: Semantic HTML uses tags that convey the meaning of the content they enclose. For example, instead of using a `<div>` or `<span>` tag to create a generic container, semantic HTML encourages the use of tags like `<header>`, `<nav>`, `<article>`, `<section>`, `<aside>`, `<footer>`, etc., which provide clear indications of the content's purpose.

2. **Accessibility**: Semantic HTML improves accessibility by providing structural cues that assistive technologies, such as screen readers, can interpret more accurately. Users who rely on these technologies can navigate and understand the content more easily when semantic markup is used.

3. **SEO Benefits**: Search engines prioritize semantic content because it provides clearer indications of the page's structure and topic. Using semantic HTML can improve a website's search engine ranking by helping search engines better understand the content and context.

4. **Maintainability**: Semantic HTML makes it easier for developers to understand and maintain code. By using descriptive tags that reflect the content's purpose, developers can quickly grasp the structure of a web page without needing to delve deep into the markup.

5. **Future-proofing**: Semantic HTML helps ensure that web content remains relevant and adaptable to changes in technology and standards. As web technologies evolve, semantic markup provides a solid foundation for integrating new features and functionalities.

6. **Separation of Concerns**: Semantic HTML promotes a clear separation between content and presentation. While CSS is used to style the content, HTML focuses on structuring and describing the content's meaning, which leads to cleaner and more maintainable code.

Here's an example of non-semantic HTML versus semantic HTML:

Non-semantic HTML:
```html
<div id="header">
  <div class="logo">
    <img src="logo.png" alt="Company Logo">
  </div>
  <div class="menu">
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </div>
</div>
```

Semantic HTML:
```html
<header>
  <div class="logo">
    <img src="logo.png" alt="Company Logo">
  </div>
  <nav>
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>
</header>
```

In the semantic HTML example, `\<header>` and `\<nav>` tags clearly indicate the purpose of the content they contain, making it easier to understand and maintain the code.

## Absolute musts in regards to semantic HTML
When it comes to using semantic HTML correctly, you want to think about what your intent for users is and what context you want (or need) to provide to them. This can vary depending on the situation, but there are some things you should absolutely be checking for moving forward:

+ If a user is meant to click something, whether it’s an actual button or not, you will usually want to use a \<button> element. This will let the user know that they can interact with the element by clicking on it.

+ If you want to provide some sort of tabular data to a user, use a \<table> element along with the elements related to it. This will allow a user to more easily navigate and understand the data being presented.

+ When you use an input element, you should always create a relationship between it and a \<label> element. A \<label> provides context for what an input actually means to assistive technologies, announcing the label contents each time the input is announced. Not only that, but a proper \<label> increases the clickable area of the input itself, which is useful for users who have trouble clicking on smaller items.

+ Continuing with inputs, you should always use the type that makes the most sense for its intended use. type="text" makes more sense for a name or address field, while type="email" or type="tel" would of course make more sense for an e-mail or telephone field, respectively. For certain devices, using the correct type may show only the required or additional characters on the keyboard. A type="tel" input, for example, might make it much easier for users to fill out their phone number by providing larger, numerical-only keys on mobile or tablet devices.

+ When you want to present a list of some sort to a user, you should use the appropriate list element (\<ol>, \<ul>, or \<dl>) and their related list item elements. This will not only let the user know when they are entering or exiting a list, but also how many items are in the list.

## Headings and landmarks
Headings are the **\<h1>** through **\<h6>** elements, and like the name implies, these elements act as headings to sections of a page.

Landmarks, on the other hand, are HTML elements that act as *regions* of a page. There are seven native HTML elements that define these landmark regions:

+ \<aside>
+ \<footer>
+ \<form>
+ \<header>
+ \<main>
+ \<nav>
+ \<section>

By properly using landmarks and headings, you provide users of assistive technologies a more operable and understandable page: not only can screen reader users navigate a page via landmarks and headings by using navigation keyboard commands (or opening a menu in their screen reader), but these elements also have their roles announced to provide additional context.

If you were to use only \<div> elements to act as these landmarks and headings, maybe adding in some CSS to visually style them, then a screen reader user would have to go through the entire page just to get to a specific section, and they may not be able to actually tell what is a heading or a landmark on the page.

## WCAG and Semantic HTML
The Web Content Accessibility Guidelines (WCAG) do not explicitly define "semantic HTML rules." However, WCAG does emphasize the importance of using semantic HTML to improve accessibility. Semantic HTML refers to using HTML elements according to their intended purpose or meaning, which helps assistive technologies and users better understand the structure and content of web pages.

While WCAG doesn't have specific rules solely focused on semantic HTML, it does include several guidelines and success criteria that indirectly encourage its use. Here are some key points related to semantic HTML in WCAG:

1. **Use of Proper Headings (Guideline 1.3)**: WCAG encourages using proper heading elements (h1, h2, h3, etc.) to structure content hierarchically. This ensures that screen readers can navigate the content easily and users can understand the organization of the page.

2. **Labeling Form Controls (Guideline 1.3)**: Ensuring that form controls are appropriately labeled using \<label> elements or other techniques helps users understand their purpose. This is crucial for users relying on assistive technologies like screen readers.

3. **Meaningful Link Text (Guideline 2.4)**: WCAG advises using descriptive link text that provides context about the destination of the link. Instead of generic text like "click here," using text that describes the destination or action of the link improves accessibility.

4. **Structural Markup (Guideline 1.3)**: Structuring content with appropriate HTML elements (such as \<section>, \<article>, \<nav>, \<aside>, etc.) helps convey the purpose and relationship of different parts of the page. This enhances accessibility for users navigating with assistive technologies.

5. **Alternative Text for Images (Guideline 1.1)**: Providing alternative text for images using the alt attribute in \<img> tags ensures that users who cannot see the images can still understand their purpose or content.

6. **Table Markup (Guideline 1.3)**: When using tables for data, WCAG advises using proper table markup (such as \<th>, \<tr>, and \<td> elements) to convey the structure and relationships within the data. This is important for users relying on screen readers or other assistive technologies.

While WCAG doesn't prescribe specific rules for semantic HTML, adherence to its guidelines promotes the use of semantic HTML practices, which ultimately enhances accessibility for all users, including those with disabilities.

---
### Knowledge Check

**Q1.** Why is semantic HTML important for accessibility?

**A1.** In terms of web accessibility, using semantic HTML is important because it provides meaning and context. Some elements have a semantic meaning, but don’t really provide any context when announced by assistive technologies, such as the \<p> element. Then there are elements that have a semantic meaning and are announced with some sort of context to help users perceive or operate them, like a \<button>.

The \<div> and \<span> elements, most likely two of the more common elements you use, are semantically neutral. That is, they themselves have no semantic meaning and provide no context on their own to assistive technologies, which can make it more difficult for users of such technologies to perceive, operate, and understand them.

**Q2.** What are the seven HTML elements that define landmarks on a page?

**A2.** Landmarks are HTML elements that act as *regions* of a page. There are seven native HTML elements that define these landmark regions:

+ \<aside>
+ \<footer>
+ \<form>
+ \<header>
+ \<main>
+ \<nav>
+ \<section>