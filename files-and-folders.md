---
title: Files & Folders
description: Test suit structure
---

# Files & Folders

## Introduction

If you are coming from PHPUnit, you will notice that the files and folder structure is almost identical.

After sucessfully installing Pest, you will have the following files and folder structure:

```none
├── 📂 tests
│   ├── 📂 Unit
│   │   └── ExampleTest.php
│   └── 📂 Feature
│   │   └── ExampleTest.php
│   └── TestCase.php
│   └── Pest.php
├── phpunit.xml
```

## Folder "tests"

This is where everything test related lives. You can find here files for PHPUnit and Pest configuration and test logic.

### Folders "Unit" and "Feature"

These two folders contain your Test files with all the test logic.

Conventionally, each test file is named with the suffix "…**Test.php"** (e.g, UserTest.php). The sufix can be configured in the file  `phpunit.xml`.

#### Unit tests

Unit tests are designed to test a small portion of your code in isolation. Unit tests should not depend on any resources, such as a database access.

#### Feature tests

In the other hand, Feature tests are designed to test your code units interacting with each other as a group. These tests can and should make use of resources like database access, for example.

### TestCase.php

The [TestCase](/docs/underlying-test-case) file is responsible for starting your application, creating an environment for your tests to run.

### Pest.php

This is the entry point of Pest PHP. By default, Pest autoload this file and here can bond a [Test Case](docs/underlying-test-case), create [Custom Helpers](docs/helpers) and extend [Expectations](/docs/custom-expectations).

## phpunit.xml

The file `phpunit.xml` is loaded automatically and it contains environment configuration for your tests.

It is essentially your test's `.env()` file. Here you can modify settings such as your database credentials, queue or mail configuration.

---

**Next**: Learn the syntax of a [`Pest Test` →](/docs/pest-tests)
