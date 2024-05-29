# Form Basics
Web forms are one of the main points of interaction between a user and a website or application. Forms allow users to enter data, which is generally sent to a web server for processing and storage, or used on the client-side to immediately update the interface in some way (for example, add another item to a list, or show or hide a UI feature).

A web form's HTML is made up of one or more form controls (sometimes called widgets), plus some additional elements to help structure the overall form. The controls can be single or multi-line text fields, dropdown boxes, buttons, checkboxes, or radio buttons, and are mostly created using the \<input> element, although there are some other elements to learn about too.

## The `form` Element
The form element is a container element like the div element we learned earlier in the curriculum. The form element wraps all of the inputs a user will interact with on a form.

The form element accepts two essential attributes; the first is the `action` attribute which takes a URL value that tells the form where it should send its data to be processed.

The second is the `method` attribute which tells the browser which HTTP request method it should use to submit the form. The GET and POST request methods are the two you will find yourself using the most.

We use `GET` when we want to retrieve something from a server. `POST` is used when we want to change something on the server.

The markup for creating a form element looks like this:

```html
<form action="example.com/path" method="post">

</form>
```

## Form Control Elements
To start collecting user data, we need to use form control elements. These are all the elements users will interact with on the form, such as text boxes, dropdowns, checkboxes and buttons. In the following few sections, we will explore some of the form controls you will use most commonly.

### A. The `input` element
The input element is the most versatile of all the form control elements. It accepts a `type` attribute which tells the browser what type of data it should expect and how it should render the input element.

The \<input> element is so powerful because of its attributes; the type attribute, being the most important. Since every \<input> element, regardless of type, is based on the `HTMLInputElement` interface, they technically share the exact same set of attributes. However, in reality, most attributes have an effect on only a specific subset of input types. In addition, the way some attributes impact an input depends on the input type, impacting different input types in different ways.

