# Session

<!-- toc -->

## Session Management

Session handler documentation can be found [here](https://fatfreeframework.com/3.8/session).

By default, sessions are stored in the database but can be configured to use the cache system. This allows session data
to be debuggable in non-production environments, while in production, storing sessions in cache enhances performance.

## Session Functions

The session management system includes the following functions:

- **authorizeUser:** Authorizes a user and initiates their session.
- **revokeUser:** Revokes a user's session and logs them out.
- **getRole:** Retrieves the role of the current user.
- **isRole:** Checks if the current user has a specific role.
