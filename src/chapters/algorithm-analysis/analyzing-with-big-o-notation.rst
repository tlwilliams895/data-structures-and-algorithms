Analyzing Algorithms With Big-O Notation
========================================

Intro
-----

Analyzing algorithms with Big-O Notation comes down to basic arithmetic. An algorithm is just a series of steps, or operations, performed by a computer. Every step itself can be classified by Big-O notation.

.. sourcecode::

   print "Hello World!"

The above pseudocode has one operation. The computer must print the string "Hello World!" to the console. The Big-O notation of this one step would be ``O(1)``.

What about loops? We don't necessarily know how many items may be in a collection of objects.

.. sourcecode::

   for student in students

A pretty common for loop, that just loops through all the individual students. The computer must do something for every item in the collection. The Big-O notation of this one step would be ``O(n)``.

``n`` represents the number of individual items in the collection ``students``.

Every single line of code can have Big-O notation to represent it's runtime complexity. In the next section we will see how we can combine various Big-O Notation of discrete steps to find the overall Big-O Notation for an entire algorithm.

Big-O Arithmetic
----------------

Figuring out the Big-O notation for a series of steps simply takes some basic arithmetic. Additive arithmetic to be precise. We predominately use addition, and multiplication. We don't have a need for subtraction, or division because we are always adding steps together.

We do reduce our Big-O Notation to  more easily communicate ideas with others, but the topic of cancellation will come later in this section. Right now we are focused on adding individual steps together to calculate the overall Big-O Notation for an algorithm.

Sum
^^^

.. sourcecode::

   print "Hello World!"
   print "Goodnight World!"

The above pseudocode has two operations. The computer must print the string "Hello World!" and then the computer must print the string "Goodnight World!".

- ``print "Hello World!"`` is ``O(1)``
- ``print "Goodnight World!"`` is ``O(1)``

So we could say the Big-O notation for both of these steps together would be ``O(1 + 1)`` or ``O(2)``.

.. admonition:: note

   Later in this section we will discuss the difference between ``O(1)`` and ``O(2)``.

Let's consider when a step of an algorithm may have sub-steps.

.. sourcecode::

   if status is true
       print("True")

Again this collection of code has two discrete steps:

- ``if status is true`` is ``O(1)``
- ``print("True")`` is ``O(1)``

So again we get a grand total of ``O(2)``.

Multiplication by Constant
^^^^^^^^^^^^^^^^^^^^^^^^^^

Revisiting our for loop from the intro we can learn about Big-O multiplication.

.. sourcecode::

   for student in students
       print student.first_name

Now our for loop has a substep!

- ``for student in students`` is ``O(n)``
- ``print student.first_name`` is ``O(1)``

We need to use some basic arithmetic to combine these into ``O(n(1))`` which is to say for every student in ``n`` they each have one operation: ``print student.first_name``.

What if we loop through the same collection twice?

.. sourcecode::

   for student in students
       print student.first_name
   for student in students
       print student.last_name

In this case we know each for loop can be represented by ``O(n(1))`` and we simply need to add them together ``O(n(1) + n(1))`` which is: ``O(2n(1))``.

Product
^^^^^^^

What happens when we nest a loop? We are no longer multiplying constants, but multiplying collections of unknown size.

.. sourcecode::

  for student in students
     for grade in student.grades

- ``for student in students`` is ``O(n)``
- ``for grade in student.grades`` is ``O(n)``

This results in some basics arithmetic like this: ``O(n * n)`` or also known as ``O(n^2)``.

Figuring out the Big-O Notation for an algorithm can be simply done by figuring out the individual steps of an algorithm and then using some basic arithmetic to combine the individual steps!

Big-O Notation Cancellation
---------------------------

.. TODO:: cancellation section here before the examples of each?

Breaking Down Common Big O Notations
------------------------------------

In the previous chapter we learned about a collection of commonly used Big O Notation (constant, n, n^2, log n). Let's look at the pseudocode to determine how these equations were derived.

