# Data Validation

The Sukarix framework uses the Respect Validation library for validating data. Each validator must have a name assigned
for later usage in error display. Here is an example of data validation in a PHP method:

```php
use Respect\Validation\Validator;
use Sukarix\Enum\UserRole;
use Sukarix\Validation\DataValidator;

public function save($f3, $params): void
{
    $v = new DataValidator();
    $form = $this->getDecodedBody();

    $v->verify($form['email'], Validator::email()->setName('email'));
    $v->verify($form['username'], Validator::length(4, 32)->setName('username'));
    $v->verify($form['password'], Validator::notEmpty()->setName('password'));
    $v->verify($form['role'], Validator::in(UserRole::getValues())->setName('role'));

    if ($v->allValid()) {
        // Process the validated data
    }
}
```

## Explanation

1. **Validator Setup:**
    - **Email:** `Validator::email()->setName('email')` ensures the input is a valid email format.
    - **Username:** `Validator::length(4, 32)->setName('username')` ensures the username length is between 4 and 32
      characters.
    - **Password:** `Validator::notEmpty()->setName('password')` ensures the password is not empty.
    - **Role:** `Validator::in(UserRole::getValues())->setName('role')` ensures the role is one of the predefined
      values.

2. **Validation Execution:**
    - The `verify` method of `DataValidator` is used to validate each input.
    - `allValid()` checks if all validations pass.

By using named validators, error messages can be easily displayed later, referencing the specific field that failed
validation.
