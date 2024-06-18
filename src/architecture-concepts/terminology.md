# Terminology

## Hive

A central place where Fat-Free Framework (F3) stores and manages application data, including configuration settings,
routing, and session information. The Hive acts as a global registry, making data accessible throughout the application.

## Configuration File

Refers to any `ini` configuration file used to define application settings and dependencies. This file helps in managing
the application's configuration in a structured and centralized manner.

## Action

Refers to action-wise micro-controllers inspired by ForkCMS. These are responsible for handling specific tasks or
requests within the application, typically mapped to routes and executed to perform a particular function.

## Bootstrapping

The application initialisation phase where the framework, akin to the kernel in other frameworks, loads configurations,
sets up the environment, and prepares the application for handling requests.

## Environment

The automatically detected application environment, which can be `test`, `development`, or `production`. This setting
can be overridden to suit specific needs during development or deployment.

## Injector

A component responsible for injecting and initializing Inversion of Control (IoC) classes defined in the configuration
file. It manages dependencies and ensures that required services are available throughout the application.

## Processor

A component responsible for applying behaviors of traits to classes. It ensures that specific functionalities or
attributes are consistently applied across relevant classes.

## Session

The class responsible for managing user sessions, including session creation, data storage, and session termination.

## ErrorChannel

The global exception handling component used to manage and route errors. It supports multiple channels like Zulip and
email for notifying about exceptions.

## User Role

Defines the various roles within the application, such as `visitor`, `admin`, `customer`, or `api` user. These roles
determine the level of access and permissions for different parts of the application.

## Assets

The class responsible for injecting JavaScript and CSS assets into views, either from the action or directly within the
view itself.

## View

Refers to the F3 template view files, typically ending with `.phtml`, used to render the user interface.

## Flash

Contains notifications to be displayed in the frontend. It manages temporary messages that inform users about the status
of their actions.

## I18n

The class that contains different types of messages depending on the localization settings. It supports
internationalization and helps manage translations.

## MailSender

The class responsible for sending emails within the application. It handles email composition, configuration, and
delivery.

## Model

A Cortex class with additional behaviors, used to represent and manage the application's data layer. It includes ORM
features for interacting with the database.

## Notifier

The component responsible for sending notifications to third parties, such as Zulip, Slack, or email, ensuring that
important events are communicated effectively.

## DataValidator

The class responsible for validating data inputs within the application. It ensures that data conforms to specified
rules and constraints before processing.
