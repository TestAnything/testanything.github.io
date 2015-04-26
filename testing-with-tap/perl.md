---
layout: default
title: Testing with TAP
---

# Testing with Perl

## Testing with Perl 5

There are a number of test modules for Perl, ranging from very simple tests through to very complex tests.
Here are some links to some of them; all of these use the Test Anything Protocol to report their successes or failures:

-    [Test::Simple](http://search.cpan.org/~mschwern/Test-Simple/lib/Test/Simple.pm)
-    [Test::More](http://search.cpan.org/~mschwern/Test-Simple/lib/Test/More.pm)
-    [Test::Exception](http://search.cpan.org/~adie/Test-Exception/lib/Test/Exception.pm)

### A number of harnesses are available including:

-    [TAP::Harness](http://search.cpan.org/~andya/Test-Harness/lib/TAP/Harness.pm)
-    [Test::Harness](http://search.cpan.org/~andya/Test-Harness/lib/Test/Harness.pm)

[TAP::Parser Cookbook](/testing-with-tap/perl/tap::parser-cookbook.html) - Cooking with TAP

## Testing with Perl 6

A set of test files, designed to output TAP, are used to define the specification for Perl 6.
Only a few modules exist, but Test is a core module for every implementation that produces Test Anything Protocol output.

-    [Test](http://design.perl6.org/S24.html)

### Perl 6 Harnesses

-    [Test::Harness](https://github.com/tadzik/Test-Harness/) (incomplete)
