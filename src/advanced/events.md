# Events

<!-- toc -->

## Overview

In Sukarix, events are managed using the `Sukarix\Behaviours\HasEvents` trait. This allows any class to emit and handle events throughout the application using the Sugar Events system integrated with the PHP Fat-Free Framework.

## Key Features of Sugar Events

- Emit events from any point in your application
- Attach multiple listeners to an event with priority
- Local events on specific objects
- Send payload and context data with events
- Support for sub-events and event propagation
- Stop the event chain
- Works with F3 v3.5 and PHP v7.2+

## Example Usage

### Initializing Events
To initialize the event system and get the global `Event` instance:
```php
$events = \Sugar\Event::instance();
```

### Defining a Listener
You can define a listener (or hook) to an event using a typical F3 callstring, callback, or callable:
```php
$events->on('user_login', 'Notification->user_login');
$events->on('user_login', function() {
  // ...
});
$events->on('user_login', [$this, 'method']);
```

### Emitting an Event
To emit an event and notify all listeners:
```php
$events->emit('user_login');
```

### Sending Payload with Event
You can send additional data (payload) with an event:
```php
$events->on('user_login', function($username) {
  \Logger::log($username . ' logged in');
});
$events->emit('user_login', 'freakazoid');
```

### Multiple Listeners with Prioritization
Listeners can be prioritized; higher numbers are called first:
```php
$events->on('user_login', function($username) {
  \Logger::log($username . ' logged in');
}, 10);
$events->on('user_login', function() {
  \Flash::addMessage('You have logged in successfully');
}, 20);
$events->emit('user_login', 'freakazoid');
```

### Stopping the Event Chain
A listener can stop further listeners from being called:
```php
$events->on('user_login', function($username) {
  \Logger::log($username . ' logged in');
});
$events->on('user_login', function() {
  \Flash::addMessage('You have logged in successfully');
  return false;
}, 20);
$events->emit('user_login', 'freakazoid');
```

### Additional Event Context Data
Send additional context data with an event:
```php
$events->on('user_login', function($username, $context) {
  if ($context['lang'] == 'en')
    \Flash::addMessage('You have logged in successfully');
  elseif ($context['lang'] == 'de')
    \Flash::addMessage('Du hast dich erfolgreich angemeldet');
});
$events->emit('user_login', 'freakazoid', array('lang' => 'en'));
```

### Additional Listener Options
Listeners can have additional options:
```php
$events->on('user_login', function($username, $context, $event) {
  \Flash::addMessage('You have logged in successfully', $event['options']['type']);
}, 20, array('type' => 'success'));
```

### Filtering Payload
Listeners can modify and return the event payload:
```php
$events->on('get_total', function($basket) {
  $sum = 0;
  foreach ($basket as $prod) {
    $sum += $prod;
  }
  return $sum;
});

$products = array('a' => 2, 'b' => 8, 'c' => 15);
$sum = $events->emit('get_total', $products);
echo $sum; // 25
```

### Adding Sub-Events
Sub-events are called after the parent event:
```php
$events->on('get_total.tax', function($sum) {
  return $sum + ($sum * 0.2);
});
$events->on('get_total.shipping', function($sum) {
  return $sum + 5;
});
$sum = $events->emit('get_total', $products);
echo $sum; // 35
```

### Removing Hooks
Remove listeners for specific events:
```php
$events->off('get_total.tax');
$sum = $events->emit('get_total', $products);
echo $sum; // 30
```

### Local Events for Mappers
Support for local events on specific objects:
```php
$user = new \Model\User();
$events->watch($user)->on('update.email', '\Mailer->sendEmailActivationLink');
```