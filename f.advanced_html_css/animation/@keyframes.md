# CSS Animations
CSS animations are a way to add movement and interactivity to web pages using CSS (Cascading Style Sheets). With CSS animations, you can animate the properties of HTML elements, such as their position, size, color, opacity, and more, without needing to use JavaScript or Flash.

The term "CSS animations" encompasses both the `transition` property and the `@keyframes` at-rule, as they are both mechanisms used in CSS to create animated effects.

1. **Transition Property**: This property allows you to control the transition of a CSS property from one value to another over a specified duration. It's commonly used for simple animations like hover effects or smooth state changes.

2. **@keyframes At-Rule**: This at-rule defines a set of keyframes for CSS animations. It allows you to specify styles for an element at various points in the animation sequence. This is typically used for more complex animations where you need precise control over each stage of the animation.

So, while `@keyframes` is often associated with more complex animations and transitions are used for simpler effects, both fall under the umbrella of CSS animations.

Meanwhile, `transform` property itself is not considered a CSS animation property, as it doesn't inherently animate properties over time. Instead, it applies transformations to elements instantaneously, altering their appearance or position without any animation effect.

However, the `transform` property is often used in conjunction with CSS animations to create more complex animations. For instance, you can use `transform` within `@keyframes` to animate properties like `scale`, `rotate`, `translate`, etc., thus incorporating it into CSS animations. Similarly, `transform` can be combined with transitions to smoothly transition between different transformations.

## `@keyframes` Animations
### Differences between `@keyframes` animations and `transition` animations
Both `@keyframes` animations and `transition` animations are used in CSS to create animations, but they differ in how they are implemented and the level of control they offer:

1. **@keyframes Animations:**
   - `@keyframes` animations allow you to define a sequence of keyframes, each representing a specific point in the animation, and interpolate between them.
   - You can specify the properties you want to animate at each keyframe.
   - You have full control over the timing and duration of each keyframe in the animation.
   - `@keyframes` animations are typically used for complex animations with multiple stages or changes in direction. The @keyframes CSS at-rule controls the intermediate steps in a CSS animation sequence by defining styles for keyframes (or waypoints) along the animation sequence. This gives more control over the intermediate steps of the animation sequence than transitions.
   - They offer more flexibility and control but require more code to define compared to transitions.

   Example:
   ```css
   @keyframes slide-in {
     0% { opacity: 0; transform: translateY(100%); }
     100% { opacity: 1; transform: translateY(0); }
   }
   
   .element {
     animation: slide-in 1s ease-out forwards;
   }
   ```

2. **transition Animations:**
   - Transitions allow you to smoothly change the value of a CSS property over a specified duration when its value changes.
   - They are simpler to implement compared to `@keyframes` animations and are ideal for basic animations like hover effects or transitions between states.
   - With transitions, you only define the initial and final states, and the browser automatically calculates the intermediate states.
   - Transitions are triggered by a change in CSS properties, such as when an element gains or loses a class, or when a pseudo-class like `:hover` is applied.
   - They are easier to use for simple effects but may lack the fine-tuned control offered by `@keyframes`.

   Example:
   ```css
   .element {
     transition: opacity 0.5s ease-in-out;
   }
   
   .element:hover {
     opacity: 0.5;
   }
   ```

In summary, `@keyframes` animations are more suitable for complex animations where you need precise control over each step of the animation, while transitions are better for simple effects and state changes.

### `animation` property
To create a CSS animation sequence, you style the element you want to animate with the `animation` property or its sub-properties. This lets you configure the timing, duration, and other details of how the animation sequence should progress. This does not configure the actual appearance of the animation, which is done using the @keyframes at-rule.

#### **`animation` shorthand property:**

The **animation** shorthand CSS property applies an animation between styles. It is a shorthand for animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction, animation-fill-mode, animation-play-state, and animation-timeline.

**Syntax:**

```css
/* @keyframes duration | easing-function | delay |
iteration-count | direction | fill-mode | play-state | name */
animation: 3s ease-in 1s 2 reverse both paused slidein;

/* @keyframes duration | easing-function | delay | name */
animation: 3s linear 1s slidein;

/* two animations */
animation:
  3s linear slidein,
  3s ease-out 5s slideout;
```

The `animation` property is specified as one or more single animations, separated by commas.

The order of time values within each `animation` definition is important: the first value that can be parsed as a \<time> is assigned to the `animation-duration`, and the second one is assigned to `animation-delay`.

The order of other values within each `animation` definition is also important for distinguishing an `animation-name` value from other values. If a value in the `animation` shorthand can be parsed as a value for an animation property other than `animation-name`, then the value will be applied to that property first and not to `animation-name`. For this reason, the recommended practice is to specify a value for `animation-name` as the last value in a list of values when using the `animation` shorthand; this holds true even when you specify multiple, comma-separated animations using the `animation` shorthand.

While an animation name must be set for an animation to be applied, all values of the `animation` shorthand are **optional**, and default to the initial value for each long-hand animation component. The initial value of `nimation-name` is none, meaning if no `animation-name` value is declared in the animation shorthand property, there is no animation to apply on any of the properties.

