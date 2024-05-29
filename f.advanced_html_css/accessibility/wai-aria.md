# WAI-ARIA
WAI-ARIA stands for Web Accessibility Initiative - Accessible Rich Internet Applications. It is a set of attributes that can be added to HTML elements to improve the accessibility of web content and applications for people with disabilities. Developed by the World Wide Web Consortium (W3C), WAI-ARIA provides a standardized way to enhance the semantics of web content, particularly for dynamic and interactive components that may not be fully accessible to all users using conventional HTML alone.

The primary goal of WAI-ARIA is to bridge the accessibility gap between conventional web content and modern web applications, which often rely heavily on JavaScript, AJAX, and other dynamic technologies that can pose challenges for users who rely on assistive technologies like screen readers. By providing additional metadata about the roles, states, and properties of elements, WAI-ARIA enables assistive technologies to better interpret and interact with complex web interfaces.

WAI-ARIA defines several key concepts:

1. Roles: ARIA introduces a set of predefined roles that describe the intended purpose or function of an element on a webpage. For example, roles such as "button", "menu", "slider", "tabpanel", etc., help convey the semantic meaning of elements beyond their native HTML semantics.

2. States and Properties: ARIA attributes can also define the current state or properties of an element, such as whether it is expanded or collapsed, enabled or disabled, selected, or not, etc. These attributes provide valuable context for assistive technologies to convey the dynamic behavior of web components.

3. Relationships: ARIA allows developers to establish relationships between different elements on a webpage. For example, specifying the relationship between a button and the content it controls in a dropdown menu.

By using ARIA attributes judiciously, web developers can significantly improve the accessibility of their applications. However, it's important to note that ARIA should be used as a supplement to, not a replacement for, native HTML semantics and accessibility features. Developers should strive to create content that is inherently accessible and progressively enhance it with ARIA where necessary.

It’s important to note that ARIA can only modify the semantics or context of an element. ARIA attributes can’t:

+ modify an element’s appearance,
+ modify an element’s behavior,
+ add focusability, or
+ add keyboard event handling.

When you use ARIA, you will usually have to take additional steps to add in any missing semantics or functionality (for example, adding focusability and event handling with keyboard to \<div> buttons).

## The Five Rules of ARIA
ARIA can be extremely powerful when used correctly, but it can be equally as dangerous when used incorrectly. Because of this, you should keep in mind that **no ARIA is better than bad ARIA**, even when you have the best intentions. 

The "Five Rules of ARIA" are guidelines established to help developers effectively implement Accessible Rich Internet Applications (ARIA) attributes in web content. These rules provide a structured approach to utilizing ARIA in a way that enhances accessibility without causing unintended consequences. Here they are:

1. **If you can use a native HTML element or attribute with the semantics and behavior you require already built-in, instead of re-purposing an element and adding ARIA roles, states, and properties to make it accessible, then do so.** 
   - This rule emphasizes the importance of using native HTML elements whenever possible. Native elements already come with built-in accessibility features and semantics. For example, using `<button>` for buttons, `<input type="checkbox">` for checkboxes, etc., is preferred over trying to create similar functionality using other elements with ARIA attributes.

2. **Do not change native semantics, unless you really have to.**
   - It's crucial to respect the native semantics of HTML elements. Altering these semantics using ARIA can lead to confusion for assistive technology users. If an element already has a specific semantic meaning, avoid changing it unless absolutely necessary for accessibility reasons.

3. **All interactive ARIA controls must be usable with the keyboard.**
   - This rule underscores the importance of keyboard accessibility. Users who cannot operate a mouse rely on keyboard navigation to interact with web content. Therefore, any interactive elements enhanced with ARIA attributes should be fully operable via keyboard input, ensuring equal access to all users.

4. **Do not use `role="presentation"` or `aria-hidden="true"` on a focusable element.**
   - `role="presentation"` and `aria-hidden="true"` are ARIA attributes used to convey to assistive technologies that an element is decorative or should be hidden from accessibility APIs, respectively. However, if an element is focusable (such as a link or button), these attributes should not be used because doing so would hide important accessibility information from keyboard users.

5. **All interactive elements must have an accessible name.**
   - An accessible name is essential for conveying the purpose or function of an interactive element to assistive technology users. Whether it's a button, link, form field, or any other interactive element, it should have a clear and descriptive accessible name that can be announced by screen readers.

Following these rules helps ensure that ARIA is used effectively and responsibly to improve accessibility without introducing unintended barriers or complications for users of assistive technologies.

The "Five Rules of ARIA" are not explicitly part of the Web Content Accessibility Guidelines (WCAG) itself; rather, they are derived from best practices and guidelines within the broader context of web accessibility, including WCAG. These rules are often referenced in accessibility discussions and training materials as a practical framework for implementing Accessible Rich Internet Applications (ARIA) attributes responsibly.

However, the principles embodied in these rules align closely with the overarching goals and principles of WCAG, particularly in relation to providing accessible web content to people with disabilities. Let's map each of the rules to relevant WCAG principles:

1. **Use Native HTML When Possible:** This rule aligns with several principles of WCAG, including:
   - **Perceivable:** Guideline 1.3 - Adaptable: Content can be presented in different ways without losing information or structure.
   - **Understandable:** Guideline 3.2 - Predictable: Make web pages appear and operate in predictable ways.
   
