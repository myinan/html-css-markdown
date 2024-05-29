# `transition`
The `transition` property in CSS is used to control the smoothness of transitions between different property values over a specified duration. It allows you to define how a CSS property should change over time when triggered by events like hovering over an element, focusing on it, or other user interactions.

Here's a breakdown of the `transition` property:

1. **Syntax**:
   ```
   transition: property duration timing-function delay;
   ```

   - `property`: Specifies the CSS property you want to transition. This can be any valid CSS property, such as `color`, `opacity`, `width`, `height`, etc. You can specify multiple properties separated by commas to apply the transition effect to multiple properties simultaneously.
   - `duration`: Specifies the duration over which the transition should occur. It is expressed in seconds (s) or milliseconds (ms).
   - `timing-function`: Defines the acceleration curve of the transition. It determines how the intermediate values of the CSS properties are calculated over time. Timing functions like `linear`, `ease`, `ease-in`, `ease-out`, and `ease-in-out` are commonly used. Additionally, you can define custom timing functions using cubic bezier curves.
   - `delay`: Optional. Specifies a delay before the transition starts. It is also expressed in seconds (s) or milliseconds (ms).

2. **Example**:
   ```css
   .box {
       width: 100px;
       height: 100px;
       background-color: blue;
       transition: width 2s ease-in-out 0.5s, height 2s linear;
   }
   .box:hover {
       width: 200px;
       height: 200px;
   }
   ```

   In this example, when you hover over the `.box` element, its width and height will transition smoothly over a duration of 2 seconds. The width will have an easing effect (`ease-in-out`) with a 0.5-second delay, while the height will transition linearly over the same duration without any delay.

3. **Usage**:
   - Commonly used for creating smooth animations and transitions in web design.
   - Provides a more polished and interactive user experience.
   - Used for effects like fading, sliding, scaling, and more.
   - Enhances usability by providing visual feedback for user interactions.

4. **Browser Support**:
   - `transition` is widely supported in modern web browsers, including Chrome, Firefox, Safari, Edge, and Opera.
   - Vendor prefixes (`-webkit-transition`, `-moz-transition`, `-ms-transition`, `-o-transition`) were used in older versions of some browsers, but they are rarely necessary nowadays.

Overall, the `transition` property in CSS is a powerful tool for creating engaging and interactive user interfaces on the web. It allows developers to add fluidity and polish to their designs with relatively simple CSS code.

### The `transition` property in CSS is a shorthand property
The `transition` property in CSS is a shorthand for several individual transition-related properties. Let's break down each of them:

1. **`transition-property`**:
   - This property specifies the CSS properties that should transition when their values change.
   - It accepts one or more property names as values.
   - If multiple properties are specified, each property can have its own transition settings.

   ```css
   transition-property: width height background-color;
   ```

2. **`transition-duration`**:
   - It defines the duration over which the transition should occur.
   - It can be specified in seconds (s) or milliseconds (ms).

   ```css
   transition-duration: 2s;
   ```

