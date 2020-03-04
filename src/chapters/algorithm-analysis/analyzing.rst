========================================
Analyzing Algorithms With Big-O Notation
========================================

Now that we have a conceptual foundation of Big-O Notation let's explore it from a practical perspective. Analysis with Big-O is about **comparing the classifications** of algorithms---not the algorithms themselves. Think of using Big-O as a way of performing a surface-level analysis of how an algorithm will behave based on the `class of algorithms` it belongs to.

Why do we look at the classifications rather than the algorithms themselves? Simply put, because it's the fastest way of comparing performance. We perform analysis to determine what is worth pursuing. If at a high level one algorithm has a Big-O that is more performant than another then we can immediately rule out the poorer candidate. We do not need to waste time implementing each algorithm to compare them in great detail. The classifications define their upper bound potential which, by definition, can never be exceeded.

In this section we will learn about the most common Big-O Values and how each of their relative performance to one another. Along the way we will cover how to calculate the Big-O Values of steps and the algorithm's they belong to. Fortunately, the arithmetic used to calculate Big-O only involves three basic operations:

- addition
- multiplication
- cancellation

Before we begin let's take a look at a visual representation of the Big-O Values you are likely to encounter. We will soon explore each of these in more detail. For now use this graph to form a mental model of each of their upper bound behaviors relative to each other.

.. todo:: preview of all the common values on a graph (operations vs input size). something like this https://s14-eu5.startpage.com/cgi-bin/serveimage?url=https%3A%2F%2Fwww.cdn.geeksforgeeks.org%2Fwp-content%2Fuploads%2Fmypic.png&sp=b82f0f2b0994a01b2ddadf6679f37c21&anticache=340636

Common Big-O Values
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

    # indexing into an element of an Array of size n
    second_element = array_of_size_n[1]

    # finding the smallest value of an Array of n numbers that are sorted in ascending order
    smallest_element = sorted_array_of_size_n[0]

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
      # some sub step(s)

    # a loop iterating over each element in an Array of size n
    for element in array:
      # some sub step(s)

    # a while loop that eventually reaches a stop condition is also applicable
    count = 0

    while count < n:
      # some sub step(s)
      # one sub-step must increment the counter to ensure the loop will eventually end
      count++ 


Why do we say that ``O(n)`` will take `at most` ``n`` number of times? Because the number of iterations depends on what the goal is. This classification tells us the `upper bound` of what is possible but the reality will depend on how the actual algorithm is used. 

For example, if we are searching for a value in a list of size ``n`` we may find that value in the beginning (1 iteration) or at the end (``n`` iterations) depending on where it is located. 