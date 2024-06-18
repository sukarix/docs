# Logging

The framework uses Monolog by default for logging. To enable logging, use the `LogWriter` behavior trait in your class.
If the class does not extend the `Tailored` singleton class, ensure to call the `initLogWriter` method in the
constructor.

## Logging Naming Conventions

Logs follow these naming patterns:

- **Application Logs:** `app-yyyy-mm-dd.log`
- **Application Error Logs:** `app-error-yyyy-mm-dd.log`
- **CLI Logs:** `cli-yyyy-mm-dd.log`
- **CLI Error Logs:** `cli-error-yyyy-mm-dd.log`
- **Exception Logs:** `exception.log`

## Log Rotation

Logs are kept for 14 days by default, configurable via the `log.keep` setting (an integer in days).
The `Sukarix\Actions\Action\Clean` action is responsible for rotating and cleaning logs.