3. **`transition-timing-function`**:
   - This property determines the acceleration curve of the transition.
   - It specifies how the intermediate values of the CSS properties are calculated over time.
   - Common transition-timing-function property values include `linear`, `ease`, `ease-in`, `ease-out`, and `ease-in-out`.
   
   ```css
   transition-timing-function: ease-in-out;
   ```

   - We can also use the cubic-bezier function to create custom timing functions.
   
   ```css
   transition-timing-function: cubic-bezier(0.42, 0, 0.58, 1); /* Example cubic bezier timing function */`
   ```

   In the cubic bezier function, the four values (x1, y1, x2, y2) define the acceleration curve. These values represent control points on a cubic Bezier curve where (0,0) is the start point and (1,1) is the end point.

4. **`transition-delay`**:
   - It specifies a delay before the transition starts.
   - The value can be specified in seconds (s) or milliseconds (ms).

   ```css
   transition-delay: 0.5s;
   ```

5. **`transition-behavior`**:
   - This property is used to control the behavior of the transition in response to changes in the underlying styles.
   - It's less commonly used and has limited browser support.

   ```css
   transition-behavior: auto;
   ```

Here's how you can use the individual transition properties:

```css
.element {
    /* transition-property */
    transition-property: width, height, background-color;

    /* transition-duration */
    transition-duration: 2s;

    /* transition-timing-function */
    transition-timing-function: ease-in-out;

    /* transition-delay */
    transition-delay: 0.5s;

    /* transition-behavior */
    transition-behavior: auto;
}
```

Using the `transition` shorthand property, you can combine all these individual properties into a single declaration, which can make your CSS cleaner and more concise:

```css
.element {
    transition: width 2s ease-in-out 0.5s, height 2s linear 0s, background-color 2s ease 0.5s;
}
```

In this shorthand declaration, each transition effect for different properties is separated by commas, and each effect includes the property name, duration, timing function, and delay.

## Transitioning `display` and `content-visibility`
`display` and `content-visibility` can be transitioned. This behavior is useful for creating entry/exit animations where you want to for example remove a container from the DOM with `display: none`, but have it fade out with opacity rather than disappearing immediately.

+ When animating display from none to block (or another visible display value), the value will flip to block at 0% of the animation duration so it is visible throughout.

+ When animating display from block (or another visible display value) to none, the value will flip to none at 100% of the animation duration so it is visible throughout.

**When transitioning these properties `transition-behavior: allow-discrete` needs to be set on the transitions. This effectively enables *display/content-visibility* transitions.**

When transitioning `display`, `@starting-style` is needed to provide a set of starting values for properties set on an element that you want to transition from when the element receives its first style update. This is needed to avoid unexpected behavior. By default, CSS transitions are not triggered on elements' first style updates when they first appear in the DOM, which includes when `display` changes from none to another state. `content-visibility` animations do not need starting values specified in a `@starting-style` block. This is because `content-visibility` doesn't hide an element from the DOM like `display` does: it just skips rendering the element's content.

```css
html {
  height: 100vh;
}

div {
  font-size: 1.6rem;
  padding: 20px;
  border: 3px solid red;
  border-radius: 20px;
  width: 480px;

  display: none;
  opacity: 0;
  transition:
    opacity 1s,
    display 1s allow-discrete;
  /* Equivalent to
  transition: all 1s allow-discrete; */
}

.showing {
  opacity: 1;
  display: block;
}

