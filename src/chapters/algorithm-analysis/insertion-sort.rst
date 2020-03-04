Insertion Sort
==============

.. IDEA:
  case studies:
    in main doc: pseudocode
    link to: directory of implementations in various languages
      c# for this first draft

.. TODO:: Link back to the recursion lesson in LC101.

Sorting
-------

``Sorting`` is the act of taking a collection of data and rearranging it into a specific order. The order can be numerical ascending, numerical descending, alphabetical, by time, etc,.

Some of the most famous algorithms are sorting algorithms. Sorting algorithms are important for many reasons, but for the purposes of this class they are primarly important because searching through unsorted data always takes ``O(n)`` time. You have to check against every single value every time you search for something. However, if your data is sorted you can implement different searching algorithms that are more performant than ``O(n)``. We will see some of these searching algorithms in future lessons.

That being said not all sorting algorithms are equal. A sorting algorithm comes with it's own Big-O Notation, making some sorting algorithms better depending on the incoming data.

Throughout this book we will introduce a number of various sorting algorithms. We will provide information about each sort which will be helpful in deciding which sort is better for which dataset. Some are more efficient for small sets of data, or for large sets of data. Most programming languages already have these sorting algorithms as a part of their standard library when working with data structures. However, it is valuable to know how they work, and how to implement them if you need to write your own custom sorting algorithm.

Insertion Sort
--------------

The first sorting algorithm we will be looking at is ``Insertion Sort``. This sort can be implemented in a couple of different ways, but we will be showing examples that sort a collection of numbers in ascending order. That is to say the smallest number will be the first element in the array, and the largest number will be the last element in the array.

An Insertion sort is a sorting algorithm that puts a collection of data into ascending numerical order. It would take an array like this ``[3,6,2,4,1,10]`` and return an array like this ``[1,2,3,4,6,10]``

An Insertion sort is an algorithm that loops through all the elements of an array and compares that value to all the previously sorted elements of the array. If it finds that the currently selected value is smaller than the value it is comparing to, it will insert that value into the position of the value it is being compared to. When an insert happens the nested loop breaks, and the outer loop moves to the next value in the remaining unsorted values of the array.

The insertion sort achieves this order by looping through all the elements of an array, starting with the second element, and compares that element to every element that comes before it. If it finds that the element is smaller than any of the previous comparison elements it will move the element into the position of the comparison element. After it has this element in place, it moves to the next element in the array. In essence the code requires a loop nested inside of another loop making it's Big-O notation ``O(n^2)``.

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

Again we have a nested loop the Big-O notation for an Insertion Sort algorithm would be ``O(n^2)``.

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