# Behaviours

<!-- toc -->

# Introduction

Behaviours in Sukarix are traits that can be plugged into classes to extend their functionality. By convention,
an `init<TraitName>` method should be implemented and is called immediately after the injector creates an instance of
the class using the trait.

## Example Behaviours

1. **LogWriter**
    - **Description**: Enables the implementing class to write to the application logs.
    - **Usage**:
      ```php
      class MyClass {
          use LogWriter;
 
          public function initLogWriter() {
              // Initialization code for LogWriter
          }
      }
      ```

2. **HasF3**
    - **Description**: Injects the `$f3` property into the class, providing access to the Fat-Free Framework instance.
    - **Usage**:
      ```php
      class MyClass {
          use HasF3;
 
          public function initHasF3() {
              // Initialization code for HasF3
          }
      }
      ```

## Singleton Classes

Any singleton class inheriting from `Tailored` will have the `init<TraitName>` methods called by default. This ensures
that all behaviours are initialised properly without additional code.

## Non-Singleton Classes

If a class does not inherit from `Tailored`, it must call `Processor::instance()->initialize($this);` in the constructor
to ensure that the `init<TraitName>` methods are called.

## Example Usage

Here’s how you might use these behaviours in a class:

```php
class MyService {
    use LogWriter;
    use HasF3;

    public function __construct() {
        Processor::instance()->initialize($this); // Initialise traits manually
    }

    public function logSomething() {
        $this->log->write('Logging something!');
    }

    public function getFrameworkInstance() {
        return $this->f3;
    }
}
```

In this example, `MyService` uses both the `LogWriter` and `HasF3` traits. Since it does not extend `Tailored`, it
explicitly calls `Processor::instance()->initialize($this);` in the constructor to ensure that the traits are
initialised.
