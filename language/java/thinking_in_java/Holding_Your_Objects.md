# <font color=#f5a37a>Holding Your Objects</font>
**It's a fairly simple program that only has a fixed quantity of objects with known lifetimes.** 

In general, your programs will always be creating new objects based on some criteria that will
be known only at run time. Before then, you won't know the quantity or even the exact type
of the objects you need. To solve the general programming problem, you need to create any
number of objects, anytime, anywhere. So you can't rely on creating a named reference to
hold each one of your objects:

since you'll never know how many of these you'll actually need.

Most languages provide some way to solve this essential problem. Java has several ways to
hold objects (or rather, references to objects). The compiler-supported type is the array,
which has been discussed before. An array is the most efficient way to hold a group of objects,
and you're pointed towards this choice if you want to hold a group of primitives. But an array
has a fixed size, and in the more general case, you won't know at the time you're writing the
program how many objects you are going to need, or whether you need a more sophisticated
way to store your objects - so the fixed-sized constraint of an array is too limiting.
