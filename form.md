# Forms

- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form

```html
<form action="" method="get" class="form-example">
  <div class="form-example">
    <label for="name">Enter your name: </label>
    <input type="text" name="name" id="name" required />
  </div>
  <div class="form-example">
    <label for="email">Enter your email: </label>
    <input type="email" name="email" id="email" required />
  </div>
  <div class="form-example">
    <input type="submit" value="Subscribe!" />
  </div>
</form>
```

enctype:

- application/x-www-form-urlencoded: default

target:

- `_self`:
- `_blank`:
- `_parent`:
- `_top`:

## Client-side form validation

- https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation

Client-side validation is an initial check and an important feature of good user experience; by catching invalid data on the client-side, the user can fix it straight away

However, Your apps should always perform security checks on any form-submitted data on the server-side as well as the client-side, because client-side validation is too easy to bypass

Read [Website security](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Website_security) for an idea of what could happen

- "This field is required"
- "Please enter your phone number in the format xxx-xxxx"
- "Please enter a valid email address"
- "Your password needs to be between 8 and 30 characters long and contain one uppercase letter, one symbol, and a number."

This is called form validation. When you enter data, the browser and/or the web server will check to see that the data is in the correct format and within the constraints set by the application

If the information is correctly formatted, the application allows the data to be submitted to the server and (usually) saved in a database; if the information isn't correctly formatted, it gives the user an error message explaining what needs to be corrected, and lets them try again.

**Different types of client-side validation**:

- Built-in form validation uses HTML form validation features - Built-in form validation has better performance than JavaScript, but it is not as customizable as JavaScript validation
- JavaScript validation is coded using JavaScript. This validation is completely customizable

### Using built-in form validation

- `required`: Specifies whether a form field needs to be filled in before the form can be submitted.
- `minlength` and `maxlength`: Specifies the minimum and maximum length of textual data (strings).
- `min` and `max`: Specifies the minimum and maximum values of numerical input types.
- `type`: Specifies whether the data needs to be a number, an email address, or some other specific preset type.
- `pattern`: Specifies a regular expression that defines a pattern the entered data needs to follow.

> When an element is valid, the following things are true:

1. The element matches the `:valid` CSS pseudo-class, which lets you apply a specific style to valid elements
2. If the user tries to send the data, the browser will submit the form, provided there is nothing else stopping it from doing so (e.g., JavaScript).

> When an element is invalid, the following things are true:

1. The element matches the `:invalid` CSS pseudo-class, and sometimes other UI pseudo-classes (e.g., `:out-of-range`) depending on the error, which lets you apply a specific style to invalid elements.
2. If the user tries to send the data, the browser will block the form and display an error message.

> **Note**: There are several errors that will prevent the form from being submitted, including a `badInput`, `patternMismatch`, `rangeOverflow` or `rangeUnderflow`, `stepMismatch`, `tooLong` or `tooShort`, `typeMismatch`, `valueMissing`,

### The Constraint Validation API

The Constraint Validation API consists of a set of methods and properties available on the following form element DOM interfaces:

- `HTMLInputElement` (represents an `<input>` element): https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement
- `HTMLTextAreaElement` (represents a `<textarea>` element): https://developer.mozilla.org/en-US/docs/Web/API/HTMLTextAreaElement

The Constraint Validation API makes the following properties available on the above elements.

- `validationMessage`: Returns a localized message describing the validation constraints that the control doesn't satisfy (if any). If the control is not a candidate for constraint validation (`willValidate` is `false`) or the element's value satisfies its constraints (is valid), this will return an empty string.
- `validity`: Returns a ValidityState object that contains several properties describing the validity state of the element. You can find full details of all the available properties in the ValidityState reference page; below is listed a few of the more common ones:
- `willValidate`: Returns `true` if the element will be validated when the form is submitted; `false` otherwise.

The Constraint Validation API also makes the following methods available on the above elements and the form element.

- `checkValidity()`: Returns true if the element's value has no validity problems; false otherwise. If the element is invalid, this method also fires an invalid event on the element.
- `reportValidity()`: Reports invalid field(s) using events. This method is useful in combination with preventDefault() in an onSubmit event handler.
- `setCustomValidity(message)`: Adds a custom error message to the element; if you set a custom error message, the element is considered to be invalid, and the specified error is displayed. This lets you use JavaScript code to establish a validation failure other than those offered by the standard HTML validation constraints. The message is shown to the user when reporting the problem.

### Implementing a customized error message

> Customizing these error messages is one of the most common use cases of the Constraint Validation API

- store a reference to the email input, then add an event listener to it that runs the contained code each time the value inside the input is changed
- check whether the email input's `validity.typeMismatch` property returns `true`, meaning that the contained value doesn't match the pattern for a well-formed email address. If so, we call the `setCustomValidity()` method with a custom message
- If the `validity.typeMismatch` property returns `false`, we call the `setCustomValidity()` method with an empty string. This renders the input valid, so the form will submit

## Sending Form Data

- https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data

Once the form data has been validated on the client-side, it is okay to submit the form.

...what happens when a user submits a form — where does the data go, and how do we handle it when it gets there?

### Client/server architecture

At its most basic, the web uses a client/server architecture that can be summarized as follows: a client (usually a web browser) sends a request to a server (most of the time a web server like Apache, Nginx, IIS, Tomcat, etc.), using the HTTP protocol. The server answers the request using the same protocol.

> _An HTML form_ on a web page _is_ nothing more than a convenient user-friendly _way to configure an HTTP request to send data to a server_. This _enables the user to provide information to be delivered in the HTTP request_.

### On the client side: defining how to send the data

The `<form>` element defines how the data will be sent. All of its attributes
are designed to let you configure the request to be sent when a user hits a submit button. The two most important attributes are `action` and `method`.

### The action attribute

- The `action` attribute defines where the data gets sent
- Its value must be a valid relative or absolute `URL`
- If this attribute isn't provided, the data will be sent to current page

```html
<!-- absolute url -->
<form action="https://example.com">…</form>
<!-- relative url -->
<form action="/somewhere_else">…</form>
```

> **Note**: It's possible to specify a URL that uses the HTTPS (secure HTTP) protocol. When you do this, the data is encrypted along with the rest of the request

### The method attribute

- The `method` attribute defines how data is sent
- The HTTP protocol provides several ways to perform a request
- the most common being the `GET` method and the `POST` method

Each time you want to reach a resource on the Web, the browser sends a request to a URL. An HTTP request consists of two parts:

1. a `header` that contains a set of global metadata about the browser's capabilities, and
2. a `body` that can contain information necessary for the server to process the specific request

- The `GET` method is the method used by the browser to ask the server to send back a given resource
- The data is appended to the URL as a series of name/value pairs. After the URL web address has ended, we include a question mark (`?`) followed by the name/value pairs, each one separated by an ampersand (`&`)
- The HTTP request looks like this: `GET /?say=Hi&to=Mom HTTP/2.0`

### The POST method

- The `POST` method is a little different.
- It's the `method` the browser uses to talk to the server when asking for a response that takes into account the data provided in the body of the HTTP request
- If a form is sent using this method, the data is appended to the body of the HTTP request

```html
<form action="http://www.foo.com" method="GET"></form>
<form action="http://www.foo.com" method="POST"></form>
```

```
GET /?say=Hi&to=Mom HTTP/2.0

POST / HTTP/2.0
Host: foo.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 13
```

- The `Content-Length` header indicates the size of the body, and the
- `Content-Type` header indicates the type of resource sent to the server

### Viewing HTTP requests

- https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data#viewing_http_requests
