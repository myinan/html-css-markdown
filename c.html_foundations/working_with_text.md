# Working with Text
Most content on the web is text-based, so you will find yourself needing to work with HTML text elements quite a bit.

### Paragraphs
If we want to create paragraphs in HTML, we need to use the paragraph element, which will add a newline after each of our paragraphs. A paragraph element is defined by wrapping text content with a \<p> tag.

### Headings
Headings are different from other HTML text elements: they are displayed larger and bolder than other text to signify that they are headings.

There are 6 different levels of headings starting from \<h1> to \<h6>. The number within a heading tag represents that heading’s level. The largest and most important heading is h1, while h6 is the tiniest heading at the lowest level.

Headings are defined much like paragraphs. For example, to create an h1 heading, we wrap our heading text in a \<h1> tag.

### Strong Element
The \<strong> element makes text bold. It also semantically marks text as important; this affects tools, like screen readers, that users with visual impairments will rely on to use your website. The tone of voice on some screen readers will change to communicate the importance of the text within a strong element. To define a strong element we wrap text content in a \<strong> tag.

Sometimes you will want to make text bold without giving it an important meaning. You’ll learn how to do that in the CSS lessons later in the curriculum.

### Em Element
The \<em> element makes text italic. It also semantically places emphasis on the text, which again may affect things like screen readers. To define an emphasised element we wrap text content in a \<em> tag.

### Nesting and Indentation
When we nest elements within other elements, we create a parent and child relationship between them. The nested elements are the children and the element they are nested within is the parent.

Just as in human relationships, HTML parent elements can have many children. Elements at the same level of nesting are considered to be siblings.

Even though browsers ignore indentations when rendering an HTML page, we use indentation to make the level of nesting clear and readable for ourselves and other developers who will work with our HTML in the future. It is recommended to indent any child elements by two spaces.

The parent, child, and sibling relationships between elements will become much more important later when we start styling our HTML with CSS and adding behavior with JavaScript.

### HTML Comments
HTML comments are not visible to the browser; they allow us to comment on our code so that other developers or our future selves can read them and get some context about something that might not be clear in the code.

Writing an HTML comment is simple: We just enclose the comment with \<!-- and --> tags.

---

### Knowledge Check

**Q1.** How do you create a paragraph in HTML?

**A1.** To create a paragraph, we use the "\<p>" tag. Example: \<p>This is a paragraph.\</p>

**Q2.** How do you create a heading in HTML?

**A2.** We create headings in html with using \<h1>, \<h2>, \<h3>, \<h4>, \<h5>, \<h6> tags. Example: \<h1>This is a heading.\</h1>

**Q3.** How many different levels of headings are there and what is the difference between them?

**A3.** There are 6 different levels of headings in HTML. The difference between them is that the tag \<h1> has the biggest font size and the tag \<h2> has the smallest. These tags also give semantic meaning to the text, search engines like Google for example will put more importance to the text with \<h1> heading than the text with \<h2> heading.

**Q4.** What element should you use to make text bold and important?

**A4.** We should use the \<strong> tag to make text bold and important. Example: \<p>\<strong>This is important.\</strong> This is not.\</p>

**Q5.** What element should you use to make text italicized to add emphasis to it?

**A5.** We should use the \<em> tag to make text italicized and add emphasis to it. Example: \<p>\<em>This is emphasized.\</em> This is not.\</p>

**Q6.** What relationship does an element have with any nested elements within it?

**A6.** When an HTML element is nested within an another element, the nested element is called the "child element", and the element the child is nested within is called the "parent element". An element that is nested at the same level with the child, is called a "sibling element".

**Q7.** What relationship do two elements have if they are at the same level of nesting?

**A7.** An element that is nested at the same level with an another element, is called a "sibling element".

**Q8.** How do you create HTML comments?

**A8.** We use the following syntax to create comments on an HTML page: \<!-- This is an HTML comment -->

---

### Formatting elements aimed to display special types of text:

+ \<b> - <b>Bold text</b>
+ \<strong> - <strong>Important text</strong>
+ \<i> - <i>Italic text</i>
+ \<em> - <em>Emphasized text</em>
+ \<mark> - <mark>Marked text</mark>
+ \<small> - <small>Smaller text</small>
+ \<del> - <del>Deleted text</del>
+ \<ins> - <ins>Inserted text</ins>
+ \<sub> - <sub>Subscript text</sub>
+ \<sup> - <sup>Superscript text</sup>
