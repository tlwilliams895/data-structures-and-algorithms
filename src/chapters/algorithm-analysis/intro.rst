Introduction
============

What Is Algorithm Analysis?
---------------------------

What Is An Algorithm?
^^^^^^^^^^^^^^^^^^^^^

.. index:: ! algorithm

.. TODO:: just link to the Algorithm definition in the LC101 book and clear out a lot of this info

An **algorithm** is an ordered sequence of steps that are taken to solve a problem. Many common tasks we do as humans can be described as an algorithm. For example, consider the series of steps of brushing your teeth. 

#. grab the toothbrush
#. apply toothpaste to the brush
#. wet the brush
#. move the brush in a circular motion over a tooth
#. repeat step 4 for each tooth in your mouth
#. rinse your mouth with water
#. rinse the toothbrush

Consider the following aspects:

- the steps have a specific order
- some steps take a fixed amount of time (steps: 1, 2, 3, 4, 6, 7)
- some steps are dependent on the number of teeth you have (step 5)
- the number of times step 4 is repeated is controlled by step 5

.. TODO:: start up again with the analysis

So how long would it take one person to brush their teeth? We simply need to figure out how long each step will take.

#. grab the toothbrush - 3 seconds
#. apply toothpaste to the brush - 3 seconds
#. wet the brush - 3 seconds
#. move the brush in a circular motion over a tooth - 4 seconds
#. repeat step 4 for each tooth in your mouth - 32 teeth at 4 seconds (32 x 4)
#. rinse your mouth with water - 5 seconds
#. rinse the toothbrush - 3 seconds

3 + 3 + 3 + (32 x 4) + 5 + 3 = 145 seconds. Our algorithm of brushing teeth takes almost 2 and a half minutes!

What we have just done is a basic `analysis` of an algorithm. We have a list of steps, and have defined which steps are dependant on the input size ---in this case the number of teeth. 

Algorithm Analysis
^^^^^^^^^^^^^^^^^^

.. index:: algorithm analysis
.. index:: complexity

**Algorithm analysis** is the full process of inspecting an algorithm and determining how a performance characteristic of interest changes depending on the size of the algorithm's input. We call each characteristic measure the **complexity** of an algorithm. In essence algorithm analysis tells us how long an algorithm will take to run.

We write algorithms to solve problems, however one problem could be solved by a huge number of algorithms. We perform algorithm analysis to determine which algorithm would perform the best. To assist with comparing algorithms programmers have developed a `common notation` that can be applied to any algorithm to assist with algorithm comparison.

Big-O Notation
^^^^^^^^^^^^^^

.. index:: ! big-o notation
.. index:: ! time complexity
.. index:: ! space complexity

**Big-O Notation** is a mathematical notation for describing the complexity of a function in relation to the size of its input. It focuses on the amount of time or space (that is, run time and memory usage) required for an algorithm to complete its steps. We refer to these performance characteristics as the algorithm's **time complexity** and **space complexity** respectively.

In software development space complexity often takes a back seat to time complexity. To understand this prioritization consider the limiting factors of each and how difficult they are to resolve. 

Time complexity is a `software limitation`. It can only be improved by implementing a faster algorithm which can take a considerable amount of effort. However, space complexity is a `hardware issue`. It can be resolved by provisioning more memory and only involves changes to the operating budget. 

Unless otherwise specified it is safe to assume that professional discussion on Big-O refers to time complexity. For this reason we will focus on time complexity and use it interchangeably with Big-O. 

Big-O Notation is important because it is the `common notation` we use to determine the performance of any algorithm. Since we use this common language we can compare two very different algorithms, and determine which one will perform better with regards to time complexity.

Concept Checks
--------------

.. admonition:: Question

  What is an algorithm?

  #. a way to determine the Big-O Value
  #. an ordered sequence of steps
  #. another word for complexity
  #. a special type of loop

.. 2/B

.. admonition:: Question

  What does the time complexity of an algorithm refer to?

  #. how much processing power an algorithm requires relative to its input size
  #. how much memory an algorithm requires relative to its input size
  #. how long an algorithm takes to complete relative to its input size
  #. how long it takes for developers to write an algorithm

.. 3/C

.. admonition:: Question

  What does the space complexity of an algorithm refer to?

  #. how much processing power an algorithm requires relative to its input size
  #. how much memory an algorithm requires relative to its input size
  #. how long an algorithm takes to complete relative to its input size
  #. how long it takes for developers to write an algorithm

.. 2/B

.. admonition:: Question

  Which complexity of an algorithm is more important to optimize? Why?

  #. time complexity because space complexity can be solved by allocating more resources
  #. space complexity because an algorithm can be written faster by assigning more developers

.. 1/A

.. admonition:: Question

  What is Big-O Notation?

  #. a general notation used to describe the complexity of an algorithm relative to its input size
  #. the process of analyzing an algorithm's performance
  #. an analogous term for an algorithm

.. 1/A

.. admonition:: Question

  What is true about a Big-O Value?

  - [ ] it is a mechanism used to calculate the time complexity of an algorithm
  - [ ] it is a complexity function in terms of an input
  - [ ] it is an analogous term for Big-O Notation
  - [ ] it can be used to describe an individual step or algorithm as a whole

.. 2, 4


.. admonition:: Question

  In what ways is understanding the Big-O of an algorithm valuable?

  - [ ] it is a standardized way of comparing the performance of candidate algorithms

  - [ ] it can help in understanding the budget required to execute an algorithm

  - [ ] it can provide an understanding of an algorithm's practical capability from its theoretical limitation

.. 1, 2, 3
  