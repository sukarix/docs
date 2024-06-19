# Debugging

<!-- toc -->

## Introduction
Sukarix uses the Tracy library for debugging. Tracy offers powerful tools to help you debug your applications
efficiently.

## Basic Usage

To use Tracy, simply call the following functions in your code:

- **Dumping Variables:**
    - `dump($variable)` or `dumpe($variable)`
    - `Debugger::dump($variable)`
    - `Debugger::barDump($variable)`

For more detailed usage and advanced features, refer to the [Tracy documentation](https://tracy.nette.org/en/guide).
