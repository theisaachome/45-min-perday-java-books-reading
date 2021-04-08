## Using Arrays

### Declaring An Array

```java
 int [] key;
 int key [];
```

### Declaring an array of object references:

```java
Student [] Students;
```

- With an array reference, put the array brackets immediately after the declared type rather than after the identifier.

- It is never legal to include the size of the array in your declaration.

```java
 int [5] scores ; // will not compile.
```

### Constructing an Array

- creating the array object on the heap
- Java must know how much space to allocate on the heap, so you must specify the size of the array at creation time.
- The size of the array is the number of elements the array will hold.

```java
    // Declares the array of ints
    int [] testScores;
    // constructs an array and assigns it to the testScores variable.
    testScores = new int[4];

```

- new object on the heap—an array object
- holding four elements
- each element containing an int with a default value of 0.

### in One Statement

```java
   int[] testScores = new int[4];
```

### Arrays of object types can be constructed in the same way:

```java
   Student[] students = new Student[10];
```

### **The JVM needs the size to allocate the appropriate space on the heap for the new array object.**

---

### Constructing Multidimensional Arrays
