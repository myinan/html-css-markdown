# Accessibility Auditing
Accessibility auditing of a webpage involves assessing the website's design, content, and functionality to ensure that it can be easily accessed and used by people with disabilities. This process aims to identify and address any barriers that may prevent individuals with disabilities from fully utilizing and navigating the website.

Accessibility auditing typically involves a combination of manual evaluation and automated testing using various tools and guidelines, such as the Web Content Accessibility Guidelines (WCAG). These guidelines provide a set of recommendations for making web content more accessible to people with disabilities, covering areas such as text alternatives for non-text content, keyboard accessibility, color contrast, and more.

During an accessibility audit, auditors may review elements such as:

1. **Semantic HTML**: Ensuring proper use of HTML elements to provide structure and meaning to content.

2. **Keyboard Accessibility**: Verifying that all website functionalities can be accessed and operated using a keyboard only, without relying on a mouse or touch input.

3. **Alternative Text**: Checking that images have descriptive alternative text for screen reader users.

4. **Color Contrast**: Assessing the color contrast between text and background to ensure readability for users with visual impairments.

5. **Form Accessibility**: Ensuring that form elements are properly labeled and can be easily understood and completed by users with disabilities.

6. **Navigational Accessibility**: Reviewing the website's navigation to ensure that it is consistent, intuitive, and easy to use for all users.

7. **Multimedia Accessibility**: Verifying that audio and video content have captions, transcripts, or audio descriptions for users who are deaf or hard of hearing.

8. **Responsive Design**: Checking that the website is responsive and works well on different devices and screen sizes, including mobile devices and assistive technologies.

9. **Focus Management**: Verifying that focus is properly managed and maintained as users navigate through interactive elements on the website.

10. **Accessibility Testing Tools**: Utilizing automated accessibility testing tools to identify common accessibility issues and streamline the auditing process.

There are several automated accessibility testing tools available that can help streamline the process of evaluating a website's accessibility. These tools typically scan web pages and provide reports highlighting accessibility issues based on established guidelines such as the Web Content Accessibility Guidelines (WCAG). Here are some commonly used automated accessibility testing tools:

  1. **WAVE (Web Accessibility Evaluation Tool)**: WAVE is a free web accessibility evaluation tool provided by WebAIM. It allows users to enter a web page URL and generates a detailed report highlighting accessibility issues, along with visual indicators directly on the web page.

  2. **axe DevTools (formerly aXe)**: axe DevTools is a browser extension and command-line tool for testing web accessibility. It integrates directly into developer tools in browsers such as Chrome and Firefox, providing real-time feedback on accessibility issues as developers work on web pages.

  3. **Lighthouse**: Lighthouse is an open-source automated tool provided by Google for improving the quality of web pages. It includes an accessibility audit feature that checks for common accessibility issues and provides suggestions for improvement.

  4. **Pa11y**: Pa11y is an open-source accessibility testing tool that can be used from the command line, integrated into build processes, or accessed via a web interface. It allows users to test individual web pages or entire websites for accessibility issues.

These tools can significantly aid in identifying and addressing accessibility barriers on websites, but it's important to note that automated testing is not foolproof and may not catch all accessibility issues. Manual testing and expert evaluation are often necessary to ensure thorough accessibility compliance.

## Accessibility DevTools
When determining whether a page is accessible, you need to have 2 general questions in mind:

+ Can I navigate the page with a keyboard or screen reader?
+ Are the page's elements properly marked up for screen readers?

In general, DevTools can help you fix errors related to question #2, because these errors are easy to detect in an automated fashion. Question #1 is just as important, but unfortunately DevTools can't help you there. The only way to find errors related to question #1 is to try using a page with a keyboard or screen reader yourself.

In general, use the accessibility checks under the **Lighthouse** panel to determine if:

+ A page is properly marked up for screen readers.
+ The text elements on a page have sufficient contrast ratios.

To audit a page:

+ Go to the URL that you want to audit.
+ In DevTools, click the Lighthouse tab. DevTools shows you various configuration options.

You may prefer to use the aXe extension or Lighthouse extension rather than the Lighthouse panel that is available by default in Chrome. They generally provide the same information, since aXe is the underlying engine that powers the Lighthouse panel. The aXe extension has a different UI and describes audits slightly differently.

