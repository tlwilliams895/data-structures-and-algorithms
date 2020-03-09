============
Binary Trees
============

.. link back to list section of C#

.. pros

.. cons -> this is why if you have an ordered list -- to put a new element in that is in the correct order O(n) -> how could we make that more efficient

.. lead-in to BT ->

.. relevant objectives
  - Understand the conceptual structure of a binary tree

.. relevant notes from paul
  - how to convert an array / list into a BT
  - Understand the conceptual structure of a binary tree

.. open with here is the data structure you've used the most list -- this is a new data structure, they have pros and cons

Throughout this course you have been using a list (both JavaScript and C#) to meet the needs of our various data requirements. Lists are great. They allow us to collect data together, and reference the contents by accessing their index. The majority of lists are unordered, but we learned to order them by using built in sort methods.

Lists are fantastic for collecting together data, but to search for a specific piece of data in an unordered list you typically would use a simple search, which is O(n). Lists aren't less performant the larger they get.

Today we will be introducing a new data structure that will allow us to easily use a Binary Search easily with our new data structure the Binary Tree.

Binary Tree
-----------
Taking the example we saw for Binary Search let's turn it into a Binary Tree.
Collection: (1, 2, 3, 4, 8, 9, 10, 14, 18, 20, 30)

Before we can learn about a Binary Search Tree which is the unique data
structure that works with Binary Search, we have to learn about the data
structure a Binary Search Tree is based on the Binary Tree.
A binary tree is a tree like data structure in which any node can have up to
two branches to additional nodes. When visualized the data structure looks
like a tree.

.. sourcecode::

        a
    b       c
  d   e   f   g

A has two branches down to b and c. B has two branches down to D and E. C has
two branches to F and G. If we were to add more elements to this data
structure we would put them as new nodes connected by branches to either D, E,
F, or G.

It should be stated that not every Binary Tree will look perfect with every
node having two children nodes. To be a Binary Tree it simply needs to fit the
definition of one node, not having any more than 2 child nodes.

.. sourcecode::

             a
         b       c
      d     e f     g
           h       i  j
          k

That is an example of a valid Binary Tree. None of the nodes have more than
two children, and not every node has the same number of children. Some nodes
have 2, 1, or even 0 children. The name Binary Tree comes from the number of children each
node can have up to 2. 

The child's position from the parent node is important.
A has two children (B and C). We would call B the left child, and C the right
child. B has two children (D and E). We would call D the left child of B, and
E the right child of B.

Binary Trees are almost always used in Computer Science when it comes to
sorting, or searching. It is very rare you would need to code a Binary Tree
yourself, but knowing how they work is beneficial in understanding how certain
sorting, or searching algorithms perform.

.. 
  list = [5, 7, 2, 10, 4, 3, 10, 11]

    5
  7   2
10 4  3  10
11 

.. while these look very different look at similarities and differences in the structure
.. similarities: ordered sequence of elements, unbounded
.. differences: not flat. recursive structure...what do we mean by recursive structure?

To assist with learning this new data structure lets talk about how they are similar.

They are both data structures that can hold any number of elements. They both have a starting element, index of 0 for a list, and the root node for a Binary Tree. They both have connections to other elements in the list. You can move forward or backward in a list, whereas you can move to the left child, or right child of a Binary Tree. They can both be unordered, or ordered.

One of the main ways lists, and binary trees are different is in the indexing of values for arrays. With an array you can access the first value by accessing index 0. You can use the same practice to access any value in the arary, you simply need to know it's position. In a binary tree you cannot access a value by knowing it's position. You find values by looking into one nodes children, and keep checking children until you find the value you are looking for. So how the data structure is used is quite different. We will see examples of how this is used in future sections.

Since you cannot access an element by it's index and you must search through child relationships, this makes a Binary Tree a recursive structure.

.. BT is a RECURSIVE structure? segue into the base algorithm of producing a tree
.. what is the "algorithm" (in numbered steps) for converting from list to BT
#. first element is the **root node**
#. left child and right child
#. repeat to next level producing another tree

.. pros -> BT has the potential of more efficient search, insertion and deletion it is the base structure of which we can achieve these goals.
.. it is a base structure from which certain operations can be made more performant analogous to relationship between arrays [base structure ordered sequence of elements] and lists [...]. the base provides the base characteristics which are fine tuned for specific use cases in the derived structures

Root Node
^^^^^^^^^

.. start with a list -> how do we turn this into a BT

.. this is the root node value 8 which element 2 -> formal definition of a root node with regards to BT

.. build the root node of the BT and display it

In a Binary Tree the root node is the first element of our data structure.

In the example list ``[5, 19, 2, 4]`` our first element is ``5``.

In the example binary tree

.. sourcecode::

         5
      19   2
    4

``5`` is our root node. The element at the top of our tree is always considered the root node of the Binary Tree.

So what are the remaining nodes called?

Child Nodes
^^^^^^^^^^^

The next level down from our root node would be the child nodes of our root node.

So in the example above of

.. sourcecode::

         5
      19   2
    4

5 is our root node, and it has two children: ``19`` and ``2``.

Even though both ``19`` and ``2`` are considered child nodes of ``5``, we may want to distinguish between the children so we have further classifications: ``left child`` and ``right child``.

In the example above ``19`` would be the ``left child`` of ``5``, and ``2`` would be the right child of ``5``.

Taking the list we had before we have ``[5, 19, 2, 4]``.
- ``5`` becomes the root node
- ``19`` becomes the left child of ``5``
- ``2`` becomes the right child of ``5``

This leaves us with one final number in our list: ``4``. We have met the total number of children that ``5`` can have with two (both ``19`` and ``2``) so ``4`` cannot be a child of ``5``. So in this case we move down a level to the left child of our now full node.

So in this case ``4`` will become the left child of the node ``19``.

Depth
^^^^^

The final term you should learn for Binary Tree is ``depth``. ``Depth`` refers to the number of levels in a given Binary Tree.

.. sourcecode::

         5
      19   2
    4

With the example we have used throughout this section we can see 3 clear levels to our tree. ``5`` is the first level, ``19`` and ``2`` are at the second level and ``4`` is at the third level. The depth of this tree is 3.

.. note::

  What you have seen is the basic algorithm for turning a list into a Binary Tree. In future sections you will see slightly more complex algorithms for creating a balanced Binary Tree from a list.

The Importance of Order
-----------------------

What we have seen so far is the basic terminology for Binary Tree and a simple algorithm that takes a list and converts it into a Binary Tree. However, the power of Binary Trees in computer science is performing performant (``O(log n)``) search, insertion, and deletion. With an unordered Binary Tree you cannot achieve ``O(log n)``.

Let's take an example of finding a specific value in the Binary Tree we created above.

.. sourcecode::

         5
      19   2
    4

What if we are looking for the value ``2``. We would first check the root node ``5``. Does ``5`` equal ``2``? No, we need to move on. Let's check the left node of the root node. ``19``. Does ``19`` equal ``2``. It does not. Let's check the left node of the ``19`` which is ``4``. Does ``4`` equal ``2`` no. Since we don't have any left nodes let's move back up a level. ``19`` does not have any right nodes so let's move up a level. ``5`` has a right node that is ``2``. Does ``2`` equal ``2`` yes! We found our value in 4 checks which happens to be the length of our data structure. The worst case was ``O(n)`` which isn't awful, but not as good as a binary search ``O(log n)``.

However, what if this Binary Tree was ordered so that the left child was always smaller than the parent node, and the right child is always greater than or larger than the parent? What if we tried to put our Binary Tree is a specific order?

.. sourcecode::

         5
      4     19
    2

Now if we try to search through our Binary Tree, since it is ordered and follows the rule that every left child is smaller, and every right child is larger or equal to the parent node, we can easily do a binary search.

If we are looking for the value ``2``. We would first check the root node ``5``. Does ``5`` equal ``2``. No, but now we can make an informed decision. If ``2`` is smaller than ``5`` we know to check the left child. If ``2`` is greater than or equal to ``5`` we know to check the right child. What is the left child of ``5``, ``4``. Does ``2`` equal ``4``. No. Is ``2`` smaler than, or greather than or equal to ``4``. It is smaller so we need to check the left child again. Does ``2`` equal ``2``? Yes! We found the matching value in one less iteration than the previous check.

A Binary Tree that is the order mentioned above makes it very easy to visualize and perform Binary Searches!

Concept Checks
--------------