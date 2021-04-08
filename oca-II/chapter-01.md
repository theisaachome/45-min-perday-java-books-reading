## **Declarations, Access annd Enums**

[Table of Contents](#table-of-contents)

- [
  Define Classes and Interfaces](#define-classes-and-interfaces)
- The static keyword and init blocks
- Abstract classes
- The final keyword
- Enums 2.5 Interfaces

---

### **Define Classes and Interfaces**

- Class Declarations and Modifiers

  - The class declarations top-level classes
  - Not nested classes or inner classes.

- a bare-bones class declaration:

  ```java
  class MyClass{}
  ```

- Add modifiers before the class declaration.

- Modifiers fall into two categories:

  - Access modifiers (public, protected, private)

  - Nonaccess modifiers (including strictfp, final, and abstract)

- **three** access modifiers.

- **four** access controls (levels of access)

  - The fourth access control level (called default or package access)

  - is either of the three access modifiers.

  - In other words, every class, method, constructor, and instance variable have an access control.

  - Although all four access controls (three modifiers) work for most method and variable declarations.

  - A class can be declared with only public or default access;

---

### Class Access

- One class (class A) has access to another class (class B)

- it means class A can do one of three things:

  - Create an instance of class B.

  - Extend class B (in other words, become a subclass of class B).

  - Access certain methods and variables within class B, depending on the access control of those methods and variables.

- _access means visibility_

### Default Access

- **_No modifier_** preceding it in the declaration!

- Default access as package-level access,

- because a class with default access can be seen only by classes within the same package.

#### example

- Tea won’t compile because its superclass,
- Beverage, has default access and is in a different package.

  ```java
  package cert;
  class Beverage{}
  ```

  ```java
  package exam.stuff;
  import cert.Beverage;
  class Tea extends Beverage{}s
  ```

---

### Public Access

- A class declaration with the public keyword

- gives all classes from all packages access to the public class.

- to use a class from a different package

  - still need to import the public class or use the fully qualified name.

---

### Other (Nonaccess) Class Modifiers

- A class declaration using the keyword **_final_**, **_abstract_**, or **_strictfp_**

- These modifiers are in addition to whatever access control is on the class,

  - for example:

  - declare a class as both public and final.

  - But you can’t always mix nonaccess modifiers.

  - you must never mark a class as both final and abstract.

- strictfp is a keyword and can be used to modify a class or a method, but **_never a variable_**.
  - Marking a class as strictfp means that
  - any method code in the class will conform strictly
  - to the IEEE 754 standard rules for floating points.
