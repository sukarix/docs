# Assets

<!-- toc -->

## Introduction

Sukarix uses the `Assets` class to manage and render CSS and JavaScript files efficiently. By default, it looks for CSS
files under `public/css` and JavaScript files under `public/js`.

## Default Storage Locations

- **CSS Files**: `public/css`
- **JavaScript Files**: `public/js`
- **Minified Files**: `public/minified`

The `Assets` class automatically handles the minification of CSS and JS files and places the minified versions in
the `public/minified` directory.

```admonish tip title="Default Storage Locations"
By default, CSS files are stored in `public/css`, JavaScript files in `public/js`, and minified files in `public/minified`.
```

## Rendering Groups

Sukarix provides two rendering groups named `head` and `footer` to organize asset rendering. To render these groups in
your template, use:

```php
{{ \Sukarix\Helpers\Assets::instance()->renderGroup('footer') }}
```

## JavaScript Initialization

The `Assets` class can also call JavaScript functions and initialize them. Example:

```html

<script>
    jQuery(document).ready(function () {
        {
            { \Sukarix\Helpers\Assets::instance()
            ->
                currentJsLocale()
            }
        }
        {
            { \Sukarix\Helpers\Assets::instance()
            ->
                setUserRole()
            }
        }
        {
            { \Sukarix\Helpers\Assets::instance()
            ->
                initJsClasses()
            }
        }
    });
</script>
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

By using these functionalities, Sukarix ensures efficient management and rendering of assets, enhancing the performance
and maintainability of your web application.