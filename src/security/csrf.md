# CSRF Protection

<!-- toc -->

## Overview

Sukarix provides built-in CSRF (Cross-Site Request Forgery) protection mechanisms to ensure the security of your forms
and requests. By enabling CSRF protection, you can safeguard your application from unauthorized actions performed by
malicious users.

## Configuration

CSRF protection is configured in the `config.ini` file. The following default settings enable CSRF protection and set
the token expiry time:

```ini
[SECURITY]
csrf.enabled = true
csrf.expiry = 3600
```

- **csrf.enabled**: Enables or disables CSRF protection.
- **csrf.expiry**: Sets the expiry time for the CSRF token in seconds (default is 3600 seconds or 1 hour).

```admonish info title="CSRF Token Expiry"
The CSRF token has an expiry time configured in the `config.ini` file. If the token has expired, it will be considered invalid. Ensure your application handles token expiry by prompting the user to refresh the form or session.
```

## Generating CSRF Token

To include a hidden CSRF token input in your forms, use the `<csrf/>` template directive. This directive generates a
hidden input field with the CSRF token, ensuring that each form submission includes a valid token.

### Example Usage

```html
<form method="post" action="{{ @ALIASES.login }}">
    <csrf/>
    <!-- other form fields -->
    <input type="submit" value="Submit">
</form>
```

This example shows how to include a CSRF token in a form. The `<csrf/>` directive automatically generates and includes
the token.

## Validating CSRF Token

To validate the CSRF token, use the `isCsrfValid()` method from the session. This method checks whether the token
submitted with the form matches the token stored in the user's session.

### Example Usage

```php
if ($this->session->isCsrfValid()) {
    // Token is valid, proceed with form processing
} else {
    // Token is invalid, handle the error
}
```

This code snippet shows how to validate the CSRF token when processing a form submission. If the token is valid, you can
proceed with the form processing. If the token is invalid, handle the error appropriately.

```admonish tip title="Single CSRF Token Per Session"
Like many other frameworks, Sukarix handles a single CSRF token per session. This means that each user's session is associated with one unique CSRF token, which is used to validate all form submissions within that session.
```
