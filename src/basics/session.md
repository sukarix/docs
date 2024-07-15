# Session

<!-- toc -->

## Session Management

Session handler documentation can be found [here](https://fatfreeframework.com/3.8/session).

By default, sessions are stored in the database but can be configured to use the cache system. This allows session data
to be debuggable in non-production environments, while in production, storing sessions in cache enhances performance.

```admonish danger title="Issues with storing sessions in transactional database"
Storing a session in the database can be problematic when using transactions, as the database connection is tied
to that session. Rolling back or failing a transaction may result in failed updates to the session data.
It's important to carefully consider this when designing your application's session management strategy.
```

## Session Functions

The session management system includes the following functions:

- **authorizeUser:** Authorizes a user and initiates their session.
- **revokeUser:** Revokes a user's session and logs them out.
- **getRole:** Retrieves the role of the current user.
- **isRole:** Checks if the current user has a specific role.
