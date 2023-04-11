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
[Go](#go),
[Java](#java),
[JavaScript](#javascript),
[Perl](#perl),
[Python](#python),
[Ruby](#ruby),
and
[Others](#others).

## <a id="python"></a> [Python](#python)

- [tappy](https://pypi.python.org/pypi/tap.py) is a standalone program suited for use as a viewer; just pipe your TAP source to its standard input.

## POSIX shell

- [tapview](https://gitlab.com/esr/tapview) is another tiny standalone viewer, one portable shell file with zero dependencies, intended to be embedded in project test directories.

## <a id="c"></a> [C](#c)

> C is an imperative (procedural) language. It was designed to be compiled
> using a relatively straightforward compiler, to provide low-level access
> to memory, to provide language constructs that map efficiently to machine
> instructions, and to require minimal run-time support.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/C_%28programming_language%29)*

**[C TAP Harness](http://www.eyrie.org/~eagle/software/c-tap-harness/)** is a
TAP library that implements much of the
[Test::More](http://perldoc.perl.org/Test/More.html) API along with some C
specific test functions.

**[tap-parser](https://github.com/ligurio/tap-parser)** is a TAP parser
written with YACC and Lex.

**[tapto](https://github.com/katef/tapto)** is a TAP parser that formats
results to XML and other formats.

## <a id="go"></a> [Go](#go)

- [tap13](https://github.com/mpontillo/tap13/) is a TAP parser that translates
input TAP into structs that can be used for further information processing.

## <a id="java"></a> [Java](#java)

> Java is a general-purpose computer programming language that is concurrent,
> class-based, object-oriented, and specifically designed to have as
> few implementation dependencies as possible.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/Java_%28programming_language%29)*

**[tap4j](https://tupilabs.com/tap4j/tap4j/)** is a full featured TAP library which
is integrated at the core of other Java projects like the
[Jenkins TAP Plugin](https://wiki.jenkins-ci.org/display/JENKINS/TAP+Plugin).

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

## <a id="ruby"></a> [Ruby](#ruby)

- [ruby-tap-parser](https://github.com/vincent-psarga/ruby-tap-parser)


## <a id="others"></a> [Others](#others)

- [Jenkins TAP Plugin](https://wiki.jenkins-ci.org/display/JENKINS/TAP+Plugin)
- [Desktop notifications](https://github.com/ryandoyle/shouldertap)
- Automake 1.13+ can [run TAP tests](https://www.gnu.org/software/automake/manual/html_node/Using-the-TAP-test-protocol.html#Using-the-TAP-test-protocol) for `make check`, via `tap-driver.sh`.
- [Kyua](https://github.com/jmmv/kyua) Testing framework for infrastructure software.
- Meson 0.50+ supports using TAP with its [`test` function](https://mesonbuild.com/Reference-manual_functions.html#test).
