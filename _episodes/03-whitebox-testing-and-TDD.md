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

**Definition**
Testing for code that the tester can modify

**When to develop tests**
Ideally test development should go hand-in-hand with the code development.
--When you start writing a code you start thinking about how you are going to convince yourself that it is correct.
--You will have thought about some input that should produce some output if the code is correct and some other output if the code is not correct. 
--Those are all the ingredients of a test. You encode that into an executable program and you have a test.

TDD(D) -- Test driven development and (design)
--Before writing any code think about how you can test its correctness
--Write the test, which should fail because the feature is not implemented yet.
--Write just enough code to pass the test
--Enhance test or write another test for any addition you wish to make to the code
--Refactor and code until the new test or the collection of tests passes

**Advantages of TDD**
The tests effectively become specification for the code
The developer gets clarity about the purpose of the code. More importantly this involves upfront thinking about what is incorrect behavior for the code, something that is often overlooked in regular development.

--However, it is not necessary to stick to the strict definition. Sometimes writing code is a way of thinking about the specification. That is why there is the term (design) in there. As long as there is a test being developed somewhere in the loop below the process is fine.

**insert figure about TDD loop**
