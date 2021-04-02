## Working With Calendar Data

### **java.time.LocalDateTime**

- To create immutable objects, each of which represents a specific date and time.
- contain BOTH information about
  - days, months, and years,
  - hours, minutes, seconds, and fractions of seconds.

### **java.time.LocalDate**

- create immutable objects, each of which represents a specific date.
- LocalDate objects are accurate only to days.

### **java.time.LocalTime**

- to create immutable objects, each of which represents a specific time.
- LocalTime objects refer
  - only hours, minutes, seconds, and fractions of seconds.

### **java.time.format.DateTimeFormatter**

- to format date/time objects for output and to parse input strings and convert them to date/time objects.

### **java.time.Period**

- create immutable objects that represent a period of time.

---

### **Immutability**

- Just like Strings! **Bro!**.
- most of the calendar-related objects you’ll create are immutable.
- To "manipulate" a calendar object,
  - invoke a method on a calendar object, and get return a new calendar object that represents the result of manipulating the value of the original calendar object.
  - But the original calendar object’s value is not,
  - and cannot, be changed.

```java
    LocalDate date1 = LocalDate.of(2021, 4, 2);
	Period oneMonth = Period.ofMonths(1);
	System.out.println(date1);
	// add one month
	date1.plus(oneMonth); // added new value is lost
	System.out.println(date1);
	LocalDate date2 = date1.plus(oneMonth);
	System.out.println(date2);
```

---

### **Factory Classes**

- No public constructors and provides at least one public static method that can create new instances of the class.
- any method that is invoked to get a new instance of the class is called a factory method.
