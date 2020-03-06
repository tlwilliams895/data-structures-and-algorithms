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


.. console output
        2

We can see from the example that our next level looks like this

  2 
1   0

What do we call this next level?

Child Nodes
^^^^^^^^^^^

.. using the same list -> this is how we get the child nodes from the list 

.. console output

        2
      1   3

.. explain that one is called the **left child**, and the other is called the **right child**
.. highlight and index
.. complete the tree all the way down each child will get it's own child

.. statement of what we have done is converting a list to a BT

.. lead-in to balanced tree

The Importance of Order
=======================

.. how does order affect searching in a list (it's still O(n)), but we can make assumptions smallest is first, largest is last -- can do a binary search

.. as covered binary search is the optimal search algorithm
how it applies to lists
segue to how it applies to BT

.. order matters in binary trees
.. will be broken if the BT is not ordered
  10
 2  5

.. segue to ordering the tree into a sub-type of BT called a BST. BST excels in usage operations. a BST is balanced (use BST balanced def)...

.. show same example but now in order to recognize power of BST
  2
5  10

.. in the next section we will explore how a BST works to support the performance measures


An Ordered Binary Tree
^^^^^^^^^^^^^^^^^^^^^^

.. we mean ordered as far as BST's are balanced -- we do not care about are even need to mention binary tree balancing
.. serve as the segue to BST
.. identify that the benefits of BT are only realized in a BST

.. root node is median of a range of values -- greater or equal values go to the right child, lesser values go to the left child

.. diagram

.. note about seeing the term balanced refering to just BT, and not BST, but for the purposes of this class we we say balanced we are always referring to a balanced BST

Concept Checks
--------------