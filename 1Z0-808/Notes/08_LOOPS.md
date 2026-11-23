# `while` loop in Java

```java
while(condition) {
    // While the condition is true, this code will be executed
}
```

Let's study a more interesting example. In hardware, `while` loops are everywhere, since they continuously monitor sensors, motors, and temperatures **until a target state is reached**.

Let's give our Blu-Ray player an interesting hardware job: **auto-focusing** the laser lens when a disc is first inserted.

```java
public class OpticalLensFocuser {

    private static final int TARGET_FOCUS_SCORE = 98;
    private static final int MAX_ATTEMPTS = 25;

    public boolean focusLaserOnDisc() {

        int focusScore = readFocusSensor(); // 0 : blurry to 100 : razor sharp
        int lensPositionMicrons = 0; // Physical height of the lens
        int attempts = 0;

        // Keep nudging the lens as long as the image isn't sharp enough
        // AND we are still within the MAX_ATTEMPTS limit
        while (focusScore < TARGET_FOCUS_SCORE && attempts < MAX_ATTEMPTS) {
            lensPositionMicrons += 10; // Move the lens 10 micrometers closer/up
            moveLensActuator(lensPositionMicrons);

            waitMicroseconds(150); // let the physical vibration settle
            focusScore = readFocusSensor();
            attempts++;
        }

        if(focusScore >= TARGET_FOCUS_SCORE) {
            System.out.println("Focus locked at " + lensPositionMicrons + "micrometers");
            return true;
        } else {
            System.out.println("Could not focus: disc may be scratched or warped.");
            return false;
        }
    }

    // Hardware sensor & actuator stubs
    private int readFocusSensor() { return 40; }
    private void moveLensActuator(int microns) { }
    private void waitMicroseconds(int microseconds) { }

}
```

Inside an optical pickup unit, the tiny glass objective lens is not glued in place; it floats on flexible suspension wires and is pushed up and down by **electromagnetic coils** (similar in principle to a tiny speaker).