2. **Avoid Changing Native Semantics:** This rule emphasizes consistency and predictability, which aligns with WCAG's principles related to clarity and consistency, such as:
   - **Understandable:** Guideline 3.2 - Predictable: Make web pages appear and operate in predictable ways.
   
3. **Ensure Keyboard Accessibility:** Keyboard accessibility is a fundamental aspect of making web content perceivable and operable for users who cannot use a mouse. This rule aligns closely with:
   - **Operable:** Guideline 2.1 - Keyboard Accessible: Make all functionality available from a keyboard.
   
4. **Avoid `role="presentation"` and `aria-hidden="true"` on Focusable Elements:** While not explicitly mentioned in WCAG, this rule is consistent with the principle of providing accessible names and ensuring that important information is available to all users. It supports principles such as:
   - **Perceivable:** Guideline 1.1 - Text Alternatives: Provide text alternatives for any non-text content so that it can be changed into other forms people need, such as large print, braille, speech, symbols, or simpler language.
   
5. **Provide Accessible Names for Interactive Elements:** This rule aligns with various WCAG principles related to providing accessible content, particularly:
   - **Perceivable:** Guideline 1.3 - Adaptable: Create content that can be presented in different ways without losing information or structure.
   - **Operable:** Guideline 2.4 - Navigable: Provide ways to help users navigate, find content, and determine where they are.

While not explicitly enumerated in WCAG, these rules serve as practical guidelines for developers striving to implement accessible web content in accordance with WCAG's overarching principles. They help ensure that ARIA is used appropriately to enhance accessibility without compromising usability or introducing new barriers for users with disabilities.

## Accessibility Tree
The accessibility tree is a fundamental concept in web accessibility, particularly in the context of how web browsers expose and communicate the structure and properties of web content to assistive technologies such as screen readers. It represents a hierarchical representation of the accessible elements within a web page, providing information about their roles, states, and properties to assistive technology tools, allowing them to interpret and present the content to users with disabilities effectively.

Here's a detailed breakdown of the key aspects of the accessibility tree:

1. **Hierarchical Structure:** Similar to the Document Object Model (DOM), which represents the structure of HTML elements in a web page, the accessibility tree also has a hierarchical structure. However, unlike the DOM, which focuses on the visual and interactive elements of a web page, the accessibility tree emphasizes the semantic and interactive aspects that are relevant for users with disabilities.

2. **Accessible Elements:** The accessibility tree contains information about the accessible elements present in the web page. These elements may include standard HTML elements (e.g., `<button>`, `<input>`, `<a>`), as well as elements that have been enhanced with Accessible Rich Internet Applications (ARIA) attributes to improve accessibility.

3. **Roles, States, and Properties:** Each accessible element in the accessibility tree is associated with various attributes that convey its role, state, and properties. For example, a button element might have a role of "button," a state of "pressed" (indicating whether it is currently activated), and properties such as its label or description.

4. **Relationships:** The accessibility tree also represents the relationships between different elements within the web page. For example, it identifies which elements are parents, children, or siblings of one another, as well as any other contextual relationships that are relevant for understanding the structure and function of the content.

5. **Updates and Dynamic Content:** The accessibility tree is dynamic and may change in response to user interactions or updates to the web page's content. For example, if new elements are added or removed from the DOM via JavaScript, the accessibility tree is updated accordingly to reflect these changes, ensuring that assistive technologies always have an accurate representation of the current state of the content.

6. **Exposure to Assistive Technologies:** Browsers expose the accessibility tree to assistive technologies through Accessibility APIs (Application Programming Interfaces). These APIs allow assistive technologies such as screen readers to programmatically access and interact with the information in the accessibility tree, enabling them to provide alternative means of accessing and navigating web content for users with disabilities.

In summary, the accessibility tree serves as a crucial bridge between the structural and semantic elements of a web page and the assistive technologies that help users with disabilities access and interact with that content. By providing a rich, hierarchical representation of accessible elements and their properties, the accessibility tree plays a central role in making the web more inclusive and accessible to all users.

## Accessible Elements and Their Properties
Accessible elements in the accessibility tree encompass a wide range of HTML elements and components that convey meaningful information or functionality to users. These elements include standard HTML elements as well as elements enhanced with Accessible Rich Internet Applications (ARIA) attributes.

Accessible elements in the accessibility tree have several properties such as "name", "description", "role", "state" etc. We are going to focus particularly on the "name" and "description" properties here.

1. **Name (Accessible Name):**
   - The name, also referred to as the accessible name, is a fundamental property of accessible elements in the accessibility tree. It represents the primary identifier or label associated with an element, which assistive technologies such as screen readers use to announce or identify the element to users.
   - The accessible name is crucial for conveying the purpose or function of an element to users with disabilities who rely on assistive technologies. It enables users to understand the meaning and significance of different elements on a web page.
   - The accessible name may be derived from various sources, including:
     - Text content: The visible text within an element serves as its accessible name. For example, the text displayed on a button or link.
     - `<label>` element: The `<label>` element in HTML provides an explicit association between form controls and their labels. The text content of the `<label>` element becomes the accessible name for the associated form control.
     - `alt` attribute: For images, the `alt` attribute provides alternative text that describes the content or purpose of the image. This alternative text serves as the accessible name for the image when it is announced by assistive technologies.
     - ARIA attributes: With Accessible Rich Internet Applications (ARIA), developers can explicitly specify the accessible name using attributes such as `aria-label` or `aria-labelledby`, providing custom labels for elements that may not have explicit text content or associated labels.

