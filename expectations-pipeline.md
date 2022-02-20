---
title: Expectation Pipelines
description: Expectation Pipelines
---

# Expectation Pipelines

- [Overview](#overview)
- [Pipes](#pipes)
- [Interceptorss](#interceptors)

<a name="overview"></a>
## Overview

Generally speaking, you can cover most of your test code using the built-in Expectation API methods and the available Pest Plugins.

For example, if you want to assert that two different users are instances of the same `Model`, you could use the Laravel Plugin as follows:

```php
expect($user)->toBeSameModelAs($anotherUser);
```

In human language, the same idea may can be expressed as: “I expect the user to be like another user”.  Note that the verb “To be”  matches the Expectation method `ToBe()`, and therefore it is only logical to try the following code:

```php
expect($user)->toBe($anotherUser); //Fails, doesn't work.
```

It certainly reads better, but it doesn’t work because `ToBe()` is used to test that values and types matches.

To help you solve this these situations, Pest provides the Expectation Pipes.

Pipes allows you to change or override any existing Expectation API method.

<a name="pipes"></a>
## Pipes

An expectation pipe is a function that is evaluated before checking the given Expectation. You can use `expect()->pipe()` to add a new pipe to a native Expectation API method.

```php
expect()->pipe($expectationName, function($next, ...$arguments){...);
```

Pipes must be included Inside the `Pest.php` file.

For example, the following code modifies the `toBe` Expectation to perform a case-insensitive comparison between `string values`:

```php
<?php

expect()->pipe('toBe', function($next, $expected)
{
    // Goes to the next pipe or expectation if the
    // value or expected value are not strings.
    if(!is_string($this->value) ||!is_string($expected)) {
        return $next();
    }

    assertEqualsIgnoringCase($expected, $this->value);
});
```

As result, the following test will pass:

```php
<?php

test('strings as case-insensitve', function({
    expect('Nuno')->toBe('nuno');
});
```

When `$next()` is called, the control is returned to the actual expectation or to the next chained pipe.

If, instead, the pipe returns nothing, the pipeline is interrupted and the original expectation is not executed. 

@TODO maybe some clarification here.

<a name="interceptors"></a>
## Interceptors

A common pipe use case is to completely replace its expectation original behavior, this can be done in a quick way using expect()->intercept()

```php
expect()->intercept($expectationName, $condition, function(){...)
```

The replacement `function` is applied only if the expectation `$value` is an `instanceof` the `$condition` .

Let’s assume that we want the `toBe` expectation to check if two instance of an `Order` class have the same id:

```php
<?
expect()->intercept('toBe', Order::class, function($another){
    Assert::assertInstanceOf(Order::class, $another);
    Assert::true($this->value->id === $another->id);
});

test('two orders are the same', function(){
    //..
    expect($order1)->toBe($order2); //true
});
```

An interceptor is also applied if the $condition is a closure that evaluates to true. Let’s assume we want that an expect($string)->toBe() passes when the expected string is a wildcard:

```php
<?
expect()->intercept(
    'toBe', 
    fn($value, $expected) => $expected === '*' && is_string($value), 
    function($expected){
        assertTrue(true);
    }
);

it('can use wildcards to compare strings', function({
    $search = '*';
    expect('lorem ipsum')->toBe($search); //true
});
```


---

Next section: [Coverage →](/docs/coverage)