### The Accessibility Pane
The Accessibility pane is where you can view the accessibility tree, ARIA attributes, and computed accessibility properties of DOM nodes.

To open the Accessibility pane:

+ Click the Elements tab.
+ In the DOM Tree, select the element which you want to inspect.
+ Click the Accessibility tab. This tab may be hidden behind the More Tabs button.

The accessibility tree is a subset of the DOM tree. It only contains elements from the DOM tree that are relevant and useful for displaying the page's contents in a screen reader.

You can inspect an element's position in the accessibility tree from the Accessibility pane.

#### **Explore the full-page accessibility tree:**
The full-page view of the accessibility tree allows you to explore the whole tree and helps you better understand how your web content is exposed to assistive technology.

To explore the accessibility tree:

+ Check Enable full-page accessibility tree.
+ On the action bar at the top, click Reload DevTools.
+ In the upper right corner of the Elements panel, toggle the Switch to Accessibility Tree view button.
+ Browse the accessibility tree. You can expand nodes or click to see details under Computed properties.

#### **View an element's ARIA attributes:**
ARIA attributes ensure that screen readers have all of the information that they need in order to properly represent a page's contents.

You can view an element's ARIA attributes in the Accessibility pane.

### Discover and fix low contrast text with DevTools
Low contrast texts make your website less readable for all users, even more so for users with vision deficiencies. DevTools can automatically find low contrast issues and suggest better colors to help you fix them.

Use DevTools to:
+ **Discover contrast issues.** Use the CSS Overview panel, (the experimental) Issues tab, or a Lighthouse report to get a list of all issues.
+ **Fix contrast issues.** View the issues with a tooltip in inspector mode and select colors that the Color Picker suggests to fix the contrast ratio.

  To fix a low contrast issue:

  + Find a contrast issue and click a link to an affected element either on the CSS Overview panel, Issues tab, or Lighthouse report. DevTools takes you to the Elements panel and selects the corresponding element.
  + Click "Inspect" at the top-right corner of DevTools and hover over the element in the viewport. DevTools shows a tooltip for this element.
  + Open the Color Picker next to the color declaration of the element's text and, in the Color Picker, expand the Contrast ratio section.
  + Click the "Use suggested color" button next to the AAA level. The Color Picker applies the text color that complies to the contrast ratio guidelines.
  + Alternatively, to pick a color manually, you can drag the circle in the shades preview. To stay within the AA or AAA level, pick a color below the top or bottom line respectively.

+ **Emulate vision deficiencies.** Look at your site the way your users see it. You can emulate vision deficiencies from the "Rendering" panel of the DevTools.

## Accessibility Auditing with Third-Party Tools
There are plenty of third-party tools to audit the accessibility of a web page, each with its own pros and cons. Here, we’re only going to mention three of those tools. By getting into the habit of auditing your web pages, you’ll be able to track down any outstanding a11y issues that you may have missed. 

