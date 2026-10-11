# Java Variables

```java
public class DemoVariables {

    public static void main(String[] args) {

        int x; // Declaring a variable.
        x = 10; // Initialize the variable.

        int y = 7; // Declare + initialize the variable.

        // x, y are identifiers, which canNOT start with
        // a number. '_' is not allowed wither
    }
}
```

## Naming Conventions in Java

- camelCase for variables and method names.
- Uppercase SNAKE_CASE for constants.
- `MyClass`, `MyInterface`, `StudentRecord`.

# Three Types of Variables

1. **Local Variables** (Block Scope: `{...}`)
2. **Instance Variables** (Fields, these are defined within the specific instance of the object)
3. **Class Variables**: belong to the class itself and these are shared with all instances of the class.