# Responsive Images

## CSS `background` property
The background shorthand CSS property sets all background style properties at once, such as color, image, origin and size, or repeat method. Component properties not set in the background shorthand property value declaration are set to their default values.

CSS `background` property is a shorthand for the following CSS properties:

+ background-attachment
+ background-clip
+ background-color
+ background-image
+ background-origin
+ background-position
+ background-repeat
+ background-size

Syntax:

```css
/* Using a <background-color> */
background: green;

/* Using a <bg-image> and <repeat-style> */
background: url("test.jpg") repeat-y;

/* Using a <box> and <background-color> */
background: border-box red;

/* A single image, centered and scaled */
background: no-repeat center/80% url("../img/image.png");
```

### `background-size`
The background-size CSS property sets the size of the element's background image. The image can be left to its natural size, stretched, or constrained to fit the available space.

Spaces not covered by a background image are filled with the background-color property, and the background color will be visible behind background images that have transparency/translucency.

Syntax:

```css
/* Keyword values */
background-size: cover;
background-size: contain;

/* One-value syntax */
/* the width of the image (height becomes 'auto') */
background-size: 50%;
background-size: 3.2em;
background-size: 12px;
background-size: auto;

/* Two-value syntax */
/* first value: width of the image, second value: height */
background-size: 50% auto;
background-size: 3em 25%;
background-size: auto 6px;
background-size: auto auto;

/* Multiple backgrounds */
background-size: auto, auto; /* Not to be confused with `auto auto` */
background-size: 50%, 25%, 25%;
background-size: 6px, auto, contain;
```

The `background-size` property is specified in one of the following ways:

+ Using the keyword values contain or cover.
+ Using a width value only, in which case the height defaults to auto.
+ Using both a width and a height value, in which case the first sets the width and the second sets the height. Each value can be a \<length>, a \<percentage>, or auto.

To specify the size of multiple background images, separate the value for each one with a comma.

### `background-position`
The background-position CSS property sets the initial position for each background image. The position is relative to the position layer set by background-origin.

Syntax:

```css
/* Keyword values */
background-position: top;
background-position: bottom;
background-position: left;
background-position: right;
background-position: center;

/* <percentage> values */
background-position: 25% 75%;

/* <length> values */
background-position: 0 0;
background-position: 1cm 2cm;
background-position: 10ch 8em;

/* Multiple images */
background-position:
  0 0,
  center;

/* Edge offsets values */
background-position: bottom 10px right 20px;
background-position: right 3em bottom 10px;
background-position: bottom 10px right;
background-position: top right 10px;
```

## CSS Replaced Elements
In CSS, a replaced element is an element whose representation is outside the scope of CSS; they're external objects whose representation is independent of the CSS formatting model.

Put in simpler terms, they're elements whose contents are not affected by the current document's styles. The position of the replaced element can be affected using CSS, but not the contents of the replaced element itself. 

Typical replaced elements are:

+ \<iframe>
+ \<video>
+ \<embed>
+ \<img>

Objects inserted using the CSS `content` property are *anonymous replaced elements*. They are "anonymous" because they don't exist in the HTML markup.

The only impact CSS can have on a replaced element is that there are properties which support controlling the positioning of the element's content within its box. Certain CSS properties can be used to specify how the object contained within the replaced element should be positioned within the element's box area. These properties are: `object-fit` (Specifies how the replaced element's content object should be fitted to the containing element's box.) and `object-position` (Specifies the alignment of the replaced element's content object within the element's box.)

### `object-fit`
The object-fit CSS property sets how the content of a replaced element, such as an \<img> or \<video>, should be resized to fit its container.

You can alter the alignment of the replaced element's content object within the element's box using the object-position property.

Syntax:

```css
object-fit: contain;
object-fit: cover;
object-fit: fill;
object-fit: none;
object-fit: scale-down;
```

Example:

