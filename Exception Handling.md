## Exceptional Handling

Exception is an error event that can happen during the execution of the program and disrupts it's normal flow.

Exception in java can arise :

- Wrong data entered by the user
- Hardware Failure
- Network Connection Failure
- DB/Server down

java provides a robust and object oriented way to handle exception scenerios, known as java Exceptional Handling.

### Throwing the Exxception

- Java being an object oriented programming language, whenever an error occurs while executing a statement, creates an exception object. The exception object contains a lot of debugging info such as method hierarchy. eg. line no. where exception occured, type of exception etc.

- Normal flow of the program halts and JRE tries to find someone that can handle the raised exception.

- When exception occured in method, the process of creating the exception object and handling it over to runtime environment is called _throwing the exception_.

```
// Java Program to Handle Divide By Zero Exception
import java.io.*;
class GFG {
	public static void main(String[] args)
	{
		int a = 6;
		int b = 0;
		System.out.print(a / b);
		// this line Throw ArithmeticException: / by zero
	}
}
```

**Output:** Exception in thread main: ArithmeticException: / by zero

Runtime main pta chala and not in compile time.

Try, catch are 2 keywords used in Exceptional Handling.

```
// Java Program to Handle Divide By Zero Exception
import java.io.*;
class GFG {
	public static void main(String[] args)
	{
		int a = 5;
		int b = 0;
		try {
		    int c = a/b; // exception throw hua
			System.out.println(c); // yeh value print nahi hoga
		}
		catch (ArithmeticException e) {
			// Exception handler
			System.out.println(
				"Divided by zero operation cannot possible");//kya error aya hai message de deta hai
		}
        System.out.println("Very Important Code");
	}
}
```

**Output:** Divided by zero operation cannot possible
</br>
Very Important Code

- Code shut down nahi hua hai and output mai divide by zero exception message print hua and Very Important Code.
- But if we don't use try, catch block jaha pe exception ayega wohi code rukh jaiga and program will crash and exit.
  "Very Important Code"-> line nhi print hoga kiuki code crash hogya hai ussi line main jaha pe exception aya tha.

JRE dekha @ line no. 10 usko ek exception mila uske baad usne koi line execute nahi kia. Usne program wohi halt kardia as we have not use try catch. JRE ne ek exception object banya and exception throw kardia and program exit hogya hai.

But if we use try catch block, exception automatically handle hogya by JRE and program halt nahi huaor crash nahi hua and furthur lines bhi execute hua.

### Catching the Exception

- Once the runtime receives the exception object it tries to find the handler for the exception. Exception handler is the block of code that can process the exception object.
- The logic to find the exception handler is simple - starting the search in the method where error occured and if no appropiate handler formed, then move to caller method and so on.

So if method call stack is A -> B -> C and exception is raised at method C, then seatrch appropiate handler will move from c -> B -> A.

If appropiate exception handler is formed, exception object is passed to the handler to process it. The handler is said to be "Catching the Exception".

```
main()
  ^
  |
  |
func1()
{
    func2();
}
  ^
  |
  |
func2()
{
    func3();
}
  ^
  |         // Checking kaha pe Exception Handle hua hai
  |
func3()
{
    c=a/0;
}

```

Ager is poore process mai hum kahi bhi exception handle kia hai to wo wohi se exception handle ho jaiga automatically.

So ager exception handle nahi hota hai in this case then it will show or print the StackTrace of the whole process.

### Try block with multiple catch blocks

```

try{

}
catch()
{

}
catch()
{

}
catch()
{

}

```

**Finally Keyword**

The finally keyword is used to create a block of code that follows a try block. A finally block of code always executes, whether or not an exception has occurred. Using a finally block allows you to run any cleanup-type statements that you just wish to execute, despite what happens within the protected code.

```
public class Tester {
   public static void main(String[] args) {

      try{
         int a = 10;
         int b = 0;
         int result = a/b;
      }catch(Exception e){
         System.out.println("Error: "+ e.getMessage());
      }
      finally{
         System.out.println("Finished.");
      }
   }
}
```

**Output:** Error: / by zero
</br>
Finished.

Finally block is used to close DB connection, close file etc.

### Throw v/s Throws Keyword
- The throw keyword is used inside a function. It is used when it is required to throw an Exception logically.	
- The throw keyword is used to throw an exception explicitly. It can throw only one exception at a time.	

- The throws keyword is used in the function signature. It is used when the function has some statements that can lead to exceptions.
- The throws keyword can be used to declare multiple exceptions, separated by a comma. Whichever exception occurs, if matched with the declared ones, is thrown automatically then.

```
class NegativeRadiusException extends Exception{
    @Override
    public String toString() {
        return "Radius cannot be negative!";
    }

    @Override
    public String getMessage() {
        return "Radius cannot be negative!";
    }
}
public class Main {

    public static double area(int r) throws NegativeRadiusException{
        if (r<0){
            throw new NegativeRadiusException();
        }
        double result = Math.PI * r * r;
        return result;
    }

    public static int divide(int a, int b) throws ArithmeticException{
        int result = a/b;
        return result;
    }
    public static void main(String[] args) {
        try{
            int c = divide(6, 0);
            System.out.println(c);
            double ar = area(-6);
            System.out.println(ar);
        }
        catch(Exception e){
            System.out.println(e);
        }
    }
}
```