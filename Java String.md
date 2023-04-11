String -> Inbuilt class name in Java
Declaration:
- String name="Arijit";
- String full_name="Arijit Sarkar";

```
Scanner sc=new Scanner(System.in);
String name = sc.next(); // For taking 1 word as an input
String name = sc.nextLine(); // For taking 1 para or 1 line as an input
char c = sc.next().charAt(0); // For taking 1 single character as an input
```

- if(s1.compareTo(s2))

compareTo check 3 cases
1. s1 > s2 : +ve or > 0
2. s1 == s2 : 0
3. s1 <> s2 : -ve or < 0

eg. s1=hello, s2=wello
Ascii value of w = 119
Ascii value of h = 104
Therefore, compareTo() will return 104 - 119 = -15

hello < wello

'a' is given less priority than 'z' or we can say ('a' < 'z').

eg. s1=aahello, s2=aabello
Ascii value of h = 104
Ascii value of b = 098
s1 > s2 as 'h' > 'b'
Therefore, 104 - 98 = 6

String is immutable.
Immutable means : Ager ap ekbar koi memory ke ander apne ek string banadi to ap change nahi kar sakte uss string ko, nahi kuch delete kar sakte hai, nahi modify, nahi add kar skate hai again.
* '==' bohut cases mai fail ho jata hai so we use, .equals() method to compare the value of 2 strings.

String is a class -> Non-Primitive Datatypes
String anotherName = new String("Arijit); // Object of a string

Both `equals()` method and `==` operator are used to compare 2 objects in Java.

But == operator compares reference or memory location of objects in a Heap, whether they point to the same location or not.

.equals() method for content comparison or we can say .equals() evaluates to comparison of values in the object.

Heap is a memory where all variables are stored. Since string is very very frequently used by the user. So without keeping the string in the heap, it decided to keep the string in another area called `String Pool Area`.





