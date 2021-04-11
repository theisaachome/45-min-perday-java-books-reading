## **Declarations, Access annd Enums**

[Table of Contents](#table-of-contents)

- [Define Classes and Interfaces](#define-classes-and-interfaces)
- [Class Access](#class-access)
- [Default Access](#default-access)
- [Public Access](#public-access)
- [Other Nonaccess Class Modifiers](#other-nonaccess-class-modifiers)
- [Final Classes](#final-classes)
- [Abstract Classes](#abstract-classes)
- [Use Interfaces](#use-interfaces)

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

---

### **_Final Classes_**

- In a class declaration, the final keyword means the class can’t be subclassed.

- No other class can ever extend a final class, and any attempts to do so will result in a compiler error.

- **_final_** gives you the security that nobody can change the implementation out from under you.

- You’ll notice many classes in the Java core libraries are final.

```java
package cert;
public final class Beverage{
  public importantMethod(){}
}

package exame.stuff;
import cert.Beverage;
class Tea extends Beverage{}

// can't subclass final classes
```

---

### **_Abstract Classes_**

- An abstract class can never be instantiated.
- The class might be just too, well, abstract.
- imagine you have a class Car that has generic methods common to all vehicles.
- But you don’t want anyone actually creating a generic abstract Car object.

- to instantiate actual car types such as BMWBoxster and SubaruOutback.

_example_

```java
abstract class Car{
  private double price;
  private String model;
  private String year;
  private abstract void goFast();
  private abstract void goUpHill();
  private abstract void impressNeighbbors();
}
```

- if even a single method is abstract, the whole class must be declared abstract.
- One abstract method spoils the whole bunch.
- there can be nonabstract methods in an abstract class.

final NOTE:

- You can’t mark a class as both **_abstract and final_**.

- They have nearly **_opposite meanings_**.

- An _abstract class must be subclassed_, whereas _a final class must not be subclassed_.

---

### **Use Interfaces**

#### Declaring an Interface

- An interface is a contract.

- Any concrete class type that implements this interface must agree to write the code for methods in the interface.

- Interfaces can be implemented by any class and from any inheritance tree.

### The relationship between interfaces and classes

- Think of an interface as a 100-percent abstract class.

- Like an abstract class, an interface defines abstract methods.

- Although an abstract class can define both abstract and nonabstract methods.

- An interface generally has only abstract methods

**_These rules are strict:_**

- All interface methods are implicitly public.

- All variables defined in an interface must be public, static, and final—in other words,

  - interfaces can declare only constants, not instance variables.

- Interface methods cannot be marked final, strictfp, or native.

- An interface can extend one or more other interfaces.

- An interface cannot extend anything but another interface.

- An interface cannot implement another interface or class.

- An interface must be declared with the keyword interface.

- interfaces are implicitly abstract.

```java
 public interface Bounceable{
   void bounce();
   void setBouncefactor(int bf);
 }
```

- the following interface methods are legal and identical:

```java
 void bounce();
 public void bounce();
 abstract void bounce();
 public abstract void bounce();
 abstract public void bounce();
```

- all interface methods are implicitly public and abstract.

- The following interface method declarations won’t compile:

---

### Declaring Interface Constants

- Constants in an interfacec.

- any class implementing the interface will have access to the same constant.

- one key rule for interface constants.

  ```java
  public static final
  ```

- Just as interface methods are always public and abstract.

- any variable defined in an interface **_must be_** and **_implicitly_** is a public constant.

```java
 interface foo{
   int BAR = 42;
   void go ();
 }

 class Zap implements Food{
   public void go(){
     // theBAR = 27assignmentwill not compile.
     BAR = 27;
     // access it and use it,but as a read-only value.
     System.out.print(BAR);
   }
 }
```

- the implementing class can access it and use it,but as a read-only value.

---

### Declaring default Interface Methods

- simple declaration rules:

- **_default methods are :_**

  - declared by using the default keyword.

  - The keyword can be used only with interface method signatures.

  - public by definition,and the public modifier is optional.

  - cannot be marked as private, protected, static, final, or abstract.

  - default methods must have a concrete method body.

```java
interface TestDefault{
  // legal
  default int m1(){return 1;}
  // legal
  public  default void m1(){}

  // illegal: default can not be marked static
  static default void m3(){}
  // illegal: default must have a method body
  default void m4();
}
```

---

### Declaring static Interface Methods

- using static interface methods:

- static interface methods are :

  - declared by using the static keyword.

  - public, by default, and the public
    modifier is optional.
  - cannot be marked as private, protected,
    final, or abstract.
  - must have a concrete method body.

  - When invoking a static interface method, the method’s type (interface name) MUST be included in the invocation.

- Here are some examples of legal and illegal static interface methods and their use:
