Introduction
============

What Is Algorithm Analysis?
---------------------------

.. todo:: how to index a multi word def?

.. index:: ! big-o notation
.. index:: ! algorithm
.. index:: ! time complexity
.. index:: ! space complexity

**Big-O Notation** is a way of describing the performance of an **algorithm**, an ordered sequence of steps, in relation to the size of its input. Specifically, it focuses on the amount of time and space (that is, run time and memory usage) required to complete its steps. We refer to these performance factors as the algorithm's **time complexity** and **space complexity** respectively.

.. index:: ! worst-case complexity

Big-O is concerned with the **worst-case complexity**, where an input is infinitely large, to determine how an algorithm behaves under the heaviest load. This is important because many algorithms behave differently as the size of their inputs are increased. Some may seem incredibly performant for small input sizes but can degrade in performance when larger inputs are introduced. 

It's important to recognize that a developer doesn't need to worry about the performance of `every` algorithm they write, since most will only be used with small data sets. However, when large inputs become a bottleneck on a system an optimized algorithm can become a top priority. In those cases determining the algorithm's theoretical limit lends confidence to its practical capability.

In software development space complexity often takes a back seat to time complexity. To understand this prioritization consider the limiting factors of each and how they can be resolved. Time complexity can only be improved by modifying or replacing an algorithm. However, space complexity can be resolved by simply provisioning more memory. For this reason we will focus on time complexity and use it interchangeably with Big-O.

Why Is Big-O Notation Important?
--------------------------------

Writing code is just one aspect of a developer's toolkit. But an important precursor is designing and planning `how to write their code` in a way that best balances readability, extendability, and performance. In order for developers to optimize their solutions they need a common language for classifying and comparing algorithmic proposals. 

.. todo:: do we index every mention or just the first?

.. index:: ! big-o notation

Big-O Notation is that common language. It allows for any algorithm, no matter how complex, to be summarized in a notation that can be easily compared to any other. When all of the proposed algorithms have been described in Big-O Notation the most performant will be the one with the lowest time complexity.

.. index:: ! time complexity
.. index:: ! space complexity

If two candidates are similar in time complexity then their space complexity can be considered as a tie-breaker. If the slower algorithm can operate under an appreciable savings of space then it may be worth the trade off. As with most decisions in software development the right choice is the best balance of gains and sacrifices needed to accomplish the goals of a system.

How
---

Deriving and comparing the time complexity of candidate algorithms is essential to designing performant systems. To that end, there are three core considerations in classifying the time complexity of an algorithm using Big-O Notation:

- the size of the input (colloquially known as ``n``)
- the time complexity of each step in the algorithm
- the order in which the algorithm's steps are executed

.. index:: ! big-o-notation

The Big-O Notation for algorithmic complexity is always classified in terms of ``n``---the input size. Traditionally the notation is described as a complexity function of ``n`` in the form ``O(complexity(n))``. 

In theoretical terms, time complexity is considered from the upper-bound of the time requirement. Often this theoretical classification is suitable for comparison across proposed solutions. But it is important to recognize that in practice this time requirement will likely be significantly less. 

There are more involved approaches that can be used to derive the best and optimal-ratio cases as well. However, these are beyond the scope of this course. Using the worst-case as a basis is often ample in ruling out poor candidates.

The Big-O of an algorithm is a composite of the time complexity of the individual steps taken within it. We will explore how each step, and any sub-steps within them, are aggregated into the overall algorithmic time complexity in the coming sections.

Concept Checks
--------------

.. admonition:: Question

  What is an algorithm?

  #. a way to determine the Big-O notation
  #. an ordered sequence of steps
  #. another word for complexity
  #. a special type of loop

.. admonition:: Question

  What does the time complexity of an algorithm refer to?

  #. how much processing power an algorithm requires relative to its input size
  #. how much RAM an algorithm requires relative to its input size
  #. how long an algorithm takes to complete relative to its input size
  #. how long it takes to write an algorithm

.. admonition:: Question

  What does the space complexity of an algorithm refer to?

  #. how much processing power an algorithm requires relative to its input size
  #. how much RAM an algorithm requires relative to its input size
  #. how long an algorithm takes to complete relative to its input size
  #. how long it takes to write an algorithm

.. admonition:: Question

  Which of the complexities is more important to optimize? Why?

  #. time complexity because space complexity can be solved by allocating more resources
  #. space complexity because an algorithm can be written faster by allocating more developers to write it

.. admonition:: Question

  In what ways is understanding the Big-O of an algorithm valuable?

  - [ ] it is a standardized way of comparing the performance of different algorithms

  - [ ] it can help reduce the time it takes to implement an algorithm

  - [ ] it can help understanding the budget required to execute an algorithm

  - [ ] it can provide an understanding of an algorithm's practical capability using its theoretical limitation
  