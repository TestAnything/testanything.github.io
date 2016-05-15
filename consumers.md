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

## <a id="c"></a> [C](#c)

> C is an imperative (procedural) language. It was designed to be compiled
> using a relatively straightforward compiler, to provide low-level access
> to memory, to provide language constructs that map efficiently to machine
> instructions, and to require minimal run-time support.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/C_%28programming_language%29)*

**[C TAP Harness](http://www.eyrie.org/~eagle/software/c-tap-harness/)** is a
TAP library that implments much of the
[Test::More](http://perldoc.perl.org/Test/More.html) API along with some C
specific test functions.

**[tap-parser](https://github.com/ligurio/tap-parser)** is a TAP parser
written with YACC and Lex.

## <a id="java"></a> [Java](#java)

- [tap4j](http://sourceforge.net/projects/tap4j/)

## <a id="javascript"></a> [JavaScript](#javascript)

- [node-tap](https://www.npmjs.com/package/tap)
- [TAP parser](https://www.npmjs.com/package/tap-parser)
- [tape](https://www.npmjs.com/package/tape)
- [Testling](https://ci.testling.com/guide/local_tests) consumes browser
  test output for any browser test suite that outputs TAP to `console.log`.

## <a id="perl"></a> [Perl](#perl)

- [TAP::Parser](http://search.cpan.org/dist/Test-Harness/lib/TAP/Parser.pm)
- [Test::Harness](http://search.cpan.org/dist/Test-Harness/lib/Test/Harness.pm)
- [Test::Run](http://search.cpan.org/dist/Test-Run/lib/Test/Run.pm)
- [Smolder project background](http://sourceforge.net/projects/smolder/)
- [TapTinder](http://dev.taptinder.org/wiki/TapTinder)
- [metatap](http://search.cpan.org/search?query=metatap)
- [Tapper test infrastructure](http://tapper-testing.org)

## <a id="python"></a> [Python](#python)

- [tappy](https://pypi.python.org/pypi/tap.py)

## <a id="others"></a> [Others](#others)

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
