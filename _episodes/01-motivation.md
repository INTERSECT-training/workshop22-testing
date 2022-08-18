---
title: "Introduction"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
FIXME

{% include links.md %}

## Testing: you're already doing it... you're just doing it *wrong*

Here's a secret --- no matter how inexperienced you might be, you're
already doing testing code. It's a natural and organic part of the
code-writing process. As you compose, do you ever run interactive
sanity checks on a code snippet (in the Python interpreter or in a
Jupyter notebook) to make sure it gives correct answers in simple
known cases? Or that it correctly loads certain data? Or that printed
output is formatted in a particular way? Mazel tov --- you're testing.

So you don't need to be convinced or taught to test. You already
understand and practice the logical basics intuitively. Instead, we
hope to convince you to *formalize* the testing process and then
*automate* it so that it happens routinely. And we'll discuss
guidelines and practical tools for doing so.

Once you're testing the right way, you will:

> - [ ] *Know* your code handles doesn't break for certain inputs or operating cases (as
> opposed to relying on wishful thinking)
>
> - [ ] Have confidence that the correct gives scientifically correct output
>
> - [ ] *Save time!*
{: .checklist}


## Anatomy of a test

## Testa are *code*

## Tests are *documentation*

Fundamentally, tests *reveal* whether code behaves the way it's
expected to. But they also *document* what those expected behaviors
are in the first place.  Some of those behaviors may be simple sanity
checks on obvious aspects of the user interface or to compare
numerical results against some ground truth fiducial example. But
there are other less obvious behaviors that tests document especially
well.

For instance, the developers may have decided how the program should
behave in an unusual corner or edge case for which other choices may
also have worked. A test for the expected output in those cases
documents that expected behavior. It becomes, in essence, a
self-validating specification.  And because tests are code, they are
less prone than is "regular" documentation to fall out of sync with
the overall code because, the moment they do, they *fail* and set off
alarms.  Traditional documentation, by contrast, is not code, it
doesn't get verified automatically by *running*, and it doesn't make
any noise when it no longer matches the code it's supposed to
describe.

Tests also document bugs.  As we discuss later, any time you uncover a
bug, it's good practice to immediately document that failure in the
form of a test that fails and then fix the bug so that the test
passes. In addition to serving as a mini-history of uncovered problems
that lives alongside the code, these bug-discovery tests help to
ensure the same bug doesn't creep back in later.


## Tests are *not* a panacea

## Testing should be easy

DISCUSS FRAMEWORK(S) HERE, AUTOMATION.  INTRODUCE BASICS OF PYTEST.
