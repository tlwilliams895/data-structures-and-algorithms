========================
Big-O Notation In Detail
========================

Previously, in the introduction, we defined Big-O Notation as a generalized notation for describing and comparing an algorithm's time complexity relative to the theoretical upper bound of its input size. 

.. admonition:: Plain English

  A generic terminology used to describe the longest time* an algorithm could theoretically take to complete by looking at its behavior when given an inconceivably large input

We went on to discuss Big-O Values, of the form ``O(time_complexity(n))``, as the individual notations that classify an algorithm by the steps it is made up of.

.. index:: big-o
.. index:: growth rate

Speaking more rigorously, Big-O is a notation for describing the **growth rate** of a time complexity function as its input size is increased towards infinity. For non-linear Big-O Values they will grow until reaching their asymptotic upper bound.

In mathematical terms it is used to describe an algorithm as a function, ``f(n)``, which will never grow faster than at the upper bound its representative complexity function, ``g(n)``. The complexity function serves as an approximate model for the behavior of the algorithm classified by it. 

.. 
  IDEA: how to fit in that these big-o values are like surrogates/proxies used to model an algorithm
    they are not the actual function of an algorithm/step
      even pre-cancellation they are still approximate models
    include why the true mathematical model of an algorithm isnt used?
      too complicated?
      not possible?  
      
      
That is to say ``f(n) < O(g(n))`` with respect to their growth rates. The use of ``<`` here is not mathematically correct but is "close enough" to provide a more relatable understanding of the definition.

There is a lot to unpack here. And if your head is spinning don't worry. In this section we will dissect the confusing parts of the definition and introduce two elementary Big-O Values.

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

At its core Big-O Notation is concerned with the **growth rates** of algorithms as a function of their input size. The growth rate of a function is its incremental change in output as the value of its input is continuously increased. 

.. index:: upper bound
.. index:: lower bound

In terms of Big-O the x-axis represents increasing input sizes, ``n``, from a **lower bound** of 0 through an **upper bound** value of infinity. The y-axis then represents the behavior of a complexity function at each increasing value of ``n``. 

.. todo:: generic graph with x (input size, n) and y as a generic complexity(n). no lines plotted just these labels of the axes as boundless arrows in the x and y

.. index:: curve

By representing algorithms as mathematical functions we are able to visualize their behavior on a graph. Each Big-O value will have a characteristic behavior that is either a straight or curved line.

Because of their linear nature the growth rate behavior of straight lines is simple and determined by their slope. A line with no slope is said to have a constant growth rate because it is fixed horizontally. A line with a positive slope will grow at a rate proportional to the size of the input.

.. index:: vertical asymptote

Curved lines have a more complex growth behavior. They will grow at a `variable` rate that itself changes with the size of the input. But curved lines eventually reach a `limitation point` where their curvature straightens and becomes practically vertical. This behavior of curved lines is exhibited as it approaches an imaginary boundary known as its **vertical asymptote**.

Asymptotic Analysis
-------------------

Previously we discussed how some algorithms can appear performant with small inputs but are then quick to degrade when introduced to larger inputs. If we only looked at a small range of inputs, that is a narrow spread between the lower and upper bounds, we can only conclude the performance of the algorithm `within that narrow range`. 

Think of these ranges of like a zoom on a camera. If we are zoomed in too close we have limited information to draw conclusions. By widening this range, or zooming out, we are be able to "see the big picture" of its behavior. From this broader vantage we can draw more confident conclusions about the overall behavior. 

So what upper bound do we choose? Ideally we would want to view the widest range. But it isn't feasible to list every possible input size. However, we can take a mathematical shortcut. By approximating the function's behavior as its input is increased towards infinity we can see the full picture of a its behavior. Our view is `infinitely broad` as nothing is larger than infinity! 

.. index:: limit

Of course, we can not actually represent infinity numerically. But we can use the concept of a mathematical **limit** to gain a practical understanding of its behavior as its input `approaches` infinity rather than `actually being` infinity. Eventually the curve will reach a point where it begins to straighten and become vertical. This point is the upper bound of the curve. 

.. index:: asymptotic analysis

In other words, it is a point as the input size approaches infinity where the output of the function itself grows indefinitely towards infinity. The process of evaluating a function at this limit is known as **asymptotic analysis** because the curve continues to grow vertically in parallel to its vertical asymptote. 

.. index:: vertical asymptote

In mathematics a **vertical asymptote** is displayed on a graph as vertical line next to a function's curve. When both the curve and the vertical line appear to nearly overlap each other we can conclude the function has reached its limit. That is, no matter how much we increase the x value it will only grow vertically. 

.. todo:: simple graph showing a curve and an asymptote. point at parts of the curve that are responding to x and highlight the x where the limit is reached


Big-O As The Upper Bound
------------------------

So how does asymptotic analysis relate to Big-O? Recall that the goal of using Big-O Notation is to be able to compare the `upper bound` time complexity of candidate algorithms. When we visualize the limit of each algorithm's Big-O growth rate we are able to compare their theoretical potentials to each other. 

Those that reach their vertical asymptote sooner are said to be less performant. Because their growth rate is limited at smaller input sizes relative to other candidates. 

.. admonition:: Plain English

  Algorithms classified by Big-O Values that take more operations to complete are less performant than those that take less operations to complete. The limit of a less performant algorithm will be exhibited at a smaller input size than one that can tolerate a larger input before reaching its upper bound.

Knowing the growth rate of a Big-O Value we can approximate the behavior of a real algorithm classified by it. We can say that the **actual algorithm will grow at some rate less than that of its classification** since the latter has a known upper bound taken at its theoretical limit.

Check Your Understanding
========================

.. admonition:: Question

  Time complexity refers to the runtime in standard units of time (seconds, minutes, etc.)

  - true
  - false

.. false

.. admonition:: Question

  The limit of a complexity function is the point where its curve becomes vertical

  - true
  - false

.. true

.. admonition:: Question

  The Big-O of an algorithm is the upper bound classification of its behavior

  - true
  - false

.. true

.. admonition:: Question

  An algorithm's actual growth rate at will always be less than the upper bound of the Big-O Value that classifies it

  - true
  - false

.. true


