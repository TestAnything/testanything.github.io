---
layout: default
title: TAP 13 specification
---


TAP at IETF: Draft Standard
Please see the Implementation section on how to work on this document.
Important note: This spec is still being worked on, and should not be considered the final draft specification for TAPv13. At the moment, the only absolute TAP standard is the codebase for Test::Harness. If you use this spec to implement TAPv13, please do let us know if you observe any discrepancy between this spec and the Test::Harness library on the mailing list, or edit this document yourself.

## Current outstanding points

Work in progress! Please ignore any obvious mistakes, and jump in and fix anything you like. Be bold!
Whitespace: single spaces, or any number of spaces between elements?
Multiline test descriptions: how do we allow TAP producers to return test descriptions with newlines in them?
An escape sequence for putting hashes into the description: is \# good enough?
Discussions are ongoing on the talk page and on the mailing list.

## Prologue

### Expiration date

To be inserted (185 days after posting)

### Authors
Gaurav Vaidya
Michael G Schwern

### Title
The Test Anything Protocol (TAP)
draft-vaidya-test-anything-protocol-00

### Feedback and comments
Comments are solicited and should be addressed to the mailing list at tap@ietf.org and/or the author(s).

### Boilerplate
By submitting this Internet-Draft, each author represents that any applicable patent or other IPR claims of which he or she is aware have been or will be disclosed, and any of which he or she becomes aware will be disclosed, in accordance with Section 6 of BCP 79.
Internet-Drafts are working documents of the Internet Engineering Task Force (IETF), its areas, and its working groups. Note that other groups may also distribute working documents as Internet-Drafts.
Internet-Drafts are draft documents valid for a maximum of six months and may be updated, replaced, or obsoleted by other documents at any time. It is inappropriate to use Internet-Drafts as reference material or to cite them other than as "work in progress."
The list of current Internet-Drafts can be accessed at http://www.ietf.org/1id-abstracts.html
The list of Internet-Draft Shadow Directories can be accessed at http://www.ietf.org/shadow.html

## Abstract

The Test Anything Protocol (TAP) is a protocol to allow communication between unit tests and a test harness. It allows individual unit tests (TAP producers) to communicate test results to the testing harness in a language-agnostic manner. Tests can indicate success or failure, mark tests as unimplemented or skipped, and provide additional information to help debug failed tests. Unlike other testing systems, it can also indicate missing tests and duplicated tests.
This specification defines TAP version 13.

## Introduction

The Test Anything Protocol (TAP) describes a standard format for testing suites to use. This format provides both human and machine-readable information on which tests were run, whether they were successful or failed, as well as other information which might be useful in tracing the cause of the failure. Being machine-readable allows this information to be easily parsed by an automated testing harness. Test results may then be summarized and analyzed. Being human-readable allows the results of a testing system to be read manually; this is useful for quickly determining whether individual tests pass and to aid in debugging the test system itself.
TAP has been in use since 1987 by Perl. The format is very stable, and capable of providing data on failed tests to help in debugging.

### Conventions Used In This Document
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC2119].
The grammatical rules in this document are following ABNF and are to be interpreted as described in [STD68].

## Definitions

-    A **test** is a piece of software which determines if a particular facility or component is functional.
-    A **test result** is the encoding in TAP of the result of a single test. It may have exactly one TAP result directive.
-    A **test set** consists of zero or more test results and exactly one plan. A test set can be determined to have failed or passed.
-    A **test suite** is a collection of test sets.
-    A **TAP stream** consists of one test set which parses correctly as defined in this document. Future expansion may allow multiple test sets to be contained in a single TAP stream, allowing an entire test suite to be stored as a single TAP stream.
-    A **plan** is the number of tests which are expected to pass in a single test set.
-    A **directive** changes the meaning of a test result; it is commonly used to indicate that a failing test should be reported as passing (TODO) or that a passing test should be tagged as suspicious (SKIP).
-    A **reason** explains why a directive was necessary.
-    A **description** says what a test result is testing.
-    A **producer** is a thing which can generate a valid TAP stream.
-    A **consumer** is a thing which can parse and interpret a TAP stream.
-    A **filter** a piece of software which consumes a TAP stream, and produces a new TAP stream based in some way on the TAP input. For example, it can reproduce the TAP stream exactly, normalize the formatting, combine multiple streams, or summarize the result of tests as a new TAP stream.

