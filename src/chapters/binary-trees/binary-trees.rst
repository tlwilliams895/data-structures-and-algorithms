============
Binary Trees
============

.. relevant objectives
- Understand the conceptual structure of a binary tree

.. relevant notes from paul
- Understand the conceptual structure of a binary tree

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
yourself, but knowing how they work is benefical in understanding how certain
sorting, or searching algorithms perform.


Binary Tree
-----------

Root Node
^^^^^^^^^

Child Nodes
^^^^^^^^^^^

Left Child
^^^^^^^^^^

Right Child
^^^^^^^^^^^

Complete Tree
^^^^^^^^^^^^^

every level, except the last level if completely filled

diagram

Full Tree
^^^^^^^^^

Each node has exactly 0, or 2 nodes

diagram

Perfect Tree
^^^^^^^^^^^^

All nodes have exactly 2 nodes, except for the final level of depth in which all nodes have 0 attached nodes

A perfect tree is a full tree, but a full tree isn't always a perfect tree.

diagram

Balanced Tree?
^^^^^^^^^^^^^^

left and right subtrees of every node differ in height by no more than 1

diagram

.. TODO:: do we care about all four of these classifications? If not just Balanced, and Full is my guess.

Concept Checks
--------------