```html
<section>
  <h2>object-fit: fill</h2>
  <img class="fill" src="mdn_logo_only_color.png" alt="MDN Logo" />

  <h2>object-fit: contain</h2>
  <img class="contain" src="mdn_logo_only_color.png" alt="MDN Logo" />
```

```css
h2 {
  font-family:
    Courier New,
    monospace;
  font-size: 1em;
  margin: 1em 0 0.3em;
}

img {
  width: 150px;
  height: 100px;
  border: 1px solid #000;
  margin: 10px 0;
}

.fill {
  object-fit: fill;
}

.contain {
  object-fit: contain;
}
```

### `object-position`
The object-position CSS property specifies the alignment of the selected replaced element's contents within the element's box. Areas of the box which aren't covered by the replaced element's object will show the element's background.

You can adjust how the replaced element's object's intrinsic size (that is, its natural size) is adjusted to fit within the element's box using the object-fit property.

Syntax:

```css
/* Keyword values */
object-position: top;
object-position: bottom;
object-position: left;
object-position: right;
object-position: center;

/* <percentage> values */
object-position: 25% 75%;

/* <length> values */
object-position: 0 0;
object-position: 1cm 2cm;
object-position: 10ch 8em;

/* Edge offsets values */
object-position: bottom 10px right 20px;
object-position: right 3em bottom 10px;
object-position: top 0 right 10px;
```

## HTML `<img>` element
The `<img>` HTML element embeds an image into the document.

The HTML standard doesn't list what image formats to support, so user agents may support different formats.

### Image loading errors
If an error occurs while loading or rendering an image, and an `onerror` event handler has been set for the `error` event, that event handler will get called. This can happen in several situations, including:

+ The src attribute is empty ("") or null.
+ The src URL is the same as the URL of the page the user is currently on.
+ The image is corrupted in some way that prevents it from being loaded.
+ The image's metadata is corrupted in such a way that it's impossible to retrieve its dimensions, and no dimensions were specified in the \<img> element's attributes.
+ The image is in a format not supported by the user agent.

### Attributes
`alt`: Defines text that can replace the image in the page.

