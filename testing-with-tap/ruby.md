---
layout: default
title: Testing with Ruby
---

# Testing with Ruby

Testing with Ruby is pretty easy, however, there is a lesser known Ruby program, that produces TAP output (on demand). This handy program is [bacon](http://github.com/chneukirchen/bacon/tree/master). You can install it using the RubyGems Ruby package management system. Just do (possibly as a privileged user):

```bash
$ gem install bacon
```

Now you can create tests. Create a Ruby file test.rb (or something like that):

```ruby
describe "a example test suite" do
  it "should consider true as the truth" do
    true.should.be.true
  end

  it "should consider false as the truth, too" do
    false.should.be.true
  end
end
```

Once you created your this file, you can issue the command

```bash
$ bacon test.rb --tap
```

which, in turn, produces the following TAP output (Version 12)

```
ok 1   - should consider true as the truth
not ok 2 - should consider false as the truth, too: FAILED
# Bacon::Error: false.true?() failed
# 	./test.rb:7: a example test suite - should consider false as the truth, too
# 	./test.rb:6
# 	./test.rb:1
1..2
# 2 tests, 2 assertions, 1 failures, 0 errors
```