[Full list of \<input> element's available attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#attributes "input_attributes")

+ #### `<input type="text">`
    A **`text`** input looks like this:

    ```html
    <form action="example.com/path" method="post">
        <input type="text">
    </form>
    ```

    Text inputs accept any text input. For example, you would use it to collect things like users’ first and last names.

    Use:
    + `size` attribute to control the physical size of the input box. With it, you can specify the number of characters the text input can display at a time. `<input type="text" size="30"`

    + `required` boolean attribute to make entering a value required before form submission is allowed.
    
    + `minlength` attribute to specify a minimum length (in characters) for the entered value; similarly, use `maxlength` to set the maximum length of the entered value, in characters.

    +  `placeholder` attribute to include placeholder text in input fields. It's value will be the placeholder text we want to display.

    + `pattern` attribute to specify a regular expression that the inputted value must match in order to be considered valid.

+ #### `<label>` element
    An input on its own isn’t very useful since the user will not know what kind of data they are supposed to provide. Instead, we can give our inputs a label to inform users what type of data they are expected to enter.

    To create a label, we use the `<label>` element. The text we want displayed in the label will go between its opening and closing tags:

    ```html
    <form action="example.com/path" method="post">
      <label for="first_name">First Name:</label>
      <input type="text" id="first_name">
    </form>
    ```

    Labels accept a `for` attribute, which associates it with a particular input. The input we want to associate with a label needs an `id` attribute with the same value as the label’s `for` attribute.

    When a label is associated with an input and is clicked, it will focus the cursor on that input, ready for the user to input some data. This helps make our forms more accessible to users who rely on assistive technologies.
   
+ #### The `name` attribute
    We need to use labels so that users understand what the data entered into an input field will represent. Just like that, we also need to let the backend, where we send our data, know what each piece of data represents.

    We do this by adding a `name` attribute to our inputs:

    ```html
    <label for="first_name">First Name:</label>
    <input type="text" id="first_name" name="first_name">
    ```

    The `name` attribute serves as a reference to the data inputted into a form control after submitting it. You can think of it as a variable name for the input. Form input should always have a `name` attribute; otherwise, it will be ignored when the form is submitted.

+ #### Using form controls outside of forms
    It’s worth mentioning that you can use **any** of the form controls HTML provides outside of the `<form>` element, even when you don’t have a backend server where you can send data. If you do so, by default that control has nothing to do with any form unless you associate it with a form using its `form attribute`. This was introduced to let you explicitly bind a control with a form even if it is not nested inside it.

    As an example for using form controls outside of forms, you might want to have an input that gets some data from a user and display that somewhere else on the page with JavaScript.

+ #### The `type` attribute
    **`email`** inputs are specialized text inputs just for email addresses. They are different from text inputs in that they will display a different keyboard which will include the @ symbol on mobile devices to make entering email addresses easier.

    They also validate that the user has entered a correctly formatted email address.

    To create an `email` input, we use an input element with type attribute of “email”:

    ```html
    <label for="user_email">Email Address:</label>
    <input type="email" id="user_email" name="email" placeholder="you@example.com">
    ```

    **`password`** inputs are another specialized text input. They differ from regular text inputs in that they mask the inputted data with another character – usually an asterisk (*) or bullet point (•) – to prevent anyone from seeing what has been entered.

    A `password` input type can be created using an input element with a type of “password”:

    ```html
    <label for="user_password">Password:</label>
    <input type="password" id="user_password" name="password">
    ```

    The **`number`** input type only accepts number values and ignores any other characters the user tries to enter.

    The number input type makes sense when the range of valid values is limited, for example a person's age or height. If the range is too large for incremental increases to make sense (such as USA ZIP codes, which range from 00001 to 99999), the **`tel`** type might be a better option; it provides the numeric keypad while forgoing the number's spinner UI feature.

    We create a number input using the input element with a type attribute of “number”:

    ```html
    <label for="amount">Amount:</label>
    <input type="number" id="amount" name="amount">
    ```

    To collect dates from a user, we can use a **`date`** input type. This input is unique because it provides a better user experience for choosing dates by rendering a simple date picker calendar.

    To create a date input, we use the input element with a type attribute of “date”:

    ```html
    <label for="dob">Date of Birth:</label>
    <input type="date" id="dob" name="dob">
    ```

    To create a file picker widget, you use the \<input> element with its type attribute set to **`file`**. The types of files that are accepted can be constrained using the accept attribute. In addition, if you want to let the user pick more than one file, you can do so by adding the multiple attribute.

    ```html
    <input type="file" name="file" id="file" accept="image/*" multiple />
    ```

+ #### `<textarea>` element
    While technically not an input element, the text area element provides an input box that can accept text that spans multiple lines like user comments and reviews. It can also be resized by clicking and dragging the bottom right corner to make it bigger or smaller.

    To create a text area, we use the `<textarea>` element:

    ```html
    <textarea></textarea>
    ```

    Unlike input elements, Textarea elements do have a closing tag. This allows you to wrap some initial content you want the text area to display:

    ```html
    <textarea>Some initial content</textarea>
    ```

    Text area elements accept a couple of unique attributes that other form controls do not. These are the rows and cols attributes. They allow you to control the initial height (rows) and width (cols) of the text area:

    ```html
    <textarea rows="20" cols="60"></textarea>
    ```

### B. Selection elements
Sometimes you will want users to select a value from a predefined list. This is where select elements will be useful.

+ #### Select dropdown
    The select element renders a dropdown list where users can select an option. Syntactically, select elements have similar markup to unordered lists. The select element wraps option elements which are the options that can be selected.

    To create a select dropdown, we use the `<select>` element. Any options we want to display within the select element are defined using `<option>` elements:

    ```html
    <select name="Car">
        <option value="mercedes">Mercedes</option>
        <option value="tesla">Tesla</option>
        <option value="volvo" selected>Volvo</option>
        <option value="bmw">BMW</option>
        <option value="mini">Mini</option>
        <option value="ford">Ford</option>
    </select>
    ```

    All the option elements should(otherwise the text content inside is used) have a `value` attribute. This value will be sent to the server when the form is submitted.

    We can set one of the options to be the default selected element when the browser first renders the form by giving one of the options the `selected` attribute.

    We may also split the list of options into groups using the `<optgroup>` element. The optgroup element takes a label attribute which the browser uses as the label for each group:

    ```html
    <select name="fashion">
      <optgroup label="Clothing">
        <option value="t_shirt">T-Shirts</option>
        <option value="sweater">Sweaters</option>
        <option value="coats">Coats</option>
      </optgroup>
      <optgroup label="Foot Wear">
        <option value="sneakers">Sneakers</option>
        <option value="boots">Boots</option>
        <option value="sandals">Sandals</option>
      </optgroup>
    </select>
    ```

+ #### Radio button (`<input type="radio">`)
    Select dropdowns are great for saving space on the page when we have an extensive list of options we want users to choose from. However, when we have a smaller list of 5 or fewer options to choose from, it is often a better user experience to have them displayed on the page instead of hidden behind a dropdown.

    In this case, we can use radio buttons. Radio buttons allow us to create multiple options that the user can choose one of. To create radio buttons, we use the ever adaptable input element again with a `type` attribute of “radio”:

    ```html
    <h1>Ticket Type</h1>
    <div>
        <input type="radio" id="child" name="ticket_type" value="child">
        <label for="child">Child</label>
    </div>

    <div>
        <input type="radio" id="adult" name="ticket_type" value="adult" checked>
        <label for="adult">Adult</label>
    </div>

    <div>
        <input type="radio" id="senior" name="ticket_type" value="senior">
        <label for="senior">Senior</label>
    </div>
    ```

    Several radio buttons can be tied together. If they share the same value for their `name` attribute, they will be considered to be in the same group of buttons. Only one button in a given group may be checked at a time; this means that when one of them is checked all the others automatically get unchecked. When the form is sent, only the value of the checked radio button is sent. If none of them are checked, the whole pool of radio buttons is considered to be in an unknown state and no value is sent with the form. Once one of the radio buttons in a same-named group of buttons is checked, it is not possible for the user to uncheck all the buttons without resetting the form. We can set the default selected radio button by adding the `checked` attribute to it.

+ #### Checkbox (`<input type="checkbox">`)
    Checkboxes are similar to radio buttons in that they allow users to choose from a set of predefined options. But unlike radio buttons, they allow multiple options to be selected at once.

    To create a checkbox, we use the input element with a `type` attribute of “checkbox”:

    ```html
    <h1>Pizza Toppings</h1>

    <div>
        <input type="checkbox" id="sausage" name="topping" value="sausage">
        <label for="sausage">Sausage</label>
    </div>

    <div>
        <input type="checkbox" id="onions" name="topping" value="onions">
        <label for="onions">Onions</label>
    </div>

    <div>
        <input type="checkbox" id="pepperoni" name="topping" value="pepperoni">
        <label for="pepperoni">Pepperoni</label>
    </div>

    <div>
        <input type="checkbox" id="mushrooms" name="topping" value="mushrooms">
        <label for="mushrooms">Mushrooms</label>
    </div>
    ```

    We can also have a single checkbox when we want users to toggle if they want something to be true or false. Like signing up to a newsletter when they create an account for example:

    ```html
    <div>
        <input type="checkbox" id="newsletter" name="news_letter" checked>
        <label for="newsletter">Send me the news letter</label>
    </div>
    ```

    Related checkbox items should use the same name attribute. Including the checked attribute makes the checkbox checked automatically when the page loads. Clicking the checkbox or its associated label toggles the checkbox on and off.

### C. Buttons
The button element creates clickable buttons that the user can interact with to submit forms and trigger other actions.

To create a button, we use the `<button>` element. The content or text we want to have displayed inside the button will go within the opening and closing tags:

```html
<button>Click Me</button>
```

The button element also accepts a `type` attribute that tells the browser which kind of button it is dealing with. There are three types of buttons available to us.

+ #### `submit` button
    Once a user is finished filling in a form, they will need a way to submit it. There is a specialized button for this; the submit button. When a submit button is clicked, it will submit the form it is contained within. The type attribute has a value of submit by default, i.e. if the type is not specified or the value provided is invalid.

    To create a submit button, we use the button element with a type attribute of “submit”:

    ```html
    <button type="submit">Submit</button>
    ```

+ #### `reset` button
    A reset button clears all the data the user has entered into the form and sets all the inputs in the form back to what they were initially.

    To create a reset button, we use the button element with a type attribute of “reset”:

    ```html
    <button type="reset">Reset</button>
    ```

+ #### Generic button
    The third and final button type is simply a generic button that can be used for anything. It’s commonly used with JS for creating interactive UI’s.

    To create a generic button, we use the button element with a type attribute of “button”:

    ```html
    <button type="button">Click to Toggle</button>
    ```


**Note:** It is important to remember that a button within a form with the type value of submit (which happens to be the default value) will always try to make a new request and submit data back to the server. Hence, for buttons that are used within a form for different purposes other than submitting the data, the type attribute should always be specified to avoid unwanted effects of submitting a form.

**Important:** Buttons always behave the same whether you use a `<button>` element or an `<input>` element. As you can see from the below examples, however, \<button> elements let you use HTML in their content, which is inserted between the opening and closing \<button> tags. \<input> elements on the other hand are void elements; their displayed content is inserted inside the value attribute, and therefore only accepts plain text as content.

```html
<input type="submit" value="Submit this form" />
<input type="reset" value="Reset this form" />
<input type="button" value="Do Nothing without JavaScript" />

<button type="submit">Submit <strong>this</strong> form</button>
<button type="reset">Reset <strong>this</strong> form</button>
<button type="button">Do Nothing <strong>without</strong> JavaScript</button>
```

## Organizing Form Elements
Using the correct inputs for the data we want users to enter goes a long way towards making our forms user friendly. However, in larger forms, users can easily get overwhelmed and discouraged if there are many inputs to fill in.

Luckily, HTML provides a couple of elements that make it easy to organize forms into sections that are visually distinct and manageable to digest.

### `fieldset` element
The fieldset element is a container element that allows us to group related form inputs into one logical unit.

To create a fieldset, we use the `<fieldset>` element. Whatever form inputs we want to group together go within the opening and closing fieldset tags:

```html
<fieldset>
  <label for="first_name">First Name</label>
  <input type="text" id="first_name" name="first_name">

  <label for="last_name">Last Name</label>
  <input type="text" id="last_name" name="last_name">
</fieldset>
```

### `legend` element
The legend element is used to give field sets a heading or caption so the user can see what a grouping of inputs is for.

To create a legend, we use the `<legend>` element with the text we want to display within its opening and closing tags. A legend should always come right after an opening fieldset tag:

```html
<fieldset>
  <legend>Contact Details</legend>

  <label for="name">Name:</label>
  <input type="text" id="name" name="name">

  <label for="phone_number">Phone Number:</label>
  <input type="tel" id="phone_number" name="phone_number">

  <label for="email">Email:</label>
  <input type="email" id="email" name="email">
</fieldset>

<fieldset>
  <legend>Delivery Details</legend>

  <label for="street_address">Street Address:</label>
  <input type="text" id="street_address" name="street_address">

  <label for="city">City:</label>
  <input type="text" id="city" name="city">

  <label for="zip_code">Zip Code:</label>
  <input type="text" id="zip_code" name="zip_code">
</fieldset>
```

A common use-case for these elements is using a fieldset to group radio buttons and using a legend to communicate to the user what each of the options is ultimately for:

```html
<fieldset>
  <legend>What would you like to drink?</legend>

  <div>
    <input type="radio" name="drink" id="coffee" value="coffee">
    <label for="coffee">Coffee</label>
  </div>

  <div>
    <input type="radio" name="drink" id="tea" value="tea">
    <label for="tea">Tea</label>
  </div>

  <div>
    <input type="radio" name="drink" id="soda" value="soda">
    <label for="soda">Soda</label>
  </div>
</fieldset>
```

### Common HTML structures used with forms
Beyond the structures specific to web forms, it's good to remember that form markup is just HTML. This means that you can use all the power of HTML to structure a web form.

It's common practice to wrap a label and its widget with a `<li>` element within a `<ul>` or `<ol>` list. `<p>` and `<div>` elements are also commonly used. Lists are recommended for structuring multiple checkboxes or radio buttons.

In addition to the `<fieldset>` element, it's also common practice to use HTML titles (e.g. h1, h2) and sectioning (e.g. `<section>`) to structure complex forms.

**Important:** For maximum usability/accessibility, you are advised to surround each list of related items in a `<fieldset>`, with a `<legend>` providing an overall description of the list. Each individual pair of `<label>/<input>` elements should be contained in its own list item (or similar).

## Styling the Form
### Types of widgets

#### Easy-to-style
- `<form>`
- `<fieldset>` and `<legend>`
- Single-line text `<input>`s (e.g., type text, url, email), except for `<input type="search">`
- Multi-line `<textarea>`
- Buttons (both `<input>` and `<button>`)
- `<label>`
- `<output>`

#### Harder-to-style
- Checkboxes and radio buttons
- `<input type="search">`

#### HTML internals can't be styled in CSS alone
- `<input type="color">`
- Date-related controls such as `<input type="datetime-local">`
- `<input type="range">`
- `<input type="file">`
- Elements involved in creating dropdown widgets, including `<select>`, `<option>`, `<optgroup>`, and `<datalist>`
- `<progress>` and `<meter>`

CSS alone is not sufficient for modifying the internal content or structure of these HTML elements; additional scripting with JavaScript may be required for such tasks.For example, the date picker calendar, and the button on `<select>` that displays an options list when clicked, can't be styled using CSS alone.

### Styling simple form widgets

#### Fonts and text
CSS font and text features can be used easily with any widget (and yes, you can use @font-face with form widgets). However, browser behavior is often inconsistent. By default, some widgets do not inherit font-family and font-size from their parents. Many browsers use the system's default appearance instead. To make your forms' appearance consistent with the rest of your content, you can add the following rules to your stylesheet:

```css
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
}
```

The inherit property value causes the property value to match the computed value of the property of its parent element; inheriting the value of the parent.

#### Box sizing
All text fields have complete support for every property related to the CSS box model, such as width, height, padding, margin, and border. As before, however, browsers rely on the system default styles when displaying these widgets. It's up to you to define how you wish to blend them into your content. If you want to keep the native look and feel of the widgets, you'll face a little difficulty if you want to give them a consistent size.

This is because each widget has its own rules for border, padding, and margin. To give the same size to several different widgets, you can use the box-sizing property along with some consistent values for other properties:

```css
input,
textarea,
select,
button {
  width: 150px;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
```

### Advanced form styling
#### The `appearance` property
Historically, the styling of web form controls was largely taken from the underlying operating system, which is part of the problem with customizing the look of the "difficult to style" controls.

The `appearance` property was created as a way to control what OS- or system-level styling was applied to web form controls. By far the most helpful value, and probably the only one you'll use, is `none`. This stops any control you apply it to from using system-level styling, as much as possible, and lets you build up the styles yourself using CSS.

Applying the following CSS to `input` removes system-level styling:

```css
input {
  appearance: none;
}
```

#### Using appearance: none on radios/checkboxes
As mentioned before, you can remove the default appearance of a checkbox or radio button altogether with appearance:none;.

```css
input[type="checkbox"] {
  appearance: none;
}
```

We can use the :checked and :disabled pseudo-classes to change the appearance of our custom checkbox as its state changes:

```css
input[type="checkbox"] {
  position: relative;
  width: 1em;
  height: 1em;
  border: 1px solid gray;
  /* Adjusts the position of the checkboxes on the text baseline */
  vertical-align: -2px;
  /* Set here so that Windows' High-Contrast Mode can override */
  color: green;
}

input[type="checkbox"]::before {
  content: "✔";
  position: absolute;
  font-size: 1.2em;
  right: -1px;
  top: -0.3em;
  visibility: hidden;
}

input[type="checkbox"]:checked::before {
  /* Use `visibility` instead of `display` to avoid recalculating layout */
  visibility: visible;
}

input[type="checkbox"]:disabled {
  border-color: black;
  background: #ddd;
  color: gray;
}
```

#### Styling the "ugly" elements
Now let's turn our attention to the controls that are really hard to thoroughly style. In short, these are drop-down boxes, complex control types like color and datetime-local, and feedback—oriented controls like \<progress> and \<meter>.

The problem is that these elements have very different default looks across browsers, and while you can style them in some ways, some parts of their internals are literally impossible to style.

If you are prepared to live with some differences in look and feel, you can get away with some simple styling to make sizing consistent, uniform styling of things like background-colors, and usage of appearance to get rid of some system-level styling.

+ **Select dropdown:** Two things are slightly problematic. First of all, the select's "arrow" icon that indicates it is a dropdown differs across browsers. It also tends to change if you increase the size of the select box, or resize in an ugly fashion. To fix this in our example we first used our old friend appearance: none to get rid of the icon altogether. We then created our own icon using generated content. We put an extra wrapper around the control, because ::before/::after don't work on \<select> elements. We then use generated content to generate a little down arrow, and put it in the right place using positioning.

  The second, slightly more important issue is that you don't have control over the box that appears containing the options when you click on the \<select> box to open it. You can inherit the font set on the parent, but you won't be able to set things like spacing and colors. The same is true for the autocomplete list that appears with \<datalist>.

  If you really need full control over the option styling, you'll have to either use some kind of library to generate a custom control, or build your own custom control.

+ **Date input types:** The date/time input types (datetime-local, time, week, month) all have the same major associated issue. The actual containing box is as easy to style as any text input.

  However, the internal parts of the control (e.g. the popup calendar that you use to pick a date, the spinner that you can use to increment/decrement values) are not stylable at all, and you can't get rid of them using appearance: none;. If you really need full control over the styling, you'll have to either use some kind of library to generate a custom control, or build your own.

+ **Range input types:** `<input type="range">` is annoying to style. It is very difficult to customize the style of the range control's drag handle — to get full control over range styling you'll need to use a whole bunch of complex CSS code, including multiple non-standard, browser-specific pseudo-elements.

+ **Color input types:** Input controls of type color are not too bad. In supporting browsers, they tend to just give you a block of solid color with a small border.

  You can remove the border, just leaving the block of color, using something like this:

  ```css
  input[type="color"] {
  border: 0;
  padding: 0;
  }
  ```

  However, a custom solution is the only way to get anything significantly different.

+ **File input types:** The only problem with file pickers is that the button provided that you press to open the file picker is completely unstylable — it can't be sized or colored, and it won't even accept a different font.

  One way around this is to take advantage of the fact that if you have a label associated with a form control, clicking the label will activate the control. So you could hide the actual form input using something like this:

  ```css
  input[type="file"] {
  height: 0;
  padding: 0;
  opacity: 0;
  }
  ```

  And then style the label to act like a button, which when pressed will open the file picker as expected.

+ **Meters and progress bars:** \<meter> and \<progress> are possibly the worst of the lot. It is easier to just create your own custom solution for these features, if you want to be able to control the styling, or use a third-party solution such as progressbar.js.

### UI pseudo-classes
The pseudo-classes that are relevant to forms are:

+ `:hover`: Selects an element only when it is being hovered over by a mouse pointer.

+ `:focus`: Selects an element only when it is focused (i.e. by being tabbed to via the keyboard).

+ `:active`: selects an element only when it is being activated (i.e. while it is being clicked on, or when the Return / Enter key is being pressed down in the case of a keyboard activation).

+ `:required` and `:optional`: Target elements that can be required (e.g. elements that support the required HTML attribute), based on whether they are required or optional.

+ `:valid` and `:invalid`, and `:in-range` and `:out-of-range`: Target form controls that are valid/invalid according to form validation constraints set on them, or in-range/out-of-range.

+ `:enabled` and `:disabled`, and `:read-only` and `:read-write`: Target elements that can be disabled (e.g. elements that support the disabled HTML attribute), based on whether they are currently enabled or disabled, and read-write or read-only form controls (e.g. elements with the readonly HTML attribute set).

+ `:checked`, `:indeterminate`, and `:default`: Respectively target checkboxes and radio buttons that are checked, in an indeterminate state (neither checked or not checked), and the default selected option when the page loads (e.g. an \<input type="checkbox"> with the checked attribute set, or an \<option> element with the selected attribute set).

For example, the following CSS will place a check (tick) mark next to inputs containing valid values, and a cross (X) next to inputs containing invalid values:

```css
div {
  margin-bottom: 10px;
  position: relative;
}

input + span {
  padding-right: 30px;
}

input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}

input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

The technique also requires a `<span>` element to be placed after the form element, which acts as a holder for the icons. This was necessary because some input types on some browsers don't display icons placed directly after them very well.

---
### Knowledge Check

**Q1.** Explain what the form element is for and what two attributes it should always include.

**A1.** `<form>` element is the container element for our form widgets. The form element accepts two essential attributes; the first is the `action` attribute which takes a URL value that tells the form where it should send its data to be processed. The second is the `method` attribute which tells the browser which HTTP request method it should use to submit the form. The GET and POST request methods are the two you will find yourself using the most.

**Q2.** Explain what form controls are at a high level.

**A2.** Form controls are elements that enables us to get data/input from the user. Main form controls are \<input> element, \<textarea> element, \<select> and \<option> elements, and also the \<button> element.

**Q3.** What is the name attribute for?

**A3.** Naturally, the input provided by the user through the use of form controls, is send to the server to be processed. The server needs to be able to identify the sent data in order to correctly handle it. The `name` attribute serves as a "variable" name to the sent data, and input data is sent to the server as "name-value" pairs.

**Q4.** What are the three most common form controls you can use for allowing users to select predefined options?

**A4.** <br>1- We can create a "select dropdown" with the use of \<select> and \<option> elements.<br>
2- We can create a group of radio buttons for the user to choose from with `<input type="radio">`.<br>
3- We can create checboxes with `<input type="checkbox">`.

**Q5.** What are the three types of buttons in HTML?

**A5.**
+ `<button type="submit">` submits the form that the button is associated with.
+ `<button type="reset">` resets the form to it's default state.
+ `<button type="button">` is a generic button that is useful to manipulate with JavaScript.

**Q6.** What are the two most challenging aspects of styling forms?

**A6.** Like many other HTML elements, forms and form widgets also have their default styles applied by the browsers. The different default styles applied by browsers presents a challenge to maintaining consistency. Also, some form widgets are really diffucult to style, like checkboxes, radio buttons, or search inputs, and they need to be styled with either extensive use of custom css rules or with javascript libraries available online.