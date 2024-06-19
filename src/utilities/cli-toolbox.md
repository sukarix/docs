# Sukarix Shell Toolbox

<!-- toc -->

## Introduction

The Sukarix Shell Toolbox is a versatile utility designed to assist with the configuration, development, monitoring, and
administration of Sukarix applications. It is installed by default in the `tools` directory of the template application
when running `vagrant up` and is currently optimized for Ubuntu 22.04.

## Functionality

### Configuration

- **--version**: Display Sukarix application version.
- **--selfinstall**: Make Sukarix runnable from anywhere.

### Development

- **--enabletests**: Enable running unit tests.
- **--test <-c> <name>**: Run unit tests with a test name. Use `-c` for coverage.
- **--fix**: Fix PHP code style.
- **--migrate**: Run database migrations.
- **--metrics**: Generate code metrics.

### Monitoring

- **--check**: Check configuration files and processes for problems.

### Administration

- **--pull**: Pull source code from its repository.
- **--deploy**: Deploy the application on a production server.
- **--build-docs**: Build the documentation.
- **--jobs**: Install the cron jobs.
- **--restart**: Restart Sukarix Stack.
- **--stop**: Stop Sukarix Stack.
- **--start**: Start Sukarix Stack.
- **--clean**: Restart and clean all log files.
- **--cleansessions**: Clean sessions from the database.
- **--status**: Display the running status of components.
- **--zip**: Zip up log files for reporting an error.

## Example Usage

```bash
# Display Sukarix application version
sukarix --version

# Enable running unit tests
sukarix --enabletests

# Run unit tests with a test name and coverage
sukarix --test -c <name>

# Check configuration files and processes for problems
sukarix --check

# Restart Sukarix Stack
sukarix --restart
```
