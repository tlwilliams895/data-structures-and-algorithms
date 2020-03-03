Insertion Sort
==============

.. IDEA:
  case studies:
    in main doc: pseudocode
    link to: directory of implementations in various languages
      c# for this first draft

.. TODO:: Link back to the recursion lesson in LC101.

Importance of Sorting
---------------------

As you have seen from the previous sections algorithms and their analysis are highly dependant on the size of the incoming input. If you have an algorithm that needs to locate a value in an array of data, and your data is not in some form of order, you would be stuck looping through every single element in the array of data ``O(n)``. However, if your data *is sorted* you can use different looping techniques. 

Instead of looping through every element of data, you can compare against an element in the middle and check if the value is greater, or smaller. You can then split the middle again and check if the value is greater, or smaller. You can keep using this strategy until you find the value. This algorithm would still be dependant on the size of the incoming input, but instead of needing to loop over all elements (``O(n)``) you are only looping through a subsection of the elements (``O(log n)``)!

Sorting your array can be highly beneficial when it comes to an algorithm's runtime efficiency.

Throughout this book we will introduce a number of various sorting algorithms. To sort data an algorithm is required, and we will provide the Big-O analysis of each sorting algorithm which will show that not all sorting algorithms are equal. Some are more efficient for small sets of data, or for large sets of data. Most programming languages already have these sorting algorithms as a part of their standard library when working with data structures. However, it is valuable to know how they work, and how to implement them if you need to write your own custom sorting algorithm.

Insertion Sort
--------------

The first sorting algorithm we will be looking at is ``Insertion Sort``. This sort can be implemented in a couple of different ways, but we will be showing examples that always sort a collection of numbers in ascending order. That is to say the smallest number will be the first element in the array, and the largest number will be the last element in the array.

If you have ever played a card game that requires sorting cards you may already be familiar with how this algorithm operates.

An Insertion sort is an algorithm that loops through all the elements of an array and compares that value to all the previously sorted elements of the array. If it finds that the currently selected value is smaller than the value it is comparing to, it will insert that value into the position of the value it is being compared to. When an insert happens the nested loop breaks, and the outer loop moves to the next value in the remaining unsorted values of the array.

It would look something like this:

.. sourcecode::

   [4, 3, 8, 7, 2, 10] // original unsorted array

   // pass 1 -- sorted elements: [4] comparison value: 3
   // 3 is smaller than 4 so it needs to be moved before 4 -- since an insert was made move onto the next value in the un-sorted array
   [3, 4, 8, 7, 2, 10] // new array after first pass
   
   // pass 2 -- sorted elements: [3, 4] comparison value: 8
   // 8 is not smaller than 3
   // 8 is not smaller than 4, and we have made it through all the already sorted numbers, nothing needs to be changed
   [3, 4, 8, 7, 2, 10] // array after second pass
   
   // pass 3 -- sorted elements: [3, 4, 8] comparison value: 7
   // 7 is not smaller than 3
   // 7 is not smaller than 4
   // 7 is smaller than 8 so it needs to be moved before 8 -- since an insert was made move onto the next value in the un-sorted array
   [3, 4, 7, 8, 2, 10] // array after third pass

   // pass 4 -- sorted elements: [3, 4, 7, 8] comparison value: 2
   // 2 is smaller than 3 so it needs to be moved before 3 -- since an insert was made move onto th enext value in the un-sorted array
   [2, 3, 4, 7, 8, 10]

   // pass 5 -- sorted elements: [2, 3, 4, 7, 8] comparison value: 10
   // 10 is not smaller than 2
   // 10 is not smaller than 3
   // 10 is not smaller than 4
   // 10 is not smaller than 7
   // 10 is not smaller than 8 and we have made it through all the already sorted numbers, nothing needs to be changed
   [2, 3, 4, 7, 8, 10] // we have made it through all the elements of the array so we know we have a sorted array

This algorithm starts with the second element of the array (since it depends on comparing 2 values at a time), and compares one specific number to all the previously sorted numbers inserting it into the sorted numbers until it has run through all the original elements of the array.

In the example above to completely sort the array we need to first loop through all the elements of the array, and then from within that intial loop we will need to loop through all the currently sorted values. Since we have a nested loop the Big-O notation for an Insertion Sort algorithm would be ``O(n^2)``.

Non-Recursive Solution
^^^^^^^^^^^^^^^^^^^^^^

An Insertion sort can be solved recursively or non-recursively we will show you the solution both recursively, and non-recursively.

What does the solution look like in C#?

How do we calculate this algorithm's run time complexity?

How do we now put that run time complexity into Big O notation?

Recursive Solution
^^^^^^^^^^^^^^^^^^

What does the solution look like in C#?

How do we calculate this algorithm's run time complexity?

How do we now put that run time complexity into Big O notation?