Binary Search Tree Operations
=============================

BST Operations
--------------

When performing operations on a binary search tree we typically think of three things:
    - Searching for values
    - Inserting new values
    - Deleting existing values

Inserting, and deleting requires a change to the binary search tree which we consider destructive actions as they alter the underlying structure of our data. The tree can remain balanced by following the rules outlined in the previous sections, however the more destructive actions that are performed on the tree the less performant the tree becomes. It moves further away from *O(log n)*, and more towards *O(n)*. We will show an example in a later section to demonstrate this.

Search
^^^^^^

We have seen Binary Search already through this chapter multiple times, and we have seen how a binary search tree handles a search, but let's go through one final example.

::

                10
            6       19
          3   9   13    25
         2 5 7   11 14    30

What are the steps for searching for ``13``:

- check the first node ``10``. ``13`` is greater than ``10`` so go to the right node.
- check the right child of the first node ``19``. ``13`` is smaller than ``19`` so go to the left.
- check the left child of previous node ``13``. ``13`` is the number we are looking for and we are done!

This binary search tree is perfectly balanced so our search take at worst *O(log n)*.

Insert
^^^^^^

Let's take the example from above and add a couple of new values to it.

::

                10
            6       19
          3   9   13    25
         2 5 7   11 14    30

First lets add a new largest value: ``31``

::

                10
            6       19
          3   9   13    25
         2 5 7   11 14    30
                            31

Lets consider the logic. We want to add a new value ``31``. We first check our root node ``10``. Our new value (``31``) is larger than 10. So this most go as the right child. However, the right child of ``10`` is already taken with the value of ``19`` so we keep comparing. Our new value ``31`` is greater than ``19`` so we need to put our new value in the right node spot of ``19``, however that spot is already taken by ``30``. Our new value ``31`` is larger than ``30`` so we need to put ``31`` into right child node of ``30``. That spot is currently available so we can put our new value ``31`` as the right child of ``30``.

To add a new value we simply perform a binary search to determine where the new position goes.

Lets see another example. Lets add the value ``4`` to our new BST.

::

                10
            6       19
          3   9   13    25
        2  5 7   11 14    30
          4                 31

Considering the logic. ``4`` is smaller than our root node ``10``. It's smaller than the left child ``6``. It's larger than the left child ``3``. It's smaller than the right child ``5``, and ``5`` has an empty left child node which is where we put ``4``.

Let's add another value as an example ``13``.

::

                10
            6       19
          3   9   13    25
        2  5 7   11 14    30
          4        13       31

The value we are inserting is a value already on our tree ``13``.

Let's walk through the logic to figure out how it was inserted into this spot.

``13`` is greater than our root node ``10`` so we need to check the right child. ``13`` is less than ``19`` so we need to check the left child. ``13`` is greater than or equal to ``13`` so we need to check the right child. ``13`` is less than ``14`` so we need to check the left child which is empty and becomes the spot for our new value ``13``.

As a final insertion example let's add ``10``.

``10`` is greater than or equal to our root node. ``10`` is less than ``19``. ``10`` is less than ``13``. ``10`` is less than ``11``. So it should go into the left child of ``11``.

::

                10
            6       19
          3   9   13    25
        2  5 7   11 14    30
          4     10 13       31

Since our insertion into a binary search tree relies on a Binary Search to find the position of the new node, this operation is performed in *O(log n)* time!

Remove
^^^^^^

Remove is similar to Insert in that it relies on a Binary Search to find the initial value to be removed. Using the final BST we had at the end of the last section let's try to remove ``31``.

::

                10
            6       19
          3   9   13    25
        2  5 7   11 14    30
          4     10 13       

To find this value a binary search was performed:

- ``31`` is greater than ``10``
- ``31`` is greater than ``19``
- ``31`` is greater than ``25``
- ``31`` is greater than ``30``
- ``31`` equals ``31``

The value ``31`` was found. The next step is to see if ``31`` has any child nodes. It does not so it can be deleted without further action.

Let's try removing a value that has child nodes: ``3``

::

                10
            6       19
          2   9   13    25
           5 7   11 14    30
          4     10 13 

Something interested happened. ``3``'s left child took the place of ``3``. Why did that happen? 

Let's walk through the logic a binary search was performed to find the value:

- ``3`` is less than ``10``
- ``3`` is less than ``6``
- ``3`` equals ``3``!

We found the value through a Binary Search. But what do we know about ``3``?

We know is that ``3`` was the left child of its parent node ``6``. To keep our binary search tree balanced we need to ensure that any value placed into ``3``'s position is still follows our rules for our binary search tree. In this case ``3`` only has one total child, and that child doesn't have any children. So we can simply move it's child into its current spot in the tree. So in this case ``3``'s only child ``2`` moves into ``3``'s position in the binary search tree.

Let's try it on the right side to see what happens. Let's remove the value ``19``.

::

                10
            6       25
          2   9   13    30
           5 7   11 14    
          4     10 13 

.. note::

    Insert and Remove are destructive operations as they change the structure of the Tree. When you change the Tree it isn't perfectly balanced. Re-balancing a tree after using a destructive operation goes beyond the scope of this course, but is a fascinating topic. If you want to learn more look into red-black trees which are essentially binary search trees that have the ability to re-balance themselves after each operation.
