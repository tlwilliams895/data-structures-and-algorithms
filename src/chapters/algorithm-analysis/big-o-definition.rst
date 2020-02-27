Defining Big-O Notation
=======================

.. 
  alternative "plain english" and "technical" explanations in order


What
----

.. 
  highlights:
    dependency on the size a function's input
    dependency on how each step is performed
      constant vs iterative steps
    how big o / data structures / algorithms relate to each other


.. plain english



.. technical

Big O notation is an equation that describes how efficient the worst case scenario (upper bound) of an algorithm is.

Why
---

.. 
  highlights:
    goals:
      break down problem into discrete steps
      categorize steps as constant or iterative
        impact of iterative steps
      what is the data set
        how it is stored
        how is data accessed in the data set
        high level mention of relation to data structures
      determine the efficiency of each step
      determine how the order of the steps impacts performance

.. plain english

The goal of using Big-O notation is to determine the most time-efficient steps, and the order of those steps, to complete the goal of the function.

.. todo:: technical

.. todo:: example

.. 
  only high-level (but technical) definition
  move details to the "analyzing with big-o notation"
    what are the difference strategies for achieving a goal?

.. 
  real-world scenario (non-technical / programmatic)
  highlights:
    describing the series of steps (plain english)
    showing how:
      categorizing each step as constant or iterative
      the effect of which steps are chosen
      the effect the order of the steps has
      the additive nature of steps
      dependency on the size of the problem input

How
---

Diagrams (or table) of most common Big O run times (O(log n), O(n), O(n + log n), O(n^2), O(n!))

- Define O -- 
- Define n -- number of operations
- Define log -- mention that it's log2
- Define n^2?
- Define n!?

Bring the diagrams (or table) together with the definitions above.


.. todo:: moved from intro, consider how these can be flowed into

The list below describes the most common notations along with simple scenarios to help illustrate their meaning. Throughout this chapter we will expand on these examples by introducing pseudo-code and, eventually, full-syntax implementations.

``O(1)``: Constant Time
^^^^^^^^^^^^^^^^^^^^^^^

A Big-O of ``1`` means the time complexity of the algorithm is **independent of the size of the input**. No matter how large the input size is the algorithm will always run in a fixed, or constant, amount of time. Constant time is often in reference to a single operation within an algorithm.

.. admonition:: Examples

  Single Operations:

  - indexing into an element in an Array
  - finding the smallest value in an Array of numbers sorted in ascending order (first element)

  Algorithms:

  - password hash comparison algorithms designed to prevent timing attacks by running in constant time

``O(n)``: Linear Time
^^^^^^^^^^^^^^^^^^^^^
