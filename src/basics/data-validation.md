# Data Validation

<!-- toc -->

## Human-readable data validation syntax

Form validation is a crucial part of building robust web applications. Sukarix simplifies this process by allowing you
to declare your validation rules in an easy-to-read configuration file. This page provides an overview of how to use
Sukarix's data validation capabilities.

## Configuration

Validation rules are declared in an INI file. Here's an example:

```ini
[CONSTRAINTS.users.edit]
email = email
username = length:4,32
role = in:Enum\UserRole
status = in:Sukarix\Enum\UserStatus
```

## Using the Validator

To validate data, use the `Constraints` class in your controller or model. Below are various examples demonstrating
different usages.

### Example: Basic Usage

```php
public function save($f3, $params): void
{
    $form = $this->getDecodedBody();

    Constraints::instance()->verify($form, 'users.edit');

    // Process the validated data
}
```

### Example: Multiple Rulesets

You can validate against multiple rulesets by separating them with a pipe (`|`).

```php
public function save($f3, $params): void
{
    $form = $this->getDecodedBody();

    Constraints::instance()->verify($form, 'settings.save.default|users.edit');

    // Process the validated data
}
```

You can also pass ruleset names as an array.

```php
public function save($f3, $params): void
{
    $form = $this->getDecodedBody();

    Constraints::instance()->verify($form, ['settings.save.default', 'users.edit']);

    // Process the validated data
}
```

### Example: Individual Checks

You can also perform individual checks using the `check` method.

```php
$filePath = '/path/to/file.css';
Constraints::instance()->check($this->f3->get('ROOT') . $filePath, 'file', true, 'css_file');
```

## How Validation Works

1. **Audit Class**:
    - If available, validation rules are first checked in the `Audit` class.

2. **Constraints Class**:
    - If the rule is not found in the `Audit` class, it falls back to the `Constraints` class.

3. **Custom Validator**:
    - If the rule is not found in the `Constraints` class, it checks for a user-defined validator class specified in
      the `VALIDATOR` configuration property.

```admonish warning title="Validation rule names are case insensitive"
Validator names are case insensitive, meaning `notempty`, `notEmpty`, `NotEmpty`, and `NOTEMPTY` are treated the same.
```

## Available Validation Rules

Here is a list of available validation rules that you can use in your INI configuration file or directly in your code:

- `email`: Validates that the input is a valid email address.
- `length:min,max`: Validates that the input length is between `min` and `max`.
- `in:Enum\ClassName`: Validates that the input is one of the values in the specified enumeration.
- `notEmpty`: Validates that the input is not empty.
- `file`: Validates that the input is a valid file path.

### Example: Custom Validator

You can define custom validation rules in your own validator class and configure Sukarix to use it.

```php
class CustomValidator
{
    public static function isCustom($value)
    {
        // Custom validation logic
        return $value === 'custom';
    }
}

// Usage
$customRules = [
    'custom_field' => 'custom'
];

Constraints::instance()->verifyRules($form, $customRules, true);
```

### Error Handling

When validation fails, the `verify` method throws an exception if the `throwOnFail` parameter is set to `true`.

```php
try {
    Constraints::instance()->verify($form, 'users.edit', true);
} catch (\RuntimeException $e) {
    echo "Validation failed: " . $e->getMessage();
}
```

To get all validation errors, use the `getErrors` method.

```php
$errors = Constraints::instance()->getErrors();
print_r($errors);
```

### Combining Validators

You can combine multiple validation rules using the pipe (`|`) separator.

```ini
[CONSTRAINTS.users.edit]
email = email
username = length:4,32|notEmpty
role = in:Enum\UserRole|notEmpty
status = in:Sukarix\Enum\UserStatus|notEmpty
```

```php
public function save($f3, $params): void
{
    $form = $this->getDecodedBody();

    Constraints::instance()->verify($form, 'users.edit');

    // Process the validated data
}
```
