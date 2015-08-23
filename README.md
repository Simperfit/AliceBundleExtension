AliceFixturesExtension
======================

A [Behat extension](http://behat.org) to load [HautelookAliceBundle](https://github.com/hautelook/AliceBundle) fixtures.

[![Package version](http://img.shields.io/packagist/v/theofidry/alice-fixtures-extension.svg?style=flat-square)](https://packagist.org/packages/theofidry/alice-fixtures-extension)
[![Build Status](https://img.shields.io/travis/theofidry/alice-fixtures-extension.svg?branch=master&style=flat-square)](https://travis-ci.org/theofidry/alice-fixtures-extension?branch=master)
[![SensioLabsInsight](https://img.shields.io/sensiolabs/i/1169e133-3d02-4ba8-a87e-f152c620f8b5.svg?style=flat-square)](https://insight.sensiolabs.com/projects/1169e133-3d02-4ba8-a87e-f152c620f8b5)
[![Scrutinizer Code Quality](https://img.shields.io/scrutinizer/g/theofidry/alice-fixtures-extension.svg?style=flat-square)](https://scrutinizer-ci.com/g/theofidry/alice-fixtures-extension/?branch=master)
[![Code Coverage](https://img.shields.io/scrutinizer/coverage/g/theofidry/alice-fixtures-extension.svg?b=master&style=flat-square)](https://scrutinizer-ci.com/g/theofidry/alice-fixtures-extension/?branch=master)


## Installation

You can use [Composer](https://getcomposer.org/) to install the bundle to your project:

```bash
composer require theofidry/alice-fixtures-extension
```

Then, in your behat config file `behat.yml`, register the extension and declare the context:

```yaml
# behat.yml
default:
    suites:
        default:
            contexts:
                - Fidry\AliceFixturesExtension\Context\AliceContext:
                      kernel:         @kernel
                      finder:         @hautelook_alice.finder
                      loader:         @hautelook_alice.fixtures.loader
                      persister:      @doctrine.orm.entity_manager
                      basePath:       %paths.base%/features/fixtures
    # ...
    extensions:
        Fidry\AliceFixturesExtension\Extension: ~
```


## Basic usage

Assuming you have the same configuration as the [Installation section](#Installation), you can create the following
fixture file:

```yaml
# features/fixtures/dummy.yml

AppBundle\Entity\Dummy:
    dummy_{1..10}:
        name: <name()>
```

Then simply load your fixtures with the following step:

```gherkin
Given the fixtures "user.yml" are loaded
```


## Credits

This bundle is developed by [Théo FIDRY](https://github.com/theofidry).


## License

[![license](https://img.shields.io/badge/license-MIT-red.svg?style=flat-square)](LICENSE)
