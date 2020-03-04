========================================
Analyzing Algorithms With Big-O Notation
========================================

Now that we have a conceptual foundation of Big-O Notation let's explore it from a practical perspective. Analysis with Big-O is about **comparing the classifications** of algorithms---not the algorithms themselves. Think of using Big-O as a way of performing a surface-level analysis of how an algorithm will behave based on the `class of algorithms` it belongs to.

Why do we look at the classifications rather than the algorithms themselves? Simply put, because it's the fastest way of comparing performance. We perform analysis to determine what is worth pursuing. If at a high level one algorithm has a Big-O that is more performant than another then we can immediately rule out the poorer candidate. We do not need to waste time implementing each algorithm to compare them in great detail. The classifications define their upper bound potential which, by definition, can never be exceeded.

In this section we will learn about the most common Big-O Values and how each of their relative performance to one another. Along the way we will cover how to evaluate the Big-O Values of steps and the algorithm's they belong to. 

Before we begin let's take a look at a visual representation of the Big-O Values you are likely to encounter. We will soon explore each of these in more detail. For now use this graph to form a mental model of each of their upper bound behaviors.

.. todo:: preview of all the common values on a graph (operations vs input size). something like this https://s14-eu5.startpage.com/cgi-bin/serveimage?url=https%3A%2F%2Fwww.cdn.geeksforgeeks.org%2Fwp-content%2Fuploads%2Fmypic.png&sp=b82f0f2b0994a01b2ddadf6679f37c21&anticache=340636

Linear Big-O Values
===================

.. todo:: consider replacing all instances of Big-O Value with Big-O Classification. it provides the same distinction from Big-O Notation but is clearer and reinforces the idea that we are dealing with classifications not the algorithms themselves

From the graph above you likely noticed the two linear Big-O Values, ``O(1)`` and ``O(n)``. Before getting into more complex Values let's explore these basic notations in the context of individual steps. Later we will learn how to use Big-O arithmetic to combine and reduce the steps of an algorithm to determine its Big-O Value. 

.. admonition:: Tip

  Remember that the Big-O of an algorithm is made up of the Big-O `of the steps within it`. 

.. index:: pseudocode

When discussing Big-O it is common to write **pseudocode** to represent the concepts associated with an algorithm. Pseudocode is an abstract way of writing code that is a mixture of plain English and generic syntax common to most programming languages. It allows us to describe programs and statements, such as the steps of an algorithm, while remaining agnostic to any specific programming language.

.. index:: O(1)

``O(1)``: Constant Time
-----------------------

A Big-O of ``1`` means the time complexity is **independent of the size of the input ``n``**. No matter how large the input size is the growth rate will always remain constant. In other words its growth rate is a fixed value represented graphically as a horizontal line. 

- A step classified as of ``O(1)`` means it is an operation that runs in constant time.
- By extension an algorithm classified as ``O(1)`` means the execution of its steps will run constant time. 

.. admonition:: Pseudocode

  .. sourcecode:: python

    # a simple print statement
    print "I am a simple print statement"

    # indexing into an element of a list of size n
    second_element = list_of_size_n[1]

    # finding the smallest value of a list of n numbers that are sorted in ascending order
    smallest_element = sorted_list_of_size_n[0]

    # comparing two elements in a list of size n
    if list_of_size_n[0] equals list_of_size_n[5]:
      # do some sub-step(s)

``O(n)``: Linear Time
---------------------

A Big-O of ``n`` means the time complexity **is directly proportional to the size of the input** ``n``. As the input size is increased it will grow at a consistent pace. It is represented graphically as a positively sloped line. 

It is associated programmatically with a finite loop such as a ``for`` loop.

- An ``O(n)`` step is a loop that will repeat its sub-step operations **at most** ``n`` number of times
- An algorithm classified as ``O(n)`` will take **at most** ``n`` number of operations to complete its steps

