# Routing and Access Control

Sukarix leverages the powerful routing and access control capabilities of the Fat-Free Framework (F3) to manage web and
CLI application routes. The configuration for routing and access control is handled through `routes.ini`
and `access.ini` for web applications, and `routes-cli.ini` and `access-cli.ini` for CLI applications.

## Routing

### Web Application Routing (`routes.ini`)

In Sukarix, routes for web applications are defined in the `routes.ini` file. Here is an example configuration with
detailed explanations:

```ini
[routes]
; default route
GET      @home        : /                          = Actions\Core\Main->execute
GET      @docs        : /docs/*                    = Actions\Core\Docs->execute
POST|PUT @set_locale  : /set-locale/@locale [ajax] = Actions\Account\SetLocale->execute
DELETE   @user_delete : /users/@id                 = Actions\Users\Delete->execute
```

### Explanation

- `GET @home      : / = Actions\Core\Main->execute`
    - **GET**: The HTTP method for the route.
    - `@home`: The route alias.
    - `:`: Separates the route identifier from the URL pattern.
    - `/`: The URL pattern for the home page.
    - `= Actions\Core\Main->execute`: The action and method that handle the request.

- `GET @docs      : /docs/*          = Actions\Core\Docs->execute`
    - **GET**: The HTTP method for the route.
    - `@docs`: The route alias.
    - `/docs/*`: The URL pattern with a wildcard to match any subpath.
    - `= Actions\Core\Docs->execute`: The action and method that handle the request.

- `POST|PUT @set_locale : /set-locale/@locale       [ajax] = Actions\Account\SetLocale->execute`
    - **POST|PUT**: The HTTP methods for the route.
    - `@set_locale`: The route alias.
    - `/set-locale/@locale`: The URL pattern with a variable (`@locale`).
    - `[ajax]`: Indicates the route should handle AJAX requests.
    - `= Actions\Account\SetLocale->execute`: The action and method that handle the request.

- `DELETE @user_delete : /users/@id = Actions\Users\Delete->execute`
    - **DELETE**: The HTTP method for the route.
    - `@user_delete`: The route alias..
    - `/users/@id`: The URL pattern with a variable (`@id`).
    - `= Actions\Users\Delete->execute`: The controller and method that handle the request.

### CLI Application Routing (`routes-cli.ini`)

In Sukarix, routes for CLI applications are defined in the `routes-cli.ini` file. Here is an example configuration with
detailed explanations:

```ini
[routes]
; route to the main task scheduler
GET @run_job        : /cli/jobs/run       [cli] = Actions\Jobs\TaskScheduler->execute
GET @logs_clean     : /cli/logs/clean     [cli] = Sukarix\Actions\Logs\Clean->execute
GET @sessions_clean : /cli/sessions/clean [cli] = Sukarix\Actions\Core\SessionsClean->execute
```

### Explanation

- `GET @run_job : /cli/jobs/run [cli] = Actions\Jobs\TaskScheduler->execute`
    - **GET**: The HTTP method for the route.
    - `@run_job`: The route alias.
    - `/cli/jobs/run`: The URL pattern for running jobs.
    - `[cli]`: Indicates the route is for CLI mode.
    - `= Actions\Jobs\TaskScheduler->execute`: The controller and method that handle the request.

- `GET @logs_clean : /cli/logs/clean [cli] = Sukarix\Actions\Logs\Clean->execute`
    - **GET**: The HTTP method for the route.
    - `@logs_clean`: The route alias.
    - `/cli/logs/clean`: The URL pattern for cleaning logs.
    - `[cli]`: Indicates the route is for CLI mode.
    - `= Sukarix\Actions\Logs\Clean->execute`: The controller and method that handle the request.

- `GET @sessions_clean : /cli/sessions/clean [cli] = Sukarix\Actions\Core\SessionsClean->execute`
    - **GET**: The HTTP method for the route.
    - `@sessions_clean`: The route alias.
    - `/cli/sessions/clean`: The URL pattern for cleaning sessions.
    - `[cli]`: Indicates the route is for CLI mode.
    - `= Sukarix\Actions\Core\SessionsClean->execute`: The controller and method that handle the request.

## Access Control

### Web Application Access Control (`access.ini`)

Sukarix uses the `access.ini` file to manage access control for web applications. The configuration defines policies and
rules for access control using the F3-Access component. Here is an example configuration with detailed explanations:

```ini
[ACCESS]
;deny all routes by default
policy = deny

[ACCESS.rules]
; Routes allowed to all type of users
deny  *      /*           = *
allow GET    @home        = *
allow GET    @docs        = admin,customer
allow        @set_locale  = *
allow DELETE @user_delete = admin
```

### Explanation

- `policy = deny`
    - Sets the default policy to deny access to all routes, this is the recommended security policy.

- `deny  *        /*                      = *`
    - Denies access to all users for all routes by default.

- `allow GET @home = *`
    - Allows access to the home route (`@home`) for all users.

- `allow GET @docs = admin,customer`
    - Allows access to the documentation route (`@docs`) only for `admin` and `customer` roles.

- `allow @set_locale = *`
    - Allows access to the set locale route (`@set_locale`) for all users.

- `allow DELETE @user_delete = admin`
    - Allows access to delete user route (`@user_delete`) only for `admin` role.

### CLI Application Access Control (`access-cli.ini`)

Sukarix uses the `access-cli.ini` file to manage access control for CLI applications. Here is an example configuration
with detailed explanations:

```ini
[ACCESS]
;deny all routes by default
policy = allow
```

### Explanation

- `policy = allow`
    - Sets the default policy to allow access to all CLI routes.

## References

For more detailed information on F3's routing and access control mechanisms, refer to the following resources:

- [Routing Engine](https://fatfreeframework.com/3.8/routing-engine)
- [F3-Access on GitHub](https://github.com/xfra35/f3-access)
