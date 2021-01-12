# <font color=#f5a37a>Holding Your Objects</font>
**It's a fairly simple program that only has a fixed quantity of objects with known lifetimes.** 
In general, your programs will always be creating new objects based on some criteria that will
be known only at run time. Before then, you won't know the quantity or even the exact type
of the objects you need. To solve the general programming problem, you need to create any
number of objects, anytime, anywhere. So you can't rely on creating a named reference to
hold each one of your objects:

