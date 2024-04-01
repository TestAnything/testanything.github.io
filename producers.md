---
layout: default
title: TAP Producers
---

# TAP Producers

TAP producers are any systems which output TAP.
This page contains a catalog of software libraries
that can act as TAP producers,
grouped by programming language.

Languages:
[Ada](#ada),
[C](#c),
[C++](#cplusplus),
[C#](#csharp),
[Common Lisp](#common-lisp),
[Crystal](#crystal),
[Elixir](#elixir),
[Erlang](#erlang),
[Fish](#fish),
[Forth](#forth),
[Fortran](#fortran),
[Gambas](#gambas),
[Go](#go),
[Haskell](#haskell),
[Igor Pro](#igorpro),
[Java](#java),
[JavaScript](#javascript),
[Limbo](#limbo),
[Lua](#lua),
[MATLAB](#matlab),
[OCaml](#ocaml),
[Omnis Studio](#omnis-studio),
[Pascal](#pascal),
[Perl5](#perl5),
[Perl6](#perl6),
[PHP](#php),
[Prolog](#prolog),
[Python](#python),
[Ruby](#ruby),
[Rust](#rust),
[Sass](#sass),
[Shell](#shell),
[SQL](#sql),
and
[TypeScript](#typescript).

Some test frameworks exist with
[TAP producers that are not language specific](#frameworks).

## <a id="ada"></a> [Ada](#ada)

> Ada is a modern programming language designed for large,
> long-lived applications – and embedded systems in particular –
> where safety and security are essential.
>
> *From [Ada Information Clearinghouse](http://www.adaic.org/)*

**[Ahven](http://ahven.stronglytyped.org/)** is a unit test library
for Ada which produces TAP 12 output.

## <a id="c"></a> [C](#c)

> C is an imperative (procedural) language. It was designed to be compiled
> using a relatively straightforward compiler, to provide low-level access
> to memory, to provide language constructs that map efficiently to machine
> instructions, and to require minimal run-time support.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/C_%28programming_language%29)*

**[ArduinoTap](https://framagit.org/fperrad/ArduinoTap)** is a C/C++ port of the Perl5 module
Test::More on Arduino.

**[C TAP Harness](http://www.eyrie.org/~eagle/software/c-tap-harness/)** is a
TAP library that implements much of the
[Test::More](http://perldoc.perl.org/Test/More.html) API along with some C
specific test functions.

**[cmocka](https://cmocka.org/)** is an elegant unit testing framework for C
with support for mock objects.

**[GLib](https://git.gnome.org/browse/glib/)** is a
low-level core library for projects such as GTK+ and GNOME.
Tests built with [GLib's test
framework](https://developer.gnome.org/glib/stable/glib-Testing.html)
produce TAP version 12 when run with the `--tap` option.

**[KUnit](https://www.kernel.org/doc/html/latest/dev-tools/kunit/start.html)**
is a unit testing framework for the Linux Kernel. Test output is written
to the kernel log in TAP format.

**[libtap](http://github.com/zorgnax/libtap)** is another TAP library that
follows the [Test::More](http://perldoc.perl.org/Test/More.html) API.

**[MyTAP](http://www.kindahl.net/mytap/doc/)** is another TAP version 12
producer for C. This library is different from the MyTAP producer for MySQL.
See [SQL](#sql).

**[Shlomi Fish's libtap](http://www.shlomifish.org/open-source/projects/libtap/)** is a
TAP version 12 producer for C. Discontinued in favor of cmocka and libtap.

The shlomifish libtap fork has
**[a branch](https://github.com/shlomif/libtap/tree/cmake)** that replaces the
Makefile with Cmake support.

**[tap4embedded](https://framagit.org/fperrad/tap4embedded)** is a TAP producer
library designed for C embedded.

## <a id="cplusplus"></a> [C++](#cplusplus)

> C++ is a general-purpose programming language with a bias towards
> systems programming that: is a better C, supports data abstraction,
> object-oriented programming, generic programming, and functional programming.
>
> *From [Standard C++](https://isocpp.org/wiki/faq/big-picture#what-is-cpp)*

Looking for a guide?
[Testing with C++](/testing-with-tap/c-plus-plus.html) has some examples.

**[GoogleTest TAP Listener](https://github.com/kinow/gtest-tap-listener)**
is a TAP producer for [GoogleTest](https://github.com/google/googletest),
Google's C++ test framework.

**[libtap++](https://github.com/Leont/libperl--)** is a TAP library
embedded within `libperl++`. It is a mostly complete port of
[Test::More](http://perldoc.perl.org/Test/More.html) to C++.

**[libtappp](https://github.com/cbab/libtappp)** is a fork of `libtap++`
that removes the build time dependency to [Boost](http://www.boost.org/).

**[QtTest](https://doc.qt.io/qt-6/qttest-index.html)** is the testing
framework of [The Qt Project](https://www.qtproject.org/) and supports
output in TAP format, by passing the `-tap` option on a test's
command-line.

## [C# <a id="csharp"></a>](#csharp)

> C# is a multi-paradigm programming language encompassing strong typing,
> imperative, declarative, functional, generic, object-oriented (class-based),
> and component-oriented programming disciplines.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/C_Sharp_%28programming_language%29)*

**[Taps](https://github.com/TestAnything/taps-testing/)** is a test tool for the
.NET framework and Mono. It is inspired on Perl's testing facilities and
is therefore quite different from tools like NUnit.

## <a id="common-lisp"></a> [Common Lisp](#common-lisp)

> Common Lisp is the modern, multi-paradigm, high-performance, compiled,
> ANSI-standardized, most prominent (along with Scheme) descendant of the
> long-running family of Lisp programming languages.
>
> *From [Common-Lisp.net](https://common-lisp.net/)*

**[cl-tap-producerX](https://github.com/brobinson9999/cl-tap-producerX)**
is a testing library which produces TAP to standard output.
cl-tap-producerX is split into two parts: a test library which generates
structured test result data, and a TAP producer which formats the
structured test data to TAP output.

**[testbild](http://www.cliki.net/testbild)** is a Common Lisp library
designed to provide a common interface for Unit testing output.
Currently, it supports TAP version 12 and xUnit style output.
It is available via [Quicklisp](http://www.quicklisp.org/).

## <a id="crystal"></a> [Crystal](#crystal)

**[crystal spec](https://crystal-lang.org/api/Spec.html)** the spec module
that comes with Crystal's standard library includes a TAP formatter.

## <a id="elixir"></a> [Elixir](#elixir)

> Elixir is a dynamic, functional language designed for building scalable
> and maintainable applications.
>
> *From [elixir-lang.org](http://elixir-lang.org/)*

**[Spout](https://github.com/Stratus3D/spout)** is a ExUnit formatter that
generates TAP output for existing ExUnit test suites. Spout provides
a simple way to generate TAP output without having to modify existing
test code. Based on CTTAP.

## <a id="erlang"></a> [Erlang](#erlang)

> Erlang is a programming language used to build massively scalable soft
> real-time systems with requirements on high availability.
>
> *From [erlang.org](http://www.erlang.org/)*

**[CTTAP](https://github.com/Stratus3D/cttap)** is a Common Test hook that
generates TAP output for existing Common Test test suites. CTTAP provides
a simple way to generate TAP output without having to modify existing
test code.

**[etap](https://github.com/ngerakines/etap)** is a collection of Erlang
modules that provide a TAP testing client library. These modules are not
meant to compete with eunit, but to offer a more general testing facility
that isn't provided by eunit.

## <a id="fish"></a> [Fish](#fish)

> fish is a smart and user-friendly command line
shell for OS X, Linux, and the rest of the family.
>
> *From [fishshell.com](http://fishshell.com/)*

**[Fishtape](http://github.com/fisherman/fishtape)** is a TAP producer
and test harness for fish.

## <a id="forth"></a> [Forth](#forth)

> Forth is a computer language originally designed for embedded and
> real-time applications.
>
> *From [FORTH, Inc.](http://www.forth.com/forth/)*

Check out the [Testing with Forth](/testing-with-tap/forth.html) guide.

**[gforth-tap](https://github.com/AndyA/gforth-tap)** is a TAP producer
for Forth at an alpha level readiness.

## <a id="fortran"></a> [Fortran](#fortran)

> Fortran (formerly FORTRAN, derived from "Formula Translation")
> is a general-purpose, imperative programming language that is especially
> suited to numeric computation and scientific computing. Originally
> developed by IBM in the 1950s for scientific and engineering
> applications, Fortran came to dominate this area of programming early on
> and has been in continuous use for over half a century in computationally
> intensive areas such as numerical weather prediction, finite element
> analysis, computational fluid dynamics, computational physics,
> crystallography and computational chemistry. It is a popular language for
> high-performance computing and is used for programs that benchmark and
> rank the world's fastest supercomputers.
>
> Fortran encompasses a lineage of versions, each of which evolved to add
> extensions to the language while usually retaining compatibility with prior
> versions. Successive versions have added support for structured programming
> and processing of character-based data (FORTRAN 77), array programming,
> modular programming and generic programming (Fortran 90), high performance
> Fortran (Fortran 95), object-oriented programming (Fortran 2003) and
> concurrent programming (Fortran 2008).
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/Fortran)*

**[fortran-tap](https://github.com/gzahl/tap)** is a minimal producer implementation of the "Test Anything Protocol" (TAP) in Fortran 90 and the c preprocessor. Just copy two files to your project and start testing.

**[fortran-testanything](https://github.com/dennisdjensen/fortran-testanything)** is a basic TAP producer for Fortran
(standard 2008TS) with a minimal test harness implementing most of
the [Test::More](http://perldoc.perl.org/Test/More.html) API.

## <a id="gambas"></a> [Gambas](#gambas)

> Gambas is an open source programming language and rapid application development system (RAD)
> which empowers a programmer to create a great variety of programs:  From simple scripts and command line applications,
> server daemons up to large GUI aplications in Gambas Basic under Linux.
>
> *From [gambaswiki.org](http://gambaswiki.org/)*

**[gb.test](http://gambaswiki.org/wiki/comp/gb.test)** is a framework for unittesting which uses TAP as interface.

## <a id="go"></a> [Go](#go)

> Go is an open source programming language that makes it easy to build
> simple, reliable, and efficient software.
>
> *From [golang.org](https://golang.org/)*

**[tap.go](https://github.com/mndrix/tap.go)** is a basic TAP producer
for `testing/quick.Check` tests.

## <a id="haskell"></a> [Haskell](#haskell)

> Haskell is an advanced purely-functional programming language.
>
> *From [haskell.org](https://www.haskell.org/)*

**[TAP](https://github.com/epsilonhalbe/TAP)** is a TAP producer
that implements most of the
[Test::More](http://perldoc.perl.org/Test/More.html) API.

**[tasty-tap](https://github.com/michaelxavier/tasty-tap)** is a TAP producer
used with the [Tasty](http://documentup.com/feuerbach/tasty) Haskell
test framework.

## <a id="igorpro"></a> [Igor Pro](#igorpro)

> IGOR Pro is a scientific data analysis software, numerical computing
> environment and programming language.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/IGOR_Pro)*

**[Igor UTF](https://github.com/byte-physics/igor-unit-testing-framework)** is
a test harness and can output its results in TAP format.

## <a id="java"></a> [Java](#java)

> Java is a general-purpose computer programming language that is concurrent,
> class-based, object-oriented, and specifically designed to have as
> few implementation dependencies as possible.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/Java_%28programming_language%29)*

**[JTap](https://solucorp.solutions/repos/solucorp/JTap/trunk/)**
is a TAP library that implements most of the
[Test::More](http://perldoc.perl.org/Test/More.html) API.

**[tap4j](https://tupilabs.com/tap4j/tap4j/)** is a full featured TAP library which
is integrated at the core of other Java projects like the
[Jenkins TAP Plugin](https://wiki.jenkins-ci.org/display/JENKINS/TAP+Plugin).

## <a id="javascript"></a> [JavaScript](#javascript)

> JavaScript is a prototype-based, multi-paradigm, dynamic scripting language,
> supporting object-oriented, imperative, and functional programming styles.
>
> *From [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)*

**[AVA](https://github.com/sindresorhus/ava)** an asynchronous test framework
combining plans and tests and has an optional TAP reporter.

**[BaseT](https://github.com/Igmat/baset)** a test tool that implements Baseline Strategy (very close to snapshot testing) with TAP output ([tap diff](https://github.com/axross/tap-diff) is default reporter).

**[BusterJS](http://busterjs.org)** is a JavaScript testing toolkit for
both [Node.js][node] and browsers that comes with a
[TAP reporter](http://docs.busterjs.org/en/latest/overview/#reporters).

**[ESLint](https://github.com/eslint/eslint)** is a JavaScript linting tool
that runs on [Node.js][node] that has a TAP 'formatter'.

**[Mocha](http://mochajs.org/)** is a [Node.js][node] and browser testing
framework that has a [TAP reporter](http://mochajs.org/#tap).

[node]: https://nodejs.org

**[node](https://nodejs.org/docs/latest-v18.x/api/test.html#test-runner)** >= version 18 has an experimental *built-in* test runner which facilitates the creation of JavaScript tests that produce results in TAP format.

**[node-tap](https://github.com/isaacs/node-tap)** <span
class="badge">14</span> is a [Node.js][node] test framework and harness toolkit
that produces and consumes the TAP format.

**[Painless](https://github.com/taylorhakes/painless)** a modern, easy to use test library for [Node.js][node] and browsers that has an optional TAP reporter.

**[qunit-tap](https://github.com/twada/qunit-tap)** is a TAP output producer
plugin for [QUnit](http://qunitjs.com/).

**[tape](https://github.com/substack/tape)** is a TAP producing test harness
for [Node.js][node] and browsers.

**[testling](https://github.com/substack/testling)** runs unit tests in all
the browsers and outputs TAP.

**[Test.Simple](https://github.com/theory/test-simple-js)** is a TAP-emitting
JavaScript test framework.

**[zora](https://github.com/lorenzofox3/zora)** is a TAP producer with pure ES6 support for [Node.js][node] and browsers without babel.

## <a id="limbo"></a> [Limbo (OS Inferno)](#limbo)

> Limbo is the application programming language for Inferno.
> Syntactically similar to C, it has several features that make it simpler,
> safer and yet more powerful and better suited to the development
> of concurrent, distributed systems.
>
> *From [vita nuova](http://www.vitanuova.com/inferno/limbo.html)*

**[inferno-contrib-tap](https://github.com/powerman/inferno-contrib-tap)**
is a TAP producer that supports version 12.

## <a id="lua"></a> [Lua](#lua)

> Lua is a powerful, fast, lightweight, embeddable scripting language.
>
> *From [lua.org](http://www.lua.org/about.html)*

**[busted](https://lunarmodules.github.io/busted/)** is a unit testing framework
for Lua with a built-in TAP output handler.

**[lua-TestMore](http://fperrad.github.io/lua-TestMore/)** is
a port of the [Test::More](http://perldoc.perl.org/Test/More.html) framework
to Lua.

**[luatest](https://github.com/tarantool/luatest)** is
a test framework written in Lua.

## <a id="matlab"></a> [MATLAB](#matlab)

> MATLAB is a high-level language for numerical computation, visualization,
> and application development.
>
> *From [MathWorks](http://www.mathworks.com/products/matlab/features.html)*

**[TAPPlugin](http://www.mathworks.com/help/matlab/ref/matlab.unittest.plugins.tapplugin-class.html)**
is a plugin for the
[matlab.unittest](http://www.mathworks.com/help/matlab/matlab-unit-test-framework.html)
framework that produces output in the TAP version 12 format.

## <a id="ocaml"></a> [OCaml](#ocaml)

> OCaml is an industrial strength programming language supporting functional,
> imperative and object-oriented styles.
>
> *From [ocaml.org](https://ocaml.org/)*

**[TestSimple](https://github.com/hcarty/ocaml-testsimple)** is a simple
unit testing framework based on Perl's very successful Test::\* modules.

## <a id="omnis-studio"></a> [Omnis Studio](#omnis-studio)

> Omnis Studio is a powerful development environment that lets you deploy apps
> to virtually any device, on any platform, including tablets, smartphones,
> and desktop computers.
>
> *From [omnis.net](http://omnis.net)*

**[OmnisTAP](https://github.com/suransys/omnistap) is a TAP-compliant unit-testing
framework for Omnis Studio.

## <a id="pascal"></a> [Pascal](#pascal)

> Pascal is a historically influential imperative and procedural
> programming language, designed as a small and efficient language
> intended to encourage good programming practices using structured
> programming and data structuring.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/Pascal_%28programming_language%29)*

**[tap4pascal](http://sourceforge.net/projects/tap4pascal/)**
is a very easy-to-use, but powerful unit testing suite for Pascal
(FreePascal, Turbo Pascal, et al), conforming to the TAP specification.

**[pascal-tap](https://github.com/bbrtj/pascal-tap)**
is a simple toolkit for producing TAP output written in Object Pascal (fpc).

## <a id="perl5"></a> [Perl5](#perl5)

> Perl is a general-purpose programming language originally developed for
> text manipulation and now used for a wide range of tasks including
> system administration, web development, network programming,
> GUI development, and more.
>
> *From [perl.org](http://perldoc.perl.org/perlintro.html)*

**[Apache::Test](http://search.cpan.org/dist/Apache-Test/)** is a
[Test.pm](http://perldoc.perl.org/Test.html) wrapper with helpers for testing Apache.

**[Test::Builder](http://search.cpan.org/perldoc?Test::Builder)** is the
base test library that
[Test::More](http://perldoc.perl.org/Test/More.html) and
[Test::Simple](http://perldoc.perl.org/Test/Simple.html) are built upon.
It provides an API that these testing libraries use to output TAP.

**[Test.pm](http://search.cpan.org/dist/Test/lib/Test.pm)** is a Perl
library with an emphasis placed on simplicity.
There are more ambitious Perl modules out there, such as
[Test::More](http://perldoc.perl.org/Test/More.html) and
[Test::Unit](http://search.cpan.org/perldoc?Test%3A%3AUnit).

**[Test2 suite](https://metacpan.org/release/Test2-Suite)** is a faster and
richer Perl library written to replace the old test suite.
[Test::More](http://perldoc.perl.org/Test/More.html) was rewritten from scratch over it. See the [Chad Granum - "Better Testing with Test2-Suite"](https://www.youtube.com/watch?v=JsZw8P_PCUg) video from ["The Perl Conference 2019"](https://perlconference.us/tpc-2019-pit/).

## <a id="perl6"></a> [Perl6](#perl6)

> "In Perl 6, we decided it would be better to fix the language than fix the user."
> — Larry Wall

**[prove6](https://modules.perl6.org/dist/App::Prove6:cpan:LEONT/META6.json)** is the perl5 `prove` command. it is based on the [perl6 TAP library](https://modules.perl6.org/dist/TAP:cpan:LEONT). Both are maintained by [Leont](https://modules.perl6.org/search/?q=author%3A%22LEONT%22). There is also a [Test::Builder](https://github.com/perl6-community-modules/p6-test-builder) project by another author.

## <a id="php"></a> [PHP](#php)

> PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used
> open source general-purpose scripting language that is especially suited
> for web development and can be embedded into HTML.
>
> *From [php.net](https://secure.php.net/manual/en/intro-whatis.php)*

**[PHPUnit](http://www.phpunit.de/)** is a programmer-oriented testing
framework for PHP. It is an instance of the xUnit architecture for unit
testing frameworks and supports logging TAP.

**[Test.php](http://search.cpan.org/dist/Test.php/Test.php)** is a TAP test
framework for PHP with an interface like
[Test::More](http://perldoc.perl.org/Test/More.html).

**[testmore](https://github.com/shiflett/testmore)** is a TAP-compliant
PHP testing library based on
[Test::More](http://perldoc.perl.org/Test/More.html).

## <a id="prolog"></a> [Prolog](#prolog)

> Prolog is a general purpose logic programming language that
> has its roots in first-order logic, a formal logic, and unlike many
> other programming languages, Prolog is declarative: the program logic
> is expressed in terms of relations, represented as facts and rules.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/Prolog)*

**[library(tap)](https://github.com/mndrix/tap)** is a TAP library
written for [SWI-Prolog](http://www.swi-prolog.org/), but may work with
other Prologs.

## <a id="python"></a> [Python](#python)

> Python is an easy to learn, powerful programming language. It has efficient
> high-level data structures and a simple but effective approach to
> object-oriented programming.
>
> *From [python.org](https://docs.python.org/3/tutorial/index.html)*

**[Bayeux](https://pypi.python.org/pypi/bayeux/)** is a module for generating
fully decorated TAP from Python
(based on [yamlish](https://pypi.python.org/pypi/yamlish)).
It also includes a [`unittest`](https://docs.python.org/3/library/unittest.html)
module that produces a TAP stream instead of the normal output.

**[nose-tap](https://github.com/python-tap/nose-tap)**
is a plugin for [nose](http://nose.readthedocs.io/en/latest/) that outputs TAP.

**[PyTAP](https://github.com/rjbs/pytap)** is a port of
[Test::Simple](http://perldoc.perl.org/Test/Simple.html) to Python.

**[pytest-tap](https://github.com/python-tap/pytest-tap)**
is a plugin for [pytest](http://pytest.org/latest/) that outputs TAP.

**[tappy](http://tappy.readthedocs.org/en/latest/)**
provides tools for working with TAP in Python.
It includes a module to work with
[`unittest`](https://docs.python.org/3/library/unittest.html).

## <a id="ruby"></a> [Ruby](#ruby)

> Ruby is a dynamic, open source programming language with a focus on
> simplicity and productivity. It has an elegant syntax that is natural
> to read and easy to write.
>
> *From [ruby-lang.org](https://www.ruby-lang.org/en/)*

**[Bacon](http://github.com/chneukirchen/bacon)** is a small
[RSpec](http://rspec.info/) clone that supports TAP output.

**[RSpec TAP](https://github.com/appleton/rspec_tap)** is a formatter for [RSpec](http://rspec.info/) which outputs TAP.

## <a id="rust"></a> [Rust](#rust)

> Rust is a multi-paradigm system programming language focused on safety,
> especially safe concurrency. Rust is syntactically similar to C++,
> but is designed to provide better memory safety while maintaining high
> performance.
>
> *according to [wikipedia](https://en.wikipedia.org/wiki/Rust_(programming_language))*

[testanything](https://crates.io/crates/testanything) is a TAP producer for the
[Rust](http://rust-lang.org/) programming langage.

## <a id="sass"></a> [Sass](#sass)

> Sass is the most mature, stable, and powerful professional grade CSS
> extension language in the world.
>
> *From [sass-lang.com](http://sass-lang.com/)*

**[SCSS-Lint](https://github.com/brigade/scss-lint)** is a
configurable tool for writing clean and consistent
[SCSS](http://sass-lang.com) that supports TAP output.

## <a id="shell"></a> [Shell](#shell)

> A shell script is a computer program designed to be run by the Unix shell,
> a command line interpreter. The various dialects of shell scripts are
> considered to be scripting languages. Typical operations performed by
> shell scripts include file manipulation, program execution, and printing text.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/Shell_script)*

**[bash-tap-functions](https://github.com/goozbach/bash-tap-functions)**
is a TAP-producing Bash libary.

**[Bats](https://github.com/bats-core/bats-core)** is a TAP-compliant testing
framework for Bash. It provides a simple way to verify that the UNIX programs
you write behave as expected.

**[Git](https://github.com/git/git)** has code that supplies the
`ok` / `not ok` and skipping functionality. Look in `t/test-lib.sh` and
other test files for example code and use.

**[Sharness](https://github.com/mlafeldt/Sharness)** is a portable shell
library to write, run, and analyze automated tests for Unix programs.
Since all tests output TAP, they can be run with any TAP harness.

**[ShellSpec](https://github.com/shellspec/shellspec)** is a full-featured
BDD unit testing framework for dash, bash, ksh, zsh and all POSIX shells,
has a TAP formatter.

**[Tapper-autoreport](https://github.com/tapper/Tapper-autoreport)**
turns bash scripts into TAP test scripts.

**[tap.sh](https://github.com/dnmfarrell/tap.sh)** is a minimalist
POSIX-compliant shell library to write TAP tests.

**[uze TAP](https://github.com/zsh-uze/devel-tap)** is a [zsh](http://www.zsh.org)
library that provides helpers similar to the
[Test2 suite](https://metacpan.org/release/Test2-Suite).
This module is a part of the [uze](http://zsh-uze.github.io/) ecosystem.

**[ZTAP](https://github.com/mattmc3/ztap)** is a TAP producer and test harness for
[zsh](http://www.zsh.org).

## <a id="sql"></a> [SQL](#sql)

> SQL (Structured Query Language) is a special-purpose programming language
> designed for managing data held in a relational database management system
> (RDBMS).
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/SQL)*

**[db2unit](https://angoca.github.io/db2unit/)** is a unit testing framework
for SQL PL routines that runs in IBM
[DB2 LUW](http://www-01.ibm.com/software/data/db2/linux-unix-windows/) and
produces TAP version 13 output.

**[MyTAP](http://hepabolu.github.io/mytap/)** is a suite of database functions
that make it easy to write TAP-emitting unit tests in mysql scripts.

**[pgTAP](http://pgtap.org/)** is a suite of database functions
for [PostgreSQL](http://www.postgresql.org/) that make it easy to write
TAP-emitting unit tests in `psql` scripts or xUnit-style test functions.

**[PL/SQL TAP](http://use.perl.org/use.perl.org/_jdavidb/journal/30641.html)**
is a script for testing with Oracle's
[PL/SQL](http://www.oracle.com/technetwork/database/features/plsql/index.html)
procedural extension for SQL.

## <a id="typescript"></a> [TypeScript](#typescript)

> TypeScript is a free and open source programming language developed and
> maintained by Microsoft. It is a strict superset of JavaScript.
>
> *From [Wikipedia](https://en.wikipedia.org/wiki/TypeScript)*

**[alsatian](https://github.com/alsatian-test/alsatian)** is a unit testing
framework which supports test cases and outputs TAP output.

**[Testy.Ts](https://github.com/Testy/TestyTs)** is a modern TypeScript testing framework with a built-in TAP reporter.

**[TypeSpec](https://github.com/Steve-Fenton/TypeSpec)** is a BDD framework
for TypeScript with a built-in TapReporter class for TAP compliant output.

## <a id="frameworks"></a> [Test frameworks](#frameworks)

Some test frameworks solve problems that are not specific to a programming
language. These frameworks might be used for infrastructure or other kinds
of high level testing.

**[autotest](http://autotest.github.io/)** is a framework for fully automated
testing with the ability to produce TAP reports.

**[CMake](https://cmake.org/)** is an open-source, cross-platform family of
tools designed to build, test and package software. CMake tests produce TAP
output with option `-A`,
[added](https://github.com/Kitware/CMake/commit/3f6ff4b5dba01f2f58dca75546ebefd0830110a5)
since version 3.23.1.

**[Xperior](https://github.com/Xyratex/xperior)** is a system for testing
distributed filesystems. Xperior can output TAP test results.
