---
layout: default
title: TAP Philosophy
---

# TAP Philosophy

## Universal desirable behaviors for parsers

- Should work on the TAP as a stream (i.e. as each line is received)
  rather than wait until all the TAP is received.
- The TAP source should be pluggable (i.e. don't assume it's always
  coming from a Perl program).
- The TAP display should be pluggable.
- Should be able to gracefully handle future upgrades to TAP.
- Should be forward compatible.
  - Ignore unknown directives
  - Ignore any unparsable lines