.. admonition:: Pseudocode

  .. sourcecode:: python

    # a loop iterating n number of times
    # notice that n can be a number itself rather than a structure of size n
    repeat from 0 to n:
      # do some sub-step(s)

    # a loop iterating over each element in a list of size n
    for element in array:
      # do some sub-step(s)

    # a while loop that eventually reaches a stop condition is also applicable
    count = 0

    while count < n:
      # do some sub-step(s)
      # one sub-step must increment the counter to ensure the loop will eventually end
      count++ 

Why do we say that ``O(n)`` will take `at most` ``n`` number of times? Because this classification tells us the `upper bound` of what is possible but the reality will depend on how the algorithm is actually used. 

For example, if we are searching for a value in a list of size ``n`` we would perform a comparison operation `up to` ``n`` times. We may find the match in the beginning (1 iteration) or at the end (``n`` iterations) depending on where it is located. We can see that the practical number of iterations depends on `the goal of the algorithm and its steps`, along with other factors covered later in this book.

Evaluating the Big-O of an Algorithm
====================================

Let's consider the relationships between an algorithm, a step, and a sub-step. As discussed previously time complexity is referenced in units of operations. This is our most basic unit of description. We relate an operation to a dependence, if any, on the input size ``n`` using Big-O Notation.

Our end goal is to `evaluate` the Big-O Value of an algorithm. But in order to do so we have to evaluate the Big-O of the steps and sub-steps that occur `within` the algorithm. These labels are just describing how operations can be grouped according to their common level.

Consider the following pseudocode:

.. admonition:: Pseudocode

  .. sourcecode:: python

    function algorithm(n):
      repeat from 0 to n: # level 0, O(n)
        if n equals 1: # level 1, O(1)
          print "it is 1" # level 2, O(1)
        if n equals 5: # level 1, O(1)
          print "it is 5" # level 2, O(1)

After evaluating this algorithm we classify it as ``O(n)``. But how did we arrive at this classification?

In our pseudocode we use indentation to visualize the `level` that each operation belongs to. You can see that the relationship, in terms of levels, becomes: 

  algorithm > step > sub-step > ...sub-step(s)...

When evaluating an algorithm's Big-O we need to:

- **count the Big-O of operations at each level**
- **reduce each level to a common Big-O**
- **repeat until we reduce to a single Big-O for the algorithm** 

Let's start by counting the operations from each level:

- level 2: there are two ``O(1)`` operations
- level 1: there are two ``O(1)`` operations, each with an operation at a sub-level
- level 0: there is one ``O(n)`` operation, with operations at a sub-level

In order to reduce each level we will need to learn a few basic rules:

- **addition**: to sum the operations at the same level
- **multiplication**: to combine the operations of a sub-level with that of the level containing it
- **cancellation**: to discard terms that have a negligible impact on growth rate

Keep in mind that the terms `addition` and `multiplication` are used conceptually to illustrate the rules. You can not `actually` add or multiply Big-O because it is just a notation not a value. So we apply these rules without writing the ``O``:

- level 2: there are two ``(1)`` operations
- level 1: there are two ``(1)`` operations, each with an operation at a sub-level
- level 0: there is one ``(n)`` operation, with operations at a sub-level

Addition
--------

When evaluating operations on the same level we add them together. ``O(1)`` operations are special because they run in constant time. So we can treat them as the number ``1`` itself.

Continuing with the pseudocode example from above:

- level 2: ``(1) + (1) = 2``
- level 1: ``(1) + (1) = 2``
- level 0: ``(n)``

Now that we have summed the operations we need a way to reduce the sub-levels into the levels that contain them until we reach the top level---the algorithm itself.

Multiplication
--------------

Levels that contain sub-levels can be combined using multiplication. We take the sum of a sub-level and multiply it by the level it is contained in. Continuing with the pseudocode example from above:

- level 2 merged with level 1: ``2 * 2 = 4``

We then repeat this reduction until we reach the top level:

- level 1 merged with level 0: ``4 * (n) = 4*n``

At this point we may be tempted classify our algorithm as ``O(4n)``. But we know the algorithm's actual classification is ``O(n)``. Why do we get rid of, or `cancel` the ``4``? 

Cancellation
------------ 



Non-Linear Big-O Values
=======================