2. **Description:**
   - The description complements the accessible name by providing additional context or information about an element. While the accessible name is typically concise and identifies the element's primary purpose, the description offers more detailed information that may be necessary for users to understand its significance or function.
   - Assistive technologies may announce the description along with the accessible name to provide users with a more comprehensive understanding of the element.
   - Unlike the accessible name, which is often derived from explicit labels or text content, the description is often provided separately, either through additional text content within the element, through ARIA attributes such as `aria-describedby`, or through other means.
   - The description is particularly valuable for elements with complex or non-standard functionality, helping users understand how to interact with them effectively.

3. **Role (aria-role):**
    - Defines the role or purpose of the element, providing semantic information to assistive technologies about how the element should be interpreted and interacted with. For example, roles can include "button", "link", "menu", "textbox", "listbox", "checkbox", etc.

4. **State (aria-\<state>):**
    - Indicates the current state of the element, such as "expanded", "selected", "checked", "disabled", "hidden", etc. These states provide important information about the behavior and appearance of the element, allowing assistive technologies to convey its current status to users.

   
In summary, the name (accessible name) and description are essential properties of accessible elements in the accessibility tree, providing users with disabilities with the information they need to navigate and interact with web content effectively using assistive technologies. By ensuring that elements have clear, descriptive names and, when necessary, supplementary descriptions, developers can create more inclusive and accessible experiences for all users.

## ARIA Attributes
The accessibility tree is based on the DOM. While the DOM represents nodes and objects that make up a web page, the accessibility tree contains only the accessibility related information that will be used by assistive technologies. The way ARIA works is by modifying properties (such as name and description) of the objects (accessible elements) that make up this accessibility tree. ARIA attributes are used to modify these properties, in order to enhance the accessibility of web content by providing additional semantic information about elements that may not be adequately conveyed through native HTML semantics alone. 

Accessible Rich Internet Applications (ARIA) attributes are a set of HTML attributes introduced by the W3C's Web Accessibility Initiative (WAI) to enhance the accessibility of web content, particularly for users with disabilities. ARIA attributes provide additional semantic information about elements on a webpage, helping assistive technologies such as screen readers interpret and interact with dynamic or interactive content more effectively. Here's a detailed explanation of ARIA attributes:

1. **Purpose and Function:** ARIA attributes serve to augment the semantics of HTML elements, providing assistive technologies with information about the purpose, role, state, and properties of elements that may not be adequately conveyed through native HTML semantics alone.

2. **Accessibility Enhancement:** ARIA attributes help bridge the accessibility gap between traditional HTML elements and modern web applications, which often rely heavily on dynamic, interactive, and custom components that may not have native accessibility features.

3. **Attributes Categories:**
   - **Roles:** ARIA roles define the intended purpose or function of an element. Roles describe the type of element it represents (e.g., button, link, menu, tabpanel) and help assistive technologies understand how to interact with it.
   - **States and Properties:** ARIA attributes can describe the current state or properties of an element, such as whether it is expanded, selected, disabled, or has a certain value. These attributes provide valuable context for assistive technologies to convey the dynamic behavior of web components.

4. **Usage:** ARIA attributes are typically added directly to HTML elements using the `aria-` prefix followed by the attribute name (e.g., `aria-role`, `aria-label`, `aria-hidden`). Developers can also use ARIA attributes in conjunction with native HTML attributes to provide comprehensive accessibility information.

5. **Examples of ARIA Attributes:**
   - `aria-role`: Specifies the role of an element, indicating its purpose or function (e.g., `aria-role="button"`, `aria-role="navigation"`).
   - `aria-label`: Provides a text label that describes the element's purpose when the visible label is not sufficient (e.g., `aria-label="Search"`, `aria-label="Close"`).
   - `aria-hidden`: Indicates whether an element is visible or hidden from assistive technologies (e.g., `aria-hidden="true"` to hide decorative elements).
   - `aria-describedby`: Associates an element with another element that serves as its description or additional information (e.g., `aria-describedby="error-message"`).
   - `aria-expanded`: Indicates whether a collapsible element is expanded or collapsed (e.g., `aria-expanded="true"`).
   
6. **Compatibility and Support:** ARIA attributes are supported by modern web browsers and assistive technologies. However, it's essential to use them judiciously and ensure they are implemented correctly to avoid unintended consequences or accessibility issues.

### DOM -> Accessibility Tree -> Accessible Elements -> ARIA Attributes
1. **DOM (Document Object Model):** The DOM represents the structure of a web page as a hierarchical tree of objects, where each object corresponds to an HTML element on the page. The DOM captures the relationships between elements, their attributes, and the content they contain.

