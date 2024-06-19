# Understanding Fat-Free Framework

<!-- toc -->

## Introduction

Fat-Free Framework (F3) is a powerful yet lightweight PHP framework designed to help developers build dynamic web
applications quickly and efficiently. One of the core concepts in F3 is the "Hive," which is a centralized place where
the framework stores and manages all application data.

## The Hive and F3 Class

### The Hive

The Hive is a key-value store that acts as the central repository for all configuration settings, routing information,
session data, and more. It is accessible throughout the application, making it easy to manage and retrieve necessary
data from anywhere in your code.

### The F3 Class

The `F3` class is a singleton, meaning there is only one instance of this class throughout the application's lifecycle.
This singleton instance is accessible from anywhere in your application, providing a consistent and centralized way to
interact with the framework's core functionalities.

## How It Works

1. **Initialization**: When the application starts, the F3 singleton is created and the Hive is initialized with system
   variables and configurations.
2. **Routing**: F3 uses the Hive to manage routes, mapping URLs to specific functions or controllers.
3. **Session Management**: The framework uses the Hive to store and manage session data, ensuring user states are
   maintained across different requests.
4. **Configuration**: All configuration settings are stored in the Hive, making it easy to adjust and retrieve settings
   as needed.
5. **Template Rendering**: F3’s template engine uses the Hive to access variables and directives needed to render views
   dynamically.

## More Resources

To dive deeper into how Fat-Free Framework works and to explore its extensive features, refer to the following
resources:

### User Guide

For a comprehensive understanding of F3, including installation, basic usage, and advanced features, consult
the [User Guide](https://fatfreeframework.com/3.8/user-guide).

### API Reference

The [API Reference](https://fatfreeframework.com/3.8/api-reference) provides detailed information on all the classes,
methods, and properties available in F3, making it an essential resource for developers looking to utilize the framework
to its fullest potential.

### System Variables

System variables are predefined variables that F3 uses to manage various aspects of the application. For a quick
reference on these variables, check out
the [System Variables](https://fatfreeframework.com/3.8/quick-reference#SystemVariables) page.

### Template Directives

F3's template engine comes with a set of powerful directives that make it easy to render dynamic content. You can find a
list of these directives and how to use them on
the [Template Directives](https://fatfreeframework.com/3.8/quick-reference#TemplateDirectives) page.

By leveraging these resources, you can gain a thorough understanding of the Fat-Free Framework and harness its full
potential to build efficient, scalable, and robust PHP applications.