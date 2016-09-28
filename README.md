# as_deprecation_tracker

Tracks known ActiveSupport (Rails) deprecation warnings and catches new issues
when an unknown warning is seen.

This allows for easier upgrades of Rails and other AS-based apps because as
each deprecation warning is fixed, it's removed from the whitelist and any
attempt to reintroduce the deprecated call will fail.

The library maintains the whitelist in a configuration file that's usually
initially written by running the app test suite with an environment variable
set. When the tests are run normally, deprecation warnings triggered that
aren't in the config file will raise an exception. The call can then be fixed
or added to the whitelist with the provided instructions.

## Installation

    $ gem install as_deprecation_tracker

or in your Gemfile:

    gem 'as_deprecation_tracker', '~> 1.0'

This gem and its API is versioned according to semver.

## Usage

### Whitelisting

The whitelist may be broad, permitting any call causing a particular
deprecation message or be precise, only permitting known calls identified by
their backtrace. With broad whitelists, more instances of the same deprecated
call may be added, but precise whitelists require more maintenance if code is
moved and the backtrace changes.

1. By message
1. By target version number(?)
1. By calltrace

## License

Copyright (c) 2016 Dominic Cleal.  Distributed under the MIT license.