## Producers and consumers

A TAP stream might exist as a file, data stream, encoded in another medium (stored in a PDF file, for instance) or in any other form which can be parsed as described below. For maximum compatibility, it may be produced by any TAP producer, and must then be consumable by any TAP consumer.
One example system of producers and consumers is the Test::More/Test::Harness system in Perl testing. In this system, test producers are executable Perl scripts with a '.t' extension, collected in a number of folders, which themselves use the Test::More library to simplify testing. These scripts can be executed individually, and emit TAP streams on standard output.
A TAP consumer, such as the Perl module TAP::Parser, can interpret the output of a TAP producer to determine how many tests were run, which tests succeeded, and which diagnostic information might be usefully reported to the user.
Note that these two processes are often decoupled. The TAP stream emitted by the TAP producer can be stored before being interpreted by the TAP parser; this allows all diagnostic and testing information to be stored for later analysis and usage. The TAP stream might be generated on one server, then downloaded to another before being processed. A single TAP parser can be used to process files in all these cases, illustrating TAP's utility as a cross-language, cross-environment tool.
The complete flow in this system can look something like this:

```
 ------------
 | Producer |
 ------------
     |
     V
 --------------        -----------           --------------------
 | TAP stream | --+--> | Storage |      +--> | Formatted Output |
 --------------   |    -----------      |    --------------------
                  |         |           |
                  |         V           |
                  |    --------------   |    --------------------
                  +--> | TAP parser |---+--> | Test summaries   |
                       --------------        --------------------
```

Additionally, utilities like "prove" can further simplify running a suite of TAP producers, by searching for files having certain characteristics or matching particular patterns. For instance, conventionally, all tests for a Perl module are stored in the 't/' folder, and consist of executable scripts (TAP producers) with extensions of 't'. The "prove" utility, part of the Test::Harness module, can then be used to find these files and run them all. In the following example, prove executes t/error.t, t/id.t and t/url.t and evaluates the produced TAP streams in turn, checking which ones passed and failed, and providing a complete summary of the entire test suite run.

```
$ prove t/*.t
t/error.t...ok   
t/id.t......ok    
t/url.t.....ok
Result: PASS
```

### The Structure Of A TAP Stream

