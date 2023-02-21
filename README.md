# Uniques coding standard

Coding standard ruleset for Uniques components.

This specification tweaks [Laminas Coding Standard](https://github.com/laminas/laminas-coding-standard).

All Uniques developers are obliged to adhere to this coding standard.

## Installation

1. Install the module via composer by running:

   ```bash
   composer require --dev uniquesca/uniques-coding-standard
   ```

2. Add composer scripts into your `composer.json`:

   ```json
   "scripts": {
     "cs-check": "phpcs",
     "cs-fix": "phpcbf"
   }
   ```

3. Create file `phpcs.xml` on base path of your repository with this content:

   ```xml
   <?xml version="1.0"?>
   <ruleset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:noNamespaceSchemaLocation="vendor/squizlabs/php_codesniffer/phpcs.xsd">

       <arg name="basepath" value="."/>
       <arg name="cache" value=".phpcs-cache"/>
       <arg name="colors"/>
       <arg name="extensions" value="php"/>
       <arg name="parallel" value="80"/>

       <!-- Show progress -->
       <arg value="sp"/>

       <!-- Paths to check -->
       <file>config</file>
       <file>src</file>
       <file>test</file>

       <!-- Include all rules from the Uniques Coding Standard -->
       <rule ref="UniquesCodingStandard"/>
   </ruleset>
   ```

You can add or exclude some locations in that file.
For a reference please see: https://github.com/squizlabs/PHP_CodeSniffer/wiki/Annotated-Ruleset

## Usage

- To run checks only:

  ```bash
  composer cs-check
  ```

- To automatically fix many CS issues:

  ```bash
  composer cs-fix
  ```

## Ignoring parts of a File

> Note: Disabling sniffer checks should not be done without a solid reason. Integration with the Standard can be 
> gradual, but once it's done, code should be maintained according to the Standard as much as possible.

> Note: Before PHP_CodeSniffer version 3.2.0, `// @codingStandardsIgnoreStart` and `// @codingStandardsIgnoreEnd` were
> used. These are deprecated and will be removed in PHP_CodeSniffer version 4.0.

Disable parts of a file:

```php
$xmlPackage = new XMLPackage;
// phpcs:disable
$xmlPackage['error_code'] = get_default_error_code_value();
$xmlPackage->send();
// phpcs:enable
```

Disable a specific rule:

```php
// phpcs:disable Generic.Commenting.Todo.Found
$xmlPackage = new XMLPackage;
$xmlPackage['error_code'] = get_default_error_code_value();
// TODO: Add an error message here.
$xmlPackage->send();
// phpcs:enable
```

Ignore a specific violation:

```php
$xmlPackage = new XMLPackage;
$xmlPackage['error_code'] = get_default_error_code_value();
// phpcs:ignore Generic.Commenting.Todo.Found
// TODO: Add an error message here.
$xmlPackage->send();
```

## Development

> **New rules or Sniffs may not be introduced in minor or bugfix releases and should always be based on the develop
branch and queued for the next major release, unless considered a bugfix for existing rules.**

## Reference

Rules can be added, excluded or tweaked locally, depending on your preferences. More information on how to do this can
be found here:

- [Coding Standard Tutorial](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Coding-Standard-Tutorial)
- [Configuration Options](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Configuration-Options)
- [Selectively Applying Rules](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Annotated-Ruleset#selectively-applying-rules)
- [Customisable Sniff Properties](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Customisable-Sniff-Properties)
