# Java Packages

Java classes are stored in different packages, which are
basically folders.
To use a class, you need to import the package into your program. Example:

```java
import java.util.Random;

public class NumberGenerator {

    public static void main(String[] args) {

        Random randomNumber = new Random();
        System.out.println(randomNumber.nextInt(100));
    }
}
```

If you don't want to use an 'import' statement, you could write the fully qualified name of the class:
```java
java.util.Random randomNumber = new java.util.Random();
// import java.util.*; // does not import subpackages
// import java.util.*.*; // ERROR
```

Class Names Conflicts:
```java
import java.util.Date;
import java.sql.Date; // Compilation error
// Instead, you need to use the fully-qualified name.
```

## Custom Packages

```java
package com.udemy.oca;

public class Oca { }
```