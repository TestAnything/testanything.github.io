---
layout: default
title: TAP Consumers
---

# TAP Consumers

TAP consumers are systems that can take TAP as an input
and do something useful with it.
This page contains a catalog of software libraries
that can act as TAP consumers,
grouped by programming language.

Languages:
[C](#c),
[Java](#java),
[JavaScript](#javascript),
[Perl](#perl),
[Python](#python),
and
[Others](#others).

## [C](#c) <a id="c"></a>

- [C Tap Harness](http://www.eyrie.org/~eagle/software/c-tap-harness/)
- [YACC parser](https://github.com/ligurio/tap-parser)

## [Java](#java) <a id="java"></a>

- [tap4j](http://sourceforge.net/projects/tap4j/)

## [JavaScript](#javascript) <a id="javascript"></a>

- [node-tap](https://www.npmjs.com/package/tap)
- [TAP parser](https://www.npmjs.com/package/tap-parser)
- [tape](https://www.npmjs.com/package/tape)
- [Testling](https://ci.testling.com/guide/local_tests) consumes browser
  test output for any browser test suite that outputs TAP to `console.log`.

## [Perl](#perl) <a id="perl"></a>

- [TAP::Parser](http://search.cpan.org/dist/Test-Harness/lib/TAP/Parser.pm)
- [Test::Harness](http://search.cpan.org/dist/Test-Harness/lib/Test/Harness.pm)
- [Test::Run](http://search.cpan.org/dist/Test-Run/lib/Test/Run.pm)
- [Smolder project background](http://sourceforge.net/projects/smolder/)
- [TapTinder](http://dev.taptinder.org/wiki/TapTinder)
- [metatap](http://search.cpan.org/search?query=metatap)
- [Tapper test infrastructure](http://tapper-testing.org)

## [Python](#python) <a id="python"></a>

- [tappy](https://pypi.python.org/pypi/tap.py)

## [Others](#others) <a id="others"></a>

- [Jenkins TAP Plugin](https://wiki.jenkins-ci.org/display/JENKINS/TAP+Plugin)
- [Desktop notifications](https://github.com/ryandoyle/shouldertap)
- Automake 1.13+ can [run TAP tests](https://www.gnu.org/software/automake/manual/html_node/Using-the-TAP-test-protocol.html#Using-the-TAP-test-protocol) for `make check`, via `tap-driver.sh`.
- [Kyua](https://github.com/jmmv/kyua) Testing framework for infrastructure software.


## Universal desirable behaviors

- These are behaviors desired in all TAP parsers.
- Should work on the TAP as a stream (ie. as each line is received) rather than wait until all the TAP is received.
- The TAP source should be pluggable (ie. don't assume its always coming from a Perl program).
- The TAP display should be pluggable.
- Should be able to gracefully handle future upgrades to TAP.
- Should be forward compatible.
  - Ignore unknown directives
  - Ignore any unparsable lines
