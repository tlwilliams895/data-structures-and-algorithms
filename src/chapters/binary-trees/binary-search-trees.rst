Binary Search Tree
===================

As we saw from our final example in the previous section a binary tree that follows a couple of additional rules becomes a balanced binary tree or as we call it in Computer Science a **binary search tree**.

Binary Search Tree
------------------

A binary search tree, is a binary tree that is balanced. Like the binary tree
each node can have no more than two child nodes. But in the case of balancing the binary tree, which creates a binary search tree,
there are two additional rules: 

#. The left child most be a smaller value than the parent node
#. The right child most be a greater than or equal in value to the parent node

Let's see an example of a balanced binary tree which is a binary search tree.

::

       __7__
      /     \
     3       15
    / \     /  \
   1   3   8    17

This binary tree is balanced. 7 is our root node. It has two children: 3 the left child node which is smaller in value than its parent (7) and 15 the right child node which is greater than or equal to its parent (7).

3 has two children: 1 the left child is smaller in value than its parent and 3 which is greater than or equal to its parent.

15 has two children: 8 the left child is smaller in value than its parent and 17 which is greater than or equal to its parent.

This is an example of balanced binary tree, which is also known as a binary search tree!

Convert Ordered List to Binary Search Tree
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Taking the example we saw for binary search let's turn it into a binary tree.

Collection: (1, 2, 3, 4, 8, 9, 10, 14, 18, 20, 30)

::

         ____9______
        /           \
       3             18
      / \           /  \
     2   4         14   30
    /     \       /    /
   1       8     10   20

In this example we most know what our middle most value is and it becomes our
root node: 9. From here we need to know what is the middle of the values that
are greater than 9 in our collection: 18. We also need to know what is the
middle of the values that are less than 9 in our collection: 3.

Now from both of those nodes we need to keep going. From 18 for the left child
node we need to know what is the middle of the remaining nodes between 9 and
18? In this case it would be 14. From 18 for the right child node we need to
know what is the middle of the remaining nodes between 18 and the last element
of the array (rounding up): 30.

We would need to keep this up to fill out the rest of the tree.

Balance
^^^^^^^

As a final point a binary search tree follow the rules of a binary tree, and the additional rule that all left child nodes must be smaller than the parent node, and all right child nodes must be greater than or equal to the parent node.

The benefit of a binary search tree is that we can perform value search, value insertion, and value deletion in *O(log n)* time.

In the next section of the chapter we will look at adding (insertion), and deleting (deletion) items from the binary search tree.

Concept Checks
--------------

.. todo:: add concept checks
