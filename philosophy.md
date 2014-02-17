---
layout: default
title: TAP Philosophy
---

# TAP Philosophy

##Universal desirable behaviors for parsers

These are behaviors desired in all TAP parsers:

-    Should work on the TAP as a stream (ie. as each line is received) rather than wait until all the TAP is received.
-    The TAP source should be pluggable (ie. don't assume its always coming from a Perl program).
-    The TAP display should be pluggable.
-    Should be able to gracefully handle future upgrades to TAP.
-    Should be forward compatible.
-    Ignore unknown directives
-    Ignore any unparsable lines
