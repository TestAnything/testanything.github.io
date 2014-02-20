---
layout: default
title: TAP Consumers
---

# TAP Consumers

Things that can take TAP as an input and do something useful with it.

## Perl

-    TAP::Parser
-    Test::Harness
-    Test::Run
-    [Smolder project background](http://sourceforge.net/projects/smolder/)
-    [TapTinder](http://dev.taptinder.org/wiki/TapTinder)
-    [metatap](http://search.cpan.org/search?query=metatap)

## Java

-    [tap4j](http://sourceforge.net/projects/tap4j/)

## JavaScript

-     [node-tap](https://github.com/isaacs/node-tap)

## Universal desirable behaviors

-    These are behaviors desired in all TAP parsers.
-    Should work on the TAP as a stream (ie. as each line is received) rather than wait until all the TAP is received.
-    The TAP source should be pluggable (ie. don't assume its always coming from a Perl program).
-    The TAP display should be pluggable.
-    Should be able to gracefully handle future upgrades to TAP.
-    Should be forward compatible.
     -     Ignore unknown directives
     -    Ignore any unparsable lines

### Non Proliferation

TAP producer authors should be aware of (and hopefully sign) the [TAP Namespace Nonproliferation Treaty](/namespace-nonproliferation-treaty.html)