When the `animation-duration` value is omitted from the animation shorthand property, the value for this property defaults to 0s. In this case, the animation will still occur (the `animationStart` and `animationEnd` events will be fired) but no animation will be visible.

Note: Animating CSS Box Model properties is discouraged. Animating any box model property is inherently CPU intensive; consider animating the `transform` property instead.

```css
:root {
  overflow: hidden;
  background-color: lightblue;
  display: flex;
  justify-content: center;
}

.sun {
  background-color: yellow;
  border-radius: 50%;
  height: 100vh;
  aspect-ratio: 1 / 1;
  /* multiple animations are separated by commas, each animation's parameters are set independently */
  animation:
    4s linear 0s infinite alternate rise,
    24s linear 0s infinite psychedelic;
}

@keyframes rise {
  from {
    transform: translateY(110vh);
  }
  to {
    transform: translateY(0);
  }
}

@keyframes psychedelic {
  from {
    filter: hue-rotate(0deg);
  }
  to {
    filter: hue-rotate(360deg);
  }
}

```

#### **animation sub-properties:**
1. `animation-name`: Specifies one or more animation names to be applied to the element. These names correspond to keyframes defined using `@keyframes` rule. If multiple names are specified, they are applied in the order given, separated by commas.

2. `animation-duration`: Sets the duration over which the animation will play. It is specified in seconds (s) or milliseconds (ms).

3. `animation-timing-function`: Defines the pace of the animation by specifying the speed curve. It determines how the intermediate values used during the animation will be calculated. Common values include `linear`, `ease`, `ease-in`, `ease-out`, and `ease-in-out`, among others.

4. `animation-delay`: Specifies a delay before the animation starts. It is specified in seconds (s) or milliseconds (ms).

5. `animation-iteration-count`: Sets the number of times the animation cycle should be played. It can take values such as a specific integer (e.g., `2`, `3`), `infinite` (to repeat indefinitely), or `initial` (default, indicating the animation should play once).

6. `animation-direction`: Determines whether the animation should play forwards, backward, alternate between forwards and backward, or alternate between forwards and backward on each cycle. Possible values include `normal`, `reverse`, `alternate`, and `alternate-reverse`.

7. `animation-fill-mode`: Specifies how the styles applied to the element are applied before and after the animation. It can take values such as `none`, `forwards`, `backwards`, and `both`. `none` (default) means no styles are applied before or after the animation. `forwards` applies the styles defined in the last keyframe after the animation ends. `backwards` applies the styles defined in the first keyframe before the animation starts. `both` applies both forwards and backwards styles.

8. `animation-play-state`: Allows pausing and resuming of an animation. It can take values `running` (default) and `paused`. `running` means the animation is playing, while `paused` means it's paused.

9. `animation-timeline`: Specifies which timeline the animation should follow, such as the element's timeline or the document timeline. It's a relatively new addition and not yet widely supported in browsers.

These sub-properties provide fine-grained control over various aspects of CSS animations.

---

**The animation shorthand property or its individual sub-properties are applied to the HTML elements that you want to animate.**

For example, if you want to animate a `<div>` element, you would apply the animation properties directly to that `<div>` element within your CSS stylesheet or inline CSS. Here's a simple example:

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .animated {
            animation: myAnimation 2s linear infinite;
        }

        @keyframes myAnimation {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
            100% {
                transform: scale(1);
            }
        }
    </style>
</head>
<body>
    <div class="animated">This div will be animated.</div>
</body>
</html>
```

In this example, the animation shorthand property `animation` is applied to the `.animated` class, specifying the animation name (`myAnimation`), duration (`2s`), timing function (`linear`), and iteration count (`infinite`). The `@keyframes` rule defines the animation's keyframes with different transform values, and the animation will continuously cycle through these keyframes, causing the element to scale up and down repeatedly.

### `@keyframes` at-rule
After you've configured the `animation` property, you need to define the "appearance" of the animation. This is done by establishing one or more keyframes using the `@keyframes` at-rule. Each keyframe describes how the animated element should render at a given time during the animation sequence.

The `@keyframes` CSS at-rule controls the intermediate steps in a CSS animation sequence by defining styles for keyframes (or waypoints) along the animation sequence.

Since the timing of the animation is defined in the CSS style that configures the animation, keyframes use a `<percentage>` to indicate the time during the animation sequence at which they take place. 0% indicates the first moment of the animation sequence, while 100% indicates the final state of the animation. Because these two times are so important, they have special aliases: from and to. Both are optional. If `from/0%` or `to/100%` is not specified, the browser starts or finishes the animation using the computed values of all attributes.

You can optionally include additional keyframes that describe intermediate steps between the start and end of the animation (e.g. 25%, 50%, 75% etc.).

To use keyframes, create a @keyframes rule with a name that is then used by the animation-name property to match an animation to its keyframe declaration. Each @keyframes rule contains a style list of keyframe selectors, which specify percentages along the animation when the keyframe occurs, and a block containing the styles for that keyframe.

If multiple keyframe sets exist for a given name, the last one encountered by the parser is used. @keyframes rules don't cascade, so animations never derive keyframes from more than one rule set.

## Animating `display` and `content-visibility`
Display and content-visibility can be animated. This behavior is useful for creating entry/exit animations where you want to for example remove a container from the DOM with display: none, but have it fade out smoothly with opacity rather than disappearing immediately.

+ When animating display from none to block (or another visible display value), the value will flip to block at 0% of the animation duration so it is visible throughout.
+ When animating display from block (or another visible display value) to none, the value will flip to none at 100% of the animation duration so it is visible throughout.

```html
<!-- html -->