+ Setting this attribute to an empty string (alt="") indicates that this image is not a key part of the content (it's decoration or a tracking pixel), and that non-visual browsers may omit it from rendering. Visual browsers will also hide the broken image icon if the alt attribute is empty and the image failed to display.

+ This attribute is also used when copying and pasting the image to text, or saving a linked image to a bookmark.

`fetchpriority`: Provides a hint of the relative priority to use when fetching the image. Allowed values:

+ high: Signals a high-priority fetch relative to other images.
+ low: Signals a low-priority fetch relative to other images.
+ auto: (Default) Signals automatic determination of fetch priority relative to other images.

`height`: The intrinsic height of the image, in pixels. Must be an integer without a unit.

+ Note: Including height and width enables the aspect ratio of the image to be calculated by the browser prior to the image being loaded. This aspect ratio is used to reserve the space needed to display the image, reducing or even preventing a layout shift when the image is downloaded and painted to the screen. Reducing layout shift is a major component of good user experience and web performance.

`loading`: Indicates how the browser should load the image.

+ eager: Loads the image immediately, regardless of whether or not the image is currently within the visible viewport (this is the default value).

+ lazy: Defers loading the image until it reaches a calculated distance from the viewport, as defined by the browser. The intent is to avoid the network and storage bandwidth needed to handle the image until it's reasonably certain that it will be needed. This generally improves the performance of the content in most typical use cases.

`sizes`: One or more strings separated by commas, indicating a set of source sizes. Each source size consists of:

+ A media condition. This must be omitted for the last item in the list.
+ A source size value.

    + Media Conditions describe properties of the viewport, not of the image. For example, (max-height: 500px) 1000px proposes to use a source of 1000px width, if the viewport is not higher than 500px.

    + Source size values specify the intended display size of the image. User agents use the current source size to select one of the sources supplied by the srcset attribute, when those sources are described using width (w) descriptors. The selected source size affects the intrinsic size of the image (the image's display size if no CSS styling is applied). If the srcset attribute is absent, or contains no values with a width descriptor, then the sizes attribute has no effect.

`src`: The image URL. Mandatory for the \<img> element. 

`srcset`: One or more strings separated by commas, indicating possible image sources for the user agent to use. Each string is composed of:

+ A URL to an image
+ Optionally, whitespace followed by one of:
    + A width descriptor (a positive integer directly followed by w). The width descriptor is divided by the source size given in the sizes attribute to calculate the effective pixel density.
    + A pixel density descriptor (a positive floating point number directly followed by x).

+ If the srcset attribute uses width descriptors, the sizes attribute must also be present, or the srcset itself will be ignored.

`width`: The intrinsic width of the image in pixels. Must be an integer without a unit.

### Styling with CSS
`<img>` is a replaced element; it has a `display` value of `inline` by default, but its default dimensions are defined by the embedded image's intrinsic values, like it were inline-block. You can set properties like `border`/`border-radius`, `padding/margin`, `width`, `height`, etc. on an image.

You can use the `object-position` property to position the image within the element's box, and the `object-fit` property to adjust the sizing of the image within the box (for example, whether the image should fit the box or fill it even if clipping is required).

Depending on its type, an image may have an intrinsic width and height. For some image types, however, intrinsic dimensions are unnecessary. SVG images, for instance, have no intrinsic dimensions if their root \<svg> element doesn't have a width or height set on it.

### Example
```html
<img
  src="clock-demo-200px.png"
  alt="The time is 12:45."
  srcset="clock-demo-200px.png 200w, clock-demo-400px.png 400w"
  sizes="(max-width: 600px) 200px, 50vw" />
```

## HTML `<picture>` element
The `<picture>` HTML element contains zero or more `<source>` elements and one `<img>` element to offer alternative versions of an image for different display/device scenarios.

The browser will consider each child \<source> element and choose the best match among them. If no matches are found—or the browser doesn't support the \<picture> element—the URL of the \<img> element's src attribute is selected. The selected image is then presented in the space occupied by the \<img> element.

Common use cases for `<picture>`:

+ **Art direction.** Cropping or modifying images for different media conditions (for example, loading a simpler version of an image which has too many details, on smaller displays).
+ **Offering alternative image formats**, for cases where certain formats are not supported.
+ **Saving bandwidth and speeding page load times** by loading the most appropriate image for the viewer's display.

If providing higher-density versions of an image for high-DPI (Retina) display, use srcset on the `<img>` element instead. This lets browsers opt for lower-density versions in data-saving modes, and you don't have to write explicit media conditions.

```html
<picture>
  <source srcset="mdn-logo-wide.png" media="(min-width: 600px)" />
  <img src="mdn-logo-narrow.png" alt="MDN" />
</picture>
```

## Responsive Images Deep Dive
When aiming for responsive images, an improvement would be to display a cropped version of the image which displays the important details of the image when the site is viewed on a narrow screen. A second cropped image could be displayed for a medium-width screen device, like a tablet. The general problem whereby you want to serve different cropped images in that way, for various layouts, is commonly known as the **art direction problem**.

In addition, there is no need to embed such large images on the page if it is being viewed on a mobile screen. Doing so can waste bandwidth; in particular, mobile users don't want to waste bandwidth by downloading a large image intended for desktop users, when a small image would do for their device. Conversely, a small raster image starts to look grainy when displayed larger than its original size (a raster image is a set number of pixels wide and a set number of pixels tall, unlike vector graphics). Ideally, multiple resolutions would be made available to the user's web browser. The browser could then determine the optimal resolution to load based on the screen size of the user's device. This is called the **resolution switching problem**.

To make things more complicated, some devices have high resolution screens that need larger images than you might expect to display nicely. This is essentially the same problem, but in a slightly different context.

You might think that vector images would solve these problems, and they do to a certain degree — they are small in file size and scale well, and you should use them wherever possible. However, they aren't suitable for all image types. Vector images are great for simple graphics, patterns, interface elements, etc., but it starts to get very complex to create a vector-based image with the kind of detail that you'd find in say, a photo. Raster image formats such as JPEGs are more suited to the kind of images that contain lots of detail.

This kind of problem didn't exist when the web first existed, in the early to mid 90s — back then the only devices in existence to browse the Web were desktops and laptops, so browser engineers and spec writers didn't even think to implement solutions. Responsive image technologies were implemented recently to solve the problems that comes with serving a website to devices across varying resolutions, by letting you offer the browser several image files, either all showing the same thing but containing different numbers of pixels **(resolution switching)**, or different images suitable for different space allocations **(art direction)**.

Note: The new features discussed below — srcset/sizes/\<picture> — are all supported in modern desktop and mobile browsers.<br>
Also, you should note that we will be focusing on \<img> elements for this section, and not CSS background images.

### Resolution switching: Different sizes
So, what is the problem that we want to solve with resolution switching? We want to display identical image content, just larger or smaller depending on the device.

The standard \<img> element traditionally only lets you point the browser to a single source file:

```html
<img src="elva-fairy-800w.jpg" alt="Elva dressed as a fairy" />
```

We can however use two attributes — `srcset` and `sizes` — to provide several additional source images along with hints to help the browser pick the right one.

```html
<img
  srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"
  sizes="(max-width: 600px) 480px,
         800px"
  src="elva-fairy-800w.jpg"
  alt="Elva dressed as a fairy" />
```

The srcset and sizes attributes look complicated, but they're not too hard to understand if you format them as shown above, with a different part of the attribute value on each line. Each value contains a comma-separated list, and each part of those lists is made up of three sub-parts. Let's run through the contents of each now:

`srcset` defines the set of images we will allow the browser to choose between, and what size each image is. Each set of image information is separated from the previous one by a comma. For each one, we write:

1. An image filename (elva-fairy-480w.jpg)
2. A space
3. The image's intrinsic width in pixels (480w) — note that this uses the `w` unit, not `px` as you might expect. An image's intrinsic size is its real size, which can be found by inspecting the image file on your computer.

`sizes` defines a set of media conditions (e.g. screen widths) and indicates what image size would be best to choose, when certain media conditions are true — these are the hints we talked about earlier. In this case, before each comma we write:

1. A media condition ((max-width:600px)) — a media condition describes a possible state that the screen can be in. In this case, we are saying "when the viewport width is 600 pixels or less".
2. A space
3. The **width of the slot** the image will fill when the media condition is true (480px)

Note: For the slot width, rather than providing an absolute width (for example, 480px), you can alternatively provide a width relative to the viewport (for example, 50vw) — but not a percentage. You may have noticed that the last slot width has no media condition (this is the default that is chosen when none of the media conditions are true). The browser ignores everything after the first matching condition, so be careful how you order the media conditions.

So, with these attributes in place, the browser will:

+ Look at screen size, pixel density, zoom level, screen orientation, and network speed.
+ Work out which media condition in the sizes list is the first one to be true.
+ Look at the slot size given to that media query.
+ Load the image referenced in the srcset list that has the same size as the slot or, if there isn't one, the first image that is bigger than the chosen slot size.

And that's it! At this point, if a supporting browser with a viewport width of 480px loads the page, the (max-width: 600px) media condition will be true, and so the browser chooses the 480px slot. The elva-fairy-480w.jpg will be loaded, as its inherent width (480w) is closest to the slot size. The 800px picture is 128KB on disk, whereas the 480px version is only 63KB — a saving of 65KB. Now, imagine if this was a page that had many pictures on it. Using this technique could save mobile users a lot of bandwidth.

Older browsers that don't support these features will just ignore them. Instead, those browsers will go ahead and load the image referenced in the `src` attribute as normal.

### Resolution switching: Same size, different resolutions
If you're supporting multiple display resolutions, but everyone sees your image at the same real-world size on the screen, you can allow the browser to choose an appropriate resolution image by using `srcset` with x-descriptors and without `sizes`.

```html
<img
  srcset="elva-fairy-320w.jpg, elva-fairy-480w.jpg 1.5x, elva-fairy-640w.jpg 2x"
  src="elva-fairy-640w.jpg"
  alt="Elva dressed as a fairy" />
```

In this example, the following CSS is applied to the image so that it will have a width of 320 pixels on the screen (also called CSS pixels):

```css
img {
  width: 320px;
}
```

In this case, sizes is not needed — the browser works out what resolution the display is that it is being shown on, and serves the most appropriate image referenced in the srcset. So if the device accessing the page has a standard/low resolution display, with one device pixel representing each CSS pixel, the elva-fairy-320w.jpg image will be loaded (the 1x is implied, so you don't need to include it.) If the device has a high resolution of two device pixels per CSS pixel or more, the elva-fairy-640w.jpg image will be loaded. The 640px image is 93KB, whereas the 320px image is only 39KB.

### Art direction
To recap, the **art direction problem** involves wanting to change the image displayed to suit different image display sizes. For example, a web page includes a large landscape shot with a person in the middle when viewed on a desktop browser. When viewed on a mobile browser, that same image is shrunk down, making the person in the image very small and hard to see. It would probably be better to show a smaller, portrait image on mobile, which zooms in on the person. The `<picture>` element allows us to implement just this kind of solution.

```html
<img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva" />
```

Let's fix this, with `<picture>`! Like `<video>` and `<audio>`, the `<picture>` element is a wrapper containing several `<source>` elements that provide different sources for the browser to choose from, followed by the all-important `<img>` element.

```html
<picture>
  <source media="(max-width: 799px)" srcset="elva-480w-close-portrait.jpg" />
  <source media="(min-width: 800px)" srcset="elva-800w.jpg" />
  <img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva" />
</picture>
```

you must provide an \<img> element, with src and alt, right before \</picture>, otherwise no images will appear. This provides a default case that will apply when none of the media conditions return true (you could actually remove the second \<source> element in this example), and a fallback for browsers that don't support the \<picture> element.

This code allows us to display a suitable image on both wide screen and narrow screen displays.

### Why can't we just do this using CSS or JavaScript?
When the browser starts to load a page, it starts to download (preload) any images before the main parser has started to load and interpret the page's CSS and JavaScript. That mechanism is useful in general for reducing page load times, but it is not helpful for responsive images — hence the need to implement solutions like srcset. For example, you couldn't load the \<img> element, then detect the viewport width with JavaScript, and then dynamically change the source image to a smaller one if desired. By then, the original image would already have been loaded, and you would load the small image as well, which is even worse in responsive image terms.

---
### Knowledge Check

**Q1.** What is the main difference between object-fit and background-size?

**A1.** The `object-fit` CSS property sets how the content of a replaced element, such as an \<img> or \<video>, should be resized to fit its container.

The `background-size` CSS property sets the size of the element's background image. The image can be left to its natural size, stretched, or constrained to fit the available space.

**Q2.** How can you define a width and a height on an img without distorting it?

**A2.** The most basic problem you are going to face when working with responsive images is the aspect ratio or the relationship between width and height. If you shrink the width of an image on smaller screens and do not manipulate the height, the image will appear distorted!

The solution to this issue is incredibly easy, and we’ve already mentioned it in an earlier lesson: don’t define both a width and a height. **If an image is given a flexible width, and the height is set to `auto`, then it should retain its aspect ratio correctly.**

**Q3.** Why would you want to provide different images at different screen resolutions?

**A3.** When aiming for responsive images, an improvement would be to display a cropped version of the image which displays the important details of the image when the site is viewed on a narrow screen. A second cropped image could be displayed for a medium-width screen device, like a tablet. The general problem whereby you want to serve different cropped images in that way, for various layouts, is commonly known as the **art direction problem**.

In addition, there is no need to embed such large images on the page if it is being viewed on a mobile screen. Doing so can waste bandwidth; in particular, mobile users don't want to waste bandwidth by downloading a large image intended for desktop users, when a small image would do for their device. Conversely, a small raster image starts to look grainy when displayed larger than its original size (a raster image is a set number of pixels wide and a set number of pixels tall, unlike vector graphics). Ideally, multiple resolutions would be made available to the user's web browser. The browser could then determine the optimal resolution to load based on the screen size of the user's device. This is called the **resolution switching problem**.

To make things more complicated, some devices have high resolution screens that need larger images than you might expect to display nicely. This is essentially the same problem, but in a slightly different context.

You might think that vector images would solve these problems, and they do to a certain degree — they are small in file size and scale well, and you should use them wherever possible. However, they aren't suitable for all image types. Vector images are great for simple graphics, patterns, interface elements, etc., but it starts to get very complex to create a vector-based image with the kind of detail that you'd find in say, a photo. Raster image formats such as JPEGs are more suited to the kind of images that contain lots of detail.

This kind of problem didn't exist when the web first existed, in the early to mid 90s — back then the only devices in existence to browse the Web were desktops and laptops, so browser engineers and spec writers didn't even think to implement solutions. Responsive image technologies were implemented recently to solve the problems that comes with serving a website to devices across varying resolutions, by letting you offer the browser several image files, either all showing the same thing but containing different numbers of pixels **(resolution switching)**, or different images suitable for different space allocations **(art direction)**.

**Q4.** When would you want to use an \<img> with a srcset vs a \<picture>?

**A4.** The `<img srcset="" src="" alt="">` syntax is for serving differently-sized versions of the *same* image. You could try to serve entirely different images using this syntax, but browsers assume that everything in a srcset is visually-identical and will choose whichever size they think is best, in impossible-for-you-to-predict ways. So I wouldn’t recommend it.

We have already established that `<img srcset="" sizes="" alt="">` is for serving differently-sized versions of the same image. The `<picture>` syntax can do that too, but the difference here is that the browser must respect the rules that you set. That’s useful when you want to change more than just the resolution of the loaded image to fit the user’s situation. This intentional **changing of the image** is usually called “art direction.”

```html
<picture>
  <source 
    srcset="baby-zoomed-out.jpg"
    media="(min-width: 1000px)"
  />
  <source 
    srcset="baby.jpg"
    media="(min-width: 600px)"
  />
  <img 
    src="baby-zoomed-in.jpg" 
    alt="Baby Sleeping"
  />
</picture>
```

Because \<source> also uses the srcset syntax, they can be combined. This means that you can still reap the performance benefits of srcset even while swapping out visually-different images with \<source>.

```html
<picture>
  <source 
    srcset="
      baby-zoomed-out-2x.jpg 2x,
      baby-zoomed-out.jpg
    "
    media="(min-width: 1000px)"
  />
  <source 
    srcset="
      baby-2x.jpg 2x,
      baby.jpg
    "
    media="(min-width: 600px)"
  />
  <img 
    srcset="
      baby-zoomed-out-2x.jpg 2x
    "
    src="baby-zoomed-out.jpg"
    alt="Baby Sleeping"
  />
</picture>
```

**Fallbacks for modern image formats:**<br>
The `<picture>` element is uniquely suited to being able to handle “fallbacks.” That is, images in cutting-edge formats that not all browsers might be able to handle, with alternative formats for browsers that can’t load the preferred, fancy one. For example, let’s say you want to use an image in the **WebP** format. It’s a pretty great image format, often being the most performant choice, and it’s supported everywhere that the `<picture>` element is, except Safari. You can handle that situation yourself, like:

```html
<picture>
  <source srcset="party.webp">
  <img src="party.jpg" alt="A huge party with cakes.">
</picture>
```

This succeeds in serving a WebP image to browsers that support it, and falls back to a JPEG image, which is definitely supported by all browsers.