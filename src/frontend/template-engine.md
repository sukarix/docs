# Template Engine

<!-- toc -->

## Introduction

The template engine in Sukarix is built on top of the Fat-Free Framework's (F3) template engine. It provides a flexible
and efficient way to render views, leveraging F3's powerful features while adding enhancements specific to Sukarix.

## Template Loading

In Sukarix, templates are loaded into views using a specific pattern. By default, the view files are stored in
the `templates` directory and have a `.phtml` extension.

### Mapping Actions to Templates

Sukarix maps actions to templates by following a convention-based approach. When an action
calls `$this->render();`, it maps to the template based on the namespace and class name, converted to snake_case.
For example:

- **Action Class:** `Actions\Core\Main`
- **Mapped Template:** `templates/actions/core/main.phtml`

```admonish info title="Default Template Extension"
The default template extension in Sukarix is `.phtml` and is automatically appended.
```

### Example Code

```php
$this->render('commons/api/response');
```

This method call will automatically render the `templates/commons/api/response.phtml` when called from any action.

### JavaScript and CSS Template Directives

Sukarix adds custom template directives for including JavaScript and CSS files in your views. These directives simplify
the process of managing assets.

- **JavaScript Directive:**
  ```html
  <js src="path/to/script.js"></js>
  ```
  This directive is used to include JavaScript files in your view.

- **CSS Directive:**
  ```html
  <css href="path/to/style.css"></css>
  ```
  This directive is used to include CSS files in your view.

```admonish tip title="File Validation"
The existence of the specified file is validated when the directive attempts to load it. If the file is not found,
an exception will be thrown. This ensures that developers can handle missing files during the development phase
before deploying to production.
```

## F3 Template Directives

F3 provides a set of powerful template directives that make it easy to render dynamic content, control flow, and manage
template inheritance. Some of the key directives include:

- **Include Directive:**
  ```html
  <include href="partial.phtml" />
  ```
  This directive includes another template file within the current template.

- **Repeat Directive:**
  ```html
  <repeat group="{{ @items }}" value="{{ @item }}">
    <!-- Content to repeat -->
  </repeat>
  ```
  This directive repeats a block of content for each item in a collection.

- **Conditional Directive:**
  ```html
  <check if="{{ @condition }}">
    <!-- Content to show if condition is true -->
  </check>
  ```
  This directive conditionally renders content based on a boolean expression.

- **Set Directive:**
  ```html
  <set name="variable" value="value" />
  ```
  This directive sets a variable to a specified value within the template.

- **Session Directive:**
  ```html
  <session name="variable" />
  ```
  This directive retrieves a value from the session.

- **Cookie Directive:**
  ```html
  <cookie name="variable" />
  ```
  This directive retrieves a value from cookies.

- **Locale Directive:**
  ```html
  <locale name="variable" />
  ```
  This directive retrieves a localized value.

## Additional Resources

For more detailed information on F3's template engine and directives, you can refer to
the [F3 Views and Templates Documentation](https://fatfreeframework.com/3.8/views-and-templates).
