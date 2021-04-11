## Using String and StirngBuilder

### The String Class

### Strings are Immuable Objects

- In Java, each character in a string is a 16-bit Unicode character. Because Unicode characters are 16 bits
- Once you have assigned a String a value, that value can never change
  - Although the String object is immutable, its reference variable is not,

```java
 String s  = new String();
 s= "abcdef";

 // refer s2 to the same String as  s.
 String s2 = s;

// appends a literal to the end.
 s = s.concat(" more stuff");

```

- Now two String objects :
  - First : "abcdef", and
  - Second : "abcdef more stuff"
- Note:
  - Technically Three String Objects.
  - contact() : " more stuff".
  - referenced by s2 : "abcdef".
  - referenced by s "abcdef more stuff".

## Another Example

- A new String object, give it the value “Java”, and refer x to it.
- JVM creates a second String object with thevalue“Java Rules!”but nothing refers to it.

- Variable x still refers to the original String with the value “Java”

```java
 String x  = "Java ";

 x.concat(" Is Fun to Code");

 System.out.print("x = " + x);
 // Output is " x = Java"

```

---

## Important Facts About Strings and Memory

- The String class is marked final.
- Nobody can override the behaviors of any of the String methods.
- So you can rest assured that the String objects you are counting on to be immutable will, in fact, be immutable.

### Creating New Strings

- "abc" will go in the pool, and s will refer to it:

- Creates one String object and one reference variable.

```java
String s =  "abc";
```

- Because of the new keyword,
- Java will create a new String object in normal (nonpool) memory,
- and s will refer to it.
- In addition, the literal "abc" will be placed in the pool:

```java
String s =  "abc";
```

---

## Important Methods in the String Class

- **public char charAt(int index)**

- returns the character located at the String’s specified index.

```java

  String x = "airplane";

  System.out.print(x.charAt(2));
// output is 'r'

```

- **public String concat(String s)**
  - returns a string with the value of the String passed in to the method appended to the end of the String used to invoke the method

```java

  String x = "taxi";

  System.out.print(x.concat("cab"));
// output is ' taxi cab'

```

- **public String replace(char old, char new)**
  - returns a String whose value is that of the String used to invoke the method, but updated so that any occurrence of the char in the first argument is replaced by the char in the second argument

```java

  String x = "oxoxoxox";

  System.out.print(x.replace("x","X"));
// output is ' oXoXoXoX'

```

- **public String substring(int begin)**
- **public String substring(int begin, int end)**

## The StringBuilderClass

- should be used when you have to make a lot of modifications to strings of characters.

**Note:**
_A common use for StringBuilders is file I/O when large, ever-changing streams of input are being handled by the program. In these cases, large blocks of characters are handled as units, and StringBuilder objects are the ideal way to handle a block of data, pass it on, and then reuse the same memory to handle the next block of data._

### Using StringBuilder

```java

	StringBuilder sb = new StringBuilder("abc");

	sb.append("def");

	System.out.println(sb);

```

- these method calls can be chained to each other

#### Example

```java

StringBuilder sb = new StringBuilder("abc");

sb.append("def").reverse().insert(4, "----");

System.out.println(sb);

```

- there are three ways to create a new StringBuilder:

  The two most common ways to work with

  ```java
  // defaul capacity= 16 characters
  StringBuilder sb0 = new StringBuilder();

  // defaul capacity= 16 + arg length
  StringBuilder sb = new StringBuilder("abc");

  // capacity = x (size)
  StringBuilder x = new StringBuilder(20);
  x.append("Hello World");
  ```

### **Three rules to keep in mind when appending and inserting:**

- append() grows a StringBuilder past its capacity, the capacity is updated automatically.

- insert() starts within a StringBuilder’s capacity but ends after the current capacity, the capacity is updated automatically.

- insert() attempts to start at an index after the StringBuilder’s current length, an exception will be thrown.

---

## Important Methods in the StringBuilder Class

- **_public StringBuilder append(String s)_**

```java

StringBuilder gameName = new StringBuilder("PUBG");

gameName.append("MOBILE");

System.out.println(gameName);

```

- **_public StringBuilder delete(int start, int end)_**
  - the first argument (which is zero-based),
  - the second argument (but it is one-based)!

```java

StringBuilder number = new StringBuilder("0123456789");

System.out.println(number.delete(4, 6));

// 01236789

```

- **_public StringBuilder insert(int offset, String s)_**
  - the first argument (which is zero-based)

```java

StringBuilder number = new StringBuilde("0123456789");

number.append("def").insert(4, "----");

System.out.println(number);

```

- **_public StringBuilder reverse()_**
  - the first character becoming the last, the second becoming the second to the last,

```java

StringBuilder reverse= new StringBuilder("abcdef");
reverse.reverse();

```
