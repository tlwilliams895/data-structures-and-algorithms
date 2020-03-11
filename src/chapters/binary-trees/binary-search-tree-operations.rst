=============================
Binary Search Tree Operations
=============================

.. relevant objectives
    - Explain how to carry out binary search on a binary search tree
    - Understand Binary Search Tree Operations and their Big-O efficiency
    - Understand common operations on BSTs and their Big-O efficiency
        - insert
        - remove
        - traverse

.. relevant notes from paul
    - Binary Search Tree Search (how is it done)
    - Binary Search Tree operations (insert, remove, traverse)
    - Big O of binary search tree operations, and binary search

BST Operations
--------------

.. destructive operation vs non-destructive operation? Search is non-destructive, but inserting, and removing is destructive.
When performing operations on a Binary Search Tree we typically think of three things:
    - Searching for values
    - Inserting new values
    - Deleting existing values

Inserting, and deleting requires a change to the Binary Search Tree which we consider destructive actions as they alter the underlying structure of our data. The tree can remain balanced by following the rules outlined in the previous sections, however the more destructive actions that are performed on the tree the less performant the tree becomes. It moves further away from ``O(log n)``, and more towards ``O(n)``. We will show an example in a later section to demonstrate this.

Search
^^^^^^

We have seen Binary Search already through this chapter multiple times, and we have seen how a Binary Search Tree handles a search, but let's go through one final example.

.. sourcecode::

                10
            6       19
          3   9   13    25
         2 5 7   11 14    30

What are the steps for searching for ``13``.
- check the first node ``10``. ``13`` is greater than ``10`` so go to the right node.
- check the right child of the first node ``19``. ``13`` is smaller than ``19`` so go to the left.
- check the left child of previous node ``13``. ``13`` is the number we are looking for and we are done!

This Binary Search Tree is perfectly balanced so our search take ``O(log n)``.

Insert
^^^^^^

.. how do you keep the tree balanced when inserting?

.. Big-O of Insertion

Remove
^^^^^^

.. how do you keep the tree balanced when removing?

.. Big-O of Remove

.. note::

    Insert and Remove are destructive operations as they change the structure of the Tree. When you change the Tree it isn't perfectly balanced. Re-balancing a tree after using a destructive operation goes beyond the scope of this course, but is a fascinating topic. If you want to learn more look into red-black trees which are essentially Binary Search Trees that have the ability to re-balance themselves after each operation.