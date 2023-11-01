# Repo to Submit a Form to a Mail Server

> _Or to wimp out and use a Netlify form on my profile_!

## Replies from Discord

Do you mean on the client side of things or the server side of things?

In the client you would either use the html default submit where by the form submits to whatever you have in the action attribute, via the http method in the method attribute.

- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form
- https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data

It's fairly common though to disable the default behavior of a form submit and handle it yourself in JavaScript. Though more modern frameworks seem to be encouraging going back to the default html submit.

On the server side of things you can use any language you like to accept the form data and do something with it.

Yes, just the html and JS (if you're using it, you don't have to for a form).

I have no experienc of cPanel so I don't know what options are there for recieving a form submission.

As long as your site is served over https then the actual transmission of the data will be secure.

However depending on the intended purpose for that data, you would most likely want to validate and sanitze whatever the user sent. For example stripping out any html markup (script tags) that they may have entered if you are intending to then show what they input in a web page.

For very simple form submissions that you get an email for I quite like using Netlify forms. You don't need any JavaScript (client or server side).

- https://docs.netlify.com/forms/setup/

One thing that is nice to do with forms is to also set up a honey pot form/input. This is a form or input fields (with fake submit) that are hidden visually in your site but appear before your true form.

This helps prevents bots spamming your form as they usually target the first form in the page, which obviously in the honey pot form won't do anything meaningful.

There is a limit if you're using the free service, I never personally hit it from equiries from my knife making business but you can pay for more.

Yeah just checked it's 100 per site per month on the free tier.
