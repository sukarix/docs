# Configuration

Sukarix is configured via `.ini` files by default, allowing for clear and manageable settings. The configuration load
order ensures that settings can be overridden based on the environment.

## Configuration Load Order

1. **Base Configuration:**
    - `config/classes.ini`
    - `config/default.ini`

2. **Additional Configurations:**
    - Files listed in the `CONFIGS` variable, e.g., `smtp`, `notifications`, `upload`. No need to add `.ini` extension.

3. **Environment-Specific Configuration:**
    - `config/config-<environment>.ini`

4. **Routing and Access Control:**
    - `config/routes.ini`
    - `config/routes-<environment>.ini`
    - `config/access.ini` or `config/access-cli.ini` (based on environment).

```admonish info title="Dynamic reconfiguration"
Configuration changes are automatically reloaded, meaning there is no need to restart any service.
```

## Environment Overrides

Any configuration setting can be overridden in the environment-specific `.ini` file (`config/config-<environment>.ini`).
This allows for tailored configurations depending on whether the application is in development, testing, or production.

## Default Configuration Example

Here is an overview of the default settings found in `default.ini`:

- **Global Settings:**
    - `DEBUG`: Stack trace verbosity.
    - `PACKAGE`: Display name in requests.
    - `LOGS`: Custom log location.
    - `TEMP`: Temporary folder for cache and compiled templates.
    - `UPLOADS`: Directory for file uploads.
    - `UI`: Paths for user interface files.
    - `LOCALES`: Location of language dictionaries.
    - `ENCODING`: Default character encoding.
    - `LANGUAGE`: Active language.
    - `FALLBACK`: Fallback language.

- **Cache and Minification:**
    - `CACHE`: Cache configuration.
    - `SEED`: Cache seed.
    - `MINIFY_JS` and `MINIFY_CSS`: Toggle minification.

- **Timezone and Environment:**
    - `TZ`: Timezone setting.
    - `application.environment`: Current environment.
    - `log.session`: Log session queries.
    - `session.table`: Table for session storage.
    - `pagination.limit`: Default pagination limit.
    - `view.default`: Default view to render.
    - `log.keep`: Log retention period.
    - `server.host`: Host for command-line actions.
    - `error.channel`: Error notification channel.
