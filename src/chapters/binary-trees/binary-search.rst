=============
Binary Search
=============

.. relevant objectives
- Use binary search to efficiently find elements in ordered collections
- Understand and write code to conduct a binary search on an ordered
  collection (eg an array or list)
- Explain why a data set must be sorted before conducting a binary search

.. relevant notes from paul
- Sort (why it's important) (not how)
- Binary Search on an ordered collection
- Big O of binary search

Sort Revisted
-------------
We have seen an insertion sort algorithm. Sorting algos are very popular
algorithms, one of the reasons for their popularity is a sorted collection can
be searched in O(log n) time. O(log n) time is one of the most performant
Big-O notations. Show some examples of O(log n) vs O(n).
How can we achieve O(log n) since it is supieror to O(n) especially as the
datasets get much larger?
Binary Search
-------------
We can achieve O(log n) with a new concept called Binary Search. We have seen
simple search (O(n)) where we loop through each value in a collection and when
we find the match we return it. Binary search is an alternative to simple
search that takes O(log n) time! So how does it work?
It requires a *sorted* collection: (1, 2, 3, 4, 8, 9, 10, 14, 18, 20, 30).
And then it searches the list by taking a split the middle approach. So if our
search value is 18 a binary search would first take the middle most value
(length / 2) which in this case is 9 and say is 9 the number we are looking
for? No it is not. Is our number bigger or smaller than 9? It's bigger so our
search's next stop would be to split the middle between whatever comes after
9, and the last number so 10, and 30. The number in the middle of 10 and 30 is
18. Our Binary search would say is 18 the number? And yes it is! We are done!
We found the correct value in only 2 steps! That wasn't the worst case, we got
the correct number in only 2 steps, so lets walk through this again with the
worst case by choosing one of the numbers on the end as our search value.
Searching for 1 in a binary search.
split the middle of collection.length returns 9.
- Is 9 the number?
  - no. is 1 smaller than 9?
    - yes. so we need to split the middle between the first element and the
      element before 9.
- Is 3 the number?
  - no. is 1 smaller than 3?
    - yes. so we need to split the middle between the first element and the
      element before 3.
- Is 2 the number?
  - no. is 1 smaller than 3?
    - yes. so we need to split the middle between the first element and the
      element before 2.
- There is only one element left in our search area: 1. Is 1 the number?
  - yes -- we found the number in 4 steps.
So for a collection with a length (n) of 11 the best case performance is 1
operation, and the worst case performance is 4 operations. That's certainly
more performant than O(n) (where the best case would be 1, and the worst case
would be 11).
A binary search gives us a much more performant way of finding a value in a
collection! In fact the big o notation for this would be O(log n) or another
way of saying that would be to take the length of the collection and perform a
2 based log on it.
Log2(11) happens to be 3.4594. Which is what we saw with our example above. It
took 4 steps in the worst case scenario!
So now we have a handy equation for calculating how many operations a binary
search would take on any size collection.
- Collection length of 10 -> log2(10) -> 3.3219
- Collection length of 100 -> log2(100) -> 6.6428
- Collection length of 10000000 -> log2(10000000) -> 26.5754
You can see how increasing the size even drastically doesn't increase the
number of operations by much. We are really seeing a benefit of cutting out
half of all numbers in our collection with every new iteration of our sort. A
binary search's worst case performance will always be better than a simple
search's worst case performance when the collection size is the same, and
greater than about 10.
Since Binary Search is so powerful a unique data structure has been created
for it. It's essentially a data structure that is structured around splitting
segments of data in half. We will explore this new structure further in the
next section.
