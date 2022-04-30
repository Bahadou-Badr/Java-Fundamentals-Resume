# Resume - Some Java Fundamentals.

### Enumerated Types
Sometimes, a variable should only hold a restricted set of values. For example,
you may sell clothes or pizza in four sizes: small, medium, large, and extra
large. Of course, you could encode these sizes as integers 1, 2, 3, 4 or characters
S, M, L, and X. But that is an error-prone setup. It is too easy for a variable to
hold a wrong value (such as 0 or m).
You can define your own enumerated type whenever such a situation arises.
An enumerated type has a finite number of named values. For example,
```java
enum Size { SMALL, MEDIUM, LARGE, EXTRA_LARGE };
```
Now you can declare variables of this type:

```java
Size s = Size.MEDIUM;
```

### Mathematical Functions and Constants

The Math class contains an assortment of mathematical functions that you may
occasionally need, depending on the kind of programming that you do.
To take the square root of a number, use the sqrt method:
```java
double x = 4;
double y = Math.sqrt(x);
System.out.println(y); // prints 2.0
```

### Casts

Numeric conversions are
possible in Java, but of course information may be lost. Conversions in which
loss of information is possible are done by means of casts. The syntax for
casting is to give the target type in parentheses, followed by the variable
name. For example:
```java
double x = 9.997;
int nx = (int) x;
```

Now, the variable nx has the value 9 because casting a floating-point value to
an integer discards the fractional part.
If you want to round a floating-point number to the nearest integer (which in
most cases is a more useful operation), use the Math.round method:
```java
double x = 9.997;
int nx = (int) Math.round(x);
```
Now the variable nx has the value 10. You still need to use the cast (int) when
you call round. 

### Strings

Conceptually, Java strings are sequences of Unicode characters. For example,
the string "Java\u2122" consists of the five Unicode characters J, a, v, a, and ™.
Java does not have a built-in string type. Instead, the standard Java library
contains a predefined class called, naturally enough, String. Each quoted string
is an instance of the String class:
```java
String e = ""; // an empty string
String greeting = "Hello";
```
- *Substrings*

You can extract a substring from a larger string with the substring method of
the String class. For example,
```java
String greeting = "Hello";
String s = greeting.substring(0, 3);
```
creates a string consisting of the characters "Hel".

- *Empty and Null Strings*

The empty string "" is a string of length 0. You can test whether a string is
empty by calling
```java
if (str.length() == 0)
```
or
```java
if (str.equals(""))
```

### Multiple Selections–The switch Statement
The if/else construct can be cumbersome when you have to deal with multiple
selections with many alternatives. Java has a switch statement that is exactly
like the switch statement in C and C++, warts and all.
For example, if you set up a menu system with four alternatives like that in
Figure 3.13, you could use code that looks like this:
```java
Scanner in = new Scanner(System.in);
System.out.print("Select an option (1, 2, 3, 4) ");
int choice = in.nextInt();
switch (choice)
{
 case 1:
 . . .
 break;
 case 2:
 . . .
 break;
 case 3:
 . . .
 break;
 case 4:
 . . .
 break;
 default:
 // bad input
 . . .
 break;
}
```
### Multidimensional arrays
You can do the
initialization as follows:
```java
balances = new double[NYEARS][NRATES];
```
In other cases, if you know the array elements, you can use a shorthand
notation for initializing a multidimensional array without a call to new. For
example:
```java
int[][] magicSquare =
 {
 {16, 3, 2, 13},
 {5, 10, 11, 8},
 {9, 6, 7, 12},
 {4, 15, 14, 1}
 };
 ```
Once the array is initialized, you can access individual elements by supplying
two pairs of brackets—for example, ```balances[i][j]```.
The example program stores a one-dimensional array interest of interest rates
and a two-dimensional array balances of account balances, one for each year
and interest rate. We initialize the first row of the array with the initial
balance:
```java
for (int j = 0; j < balances[0].length; j++)
 balances[0][j] = 10000;
```

Then we compute the other rows, as follows:
```java
for (int i = 1; i < balances.length; i++)
{
 for (int j = 0; j < balances[i].length; j++)
 {
 double oldBalance = balances[i - 1][j];
 double interest = . . .;
 balances[i][j] = oldBalance + interest;
 }
}
 ```
