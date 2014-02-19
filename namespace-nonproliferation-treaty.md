---
layout: default
title: TAP Namespace Nonproliferation Treaty
---

# TAP Namespace Nonproliferation Treaty
This proposal originates in Perl world where the module naming scheme can result in congestion around 'obvious' module names. While not directly applicable to other languages you should, of course, consider the namespace impact of whatever name you choose regardless of language. What follows is Perl specific.
To avoid one Perl module grabbing all the "juicy" names in the TAP namespace (for example, TAP::Parser, TAP::Grammar and TAP.pm) I propose that we all avoid taking them. This avoids the sort of problem CGI.pm caused in the CGI namespace. Signatories should claim a single namespace at the top level (for example, TAP::Harness) and place their sub-classes under that (ex. TAP::Harness::Parser).
This is inspired by article 4 of the [Antarctic Treaty System](http://en.wikipedia.org/wiki/Antarctic_Treaty_System).
Article 4 - does not recognize, dispute, or establish territorial claims and no new claims shall be asserted while the treaty is in force.

## A list of prohibited names

This is a non-exclusive list.

-    TAP::Grammar
-    TAP::Lexer
-    TAP::Source

## List of reserved names

The following names are reserved by the signatories for their modules.

**TAP**
    Andy Lester has reserved TAP.pm for future use as the documentation of TAP.
**TAP::Harness**
    Schwern has reserved TAP::Harness.

## List of signatories

-    Schwern 15:01, 7 July 2006 (PDT)
-    Andy Lester 7 July 2006
-    Michael Peters 7 July 2006
-    Adrian Howard 8 July 2006
-    Adam Kennedy
-    Curtis "Ovid" Poe 8 July 2006
-    AndyArmstrong 22:25, 19 March 2007 (GMT)
-    Jeremiah Foster 15:35, 14 March 2008 (CET)
-    David E. Wheeler 18:17, 30 July 2008 (UTC)
-    Brendon Robinson 20:11, 20 January 2010 (EST)

## Alternatives and Enforcement

While a voluntary treaty is fine, there does exist a convention for reserving namespaces, for example DBI:: and PPI:: which are both off limits to non-"official" modules merely by declaration.
Speaking in the capacity of the most junior of the PAUSE admins, given that the TAP namespace has remained unused for so long, and that Andy owns TAP.pm, I would be reasonably happy to have TAP:: as a reserved-by-convention namespace, with modules to be blessed by Andy, and third-party experimental modules welcome in TAPx::
Brian or Andreas may have alternate opinions though...
--Adam Kennedy