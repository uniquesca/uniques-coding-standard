# Uniques Coding Standard

This library is established Uniques Coding Standard which incorporates the following:
1. Codestyle ruleset for PHP Codesniffer - it is a tweaked version of 
  [Laminas Coding Standard](https://github.com/laminas/laminas-coding-standard)
2. Rules for checking code for potential bugs by Psalm - right now base level is 
  set to 3 out of 9 (the lower the level, the more strict are the rules).

All Uniques developers are obliged to adhere to this coding standard.

## Installation

1. Install the module via composer by running:

   ```bash
   composer require --dev uniquesca/uniques-coding-standard
   ```

2. Add composer scripts into your `composer.json`:

   ```json
   "scripts": {
     "cs-check": "./vendor/bin/phpcs",
     "cs-fix": "./vendor/bin/phpcbf",
     "psalm": "./vendor/bin/psalm --show-info"
   }
   ```

3. Copy `phpcs.xml.dist` file from this project to `phpcs.xml` file in the root directory
   of your repository, adjust list of paths accordingly.
   You can add or exclude some locations in that file.
   For a reference please see: https://github.com/squizlabs/PHP_CodeSniffer/wiki/Annotated-Ruleset

4. Copy `psalm.xml.dist` file from this project to `psalm.xml` file in the root directory
   of your repository, adjust list of paths accordingly.

## Usage

- To run code style check:

  ```bash
  composer cs-check
  ```

- To automatically fix many codestyle issues:

  ```bash
  composer cs-fix
  ```

- To run code inspection for potential bugs:

  ```bash
  composer psalm
  ```
  
- If there are issues that can be fixed automatically by Psalm:

  ```bash
  # Use --dry-run first to check what and how Psalm is going to fix
  ./vendor/bin/psalter --issues=<ISSUE NAMES FROM THE PSALM RUN> [--dry-run]
  ```
  
## Reference:
1. [Psalm](https://psalm.dev)
2. [PHP Codesniffer](https://github.com/squizlabs/PHP_CodeSniffer/wiki)
   - [Coding Standard Tutorial](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Coding-Standard-Tutorial)
   - [Configuration Options](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Configuration-Options)
   - [Selectively Applying Rules](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Annotated-Ruleset#selectively-applying-rules)
   - [Customisable Sniff Properties](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Customisable-Sniff-Properties)
