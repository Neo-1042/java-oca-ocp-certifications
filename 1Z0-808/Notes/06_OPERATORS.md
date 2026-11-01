# Operators in Java

We have three main types:

1. Unary Operators (e.g. `a++`)
2. Binary Operators (e.g. `x*y`)
3. Ternary Operator  
`a = ( b >= 0 ) ? 3 : -3; `

## Operator Precedence

(i) Unary operators go first, then  
(ii) Binary mathematical operators  
(iii) Relational and logical operators  
(iv) Ternary Operator  
(v) Assignment Operator  
(vi) Arrow Operator (`->`)

Exercises:

```java
boolean b = 2>1&&2+2*2==5;
// Is equivalent to:
b = (2 > 1) && (2+(2*2) == 5);
b = true && (6 == 5);
b = true && false;
b = false;

int x = 1;
int y = ++x*2;
y = (++x)*2;
y = 4, x = 2;
```

## Unary Operators

- auto-increment/decrement: `a++`, `++a`, `a--`, `--a`
- Logical complement: `!b`
- Bitwise complement: `~a` (flips `0 <-> 1`)
- Casting `(int) a`

### Increment and Decrement Operators

```
++a ---> Increases the value by 1 and then returns the NEW value.
a++ ---> Increases the value by 1 and returns the OLD value.
```

Examples:

```java
int a = 3;
int b = 3;
a = ++a; // a == 4
b = b++; // b == 3

int c = 5;
int d = c++;
System.out.prinln("c = " + c); // 6
System.out.prinln("d = " + d); // 5 (old value)
```

```java
int a = 5;
a = a++; // returns 5, thus, a -> 5
System.out.println("a = " + a); // a = 5
```

# Two-argument Operators

- Addition, substraction, multiplication, division, modulo (`a % b`).

# Rules of Numeric Promotion

1. If the operands have different data types, Java automatically promotes one of them to the larger one.

2. If one value is an integer and the second value is a rational number, Java promotes int -> decimal (`float` or `double`).

3. `byte`, `short` and `char` are always first promoted to `int` before the operation is done.

4. The resulting value has the same data type as the promoted operands.

```java
// Example 1
short a = 17;

float b = 15; // b ==> 15.0

double c = 35; // largest type.

System.out.println(a * b / c);
// 'a' and 'b' are promoted to double, the result is then a double.
// result ==> 7.285714285714286

short x = 5;
short y = 7;
short result = x+y; // ERROR, INCOMPATIBLE TYPES.
// short + short ---> INT
System.out.println(x+y);
// x and y are promoted to int, the result is thus an int.
```

# Assignment Operator

The assignment operator (`=`) has the lowest precedence.

- Auto-casting: Java automatically promotes smaller to larger data types when performing operations.

```java
short x = 5;
int y;
y = x; // OK, x is automatically casted into int.

int a = 5;
short b;
b = a; // ERROR. a short variable cannot be assigned to an int variable.

// SOLUTION: Explicit cast
b = (short) a; // OK

// int x = 1.0; // ERROR
// int y = 123L; // ERROR
long z = 5; // OK. int -> long
long w = (byte) 7; // OK. byte -> long
// float k = 2.3; // ERROR. double -> float WRONG
float k = 2.3f; // OK
float m = 3.7f; // OK
double pi = 3.141592; // OK
////////////////////////////////////////////////////
short a = 7:
short b = 5;
// short c = a+b; // Wrong. int -> short
short c = (short) (a+b); // OK
```

## Compound Assignment Operators

```java
a += 5; // a = a + 5;
a -= 5; // a = a - 5;
a *= 5; // a = a * 5;
a /= 5; // a = a / 5;
```

# Return Value of the Assignment Operator

- The expression `a = 10;` does two things:
    - Assigns the value `10` to the variable `a`.
    - Returns the value `10` (to the program execution).

## Exam Tricky Examples:

```java
int x = 5;
int y = (x = 3) * 2; // 3*2, y ==> 6
```

```java
// Favorite exam trick

boolean isOK = false;
if (isOK = true) {
    System.out.println("A"); // THIS IS THE RESULT
} else {
    System.out.println("B");
}

System.out.println("The value that is stored in 'isOK' is --> " + isOK);
// isOK is assigned to true and the output of this logical evaluation is "true". Thus, "A" is printed
```