2. **Accessibility Tree:** The browser uses the information from the DOM to construct an accessibility tree, which represents the accessible elements on the page. The accessibility tree is similar to the DOM but is tailored specifically for assistive technologies. It includes additional accessibility-related information, such as roles, states, and properties, to ensure that users with disabilities can access and interact with the content effectively.

3. **Accessible Elements:** These are the nodes in the accessibility tree. Each accessible element corresponds to an element in the DOM but includes additional accessibility-related information. Accessible elements have properties such as name, description, role, state, and other attributes that assistive technologies use to convey the meaning and functionality of the elements to users.

4. **ARIA Attributes:** ARIA attributes are used to enhance the accessibility of web content by providing additional semantic information about elements that may not be adequately conveyed through native HTML semantics alone. ARIA attributes can be added to HTML elements to modify their properties dynamically and ensure they are properly represented in the accessibility tree.

   - For example, developers can use ARIA attributes like `aria-label`, `aria-describedby`, `aria-hidden`, `aria-role`, and others to specify the accessible name, description, role, state, or properties of elements, thus influencing how they are interpreted by assistive technologies and presented to users with disabilities.

In summary, ARIA attributes are used to manipulate the properties of accessible elements dynamically, ensuring that the accessibility tree accurately represents the content and functionality of a web page for users who rely on assistive technologies. By leveraging ARIA attributes effectively, developers can create more inclusive and accessible web experiences that cater to the diverse needs of all users.


It’s important to note that ARIA attributes can only modify the semantics or context of an element. ARIA attributes can’t:

+ modify an element’s appearance,
+ modify an element’s behavior,
+ add focusability, or
+ add keyboard event handling.

When you use ARIA, you will usually have to take additional steps to add in any missing semantics or functionality (for example, adding focusability and event handling with keyboard to \<div> buttons).

Now let's take a closer look to some of the most commonly used aria-attributes: `aria-label`, `aria-labelledby`, and `aria-describedby`. These attributes are essential for providing accessible names and descriptions for elements on a webpage, particularly when the native HTML semantics alone are insufficient to convey their meaning or purpose effectively.

### `aria-label`
The purpose of the "aria-label" attribute is to provide a descriptive label for an HTML element that might not have textual content visible on the screen or when the visible text is not descriptive enough for users relying on assistive technologies. This is particularly useful for elements like buttons, links, or other interactive components that rely solely on icons or images without accompanying text. By adding an "aria-label," developers can ensure that screen reader users understand the purpose or function of these elements. The `aria-label` attribute modifies the "name" property of the accessible element, on the accessibility tree. When added, the string value of the `aria-label` attribute becomes the element’s accessible name. However, aria-label does not have any effect on some HTML elements, such as \<div> or a \<span>.

1. **Syntax**: The "aria-label" attribute is added to an HTML element as an attribute, typically in the form `aria-label="description"`. The value of the attribute should be a text string that describes the purpose or function of the element it is associated with.

2. **Usage**: It can be applied to various HTML elements, but it's most commonly used with interactive elements such as buttons, links, form inputs, and other controls. For example:

    ```html
    <button aria-label="Add to Cart">
        <img src="cart-icon.png" alt="Cart">
    </button>
    ```

    In this example, the button contains an image of a shopping cart icon. The "aria-label" attribute provides an accessible label, "Add to Cart," to convey the button's function to screen reader users.

    Another way you could use aria-label is on landmark elements:
    
    ```html
    <nav aria-label='main navigation'>...</nav>
    ```

    Once a screen reader reaches the above HTML, it would announce “Main navigation, navigation landmark”. If you had multiple navigation elements on a page, you could give each a different aria-label value in order to separate them from one another, making them more understandable for screen reader users.

### `aria-labelledby`
The "aria-labelledby" attribute serves a similar purpose to "aria-label" but provides a more versatile method for associating accessible labels with HTML elements. "aria-labelledby" allows developers to reference one or more elements on the page as the source of the accessible label, rather than providing a direct label within the attribute itself.

The aria-labelledby attribute overrides both the native label and the aria-label attribute. aria-labelledby changes an element’s accessible name (created by aria-labelledby) to a concatenated string of the text contents or alt attributes of the labeling elements (the ones whose id are passed in).

1. **Syntax**: The "aria-labelledby" attribute is used to associate an HTML element with one or more elements on the page that serve as labels for the element. The syntax is `aria-labelledby="IDREF1 IDREF2 ..."`, where IDREF is the ID of the element providing the label(s).

2. **Usage**: Developers can apply the "aria-labelledby" attribute to various HTML elements, particularly those that require accessible labels but may not have explicit text content. This includes elements like buttons, links, form inputs, and other interactive components.

    The great thing about aria-labelledby is that not only can you pass in any number of id references, but you can also have an element reference itself. Keep in mind that you can’t pass in the same reference multiple times, because any subsequent references after the first will be ignored.

  ```html
    <!-- Here's the labelling element -->
    <h2 id='label'>Shirts</h2>

    <!-- And here's the labelled element. Note the order of the ID references passed in -->
    <button type='button' id='shop-btn' aria-labelledby='label shop-btn'>Shop Now</button>
  ```

  The HTML above would be announced by a screen reader as, “Shirts, shop now, button”. This can make multiple “shop now” buttons on a page unique from one another and thus provide additional context, making the page more understandable.

