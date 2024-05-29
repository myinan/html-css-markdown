# Links and Images

## Links

To create a link in HTML, we use the anchor element. An anchor element is defined by wrapping the text or another HTML element we want to be a link with an **\<a>** tag.

\<a>click me\</a>

You may have noticed that clicking this link doesn’t do anything. This is because an anchor tag on its own won’t know where we want to link to. We have to tell it a destination to go to. We do this by using an HTML attribute.

An HTML attribute gives additional information to an HTML element and always goes in the element’s opening tag. An attribute is usually made up of two parts: a name(key), and a value; however, not all attributes require a value. In our case, we need to add a href (hyperlink reference) attribute to the opening anchor tag. The value of the href attribute is the destination we want our link to go to.

\<a href="https://www.theodinproject.com/about">click me\</a>

By default, any text wrapped with an anchor tag without a href attribute will look like plain text. If the href attribute is present, the browser will give the text a blue color and underline it to signify it is a link.

It’s worth noting you can use anchor tags to link to any kind of resource on the internet, not just other HTML documents. You can link to videos, pdf files, images, and so on, but for the most part, you will be linking to other HTML documents.

### Absolute and relative links

Generally, there are two kinds of links we will create:

Links to pages on other websites on the internet
Links to pages located on our own websites

#### Absolute links

Links to pages on other websites on the internet are called absolute links. A typical absolute link will be made up of the following parts: protocol://domain/path. An absolute link will always contain the protocol and domain of the destination.

We’ve already seen an absolute link in action. The link we created to The Odin Project’s About page earlier was an absolute link as it contains the protocol and domain.

https://www.theodinproject.com/about

#### Relative links

Links to other pages within our own website are called relative links. Relative links do not include the domain name, since it is another page on the same site, it assumes the domain name will be the same as the page we created the link on.

Relative links only include the file path to the other page, relative to the page you are creating the link on.

\<a href="about.html">About\</a>

Clicking the link should go to the about page we just created.

This works because the index and about page are in the same directory. That means we can simply use its name (about.html) as the link’s href value.

But we will usually want to organize our website directories a little better. Normally we would only have the index.html at the root directory and all other HTML files in their own directory.

## Images

Websites would be fairly boring if they could only display text. Luckily HTML provides a wide variety of elements for displaying all sorts of different media.

To display an image in HTML we use the \<img> element. Unlike the other elements we have encountered, the \<img> element is self-closing. Empty, self-closing HTML elements do not need a closing tag.

Instead of wrapping content with an opening and closing tag, it embeds an image into the page using a src attribute which tells the browser where the image file is located. The src attribute works much like the href attribute for anchor tags. It can embed an image using both absolute and relative paths.

\<img src="https://www.theodinproject.com/mstile-310x310.png">

OR

\<img src="./images/dog.jpg">

### Alt Attribute

Besides the src attribute, every image element must also have an alt (alternative text) attribute.

The alt attribute is used to describe an image. It will be used in place of the image if it cannot be loaded. It is also used with screen readers to describe what the image is to visually impaired users.

This is how the The Odin Project logo example we used earlier looks with an alt attribute included:

\<img src="https://www.theodinproject.com/mstile-310x310.png" alt="The Odin Project Logo">

---

### Knowledge Check

**Q1.** What element is used to create a link?

**A1.** "\<a>" (anchor tag) is used to create links on an HTML page.

**Q2.** What is an attribute?

**A2.** An HTML attribute is a piece of markup language used to adjust the behaviour or display of an HTML element. For example, attributes can be used to change the color, size or functionality of HTML elements.

**Q3.** What attribute tells links where to go to?

**A3.** "href" attribute has to be used with the "\<a>" tag to specify the link. Example: \<a href="https://www.google.com">

**Q4.** What is the difference between an absolute and relative link?

**A4.** Absolute link specifies the link with it's absolute path. For example, "https://www.google.com/search" is an absolute link. It specifies the protocol, domain adress and the path. A relative link on the other hand is a link only relative to the current page. If the current html page is on a directory called "pages" and we want to create a link to an image that lives on a directory called "images", if these two directories share the same parent directory our relative link would be as this: "../images/image.jpg" .

**Q5.** Which element is used to display an image?

**A5.** The "\<img>" element is used to display images.

**Q6.** What two attributes do images always need to have?

**A6.** an "\<img>" element always need to have these two attributes: 1- the "src" attribute which contains the link to the image we want to display, 2- the "alt" (alternative text) attribute which provides additional information regarding the image in case the browser fails to render the image. The other use for the "alt" tag is that it provides a description of an image to screenreaders.

**Q7.** How do you access a parent directory in a filepath?

**A7.** We use "../" to access the parent directory.

**Q8.** What are the four main image formats that you can use for images on the web?

**A8.** 1-JPG, 2-GIF, 3-PNG, 4-SVG.




