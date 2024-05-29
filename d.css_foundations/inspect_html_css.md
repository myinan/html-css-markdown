# Inspecting HTML and CSS
Being able to inspect and debug your HTML and CSS is critical to frontend development. This lesson will take us through the Chrome Dev Tools, which allow you to see detailed information about your elements and CSS rules, as well as assist you in finding and fixing problems in your code.

## The Inspector
To open up the inspector, you can right-click on any element of a webpage and click “Inspect” or press F12.

## Inspecting Elements
In the Elements pane, you can see the entire HTML structure of your page. You can click on any of the elements in this pane to select that specific element.

When an element is selected, the Styles tab will show all the currently applied styles, as well as any styles that are being overwritten (indicated by a strikethrough of the text). 

## Testing Styles in the Inspector
The Styles pane also allows you to edit styles directly in the browser. You can click inside of any individual selector to add a new rule or click on an existing attribute or value to alter it. When doing so, the webpage responds with the changes in real-time. This won’t affect the source code in your text editor, but it is extremely useful for quickly testing out various attributes and values without needing to reload the page over and over again.

### Official Chrome DevTools Documentation

[Chrome DevTools docs](https://developer.chrome.com/docs/devtools/)

---

### Knowledge Check

**Q1.** How do you select a specific element on your page with your browser’s developer tools?

**A1.** 1- Right click on the element then click inspect. 2- Open the developer tools, open the search bar with Ctrl + F, then search the specific element you want to select. 3- Select the element from the DOM tree on the Developer Tools' "Elements" panel.

**Q2.** What does a strikethrough in a CSS declaration mean in your browser’s developer tools?

**A2.** It means that, striked CSS declaration is overwritten by another more specific CSS rule.

**Q3.** How do you change CSS in real time on specific elements of a web page with your browser’s developer tools?

**A3.** We can add new CSS declerations from the "Styles" pane in Developer Tools. We can also toggle current applied CSS declarations on and off from the "Styles" pane. From the "Styles" pane, we can add classes or force element states to an element.

---

[Utilize css overview in the developer tools to check the colors, font styles, media-queries, etc. used on a particular webpage](https://www.freecodecamp.org/news/how-to-use-css-overview-in-chrome-developer-tools/)