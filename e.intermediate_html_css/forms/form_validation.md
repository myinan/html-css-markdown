# Client-side Form Validation
Validations allow us to set specific constraints or rules that determine what data users can enter into an input. When a user enters data that breaks the rules, a message will appear, providing feedback on what was wrong with the entered data and how to fix it.

Validations are a vital ingredient in well-designed forms. They help protect our backend systems from receiving incorrect data, and they help make the experience of interacting with our form as simple as possible for our users.

### "required" Validation
We will often want to ensure specific fields have been filled in before submitting the form, for example, the email and password in a login form.

To make a field required, we simply add the `required` attribute to it.

To ensure a good user experience and to meet accessibility guidelines, we should always indicate which fields are required. This will often be done by adding an asterisk(*) to the required field label.

### Text Length Validations
Sometimes we will want users to enter a minimum or a maximum amount of text into a field. Real-world examples of using these validations would be the old 140 character limit that Twitter used to have in its status field or having minimum and maximum length constraints on a username field.

**Minimum length validation**: To add the minimum length validation, we give the form control a `minlength` attribute with an integer value that represents the minimum amount of characters we want to allow in the form control.

**Maximum length validation**: To add a maximum length validation, we give the form control a `maxlength` attribute with an integer value which represents the maximum amount of characters we want to allow in the form control.

### Number Range Validations
Just like we often need to control the length of text-based form controls, there will be many situations where we will want to control the range of values users can enter into number based form controls.

We can do this with the `min` and `max` attributes, which allows us to set the lower and upper bounds of the value entered into the form control. The min and max attributes only work with number-based form controls such as the number, dates and time inputs.

When the data entered by the user doesn't adhere to the min or max value set, the value is considered invalid in constraint validation and will match the :invalid and :out-of-range pseudo-classes.

### Pattern Validations
To ensure we get the correct information from users, we will often want to ensure data matches a particular pattern. Real-world applications would be checking if a credit card number or a zipcode is in the correct format.

To add a pattern validation, we give the form control a `pattern` attribute with a `regular expression` as the value. For example we can use pattern validation to ensure a US zip code is in the correct format (5 numbers followed by an optional dash and 4 more numbers).

The pattern attribute can only be used on \<input> elements. Some input elements already validate data that matches a certain pattern. For example, the email input field will make sure a valid email is entered and the url input element will check to ensure the URL starts with http or https.

**IMPORTANT!**: The built-in validations will take you far with ensuring your users enter the correct data. They are quick and easy to add. However, they have their limitations.<br>
Sometimes you will need to include validations that the built-in validations won’t be able to do. For example, validating that a password input and password confirmation input have the same value or validating that a username has not already been taken. We are also limited with what we can do with styling the validation messages and the content within them.<br>
In this case, we will need to get creative and make custom validations using JavaScript and CSS. We’ll dive into how to achieve validation via JavaScript in a future lesson.<br>
It’s also worth noting client-side validations are not a silver bullet for ensuring users enter the correct data. To ensure the integrity of any user data coming into our systems, we should also have server-side validations in place. We will cover this side of validations later in the curriculum.

---
### Knowledge Check

**Q1.** What does the required validation do?

**A1.** `required` boolean attribute set on an input field will require the field to be filled before submission, otherwise the browser will show an error message to the user indicating that the field must be filled before it's submitted.

**Q2.** What validations can you use for checking text length?

**A2.** For text input fields, we can use `minlength` and `maxlength` validation attributes to check input text length.

**Q3.** How can you validate the minimum and maximum of numeric inputs?

**A3.** `min` and `max` attributes can be used to set minimum and maximum allowed values for numeric inputs.

**Q4.** What can you use the pattern validation for?

**A4.** We could use the `pattern` attribute to validate if the input provided by the user conforms to a particular pattern. The pattern attribute accepts a regular expression as value, then the user input is tested against the set regular expression to determine whether it's valid or invalid.

**Q5.** What pseudo CSS selectors are available for styling valid and invalid inputs?

**A5.** `:valid` and `:invalid` pseudo-classes can be used to style HTML elements based on their current validation status.


