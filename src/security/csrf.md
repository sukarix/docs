# CSRF Protection

<!-- toc -->

## Overview

Sukarix provides built-in CSRF (Cross-Site Request Forgery) protection mechanisms to ensure the security of your forms
and requests.

## Generating CSRF Token

To include a hidden CSRF token input in your forms, use the `<csrf/>` template directive. This directive generates a
hidden input field with the CSRF token, ensuring that each form submission includes a valid token.

```html
form method="post" action="{{ @ALIASES.login }}">
    <csrf/>
    <!-- other form fields -->
    <input type="submit" value="Submit">
</form>
```

## Validating CSRF Token

To validate the CSRF token, use the `validateToken()` method from the session. This method checks whether the token
submitted with the form matches the token stored in the user's session.

### Example Usage

```php
if ($this->session->validateToken($submittedToken)) {
    // Token is valid, proceed with form processing
} else {
    // Token is invalid, handle the error
}
```
