# Netlify Form for Portfolio

> https://jameskernicky.netlify.app/

For very simple form submissions that you get an email try using Netlify forms. You don't need any JavaScript (client or server side).

- https://docs.netlify.com/forms/setup/

Netlify’s serverless form handling allows you to manage forms without extra API calls or additional JavaScript

1. Once enabled, the built-in form detection feature allows our build system to automatically parse your HTML at deploy time, so there’s no need for you to make an API call or include extra JavaScript on your site
2. To get started, enable `automatic form detection` and then add a `netlify` attribute to your HTML form

Visit our [form submissions](https://docs.netlify.com/forms/submissions/) doc to learn more about the form submissions UI, API endpoints, and more

## Automatic form detection

If you would like Netlify to automatically manage your form submissions, you need to enable form detection

### Enable form detection

To enable form detection for your site:

1. In the Netlify UI (for each deploy), go to Forms.
2. Select Enable form detection.

Starting with your next site deploy, Netlify will automatically scan your deploys for forms that require submission handling

### HTML forms

Once you enable form detection, add an HTML form to your site with a `data-netlify="true"` or a netlify attribute in the `<form>` tag. Deploy your site with that form included and you can start receiving submissions in your Netlify site admin panel.

Your form’s `name` attribute determines what we call the form in the Netlify UI. If you have more than one form on a site, each form should have a different `name` attribute.

Here’s an example of how to use the data-netlify="true" attribute or the netlify attribute in your form:

```html
<form name="contact" method="POST" data-netlify="true">
  <p>
    <label>Your Name: <input type="text" name="name" /></label>
  </p>
  <p>
    <label>Your Email: <input type="email" name="email" /></label>
  </p>
  <p>
    <label>Message: <textarea name="message"></textarea></label>
  </p>
  <p>
    <button type="submit">Send</button>
  </p>
</form>
```

When Netlify parses the static HTML for a form you’ve added, the build system automatically strips the `data-netlify="true"` or `netlify` attribute from the `<form>` tag and injects a hidden input named `form-name`.

In the resulting HTML that’s deployed, the `data-netlify="true"` or `netlify` attribute is gone, and the hidden `form-name` input’s value matches the `name` attribute of `<form>` like this:

```html
<input type="hidden" name="form-name" value="contact" />
```

### JavaScript forms

- https://docs.netlify.com/forms/setup/#javascript-forms - `SKIP`

### Success messages

- https://docs.netlify.com/forms/setup/#success-messages

By default, when visitors complete a form, they are redirected to a page with a generically styled success message with a link back to the form page

Custom Success Page

- You can replace the default success page with a custom page you create by adding an `action` attribute to the `<form>` tag, entering the path of your custom page (like "/pages/success") as the value.
- The path must be relative to the site root, starting with a `/`

> use div > label + input

Portfolio forms

1. https://portfolio-site-cyphermoon.vercel.app/#contact_section
2. https://davidbilson.vercel.app/#contact
3. https://nathaniel-grandinette.netlify.app/ - label display inline-block - copy the styles as a starter
4.

### File uploads

> Skip

### More Forms resources

- Spam filters: https://docs.netlify.com/forms/spam-filters/
- Form submissions: SEE BELOW
- Form submission notifications: https://docs.netlify.com/forms/notifications/
- Troubleshooting tips: https://docs.netlify.com/forms/troubleshooting-tips/
- Forms usage and billing: https://docs.netlify.com/forms/usage-and-billing/

## form submissions

- https://docs.netlify.com/forms/submissions/

## Billing and emails per month

- https://docs.netlify.com/accounts-and-billing/billing-faq/
