========================
Exploring Big-O Notation
========================

Previously, in the introduction, we defined Big-O Notation as a generalized notation for describing and comparing an algorithm's time complexity relative to the theoretical upper bound of its input size. 

.. admonition:: Plain English

  A generic terminology used to describe the longest time* an algorithm could theoretically take to complete by looking at its behavior when given an inconceivably large input

We went on to discuss Big-O Values, of the form ``O(time_complexity(n))``, as the individual notations that classify an algorithm by the steps it is made up of.

.. index:: big-o
.. index:: growth rate

In more rigorous terms, Big-O is a notation for describing the **growth rate** of a time complexity function as its input size approaches a theoretical upper bound of infinity. It is used to classify an algorithm as a function, ``f(n)``, which will never grow faster than the upper bound of the complexity function, ``g(n)``.

.. 
  IDEA: how to fit in that these big-o values are like surrogates/proxies used to model an algorithm
    they are not the actual function of an algorithm/step
      even pre-cancellation they are still approximate models
    include why the true mathematical model of an algorithm isnt used?
      too complicated?
      not possible?  
    example, too heavy?
      It is used to classify an algorithm as a function, ``f(n)``, which will never grow faster than its representative complexity function, ``g(n)``, as its input size approaches infinity.
      
That is to say ``f(n) ≤ O(g(n))`` with respect to their growth rates. The use of ``≤`` here is not mathematically correct but is "close enough" to provide a more relatable understanding of the definition.

There is a lot to unpack here. And if your head is spinning don't worry. In this section we will dissect the confusing parts of the definition and introduce the three elementary Big-O Values. This will prepare you for the more practical section to follow where you will learn the arithmetic used to calculate the Big-O of steps and algorithms along with some other common Big-O Values.

Time Complexity
===============

Let's first clarify what we mean by an algorithm's complexity and what units it can be described in. As is typical in industry usage of Big-O we will focus on time complexity in particular. However, remember that `complexity can refer to any performance characteristic` such as space (memory) or network requests. This is a key facet of Big-O notation---its flexibility in representing any characteristic of interest relative to an upper bound of input size.

.. admonition:: Tip

  Keep in mind that Big-O, described in the chosen complexity of interest, must be able to describe `any algorithm` in terms that are `relative to the system` they are executed in. 

Time complexity **does not refer to how long an algorithm takes in traditional units of time such as seconds or minutes**. We will refer to these units as `human units of time` as we explore the reason why.

.. index:: computational units
.. index:: clock cycle
.. index:: operation

Instead of human units of time we use `computational units of time` to describe time complexity. A computational unit is a generic term for an individual operation executed in an algorithm. Why all the confusion? Because computers operate on `clock cycles` which can be equated to, but are not directly, human units of time. 

.. admonition:: Plain English

  *Time complexity is not the literal time, in seconds, an algorithm takes to complete. Instead it is in units of operations. They are related to seconds by how long the executing computer takes to process each of the operations used in the algorithm.

In (very) simple terms a clock cycle is the frequency, `1 "something" per second`, that a CPU can perform an operation. This is why CPUs are defined in terms of Hertz (Hz) frequency, ``1 cycle/s`` or 1 clock cycle per second, like Mega-Hertz (MHz) or Giga-Hertz (GHz). The speed at which a computer can execute an operation depends on the capability of its CPU in addition to other contextually insignificant factors.

A super computer can certainly execute an algorithm faster, in human units of time, than a common laptop. But by defining time complexity using computational units of time it affords a more portable description. The Big-O of an algorithm can hold true regardless of the machine it is executed on.

It is possible to convert to the `actual human time` using a constant factor, ``s/operation`` or seconds per operation, defined by the capability of the executing machine. But candidate algorithms are typically compared in relative, not absolute, terms.

When speaking generally about Big-O we will refer to time complexity in units of operations. That is to say an algorithm will be described as having an upper bound time complexity that takes `X many operations` rather than `X many seconds`. 

.. todo:: fact check/worth including?
  Later, when we learn about data structures, we can be more specific about `the cost of an operation` such as `inserting an element` or `comparing two elements` in a list. 

Growth Rates
============

.. index:: growth rate
.. index:: upper bound

At its core Big-O Notation is concerned with the **growth rates** of algorithms as a function of their input size. The growth rate of a function is defined as its percentage change as the value of its input is continuously increased. When a function's growth rate is plotted in a graph its x-axis is defined as the size of the variable input. Its y-axis is then defined as the output of the function for each of those values of x.

.. index:: upper bound
.. index:: lower bound

In terms of Big-O the x-axis will be a range from 0, the **lower bound**, to some **upper bound** value of the input size---``n``. The y-axis then represents the behavior of the function, the corresponding output at each value of ``n``. The y-axis will be defined as complexity, some performance measure, as a function of ``n``. 

As is typical in industry usage of Big-O we will focus on time complexity in particular. However, remember that the y-axis can be any performance characteristic such as space (memory) or network requests. This is the key to Big-O notation---its flexibility in representing any characteristic of interest relative to an increasing input size.

