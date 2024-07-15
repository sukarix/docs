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

Additionally, the `Injector` can find an object from its class directly:

```php
$multiLang = Injector::instance()->get(\Multilang::class);
```

## Configuration & Default Dependencies

These default classes can be easily changed or overridden by updating the `classes.ini` file. The default configuration
is in the table below:

| Key              | Class                         |
|------------------|-------------------------------|
| `mailer`         | Sukarix\Mail\MailSender       |
| `notifier`       | Sukarix\Notification\Notifier |
| `session`        | Sukarix\Core\Session          |
| `i18n`           | Sukarix\Helpers\I18n          |
| `assets`         | Sukarix\Helpers\Assets        |
| `access`         | \Access                       |
| `events`         | Sugar\Event                   |
| `template`       | \Template                     |
| `html`           | Sukarix\Helpers\HTML          |
| `multi_language` | \Multilang                    |
| `receiver`       | Sukarix\Helpers\Receiver      |

## Creating Injectable Singletons

For classes that should be singletons with behaviors, they must extend the `Sukarix\Core\Tailored` class. This ensures
the framework can automatically integrate their behaviors. More details on these behaviors can be found in the Behaviors
section of the documentation.

```admonish info title="Instantiating an injectable singleton object"
There is no need to manually instantiate the injected object, Sukarix will do it for you.
```

## Storing DI Classes

The F3 `\Registry` class is used to store these dependency-injected classes, ensuring they are easily accessible
throughout your application. However, it is recommended to use the `Injector` class that already wraps this
functionality, as it provides additional features and should be preferred over direct usage of `\Registry`.
