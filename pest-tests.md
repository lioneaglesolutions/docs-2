---
title: Pest Tests
description: Pest test files
---

# Pest Tests

- [Test files](#test-files)
- [Pest syntax](#pest-syntax)
- [PHPUnit syntax](#phpunit-syntax)

<a name="test-files"></a>
## Test files

Pest test files are clean and simple and easy to read. There is no need for classes and no boilerplate code.

You can read more about [Files & Folders](http://pestphp.com/) in Pest.

<a name="pest-syntax"></a>
## Pest syntax

Pest offers you two functions to write tests with: `test()` and `it()`.

You can use them as you prefer, the two functions are used in the same way:

- They require two parameters: The first is the test description. The second is a `closure` containing the test code.
- Both can handle [Assertions](/docs/assertions) and [Expectations](/docs/expectations) to perform checks.

Example of a test written syntax Pest API:

```php
<?php

test('TRUE is TRUE', function () {
    $this->assertTrue(true);   // assertion
    expect(true)->toBeTrue();  // expectation
});
```

The function `it()` prepends the word *"it"* to your test description.

In other words, for the example below, the test report will show: `it checks that TRUE is TRUE`.

```php
<?php

it('checks that TRUE is TRUE', function () {
    $this->assertTrue(true);   // assertion
    expect(true)->toBeTrue();   // expectation
});
```

> 💡 A closure is an anonymous function passed as an argument to another function.

<br/>

## PHPUnit syntax

Just for comparison, here is the PHPUnit version of the examples featured in this section.

Tests written with PHPUnit syntax are fully compatible with Pest, and will run as expected.

```php
<?php

namespace Tests\Feature;

use Tests\TestCase;

class ExampleTest extends TestCase
{
    /**
     * A basic test example.
     *
     * @return void
     */
    public function test_true_is_true()
    {
        $this->assertTrue(true);
    }
}
```

---

**Next**: Let's start [`writing tests` →](/docs/writing-tests)