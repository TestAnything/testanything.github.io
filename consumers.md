---
layout: default
title: TAP Consumers
---

# TAP Consumers

Things that can take TAP as an input and do something useful with it.

## Perl

-    [TAP::Parser](http://search.cpan.org/~markwkm/Test-Parser-1.9/lib/Test/Parser.pm)
-    [Test::Harness](http://search.cpan.org/~leont/Test-Harness-3.30/lib/Test/Harness.pm)
-    [Test::Run](http://search.cpan.org/~shlomif/Test-Run-0.0302/lib/Test/Run.pm)
-    [Smolder project background](http://sourceforge.net/projects/smolder/)
-    [TapTinder](http://dev.taptinder.org/wiki/TapTinder)
-    [metatap](http://search.cpan.org/search?query=metatap)

## Java

-    [tap4j](http://sourceforge.net/projects/tap4j/)

## JavaScript

-    [node-tap](https://github.com/isaacs/node-tap)
-    [TAP parser](https://www.npmjs.org/package/tap-parser)

## C

-    [C Tap Harness](http://www.eyrie.org/~eagle/software/c-tap-harness/)

## Others

-    [Jenkins TAP Plugin](https://wiki.jenkins-ci.org/display/JENKINS/TAP+Plugin)

## Universal desirable behaviors

-    These are behaviors desired in all TAP parsers.
-    Should work on the TAP as a stream (ie. as each line is received) rather than wait until all the TAP is received.
-    The TAP source should be pluggable (ie. don't assume its always coming from a Perl program).
-    The TAP display should be pluggable.
-    Should be able to gracefully handle future upgrades to TAP.
-    Should be forward compatible.
     -    Ignore unknown directives
     -    Ignore any unparsable lines

### Non Proliferation

TAP producer authors should be aware of (and hopefully sign) the [TAP Namespace Nonproliferation Treaty](/namespace-nonproliferation-treaty.html)
