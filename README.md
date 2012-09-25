rails_test_scripting
====================

Bash script for running various tests in a Rails environment

How to use it:
==============

This method of running tests in a Rails environment does not prepare the database first. As a benefit, the entire test run is a little faster; the obvious drawback is that the test database could be out-of-sync.

In order to get your test database in sync, you can pass the -m flag.

You can specify tests by their path or by a regular expression, which can be any valid regular expression in Ruby.

The script assumes that you are running in your Rails root directory, and that there is a "test" sub-directory.

Usage:
======
```
    usage: /some/where/in/your/path/run_tests -f [path(s)|regex(s)] options
  
    This script runs tests specified by path(s) or regex(s). The
    -f argument may be specified multiple times.
  
    If the -n argument is given it will pass that to Test::Unit
    for method level filtering.
  
    OPTIONS:
       -n arg  Run test methods that match this string
       -f arg  Specify which test files to include (paths or regexs)
       -i      Run integration tests
       -t      Run functional tests
       -u      Run unit tests
       -m      Migrate the test database by running "rake db:test:prepare"
       -h, -?  Show this message
       -c      Start memcached before the run and stop it after
  
    EXAMPLES:
       /some/where/in/your/path/run_tests -f job -n scheduling
       /some/where/in/your/path/run_tests -f test/unit/job_test.rb -f job_review_ -f '/(subm|worker)/'
```
