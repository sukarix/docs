# Features

<!-- toc -->

## Introduction

Sukarix builds upon the robust and lightweight foundation of the Fat-Free Framework (F3), a micro-framework known for
its efficiency and simplicity. We have retained the best features of F3 where it excels, ensuring a solid, stable, and
high-performance core. At the same time, we have integrated or replaced certain components with more powerful and
feature-rich libraries to make Sukarix enterprise-ready. These enhancements provide additional functionality, improve
scalability, and offer a more comprehensive development experience for building complex, modern PHP applications.

## Feature List

| Feature Name                               | F3 Native | Sukarix Replacement (Library) |
|--------------------------------------------|-----------|-------------------------------|
| Fast and clean template engine             | Yes       | -                             |
| Unit testing toolkit (Web UI & CLI)        | Yes       | PHPUnit Code Coverage         |
| Database-managed sessions                  | Yes       | -                             |
| Markdown-to-HTML converter                 | Yes       | -                             |
| Atom/RSS feed reader                       | Yes       | -                             |
| Image processor                            | Yes       | -                             |
| Geodata handler                            | Yes       | -                             |
| On-the-fly Javascript/CSS compressor       | Yes       | Matthias Mullie Minify        |
| OpenID (consumer)                          | Yes       | -                             |
| Custom logger                              | Yes       | Monolog                       |
| Basket/Shopping cart                       | Yes       | -                             |
| Pingback server/consumer                   | Yes       | -                             |
| Unicode-aware string functions             | Yes       | -                             |
| SMTP over SSL/TLS                          | Yes       | F3 Mailer                     |
| Tools for communicating with other servers | Yes       | -                             |
| Data Validation                            | Yes       | Respect Validation            |
| ORM                                        | -         | F3 Cortex                     |
| ACL                                        | -         | F3 Access                     |
| Event Dispatching                          | -         | F3 Events                     |
| Messages to chat platforms                 | -         | Guanguans Notify              |
| Database Migrations                        | -         | Phinx                         |
| Debugging & Global Event Catching          | -         | Tracy                         |
| Cron job scheduler                         | -         | peppeocchi/php-cron-scheduler |
| Dependency Injection                       | -         | Sukarix                       |
| Inversion of Control                       | -         | Sukarix                       |
| Bash tool                                  | -         | Sukarix (coming...)           |

### Description of Features

- **Fast and clean template engine**: Provides a lightweight and efficient templating system that allows for easy
  creation of dynamic web pages.
- **Unit testing toolkit (Web UI & CLI)**: Integrated tools for unit testing both web interfaces and command-line
  interfaces, ensuring comprehensive code coverage and reliability.
- **Database-managed sessions**: Manages user sessions through the database, enhancing security and scalability.
- **Markdown-to-HTML converter**: Converts Markdown syntax into HTML, facilitating easy content creation and management.
- **Atom/RSS feed reader**: Parses and reads Atom and RSS feeds, allowing for integration with external content sources.
- **Image processor**: Handles image manipulation tasks such as resizing, cropping, and format conversion.
- **Geodata handler**: Manages geographical data, enabling features such as location-based services and mapping.
- **On-the-fly Javascript/CSS compressor**: Minifies JavaScript and CSS files on the fly to improve page load times and
  performance.
- **OpenID (consumer)**: Supports OpenID authentication, allowing users to log in using their existing OpenID accounts.
- **Custom logger**: Enhanced logging capabilities using Monolog, providing flexible and powerful logging options.
- **Basket/Shopping cart**: Manages e-commerce functionalities such as shopping carts and order processing.
- **Pingback server/consumer**: Implements pingback functionality for communication between blogs and websites.
- **Unicode-aware string functions**: Handles string operations with full Unicode support, ensuring compatibility with
  multiple languages and character sets.
- **SMTP over SSL/TLS**: Securely sends emails using SMTP with SSL/TLS encryption, enhancing email security.
- **Tools for communicating with other servers**: Provides utilities for making HTTP requests and interacting with
  external APIs.
- **Data Validation**: Validates input data using Respect Validation, ensuring that data conforms to specified rules and
  constraints before processing.
- **ORM**: Uses F3 Cortex for object-relational mapping, simplifying database interactions.
- **ACL**: Manages access control using F3 Access, enforcing permissions and roles.
- **Event Dispatching**: Handles event management using F3 Events, allowing for flexible and decoupled event-driven
  architecture.
- **Messages to chat platforms**: Sends notifications to chat platforms like Zulip and Slack using Guanguans Notify.
- **Database Migrations**: Manages database schema changes using Phinx, ensuring smooth and controlled migrations.
- **Debugging & Global Event Catching**: Utilizes Tracy for debugging and catching global events, providing detailed
  error reports and insights.
- **Cron job scheduler**: Schedules and manages cron jobs using peppeocchi/php-cron-scheduler, automating repetitive
  tasks.
- **Dependency Injection**: Facilitates dependency management using Sukarix's own DI container, promoting loose coupling
  and testability.
- **Inversion of Control**: Implements IoC using Sukarix, ensuring modular and maintainable code.
- **Bash tool**: A forthcoming feature in Sukarix for creating and managing bash scripts, enhancing CLI capabilities.
 