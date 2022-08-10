---
title: "Integration Testing"
teaching: 0
exercises: 0
questions:
- "Does combining components result in desired use cases running correctly?"
objectives:
- "First learning objective. Design tests to verify desired combinations of
components"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
FIXME

{% include links.md %}

The design module tells us that the code should have 
components. Earlier in the testing module we told you that you should
have unit tests for each of the components and their
subcomponents. This ensures that each component is doing what it
is supposed to do. What happens when you put these components together
into an application or an executable? Integration testing ensures that
when you combine them they work seamlessly with one another and
continue to behave as they ought? 

Let us go back to the components we created earlier in the module. 
Let us also assume that you have run the unit tests and verified that
they work independently. Next let us write a driver that uses these
modules to accomplish a specific task.

-  initialize
- component 1
- component 2 ... component n
- output

Same principles as those for writing unit tests apply in terms of how
to approach it. Think about what do you
expect this assembly of components to accomplish. Think about what
would be correct behavior and what would be incorrect behavior. Think
about what would be a good way of breaking the execution if there is a
defect. Even better, think of a way to break it quickly if there is a
defect.

**test for integrating components above to be inserted here**

> ## Permutations and combinations of components
>
> Is that the only way in which those components can be combined?
>
> ~~~
> What about -- an alternative way of combining them
> ~~~




The next challenge is pin-pointing which of the components is
responsible for the failure. Here we introduce the concept of
building a scaffolding of tests such that the pattern of failures tells you
which section of the code is resposible for failure.

## Example from a real world problem

**Problem Statement** - test a code used for shock hydrodynamics
using adaptive mesh refinement (AMR). Adaptive mesh refinement allows higher
resolution in regions of domain where there is more structure and lower
resolution where there isn't.

**Code components**

Hydro
	> finite volume stencil based method where a block with halo cells
	filled from neighboring blocks presents a stand-alone decomposed
	domain section to the solver. An analytical solution exists for one shock hydrodynamics
	application (Sedov blast wave). Comparing that against computed
	solution is a way of verifying correctness.

EOS
	> pointwise computation of thermodynamic quantities. Energy and
	temperature can be computed from density and pressure, or pressure
	and temperature can be computed from density and energy, or
	presssure and energy can be computed from density and temperature


Mesh
	> domain dicretized into cells for finite volume approximation
	> domain decomposed into rectangular blocks of adjacent cells
	along all the dimensions, each block having same number of dimensions as the overall domain
	>method to fill halo cells around each block from neighboring
	 blocks for stencil computations
	>AMR methods to handle different dx/dy/dz in different blocks
	 (all the cells in one block have identical dx/dy/dz
		 >> methods to reconcile quantities at fine-coarse boundaries
		 >> methods to regrid as the areas of higher resolution change


> ## Series of tests
> 
> ~~~
>Test 1 - Unit test for EOS
>Test 2 - Unit test Filling the halo cells
>Test 3 - Sedov with uniformly discretized mesh
>Test 4 - Sedov with AMR but regridding turned off
>Test 5 - Sedov with AMR and regridding turned onWhat about -- an alternative way of combining them
> ~~~

> ## Deducing the cause of failure
> The unit tests (Test 1 and Test 2) are self contained
> ~~~	
> Tests 1&2 pass, Test 3 fails =>  hydrodynamics failure
> Tests 1,2,3 pass, Test 4 fails => fine-coarse resolution failure
> Tests 1-4 pass, Test 5 fails => regridding failure
> ~~~	

**When to rely on scaffolding**

In an ideal situation we should have had stand-alone unit tests for regridding, fine-coarse resolution and hydrodynamics. Two reasons for doing it this way.
- This is a legacy code with more integrated tests available
- For several of these, mocked up dependencies are harder to build than using this approach

**The main takeaway is that you should build tests to maximize your code functionality coverage in any mode that you can**


## Advanced Mocking for Legacy Codes

A difficult challenge withe legacy codes is isolating a section of code for testing. Most likely the whole code is going to be a candidate for black box testing. However, sometimes it is possible to discern some possbility of componentization where mocking and stubbing ideas can help isolate a code section for testing. Consider a situation that you are working with a legacy code where different solvers are called one after another. In principle, it should be possible to test each solver independently, but you have no way of knowing what the input going into that solver should look like. One possible mocking approach is described below:

> ## mockup for legacy component testing
> 
> ~~~
>Write a utility that can dump the state of the data at desired points in the code
>Write a reader for reading from the dump and populating the state
>Write a utility that can compare dumps
>Write a driver that can use the reader you wrote, call the solver you wish to test and invoke the comparison utility
>Insert a call to the utility just before, and just after invoking the solver you wish to test
>Run the whole code as you normally would, the first dump becomes the input for the test, and the second dump becomes the baseline for comparing
>The driver is your test for the solver
> ~~~

**Insert a challenge and a solution for an example of the above method**


Now let us extend that idea a bit further. You have a solver that invokes another code component to generate some of the input data. You can solve this problem in one of two ways.

> ## stubbing for legacy component testing
> 
> ~~~
>take a dump of data generated by the invoked component as described above. Add that to the dump from above and enhance the reader to read in this added data.
>Create a stub for the invoked code component
>The driver you wrote before is still the test
> ~~~


> ## scaffolding for the same component testing
> ~~~
>Create a similar mocked up test for the invoked component.
>This test provides scaffolding for testing of the solver.
> ~~~

