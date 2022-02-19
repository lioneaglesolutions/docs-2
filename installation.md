---
title: Installation
description: Installation
---

# Installation

**Requirements:**

-  [PHP 7.3+](https://php.net/releases/).
-  [Composer](https://getcomposer.org/).
-  (optional) see [compatibility →](/docs/compatibility)

## Installation

The installation process consists of 3 steps to be performed in your command line.

<br/>

``Step 1:`` Require Pest as a dev dependency in your project. Run the following command:

```bash
composer require pestphp/pest --dev --with-all-dependencies
```

<hr/>

`Step 2:` What project do you have?  Choose and click below to continue with the installation:

<details>
  <summary><em>Laravel Framework</em></summary>
    
  Pest has a dedicated [Laravel Plugin](/docs/plugins/laravel) which gives you direct access to Laravel's testing API in your test files.

  2.1. Require the Laravel Plugin via Composer, running the following command:

  ```bash
  composer require pestphp/pest-plugin-laravel --dev
  ```

  2.2. Install Pest using Artisan, run the following command:

  ```bash
  php artisan pest:install
  ```

  Pest has now configured its [Files & Folders](/docs/files-and-folders) structure, and it’s ready to be used.

  <br/>

</details>

<details>
  <summary><em>PHP Project (PHP Frameworks)</em></summary>

  2.1. Initialize and setup Pest. Run the following command:

  ```bash
  ./vendor/bin/pest --init
  ```

  Pest has now configured its [Files & Folders](/docs/files-and-folders) structure, and it’s ready to be used.

</details>

<hr/>

`Step 3:` Pest is a command line tool. To run your tests, execute the command:

```bash
./vendor/bin/pest
```

<br/>

The image below shows the default Test Report in a brand-new project.

Now, click here let's see the syntax of a [`Pest Test` →](/docs/pest-tests)

![Install](/assets/img/pestinstall.png)

---

**Next**: Let's see the syntax of a [`Pest Test` →](/docs/pest-tests)
