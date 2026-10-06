# Java Classes

- Classes are the basic building blocks of every Java program.
- Set of properties and behaviors.
- To instantiate a class means to generate an actual object of that class, which is stored in the JVM's heap:  
`MyClass obj = new Myclass();`
- `obj` is the reference that points to that newly-created object.

```java
public class Student {
    private Long id;

    private String name;

    public Student() { }

    public Student (String name) {
        this.name = name;
    }
    // Getters and setters
}
```

- Comments review `//    /* */`
- It is possible to have more than one class in one Java file (only one of them is the **top-level class**), however, it is recommended to have only one class per Java file.
- If you mark the **top-level class** with `public`, then the filename must match the class name.
- Only one class can be `public` in the same file.

## Basic Names.java Program

```java
public class Names {

    // Every Java Program begins by executing the main() method
    // static -> The method belongs to the class, not to any
    // instance of the class.
    public static void main(String[] args) {
        System.out.println("Hello, OCA");
        System.out.println("First Name: " + args[0]);
        System.out.println("Last Name: " + args[1]);
    }
    
    // This syntax is also permissible
    // static public void main(String sillyName[]) { }
}
```

## Compile the program:

```bash
cd /Users/RRHG/projects/Names
# Compile the main class:
javac Names.java # Generates the Names.class
# Run the program:
java Names Rodrigo Hurtado

# If args[] does not match, then -> IndexOutOfBoundsException
```

# Java Objects

```java
private String firstName;

private String lastName;
// If you don't generate any constructor, the compiler will
// generate a simple no-argument constructor:
public Student() { }

public Student(String firstName, String lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}
// Calling the constructor to create a new object:
Student s = new Student("Rodrigo", "Hurtado");

// Setters and Getters
```

# Order of Initialization

- `{...}` code block.
- Instance initializer ---> code block outside the method.
- Order of Initialization:
    1. **Fields** and **instance initializer blocks** in the order in which they appear.
    2. Constructor runs.

```java
public class Dog {

    private String name = "Chip";

    // 2
    public Dog() {
        this.name = "Teddy";
        System.out.println("Inside the constructor...");
    }

    {
        // Initializer block (1)
        System.out.println("Inside the initializer block");
    }

    public static void main(String[] args) {
        // "Inside the initializer block"
        Dog dog = new Dog(); // When this code is run, "Teddy"
        System.out.println(dog.name); // (3) "Teddy"
    }
}
```