.. todo:: generic graph with X (input size, n) and Y as a generic "complexity" (function of n). no lines just the labels of the axes

.. index:: curve

By representing algorithms as mathematical functions we are able to visualize their behavior as an x-y graph. Each function will produce a line created from connecting each of points made up of an x value and its corresponding y value when that x value is applied to the function. Some of these lines will be straight while most will be curved. This curve behavior will be 

.. todo:: doesnt have to be so basic.

Consider a set of proposed algorithms for a given problem. When each of those algorithms are represented as a function and plotted on a graph we can easily compare their behaviors, lines or curves, relative to each other. From this graphical view we can determine which is optimal for the task at hand.

Asymptotic Analysis
^^^^^^^^^^^^^^^^^^^

Previously we discussed how some algorithms can appear performant with small inputs but are then quick to degrade when introduced to larger inputs. If we only looked at a small range of inputs, that is a narrow lower and upper bound, we can only conclude the performance of the algorithm `within that range`. 

Think of these ranges of x like a zoom on a camera. If we are zoomed in too close we have limited information to draw conclusions. By widening this range, or zooming out, we are be able to "see the big picture" of its behavior. From this broader vantage we can draw more confident conclusions about the overall behavior. 

So what upper bound do we choose? Ideally we would want to view the widest range. But it isn't feasible to list every possible input size. However, we can take a mathematical shortcut. By setting the upper bound to infinity we can see the full picture of a function's behavior. Our view is infinitely broad as nothing is larger than infinity! 

.. index:: limit

Of course, we can not actually represent infinity numerically. But we can use the concept of a mathematical **limit** to gain a practical understanding of its behavior at that theoretical upper bound. The limit of a function is its behavior as its input value `approaches` infinity rather than `actually being` infinity.  

The process of evaluating a function at its theoretical limit is known as **asymptotic analysis**. In order to understand asymptotic analysis let's consider what we know about lines and curves on an x-y graph. 

A straight line may be vertical, horizontal, or at some angle in between. This angle, or rate of change, is constant for straight lines. We know this rate as the slope of a line, the ``m`` in the classic equation of a line---``y = m*x + b``. Vertical and horizontal lines indeed have a slope but are simply 1 and 0 respectively. The key here is that straight lines `change at a constant rate` dictated by their slope. 

Curves however `do not change at a constant rate`. They can take the shape of a U or a J rather than a straight line.  A function exhibiting a curve exists because it's y value changes `at different rates` depending on the given value of x. However, at a certain point, some value of x, every curve will reach a limit to this rate of change and will begin to behave like a straight line. 

.. todo:: graph with a straight lines (v, h, between), parabola and exponential to visualize the shapes described above.

.. index:: vertical asymptote

In mathematics a **vertical asymptote** is displayed on a graph as vertical line next to a function's curve. When both the curve and the vertical line appear to nearly overlap each other we can conclude the function has reached its limit. That is, no matter how much we increase the x value it will continue to remain parallel to the vertical line. 

The value of x that causes the function to exhibit this vertical behavior is known as its vertical asymptote. This point is the limit of x for the function because it is the point where no more change can be exhibited.

.. todo:: simple graph showing a curve and an asymptote. point at parts of the curve that are responding to x and highlight the x where the limit is reached

Big-O As The Upper Bound
^^^^^^^^^^^^^^^^^^^^^^^^

So how does this relate to Big-O? Recall that the goal of using Big-O notation is to be able to compare the `upper bound` time complexity of candidate algorithms. When we visualize the limit of each algorithm's growth rate we are able to compare their theoretical potentials to each other. This allows us to quickly, visually, rule out all of algorithms whose performance are relatively less favorable. By process of elimination we can arrive at the optimal choice to solve the given problem.

However, recall that Big-O Notation is generic by design. This means that once we understand the upper bound behavior of the most common Big-O Values we do not have to plot them against each other every time. Rather than needing to visualize them we only need to spend our time calculating each algorithm's Big-O. After we calculate, classify, and order each candidate and order them from our knowledge of their behaviors we can conclude which is the best choice without requiring much more than basic arithmetic!

.. 
  discuss how time complexity is in terms of "operations" not literal time
    more generic term that affords leeway due to differences in processing capacity of host machine
  segue into the three "base values"?? of Big-O
    constant
    n
    log2 n
    are there others? is this correct?

``O(1)``: Constant Time
^^^^^^^^^^^^^^^^^^^^^^^

A Big-O of ``1`` means the time complexity of the algorithm is **independent of the size of the input**. No matter how large the input size is the algorithm will always run in a fixed, or constant, amount of time. Constant time is often in reference to a single operation within an algorithm.

.. admonition:: Examples

  Single Operations:

  - indexing into an element in an Array
  - finding the smallest value in an Array of numbers sorted in ascending order (first element)

  Algorithms:

  - password hash comparison algorithms designed to prevent timing attacks by running in constant time

``O(n)``: Linear Time
^^^^^^^^^^^^^^^^^^^^^
