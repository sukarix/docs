# Users

<!-- toc -->

## Introduction

The `User` Model class in Sukarix is the central class for managing users. It includes user status, roles, and
authentication mechanisms.

## User Status

User status can be either `active` or `inactive`, managed using the `Sukarix\Enum\UserStatus` enum.

## User Roles

Sukarix provides four default user roles:

- **visitor**: Default role, represented as `*` in the routing ACL.
- **admin**
- **customer**
- **api**: A user that can authenticate through HTTP basic authentication.

These roles impact the access control list (ACL) in the configuration and can be extended by developers as needed.

## Extending User Roles

Developers can extend user roles by adding new roles to the `UserRole` enum and updating the ACL configuration
accordingly. This allows for greater flexibility and customization to fit the needs of your application.
