# Dependency Injection

<!-- toc -->

## Overview

Dependency Injection in Sukarix is facilitated through the singleton class `Injector::instance()->get('access')`. This
method allows for easy and efficient management of dependencies within your application.

## Example Usage

In this example, `access` is the default ACL Middleware tied to `f3-access`:

```php
$access = Injector::instance()->get('access');
```

## Configuration & default dependencies

These default classes can be easily changed or overridden by updating the `classes.ini` file. The default configuration
is in the table below:

| Key        | Class                         |
|------------|-------------------------------|
| `mailer`   | Sukarix\Mail\MailSender       |
| `notifier` | Sukarix\Notification\Notifier |
| `session`  | Sukarix\Core\Session          |
| `i18n`     | Sukarix\Helpers\I18n          |
| `assets`   | Sukarix\Helpers\Assets        |
| `access`   | \Access                       |
| `events`   | Sugar\Event                   |
| `template` | \Template                     |
| `html`     | Sukarix\Helpers\HTML          |

## Creating Injectable Singletons

For classes that should be singletons with behaviours, they must extend the `Sukarix\Core\Tailored` class. This ensures
the framework can automatically integrate their behaviours. More details on these behaviors can be found in the
Behaviours section of the documentation.

```admonish info title="Instantiating an injectable singleton object"
There is no need to manually instantiate the injected object, Sukarix will do it for you.
```

## Storing DI Classes

The F3 `\Registry` class is used to store these dependency-injected classes, ensuring they are easily accessible
throughout your application.
