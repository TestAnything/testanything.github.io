---
layout: default
title: TAP History
---

# TAP History
The protocol has been around since 1988.

## TAP Namespace Nonproliferation Treaty

TAP has roots from the Perl programming language. Due to conficting namespaces
in that language, many Perl TAP authors signed a "nonproliferation treaty"
with the intent to reduce namespace conflicts.

The vast range of programming languages makes the treaty difficult to
enforce across the TAP ecosystem. The
[original treaty page](/namespace-nonproliferation-treaty.html)
is included on this history page for posterity.

## Historical Versions

Pulling apart the historical revisions of TAP is difficult both because there was no standard and because t/TEST in the perl core and Test::Harness parse slightly different dialects of TAP. Here's the best we can piece together right now. This information comes from Sam Villan's historical Perl GIT repository.

### Version 1

TAP as understood by Perl 1.0's t/TEST. It understands the basic 1..M header, "ok #" and "not ok #". No blank lines, directive, garbage lines or anything else is understood.
This is implemented by t/TEST as part of Perl 1.

```
commit 840163baa12f7970131f7841c479bccf5be40ba9
Author: Larry Wall <lwall@jpl-devvax.jpl.nasa.gov>
Date:   Sat Jan 30 23:00:00 1988 +0000
```

### Version 2

Checks the wait/exit status of each test.

Implemented by Test::Harness in Perl 5.002beta3

```
commit 4bce96efdcaa480e392138e10166c92c5fc5f22c
Author: Perl 5 Porters <perl5-porters@africa.nicoh.com>
Date:   Fri Feb 2 18:52:27 1996 -0800
```

### Version 3

Comment lines beginning with # are ignored.

```
Implemented by Test::Harness in Perl 5.002beta3
commit 4bce96efdcaa480e392138e10166c92c5fc5f22c
Author: Perl 5 Porters <perl5-porters@africa.nicoh.com>
Date:   Fri Feb 2 18:52:27 1996 -0800
```

### Version 4
Adds the "1..0" header for skipping the entire test. Previously it was considered a passing test.

This is first implemented by t/TEST as part of Perl 5.003_01 followed ten minutes later by Test::Harness.

```
commit 845b835a0bd51ac2f83e2e81f4088986d97114ff
Author: Perl 5 Porters <perl5-porters@africa.nicoh.com>
Date:   Mon Jul 8 23:11:22 1996 +0000
```

### Version 5
All non-TAP lines are ignored.
Implemented by Test::Harness in Perl 5.003_01.

```
commit ae85fcb6e790acc2343e92002216642e766aa196
Author: Perl 5 Porters <perl5-porters@africa.nicoh.com>
Date:   Mon Jul 8 23:22:00 1996 +0000
```

### Version 6
Support for the skip directive.
Added in Test::Harness and allow (but ignored) in t/TEST in Perl 5.004_55.

```
Change 318: Output skipped test information in test suite:
            Subject: 5.004_55: Making test harness platform_aware
            Date: Wed, 26 Nov 1997 17:16:55 -0500 (EST)
            Date: Wed, 26 Nov 1997 17:16:55 -0500 (EST)
```

### Version 7
In-header "todo" syntax added to Test::Harness in Perl 5.004_59.

```
Change 539: Subject: [PATCH 5.004_59] allow the Test::Harness to grok TODO-type tests docs
    Date: Sat, 14 Feb 1998 17:58:01 -0500
    From: Joshua Pritikin <pritikin@mindspring.com>
```

### Version 8
A reason is added to the skip directive.
Added in Test::Harness in Perl 5.005_53.

```
Change 3389: From: Ilya Zakharevich <ilya@math.ohio-state.edu>
            Date: Mon, 10 May 1999 02:07:01 -0400 (EDT)
            Message-Id: <199905100607.CAA26045@monk.mps.ohio-state.edu>
            Subject: [PATCH 5.005_53] Explanations by Test::Harness
```

### Version 9
A reason is added to the skip all header.

```
Change 3399: more testsuite smarts (many of them courtesy Ilya)
```

### Version 10
Added "Bail Out!"

```
Change 8028: Introduce macros for UTF8 decoding.
```

### Version 11
Added TODO directive.

```
Change 8824: Subject: [PATCH t/TEST lib/Test/Harness.pm] Adding todo tests
    From: schwern@pobox.com
    Date: Sun, 18 Feb 2001 01:48:50 -0500
    Message-ID: <20010218014850.C19957@magnonel.guild.net>
```

### Version 12
Allowed header at end.

Implemented in [Test::Harness](http://search.cpan.org/dist/Test-Harness/) 1.21.

### Version 13
Understands TAP version syntax.

Implemented in [TAP::Parser](http://search.cpan.org/dist/Test-Harness/lib/TAP/Parser.pm) 0.52.

### Version 14 (Current version)
Adds subtest test syntax.

More precise specification of harness behavior across language runtimes.
