.. 
  mirror the big-o-definition headers
    all in plain-english
  examples are describing the scenarios in english only
  headers
    What -> What is Big-O?
    Why -> Why is it Important?
    How -> How is it used?

Introduction
============

What
----

Big-O Notation is a way of describing the performance of an algorithm, an ordered sequence of steps, in relation to the size of its input. Specifically, it focuses on the amount of [run] time and space [memory usage] required to complete its steps. We refer to these performance factors as the algorithm's **time complexity** and **space complexity** respectively.

Big-O is concerned with the **worst-case**, where an input is infinitely large, to determine how an algorithm behaves under the heaviest load. This is important because many algorithms behave differently as the size of their inputs are scaled. Some may seem incredibly performant for small sizes but are quick to reach their asymptotic limit with larger input sizes. 

In real world systems, where performance optimization becomes a top priority, it is likely that large data sets are the subject of seeking an algorithm. Development time is expensive. It would rarely, if ever, be expended on micro-optimizations for small data sets. Understanding the algorithm's theoretical limit lends confidence to its practical capability when used in a real system.

In software development space complexity often takes a back seat to time complexity. To understand this prioritization consider the limiting factors and their avenues for resolution. If an algorithm is slow then nothing, short of choosing a new algorithm, can improve its time complexity. However, memory is abundant and easy to allocate if a golden algorithm demands it. Especially in the world of cloud computing where provisioning hardware is only limited by the operating budget. For this reason we will use the terms time complexity and Big-O interchangeably.

It should now be clear that deriving and comparing the time complexity of candidate algorithms is essential to writing performant systems. To that end, there are three main considerations in classifying the time complexity of an algorithm using Big-O Notation:

- the size of the input (colloquially known as ``n``)
- the time complexity of each step in the algorithm
- the order in which the algorithm's steps are executed

Why
---

Actually writing code is typically the least consuming aspect of a developer's day. Most of their time is spent rigorously planning `how to write their code` in a way that best balances readability, extendability, and performance. In order for developers to optimize their solutions they need a common language for classifying and comparing algorithmic proposals. 

Big-O is that common language. It allows for any algorithm, no matter how complex, to be summarized in a notation that can be easily compared to any other. When all of the proposed algorithms have been described in Big-O Notation the most performant will be the one with the lowest time complexity.

If two candidates are similar in time complexity then their space complexity can be considered as a tie-breaker. If the slower algorithm can operate under an appreciable savings of space then it may be worth the trade off. As with most decisions in software development the right choice is the best balance of gains and sacrifices needed to accomplish the goals of a system.


How
---

The Big-O Notation for algorithmic complexity is always classified in terms of ``n`` - the input size. Traditionally the notation is described as a function of ``n`` in the form ``O(complexity(n))``. 

In theoretical terms, time complexity is considered from the upper-bound of the time requirement. Often this theoretical classification is suitable for comparison across proposed solutions. But it is important to recognize that in practice this time requirement will likely be significantly less. There are more detailed approaches that can be used to derive the best and optimal ratio cases as well. However, these are beyond the scope of this course.

.. todo:: fact check

.. note::
  The time complexity of an algorithm is a composite of the steps taken within it. We will explore how individual steps, and any sub-steps within them, are aggregated into the overall algorithmic time complexity in later sections.








  