3. **Associating with Multiple Labels**: Unlike "aria-label," which provides a single label, "aria-labelledby" allows for the association of multiple labels by referencing multiple elements. This flexibility enables developers to compose complex accessible descriptions from multiple parts of the page.

4. **Dynamic Labeling**: One significant advantage of "aria-labelledby" is its support for dynamic labeling. Developers can dynamically change the content of the labeled elements, and the associated accessible label will update accordingly without needing to modify the target element itself.

5. **Accessibility**: When a user interacts with an element, the screen reader reads out the content of the labeled elements referenced by "aria-labelledby" in addition to the element's own content.

6. **Example**:

    ```html
    <div id="dynamicLabel">Dynamic Label</div>
    <button aria-labelledby="dynamicLabel">
        <img src="icon.png" alt="Icon">
    </button>
    ```

    In this example, the button is associated with the "dynamicLabel" div element using the "aria-labelledby" attribute. When a screen reader encounters the button, it will announce both the content of the button itself (the alt attribute of the image) and the content of the "dynamicLabel" div.

### `aria-describedby`
The "aria-describedby" attribute enables developers to associate descriptive information or help text with an HTML element, providing additional context or guidance to users, particularly those who rely on assistive technologies like screen readers. The aria-describedby attribute modifies the "description" property in the accessibility tree.

1. **Syntax**: The "aria-describedby" attribute is used to associate an HTML element with one or more elements on the page that contain descriptive information or help text. The syntax is similar to "aria-labelledby": `aria-describedby="IDREF1 IDREF2 ..."`, where IDREF is the ID of the element(s) providing the descriptive content.

2. **Usage**: Developers can apply the "aria-describedby" attribute to various HTML elements, such as form fields, buttons, or other interactive elements, where additional context or instructions may be beneficial for users.

3. **Associating with Descriptive Content**: The primary purpose of "aria-describedby" is to provide users with access to more detailed information related to a specific element on the page. This could include instructions on how to complete a form field, explanations of the purpose of a button, or any other relevant information.

4. **Accessibility**: Screen readers and other assistive technologies utilize the "aria-describedby" attribute to convey the associated descriptive content to users with disabilities. When a user interacts with an element, the screen reader reads out both the content of the element itself and the content of the elements referenced by "aria-describedby," providing a more comprehensive understanding of the element's purpose or function.

5. **Example**:

    ```html
    <label for="email">Email:</label>
    <input type="email" id="email" aria-describedby="emailHelp">
    <div id="emailHelp">Please enter your valid email address.</div>
    ```

    In this example, the input field for entering an email address is associated with the "emailHelp" div element using the "aria-describedby" attribute. When a screen reader encounters the input field, it will announce both the label ("Email") and the content of the "emailHelp" div ("Please enter your valid email address"), providing users with additional guidance.

    As an another example: 

    ```html
    <label>Password:
    <input type='password' aria-describedby='password-requirements' />
    </label>

    <!-- Meaningful text + ARIA! -->
    <span id='password-requirements'>Password must be at least 10 characters long.</span>
    ```

    When the \<input> element receives focus, a screen reader would announce, “Password, edit protected, password must be at least ten characters long.” This immediately notifies a screen reader user of any requirements for the password they want to choose, any time the input receives focus.

6. **Dynamic Content**: Similar to "aria-labelledby," "aria-describedby" supports dynamic content updates. Developers can modify the content of the referenced elements dynamically, and the associated descriptive information will update accordingly, ensuring that users always have access to the most relevant information.

## Hiding Content From the Accessibility Tree
Similar to how you can visually hide elements with the hidden HTML attribute or the display and visibility CSS properties, you can use the aria-hidden attribute to hide certain elements, such as decorative images and icons, from the accessibility tree. The difference with aria-hidden, however, is that the element will remain visible to sighted users. This can be especially useful when you want to add an icon inside of another element. For example, if we were to use Material Icons inside of a button:

```html
<!-- Example 1 -->
<button type='button'>
  <span class='material-icons'>add</span>
  Add Book
</button>

<!-- Example 2 -->
<button type='button'>
  <span class='material-icons' aria-hidden='true'>add</span>
  Add Book
</button>
```

While both of the above examples would look visually identical, the button in Example 1 would be announced by a screen reader as, “Add add book, button”. The text content of the \<span> and the text content of the button itself are concatenated as the accessible name of the button. The button in Example 2, however, hides the \<span> from the accessibility tree so its text content isn’t added to the button’s accessible name, meaning a screen reader would correctly announce “Add book, button”.

Be careful when using this attribute, though. When you give an element aria-hidden='true', all children of that element will also become hidden to the accessibility tree. Adding aria-hidden='false' to a child element won’t have any effect if one of its parents still has aria-hidden='true', either.

You should also be careful not to give an element aria-hidden='true' if it is focusable. Doing so would cause nothing to be announced when the element receives focus, which would confuse users that use a screen reader and navigate the page via a keyboard.

---
### Knowledge Check

**Q1.** What purpose does WAI-ARIA serve?

