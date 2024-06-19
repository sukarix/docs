# Assets

<!-- toc -->

## Introduction

Sukarix uses the `Assets` class to manage and render CSS and JavaScript files efficiently. By default, it looks for CSS
files under `public/css` and JavaScript files under `public/js`.

## Rendering Groups

Sukarix provides two rendering groups named `head` and `footer` to organise asset rendering. To render these groups in
your template, use:

```php
{{ \Sukarix\Helpers\Assets::instance()->renderGroup('footer') }}
```

## JavaScript Initialization

The `Assets` class can also call JavaScript functions and initialize them. Example:

```html
<script>
    jQuery(document).ready(function () {
        {{ \Sukarix\Helpers\Assets::instance()->currentJsLocale() }}
        {{ \Sukarix\Helpers\Assets::instance()->setUserRole() }}
        {{ \Sukarix\Helpers\Assets::instance()->initJsClasses() }}
    });
</script>

```

```admonish tip
The `Assets` class is responsible for minifying CSS and JS files and placing them in the `public/minified` directory.
```

## Example Usage

### Adding CSS and JS Files in a View

In your action, you can add CSS and JS files like this:

```php
$this->assets->addJs('core.js');
$this->assets->addJs('core/servers.js');
$this->assets->addJs('vendors/datatables.min.js');
$this->assets->addCss('datatables.min.css');
$f3->push('init.js', 'Servers');
```

### Rendering Assets

To render assets in the `head` group:

```php
{{ \Sukarix\Helpers\Assets::instance()->renderGroup('head') }}
```

To render assets in the `footer` group:

```php
{{ \Sukarix\Helpers\Assets::instance()->renderGroup('footer') }}
```
