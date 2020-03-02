========================
Exploring Big-O Notation
========================

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
