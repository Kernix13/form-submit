# Netlify Form for Portfolio

> https://jameskernicky.netlify.app/

> Netlify comes with `built-in form handling`

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

Once you enable form detection, add an HTML form to your site with a `data-netlify="true"` or a `netlify` attribute in the `<form>` tag. Deploy your site with that form included and you can start receiving submissions in your Netlify site admin panel.

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

1. Spam filters: https://docs.netlify.com/forms/spam-filters/

- All form submissions are filtered for spam using Akismet
- Its signatures database is constantly improving, and the Akismet API can be used for all sorts of applications, including Netlify Forms submissions
- VALIDATIONS: As soon as the validation completes, you will be notified about the new message
- Akismet runs in the background for every form submission

2. Form submission notifications: https://docs.netlify.com/forms/notifications/

- Send form notifications to email, webhooks, or a Slack workspace
- To send form notifications to email or webhooks: `Pro account`: Site configuration > Notifications > Emails and webhooks > Form submission notifications: https://app.netlify.com/sites/jameskernicky/configuration/notifications#form-submission-notifications
- To send form notifications to a Slack workspace: `Beta`: https://docs.netlify.com/integrations/slack-app/

3. Troubleshooting tips: https://docs.netlify.com/forms/troubleshooting-tips/

> If you have questions that aren’t answered here, visit our Support Forums to get more advice about how to debug your form: https://answers.netlify.com/t/support-guide-form-problems-form-debugging-404-when-submitting/92

- `Custom success page`: If you’re having trouble using the form `action` to customize the success page, try linking to your custom success page from somewhere on the same page as the form - Use the same exact path in your test link as you’re trying to use for the `action` attribute, and make sure the link works there before digging further into your form
- `Extra spam prevention`: If you’re adding a `honeypot` field or reCAPTCHA 2 challenge, you can check the form detail page to confirm whether or not the Extra spam prevention has been successfully enabled
- `Missing submissions`: Here are some common causes and solutions for missing form submissions ... 1) Test submissions flagged as spam | 2) Form detection disabled

4. Forms usage and billing: https://docs.netlify.com/forms/usage-and-billing/

> Check it out later

5. Form submissions - see below

## Form submissions

- https://docs.netlify.com/forms/submissions/

1. Form submissions UI:

- You can find all submissions to your Netlify forms in your site’s Forms tab
- Select a form name from the Active forms list to access the submissions for that form
- By default, only verified submissions are listed.
- You can switch to spam submissions using a menu above the list

2. Export form submissions to CSV - `SKIP`

3. Change a form submission’s state

- You can change the state of a submission from spam to verified or vice versa

4. Delete a form submission

- You can delete both verified submissions and spam submissions

5. Delete a form: `SKIP`

## Billing and emails per month

- https://docs.netlify.com/accounts-and-billing/billing-faq/

```html
<!-- From Will's site: https://bushblade.co.uk/contact -->
<!-- check out https://gitlab.com/bushblade -->
<article style="margin: 30% auto 0px; text-align: center;">
  <h2>Message Sent!</h2>
  <p>
    <span role="img" aria-label="mail">📩</span> Your message is on it's way to
    me and I'll get back to you as soon as I can. Thanks for getting in touch.
  </p>
</article>
```

.................................................

## From Discord

the Netlify forms works great. I've seen their success message with a back button on other dev portfolio sites, but I created a success page and that works also. Thanks! Now what site do you use Netlify forms on if not your knife site? Also, do you know if Brad has done a video on a server-side JavaScript form?

Yes, just the html and JS (if you're using it, you don't have to for a form).
I have no experienc of cPanel so I don't know what options are there for recieving a form submission.
As long as your site is served over https then the actual transmission of the data will be secure.
However depending on the intended purpose for that data, you would most likely want to validate and sanitze whatever the user sent. For example stripping out any html markup (script tags) that they may have entered if you are intending to then show what they input in a web page.
For very simple form submissions that you get an email for I quite like using Netlify forms. You don't need any JavaScript (client or server side).
https://docs.netlify.com/forms/setup/