**A1.** WAI-ARIA stands for Web Accessibility Initiative - Accessible Rich Internet Applications. It is a set of attributes that can be added to HTML elements to improve the accessibility of web content and applications for people with disabilities. Developed by the World Wide Web Consortium (W3C), WAI-ARIA provides a standardized way to enhance the semantics of web content, particularly for dynamic and interactive components that may not be fully accessible to all users using conventional HTML alone.

The primary goal of WAI-ARIA is to bridge the accessibility gap between conventional web content and modern web applications, which often rely heavily on JavaScript, AJAX, and other dynamic technologies that can pose challenges for users who rely on assistive technologies like screen readers. By providing additional metadata about the roles, states, and properties of elements, WAI-ARIA enables assistive technologies to better interpret and interact with complex web interfaces.

**Q2.** What are the four things ARIA can’t do?

**A2.** It’s important to note that ARIA can only modify the semantics or context of an element. ARIA attributes can’t:

+ modify an element’s appearance,
+ modify an element’s behavior,
+ add focusability, or
+ add keyboard event handling.

When you use ARIA, you will usually have to take additional steps to add in any missing semantics or functionality (for example, adding focusability and event handling with keyboard to \<div> buttons).

**Q3.** What are the five rules of ARIA?

**A3.** ARIA can be extremely powerful when used correctly, but it can be equally as dangerous when used incorrectly. Because of this, you should keep in mind that **no ARIA is better than bad ARIA**, even when you have the best intentions.

The "Five Rules of ARIA" are guidelines established to help developers effectively implement Accessible Rich Internet Applications (ARIA) attributes in web content. These rules provide a structured approach to utilizing ARIA in a way that enhances accessibility without causing unintended consequences. Here they are:

1. **If you can use a native HTML element or attribute with the semantics and behavior you require already built-in, instead of re-purposing an element and adding ARIA roles, states, and properties to make it accessible, then do so.** 
   - This rule emphasizes the importance of using native HTML elements whenever possible. Native elements already come with built-in accessibility features and semantics. For example, using `<button>` for buttons, `<input type="checkbox">` for checkboxes, etc., is preferred over trying to create similar functionality using other elements with ARIA attributes.

2. **Do not change native semantics, unless you really have to.**
   - It's crucial to respect the native semantics of HTML elements. Altering these semantics using ARIA can lead to confusion for assistive technology users. If an element already has a specific semantic meaning, avoid changing it unless absolutely necessary for accessibility reasons.

3. **All interactive ARIA controls must be usable with the keyboard.**
   - This rule underscores the importance of keyboard accessibility. Users who cannot operate a mouse rely on keyboard navigation to interact with web content. Therefore, any interactive elements enhanced with ARIA attributes should be fully operable via keyboard input, ensuring equal access to all users.

4. **Do not use `role="presentation"` or `aria-hidden="true"` on a focusable element.**
   - `role="presentation"` and `aria-hidden="true"` are ARIA attributes used to convey to assistive technologies that an element is decorative or should be hidden from accessibility APIs, respectively. However, if an element is focusable (such as a link or button), these attributes should not be used because doing so would hide important accessibility information from keyboard users.

5. **All interactive elements must have an accessible name.**
   - An accessible name is essential for conveying the purpose or function of an interactive element to assistive technology users. Whether it's a button, link, form field, or any other interactive element, it should have a clear and descriptive accessible name that can be announced by screen readers.

Following these rules helps ensure that ARIA is used effectively and responsibly to improve accessibility without introducing unintended barriers or complications for users of assistive technologies.

The "Five Rules of ARIA" are not explicitly part of the Web Content Accessibility Guidelines (WCAG) itself; rather, they are derived from best practices and guidelines within the broader context of web accessibility, including WCAG. These rules are often referenced in accessibility discussions and training materials as a practical framework for implementing Accessible Rich Internet Applications (ARIA) attributes responsibly.

**Q4.** What is the accessibility tree?

**A4.** The accessibility tree is a fundamental concept in web accessibility, particularly in the context of how web browsers expose and communicate the structure and properties of web content to assistive technologies such as screen readers. It represents a hierarchical representation of the accessible elements within a web page, providing information about their roles, states, and properties to assistive technology tools, allowing them to interpret and present the content to users with disabilities effectively.

Here's a detailed breakdown of the key aspects of the accessibility tree:

1. **Hierarchical Structure:** Similar to the Document Object Model (DOM), which represents the structure of HTML elements in a web page, the accessibility tree also has a hierarchical structure. However, unlike the DOM, which focuses on the visual and interactive elements of a web page, the accessibility tree emphasizes the semantic and interactive aspects that are relevant for users with disabilities.

2. **Accessible Elements:** The accessibility tree contains information about the accessible elements present in the web page. These elements may include standard HTML elements (e.g., `<button>`, `<input>`, `<a>`), as well as elements that have been enhanced with Accessible Rich Internet Applications (ARIA) attributes to improve accessibility.

3. **Roles, States, and Properties:** Each accessible element in the accessibility tree is associated with various attributes that convey its role, state, and properties. For example, a button element might have a role of "button," a state of "pressed" (indicating whether it is currently activated), and properties such as its label or description.

