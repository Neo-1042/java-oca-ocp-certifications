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
Marked with the keyword `static`.

- Instance and Class variables don't require initialization.
Instead, assume the default values of their type.

# Final Variables (constants)

```java
// Mind the SNAKE_CASE:
final int MAX_HEIGHT = 100;

// 'final' can also be applied to a reference:
final int[] MY_NUMBERS = new int[5];
// This reference cannot be modified, but the content of the object can:
MY_NUMBERS = null; // ERROR
MY_NUMBERS[2] = 17; // OK
```

# Variable Scope

Variables can go out of scope, that is, "cease to exist":

1. *Local Variables* have scope within `{...}`
2. *Method Parameters*: in scope during the execution of the method.
3. *Instance Variables*: in scope declaration until the object is eligible for the garbage collector.
4. *Class Variables*: in scope from declaration until the program ends.