+ [axe DevTools for Chrome](https://chromewebstore.google.com/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US "axe-devtools") is an extension-based tool that returns a list of issues ranked by severity level, and will note any issues for you to manually check.

+ **Lighthouse for Chrome** is available in the Chrome DevTools by default (it might also be listed as the Auditing tab in older versions) or it can be run from the command line. Lighthouse provides more than just a11y auditing, including performance, best practices, search engine optimization (SEO), and progressive web app (PWA) if applicable. Issues are separated by category, and like the axe DevTools, there may be a list of issues for you to manually check.

+ [WebAIM’s WAVE](https://wave.webaim.org) is a website-based tool where you enter the URL of the page you want to audit. There are also browser extensions and API options. WAVE will return a preview of the page with an overlay of icons on it, and issues are separated into categories of alerts, warnings, and contrast errors. Unfortunately, the icons that are placed on the page may cause the layout to break, but that could be a minor issue if you’re more focused on the a11y issues that are found.

---
### Knowledge Check

**Q1.** What are some of the various accessibility features available in your browser’s DevTools?

**A1.** When determining whether a page is accessible, you need to have 2 general questions in mind:

+ Can I navigate the page with a keyboard or screen reader?
+ Are the page's elements properly marked up for screen readers?

In general, DevTools can help you fix errors related to question #2, because these errors are easy to detect in an automated fashion. Question #1 is just as important, but unfortunately DevTools can't help you there. The only way to find errors related to question #1 is to try using a page with a keyboard or screen reader yourself.

In general, use the accessibility checks under the **Lighthouse** panel to determine if:

+ A page is properly marked up for screen readers.
+ The text elements on a page have sufficient contrast ratios.

To audit a page:

+ Go to the URL that you want to audit.
+ In DevTools, click the Lighthouse tab. DevTools shows you various configuration options.

You may prefer to use the aXe extension or Lighthouse extension rather than the Lighthouse panel that is available by default in Chrome. They generally provide the same information, since aXe is the underlying engine that powers the Lighthouse panel. The aXe extension has a different UI and describes audits slightly differently.

### The Accessibility Pane
The Accessibility pane is where you can view the accessibility tree, ARIA attributes, and computed accessibility properties of DOM nodes.

To open the Accessibility pane:

+ Click the Elements tab.
+ In the DOM Tree, select the element which you want to inspect.
+ Click the Accessibility tab. This tab may be hidden behind the More Tabs button.

The accessibility tree is a subset of the DOM tree. It only contains elements from the DOM tree that are relevant and useful for displaying the page's contents in a screen reader.

You can inspect an element's position in the accessibility tree from the Accessibility pane.

#### **Explore the full-page accessibility tree:**
The full-page view of the accessibility tree allows you to explore the whole tree and helps you better understand how your web content is exposed to assistive technology.

To explore the accessibility tree:

+ Check Enable full-page accessibility tree.
+ On the action bar at the top, click Reload DevTools.
+ In the upper right corner of the Elements panel, toggle the Switch to Accessibility Tree view button.
+ Browse the accessibility tree. You can expand nodes or click to see details under Computed properties.

#### **View an element's ARIA attributes:**
ARIA attributes ensure that screen readers have all of the information that they need in order to properly represent a page's contents.

You can view an element's ARIA attributes in the Accessibility pane.

### Discover and fix low contrast text with DevTools
Low contrast texts make your website less readable for all users, even more so for users with vision deficiencies. DevTools can automatically find low contrast issues and suggest better colors to help you fix them.

Use DevTools to:
+ **Discover contrast issues.** Use the CSS Overview panel, (the experimental) Issues tab, or a Lighthouse report to get a list of all issues.
+ **Fix contrast issues.** View the issues with a tooltip in inspector mode and select colors that the Color Picker suggests to fix the contrast ratio.

  To fix a low contrast issue:

  + Find a contrast issue and click a link to an affected element either on the CSS Overview panel, Issues tab, or Lighthouse report. DevTools takes you to the Elements panel and selects the corresponding element.
  + Click "Inspect" at the top-right corner of DevTools and hover over the element in the viewport. DevTools shows a tooltip for this element.
  + Open the Color Picker next to the color declaration of the element's text and, in the Color Picker, expand the Contrast ratio section.
  + Click the "Use suggested color" button next to the AAA level. The Color Picker applies the text color that complies to the contrast ratio guidelines.
  + Alternatively, to pick a color manually, you can drag the circle in the shades preview. To stay within the AA or AAA level, pick a color below the top or bottom line respectively.

+ **Emulate vision deficiencies.** Look at your site the way your users see it. You can emulate vision deficiencies from the "Rendering" panel of the DevTools.

**Q2.** Which third-party accessibility auditing tool is available in the Chrome DevTools by default?

**A2.** **Lighthouse for Chrome** is available in the Chrome DevTools by default (it might also be listed as the Auditing tab in older versions) or it can be run from the command line. Lighthouse provides more than just a11y auditing, including performance, best practices, search engine optimization (SEO), and progressive web app (PWA) if applicable. Issues are separated by category and there may be a list of issues for you to manually check.

Lighthouse is an open-source, automated tool for improving the quality of web pages. You can run it against any web page, public or requiring authentication. It has audits for performance, accessibility, progressive web apps, SEO, and more.

You can run Lighthouse in Chrome DevTools, from the command line, or as a Node module. You give Lighthouse a URL to audit, it runs a series of audits against the page, and then it generates a report on how well the page did. From there, use the failing audits as indicators on how to improve the page. Each audit has a reference doc explaining why the audit is important, as well as how to fix it.

