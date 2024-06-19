# Testing with Sukarix

<!-- toc -->

The Sukarix Shell Toolbox provides several commands to facilitate testing, ensuring your application maintains high
quality and reliability. Here’s how you can leverage these testing commands:

## Enabling and Running Tests

### Enable Tests

To enable the testing environment, use:

```bash
sukarix --enabletests
```

### Running Unit Tests

Run unit tests with an optional coverage report using:

```bash
sukarix --test <-c> <name>
```

- **`-c`**: Generates a coverage report.
- **`<name>`**: Specify the name of the test to run.
