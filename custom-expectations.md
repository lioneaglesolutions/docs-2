---
title: Cusom Expectations
description: Custom Expectations
---

# Custom Expectations

- [Overview](#overview)


<a name="overview"></a>
## Overview

You can use `expect()->extend()` to add your own expectations to Pest. For example, let's say that you're testing a number utility library and you're frequently asserting that numbers appear within particular ranges of other numbers. You could abstract that into a `toBeWithinRange` expectation.

```php
expect()->extend('toBeWithinRange', function ($min, $max) {
    return $this->toBeGreaterThanOrEqual($min)
                ->toBeLessThanOrEqual($max);
});

test('numeric ranges', function () {
    expect(100)->toBeWithinRange(90, 110);
});
```

Those custom expectations may be also placed in your `tests/Pest.php` file.

---

Next section: [Setup And Teardown →](/docs/setup-and-teardown)