<p>
  This is the first paragraph.
</p>

<div>
  This is an element that animates.
</div>

<p>
  This is another paragraph to show that animation is being
  applied and removed.
</p>

```

```css
/* css */

html {
  height: 100vh;
}

div {
  font-size: 1.6rem;
  padding: 20px;
  border: 3px solid red;
  border-radius: 20px;
  width: 480px;
  opacity: 0;
  display: none;
}

/* Animation classes */

div.fade-in {
  display: block;
  animation: fade-in 0.7s ease-in forwards;
}

div.fade-out {
  animation: fade-out 0.7s ease-out forwards;
}

/* Animation keyframes */

@keyframes fade-in {
  0% {
    opacity: 0;
    display: none;
  }

  100% {
    opacity: 1;
    display: block;
  }
}

@keyframes fade-out {
  0% {
    opacity: 1;
    display: block;
  }

  100% {
    opacity: 0;
    display: none;
  }
}
```

Note the inclusion of the `display` property in the keyframe animations.

---
### Knowledge Check

**Q1.** What are the long and short-hand notations for CSS animations?

**A1.** The animation shorthand CSS property applies an animation between styles. It is a shorthand for animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction, animation-fill-mode, animation-play-state, and animation-timeline.

**Q2.** How do you add keyframes to an animation?

**A2.** To create a CSS animation sequence, you style the element you want to animate with the animation property or its sub-properties. This lets you configure the timing, duration, and other details of how the animation sequence should progress. This does not configure the actual appearance of the animation, which is done using the @keyframes at-rule.

After you've configured the animation property, you need to define the appearance of the animation. This is done by establishing one or more keyframes using the @keyframes at-rule. Each keyframe describes how the animated element should render at a given time during the animation sequence.

Since the timing of the animation is defined in the CSS style that configures the animation, keyframes use a \<percentage> to indicate the time during the animation sequence at which they take place. 0% indicates the first moment of the animation sequence, while 100% indicates the final state of the animation. Because these two times are so important, they have special aliases: from and to. Both are optional. If from/0% or to/100% is not specified, the browser starts or finishes the animation using the computed values of all attributes.

You can optionally include additional keyframes that describe intermediate steps between the start and end of the animation.

```css
p {
  animation-duration: 3s;
  animation-name: slidein;
}

@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

**Q3.** When would you use an animation over a transition (and vice versa)?

**A3.**
### Differences between `@keyframes` animations and `transition` animations
Both `@keyframes` animations and `transition` animations are used in CSS to create animations, but they differ in how they are implemented and the level of control they offer:

1. **@keyframes Animations:**
   - `@keyframes` animations allow you to define a sequence of keyframes, each representing a specific point in the animation, and interpolate between them.
   - You can specify the properties you want to animate at each keyframe.
   - You have full control over the timing and duration of each keyframe in the animation.
   - `@keyframes` animations are typically used for complex animations with multiple stages or changes in direction. The @keyframes CSS at-rule controls the intermediate steps in a CSS animation sequence by defining styles for keyframes (or waypoints) along the animation sequence. This gives more control over the intermediate steps of the animation sequence than transitions.
   - They offer more flexibility and control but require more code to define compared to transitions.

   Example:
   ```css
   @keyframes slide-in {
     0% { opacity: 0; transform: translateY(100%); }
     100% { opacity: 1; transform: translateY(0); }
   }
   
   .element {
     animation: slide-in 1s ease-out forwards;
   }
   ```

2. **transition Animations:**
   - Transitions allow you to smoothly change the value of a CSS property over a specified duration when its value changes.
   - They are simpler to implement compared to `@keyframes` animations and are ideal for basic animations like hover effects or transitions between states.
   - With transitions, you only define the initial and final states, and the browser automatically calculates the intermediate states.
   - Transitions are triggered by a change in CSS properties, such as when an element gains or loses a class, or when a pseudo-class like `:hover` is applied.
   - They are easier to use for simple effects but may lack the fine-tuned control offered by `@keyframes`.

   Example:
   ```css
   .element {
     transition: opacity 0.5s ease-in-out;
   }
   
   .element:hover {
     opacity: 0.5;
   }
   ```

In summary, `@keyframes` animations are more suitable for complex animations where you need precise control over each step of the animation, while transitions are better for simple effects and state changes.