4. **Relationships:** The accessibility tree also represents the relationships between different elements within the web page. For example, it identifies which elements are parents, children, or siblings of one another, as well as any other contextual relationships that are relevant for understanding the structure and function of the content.

5. **Updates and Dynamic Content:** The accessibility tree is dynamic and may change in response to user interactions or updates to the web page's content. For example, if new elements are added or removed from the DOM via JavaScript, the accessibility tree is updated accordingly to reflect these changes, ensuring that assistive technologies always have an accurate representation of the current state of the content.

6. **Exposure to Assistive Technologies:** Browsers expose the accessibility tree to assistive technologies through Accessibility APIs (Application Programming Interfaces). These APIs allow assistive technologies such as screen readers to programmatically access and interact with the information in the accessibility tree, enabling them to provide alternative means of accessing and navigating web content for users with disabilities.

In summary, the accessibility tree serves as a crucial bridge between the structural and semantic elements of a web page and the assistive technologies that help users with disabilities access and interact with that content. By providing a rich, hierarchical representation of accessible elements and their properties, the accessibility tree plays a central role in making the web more inclusive and accessible to all users.

**Q5.** What are the differences between the three ARIA labels?

**A5.** **ARIA Attributes:** ARIA attributes are used to enhance the accessibility of web content by providing additional semantic information about elements that may not be adequately conveyed through native HTML semantics alone. ARIA attributes can be added to HTML elements to modify their properties dynamically and ensure they are properly represented in the accessibility tree.

   - For example, developers can use ARIA attributes like `aria-label`, `aria-describedby`, `aria-hidden`, `aria-role`, and others to specify the accessible name, description, role, state, or properties of elements, thus influencing how they are interpreted by assistive technologies and presented to users with disabilities.

In summary, ARIA attributes are used to manipulate the properties of accessible elements dynamically, ensuring that the accessibility tree accurately represents the content and functionality of a web page for users who rely on assistive technologies. By leveraging ARIA attributes effectively, developers can create more inclusive and accessible web experiences that cater to the diverse needs of all users.


It’s important to note that ARIA attributes can only modify the semantics or context of an element. ARIA attributes can’t:

+ modify an element’s appearance,
+ modify an element’s behavior,
+ add focusability, or
+ add keyboard event handling.

When you use ARIA, you will usually have to take additional steps to add in any missing semantics or functionality (for example, adding focusability and event handling with keyboard to \<div> buttons).

Now let's take a closer look to some of the most commonly used aria-attributes: `aria-label`, `aria-labelledby`, and `aria-describedby`. These attributes are essential for providing accessible names and descriptions for elements on a webpage, particularly when the native HTML semantics alone are insufficient to convey their meaning or purpose effectively.

### `aria-label`
The purpose of the "aria-label" attribute is to provide a descriptive label for an HTML element that might not have textual content visible on the screen or when the visible text is not descriptive enough for users relying on assistive technologies. This is particularly useful for elements like buttons, links, or other interactive components that rely solely on icons or images without accompanying text. By adding an "aria-label," developers can ensure that screen reader users understand the purpose or function of these elements. The `aria-label` attribute modifies the "name" property of the accessible element, on the accessibility tree. When added, the string value of the `aria-label` attribute becomes the element’s accessible name. However, aria-label does not have any effect on some HTML elements, such as \<div> or a \<span>.

1. **Syntax**: The "aria-label" attribute is added to an HTML element as an attribute, typically in the form `aria-label="description"`. The value of the attribute should be a text string that describes the purpose or function of the element it is associated with.

2. **Usage**: It can be applied to various HTML elements, but it's most commonly used with interactive elements such as buttons, links, form inputs, and other controls. For example:

    ```html
    <button aria-label="Add to Cart">
        <img src="cart-icon.png" alt="Cart">
    </button>
    ```

    In this example, the button contains an image of a shopping cart icon. The "aria-label" attribute provides an accessible label, "Add to Cart," to convey the button's function to screen reader users.

    Another way you could use aria-label is on landmark elements:
    
    ```html
    <nav aria-label='main navigation'>...</nav>
    ```

    Once a screen reader reaches the above HTML, it would announce “Main navigation, navigation landmark”. If you had multiple navigation elements on a page, you could give each a different aria-label value in order to separate them from one another, making them more understandable for screen reader users.

### `aria-labelledby`
The "aria-labelledby" attribute serves a similar purpose to "aria-label" but provides a more versatile method for associating accessible labels with HTML elements. "aria-labelledby" allows developers to reference one or more elements on the page as the source of the accessible label, rather than providing a direct label within the attribute itself.

The aria-labelledby attribute overrides both the native label and the aria-label attribute. aria-labelledby changes an element’s accessible name (created by aria-labelledby) to a concatenated string of the text contents or alt attributes of the labeling elements (the ones whose id are passed in).

1. **Syntax**: The "aria-labelledby" attribute is used to associate an HTML element with one or more elements on the page that serve as labels for the element. The syntax is `aria-labelledby="IDREF1 IDREF2 ..."`, where IDREF is the ID of the element providing the label(s).

