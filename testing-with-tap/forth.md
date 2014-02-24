---
layout: default
title: Testing with Forth
---

# Testing with Forth

Disclaimer: The purpose of this article is to demonstrate how easy it is to start using TAP with a particular language. It is not supposed to represent Forth best practice. I'm a Forth beginner in the sense that I haven't used the language for twenty years and even then I was, at best, an intermediate Forth programmer --AndyArmstrong

## TAP in your language

You're working with a language that isn't currently supported by TAP and you'd like to start writing TAP based tests. All you need to get started is some simple code to output

-    a plan
-    a test result ('ok' or 'not ok')

That's it. As your testing regime develops you'll want to add more sugar but that's enough to get started.

## A sample TAP implementation in Forth

You may not be familiar with [Forth](https://en.wikipedia.org/wiki/Forth_(programming_language)). It's a stack based language with syntax that can get pretty obscure. Our initial TAP portable generators in Forth will consist of just eleven lines of code so even if the reverse polish notation looks odd you should be able to see that the task is pretty simple.

### The plan

It's recommended that whenever possible your TAP should start with a plan. The plan says how many tests are expected to run and looks like this:

```
 1..10
```

The plan always takes the form 1..*number* of tests.
In Forth we can output a plan like this:

```
 ." 1..10" cr
```

Or you can define the word plan like this:

```
 : plan ( n -- )
     ." 1.." . cr
 ;
```

and use it like this:

```
 10 plan
```

### Test results

The general form of a test result is either

```
 ok test-number description
```

or

```
 not ok test-number description
```

The description is optional so we'll omit it for now and concentrate on generating results that a TAP parser can process.
We need a variable to hold the number of the next test. In Forth that looks like this:

```
 Variable test# 
 0 test# !
```

And we need something to output the result:

```
 : ok ( f -- )
 	0= if ." not " then
 	." ok "
 	test# dup @ 1+ dup . swap !
 	cr
 ;
```

Now we have a word called ok which checks the top value on the stack and outputs 'ok' or 'not ok' depending on whether it's true (non-zero) or false (zero). With that we have everything necessary to start TAP based testing.


### A sample test script

Here's a simple test of addition and subtraction using the words we just defined:

```
 #! /usr/local/bin/gforth
 
 require tap.fs
 
 2 plan
 1 1 + 2 = ok
 2 1 - 1 = ok
 
 bye
```

It assumes that we saved our TAP generating code in a file called tap.fs. When run it will output

```
 1..2
 ok 1
 ok 2
```

### Analysing the results

If you have the Perl prove utility (which is part of [Test::Harness](http://search.cpan.org/dist/Test-Harness/) you can use it to run this test script and analyse the results:

```
 $ prove -v simple.fs
 t/simple...1..2 
 ok 1 
 ok 2 
 ok
 All tests successful.
 Files=1, Tests=2,  0 wallclock secs ( 0.01 cusr +  0.02 csys =  0.03 CPU)
```

#### Get the code

Here's a slightly extended version of the code in this article:

[forth-tap-0.0.1.tar.gz](/assets/forth-tap-0.0.1.tar.gz)

You'll need [GNU Forth](http://www.gnu.org/software/gforth) and Perl installed to run it.