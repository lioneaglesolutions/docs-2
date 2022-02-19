---
title: Expectations
description: Expectations
---

# Expectations

- [Overview](#overview)
- [Usage](#usage)
- [Available Expectations](#available-expectations)
- [Available Modifiers](#available-modifiers)

<a name="overview"></a>
## Overview

The `Expectation API` offers you a different experience in creating PHP tests.

You can write your code almost as if you were writing natural human language. This makes tests very easy to read and understand.

The syntax was inspired by [Jest](https://jestjs.io/docs/expect) and can also be used along with [Assertions](/docs/assertions).


<a name="usage"></a>
## Usage

Start your test by passing your `$value` to the `expect()` function.

Then, you can chain your [expectation](#available-expectations) check(s).

```php
expect($value)->// chain your checks here
```

Let's see an example:

Imagine a situation where you expect that a given user has to be verified and older than 18.

```php
<?php

test('user is verified and over 18', function () {
    // Get the user
    $user = ['name' => 'Nuno', 'age' => 21, 'is_verified' => true];

    // Test
    expect($user)
        ->is_verified->toBeTrue()
        ->age->ToBeGreaterThan(18);
});
```

<a name="available-expectations"></a>
## Available Expectations

Chain one or more Expectations to an `expect()` function to perform checks.

<div class="collection-method-list" markdown="1">

- [`toBe()`](#expect-toBe)
- [`toBeArray()`](#expect-toBeArray)
- [`toBeEmpty()`](#expect-toBeEmpty)
- [`toBeTrue()`](#expect-toBeTrue)
- [`toBeTruthy()`](#expect-toBeTruthy)
- [`toBeFalse()`](#expect-toBeFalse)
- [`toBeFalsy()`](#expect-toBeFalsy)
- [`toBeGreaterThan()`](#expect-toBeGreaterThan)
- [`toBeGreaterThanOrEqual()`](#expect-toBeGreaterThanOrEqual)
- [`toBeLessThan()`](#expect-toBeLessThan)
- [`toBeLessThanOrEqual()`](#expect-toBeLessThanOrEqual)
- [`toContain()`](#expect-toContain)
- [`toHaveCount()`](#expect-toHaveCount)
- [`toHaveProperty()`](#expect-toHaveProperty)
- [`toHaveProperties()`](#expect-toHaveProperties)
- [`toMatchArray()`](#expect-toMatchArray)
- [`toMatchObject()`](#expect-toMatchObject)
- [`toEqual()`](#expect-toEqual)
- [`toEqualCanonicalizing()`](#expect-toEqualCanonicalizing)
- [`toEqualWithDelta()`](#expect-toEqualWithDelta)
- [`toBeIn()`](#expect-toBeIn)
- [`toBeInfinite()`](#expect-toBeInfinite)
- [`toBeInstanceOf()`](#expect-toBeInstanceOf)
- [`toBeBool()`](#expect-toBeBool)
- [`toBeCallable()`](#expect-toBeCallable)
- [`toBeFloat()`](#expect-toBeFloat)
- [`toBeInt()`](#expect-toBeInt)
- [`toBeIterable()`](#expect-toBeIterable)
- [`toBeNumeric()`](#expect-toBeNumeric)
- [`toBeObject()`](#expect-toBeObject)
- [`toBeResource()`](#expect-toBeResource)
- [`toBeScalar()`](#expect-toBeScalar)
- [`toBeString()`](#expect-toBeString)
- [`toBeJson()`](#expect-toBeJson)
- [`toBeNan()`](#expect-toBeNan)
- [`toBeNull()`](#expect-toBeNull)
- [`toHaveKey()`](#expect-toHaveKey)
- [`toHaveKeys()`](#expect-toHaveKeys)
- [`toHaveLength()`](#expect-toHaveLength)
- [`toBeReadableDirectory()`](#expect-toBeReadableDirectory)
- [`toBeWritableDirectory()`](#expect-toBeWritableDirectory)
- [`toStartWith()`](#expect-toStartWith)
- [`toThrow()`](#expect-toThrow)
- [`toEndWith()`](#expect-toEndWith)
- [`toMatch()`](#expect-toMatch)
- [`toMatchConstraint()`](#expect-toMatchConstraint)

</div>

**Note**: Expectation functionality can be changed using [Modifiers](#available-modifiers).


<a name="expect-toBe"></a>
### `toBe()`

Asserts that two variables have the same `type` and `$value`.
Used on objects, it asserts that the two variables reference the same object.

```php
expect($color)->toBe('pink');

expect($user)->toBe($user);
```

<a name="expect-toBeEmpty"></a>
### `toBeEmpty()`

Asserts that the `$value` is empty.

```php
expect($lastSeen)->toBeEmpty();
```

<a name="expect-toBeTrue"></a>
### `toBeTrue()`

Asserts that the `$value` is `true`.

```php
expect($isPublished)->toBeTrue();
```

<a name="expect-toBeTruthy"></a>
### `toBeTruthy()`

Asserts that the `$value` is truthy.

```php
expect(1)->toBeTruthy();
expect('1')->toBeTruthy();
```

<a name="expect-toBeFalse"></a>
### `toBeFalse()`

Asserts that the `$value` is `false`.

```php
expect($isPublished)->toBeFalse();
```

<a name="expect-toBeFalsy"></a>
### `toBeFalsy()`

Asserts that the `$value` is falsy.

```php
expect(0)->toBeFalsy();
expect('')->toBeFalsy();
```

<a name="expect-toBeGreaterThan"></a>
### `toBeGreaterThan($expected)`

Asserts that the `$value` is greater than the expected one.

```php
expect($count)->toBeGreaterThan(20);
```

<a name="expect-toBeGreaterThanOrEqual"></a>
### `toBeGreaterThanOrEqual($expected)`

Asserts that the `$value` is greater than or equal to the expected one.

```php
expect($count)->toBeGreaterThanOrEqual(21);
```

<a name="expect-toBeLessThan"></a>
### `toBeLessThan($expected)`

Asserts that the `$value` is lesser than the expected one.

```php
expect($count)->toBeLessThan(3);
```

<a name="expect-toBeLessThanOrEqual"></a>
### `toBeLessThanOrEqual($expected)`

Asserts that the `$value` is lesser than or equal to the expected one.

```php
expect($count)->toBeLessThanOrEqual(2);
```

<a name="expect-toContain"></a>
### `toContain($needles)`

Asserts that all given needles are elements of the `$value`.

```php
expect('Hello World')->toContain('Hello');
expect([1, 2, 3, 4])->toContain(2, 4);
```

<a name="expect-toHaveCount"></a>
### `toHaveCount(int $count)`

Asserts the provided `$count` matches the number of elements in an `iterable` `$value`.

```php
expect(['Nuno', 'Luke', 'Alex', 'Dan'])->toHaveCount(4);
```

> 💡 To assert length, see the [`toHaveLength()`](#expect-toHaveLength) method.

<a name="expect-toHaveProperty"></a>
### `toHaveProperty(string $name, $value = null)`

Asserts that the `$value` contains the property `$name`.

```php
expect($user)->toHaveProperty('name');
expect($user)->toHaveProperty('name', 'Nuno');
```

<a name="expect-toHaveProperties"></a>
### `toHaveProperties(iterable $name)`

Asserts that the `$value` contains the provided properties `$names`.

```php
expect($user)->toHaveProperties(['name', 'email']);
```

<a name="expect-toMatchArray"></a>
### `toMatchArray($array)`

Asserts that the `$value` array matches the given `$array` subset.

```php
$user = [
    'id'    => 1,
    'name'  => 'Nuno',
    'email' => 'enunomaduro@gmail.com',
];

expect($user)->toMatchArray([
    'email' => 'enunomaduro@gmail.com',
    'name' => 'Nuno'
]);
```

<a name="expect-toMatchObject"></a>
### `toMatchObject($object)`

Asserts that the `$value` object matches a subset of the properties of a given `$object`.

```php
$user = new stdClass();
$user->id = 1;
$user->email = 'enunomaduro@gmail.com';
$user->name = 'Nuno';

expect($user)->toMatchObject([
    'email' => 'enunomaduro@gmail.com',
    'name' => 'Nuno'
]);
```

<a name="expect-toEqual"></a>
### `toEqual($expected)`

Asserts that two variables have the same `$value`, not considering the `$value` `type`.

```php
expect($title)->toEqual('Hello World');
expect(1)->toEqual('1');
```

<a name="expect-toEqualCanonicalizing"></a>
### `toEqualCanonicalizing($expected)`

Asserts that two variables have the same `$value`.
The contents of `$value` and `$expected` are canonicalized before
they are compared. For instance, when the two variables are arrays,
then these arrays are sorted before they are compared.
When they are objects, each object is converted to an array
containing all private, protected, and public attributes.

```php
expect([4, 2, 1])->toEqualCanonicalizing([2, 4, 1]);

// this is the equivalent of:
expect([1, 2, 4])->toEqual([1, 2, 4]);
```

<a name="expect-toEqualWithDelta"></a>
### `toEqualWithDelta($expected, float $delta)`

Asserts that the absolute difference between `$value` and `$expected` is lower than `$delta`.

```php
expect($bakingTime)->toEqualWithDelta(30, 5); //Baking time with a 5 minute variance
```

<a name="expect-toBeIn"></a>
### `toBeIn()`

Asserts that the `$value` is one of the given values.

```php
expect($response->httpCode)->toBeIn([200, 301, 302]);
```

<a name="expect-toBeInfinite"></a>
### `toBeInfinite()`

Asserts that the `$value` is infinite.

```php
expect(log(0))->toBeInfinite();
```

<a name="expect-toBeInstanceOf"></a>
### `toBeInstanceOf($class)`

Asserts that the `$value` is an instance of `$class`.

```php
expect($user)->toBeInstanceOf(User::class);
```

<a name="expect-toBeArray"></a>
### `toBeArray()`

Asserts that the `$value` is an array.

```php
expect(['Pest','PHP','Laravel'])->toBeArray();
```

<a name="expect-toBeBool"></a>
### `toBeBool()`

Asserts that the `$value` is of type `bool`.

```php
expect($isActive)->toBeBool();
```

<a name="expect-toBeCallable"></a>
### `toBeCallable()`

Asserts that the `$value` is of type `callable`.

```php
$myFunction = function () {};

expect($myFunction)->toBeCallable();
```

<a name="expect-toBeFloat"></a>
### `toBeFloat()`

Asserts that the `$value` is of type `float`.

```php
expect($height)->toBeFloat();
```

<a name="expect-toBeInt"></a>
### `toBeInt()`

Asserts that the `$value` is of type `integer`.

```php
expect($count)->toBeInt();
```

<a name="expect-toBeIterable"></a>
### `toBeIterable()`

Asserts that the `$value` is of type `iterable`.

```php
expect($value)->toBeIterable();
```

<a name="expect-toBeNumeric"></a>
### `toBeNumeric()`

Asserts that the `$value` is of type `numeric`.

```php
expect(10)->toBeNumeric();
expect('10')->toBeNumeric();
```

<a name="expect-toBeObject"></a>
### `toBeObject()`

Asserts that the `$value` is of type `object`.

```php
$object = new stdClass();

expect($object)->toBeObject();
```

<a name="expect-toBeResource"></a>
### `toBeResource()`

Asserts that the `$value` is of type `resource`.

```php
$handle = fopen('php://memory', 'r+');

expect($handle)->toBeResource();
```

<a name="expect-toBeScalar"></a>
### `toBeScalar()`

Asserts that the `$value` is of type `scalar`.

```php
expect('1')->toBeScalar();
expect(1)->toBeScalar();
expect(1.0)->toBeScalar();
expect(true)->toBeScalar();
expect([1, '1'])->not->toBeScalar();
```

<a name="expect-toBeString"></a>
### `toBeString()`

Asserts that the `$value` is of type `string`.

```php
expect('Hello world')->toBeString();
```

<a name="expect-toBeJson"></a>
### `toBeJson()`

Asserts that the `$value` is a JSON string.

```php
expect('{"hello":"world"}')->toBeJson();
```

> 💡 See also the [`json()`](#expect-json) modifier.


<a name="expect-toBeNan"></a>
### `toBeNan()`

Asserts that the `$value` is not a number (NaN).

```php
expect(sqrt(-1))->toBeNan();
```

<a name="expect-toBeNull"></a>
### `toBeNull()`

Asserts that the `$value` is `null`.

```php
expect(null)->toBeNull();
```

<a name="expect-toHaveKey"></a>
### `toHaveKey(string $key)`

Asserts that the `$value` contains the provided `$key`.

```php
expect(['name' => 'Nuno', 'surname' => 'Maduro'])->toHaveKey('name');
```

You may pass a second parameter to assert that the `$value` at the given key is equal to something:

```php
expect(['name' => 'Nuno', 'surname' => 'Maduro'])->toHaveKey('name', 'Nuno');
```

This expectation also supports dot notation for reaching deeper into nested arrays:

```php
expect(['user' => ['name' => 'Nuno', 'surname' => 'Maduro']])->toHaveKey('user.name');
expect(['user' => ['name' => 'Nuno', 'surname' => 'Maduro']])->toHaveKey('user.name', 'Nuno');
```

<a name="expect-toHaveKeys"></a>
### `toHaveKeys(array $keys)`

Asserts that the `$value` contains the provided `$keys`.

```php
expect(['id' => 1, 'name' => 'Nuno'])->toHaveKeys(['id', 'name']);
```

This expectation also supports dot notation for reaching deeper into nested arrays:

```php
expect(['message' => ['from' => 'Nuno', 'to' => 'Luke'] ])->toHaveKeys(['message.from', 'message.to']);
```

<a name="expect-toHaveLength"></a>
### `toHaveLength(int $number)`

Asserts that the provided `$number` matches the length of a `string` `$value` or the number of elements in an `iterable` `$value`.

```php
expect('Pest')->toHaveLength(4);
expect(['Nuno', 'Maduro'])->toHaveLength(2);
```

<a name="expect-toBeDirectory"></a>
### `toBeDirectory()`

Asserts that the `string` `$value` is a directory.

```php
expect('/tmp')->toBeDirectory();
```

<a name="expect-toBeReadableDirectory"></a>
### `toBeReadableDirectory()`

Asserts that the `string` `$value` is a directory, and it is readable.

```php
expect('/tmp')->toBeReadableDirectory();
```

<a name="expect-toBeWritableDirectory"></a>
### `toBeWritableDirectory()`

Asserts that the `string` `$value` is a directory, and it is writable.

```php
expect('/tmp')->toBeWritableDirectory();
```

<a name="expect-toStartWith"></a>
### `toStartWith(string $expected)`

Asserts that the `$value` starts with the provided `string` `$expected`.

The expectation is case-sensitive.

```php
expect('Hello World')->toStartWith('Hello');
```

<a name="expect-toThrow"></a>
### `toThrow()`

Asserts that a closure throws an exception class, exception message, or the combination of both.

```php
test('it throws the desired Exception class', function () {
    expect(fn() => throw new Exception('Something happened.'))->toThrow(Exception::class);
});
```

```php
test('it throws an exception with desired message', function () {
    expect(fn() => throw new Exception('Something happened.'))->toThrow('Something happened.');
});
```

```php
test('it throws the desired Exception class with the desired message', function () {
    expect(fn() => throw new Exception('Something happened.'))->toThrow(Exception::class, 'Something happened.');
});
```

You may assert more than one exception per test:

```php
test('it asserts two exceptions with their specific messages', function () {
    expect(fn() => throw new Exception('Error 1'))->toThrow(Exception::class, 'Error 1');

    expect(fn() => throw new Exception('Error 2'))->toThrow(Exception::class, 'Error 2');
});
```

It is also possible to use `not()` modifier together with `toThrow()`.

```php
test('it does not throw an Exception', function () {
    expect(fn ($x, $y) => $x + $y)->not->toThrow(Exception::class);
});
```

<a name="expect-toMatch"></a>
### `toMatch(string $expression)`

Asserts that the `$value` matches a regular expression.

```php
expect('Hello World')->toMatch('/^hello wo.*$/i');
```

<a name="expect-toEndWith"></a>
### `toEndWith(string $expected)`

Asserts that the `$value` ends with the provided `string` `$expected`.

The expectation is case-sensitive.

```php
expect('Hello World')->toEndWith('World');
```

<a name="expect-toMatchConstraint"></a>
### `toMatchConstraint(Constraint $constraint)`

Asserts that the `$value` matches a specified [PHPUnit constraint](https://github.com/sebastianbergmann/phpunit/tree/master/src/Framework/Constraint).

```php
use PHPUnit\Framework\Constraint\IsTrue;

expect(true)->toMatchConstraint(new IsTrue());
```

Asserts that the `$value` matches a complex group of constraints.

```php
use PHPUnit\Framework\Constraint\IsFalse;
use PHPUnit\Framework\Constraint\IsType;

expect(true)->toMatchConstraint(
    $this->logicalAnd(
         $this->logicalNot(new IsFalse()),
         new IsType(IsType::TYPE_BOOL)
    )
);
```

Asserts that the `$value` matches a custom constraint.

```php
expect('https://google.com')->toMatchConstraint(new IsValidUrlConstraint());
class IsValidUrlConstraint extends \PHPUnit\Framework\Constraint\Constraint
{
    public function toString(): string
    {
        return 'is a valid url';
    }
    protected function matches($other): bool
    {
        if (! is_string($other)) {
            return false;
        }
        return preg_match(
            Symfony\Component\Validator\Constraints\UrlValidator::PATTERN,
            $other
        ) > 0;
    }
}
```

> Custom constraints should extend `PHPUnit\Framework\Constraint\Constraint`, and provide a `matches()` and `toString()` method, and optionally override the `evaluate()` method.

<a name="available-modifiers"></a>
## Available Modifiers

Modifiers can be used to enhance or modify the functionality of [Expectations](#available-expectations) methods.

<div class="collection-method-list" markdown="1">

- [`and()`](#expect-and)
- [`dd()`](#expect-dd)
- [`each()`](#expect-each)
- [`json()`](#expect-json)
- [`match()`](#match)
- [`not()`](#expect-not)
- [`ray()`](#expect-ray)
- [`sequence()`](#expect-sequence)
- [`unless()`](#unless)
- [`when()`](#when)

</div>

<a name="expect-and"></a>
### `and()`

The `and()` modifier allows you to chain multiples `expectations` to a single `expect()` call.

Pass a new `value` to the `and` function and continue chaining tests.

```php
expect($id)->toBe(14)
    ->and($name)->toBe('Nuno')
    ->and($country)->toBe('Portugal');
```

<a name="expect-dd"></a>
### `dd()`

Use the `dd()` method to dump the current expectation value and end the script.

```php
expect(14)->dd(); // 14

expect([1, 2])->sequence(
    fn ($number) => $number->toBe(1),
    fn ($number) => $number->dd(), // 2
);
```

> 💡 The acronym "dd" stands for "dump and die".

<a name="expect-each"></a>
### `each()`

Use the `each()` modifier to create an expectation on each item of the given iterable.

```php
expect([1, 2, 3])->each->toBeInt();
expect([1, 2, 3])->each->not->toBeString();

expect([1, 2, 3])->each(fn ($number) => $number->toBeLessThan(4));
```


<a name="expect-json"></a>

### `json()`

The `json()` modifier asserts that the given `value` is a valid `json string`.

This method also provides a convenient way to test the Json values by converting the string into an `iterable` `value`.

```php
expect('{"name":"Nuno","credit":1000.00}')
    ->json()
    ->toHaveCount(2)
    ->name->toBe('Nuno')
    ->credit->toBeFloat();

expect('not-a-json')->json(); //FAILS: Failed asserting that 'not-a-json' is valid JSON

```

> **NOTE:**  Using this modifier in a Higher Order test, will not allow the scope to be reset back to upper levels, locking it in the transformed value.

<a name="match"></a>
### `match()`

The `match()` method executes the `callback` of the first `key` that matches the first argument given to the method.

```php
expect('pest')
    ->match(true, [
        true  => fn ($value) => $value->toEqual('pest'),
        false => fn ($value) => $value->not->toEqual('pest')
    ]);
```

If you just want to check that the expected `value` is equal to the `$value` of the matching key, you can pass the expected `value` directly instead of using a `callback`.

```php
expect('pestphp')
    ->match('twitter', [
        'twitter' => 'pestphp',
        'website' => 'pestphp.com'
    ]);
```

<a name="expect-not"></a>
### `not()`

Use the `not()` modifier before a `method` to invert it.

```php
expect(10)->not->toBeGreaterThan(100);
```

<a name="expect-ray"></a>
### `ray()`

Use the `ray()` method to debug the current expectation value with **[myray.app](https://myray.app/)**.

```php
expect(14)->ray(); // 14

expect([1, 2])->sequence(
    fn ($number) => $number->toBe(1),
    fn ($number) => $number->ray(), // 2
);
```

<a name="expect-sequence"></a>
### `sequence()`

Use the `sequence()` method to specify a sequential set of expectations for each item of the given iterable.

```php
expect([1, 2, 3])->sequence(
    fn ($number) => $number->toBe(1),
    fn ($number) => $number->toBe(2),
    fn ($number) => $number->toBe(3),
);
```

You can also use the `sequence()` method with associative iterables. Each closure receives the `$value` as an expectation for
the first argument, and the key as an expectation for the second argument.

```php
expect(['hello' => 'world', 'foo' => 'bar', 'john' => 'doe'])->sequence(
    fn ($value, $key) => $value->toEqual('hello'),
    fn ($value, $key) => $key->toEqual('foo'),
    fn ($value, $key) => $value->toBeString(),
);
```

If you just want to check that each `value` in the `iterable` is equal to another `value`, you can pass the expected `value`
directly instead of using a `closure`.

```php
expect(['foo', 'bar', 'baz'])->sequence('foo', 'bar', 'baz');
```

<a name="when"></a>
### `when()`

The when method will execute the given `callback` when the first argument given to the method evaluates to `true`.

```php
expect($user)
    ->when(true, fn ($user) => $user->verified->toBeTrue())
    ->first_name->toEqual('Nuno');
```

<a name="unless"></a>
### `unless()`

The `unless()` method will execute the given `callback` unless the first argument given to the method evaluates to `true`.

```php
expect($user)
    ->unless(false, fn ($user) => $user->verified->toBeTrue())
    ->first_name->toEqual('Nuno');
```

Next section: [Assertions →](/docs/assertions)