@starting-style {
  .showing {
    opacity: 0;
  }
}
```

Note the `@starting-style` block used to specify the starting style for the transition, and the inclusion of the `display` property in the transitions list, with `allow-discrete` set on it.

## Detecting the start and completion of a transition with JS
You can use the `transitionend` event to detect that an animation has finished running. This is a `TransitionEvent` object, which has two added properties beyond a typical `Event` object:

+ propertyName: A string indicating the name of the CSS property whose transition completed.
+ elapsedTime: A float indicating the number of seconds the transition had been running at the time the event fired. This value isn't affected by the value of *transition-delay*.

As usual, you can use the `addEventListener()` method to monitor for this event:

```js
el.addEventListener("transitionend", updateTransition, true);
```

You detect the beginning of a transition using `transitionrun` (fires before any delay) and `transitionstart` (fires after any delay), in the same kind of fashion:

```js
el.addEventListener("transitionrun", signalStart, true);
el.addEventListener("transitionstart", signalStart, true);
```

Note: The transitionend event doesn't fire if the transition is aborted before the transition is completed because either the element is made `display: none` or the animating property's value is changed.

## Transition Performance
### `Stacking context`
Stacking context is a three-dimensional conceptualization of HTML elements along an imaginary z-axis relative to the user, who is assumed to be facing the viewport or the webpage. HTML elements occupy this space in priority order based on element attributes.

A stacking context is formed, anywhere in the document, by any element in the following scenarios:

+ Root element of the document (\<html>).
+ Element with a `position` value `absolute` or `relative` and `z-index` value other than `auto`.
+ Element with a `position` value `fixed` or `sticky` (sticky for all mobile browsers, but not older desktop browsers).
+ Element with a `container-type` value `size` or `inline-size` set, intended for container queries.
+ Element that is a child of a `flex` container, with `z-index` value other than `auto`.
+ Element that is a child of a `grid` container, with `z-index` value other than `auto`.
+ Element with an `opacity` value less than 1.
+ Element with a `mix-blend-mode` value other than `normal`.
+ Element with any of the following properties with value other than `none`:
  - `transform`
  - `filter`
  - `backdrop-filter`
  - `perspective`
  - `clip-path`
  - `mask` / `mask-image` / `mask-border`
+ Element with an `isolation` value `isolate`.
+ Element with a `will-change` value specifying any property that would create a stacking context on non-initial value.
+ Element with a `contain` value of `layout`, or `paint`, or a composite value that includes either of them (i.e. `contain: strict`, `contain: content`).
+ Element placed into the `top layer` and its corresponding `::backdrop`. Examples include `fullscreen` and `popover` elements.

Within a stacking context, child elements are stacked according to the same rules explained just above. Importantly, the `z-index` values of its child stacking contexts only have meaning in this parent. Stacking contexts are treated atomically as a single unit in the parent stacking context.

In summary:

+ Stacking contexts can be contained in other stacking contexts, and together create a hierarchy of stacking contexts.
+ Each stacking context is completely independent of its siblings: only descendant elements are considered when stacking is processed.
+ Each stacking context is self-contained: after the element's contents are stacked, the whole element is considered in the stacking order of the parent stacking context.

### Why are some animations slow?
Modern browsers can animate two CSS properties cheaply: transform and opacity. If you animate anything else, the chances are you're not going to hit a silky smooth 60 frames per second (FPS).

The **rendering pipeline** steps that we mentioned in the "transform" lesson (js > style > layout > paint > composite) are sequential. For example, if you animate something that changes layout, the paint and composite steps also have to run again. Animating something that changes layout is therefore more expensive than animating something that only changes compositing.

Layout changes involve calculating the geometry (position and size) of all the elements affected by the change.

Paint is the process of determining in what order elements should be painted to the screen. It is often the longest-running of all tasks in the pipeline.

Compositing is the process of separating the page into layers, converting the information about how the page should look into pixels (rasterization), and putting the layers together to create a page (compositing).

If you change a property that requires neither layout or paint, the browser can jump straight to the compositing step. This is the cheapest and most desirable pathway through the rendering pipeline for high pressure points in a page's lifecycle, such as animations or scrolling. Today there are only two properties for which that it is possible - `transform`s and `opacity`.

The caveat for the use of transforms and opacity is that the element on which you change these properties should be on its own *compositor layer*. In order to make a layer you must *promote* the element to it's own layer.

By placing animated elements on a new layer they can be repainted without also requiring the rest of the layout to be repainted. Browsers will often make good decisions about which items should be placed on a new layer, but you can manually force layer creation with the `will-change` property. As the name suggests, this property tells the browser that this element is going to be changed in some way.

### Key Points to Follow to Ensure Higher Performance Transitions
1. **Use Transform and Opacity**: Stick to using the `transform` and `opacity` properties for animations whenever possible. These properties typically perform well and keep animations on the compositing stage of the rendering path.

2. **Avoid Properties Triggering Layout or Paint**: Stay away from CSS properties that trigger layout or paint, except when absolutely necessary. These properties can degrade performance significantly.

3. **Force Layer Creation Selectively**: You can manually force layer creation using the `will-change` property to optimize performance. However, use this property sparingly and only when you encounter performance issues.

4. **Debug Slow Animations**: Use browser developer tools like Chrome DevTools or Firefox DevTools to diagnose and debug slow animations. Check if an animation triggers layout, drops frames, or triggers paint, and adjust accordingly.

5. **Check for Layout Triggers**: Be mindful of CSS properties that can cause layout recalculations during animations. Stick to using `transform` and `opacity` to avoid these issues.

6. **Optimize Painting**: Use tools like Chrome DevTools' Paint Flashing feature or Firefox DevTools to identify areas of the screen that require repainting during animations. Opt for CSS properties that minimize expensive paint operations.

7. **Conclusion**: Restrict animations to `opacity` and `transform` where possible, utilize developer tools to diagnose performance issues, and sparingly use the `will-change` property only when necessary.

By following these recommendations, you can ensure smoother and higher-performing CSS animations.

---
### Knowledge Check

**Q1.** Are all CSS properties animatable?

**A1.** CSS Animations and Transitions rely on the concept of animatable properties, and **all CSS properties are animatable unless otherwise specified.**

**Q2.** What are the long and short-hand notations for transitions?

**A2.** <br>
The transition CSS property is a shorthand property for transition-property, transition-duration, transition-timing-function and transition-delay.

```css
transition: property duration timing-function delay;
```

The `transition` property in CSS is a shorthand for several individual transition-related properties. Let's break down each of them:

1. **`transition-property`**:
   - This property specifies the CSS properties that should transition when their values change.
   - It accepts one or more property names as values.
   - If multiple properties are specified, each property can have its own transition settings.

   ```css
   transition-property: width height background-color;
   ```

2. **`transition-duration`**:
   - It defines the duration over which the transition should occur.
   - It can be specified in seconds (s) or milliseconds (ms).

   ```css
   transition-duration: 2s;
   ```

3. **`transition-timing-function`**:
   - This property determines the acceleration curve of the transition.
   - It specifies how the intermediate values of the CSS properties are calculated over time.
   - Common transition-timing-function property values include `linear`, `ease`, `ease-in`, `ease-out`, and `ease-in-out`.
   
   ```css
   transition-timing-function: ease-in-out;
   ```

   - We can also use the cubic-bezier function to create custom timing functions.
   
   ```css
   transition-timing-function: cubic-bezier(0.42, 0, 0.58, 1); /* Example cubic bezier timing function */`
   ```

   In the cubic bezier function, the four values (x1, y1, x2, y2) define the acceleration curve. These values represent control points on a cubic Bezier curve where (0,0) is the start point and (1,1) is the end point.

