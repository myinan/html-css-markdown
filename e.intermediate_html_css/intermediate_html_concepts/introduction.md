# Introduction
### MDN Complete HTML Elements Reference

[MDN Complete HTML Elements Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

## HTML Attributes
HTML attributes are an essential part of HTML (Hypertext Markup Language), the standard language used to create and structure content on the World Wide Web. Attributes provide additional information about HTML elements and allow developers to control various aspects of how elements are displayed, interacted with, or behave within a web page. They are typically used as key-value pairs and are added directly within the opening tag of an HTML element.

Here's a detailed explanation of HTML attributes:

1. **Syntax:**
   Attributes are added to HTML elements as part of their opening tag. The syntax generally follows this pattern:
   
   ```html
   <element attribute_name="attribute_value">Content</element>
   ```

   Here, `element` is the HTML tag, `attribute_name` is the name of the attribute, and `attribute_value` is the value assigned to that attribute.<br> In some cases, attributes don't require a value, and their presence alone provides a certain behavior or styling (`boolean attributes`).

2. **Purpose:**
   Attributes serve several purposes, including:
   
   - **Controlling Appearance:** Attributes can be used to style elements or modify their appearance. For instance, the "class" and "style" attributes are commonly used to apply CSS styles to elements.
   
   - **Providing Metadata:** Attributes can offer metadata about elements that can be used by search engines, screen readers, or other automated systems. The "title" and "alt" attributes are examples of this.

   - **Defining Behavior:** Attributes can define how elements interact with users or other elements. The "href" attribute in anchor tags (`<a>`) is used to specify the destination URL of a hyperlink.

   - **Form Elements:** Attributes play a crucial role in form elements like `<input>`, `<select>`, and `<textarea>`. They determine input types, default values, validation rules, and more.

3. **Common Attributes:**
   There are many attributes available in HTML, each serving a specific purpose. Some commonly used attributes include:
   
   - `id`: Provides a unique identifier for an element, which can be used for scripting or styling purposes.
   - `class`: Assigns one or more CSS classes to an element for styling or scripting purposes.
   - `style`: Allows inline CSS styling to be applied directly to an element.
   - `src`: Specifies the source URL for elements like images, videos, and scripts.
   - `alt`: Provides alternative text for elements like images, which is displayed when the element cannot be rendered.
   - `href`: Specifies the target URL for anchor tags to create hyperlinks.
   - `target`: Defines where a linked resource will be opened, such as in a new window or tab.
   - `title`: Offers additional information about an element, often displayed as a tooltip.

4. **Boolean Attributes:**
   Some attributes are boolean, meaning they don't require a value. The presence of the attribute itself implies a certain behavior. For example:
   
   - `disabled`: Disables user interaction with an element like an input or button.
   - `readonly`: Makes an input or textarea element non-editable.
   - `checked`: Pre-selects a checkbox or radio button.
   - `required`: Specifies that an input field must be filled out before submitting a form.
   
    If a boolean attribute is present, its value is true, and if it's absent, its value is false. (To be clear, the values "true" and "false" are not allowed on boolean attributes. To represent a false value, the attribute has to be omitted altogether.)

5. **Event Handler Attributes:**
   Event handler attributes are used to specify JavaScript code that should be executed when a particular event occurs on an HTML element. They are often referred to as "event handlers" and are denoted by the prefix "on-" followed by the event name. Here are some common event handler attributes:

   - `onclick`: Triggers when an element is clicked.
   - `onmouseover`: Fires when the mouse pointer moves over an element.
   - `onmouseout`: Fires when the mouse pointer leaves an element.
   - `onkeydown`: Activates when a key is pressed down while the element has focus.
   - `onkeyup`: Executes when a key is released after being pressed down.
   - `onsubmit`: Fires when a form is submitted.
   - `onchange`: Triggers when the value of an input element changes.

   The syntax for event handler attributes is as follows:

   ```html
   <element event_name="javascript_code">Content</element>
   ```

   Here, `element` is the HTML tag, `event_name` is the name of the event (e.g., `click`, `mouseover`), and `javascript_code` is the JavaScript code that will be executed when the event occurs.

   Event handler attributes are used to add interactivity to web pages. By attaching event handlers to HTML elements, you can define how those elements respond to user interactions. For example, you can use the `onclick` attribute to execute a JavaScript function when a button is clicked, or the `onmouseover` attribute to change the color of an element when the mouse hovers over it. Here's an example of how the `onclick` event attribute can be used to display an alert when a button is clicked:

   ```html
   <button onclick="alert('Button clicked!')">Click me</button>
   ```

   In this example, when the button is clicked, the `onclick` event triggers the JavaScript code within the attribute, which displays an alert box with the message "Button clicked!".

   **Warning:** The use of event handler content attributes is discouraged. The mix of HTML and JavaScript often produces unmaintainable code, and the execution of event handler attributes may also be blocked by content security policies.

6. **Custom Attributes:**
   While HTML provides a set of standard attributes, you can also create your own custom attributes. However, it's essential to note that custom attributes may not be recognized by all browsers and are not guaranteed to have standardized behavior. For data storage or scripting purposes, it's recommended to use `data-*` attributes (e.g., `data-attribute_name="value"`), which are specifically designed for this purpose and won't interfere with browser behavior.

In summary, HTML attributes are crucial tools for controlling the presentation, behavior, and functionality of elements within web pages. By properly using attributes, web developers can create rich and interactive user experiences while ensuring semantic and accessible content.

### [MDN Complete HTML Attributes Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes?retiredLocale=tr#event_handler_attributes)
