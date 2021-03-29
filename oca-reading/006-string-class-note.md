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
