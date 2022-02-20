---
title: Run a single test
description: Running a single test with only()
---

# Run a single test

Sometimes you might want to run a single test to debug a problem instead of running the entire Test Suit.

For these cases, Pest provides the method `only()`. This method can be chained to `test()` and `it()` functions.

For example:

```php
<?php

// Test I want to debug
test('TRUE is TRUE', function () {
    expect(false)->toBeTrue();
})->only();

// The 2 tests below will not run...

test('FALSE is FALSE', function () {
    expect(false)->toBeFalse();
});

it('contains hello', function () {
    expect('Hello World')->toContain('Hello');
});
```

> **NOTE:** Please be aware that `only()` will be ignored if the `--ci` option is added to the cli command.

Read more about: [Skipping Tests →](/docs/skipping-tests)
