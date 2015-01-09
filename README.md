puppet-lint-spaceship_operator_without_tag-check
=================================

[![Build Status](https://travis-ci.org/camptocamp/puppet-lint-spaceship_operator_without_tag-check.svg)](https://travis-ci.org/camptocamp/puppet-lint-spaceship_operator_without_tag-check)
[![Code Climate](https://codeclimate.com/github/camptocamp/puppet-lint-spaceship_operator_without_tag-check/badges/gpa.svg)](https://codeclimate.com/github/camptocamp/puppet-lint-spaceship_operator_without_tag-check)
[![Gem Version](https://badge.fury.io/rb/puppet-lint-spaceship_operator_without_tag-check.svg)](http://badge.fury.io/rb/puppet-lint-spaceship_operator_without_tag-check)
[![Coverage Status](https://img.shields.io/coveralls/camptocamp/puppet-lint-spaceship_operator_without_tag-check.svg)](https://coveralls.io/r/camptocamp/puppet-lint-spaceship_operator_without_tag-check?branch=master)

A puppet-lint plugin to check that spaceship operator is called with a tag.


## Checks

### Spaceship operator without tag

Calling spaceship operator (<| |>) without tag can be dangerous because it will realise all virtual resources of that type.

#### What you have done

```puppet
Package <| |>
```

#### What you should have done

```puppet
Package <| tag != 'virtual' |>
```

#### Disabling the check

To disable this check, you can add `--no-spaceship_operator_without_tag_in_case-check` to your puppet-lint command line.

```shell
$ puppet-lint --no-spaceship_operator_without_tag_in_case-check path/to/file.pp
```

Alternatively, if you’re calling puppet-lint via the Rake task, you should insert the following line to your `Rakefile`.

```ruby
PuppetLint.configuration.send('disable_spaceship_operator_without_tag_in_case')
```