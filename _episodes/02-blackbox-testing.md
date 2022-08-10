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

Imagine that you were asked to test a funtion in a lecgacy code that you don't have access to. In such a situation, black-box testing can be used. Treat your code as a black box for which you only know the inputs and outputs (i.e. the specification) and not how it is implemented or the internal structre of the code. This method can by used to test any third party components that you use in your code as well.

Here you use the specifiction of the fucntion to derive the inputs and the expected output. For example, consider that you were given the following specification for a function. 

Example: with legacy code. Show how the inputs and outputs and how the pytest is written 

There is potentially infinite number of inputs that you can test with. How can we limit the number of tests in an effective manner. There are two appooaches used for this. 
- Equivalance class partitioning
- Boundary value testing

## Equivalance class partitioning
Equivalace class partioning allows to select a relatively small number of test cases to actually run. This is done by partitioning the input space into "equivalence classes." Each equivalence class contains a set of "equivalent" inputs where the program is expectd to process them both in the same way (i.e., follow the same path through the code). If you expect the program to process two inputs in the same way, only use one of them for testing, thus reducing the number of test cases you have to run.

How to create the partitions:
1. First-level partitioning: Valid vs. Invalid inputs.
TODO: add image
2.  Partition valid and invalid inputs into equivalence classes. When creating these internal partions you can either take an *interfce-based approach* or a *functionality-based approach*.
  * Interface-based apporach: Here partitions are created based on the charachteristics of the input parameters of the function that you are testing. You can consider each input parameter in isolation and create the partiions for each parameter. 
  * Functionality-based approach: Here partitions are created based on the behavioral view of the fucntion that you are testing. Here the partitioning is based on the requirements.
TODO: add image
3. Create a test case for at least one value from each equivalence class
TODO: add image
TODO: Add to the previous example

To improve the 
## Boundary value testing
Think as an adversarial to your code–how can you break it? The values at and near the boundaries of the equivalance classes are most likely to break the code. Thefore, we pick values (1) at the boundary and (2) near the boundary to as test cases.

TODO: add image
TODO: Add to the same example



{% include links.md %}

