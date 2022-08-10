---
title: "Integration Testing"
teaching: 0
exercises: 0
questions:
- "Do the components interoperate as they should?"
objectives:
- "First learning objective. Design tests to verify interoperability
of components"
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
- component1
- component2 ... componentn
- output

Same principles as those for writing unit tests apply in terms of how
to approach it. Think about what do you
expect this assembly of components to accomplish. Think about what
would be correct behavior and what would be incorrect behavior. Think
about what would be a good way of breaking the execution if there is a
defect. Even better, think of a way to break it quickly if there is a
defect.

- test for integrating components above

The next challenge is pin-pointing which of the components is
responsible for the failure. Here we introduce the concept of
scaffolding of tests such that the pattern of failures tells you
which section of the code is resposible for failure.

## Example from a real world problem

** Problem Statement ** to test a code used for shock hydrodynamics
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


**Series of Test**

Test 1 - Unit test for EOS
Test 2 - Unit test Filling the halo cells
Test 3 - Sedov with uniformly discretized mesh
Test 4 - Sedov with AMR but regridding turned off
Test 5 - Sedov with AMR and regridding turned on

**Deducing the cause of failure**
	> Test1 and Test2 are self contained
	> If Test1 and Test2 pass but Test3 fails, then fault is in
	hydrodynamics solver
	> If first three tests pass and Test 4 fails, then fault is in the
	section of mesh that reconciles quantities at fine-coarse
	boundaries
	> if first four tests pass and Test 5 fails then the culprit is
	regridding
	
> ## Callout Title
>
> text
> text
> text
>
> ~~~
> code
> ~~~
> {: .source}
{: .callout}





