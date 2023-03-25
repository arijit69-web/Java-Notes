- Object class is parent class of all the objects.
- Sabhi class Object class ko inherit karte hai.

- hashCode() and equals() methods have been defined in Object class which is the parent class
  for java objects.For this reason all java objects inherit a default implementation of these methods.

```
class Pen{
    int price;
    String color;
    public Pen(int price,String color)
    {
        this.price=price;
        this.color=color;
    }
}
public class Main{
public static void main(String args[])
{
    Pen pen1=new Pen(10,"blue");
    Pen pen2=new Pen(10,"blue");
    System.out.println(pen1.equals(pen2));   
    System.out.println(pen1==pen2);          
}
}

---------------------------------------------
OUTPUT
---------------------------------------------
false
false
```
- Qs. The value of price and the value of color of both the objects pen1 and pen2 are same but still the output is False - Why?
Ans: Because 2 objects memory mai alag alag jaga store hai and default implementation of equals() and == kya karta hai? Ager same reference ko point nahi kar rha hai to wo alag alag cheez hai.

- Now how to change the behaviour?
Ager pen ke color alag hai yaha phir pen ke price alag hai - To fir wo dono pen alag alag hai nahito ager dono pen ke price or color equal hai to wo dono pen same hai.

```
class Pen{
    int price;
    String color;
    public Pen(int price,String color)
    {
        this.price=price;
        this.color=color;
    }
    public boolean equals(Object obj)
    {
        Pen that=(Pen)obj; //cast to Pen Object as obj is of Object type
        boolean isEqual=this.price==that.price&&this.color.equals(that.color);
        return isEqual;
    }
    public int hashCode()
    {
        return price+color.hashCode();
    }
    
    
}
public class Main{
public static void main(String args[])
{
    Pen pen1=new Pen(10,"blue");
    Pen pen2=new Pen(10,"blue");
    System.out.println(pen1.equals(pen2));  
    System.out.println(pen1==pen2);          
}
}

---------------------------------------------
OUTPUT
---------------------------------------------
true
false
```

- pen1 and pen2 dono alag alag memory mai hai lekin wo dono objects same hai kiuki humne unka equals method define kardia hai.According to humare equals() method implementation wo dono objects equal tab honge jab uss dono objects ke price oro color same honge.

Now if we put these 2 objects pen 1 and pen 2 in a HashSet.The HashSet size is equal to 2.
But it should be 1 as both the objects pen1 and pen2 are equal and HashSet only allows unique values.
So we also have to write hashCode() method of this Pen class.hashCode() and equals() methods sath ke sath chalte hai.
Jo cheeze equals define karne k liye use kar rahe hai wo same to same cheeze humko hashCode() define karne ke liye use karne hai i.e. price and color in this case.
```
public int hashCode()
    {
        return price+color.hashCode();
    }
```
Ab set ka size 1 hoga kiuki humne Pen class ke ander hashCode() and equals methods define kardia hai.
Now, dono objects pen1 and pen2 same memory main point kar rha hai.Do pens ager same hai to unke HashCode bhi same hone chaiye. 

**HashCode and Equals - Contract**

- If two objects are equal then they must have same hashcodes.
- If two objects have same hashcodes they may of may not be equal. [Collision Case]

**Important Notes**

- Always use same attributes of an object to generate both hashCode() and equals() methods.
- equals() must be consistent (if the objects are not modified then it must be returning the same value).
- Whenever a.equals(b) then a.hashCode() must be same as b.hashCode().
- If u override one,you should override other.