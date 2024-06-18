# Framework Variables

## Fat Free Framework Variables

Detailed information on Fat-Free Framework variables can be
found [here](https://fatfreeframework.com/3.8/framework-variables).

## Globals

Global variables and their usage are explained [here](https://fatfreeframework.com/3.8/framework-variables#Globals).

## Naming Rules

Naming conventions are outlined [here](https://fatfreeframework.com/3.8/framework-variables#Globals). Sukarix follows
these rules, using capital letters when possible. If F3 extensions deviate from this rule, they are used as is.

# Sukarix Framework Variables

Fat-Free Framework system variables are listed [here](https://fatfreeframework.com/3.8/quick-reference#SystemVariables).

Example Sukarix framework variables:

### MINIFY_JS

`boolean` &nbsp; &nbsp; **Default:** `TRUE` in production configuration

Turns JavaScript minification on or off. Should be environment dependant.
~~~~
### MINIFY_CSS

`boolean` &nbsp; &nbsp; **Default in template application:** `TRUE` in production configuration

Turns CSS minification on or off. Should be environment dependant.

### CONFIGS

`string` &nbsp; &nbsp; **Default in template application:** `smtp,notifications,upload`

List of configuration files to load.

### application.environment

`string`

Sets the application environment (e.g., development, testing).

```admonish abstract title="<u>Sukarix Convention:</u> Environment auto-detection"
If the server hostname ends with `.test` the `application.environment` variable will automatically be set
to `development`. 
```

### view.default

`string` &nbsp; &nbsp; **Default in template application:** `website`

Default view to render.

### log.keep

`integer` &nbsp; &nbsp; **Default in template application:** `14`

Days to keep logs before cleanup.

### server.host

`string` &nbsp; &nbsp; **Default:** `NULL`

Server host for command line actions.

### error.channel

`string` &nbsp; &nbsp; **Default:** `NULL`

Error notification channel ("email" or "zulip").
