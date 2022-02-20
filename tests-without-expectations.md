---
title: Tests Without Expectations
description: Tests Without Expectations
---

# Tests Without Expectations

- [Overview](#overview)

<a name="overview"></a>
## Overview

@TODO work on this text. Copied from the PR.

A feature that is often useful in PHPUnit is expectNotToPerformAssertions. This is handy when you have a method that is simply testing that a method can be called without throwing any exceptions or causing any errors, without being interested in the end result.

This PR adds a new hasNoExpectations method to the TestCall class, which allows us to support this functionality in a style more aligned with Pest:

```php
it('does not throw any errors when run', function () {
    SomeComplexService::run();
})->hasNoExpectations();
```

---

Next section: [?? →](/docs/??)
