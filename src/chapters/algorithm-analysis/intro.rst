Introduction
============

What Is Algorithm Analysis?
---------------------------

What Is An Algorithm?
^^^^^^^^^^^^^^^^^^^^^

.. index:: ! algorithm

An **algorithm** is an ordered sequence of steps that are taken to solve a problem. You will often hear the term used in the context of Computer Science. But many common tasks we do as humans can be described as an algorithm. For example, consider the algorithm of brushing your teeth. What are the steps taken to solve the problem of unhealthy teeth? 

#. grab the toothbrush
#. apply toothpaste to the brush
#. wet the brush
#. move the brush in a circular motion over a tooth
#. repeat step 4 for each tooth in your mouth
#. rinse your mouth with water
#. rinse the toothbrush

Consider the following aspects:

- the steps have a specific order
- some steps take a fixed amount of time (1, 2, 3, 4, 6, 7)
- some steps are dependent on the number of teeth you have (5)
- the number of times step 4 is repeated is controlled by step 5

Dentists recommend that we should brush our teeth for 2 minutes assuming we have all 32 adult teeth---about 4 seconds per tooth. But what if you have less teeth? Or more? Then it's clear that the `time it takes to brush is impacted by the number of teeth you need to clean`. Because the other steps will `always take a constant amount of time` no matter how many teeth are present. 

What we have just done is a basic `analysis` of an algorithm. Of course this is a contrived example devoid of finer details. But the first part of the analysis is the same. We have separated each step according to its dependence on the input size---in this case the number of teeth. 

.. index:: algorithm analysis
.. index:: complexity

In Computer Science **algorithm analysis** is the full process of inspecting an algorithm and determining how a performance characteristic of interest changes depending on the size of the algorithm's input. We call each characteristic measure the **complexity** of an algorithm.

Because there many ways to solve a problem we need a way to objectively compare the complexity of proposed algorithms and determine which is most performant. At the same time this mechanism of comparison needs to be broad enough to be applied to any type of problem. In other words, we need a `common notation` that can be applied to any algorithm and any form of complexity we are seeking to compare.

Big-O Notation
^^^^^^^^^^^^^^

.. index:: ! big-o notation
.. index:: ! time complexity
.. index:: ! space complexity

**Big-O Notation** is a mathematical notation for describing the complexity of a function in relation to the size of its input. In Computer Science it focuses on the amount of time or space (that is, run time and memory usage) required for an algorithm to complete its steps. We refer to these performance characteristics as the algorithm's **time complexity** and **space complexity** respectively.

Big-O is most often used to determine the worst-case theoretical complexity, where an input is infinitely large, to determine an algorithm's limitations. Often the performance of an algorithm will change as the size of its input is increased. Some may seem performant for small input sizes but can degrade when larger and larger inputs are introduced. 

It's important to recognize that a developer doesn't need to worry about the performance of `every` algorithm they write, since most will only be used with small data sets. However, when large inputs become a bottleneck on a system an optimized algorithm becomes a top priority. In those cases determining the algorithm's theoretical limit lends confidence to its practical capability under a heavy load.

In software development space complexity often takes a back seat to time complexity. To understand this prioritization consider the limiting factors of each and how difficult they are to resolve. 

Time complexity is a `software limitation`. It can only be improved by implementing a faster algorithm which can take a considerable amount of effort. However, space complexity is a `hardware issue`. It can be resolved by provisioning more memory and only involves changes to the operating budget. 

Unless otherwise specified it is safe to assume that professional discussion on Big-O refers to time complexity. For this reason we will focus on time complexity and use it interchangeably with Big-O. 

Why Is Big-O Notation Important?
--------------------------------

Writing code is just one aspect of a developer's toolkit. Another important tool is designing and planning `how to write the code` in a way that best balances readability, extendability, and performance. In order for developers to optimize their solutions they need a consistent mechanism and language for comparing candidate algorithms. 

.. todo:: do we index every mention or just the first?

.. index:: ! big-o notation

Big-O Notation is that mechanism. It allows for any proposed algorithm be summarized in a way that can be easily compared to other potential solutions for a given problem. When all of the proposed algorithms have been described using Big-O Notation the best choice will be the one with the lowest time complexity.

.. index:: ! time complexity
.. index:: ! space complexity

If two candidates are similar in time complexity then their space complexity can be considered as a tie-breaker. If the slower algorithm can operate under an appreciable savings of space, or operating cost, then it may be worth the trade off. As with most decisions in software development the right choice is the best balance of gains and sacrifices needed to accomplish the goals of a system.

.. admonition:: Tip

  Remember that Big-O is a general notation. It can be used to compare algorithmic performance relative to other complexity characteristics, beyond time and space, that are relevant to a system.

How Does Big-O Notation Work?
-----------------------------

Calculating and comparing the time complexity of candidate algorithms is essential to designing performant systems. To that end, there are three core considerations in analyzing the time complexity of an algorithm and describing it in Big-O Notation:

- the size of the input (colloquially known as ``n``)
- the time complexity of each step in the algorithm
- the order in which the algorithm's steps are executed

.. index:: ! big-o value
.. index:: ! n

When an algorithm is classified using Big-O Notation we refer to it as the algorithm's **Big-O Value**. The Big-O Value of an algorithm, often abbreviated as just "Big-O", is always described in terms of ``n``---the variable input size. 

.. index:: ! complexity function

Traditionally the value is written as a **complexity function** of ``n`` in the form ``O(complexity(n))``. 

Calculating the Big-O of an algorithm involves analysis of the individual steps taken within it. Each step has `its own` Big-O Value which describes how its time complexity is affected by the size of ``n``. Steps themselves can also have sub-steps, such as operations taken with a loop, which in turn have their own Value. Although this sounds complicated you will soon see that the process is methodical and nothing to feel overwhelmed by.

In later sections we will explore most common Big-O Values and the arithmetic involved in calculating them both for a step and an algorithm as a whole. What is important to understand now is that the Big-O of an algorithm is dependent on the Big-O of the steps taken within it. 

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
  