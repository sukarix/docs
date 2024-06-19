# Statera: The Testing Package

<!-- toc -->

## Overview

Statera is a testing package designed to work with Sukarix, offering an alternative to PHPUnit. It supports generating
coverage reports in formats like Clover, HTML, and Text. Statera operates in both Web and CLI modes, providing flexible
testing options.

## Key Concepts

### TestGroup

A `TestGroup` is used to group multiple `TestScenario` instances. It helps organize related test scenarios into logical
groups, making it easier to manage and run tests collectively.

### TestScenario

A `TestScenario` represents a specific test case or scenario. It encompasses multiple `UnitTest` instances that define
the individual tests to be run as part of the scenario.

### UnitTest

A `UnitTest` is an individual test case created inside a `TestScenario`. It contains the actual test logic and
assertions to verify the expected behavior of the code under test.

## Running Tests

Statera can run tests in both Web and CLI modes, providing detailed coverage reports.
~~~~