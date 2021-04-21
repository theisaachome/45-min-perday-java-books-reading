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
- [Declare Class Members](#declare-class-members)
  - [Access Modifiers](#access-modifiers)
  - [Public Members](#public-members)
  - [Private Members](#private-members)
  - [Protected and Default Members](#protected-and-default-members)
  - [Protected Details](#protected-details)
  - [Local Variables and Access Modifiers](#local-variables-and-access-modifiers)
- [Nonaccess Member Modifiers](#nonaccess-member-modifiers)
  - [Final Methods](#final-methods)
  - [Final Arguments](#final-arguments)
  - [Abstract Methods](#abstract-methods)
  - [Synchronized Methods](#synchronized-methods)
  - [Methods with Variable Argument Lists](#methods-with-variable-argument-lists)
- [Constructor Declaration](#constructor-declaration)
- [Variable Declarations](#variable-declarations)
  - [Declaring Primitives and Primitive Ranges](#declaring-primitives-and-primitive-ranges)
  - [Declaring Reference Variables](#declaring-reference-variables)
    - [Instance Variables](#instance-variables)
    - [Local Variables](#local-variables)
    - [Array Declarations](#array-declarations)
    - [Final Variables](#final-variables)
- [Declare and Use enums](#declare-and-use-enums)

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

---

### Declare Class Members

- What it means to modify a method or variable declaration.

- Methods and instance variables are collectively known as members.

- Can modify a member with both access and nonaccess modifiers

#### Access Modifiers

- method and variable members are usually given access control in exactly the same way.

- a class can use just two of the four access control levels:
  - (default or public)
- members can use all four:

  - public

  - protected

  - default

  - private

- Default protection is when you don’t type an access modifier in the member declaration.

- The default and protected access control types have almost identical behavior.

  - Note: As of Java 8 :

    - the word default can ALSO be used to declare certain methods in interfaces.
    - in an interface’s method declaration,
    - default has a different meaning .

- If class A has access to a member of class B, it means that class B’s member is visible to class A.

- Two different access issues:

  - Whether method code in one class can access a member of another class.

  - Whether a subclass can inherit a member of its superclass.

- when a method in one class tries to access a method or a variable of another class, using the dot operator (.) to invoke a method or retrieve a variable.

```java

```

- Members of a superclass, a subclass can access through inheritance.

- the subclass inherits a member of its superclass.

- If a subclass inherits a member, it’s exactly as if the subclass actually declared the member itself.

- If a subclass inherits a member, the subclass has the member.

```java

```

---

### Public Members

- When a method or variable member is declared public,
- it means all other classes, regardless of the package they belong to, can access the member.

- if a method invoked (or a variable accessed) without the dot operator (.):
  - it means the method or variable belongs to the class where you see that code.
  - It also means that the method or variable is implicitly being accessed using the this reference.

---

### Private Members

- Members marked private can’t be accessed by code in any class other than the class in which the private member was declared.

- A private member is invisible to any code outside the member’s own class.

- When a member is declared private, a subclass can’t inherit it.

---

### Protected and Default Members

- Both access control levels are almost identical,

- with one critical difference:

  - A default member may be accessed only if the class accessing the member belongs to the same package.

  - A protected member can be accessed (through inheritance) by a subclass even if the subclass is in a different package.

- Default and protected behavior differ only when we talk about subclasses.

- the protected member, any subclass of the class declaring the member can access it through inheritance.

- the default behavior,doesn’t allow a subclass to access a superclass member unless the subclass is in the same package as the superclass.

- The subclass can see the protected member only through inheritance.

### Protected Details

- For a subclass outside the package, the protected member can be accessed only through inheritance.

```java

```

### Default Details

- default members are visible to subclasses only if those subclasses are in the same package as the superclass.

### Local Variables and Access Modifiers

- Can access modifiers be applied to local variables?
- **NO!**

- there is only one modifier that can ever be applied to local variables—final.

---

### Nonaccess Member Modifiers

- final

- abstract

- static

- transient and synchronized.

### Final Methods

- The final keyword prevents a method from being overridden in a subclass.

- It is often used to enforce the API functionality of a method.

### Final Arguments

- Method arguments are the variable declarations that appear in between the parentheses in a method declaration.

- A typical method declaration with multiple arguments looks like this:

```java
 public Record
 getRecord(int fileNumber, final int recNumber){}
```

- recNumber is declared as final, which, of course, means it can’t be modified within the method.

### Abstract Methods

- a method that’s been declared (as abstract) but not implemented.

- it has no method body.

- You mark a method abstract when you want to force subclasses to provide the implementation.

  ```java

    public abstract void showSample();
  ```

- It is illegal to have even a single abstract method in a class that is not explicitly declared abstract!

- The first concrete subclass of an abstract class must implement all abstract methods of the superclass.

- abstract class extending another abstract class, the abstract subclass doesn’t need to provide implementations for the inherited abstract methods.

---

### Synchronized Methods

- The synchronized keyword indicates that a method can be accessed by only one thread at a time.

```java
public synchronized Record retrieveUserInfo(int id) { }
```

- The synchronized modifier can be matched with any of the four access control levels

---

### Methods with Variable Argument Lists

- **_arguments_** The things you specify between the parentheses when you’re invoking a method:

  ```java
    public Record retrieveUserInfo(int id){}
  ```

- **_parameters_** The things in the method’s signature that indicate what
  the method must receive when it’s invoked:

  ```java
  doStuff("a",2);
  ```

- the declaration rules for var-args:

- **Var-arg type** : the parameter of your method can receive. (primitive type or an object type.)

- **Basic syntax** : To declare a method using a var-arg parameter, (...)

- **Other parameters** : It’s legal to have other parameters in a method that uses a var-arg.

- **Var-arg limits** : The var-arg must be the last parameter in the method’s signature, and you can have only one var-arg in a method.

```java
 void doStuff(int... x){}
 void doStuff2(char c, int... x){}
 void doStuff3(Animal... animal){}
```

---

### Constructor Declaration

- A constructor can’t have a return type.

- Constructor declarations can,have all of the normal access modifiers
- they can take arguments (including var-args).

- BIG RULE they must have the same name as the class in which they are declared.

- Constructors can’t be marked static.

- they can’t be marked final or abstract (because they can’t be overridden)

---

### Variable Declarations

- **Primitives**

  - A primitive can be one of eight types: char, boolean, byte, short, int, long, double, or float.

- **Reference**

  - variables A reference variable is used to refer to (or access) an object.

  - can be used to refer to any object of the declared type or of a subtype of the declared type.

### Declaring Primitives and Primitive Ranges

- Can be declared

  - as class variables (statics),

  - instance variables,

  - method parameters, or local variables.

  - You can declare one or more primitives, of the same primitive type, in a single line.

---

### Declaring Reference Variables

- Can be declared as
  - static variables,
  - instance variables,
  - method parameters, or local variables.

### Instance Variables

- defined inside the class,
- but outside of any method, and
- are initialized only when the class is instantiated.
- Instance variables are the fields that belong to each unique object.

- know that instance variables
  - Can use any of the four access levels
  - Can be marked final
  - Can be marked transient

---

### Local Variables

- Declared within a method.

- Declared and initialized within the method.

- Starts its life inside the method.

- it’s also destroyed when the method has completed.

- Local variables are always on the stack, not the heap.

- must be initialized before you try to use it.

- local variables don’t get default values.

---

### Array Declarations

- store multiple variables of the same type or variables that are all subclasses of the same type.

- Arrays can hold either primitives or object references,

- but an array itself will always be an object on the heap,

- even if the array is declared to hold primitive elements.

---

### Final Variables

- the final keyword makes it impossible to reassign that variable once it has been initialized with an explicit value.

- A reference variable marked final can never be reassigned to refer to a different object.

- The data within the object can be modified,

- but the reference variable cannot be changed.

- there are no final objects, only final references.

---

### Transient Variables

- If you mark an instance variable as transient,

- you’re telling the JVM to skip
  (ignore)
- this variable when you attempt to serialize the object containing it.

---

### Declare and Use enums

-

```java
enum CoffeeSize{
  BIG,HUGE,OVERWHELMING
}
```

- enums can be declared as their own class or enclosed in another class.

```java
class Coffee {
	private CoffeeSize size;
	public CoffeeSize getSize() {
		return size;
	}
	public void setSize(CoffeeSize size) {
		this.size = size;
	}
}
public class MainApp {
	public static void main(String[] args) {
		var drink = new Coffee();
		drink.setSize(CoffeeSize.BIG);
	}
}
```

- Each of the enumerated CoffeeSize values is actually an instance of CoffeeSize.
- In other words, BIG is of type CoffeeSize.

---

### Declaring Constructors, Methods, and Variables in an enum

- an enum really is a special kind of class,

- more than just list the enumerated constant values.

- You can add constructors, instance variables, methods, and

- something really strange known as a constant specific class body.

- Example:

  - You want to know that
    - BIG is 8 ounces,
    - HUGE is 10 ounces, and
    - OVERWHELMING is a whopping 16 ounces.

```java
enum CoffeeSize{
	BIG(8),HUGE(10),OVERWHELMING(16);
	private CoffeeSize(int ounces) {
		this.ounces = ounces;
	}
	private int ounces;
	public int getOunces() {
		return ounces;
	}
}
```

```java
  Coffee drink1 = new Coffee();
  drink1.size = CoffeeSize.BIG;
  Coffee drink2 = new Coffee();
  drink2.size = CoffeeSize.HUGE;
  System.out.println(drink1.size.getOunces());

  for (CoffeeSize cs : CoffeeSize.values()) {
  System.out.println(cs + " " + cs.getOunces());
  }
```

- **_key points to remember about enum constructors_**

  - NEVER invoke an enum constructor directly.
  - The enum constructor is invoked automatically with the arguments you define after the constant value.

  - can define more than one argument to the constructorand
  - can overload the enum constructors,
  - like overloading a normal class constructor.

#### _example_

```java

enum CoffeeSize{
	BIG(8),
	HUGE(10),
	OVERWHELMING(16){
		public String getLidCode() {
			return "A";
		}
	};
	private CoffeeSize(int ounces) {
		this.ounces = ounces;
	}
	private int ounces;
	public int getOunces() {
		return ounces;
	}
	public String getLidCode() {
		return "B";
	}
}
```
