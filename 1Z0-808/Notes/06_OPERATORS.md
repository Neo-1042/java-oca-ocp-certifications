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