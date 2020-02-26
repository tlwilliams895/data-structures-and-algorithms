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

An approach to finding the upper bound of how long a function, made up of a series of steps, will take to complete. 

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

Types of Time Complexity
------------------------

.. 
  relative to:
    a single step
    the overall algorithm
  how steps become additive
    dominance of highest order
      why?
      rejecting constants and lower orders
        theoretical vs practical rejection

- Constant -- same number of steps every time
- Polynomial linear -- single pass over the entire data
- Polynomial quadratic -- 
- log -- s

Worst Case?
-----------

Bring back the first section definition highlighting worst case or upper bounds.

- What do we mean by worst case? 
- What is best case? 
- Why don't we use Big O notation for best case?

.. TODO: Should Big O Operations be discussed here? or analyzing with big o notation?

Big O Operations
----------------

What do we mean by operations?

- Sum
- Product
- multiplication by product

Another Example?
----------------

.. TODO: move following section to insertion-sort doc

.. 
  case studies:
    in main doc: pseudocode
    link to: directory of implementations in various languages
      c# for this first draft

Case Study: Insertion Sort
--------------------------

What is the insertion sort algorithm. What are the two implementations of this algorithm?

Link back to the recursion lesson in LC101.

Recursive
^^^^^^^^^

What does the solution look like in C#? (psuedo-code)

How do we calculate this algorithm's run time complexity?

How do we now put that run time complexity into Big O notation?

Non-Recursive
^^^^^^^^^^^^^

What does the solution look like in C#? (psuedo-code)

How do we calculate this algorithm's run time complexity?

How do we now put that run time complexity into Big O notation?
