# Application Lifecycle

The entry point for a Sukarix application is `public/index.php`.

This is where initial detection happens to determine if unit tests need to be run in the browser, a process that will be
covered in detail later.

Once the Application is instantiated, the following steps occur:

## 1. Detect if the Application is Running in CLI Mode

The application first checks if it is being executed from the command line (CLI) or through a web server. This allows
for conditional loading of CLI-specific configurations and behaviors.

## 2. Create an Instance of the Fat-Free Framework (F3) Singleton Class

An instance of the F3 singleton class is created. This instance acts as the central hub for managing application
configuration, routing, and other core functionalities.

## 3. Set Up PHP Variables

The application sets up necessary PHP variables, including error reporting levels, timezone settings, and memory limits,
to ensure a consistent execution environment. Up to the developer to override it.

## 4. Automatically Detect the Application Environment

The application detects the current environment (`test`, `development`, or `production`). This setting can be overridden
if needed, and it dictates how the application behaves, including error reporting and debugging levels.

## 5. Load the Configuration Files

The application loads its configuration settings from `ini` configuration files. These files define various parameters
and settings required for the application's operation.

## 6. Set Up Logging

Logging is set up to capture and record important events, errors, and performance metrics. This is crucial for
monitoring the application and diagnosing issues.

## 7. Add the Global Exception Handler

A global exception handler is added to catch and manage any unhandled exceptions, ensuring that errors are logged and
appropriate responses are provided without crashing the application.

## 8. Connect to the Database

The application establishes a connection to the database using the settings defined in the configuration files. This
connection is essential for data storage and retrieval.

## 9. Prepare the Session

The session handler is initialized to manage user sessions, including creating, storing, and terminating sessions. This
is important for maintaining user state across requests.

## 10. Load Additional Application Settings

Additional settings and configurations specific to the application are loaded. These can include custom parameters,
feature toggles, and other application-specific settings.

## 11. Load Additional CLI Configuration if CLI Mode is Detected

If the application is running in CLI mode, additional configurations specific to the command-line environment are
loaded. This ensures that CLI commands have the necessary settings and resources.

## 12. Load Routing and Access Control Lists (ACL)

The routing configuration and ACLs are loaded to define how incoming requests are handled and to enforce access
permissions. This ensures that routes are correctly mapped to actions and that users have appropriate access rights.

## 13. Execute the Start Function

The `start` function of the application is executed, which in turn calls the F3 `run` function. This kicks off the
application, allowing it to handle incoming requests or execute CLI commands.

## 14. Log Performance Metrics and Finish

Finally, the application logs performance metrics for the entire lifecycle process. This includes timing information and
resource usage statistics, which are useful for performance monitoring and optimization.

This comprehensive sequence ensures that the Sukarix application is thoroughly initialized, configured, and prepared to
handle both web requests and CLI commands efficiently and reliably.
