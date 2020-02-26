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
- the time complexity of each step in the algorithm
- the order in which the steps are executed

Why
---

Actually writing code is typically the least consuming aspect of a developer's day. Most of their time is spent rigorously planning `how to write their code` in a way that best balances readability, extendability, and performance. In order for developers to optimize their solutions they need a common language for classifying and comparing algorithmic solutions. 

Big-O is that common language. It allows for any algorithm, no matter how complex, to be summarized in a notation that can be easily compared to another. When all of the proposed algorithms have been described in Big-O Notation the most performant will be the one with the lowest time complexity. At least in terms of how long it takes to complete its steps.

.. todo:: fact check this. also how does the data structure contribute to overall performance?

.. note::
  Determining the holistic performance of an algorithm must also factors in its **space complexity**. Space complexity describes performance relative to the algorithm's resource [memory] usage. An algorithm may be incredibly fast but if the host machine is incapable of executing it then it's of no use!


How
---