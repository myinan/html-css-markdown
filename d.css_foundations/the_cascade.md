# The Cascade

### Reasons for unexpected display
+ Default browser stylesheet
+ Incorrect CSS values
+ Conflicts in the cascade

## Cascade Factors
The cascade is what determines which rules actually get applied to our HTML. There are different factors that the cascade uses to determine this.

### Specificity
A CSS declaration that is more specific will take precedence over less specific ones. Inline styles, which we went over in the previous lesson, have the highest specificity(1000) compared to selectors, while each type of selector has its own specificity level that contributes to how specific a declaration is. Other selectors contribute to specificity, but we’re focusing only on the ones we’ve gone over so far:

1. ID selectors (most specific selector) (100)
1. Class selectors (10)
1. Type selectors (1)

Specificity will only be taken into account when an element has multiple, conflicting declarations targeting it, sort of like a tie-breaker. An ID selector will always beat any number of class selectors, a class selector will always beat any number of type selectors, and a type selector will always beat any number of anything less specific than it. When no declaration has a selector with a higher specificity, a larger amount of a single selector will beat a smaller amount of that same selector.

> Not everything adds to specificity. When comparing selectors, you may come across special symbols for the universal selector (*) as well as combinators (+, ~, >, and an empty space). These symbols do not add any specificity in and of themselves.

```
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class .second-class {
  font-size: 24px;
}
```
Here both rule 1 and rule 2 have the same specificity. Rule 1 uses a chaining selector (no space) and rule 2 uses a descendant combinator (the empty space). But both rules have two classes and the combinator symbol itself does not add to the specificity.

```
/* rule 1 */
* {
  color: black;
}

/* rule 2 */
h1 {
  color: orange;
}
```

In this example, rule 2 would have higher specificity and the orange value would take precedence for this element. Rule 2 uses a type selector, which has the lowest specificity value. But rule 1 uses the universal selector (*) which has no specificity value.

### Inheritance
Inheritance refers to certain CSS properties that, when applied to an element, are inherited by that element’s descendants, even if we don’t explicitly write a rule for those descendants. Typography based properties (color, font-size, font-family, etc.) are usually inherited, while most other properties aren’t.

The exception to this is when directly targeting an element, as this always beats inheritance:

```
<!-- index.html -->

<div id="parent">
  <div class="child"></div>
</div>
```

```
/* styles.css */

#parent {
  color: red;
}

.child {
  color: blue;
}
```

Despite the parent element having a higher specificity with an ID, the child element would have the color: blue style applied since that declaration directly targets it, while color: red from the parent is only inherited.

### Rule Order (Order of Appearance)
The final factor, the end of the line, the tie-breaker of the tie-breaker. Let’s say that after every other factor has been taken into account, there are still multiple conflicting rules targeting an element. How does the cascade determine which rule to apply?

Really simply, actually. Whichever rule was the last defined is the winner.

```
/* styles.css */

.alert {
  color: red;
}

.warning {
  color: yellow;
}
```

For an element that has both the alert and warning classes, the cascade would run through every other factor, including inheritance (none here) and specificity (neither rule is more specific than the other). Since the .warning rule was the last one defined, and no other factor was able to determine which rule to apply, it’s the one that gets applied to the element.

---

Assignment "odin-css-exercises-fork -) foundations -) 6" completed.

---

### Knowledge Check

**Q1.** Between a rule that uses one class selector and a rule that uses three type selectors, which rule has the higher specificity?

**A1.** A CSS rule that uses a class selector will always have more specificity than any CSS rules that uses type selectors.