2. **Usage**: Developers can apply the "aria-labelledby" attribute to various HTML elements, particularly those that require accessible labels but may not have explicit text content. This includes elements like buttons, links, form inputs, and other interactive components.

    The great thing about aria-labelledby is that not only can you pass in any number of id references, but you can also have an element reference itself. Keep in mind that you can’t pass in the same reference multiple times, because any subsequent references after the first will be ignored.

  ```html
    <!-- Here's the labelling element -->
    <h2 id='label'>Shirts</h2>

    <!-- And here's the labelled element. Note the order of the ID references passed in -->
    <button type='button' id='shop-btn' aria-labelledby='label shop-btn'>Shop Now</button>
  ```

  The HTML above would be announced by a screen reader as, “Shirts, shop now, button”. This can make multiple “shop now” buttons on a page unique from one another and thus provide additional context, making the page more understandable.

3. **Associating with Multiple Labels**: Unlike "aria-label," which provides a single label, "aria-labelledby" allows for the association of multiple labels by referencing multiple elements. This flexibility enables developers to compose complex accessible descriptions from multiple parts of the page.

4. **Dynamic Labeling**: One significant advantage of "aria-labelledby" is its support for dynamic labeling. Developers can dynamically change the content of the labeled elements, and the associated accessible label will update accordingly without needing to modify the target element itself.

5. **Accessibility**: When a user interacts with an element, the screen reader reads out the content of the labeled elements referenced by "aria-labelledby" in addition to the element's own content.

6. **Example**:

    ```html
    <div id="dynamicLabel">Dynamic Label</div>
    <button aria-labelledby="dynamicLabel">
        <img src="icon.png" alt="Icon">
    </button>
    ```

    In this example, the button is associated with the "dynamicLabel" div element using the "aria-labelledby" attribute. When a screen reader encounters the button, it will announce both the content of the button itself (the alt attribute of the image) and the content of the "dynamicLabel" div.

### `aria-describedby`
The "aria-describedby" attribute enables developers to associate descriptive information or help text with an HTML element, providing additional context or guidance to users, particularly those who rely on assistive technologies like screen readers. The aria-describedby attribute modifies the "description" property in the accessibility tree.

1. **Syntax**: The "aria-describedby" attribute is used to associate an HTML element with one or more elements on the page that contain descriptive information or help text. The syntax is similar to "aria-labelledby": `aria-describedby="IDREF1 IDREF2 ..."`, where IDREF is the ID of the element(s) providing the descriptive content.

2. **Usage**: Developers can apply the "aria-describedby" attribute to various HTML elements, such as form fields, buttons, or other interactive elements, where additional context or instructions may be beneficial for users.

3. **Associating with Descriptive Content**: The primary purpose of "aria-describedby" is to provide users with access to more detailed information related to a specific element on the page. This could include instructions on how to complete a form field, explanations of the purpose of a button, or any other relevant information.

4. **Accessibility**: Screen readers and other assistive technologies utilize the "aria-describedby" attribute to convey the associated descriptive content to users with disabilities. When a user interacts with an element, the screen reader reads out both the content of the element itself and the content of the elements referenced by "aria-describedby," providing a more comprehensive understanding of the element's purpose or function.

5. **Example**:

    ```html
    <label for="email">Email:</label>
    <input type="email" id="email" aria-describedby="emailHelp">
    <div id="emailHelp">Please enter your valid email address.</div>
    ```

    In this example, the input field for entering an email address is associated with the "emailHelp" div element using the "aria-describedby" attribute. When a screen reader encounters the input field, it will announce both the label ("Email") and the content of the "emailHelp" div ("Please enter your valid email address"), providing users with additional guidance.

    As an another example: 

    ```html
    <label>Password:
    <input type='password' aria-describedby='password-requirements' />
    </label>

    <!-- Meaningful text + ARIA! -->
    <span id='password-requirements'>Password must be at least 10 characters long.</span>
    ```

    When the \<input> element receives focus, a screen reader would announce, “Password, edit protected, password must be at least ten characters long.” This immediately notifies a screen reader user of any requirements for the password they want to choose, any time the input receives focus.

6. **Dynamic Content**: Similar to "aria-labelledby," "aria-describedby" supports dynamic content updates. Developers can modify the content of the referenced elements dynamically, and the associated descriptive information will update accordingly, ensuring that users always have access to the most relevant information.

**Q6.** What does the aria-hidden attribute do?

**A6.** Similar to how you can visually hide elements with the hidden HTML attribute or the display and visibility CSS properties, you can use the aria-hidden attribute to hide certain elements, such as decorative images and icons, from the accessibility tree. The difference with aria-hidden, however, is that the element will remain visible to sighted users. This can be especially useful when you want to add an icon inside of another element. For example, if we were to use Material Icons inside of a button:

```html
<!-- Example 1 -->
<button type='button'>
  <span class='material-icons'>add</span>
  Add Book
</button>

<!-- Example 2 -->
<button type='button'>
  <span class='material-icons' aria-hidden='true'>add</span>
  Add Book
</button>
```

While both of the above examples would look visually identical, the button in Example 1 would be announced by a screen reader as, “Add add book, button”. The text content of the \<span> and the text content of the button itself are concatenated as the accessible name of the button. The button in Example 2, however, hides the \<span> from the accessibility tree so its text content isn’t added to the button’s accessible name, meaning a screen reader would correctly announce “Add book, button”.