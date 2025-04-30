# Spring Boot Fundamentals Training - ITM Gwalior

## **Duration**: 4 hours per day x 6 days (24 hours total)

### Day 1 : Introduction & Java Refresher

#### Session 1 (2 hours) : Welcome, environment setup, OOP concepts review

* **Welcome & Overview** (30 minutes)
  * Training objectives and schedule  

    > By the end of this training program, _YOU_ will be able to:
    > * Understand core Spring Boot concepts and its advantages over traditional Spring framework.
    > * Design and implement RESTful APIs following industry best practices.
    > * Work with data persistence using Spring Data JPA and Hibernate.
    > * Implement proper exception handling and API documentation.
    > * Apply the MVC architectural pattern in Spring Boot applications.
    > * Develop and test a complete Spring Boot application from scratch.

  * Pre-requisite knowledge assessment
  * Setting up the development environment (JDK, IntelliJ IDEA, Git)


* **Java Refresher: OOP Concepts** (90 minutes)
  * [Classes and Objects review](./README.md#classes-and-objects-review)
  * [Inheritance and polymorphism in practice](./README.md#inheritance-and-polymorphism-in-practice)
  * [Interfaces and abstract classes](./README.md#interfaces-and-abstract-classes)
  * [Annotations in Java (built-in annotations and their purpose)](./README.md#annotations-in-java-built-in-annotations-and-their-purpose)

#### Session 2 (2 hours) : Modern Java features, Introduction to Spring Framework

* **Java Refresher: Modern Java Features** (60 minutes)
    * [Lambda expressions and Functional Interfaces](./README.md#lambda-expression-and-functional-interfaces)
    * [Stream API basics](./README.md#stream-api-basics)
    * [Optional class for null handling](./README.md#optional-class-for-null-handling)
    * [Method references](./README.md#method-reference)


* **Introduction to Spring Framework** (60 minutes)
    * [Spring Core concepts](./README.md#spring-core-concepts)
    * [Dependency Injection and Inversion of Control](./README.md#dependency-injection-di-and-inversion-of-control-ioc)
    * [Spring vs Spring Boot](./README.md#spring-vs-spring-boot)
    * [Spring Boot advantages and features](./README.md#spring-boot-advantages-and-features)


---

**Official Learning Links**

- [Link to learn more about Java versions (Java Almanac)](https://javaalmanac.io/)
- [Objects, Classes, Interfaces, Packages, and Inheritance (dev.java)](https://dev.java/learn/oop/)  
- [Classes & Objects (dev.java)](https://dev.java/learn/classes-objects/)

### Classes and Objects review

**What is a class?**

A class describes an object in terms of its
  - data (variables/fields)
  - operations (functions/methods)

Any concept you wish to implement in a Java program must be _encapsulated_ within a class!

A student class example

```java
public class Student {
	int rollNumber;
	String name;
	double marks;
	
	// ...
}
```
In this `Student` class there are 3 fields (data points)
- roll number of the student called `rollNumber`, which is of the `int` (integer) type.
- name of the student called `name`, which is of the `String` type.
- marks of the student called `marks`, which is of the `double` type.

This means, we are telling out Java program about a new object type - `Student`, and
we are saying every student should have a 
- roll number,
- name,
- and marks.

---

**POJO: Plain-Old Java Object**

A complete POJO implementation of the same Student class would look like this

```java
import java.util.Objects;

public class Student {
	private final int rollNumber;
	private final String name;
	private double marks;

	public Student() {
		this.rollNumber = 0;
		this.name = "";
	}

	public Student(int rollNumber, String name, double marks) {
		this.rollNumber = rollNumber;
		this.name = name;
		this.marks = marks;
	}

	public int getRollNumber() {
		return rollNumber;
	}

	public String getName() {
		return name;
	}

	public double getMarks() {
		return marks;
	}

	public void setMarks(double marks) {
		this.marks = marks;
	}

	@Override
	public boolean equals(Object o) {
		if (o == null || getClass() != o.getClass()) return false;

		Student student = (Student) o;
		return rollNumber == student.rollNumber 
				&& Double.compare(marks, student.marks) == 0 
				&& Objects.equals(name, student.name);
	}

	@Override
	public int hashCode() {
		int result = rollNumber;
		result = 31 * result + Objects.hashCode(name);
		result = 31 * result + Double.hashCode(marks);
		return result;
	}

	@Override
	public String toString() {
		return "Student{" +
				"rollNumber=" + rollNumber +
				", name='" + name + '\'' +
				", marks=" + marks +
				'}';
	}
}
```

Don't be afraid of the code. This is simply the same class we have seen earlier with some extra instructions
for the Java program. This complete "POJO" (Plain-Old Java Object) implementation can be created for any class!
The general requirements to create a POJO class are
1. The class should be public.
2. The fields should be private.
3. There should be a no-args constructor in the class.
4. There should be public getter and setter methods.
5. **There should be NO business logic in the class.**
6. **Optional:** Parameterized Constructor.
7. **Optional:** Override the `toString()` method.
8. **Optional:** Override the `equals()` and the `hashCode()` methods.

---

**What is an object?**

An _object_ in Java is a real-world entity, created from a class, that exists in memory when the Java program is running!

For example, before creating an actual house, an architect designs the house on a blueprint. IN this scenario, the blueprint
is the _class_ and the actual house is the _object_.

Code Example - 

```java
public class Main {
    public static void main(String[] args) {
        Student chatur = new Student();
    }
}
```

In this example, we have created a new `Student` object, and we are referring to the object with the name `chatur`.

After the creation of the object is completed successfully, you can read and write the values of the data fields of the object
i.e. `rollNumber`, `name`, and `marks` as defined in the `Student` class. 

Also, you can _make_ the `chatur` object do something by calling the `Student` methods defined in the class.

```java
public class Main {
    public static void main(String[] args) {
        Student chatur = new Student();
		chatur.rollNumber = 4;
		chatur.name = "Chatur";
		chatur.marks = 95;
    }
}
```

---

**Official Learning Links**

- [Inheritance (dev.java)](https://dev.java/learn/inheritance/)

### Inheritance and polymorphism in practice

**Inheritance**

Inheritance in Java, is a _technique_ by which a class (parent class/superclass) can share its data (fields/variables) and
operations (methods) with another class (child class/subclass).

Let us take the `Student` example from before.

We want to create a new class called `Topper` which is a type of `Student`.
Now this means, the `Topper` class should also define all the fields and methods created in the `Student` class.

Instead of writing all the same code again, we can share the fields and methods of the Student class with the Topper class.
**Important**: You may be tempted to create every class using inheritance from now on, don't do that!

Inheritance not just about code-reusing, it is about making a parent and child relationship in Java code where an actual 
such relationship exists in the real-world, i.e. if a real-world Topper entity and a Student entity are not related in the 
real-world, we as developers should not add inheritance just because we can.

code:

```java
public class Topper extends Student {
    private int numberOfHoursStudied;

    public Topper() {
    }

    public Topper(int rollNumber, String name, double marks, int numberOfHoursStudied) {
        super(rollNumber, name, marks);
        this.numberOfHoursStudied = numberOfHoursStudied;
    }

    public int getNumberOfHoursStudied() {
        return numberOfHoursStudied;
    }

    public void setNumberOfHoursStudied(int numberOfHoursStudied) {
        this.numberOfHoursStudied = numberOfHoursStudied;
    }

    @Override
    public boolean equals(Object o) {
        if (o == null || getClass() != o.getClass()) return false;
        if (!super.equals(o)) return false;

        Topper topper = (Topper) o;
        return numberOfHoursStudied == topper.numberOfHoursStudied;
    }

    @Override
    public int hashCode() {
        int result = super.hashCode();
        result = 31 * result + numberOfHoursStudied;
        return result;
    }

    @Override
    public String toString() {
        return "Topper{" +
                "numberOfHoursStudied=" + numberOfHoursStudied +
                '}';
    }
}
```

We followed the POJO principles again to create the Topper class.

Note that, just by writing the `extends <ClassName>` syntax in the Topper class, the Topper class
can now actually 4 fields
- int rollNumber (inherited from Student)
- String name (inherited from Student)
- double marks (inherited from Student)
- int numberOfHoursStudied (created in Topper class)

This is also true for all the methods created in the Student class.

---

**Types of Relationships**

* IS-A (inheritance)  
    The `IS-A` relationship represents a real-world inheritance scenario where one class is a type
    of another class.  
    Ex - Topper IS-A Student  
    Syntax - <ChildClass> IS-A <ParentClass>, if this sentence makes sense, then it is okay to add the `extends` keyword.  

    ```java
    public class Topper extends Student {}
    ```

* HAS-A (aggregation)
    The `HAS-A` relationship represents _aggregation_ where one class contains another class as a field.
    It is derived from the English word `aggregate`.

    > aggregate  
  noun | ˈaɡrɪɡət |  
  a whole formed by combining several separate elements
    
    ```java
    public class Car {
        private Engine engine;
        private SoundSystem soundSystem;
        private NavigationSystem navigationSystem;
    }
    ```

    In this example, we can say that the `Car` object is an _aggregate_ of
    the `Engine` object + `SoundSystem` object + `NavigationSystem`.


* USES-A (association/dependence)

    The `USES-A` relationship represents _association_ or _dependence_ as a temporary
    relationship where a class uses another class (often as a paremeter).

    ```java
    class College {
        public void turnIntoEngineer(Student student) {}
    }
    ```

    In this example, we can say that the `College` class uses a `Student` object.

---

**Polymorphism**

Polymorphism in Java, is a _technique_ by which a method can behave differently based on the number and type of input _OR_
the type of object that is calling the method, namely `method overloading` and `method overriding`.

Polymorphism in Java can be observed in two ways:

- Method Overloading (Compile-time Polymorphism)
- Method Overriding (Runtime Polymorphism)

Let us take the `Student` class example again.

```java
public class Student {
    private int rollNumber;
    private String name;
    private double marks;

    public void updateMarks(double newMarks) {
        this.marks = newMarks;
    }

    public void updateMarks(double additionalMarks, boolean isBonus) {
        if (isBonus) this.marks += additionalMarks;
        else this.marks = additionalMarks;
    }
}

```
Here you can see that the `updateMarks` method is created twice. The first declaration has only one parameter called `newMarks`,
but the second one has two parameters `additionalMarks` and `isBonus`. This is how the `updateMarks` method behaves
differently on the basis of number and type of input.

```java
public class Topper extends Student {
    @Override
    public void updateMarks(double newMarks) {
        // Ensure topper's marks are always at least 90
        if (newMarks < 90) {
            super.updateMarks(90.0);
        } else {
            super.updateMarks(newMarks);
        }
    }

    @Override
    public void updateMarks(double additionalMarks, boolean isBonus) {
        if (isBonus) {
            // For bonus, add points but ensure minimum of 90
            super.updateMarks(additionalMarks, true);
        } else {
            // For regular updates, ensure minimum of 90
            if (additionalMarks < 90) {
                super.updateMarks(90.0);
            } else {
                super.updateMarks(additionalMarks);
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Student chatur = new Student();
		chatur.updateMarks(99);
		
		Topper rancho = new Topper();
		rancho.updateMarks(99);
    }
}
```

Here you can see, since the `Topper` class is inheriting the `updateMarks()` method from the `Student` class, the 
method will work as defined in the `Student` class, but the `Topper` class wants the `updateMarks()` method to behave differently
if the `Topper` object is calling the method. Hence, we have **overridden** the method.

Both the `chatur.updateMarks()` and the `rancho.updateMarks()` methods will work differently, but they are connected together 
via inheritance. So, in a way you can also say that inheritance is needed for overriding a method.

---

### Interfaces and abstract classes

**Abstract Class**

An abstract class is like a blueprint that's not quite complete. It's a class that can't be used to create objects 
directly but is meant to be extended by other classes. Abstract classes can have both regular methods with 
implementations and abstract methods (methods without bodies) that child classes must implement.

```java
public abstract class Person {
    protected String name;
    protected int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // Regular method with implementation
    public String getName() {
        return name;
    }
    
    // Abstract method - must be implemented by subclasses
    public abstract String getRole();
    
    // Regular method with implementation
    public String getDetails() {
        return name + " (" + age + " years) - " + getRole();
    }
}
```

---

**Official Learning Links**

- [Interfaces (dev.java)](https://dev.java/learn/interfaces/)

**Interface**

An interface is a contract that specifies what a class can do, without saying how it does it. It is a program unit, like a class, but it can only have abstract methods* and final fields.

Since Java 8, interfaces can also include default and static methods with implementations. Interfaces allow different 
classes to be treated interchangeably if they implement the same interface, which is great for flexibility in your code.

```java
// Interface with a single abstract method
interface Coder {
    String code(String language);
}

// Topper class implementing both Student class and Coder interface
public class Topper extends Student implements Coder {
    private String achievement;
    
    public Topper(String name, int age, int rollNumber, double marks, String achievement) {
        super(name, age, rollNumber, marks);
        this.achievement = achievement;
    }
    
    // Override method from parent class
    @Override
    public void updateMarks(double newMarks) {
        // Ensure topper's marks are always at least 90
        if (newMarks < 90) {
            super.updateMarks(90.0);
        } else {
            super.updateMarks(newMarks);
        }
    }
    
    // Implementation of the code method from Coder interface
    @Override
    public String code(String language) {
        return name + " is coding in " + language + " with excellence!";
    }
    
    // Additional method specific to Topper
    public String getAchievement() {
        return achievement;
    }
}
```

---

**Official Learning Link**

- [Annotations (dev.java)](https://dev.java/learn/annotations/)

### Annotations in Java (built-in annotations and their purpose)

  An annotation in Java is a special syntax that conveys information about the code; aka metadata.
  They are special tags or markers that you add to your code to provide extra information. They start with an @ symbol (like @Override) and can be attached to classes, methods, fields, and other program elements. Annotations don't directly affect your code's execution but they give instructions to the compiler, development tools, or frameworks about how to process your code.

  **@Override** is a common example of a Java annotation you use frequently.
  There are other annotations in Java and in other Java supported frameworks as we will learn 
  throughout this course, it is also possible to create your own annotation completely from scratch.

---

**Official Learning Link**

- [Lambdas (dev.java)](https://dev.java/learn/lambdas/)

### Lambda expression and Functional Interfaces

**Functional Interfaces**

A Functional Interface is a special type of interface that can have **ONLY ONE**
abstract method, hence they are also called **SINGLE ABSTRACT METHOD Types**.

```java
@FunctionalInterface
public interface Coder {
    String code(String language);
}
```
This is the same `Coder` interface example from before, since the interface only has on abstract method, it qualifies as
a `Functional Interface`. 

Notice the `@FunctionalInterface` annotation, it indicates that an interface type declaration is intended to be a 
functional interface as defined by Java i.e. it can only have at most one abstract method.

The interface is still allowed to have any number of non-abstract methods inside it.

```java
@FunctionalInterface
public interface Coder {
    String code(String language);
	
    default void study(int numberOfHours) {
        System.out.println("Studying...");
    }
}
```

Notice that although the `Coder` interface now has two methods, only one is abstract, as allowed. Hence, it still qualifies
as a `Functional Interface` to the Java compiler.

In Java, there is a package called `java.util.function`, which you can also observe in IntelliJ IDEA in the "Project View".
This package contains 43 functional interfaces built-in and ready to go. You don't need to remember all of this,
just the basic ones will do for now
- Function: Represents a function that accepts one argument and produces a result.
- Consumer: Represents an operation that accepts a single input argument and returns no result.
- Supplier: Represents a supplier of results.
- Predicate: Represents a predicate (boolean-valued function) of one argument.

All the other in-built functional interfaces are built on top of these.

You can see a summary of all the in-built functional interfaces in Java [here](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/function/package-summary.html)

---

**Lambda Expressions**

A Lambda Expression is a new syntactical way (since Java 8) for us developers to provide the concrete implementation for 
an abstract method of a functional interface anonymously.

```java

@FunctionalInterface
public interface Coder {
    String code(String language);
}

public class Main {
    public static void main(String[] args) {
        Coder chatur = language -> "I can code in " + language + "!";
        chatur.code("Java");
    }
}
```

Note that earlier, just to provide the concrete implementation of the `code()` method, we had to implement the `Coder` 
interface in the `Student` class. But now, since the lambda provides us with a way of creating this anonymous class we can
use the same functionality with concise syntax.

The general syntax for a lambda expression in Java is as follows

```
(parameters) -> { body }
```

The `->` here is a new operator added in Java 8 called the **arrow operator**.

---

**Official Learning Link**

- [The Stream API (dev.java)](https://dev.java/learn/api/streams/)

### Stream API basics

The Stream API is a powerful, but simple to understand set of tool for processing a sequence of elements.

It introduces the `map-filter-reduce` operations on collections such as arrays, lists, sets, etc.

```java
import java.util.*;
import java.util.stream.*;

class Student {
    private int rollNumber;
    private String name;
    private double marks;
    private String department;
    
    public Student(int rollNumber, String name, double marks, String department) {
        this.rollNumber = rollNumber;
        this.name = name;
        this.marks = marks;
        this.department = department;
    }
    
    public int getRollNumber() { return rollNumber; }
    public String getName() { return name; }
    public double getMarks() { return marks; }
    public String getDepartment() { return department; }
    
    @Override
    public String toString() {
        return "Student{" +
               "rollNumber=" + rollNumber +
               ", name='" + name + '\'' +
               ", marks=" + marks +
               ", department='" + department + '\'' +
               '}';
    }
}

public class StreamAPIDemo {
    
    public static void main(String[] args) {
        List<Student> students = List.of(
            new Student(101, "Alice", 92.5, "Computer Science"),
            new Student(102, "Bob", 78.0, "Mathematics"),
            new Student(103, "Charlie", 86.7, "Computer Science"),
            new Student(104, "David", 65.5, "Physics"),
            new Student(105, "Emma", 95.0, "Mathematics"),
            new Student(106, "Frank", 72.8, "Physics"),
            new Student(107, "Grace", 88.3, "Computer Science")
        );
        
        System.out.println("===== Stream API Demonstrations =====");
        
        // Filter operation
        filterStudents(students);
        
        // Map operations
        transformStudentData(students);
        
        // Sort operations
        sortStudents(students);
        
        // Aggregation operations
        aggregateStudentData(students);
        
        // Grouping operations
        groupStudents(students);
        
        // Additional operations
        additionalOperations(students);
    }
    
    // Filter demonstration
    public static void filterStudents(List<Student> students) {
        System.out.println("\n----- Filter Operations -----");
        
        // Filter students with marks above 85
        List<Student> highScorers = students.stream()
            .filter(student -> student.getMarks() > 85)
            .collect(Collectors.toList());
        
        System.out.println("Students with marks above 85:");
        highScorers.forEach(student -> System.out.println(student.getName() + ": " + student.getMarks()));
        
        // Filter CS students
        long csStudentCount = students.stream()
            .filter(student -> student.getDepartment().equals("Computer Science"))
            .count();
        
        System.out.println("Number of Computer Science students: " + csStudentCount);
    }
    
    // Map demonstration
    public static void transformStudentData(List<Student> students) {
        System.out.println("\n----- Map Operations -----");
        
        // Get all student names
        List<String> studentNames = students.stream()
            .map(Student::getName)
            .collect(Collectors.toList());
        
        System.out.println("Student names: " + studentNames);
        
        // Transform student marks (add 5 bonus points)
        List<Double> adjustedMarks = students.stream()
            .map(student -> student.getMarks() + 5.0)
            .collect(Collectors.toList());
        
        System.out.println("Marks after 5 point bonus: " + adjustedMarks);
        
        // Create custom formatted strings
        List<String> formattedStudents = students.stream()
            .map(student -> student.getName() + " (" + student.getDepartment() + "): " + student.getMarks())
            .collect(Collectors.toList());
        
        System.out.println("Formatted student info:");
        formattedStudents.forEach(System.out::println);
    }
    
    // Sort demonstration
    public static void sortStudents(List<Student> students) {
        System.out.println("\n----- Sort Operations -----");
        
        // Sort by marks (ascending)
        List<Student> sortedByMarks = students.stream()
            .sorted(Comparator.comparing(Student::getMarks))
            .collect(Collectors.toList());
        
        System.out.println("Students sorted by marks (ascending):");
        sortedByMarks.forEach(s -> System.out.println(s.getName() + ": " + s.getMarks()));
        
        // Sort by name
        List<String> namesSortedAlphabetically = students.stream()
            .map(Student::getName)
            .sorted()
            .collect(Collectors.toList());
        
        System.out.println("Student names sorted alphabetically: " + namesSortedAlphabetically);
        
        // Sort by department and then by marks (descending)
        List<Student> sortedByDeptAndMarks = students.stream()
            .sorted(Comparator.comparing(Student::getDepartment)
                    .thenComparing(Student::getMarks, Comparator.reverseOrder()))
            .collect(Collectors.toList());
        
        System.out.println("Students sorted by department and then by marks (descending):");
        sortedByDeptAndMarks.forEach(s -> 
            System.out.println(s.getDepartment() + " - " + s.getName() + ": " + s.getMarks()));
    }
    
    // Aggregation demonstration
    public static void aggregateStudentData(List<Student> students) {
        System.out.println("\n----- Aggregation Operations -----");
        
        // Calculate average marks
        double averageMarks = students.stream()
            .mapToDouble(Student::getMarks)
            .average()
            .orElse(0.0);
        
        System.out.println("Average marks: " + averageMarks);
        
        // Find student with highest marks
        Student topStudent = students.stream()
            .max(Comparator.comparing(Student::getMarks))
            .orElse(null);
        
        System.out.println("Top student: " + 
            (topStudent != null ? topStudent.getName() + " with " + topStudent.getMarks() + " marks" : "None"));
        
        // Check if all students passed (marks > 60)
        boolean allPassed = students.stream()
            .allMatch(student -> student.getMarks() > 60);
        
        System.out.println("Did all students pass? " + allPassed);
        
        // Check if any student got perfect score
        boolean anyPerfectScore = students.stream()
            .anyMatch(student -> student.getMarks() == 100.0);
        
        System.out.println("Did any student get a perfect score? " + anyPerfectScore);
        
        // Calculate sum of all marks
        double totalMarks = students.stream()
            .mapToDouble(Student::getMarks)
            .sum();
        
        System.out.println("Sum of all marks: " + totalMarks);
    }
    
    // Grouping demonstration
    public static void groupStudents(List<Student> students) {
        System.out.println("\n----- Grouping Operations -----");
        
        // Group students by department
        Map<String, List<Student>> studentsByDepartment = students.stream()
            .collect(Collectors.groupingBy(Student::getDepartment));
        
        System.out.println("Students grouped by department:");
        studentsByDepartment.forEach((dept, stdList) -> {
            System.out.println(dept + ":");
            stdList.forEach(s -> System.out.println("  - " + s.getName() + ": " + s.getMarks()));
        });
        
        // Count students in each department
        Map<String, Long> studentCountByDepartment = students.stream()
            .collect(Collectors.groupingBy(Student::getDepartment, Collectors.counting()));
        
        System.out.println("Number of students in each department: " + studentCountByDepartment);
        
        // Average marks by department
        Map<String, Double> avgMarksByDepartment = students.stream()
            .collect(Collectors.groupingBy(
                Student::getDepartment, 
                Collectors.averagingDouble(Student::getMarks)));
        
        System.out.println("Average marks by department: " + avgMarksByDepartment);
    }
    
    // Additional operations
    public static void additionalOperations(List<Student> students) {
        System.out.println("\n----- Additional Stream Operations -----");
        
        // Get first 3 students
        List<Student> firstThree = students.stream()
            .limit(3)
            .collect(Collectors.toList());
        
        System.out.println("First 3 students:");
        firstThree.forEach(s -> System.out.println(s.getName()));
        
        // Skip first 2 students
        List<Student> afterSkipping = students.stream()
            .skip(2)
            .collect(Collectors.toList());
        
        System.out.println("After skipping first 2 students:");
        afterSkipping.forEach(s -> System.out.println(s.getName()));
        
        // Get distinct departments
        List<String> departments = students.stream()
            .map(Student::getDepartment)
            .distinct()
            .collect(Collectors.toList());
        
        System.out.println("Departments: " + departments);
        
        // Performance categories using partitioning
        Map<Boolean, List<Student>> performanceGroups = students.stream()
            .collect(Collectors.partitioningBy(s -> s.getMarks() >= 80));
        
        System.out.println("High performers (marks >= 80):");
        performanceGroups.get(true).forEach(s -> System.out.println(s.getName() + ": " + s.getMarks()));
        
        System.out.println("Regular performers (marks < 80):");
        performanceGroups.get(false).forEach(s -> System.out.println(s.getName() + ": " + s.getMarks()));
    }
}
```

The Stream API in Java lets you process collections of data in a clean, functional style.  
Streams are like assembly lines for data processing. You start with a collection (our student list), create a stream 
from it, then apply operations to transform, filter, or analyze the data. Finally, you collect the results back into a 
collection or a single value.

Points to understand:

- Streams don't modify the original collection
- Stream operations are either intermediate (return another stream) or terminal (produce a result)
- Most stream operations are lazy - they only process data when needed
- Once a stream is consumed by a terminal operation, it cannot be reused

Points to remember:

- Use filter when you need to select elements
- Use map when you need to transform elements
- Use collect when you need to gather results into a collection
- Use sorted for ordering elements
- Use aggregation methods (average, sum, max) for data analysis
- The Optional type is used with operations that might not produce a result
- You can chain multiple operations together for complex data processing

---

### Method reference

A method reference is a shorthand way to refer to a method without actually calling it.

It is a simpler alternative to lambda expressions when all you want to do is call an existing method.

A method reference in Java is depicted using the `::` (double-color syntax)

The `::` operator creates a reference to a method or constructor, essentially treating the method as a function object.

It is not actually an operator in the traditional sense - it is a special syntax specifically for method references.

```java
import java.util.ArrayList;
import java.util.List;

@FunctionalInterface
interface Coder {
	String code(String language);
}

class Student {
	private int rollNumber;
	private String name;
	private double marks;

	public Student(int rollNumber, String name, double marks) {
		this.rollNumber = rollNumber;
		this.name = name;
		this.marks = marks;
	}
	// rest of the POJO implementation
}

class Topper extends Student implements Coder {
	public Topper(int rollNumber, String name, double marks) {
		super(rollNumber, name, marks);
	}

	void createApplication() {
		System.out.println("Creating application");
	}
	
	@Override
	public String code(String language) {
		return "I can code in " + language + "!";
	}
}

class Main {
	public static void main(String[] args) {
		List<Topper> toppers = new ArrayList<>();

		for (int index = 0; index < 10; index++) {
			toppers.add(new Topper(
					index + 1,
					"Topper " + index,
					Math.random() * 100
			));
		}

		toppers.forEach(Topper::createApplication);
	}
}
```

---

### Optional class for null handling

Optional helps eliminate null pointer exceptions by forcing you to explicitly handle cases where a value might be absent.

So, instead of writing something like

```java
class UserUtility {
    public User findUserByEmail(String email) {
		// implementation logic
    }
}
```

we should write

```java
class UserUtility {
    public Optional<User> findUserByEmail(String email) {
		// implementation logic
    }
}
```

Just a small chang like this forces us the developer to handle the case where the email will not match to 
any of the users, in such a case instead of simply saying `return null`, now the return type `Optional<User>` of the method
will not allow us to use the `null` as a return value. This will make you think what should actually be returned in such a case.

---

### Spring Core concepts

Spring Framework is a comprehensive Java application development framework that has become the industry standard for enterprise Java development. Here are its core concepts:

**Inversion of Control (IoC)**  
The fundamental concept where Spring takes control of object creation and lifecycle management instead of the developer doing it manually. Instead of creating objects directly with "new," you let Spring handle instantiation and dependencies.

**Dependency Injection (DI)**  
Spring's implementation of IoC where objects are given their dependencies rather than creating them internally. This promotes loose coupling and makes code more testable. Spring supports three types of dependency injection:
- Constructor injection (preferred)
- Setter injection
- Field injection (using @Autowired)

**Bean Management**  
A Spring bean is an object managed by the Spring IoC container. Beans are created, configured, and managed by Spring. You can define beans through:
- XML configuration
- Java configuration with @Bean
- Component scanning with @Component, @Service, @Repository, etc.

**Application Context**  
The central interface for providing configuration information to the application. It represents the Spring IoC container and is responsible for instantiating, configuring, and assembling beans.

**Aspect-Oriented Programming (AOP)**  
Allows separation of cross-cutting concerns (like logging, security, or transactions) from business logic. Spring AOP lets you define "aspects" that can be applied across multiple classes without modifying their code.

**Spring MVC**  
A web framework built on the Model-View-Controller pattern for building web applications. It provides features like request mapping, data binding, validation, and view resolution.

**Data Access**  
Spring provides consistent data access abstractions across different technologies:
- JDBC Template simplifies database operations
- Transaction management for data integrity
- ORM integration with Hibernate, JPA, etc.

**Spring Boot**  
While technically a separate project, Spring Boot has become a core part of the Spring ecosystem. It provides auto-configuration, standalone applications, and an embedded server to simplify Spring application development.

**Profiles**  
Allow you to define different configurations for different environments (development, testing, production) and activate them conditionally.

**Spring Security**  
Framework for authentication, authorization, and protection against common attacks.

These core concepts work together to create a flexible, modular architecture that's both powerful and maintainable. The Spring Framework significantly reduces boilerplate code and lets developers focus on business logic rather than infrastructure concerns.

---

## Practice Exercises

1. Create an `abstract` superclass named `Fruit`, and a concrete subclass named `Apple`. The superclass (`Fruit`) should 
belong to a package called `food` and the subclass (`Apple`) can belong to the default package. Make the superclass `public`
and give the subclass **default** access.
   - Create the superclass as follows
   ```java
        package food;
     
        public abstract class Fruit {
            // data 
            // operations
            // write the complete POJO implementation
        }
     ```
   - Create the subclass as follows
   ```java
        import food.Fruit;
        class Apple extends Fruit {
            // data
            // operations
            // write the complete POJO implementation
        }  
   ```
   - Create a `Main` class, and create the `main()` method inside it. Create objects of both the classes.  

2. You are given an interface as follows
   ```java
        public interface Vehicle {
            public int getYear();
            public String getModelName;
            public String getCompanyName;
        }    
   ```
   Write a class called `Ferrari` that implement the interface. Write the complete POJO implementation for the `Ferrari`
   class. Create a `Main` class, and create the `main()` method inside it. Create object of the `Ferrari` class inside it.

3. Create a class called `Bird` and define an instance method called `fly()` inside it. Define some instance fields for the `Bird`
class such as `name`, `height`, `weight` etc. Define a _static_ field for the `Bird` class called `birdCount`. 
Create a `Main` class, and create the `main()` method inside it. Create a static variable inside the `main()` method of the `Bird` type.
Initialize the variable with a valid `Bird` object and print the values of the instance and _static_ fields. Write some logic
in the `Bird` class to increment the `birdCount` variable every time a new `Bird` class object is created. Create an array of `Bird`s (`Bird[]`)
4. Try the Stream API practice questions given [here](https://github.com/dbc2201/StreamPracticeQuestions)
5. Write a program that counts duplicate characters from a given string.
    ```java
    /**
     * Counts duplicate characters in a given string and returns only those 
     * that appear more than the specified threshold.
     *
     * @param input the string to analyze for duplicate characters
     * @param threshold minimum number of occurrences to be considered duplicate
     * @return a Map with each duplicate character as key and its count as value
     * @throws NullPointerException if the input string is null
     * @throws IllegalArgumentException if threshold is less than 1
     */
    public Map<Character, Integer> countDuplicateCharacters(String input, int threshold) 
            throws NullPointerException, IllegalArgumentException {
        // TODO: Implement the duplicate counting logic
        return new HashMap<>(); // Placeholder return
    }
    ```
6. Write a program that reverses the letters of a word.
    ```java
    /**
     * Reverses the letters of each word in the input text while preserving word order.
     * For example: "Hello World" becomes "olleH dlroW"
     *
     * @param text The input text to process
     * @return A new string with each word's letters reversed
     * @throws IllegalArgumentException if the input text is null or empty
     */
    public String reverseLettersInWords(String text) throws IllegalArgumentException {
        // TODO: Implement the letter reversal logic
        return null;
    }
    ```
7. Write a program that counts the occurrences of a certain character in a given string.
    ```java
    /**
     * Counts the number of occurrences of a specific character in the given string.
     *
     * @param inputString the string to search in
     * @param targetChar the character to search for
     * @return the number of occurrences of the target character in the input string
     * @throws NullPointerException if the input string is null
     */
    public static int countCharacterOccurrences(String inputString, char targetChar) throws NullPointerException {
        // TODO: Implement the character counting logic
        return 0;
    }
    ```
8. Write a program that removes all white spaces from the given string.
    ```java
    /**
     * Removes all white spaces from the input string.
     * 
     * @param input the string from which to remove white spaces
     * @return a new string with all white spaces removed
     * @throws NullPointerException if the input string is null
     */
    public static String removeWhiteSpaces(String input) throws NullPointerException {
        // TODO: Implement the white space removing logic
        return null;
    }
    ```
--- 
##### Special Problem Statement
Design a robust product classification hierarchy for an inventory system where:

Products must be classified as exactly one of the following: Electronics, Clothing, or Food.
Each main category must restrict which specific product types can extend/implement it:

Electronics should only allow Smartphone, Laptop, and SmartWatch implementations
Clothing should only allow TShirt, Jeans, and Jacket implementations
Food should only allow Fruit, Vegetable, and PreparedMeal implementations


It should be impossible for developers to create new product types outside these predefined categories.
The system must enforce strong compile-time type checking to prevent unauthorized extensions of the hierarchy.

Requirements

Create a type hierarchy that enforces these strict classification rules
Implement the required classes/interfaces with appropriate attributes
Demonstrate your solution with a test program that:

Creates instances of valid product types
Shows how the system prevents creation of invalid product types
Processes different products appropriately based on their classification.