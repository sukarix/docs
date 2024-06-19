# Error Handling

<!-- toc -->

## Introduction

In Sukarix, error handling is managed by a global error handler that can be overridden in the `Application` class. The
default implementation uses `Tracy\Debugger` for managing errors and handling fatal exceptions. The global exception
handling is only active in the production environment.

## Default Implementation

The `Application` class includes a protected method `handleException()` that sets up the error handler. The default
implementation is capable of sending email or Zulip notifications based on the configuration of `error.channel`. Before
sending the email, it stores the exception stack trace in HTML format. It's important to note that the error stack might
contain sensitive information, so sending it by default is not enabled.

Additionally, notifications for the same exception hash are sent only once every 24 hours.

## Customizing Error Handling

To customize the error handling, you can override the `handleException()` method in your `Application` class:

```php
protected function handleException(): void {
    if (Debugger::$productionMode) {
        Debugger::$onFatalError[] = function($exception) {
            // Custom fatal error handling logic
        };
    }
}
```
