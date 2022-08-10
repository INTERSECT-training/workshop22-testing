---
title: "Black-box Testing"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Can you test code that you don’t have access to? Yes, that is where black-box testing can be used. Treat your code as a black box in which you know the inputs and outputs. 

Example: with legacy code. Show how the inputs and outputs and how the pytest is written 

There is potentially infinite number of inputs that you can test with. How can we limit the number of tests in an effective manner. There are two appooaches used for this. 
- Eauivalance class partitioning
- Boundary value testing

## Equivalance class partitioning
Equivalace class partioning allows to select a relatively small number of test cases to actually run. This is done by partitioning the input space into "equivalence classes." Each equivalence class contains a set of "equivalent" inputs where the program is expectd to process them both in the same way (i.e., follow the same path through the code). If you expect the program to process two inputs in the same way, only use one of them for testing, thus reducing the number of test cases you have to run.

How to create the partitions:
1. First-level partitioning: Valid vs. Invalid test cases
TODO: add image
2.  Partition valid and invalid test cases into equivalence classes
TODO: add image
3. Create a test case for at least one value from each equivalence class
TODO: add image
TODO: Add to the previous example

## Boundary value testing
Think as an adversarial to your code–how can you break it? The values at and near the boundaries of the equivalance classes are most likely to break the code. Thefore, we pick values (1) at the boundary and (2) near the boundary to as test cases.

TODO: add image
TODO: Add to the same example



{% include links.md %}

