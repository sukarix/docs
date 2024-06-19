# Authentication

<!-- toc -->

## Introduction

Sukarix provides a straightforward method for authenticating users using models and session management. Below are
examples and explanations on how to implement authentication and handle user verification in Sukarix.

## Authenticating a User

To authenticate a user, retrieve the user model by their email, check their status and role, and verify their password.
If all conditions are met, authorize the user in the session.

### Example Code

```php
$user = new UserModel();
$user = $user->getByEmail($email);
if (UserStatus::ACTIVE === $user->status && UserRole::API !== $user->role && $user->verifyPassword($password)) {
    $this->session->authorizeUser($user);
}
```

## Authorizing a User

The `authorizeUser` method is used to authorize a user in the session. This method sets the necessary session variables
to mark the user as authenticated.

## Verifying API Users

In the `Action` class, the `isApiUserVerified()` method checks if a user has authenticated via the HTTP Basic Auth
header. This is useful for API endpoints where HTTP Basic Authentication is preferred.

### Example Usage

```php
if ($this->isApiUserVerified()) {
    // API user is authenticated
}
```
