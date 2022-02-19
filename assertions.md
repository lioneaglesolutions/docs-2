---
title: Assertions
description: Assertions
---

# Assertions

- [Overview](#overview)
- [Available Assertions](#available-assertions)

<a name="overview"></a>
## Overview

In addition to [Expectations](/docs/expectations), Pest also provide full access to the PHPUnit built-in Assertions.

Assertions are the methods which are actually performing the checks to ensure that your code behave as intended.

```php
it('asserts that TRUE is TRUE', function () {
    $this->assertTrue(true);
});
```

It's  important to remember that `Assertions` are methods of the `$this` variable.

This is because the closure in `test()` and `it()`  functions is always bound to a `Test Case` class.


<a name="available-assertions"></a>
## Available Assertions

<div class="collection-method-list" markdown="1">

- [`assertTrue()`](#assertTrue)
- [`assertFalse()`](#assertFalse)
- [`assertCount()`](#assertCount)
- [`assertEquals()`](#assertEquals)
- [`assertEmpty()`](#assertEmpty)
- [`assertStringContainsString()`](#assertStringContainsString)

</div>

For the full list of **Assertions**, please refer to [PHPUnit Assertions](https://phpunit.readthedocs.io/en/9.5/assertions.html) documentation.

<a name="assertTrue"></a>
### `assertTrue()`

The `assertTrue` asserts the given value is truthy.

```php
$this->assertTrue(true);
```

<a name="assertFalse"></a>
### `assertFalse()`

The `assertFalse` asserts the given value is falsy.

```php
$this->assertFalse(false);
```

<a name="assertCount"></a>
### `assertCount()`

The `assertCount` asserts the given iterable to contain the same number of items.

```php
$array = [1, 2, 3, 4];

$this->assertCount(4, $array);
```

<a name="assertEquals"></a>
### `assertEquals()`

The `assertEquals` asserts the given values are equal.

```php
$array = ['Nuno', 'Luke', 'Alex', 'Dan'];

$this->assertEquals(['Nuno', 'Luke', 'Alex', 'Dan'], $array);
```

<a name="assertEmpty"></a>
### `assertEmpty()`

The `assertEmpty` asserts the given iterable is empty.

```php
$array = [];

$this->assertEmpty($array);
```

<a name="assertStringContainsString"></a>
### `assertStringContainsString()`

The `assertStringContainsString` asserts the given string exists.

```php
    $this->assertStringContainsString('Hello', 'Hello World');
```

---

Next section: [Run a single test →](/docs/run-a-single-test)
