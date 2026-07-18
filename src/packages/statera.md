# Statera: The Testing Package

<!-- toc -->

## Overview

Statera is a testing package designed to work with Sukarix, offering an alternative to PHPUnit. It supports generating
coverage reports in formats like Clover, HTML, and Text. Statera operates in both Web and CLI modes, providing flexible
testing options.

Statera is an optional, standalone package — applications can choose whether or not to use it for unit testing. The
Sukarix framework itself uses Statera for its own test suite via a `require-dev` dependency.

## Key Concepts

### TestGroup

A `TestGroup` is used to group multiple `TestScenario` instances. It helps organize related test scenarios into logical
groups, making it easier to manage and run tests collectively.

### TestScenario

A `TestScenario` represents a specific test case or scenario. It encompasses multiple `TestCase` instances that define
the individual tests to be run as part of the scenario.

### TestCase

A `TestCase` is an individual test case created inside a `TestScenario`. It extends the Fat-Free Framework's `Test`
class and provides the `expect()` method for assertions to verify the expected behavior of the code under test.

## Running Tests

Statera can run tests in both Web and CLI modes, providing detailed coverage reports.
