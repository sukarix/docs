# JavaScript

<!-- toc -->

## Introduction

The default Sukarix application template includes `locale.js`, which downloads the session locale using AJAX and
provides functions to access localized strings. Additionally, `Common.userRole` is accessible via JavaScript and is set
from the session.

## locale.js

`locale.js` handles the localization of strings in your application. It downloads the session locale and provides easy
access to localized strings. This ensures that your application can support multiple languages and dynamically switch
between them based on the user's session.

## Common.userRole

The `Common.userRole` variable is set from the session and is accessible via JavaScript. This allows you to manage user
roles on the client side and adjust your application's behavior based on the user's role.

## Minimalistic Implementation

Sukarix provides this minimalistic implementation, giving developers the flexibility to use modern frontend frameworks
as needed. You can integrate libraries and frameworks such as React, Vue, or Angular to build more complex and
interactive user interfaces.

## Example Usage

### Accessing Localized Strings

```javascript
var welcomeMessage = Locale.msg('welcome');
console.log(welcomeMessage);
```

### Using Common.userRole

```javascript
if (Common.userRole === 'admin') {
    console.log('User is an admin');
} else {
    console.log('User is not an admin');
}
```
