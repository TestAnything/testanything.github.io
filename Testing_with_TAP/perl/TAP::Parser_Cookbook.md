---
layout: default
title: TAP::Parser Cookbook
---

Share your TAP::Parser tips, recipes.

I use TAP::Parser to schedule a bunch of scripts that run tests against a cluster. Here is my code:

```perl
#!/usr/bin/perl -w

# Name:          run_all.pl
# Purpose:       A test scheduler and runner

use strict;
use POSIX qw/strftime/;
use TAP::Parser qw/all/;
use TAP::Parser::Aggregator qw/all/;

open my $out_file, ">>", "/usr/lib/cgi-bin/test_cases/test_reports/test_report.txt"
  or die "Cannot open outfile. $!\n";
printf $out_file "\n---\nReport %s\n---\n", strftime("%y%m%d-%H:%M", localtime);

my @files = qw[
               /usr/lib/cgi-bin/test_cases/007.07.pl
               /usr/lib/cgi-bin/test_cases/007.08.pl
               /usr/lib/cgi-bin/test_cases/002.1.sh
               /usr/lib/cgi-bin/test_cases/002.2.sh
               /usr/lib/cgi-bin/test_cases/007.01.pl
               /usr/lib/cgi-bin/test_cases/007.10.pl
               /usr/lib/cgi-bin/test_cases/011.04.pl
               /usr/lib/cgi-bin/test_cases/011.06.pl
               /usr/lib/cgi-bin/test_cases/011.07.pl
               /usr/lib/cgi-bin/test_cases/011.08.pl
               /usr/lib/cgi-bin/test_cases/101.03.sh
               /usr/lib/cgi-bin/test_cases/101.05.sh
               /usr/lib/cgi-bin/test_cases/101.04.pl
               /usr/lib/cgi-bin/test_cases/007.03.pl
               /usr/lib/cgi-bin/test_cases/201.3.pl
               /usr/lib/cgi-bin/test_cases/003.3.pl
               ];

foreach my $file (@files) {
  my $parser = TAP::Parser->new( { source => $file } );
  while ( my $result = $parser->next ) {
    print $out_file "$file results: $result->as_string\n";
  }
  my $aggregate = TAP::Parser::Aggregator->new;
  $aggregate->add( 'testcases', $parser );
  printf $out_file "\n\tPassed: %s\n\tFailed: %s\n", scalar $aggregate->passed, scalar $aggregate->failed;
}
```

It is pretty straightforward, or at least I hope so. What it does is create an out file which will be the place where the output from TAP shows up. Then I create an array of files to run, these are my tests. As you can see from the suffixes, some are shell code, some are perl - there are even some Expect scripts as well but they are not listed here. Instead the Expect scripts get called directly from the perl or shell scripts.
In the foreach loop I run each test and then create a new TAP::Parser::Aggregator object to let me know the totals of tests that passed and failed.
