# <font color=#f5a37a>Holding Your Objects</font>

## <font color=#55aa7f>List</font>
Basic concepts
```java
//: holding/SimpleCollection.java
import java.util.*;

public class SimpleCollection {
	Collection<Integer> c = new ArrayList<Integer>();
	for(int i = 0; i < 10; i++)
		c.add(i);	// Autoboxing
	for(Integer i : c)
		System.out.print(i + ", ");
}
```

Since this example only uses Collection methods, any object of a class inherited from
Collection would work, but ArrayList is the most basic type of sequence.
