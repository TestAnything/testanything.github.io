---
layout: default
title: Main Page
---

# Test Anything Protocol

TAP, the Test Anything Protocol, is a simple text-based interface between testing modules in a test harness. TAP started life as part of the test harness for Perl but now has implementations in C, C++, Python, PHP, Perl, Java, JavaScript, and others.

Here's what a TAP test stream looks like:

```
 1..4
 ok 1 - Input file opened
 not ok 2 - First line of the input valid
 ok 3 - Read the rest of the file
 not ok 4 - Summarized correctly # TODO Not written yet
```

## Testing with TAP

-    [Testing with TAP](/Testing_with_TAP) - How to run TAP based tests in your language of choice


## TAP Development

{% comment %}
TODO review needed - might be worth moving to github issues and involving individual content owners
     <li><a href="http://testanything.org/wiki/index.php/TAP_Proposals" title="TAP Proposals">TAP Proposals</a> - What next?</li>
{% endcomment %}

-    [TAP Producers](/producers.html) - Testing tools that generate TAP output
-    [TAP Consumers](/consumers.html) - Test harnesses that read TAP
-    [TAP Philosophy](/philosophy.html) - The Tao of TAP
-    [TAP History](/history.html) - The story of TAP

{% comment %}
TODO review needed
    <li><a href="http://testanything.org/wiki/index.php/TAP_Critique" title="TAP Critique">TAP Critique</a> - Design infelicities</li>
    <li><a href="http://testanything.org/wiki/index.php/YAMLish" title="YAMLish">YAMLish</a> - TAP's embedded YAML dialect</li>
    <li><a href="http://testanything.org/wiki/index.php/Things_missing_from_TAP" title="Things missing from TAP">Things missing from TAP</a></li>
{% endcomment %}

## Specifications

-    [TAP specification](/tap-specification.html)
-    [TAP version 13 specification](/tap-version-13-specification.html)

## External Resources

-    [Wikipedia article on TAP](http://en.wikipedia.org/wiki/Test_Anything_Protocol)

{% comment %}
 TODO review needed
  <h2>Mailing Lists</h2>
  <ul>
    <li><a href="http://testanything.org/mailman/listinfo/tap-l" class="external text" title="http://testanything.org/mailman/listinfo/tap-l" rel="nofollow">TAP-L</a> - For discussion of the Test Anything Protocol</li>
    <li><a href="http://www.hexten.net/mailman/listinfo/tapx-dev" class="external text" title="http://www.hexten.net/mailman/listinfo/tapx-dev" rel="nofollow">TAPX-DEV</a> - For developers of <a href="http://testanything.org/wiki/index.php/TAP::Parser" title="TAP::Parser">TAP::Parser</a> and other interested parties. Perl specific.</li>
  </ul>
{% endcomment %}


{% if site.posts.size > 0 %}
  ## Updates

  {% for post in site.posts %}
    -    {{ post.date | date_to_string }} &raquo; [{{ post.title }}]({{ post.url }})
  {% endfor %}
{% endif %}
