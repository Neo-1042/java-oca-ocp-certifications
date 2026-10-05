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