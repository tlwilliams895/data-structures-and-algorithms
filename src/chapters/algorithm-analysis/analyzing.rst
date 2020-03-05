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

A Big-O of ``1`` means the time complexity is **independent of the size of the input ``n``**. No matter how large the input size is the growth rate will always remain constant. In other words its growth rate is constant and represented graphically as a horizontal line. 

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

A Big-O of ``n`` means the time complexity **is directly proportional to the size of the input** ``n``. As the input size is increased it will grow at a constant rate. It is represented graphically as a positively sloped line. 

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

Why do we say that ``O(n)`` will take `at most` ``n`` number of operations? Because this classification tells us the `upper bound` of what is possible but the actual number of operations will depend on how the algorithm is used in practice. 

For example, if we are searching for a value in a list of size ``n`` we would perform a comparison operation `up to` ``n`` times. We may find the match in the beginning (1 iteration) or at the end (``n`` iterations) depending on where it is located. We can see that the practical number of iterations depends on `the goal of the algorithm and its steps`, along with other factors covered later in this book.

Evaluating the Big-O of an Algorithm
====================================

As discussed previously time complexity is referenced in units of operations. Some operations take a constant amount of time while others are dependent on the size of the input ``n``. Algorithms are comprised of a series of steps, each of which can be thought of as an operation. Steps can also have sub-steps within them such as an operation taken within a loop.

Our end goal is to `evaluate` the Big-O Value of an algorithm. But in order to do so we have to evaluate the Big-O of the steps and sub-steps `within` it. We group and evaluate steps according to their **scope**.

In the pseudocode below we use indentation to visualize the scope of each step and any sub-step within it. 

.. admonition:: Pseudocode

  .. sourcecode:: python

    function algorithm(n):
      # outermost scope, print and loop operations

      print "let's learn how evaluation works!"

      repeat from 0 to n:
        # loop scope, nested print operation
        
        print "I am in the loop scope" # O(1)

        print n 

After evaluating this algorithm we classify it as ``O(n)``. But how did we arrive at this classification?

.. worth including?
You can see that the relationship, in terms of scopes, becomes: 
  algorithm > step > sub-step > ...sub-step(s)...

When evaluating an algorithm's Big-O we need to evaluate each scope as a group. We start from the innermost scope and reduce outwards to the final scope of the algorithm itself.

.. admonition:: Fun Fact

  We are using an algorithm to evaluate and classify other algorithms!

#. **count**: classify and sum the Big-O of each operation of the inner scope
#. **reduce**: multiply the sum of the inner scope with the Big-O of its outer operation
#. repeat this process until reaching the outermost scope

As a final step we **cancel** out terms that have a negligible effect on the growth rate. The result, in Big-O Notation, is the classification of the algorithm.

.. todo:: an example that supports renaming "Big-O Value" to "Big-O Classification". "Big-O Value...not a value" is confusing

.. admonition:: Note

  Keep in mind that the use of `addition` and `multiplication` are used conceptually. You can not `actually` add or multiply a Big-O Value because it is just a notation not a value.
  
We apply this evaluation considering the value inside the notation. For example, ``O(1)`` and ``O(n)`` are treated as ``1`` and ``n`` respectively.

Addition
--------

When evaluating operations in the same scope we add them together.

Let's begin with the innermost scope---the ``loop scope``. It contains a two print operations which both run in constant time.

.. admonition:: Pseudocode

  .. sourcecode:: python
      repeat from 0 to n:
        # loop scope, nested print operation
        
        print "I am in the loop scope" # O(1)

        print n # O(1)

The ``loop scope`` sum, with two ``O(1)`` operations, is evaluated as ``1 + 1 = 2``.

Multiplication
--------------

A scope is merged with its outer operation using multiplication. We take the sum of the inner scope and multiply it by the operation it is contained in.

The loop operation will repeat up to the input size, ``n``, number of times.

.. admonition:: Pseudocode

  .. sourcecode:: python
      repeat from 0 to n: # O(n)
        # loop scope, nested print operation

        print "I am in the loop scope" # O(1)
        print n # O(1)

The loop scope sum is ``2``. The loop operation runs in ``O(n)``. Its product is evaluated as ``2 * n`` or ``2n``.

The ``outermost scope`` contains the reduced loop operation and a print operation. We take the sum of the print and the ``loop scope's`` product as ``2n + 1``.

At this point we may be tempted classify our algorithm as the final sum, ``2n + 1``. But we saw the algorithm's actual classification is ``O(n)``. Why do we get rid of, or `cancel` the coefficient ``2`` and the constant term ``1``? 

Cancellation
------------ 

Recall that Big-O represents the theoretical upper bound of an algorithm's classification. We qualify this upper bound as theoretical because it is determined when approximating an input size ``n`` at a non-real value of infinity. 

When we consider the behavior at this theoretical upper bound we recognize that the following can be discarded: 

- constant terms: any number that doesn't change
- coefficients: any number that is multiplied with a variable
- lower order terms: variables at a power less than the highest found in a polynomial 

To avoid getting bogged down in the mathematical details of **asymptotic analysis** that supports cancellation let's think about constants and coefficients in a practical sense. We will defer the discussion on lower order terms until later in this section when they have a relevant context.

If you multiply infinity by any number, no matter how large, what do you get? Infinity, because there is no concept of anything larger. If you add any number, no matter how large, to infinity what do you get? Infinity.

Essentially there is no number that can be multiplied (coefficient) or added (constant term) to the factor of ``n`` that will have any effect on the growth rate. For this reason we consider coefficients and constants as `negligible` relative to the ``n`` term itself and can discard them.

From our pseudocode example that was reduced to ``2n + 1`` we can see that ``2`` is a coefficient of ``n`` and ``1`` is a constant term, both can be cancelled. After cancelling we are left with ``n``. In Big-O Notation we can clasiffy the algorithm as ``O(n)``!

Non-Linear Big-O Values
=======================


