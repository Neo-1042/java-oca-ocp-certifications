# Java Primitive Data Types

1. `boolean` ---> The default value is `false`. (its size in bits depends on the particular JVM)
2. `byte` ---> 8-bit integers: from -128 to +127.
3. `short` ---> 16-bit integers: from -32'768 to +32'767.
4. `int` ---> 32-bit integers: from -2'147'483'648 to +2'147'483'647.
5. `long` ---> 64-bit integers: from -2^63 to 2^63 - 1.
    Number of type `long` are specified = `2026L`
6. `float` ---> 32-bit floating values. (`0.0f`)
7. `double` ---> 64-bit floating values. (`0.0`)
8. `char` ---> 16-bit Unicode value. Min = 0, Max = 65'535.

Note*: In Java, `true` and `false` are NOT related to 1 and 0 (like they are in C).

### Supported Numerical Bases

- Base 10
- Base 8: (Uses `0` as a prefix)
- Base 6: (uses `0x` as a prefix)
- Base 2 (uses `0b` as a prefix)

Java supports underscores for readability:
```java
int a = 1_000_000;
int b = 1_2;
int c = 1___2; // useless, but valid
double d = 1_000_000.000_000; // OK and makes sense
```

# Wrapper Classes

Primitive data types are not Java objects, and sometimes we prefer to work with objects.
Each primitive type has a corresponding **wrapper class**.

The most common way to create an object from a primitive data type is by using the static method: `[WrapperClass].valueOf()`:

```java
// valueOf() is a static method
Integer a = Integer.valueOf(7);
Boolean b = Boolean.valueOf(true);
// Byte c = Byte.valueOf(12); ERROR, you need to use casting:
Byte c = Byte.valueOf((byte) 12);
Short d = Short.valueOf((short) 20);
Long e = Long.valueOf(100L);
Float f = Float.valueOf(17.0F);
Double g = Double.valueOf(100.10);
Character h = Character.valueOf('c');

Integer n = Integer.valueOf("200");
```

Wrapper classes come along useful methods:
```java
int m = Integer.parseInt("1492");
// Before Java 9, this was still possible:
Integer beforeJ9 = new Integer(9); // even then, this was not recommended

// byteValue(), shortValue(), intValue(), floatValue()
// doubleValue(), booleanValue(), charValue()
```

# String and Text Blocks (Java 15)

Java Strings are not primitive data types, but they are so commonly used, that people think of them as "primitives".

```java
String sql = "SELECT * FROM DUAL;";

// Old way:
String oldTitle = "\"Java SE 17 Developer Course\"\n   by LP.";

// New way:
// This is a text block (only from Java 15)
// Mind the incidental vs the essential whitespace
String newTitle = """
    "Java SE 17 Developer Course"
        by Luka Popov.
""";
```