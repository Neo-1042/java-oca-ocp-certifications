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