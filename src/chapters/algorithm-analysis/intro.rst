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

Big-O Notation is a mechanism for describing the performance of an algorithm, an ordered sequence of steps, in relation to its input. In other words, it is a method for analyzing the steps in a function and how the size of its argument impacts the time it takes to complete those steps. The result of the analysis is referred to as the `[run]time complexity` of the algorithm that was analyzed.


Deriving and comparing the time complexity of algorithms is essential to writing performant systems throughout the countless avenues of applied Computer Science. To that end, there are three main considerations in classifying the time complexity of an algorithm using Big-O Notation:

- the size of the input (colloquially known as ``n``)
- the time complexity of each step (``operation``) in the algorithm
- the order in which the steps (``operations``) are executed

Why
---

Actually writing code is typically the least consuming aspect of a developer's day. Most of their time is spent rigorously planning `how to write their code` in a way that best balances readability, extendability, and performance. In order for developers to optimize their solutions they need a common language for classifying and comparing algorithmic solutions. 

Big-O is that common language. It allows for any algorithm, no matter how complex, to be summarized in a notation that can be easily compared to another. When all of the proposed algorithms have been described in Big-O Notation the most performant will be the one with the lowest time complexity. At least in terms of how long it takes to complete its steps.

.. todo:: fact check this. also how does the data structure contribute to overall performance?

.. note::
  Determining the holistic performance of an algorithm must also factors in its **space complexity**. Space complexity describes performance relative to the algorithm's resource [memory] usage. An algorithm may be incredibly fast but if the host machine is incapable of executing it then it's of no use!


How
---

The Big-O Notation for algorithmic time complexity is always classified in terms of ``n`` - the input size. Traditionally the notation is described as a function of ``n`` in the form ``O(complexity(n))``. 

In theoretical terms, time complexity is considered from a **worst-case**, or upper-bound, of the time requirement. Often this theoretical classification is suitable for comparison across proposed solutions. But it is important to recognize that in practice this time requirement will likely be significantly less.

.. todo:: fact check

.. note::
  The time complexity of an algorithm is a composite of the steps taken within it. We will explore how individual steps, and sub-steps within them, are aggregated into the overall algorithmic time complexity in later sections.

.. todo:: terminology check - "time complexity notations"?

The list below describes the most common time complexity notations along with simple scenarios to help illustrate their meaning. Throughout this chapter we will expand on these examples by introducing pseudo-code and, eventually, full-syntax implementations.

``O(1)``: Constant Time
^^^^^^^^^^^^^^^^^^^^^^^

A Big-O of ``1`` means the time complexity of the algorithm is **independent of the size of the input**. No matter how large the input size is the algorithm will always run in a fixed, or constant, amount of time. Constant time is often in reference to a single operation within an algorithm.

.. admonition:: Examples

  - indexing into an element in an Array
  - finding the smallest value in an Array of numbers sorted in ascending order (first element)






  



