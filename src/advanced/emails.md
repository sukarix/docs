# Emails

<!-- toc -->

## MailSender Class

The `MailSender` class in Sukarix is used to send emails with a predefined template. The primary method for sending
emails is `send()`, which has the following signature:

```php
send($template, $vars, $to, $title, $subject): bool
```

## Method Parameters

- **$template**: The name of the email template, which must be located in the `/mail` folder.
- **$vars**: An array of variables to be used within the template.
- **$to**: The recipient's email address.
- **$title**: The title of the email.
- **$subject**: The subject line of the email.

## Usage Example

Here’s how you might use the `send()` method to send an email:

```php
/**
 * @var MailSender $mailSender
 */
$mailSender = Injector::instance()->get('mailer');
$template = 'welcome';
$vars = ['name' => 'John Doe', 'link' => 'https://example.com'];
$to = 'johndoe@example.com';
$title = 'Welcome to Our Service';
$subject = 'Getting Started with Our Service';

$mailSender->send($template, $vars, $to, $title, $subject);
```

This example sends a welcome email using the `welcome` template, passing in the recipient’s name and a link to be used
within the email body.
