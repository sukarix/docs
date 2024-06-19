# Notifications

<!-- toc -->

## Notifier Class

The `Notifier` class in Sukarix is designed to send notifications about exceptions that occur in the application. This
class extends the `Tailored` class and uses the `HasF3` and `LogWriter` traits.

## Methods

### notifyException

The `notifyException` method is responsible for sending an exception notification. It generates a unique error ID,
creates a notification message, and sends it to a specified Zulip stream.

**Method Signature:**

```php
public function notifyException($exception): void
```

**Parameters:**

- **$exception**: An instance of `\Exception` containing the exception details to be notified.

## Usage

Here is an example of how to use the `notifyException` method:

```php
/**
 * @var Notifier $notifier
 */
$notifier = Injector::instance()->get('notifier');
try {
    // Code that may throw an exception
} catch (\Exception $e) {
    $notifier->notifyException($e);
}
```

## Configuration

Ensure the following configuration settings in your `.ini` file:

```ini
[globals]
; error notification channel "email" or "zulip"
error.channel = zulip

[NOTIFICATIONS.zulip]
token = "your-zulip-token"
mail = "your-zulip-email"
uri = "your-zulip-uri"
stream = "your-zulip-stream"
topic = "your-zulip-topic"
```
