# Media Queries

### [MDN Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries "developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries")

Media queries are a fundamental component of responsive web design. They are a feature in CSS (Cascading Style Sheets) that allow web developers to apply different styles to a webpage based on various characteristics of the device or viewport where the page is being displayed. These characteristics can include factors such as screen size, resolution, orientation (landscape or portrait), and more.

Media queries allow developers to create flexible layouts that adapt to different devices and screen sizes, ensuring that websites look good and are usable across a wide range of devices, from desktop computers to smartphones and tablets.

### Media query syntax
The basic syntax for media queries is as follows:

```css
body {
  margin: 24px;
}

@media (max-width: 600px) {
  body {
    margin: 8px;
  }
}
```

In the above example, the margin is changed based on screen size. Specifically, on all screens below or equal to 600px, the margin will be 8px, and on all screens above 600px, it will be 24px.

Really, that’s all there is to it. You can create some complex shifting layouts with just this knowledge alone. You can create an unlimited number of media queries in a single document.

You can also put any number of style definitions inside a media query:

```css
body {
  margin: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
}
header {
  background: dodgerblue;
  padding: 32px 64px;
  font-size: 32px;
  color: white;
}
main {
  display: flex;
  flex: 1;
}
aside {
  width: 300px;
  flex-shrink: 0;
  background: palevioletred;
  color: white;
}
li {
  font-size: 24px;
  list-style-type: none;
}

section {
  padding: 16px;
  margin: 16px;
  font-size: 24px;
  background: blanchedalmond;
}

footer {
  height: 96px;
  background: darkslateblue;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (max-width: 800px) {
  main {
    flex-direction: column;
  }
  header {
    text-align: center;
    padding: 24px
  }
  aside {
    width: auto;
  }
  ul {
    display: flex;
    gap: 16px;
    justify-content: center;
    padding: 0;
  }
}
```

## Some Tips Regarding Media Queries
### Other queries
In all of the above examples, our queries specify a max-width which will apply styles to any screen resolution below the given style. Said another way: a max-width query will apply on any screen up to the defined max-width. It is also possible to define a min-width, which applies to screens that are larger than the given value. max-height and min-height are also valid.

### Limit media queries
As mentioned earlier, it is possible to create an unlimited number of media queries for every possible screen size. However, it is best to minimize your media-query usage and rely more on the natural flexibility of your layouts.

### Common breakpoints
‘Breakpoint’ is the term for the screen size that triggers your media query. You will find quite a lot of differing opinions on what exactly your breakpoints should be. In general, it’s helpful to think about the kinds of devices and screens that your users will be using. Mobile phones are usually under **500px**. Tablets are often between **500px** and **1000px**. Anything larger than **1000px** is likely to be a normal browser screen. Super wide screens are also becoming more common, which means that your site could end up being viewed on a screen wider than **2000px**!

This does not mean that you should just start your project with media queries for each device. Each project is going to have different requirements based on the design you’re trying to achieve. As mentioned above, try to limit your breakpoints to just what you need. With many relatively basic layouts, you can get by with only one mobile-centric breakpoint somewhere around 500-600px. **More complex layouts might benefit from doing a full-sized layout above 1200px, an altered “tablet” layout between 600px and 1200px and mobile below 600px.** The real takeaway here is that it doesn’t really matter exactly where you set your breakpoints, just do what makes sense for your project.

### Zooming!
In most browsers, zooming in on a webpage will change the effective resolution of that page. If your browser window is exactly 1000px wide, zooming in will cause the page to behave as if the screen is smaller, and will trigger media queries based on the simulated/zoomed screen resolution. Zooming out can be handy for debugging issues that arise on screens that are larger than your own computer screen.

## Print styles
You’ll often see media queries defined with the `screen` keyword like so:

```css
@media screen and (max-width: 480px) {
}
```

This is not necessary, but it does point toward another very useful capability of media queries: changing styles based on the media type. Everything we’ve covered so far has been specifically intended for viewing on some kind of screen so specifying `screen` is redundant. However, it is possible to create a different set of styles for your website when it is sent to your printer or viewed in print-preview mode by using the `print` keyword.

```css
@media print {
  /* print styles go here! */
}
```

This is not something we’re going to focus on in our curriculum, but it may be something you want to consider taking advantage of in some cases. It’s fairly common to change some colors (i.e. make things black/white), and add display: none to hide elements that are useless in a printed environment (buttons, nav links, etc).

---
### Knowledge Check

**Q1.** How do you define a media query to create a mobile layout for your site?

**A1.** The basic syntax for media queries is as follows:

```css
body {
  margin: 24px;
}

@media (max-width: 600px) {
  body {
    margin: 8px;
  }
}
```

In media queries a mobile centric breakpoint is usually somewhere around 500-600px.

**Q2.** What is the difference between max-width and min-width in a media query definition?

**A2.** A max-width query will apply on any screen up to the defined max-width. It is also possible to define a min-width, which applies to screens that are larger than the given value. max-height and min-height are also valid.