A TAP stream is split into lines, typically separated by some combination of the characters CARRIAGE RETURN (#xD) and LINE FEED (#xA). All TAP consumers MUST behave as if it normalized all line breaks in the TAP stream, before parsing, by translating both the two-character sequence #xD #xA and any #xD that is not followed by #xA to a single #xA character.

-    This suggestion from [http://www.w3.org/TR/REC-xml/](http://www.w3.org/TR/REC-xml/) section 2.11.

A TAP test set consists of one version, one plan, zero or more test results, and any number of comments and ignored elements. Any line beginning with the letters 'ok' or 'not ok' is a test result. All unparsable lines must be ignored by TAP consumers.
Free-form strings in TAP, such as reasons and descriptions, must be in UTF8 unless the interchange parties agree otherwise. Strings MUST NOT contain an EOL or NUL character. Since directives start with a "#" and come after a description, descriptions MUST NOT contain a "#".

*Rationale*: This is expressed in the grammar below as a Safe-String without "#" and a more general String with "#".

But we need an escape system to have a #

This whole section is repeating the grammar but leaving out important details.

### Version

Every test set as defined in this document should contain a version definition. A test set without a version definition is assumed to be written in TAP version 12, which is not covered by this document.

### Plan

Every test set should contain one and only one plan. A test set containing multiple plans can be parsed as a TAP stream, but will be judged to have failed.

### Test results

A test result reports the status of one single test. The test must summarize itself as passing ("ok") or failing ("not ok"), and must have a test number. A test result without an explicit test number will be assumed to have the next number in increasing numeric sequence from the start of the test set. A test result can also have a description and a directive, which modifies the meaning of the test, but both are optional.
Test results must be present in the correct order, without missing tests or duplicate test numbers, for the test set to be judged to pass.

### Bail Out

A Bail-Out line indicates a gross failure in the TAP producer. Results from this test set can no longer be trusted. The TAP consumer should ignore the rest of the TAP syntax and may terminate the TAP producer if it can do so safely. If processing multiple files, the TAP consumer should stop processing other files which are part of the same test suite.

### Comments

Comments are lines which have no meaning in TAP. They do not alter the result of a test. A TAP stream with and without comments has exactly the same meaning.
Comments typically contain debugging information. TAP consumers should not display comments by default, as there will likely be a large number of tests in such a suite.
Note that TAP does not provide a mechanism for comments to be associated with particular test results; for instance, comments of a general nature might be interspersed with comments specific to a particular test.

### Ignored elements

In order to allow extension of the protocol while maintaining backwards compatibility, a TAP consumer must ignore certain lines and elements. Any line which does not parse must be ignored. Any directive or plan-directive which is not recognized must also be ignored.
Here's an example of a TAP stream which contains ignored elements.

```
   1..2
   Error at line 12
   ok 1
   ok 2 # BANG
```

Line 2 should be ignored, it does not parse. The directive "BANG" on test #2 should be treated as an ordinary comment, it is not a TAP directive.

## Grammar

The test set is defined below using Augmented Backus-Naur Form (ABNF), as defined in [STD68]. Note that double-quoted strings in ABNF are always case-insensitive.

```
   ; Overall structure
   Testset         = Header (Plan Body / Body Plan) Footer
   Header          = [Comments] [Version]
   Footer          = [Comments]
   Body            = *(Comment / TAP-Line)
   TAP-Line        = Test-Result / Bail-Out
   
   ; TAP version
   Version         = "TAP version" SP Version-Number EOL ; ie. "TAP version 13"
   Version-Number  = Positive-Integer
   
   ; Plan
   Plan            = ( Plan-Simple / Plan-Todo / Plan-Skip-All ) EOL
   Plan-Simple     = "1.." Number-Of-Tests
   Plan-Todo       = Plan-Simple "todo" 1*(SP Test-Number) ";"  ; Obsolete
   Plan-Skip-All   = "1..0" SP "skip" SP Reason
   Reason          = String
   Number-Of-Tests = 1*DIGIT               ; The number of tests contained in this stream
   Test-Number     = Positive-Integer      ; The sequence of a test result
   
   ; Test result
   Test-Result     = Status [SP Test-Number] [SP Description]
                      [SP "#" SP Directive [SP Reason]] EOL
   Status          = "ok" / "not ok"       ; Whether the test succeeded or failed
   Description     = Safe-String           ; A description of this test.
   Directive       = "SKIP" / "TODO"
   
   ; Bail out
   Bail-Out        = "Bail out!" [SP Reason] EOL
   
   ; Comments
   Comment         = "#" String EOL
   Comments        = 1*Comment
   
   ; Values
   EOL              = LF / CRLF             ; Specific to the system producing the stream
   Safe-String      = 1*(%x01-09 %x0B-0C %x0E-22 %x24-FF)  ; UTF8 without EOL or "#"
   String           = 1*(Safe-String / "#")                ; UTF8 without EOL
   Positive-Integer = ("1" / "2" / "3" / "4" / "5" / "6" / "7" / "8" / "9") *DIGIT
```

A stream must parse as per the grammar above to qualify as a TAP stream. The grammar presented below may be used by TAP consumers to ensure that a test set contains all the required parts.

```
   ; Overall structure
   Passing-Testset = Header
                     (Plan-With-Tests Passing-Body / Passing-Body Plan-With-Tests / Plan-Skip-All)
                     Footer
   Passing-Body    = [Comments] 1*Passing-Line *(Passing-Line / Comment) [Comments]
   Passing-Line    = (Simple-OK / Passing-TODO / Failing-TODO / Passing-SKIP) EOL
   Failing-Line    = (Simple-Fail / Failing-SKIP) EOL
   
   ; Plans that must have tests
   Plan-With-Tests = ( Plan-Simple / Plan-Todo )
   
   ; Passing and failing test lines
   Simple-OK       = "ok" [SP Test-Number] [SP Description]        ; pass
   Simple-Fail     = "not ok" [SP Test-Number] [SP Description]    ; fail
   Passing-TODO    = Simple-OK   SP TODO-Directive                 ; pass (with warning)
   Failing-TODO    = Simple-Fail SP TODO-Directive                 ; pass
   Passing-SKIP    = Simple-OK   SP SKIP-Directive                 ; pass
   Failing-SKIP    = Simple-Fail SP SKIP-Directive                 ; fail (with warning)
   TODO-Directive  = "# TODO" [SP Reason]
   SKIP-Directive  = "# SKIP" [SP Reason]
```

## Passing and Failing

Both test sets and test results can be determined to have passed or failed as detailed below. Note that a test set might fail even if every single test result contained in it passes.

### Test results

A test result indicates whether the test it reports has passed ("ok") or failed ("not ok"). It is itself said to pass or fail, depending on the result of the underlying test and on any directives applied to that result. It can be modified with any of the directives listed below. The table below summarises how directives can change a test result.
No directives	 `TODO`	 `SKIP`
ok	 pass	 pass (optionally with warning)	 pass
not ok	 fail	 pass	 fail (with warning)
Except in the cases indicated, it is left to TAP consumers whether the presence of directives are reported.

### The `SKIP` directive
This directive indicates that the test was not begun. Usually this is caused by environmental reasons: a missing optional library, an operating system specific test, or an expensive test that is only run on request.
Since the test was skipped, the test result is expected to be "ok" (indicating that the test was skipped correctly). A skipped test with a result of "not ok" is suspicious, and the TAP consumer should report a warning.

### The `TODO` directive
This directive indicates that the test was run, but failure is expected and should not cause the test set to fail. This is usually because the functionality being tested has not yet been implemented.
This directive allows testing for functionality which has not been completely implemented or is obstructed by a known bug. Such tests can be marked as "TODO", signaling to the TAP consumer that this test is expected to fail. In this way, a "TODO" test becomes an executable bug tracker. Known, unresolved issues are silently ignored, allowing the rest of the test suite to pass.
Neither a failing nor a passing TODO test will cause the test set to fail, but since passing TODOs are suspicious, they may optionally be reported by TAP consumers.

### Plan
The plan indicates the number of tests which are expected to be run in the current test set. Two types of plans are defined, with different requirements for passing:
A simple plan: the number of expected tests must be a positive integer. In order for a test set with a simple plan to pass, it must contain exactly the number of test results indicated in the plan, in ascending numeric order, without either any gaps in test number or any duplicate tests. Every test result must pass.
A skip-all plan: the number of expected tests is zero. A test set with a skip-all plan passes unless it contains any test results.
Allowing simple plans to plan for zero tests is being considered, but is not a part of this specification.

### Other factors
TAP consumers may use any other system-specific factors to determine whether a test set passes or fails. If such a failure is to be reported, it MUST inform the user of the state of the TAP parsing and whether all tests appear to have passed, and then must separately describe the nature of the system-specific failure which caused the consumer to become suspicious of the results.
TAP consumers which also act as TAP producers could add additional test results to the end of the output TAP stream if such a failure occurs. For instance, take a TAP producer which emits ten successful tests, then throws an exception and exits with a failure. A filter might add a new (11th) failing ("not ok") test result to the end of the TAP it emits, which informs the user of the exception or failure exit code. Note that such a test result would cause the test set to fail; unless the test set planned one more test than it emitted, the number of tests would not equal the number of tests planned; even if it did this, this 11th failing test would cause the test set to fail.
An example of the use of this option is to check exit codes of TAP producers for a failure, which might indicate that the producer failed after having emitted a complete TAP stream. It seems unpragmatic to ignore such exit codes, but this information cannot be reliably expressed into its own TAP output by a failing producer, and must be treated separately. This also allows for language-specific and system-specific features to be used by the TAP consumer at its discretion to improve the rigour of its testing.

## Security considerations

See [RFC 3552](http://www.apps.ietf.org/rfc/rfc3552.html) for tips on how to write this section.
Problems with parsing debugging status?
A parser which stores test results in a dynamically sized array may be vulnerable to memory starvation by a test which uses a very high test number. For example...

```
  1..3
  ok 1
  ok 2
  ok 123456789
```

Would cause an array of 123456789 elements to be allocated. So it is recommended that test results, if stored at all, are stored in a sparse array.

## IANA considerations

-    *Comment: blantantly nicked from [RFC 4627](http://www.faqs.org/rfcs/rfc4627.html), so we should recheck this section. Registration of MIME types is described in [RFC4288](http://www.faqs.org/rfcs/rfc4288.html) and [RFC4289](http://www.faqs.org/rfcs/rfc4289.html).*

The MIME media type for TAP is application/tap.
Type name: application
Subtype name: tap
Required parameters: n/a
Optional parameters: n/a
Encoding considerations: 8bit if UTF-8; binary if UTF-16 or UTF-32
TAP may be represented using UTF-8, UTF-16, or UTF-32. When TAP is written in UTF-8, TAP is 8bit compatible. When TAP iswritten in UTF-16 or UTF-32, the binary content-transfer-encoding must be used.
Security considerations:
Interoperability considerations: n/a
Published specification: TODO: insert once we have a spec (i.e. this document)
Applications that use this media type: Perl's test system (including the core Test::More and Test::Harness modules), Perl testing modules such as Test::Most and Test::Class, applications which store and summarize test results such as Smolder, and testing suites in other systems, including pgTAP and
Additional information:
Magic number(s): "TAP version" in the encoding used.
File extension(s): .tap
Macintosh file type code(s): TEXT
Person & email address to contact for further information: TODO (Can we get TPF to monitor this?)
Intended usage: COMMON
Restrictions on usage: none
Author: TODO
Change controller: TODO

## Acknowledgements

This document is based on Andy Armstrong's description of the TAP protocol, version 13, which is itself based on Andy Lester's description of the TAP protocol, version 1.00. The basis for the TAP format was created by Larry Wall in the original test script for Perl 1. Tim Bunce and Andreas Koenig developed it further with their modifications to the Test::Harness module.

## References

## Normative references

-    [STD68]: Crocker, D., and Overel, P. "Augmented BNF for Syntax Specifications: ABNF", RFC5234, January 2008.
-    [RFC2119]: Bradner, S. "Key words for use in RFCs to Indicate Requirement Levels", RFC2119, March 1997.

## Informative references

None

## Author's address

-    Gaurav Vaidya
-    Michael G Schwern

## IPR disclosure

By submitting this Internet-Draft, each author represents that any applicable patent or other IPR claims of which he or she is aware have been or will be disclosed, and any of which he or she becomes aware will be disclosed, in accordance with Section 6 of BCP 79.

## IPR disclaimer

The IETF takes no position regarding the validity or scope of any Intellectual Property Rights or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; nor does it represent that it has made any independent effort to identify any such rights. Information on the procedures with respect to rights in RFC documents can be found in BCP 78 and BCP 79.
Copies of IPR disclosures made to the IETF Secretariat and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this specification can be obtained from the IETF on-line IPR repository at [http://www.ietf.org/ipr](http://www.ietf.org/ipr).
The IETF invites any interested party to bring to its attention any copyrights, patents or patent applications, or other proprietary rights that may cover technology that may be required to implement this standard. Please address the information to the IETF at ietf-ipr@ietf.org.

## Copyright notice and disclaimer

Copyright (C) The IETF Trust (2009).
This document is subject to the rights, licenses and restrictions contained in BCP 78, and except as set forth therein, the authors retain all their rights.
This document and the information contained herein are provided on an "AS IS" basis and THE CONTRIBUTOR, THE ORGANIZATION HE/SHE REPRESENTS OR IS SPONSORED BY (IF ANY), THE INTERNET SOCIETY, THE IETF TRUST AND THE INTERNET ENGINEERING TASK FORCE DISCLAIM ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.

## Implementation notes

The IETF [strongly recommends](http://www.ietf.org/ID-Checklist.html) that [xml2rfc](http://xml.resource.org/) is used to ensure that Internet-Drafts are formatted exactly as required. I've converted a previous version of this page into XML; you can get this version in [my GitHub account](http://github.com/gaurav/test-anything-protocol/blob/master/draft-vaidya-test-anything-protocol-00.xml).

-    [The Tao of IETF](http://www.ietf.org/tao.html) (if you don't have any experience with IETF procedures and/or meetings)
-    [Guidelines to Authors of Internet-Drafts](http://www.ietf.org/ietf/1id-guidelines.html)
-    [Internet-Drafts checklist](http://www.ietf.org/ID-Checklist.html)
-    [RFC Editorial Guidelines and Procedures](http://www.rfc-editor.org/policy.html)

## Other TAP specifications

-    [TAP specification](/tap-specification.html)
-    [TAP version 13 specification](/tap-version-13-specification.html)
