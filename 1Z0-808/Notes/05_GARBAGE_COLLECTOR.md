# Java Garbage Collector

All Java objects are stored in the program's memory area called **the heap** (AKA *free store*).
Garbage collection is a process of automatically freeing up memory on the heap by removing objects which are no longer reachable in the program, thus creating space for other objects. Objects are said to be **eligible for garbage collection**.

You cannot force Java to "collect garbage". You can ask for it, but ultimately, the JVM will decide when it is time to collect the garbage. You cannot know if or when the memory will be freed.

```java
System.gc(); // Only a suggestion
```

Example

```java
public class gcExample {
    public static void main(String[] args) {

        String a,b;
        a = new String("Emperor");
        b = new String("King");

        a = b; // "Emperor" has no reference, thus eligible for gc
        String c = a; // c points to "King"
        a = null; // 'a' points to nowhere.
    }
}
```

**References** live in the **Stack**.  
**Objects** live in the **Heap**.

<u>Important:</u> OBJECTS are collected by the GC (not references).