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