# Authorisation System

<!-- toc -->

## Introduction

The authorisation system in Sukarix is managed through the `f3-access` library. The documentation for `f3-access` is
available in the [f3-access repository](https://github.com/xfra35/f3-access).

## Access Instance

The access instance is available in classes using the `HasAccess` behaviour trait. This trait integrates the access
control mechanisms provided by `f3-access` into your Sukarix application.

## Default Authorization System

The `beforeroute` method of the `Action` class implements the default authorization system. This method checks the
user's permissions before allowing access to specific routes or actions.

## Security Best Practices

By default, everything is set to `deny` in the template application for security reasons. This default setting ensures
that only explicitly allowed actions are accessible, enhancing the overall security of your application.

```admonish danger title="Recommended Authorization Policy"
For security, it is recommended to maintain the default `deny` setting and explicitly allow access to necessary
routes and actions.
```