O(1) Analysis
^^^^^^^^^^^^^

.. TODO:: introduce the idea of putting them into functions and being a little more in depth.

.. sourcecode::

   function printMessage(message) {
     print message
   }
   
In the instance of printing some message to the console the action does not depend on the size of the data coming in. Only one operation is performed every single time this function is invoked. A very long message being passed into this function may take a few more milliseconds to display the message to the console, but the number of operations is always constant.

We would consider this function to be constant time represented in Big O Notation by: ``O(1)``.


.. sourcecode::

   function printPersonalMessage(person, message) {
     print "Welcome " + person + "!"
     print message
   }

This example has two operations. It prints two messages to the console. This is another representation of constant time.

The correct Big O Notation for this is: ``O(1)``.

You may be thinking the Big O Notation should be: ``O(2)`` because there are two operations being performed, and although you are correct about the number of operations being performed the usefullness of Big O Notation is to compare the performance of one algorithm to another algorithm. We are less concerned with individual operations unless those operations are dependant on a collection of data. So in this example we simply reduce the extra operations to the simplest notation. Which would be: ``O(1)``. After all ``O(1)`` represents constant time, and it doesn't matter how many individual steps there are, those steps will always execute in constant time.

O(n) Analysis
^^^^^^^^^^^^^

.. sourcecode::

   function sumNumbers(arr) {
     sum = 0
     for number in arr
         sum += number
     return sum
   }

In this example we are calculating the sum of a collection of numbers. 

In this function we must loop through each number in our collection and add that number to our sum variable. In essence we are performing an operation (adding a number to our sum variable) for every element in our collection. So the time it will take this function to run is dependant on the size of the data coming into the function.

We would consider this function to be represented in Big O Notation by: ``O(n)`` which refers to the size (number of elements in the collection) of the incoming data.

.. sourcecode::

   function averageNumbers(arr) {
     sum = 0

     for number in arr
         sum += number
     
     total = 0
     
     for number in arr
         total += 1
     
     return sum / total
   }

In this function we are calculating the average value of a collection of numbers. We loop through our collection first to find the sum, and then we loop through the collection again to figure out the length of the collection. Finally, we return the average by dividing the sum by the total number of elements in our collection.

The Big O Notation of this algorithm is: ``O(n)``.

Similar to the example we saw in our first example we reduce the number of times we have to loop through the data, because it's only dependant on the size of the data.

Again you may argue that the actual equation should be: ``O(2n + 1)`` because we have to loop through the collection two times and we have 1 constant operation (sum / total), and in practicality you would be correct. But for the sake of comparison of various algorithms, the benefit comes in having a common language to refer to each algorithm. In this functions case it is only dependant on the size of the collection (regardless to how many times it loops through the data) which would be regarded as ``O(n)``.

We effectively took ``O(2n + 1)`` and cancelled the constant operations, and the number of times we looped through n leaving us with ``O(n)``. Again this is our way of saying this algorithm's runtime complexity is dependant on the size of the collection being passed into the function.

O(n^2) Analysis
^^^^^^^^^^^^^^^


O(log n) Analysis
^^^^^^^^^^^^^^^^^

Big O Operations
----------------




concept checks
- what are the big o operators?
- what is cancelling?
- when is it appropriate to cancel?
- what is the relationship of the a specific step in an algorithm, vs the overall algorithm big o?
- why do you look for the highest order term? -- answer it's what has the biggest impact as the data (n) increases
- what is a primitive operation?
- analyzing section is the part to do the pseudocode of the constant, n, n^2, log n, etc

Worst Case?
-----------

Bring back the first section definition highlighting worst case or upper bounds.

- What do we mean by worst case? 
- What is best case? 
- Why don't we use Big O notation for best case?

.. TODO: Should Big O Operations be discussed here? or analyzing with big o notation?

Big O Operations
----------------

What do we mean by operations?

- Sum
- Product
- multiplication by product