4. **`transition-delay`**:
   - It specifies a delay before the transition starts.
   - The value can be specified in seconds (s) or milliseconds (ms).

   ```css
   transition-delay: 0.5s;
   ```

**Q3.** What is the stacking context?

**A3.** Stacking context is a three-dimensional conceptualization of HTML elements along an imaginary z-axis relative to the user, who is assumed to be facing the viewport or the webpage. HTML elements occupy this space in priority order based on element attributes.

A stacking context is formed, anywhere in the document, by any element in the following scenarios:

+ Root element of the document (\<html>).
+ Element with a `position` value `absolute` or `relative` and `z-index` value other than `auto`.
+ Element with a `position` value `fixed` or `sticky` (sticky for all mobile browsers, but not older desktop browsers).
+ Element with a `container-type` value `size` or `inline-size` set, intended for container queries.
+ Element that is a child of a `flex` container, with `z-index` value other than `auto`.
+ Element that is a child of a `grid` container, with `z-index` value other than `auto`.
+ Element with an `opacity` value less than 1.
+ Element with a `mix-blend-mode` value other than `normal`.
+ Element with any of the following properties with value other than `none`:
  - `transform`
  - `filter`
  - `backdrop-filter`
  - `perspective`
  - `clip-path`
  - `mask` / `mask-image` / `mask-border`
+ Element with an `isolation` value `isolate`.
+ Element with a `will-change` value specifying any property that would create a stacking context on non-initial value.
+ Element with a `contain` value of `layout`, or `paint`, or a composite value that includes either of them (i.e. `contain: strict`, `contain: content`).
+ Element placed into the `top layer` and its corresponding `::backdrop`. Examples include `fullscreen` and `popover` elements.

Within a stacking context, child elements are stacked according to the same rules explained just above. Importantly, the `z-index` values of its child stacking contexts only have meaning in this parent. Stacking contexts are treated atomically as a single unit in the parent stacking context.

In summary:

+ Stacking contexts can be contained in other stacking contexts, and together create a hierarchy of stacking contexts.
+ Each stacking context is completely independent of its siblings: only descendant elements are considered when stacking is processed.
+ Each stacking context is self-contained: after the element's contents are stacked, the whole element is considered in the stacking order of the parent stacking context.

**Q4.** Why do you need to keep an eye on repaints?

**A4.** Each stacking context is self-contained: after the element's contents are stacked, the whole element is considered in the stacking order of the parent stacking context. So, if an element which is not a top element it the stacking context performs any kind of rendering operation including layout calculation, repainting or even just compositing, it will also trigger elements that are stacked on top of it to render again. For example if a \<span> element which has other elements stacked on top it, has a transition-property property of "transform", it would still trigger repainting on the elements that are on top of it.