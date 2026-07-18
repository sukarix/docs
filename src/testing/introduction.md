# Testing with Sukarix

<!-- toc -->

The Sukarix Shell Toolbox provides several commands to facilitate testing, ensuring your application maintains high
quality and reliability. Here’s how you can leverage these testing commands:

## Enabling and Running Tests

### Enable Tests

To enable the testing environment, use:

```bash
sukarix --enabletests
```

### Running Unit Tests

Run unit tests with an optional coverage report using:

```bash
sukarix --test <-c> <name>
```

- **`-c`**: Generates a coverage report.
- **`<name>`**: Specify the name of the test to run.

## Statera Test Runner

Sukarix uses the [Statera](../packages/statera.md) test runner, which is built on top of the Fat-Free Framework's
`Test` class. Tests are organised into **groups** and **scenarios**.

### Test Structure

- **TestGroup**: A collection of test scenario classes. Extends `Sukarix\TestGroup`.
- **TestScenario**: A class containing test methods (methods starting with `test`). Extends `Sukarix\TestScenario`.
- **TestCase**: Individual test assertions. Extends `Sukarix\TestCase`.

### Registering Test Groups

Create a `Statera` class in your application's `tests/src/Core/` directory:

```php
namespace Core;

use Sukarix\Statera as SukarixStatera;
use Suite\ConfigurationTest;
use Suite\ModelTest;

class Statera extends SukarixStatera
{
    public static function registerGroups(): void
    {
        self::setGroups([
            ConfigurationTest::class,
            ModelTest::class,
        ]);
    }
}
```

### Writing a Test Suite

A test suite groups related scenarios:

```php
namespace Suite;

use Test\TestGroup;

final class ConfigurationTest extends TestGroup
{
    protected $classes = [
        \Core\ConfigurationTest::class,
    ];
}
```

### Writing a Test Scenario

```php
namespace Core;

use Test\Scenario;

final class ConfigurationTest extends Scenario
{
    protected $group = 'Framework Configuration';

    public function testDefaultConfiguration($f3)
    {
        $test = $this->newTest();
        $test->expect('UTC' === date_default_timezone_get(), 'Timezone set to UTC');
        $test->expect('UTF-8' === \ini_get('default_charset'), 'Default charset is UTF-8');

        return $test->results();
    }
}
```

### Running Tests via CLI

Create a `tools/statera.php` entry point:

```php
require_once __DIR__ . '/../vendor/autoload.php';
chdir(realpath(dirname(__DIR__) . DIRECTORY_SEPARATOR . 'app'));
$GLOBALS['test_cli'] = PHP_SAPI === 'cli';
$f3 = Base::instance();
if (!$f3->exists('GET.statera')) {
    $f3->set('GET.statera', 'all');
}
Core\Statera::registerGroups();
$app = new Application\Application();
$app->start();
```

Run with: `php tools/statera.php`

### Test Environment

The test environment is activated by setting `GET.statera` in the F3 hive. When detected, Sukarix loads
`config-test.ini` and uses the test database. The `config-test.ini` should use a separate database and
can use file-based cache to avoid Redis dependency during testing.
