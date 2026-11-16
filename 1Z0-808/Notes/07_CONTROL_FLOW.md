# `if-else` Statement. Blu-Ray Player Example.

When you insert a disc into the Blu-Ray Player, the hardware must determine what kind of dic it is (Blu-Ray, DVD or CD) so it can activate the correct internal laser. Blu-Ray discs require a blue laser, DVDs require a red laser and CDs require an infrared laser. 

```java
public class OpticalDriveController {

    public void processDisc(int detectedWavelength) {

        // Check if the disc requires a 405 nanometer(blue) laser
        if (detectedWavelength == 405) {
            activateBlueLaser();
            setMotorSpeed(10000); // High speed for high-density data
            System.out.println("Blu-Ray detected: HD Video mode ready");

            // If not a Blu-Ray, check if a red laser (650 nm) is required
        } else if (detectedWavelength == 650) {
            activateRedLaser();
            setMotorSpeed(5000); // spin at a medium speed
            System.out.println("DVD detected: Standard Video mode ready");

            // If nether above, check if an infrared laser (780) is required
        } else if (detectedWavelength == 780) {
            activateInfraredLaser();
            setMotorSpeed(2000); // Spin slowly for simple audio data
            System.out.println("CD detected: Audio mode ready");

            // If none of the specific wavelengths match, handle the error:
        } else {
            turnOffLasers();
            stopMotor();
            displayScreenError("Unrecognized disc format.");
        }
    }

    // Hardware control methods, such as "activateBlueLaser()" would be defined down here.
}
```

# Switch Case: Disc Recognition and Laser Calibration

- Pattern Matching

Here is how a Java 21+ program might handle disc recognition and laser calibration:

```java
// Define what kinds of physical media our player understands (Sealed hierarchy)
public sealed interface Disc permits BluRay, DVD, CD, BlankDisc {}

record BluRay(int capacityGB, boolean isDualLayer) implements Disc {}
record DVD(boolean isDoubleSided) implements Disc {}
record CD() implements Disc {}
record BlankDisc() implements Disc {}

public class AdvancedOpticalDrive {

    public void configureDrive(Disc disc) {

        // Modern Java Switch Expression with Pattern Matching
        String status = switch (disc) {

            case BluRay b when b.isDualLayer() -> {
                activateBlueLaser(405);
                setMotorSpeed(12000);
                yield "Dual-Layer Blu-Ray: High Capacity HD mode active";
            }
            // Check for a standard Single-Layer Blu-Ray
            case BluRay b -> {
                activateBlueLaser(405);
                setMotorSpeed(10000);
                yield "Standard Blu-Ray: HD mode active.";
            }
            // Check for double-sided DVDs:
            case DVD d when d.isDoubleSided() -> {
                activateRedLaser(650);
                setMotorSpeed(6000);
                yield "Double-sided DVD: Standard video mode active";
            }
            case DVD d -> {
                activateRedLaser(650);
                setMotorSpeed(5000);
                yield "Standard DVD: Video mode active";
            }
            case CD c -> {
                activateInfraredLaser(780);
                setMotorSpeed(2000);
                yield "CD: Audio playback mode active.";
            }
            case BlankDisc b -> {
                turnOffLasers();
                setMotorSpeed(0);
                yield "Blank disc detected. Ready for burning.";
            }
            // Safe handling for null values or completely unknown objects
            case null, default -> {
                turnOffLasers();
                stopMotor();
                yield "Error: Unrecognized or corrupted media format";
            }
        };

        System.out.println(status);
    }

    // Hardware control STUB
    // Un 'stub' es un módulo de código temporal y simplificada que simula el comportamiento de un dispositivo físico.
    // Se usan para desarrollo y pruebas cuando el hardware real aún no está disponible
    private void activateBlueLaser(int nm) {}
    private void activateRedLaser(int nm) {}
    private void activateInfraredLaser(int nm) {}
    private void setMotorSpeed(int rpm) {}
    private void stopMotor() {}
    private void turnOffLasers() {}
}
```

## Modern Java 21+ Features

- **Sealed Interfaces and Records** --> These define rigid data structures. A `Disc` can only be one of the explicitly permitted types (`Blu-Ray`, `DVD`, `CD`, `BlankDisc`), keeping the hardware logic secure and predictable.

- **Pattern Matching in `switch`** --> Instead of checking primitive numbers, Java directly inspects the **type** of the disc object (`case BluRay b`). It automatically extracts the object into a variable (`b`) so you can inspect its internal properties instantly.

- **The `when` Guard** --> These act as secondary filters. For example, `case BluRay b when b.isDualLayer()` means: "Match this branch only if it's a Blu-Ray and its dual-layer property is true."

- **Arrow Syntax (`->`) and `yield`** --> Modern switch blocks use arrows to avoid the old bug of "fall-through" (where code accidentally leaked into the next case). The `yield` keyword sends a resulting text string out of the code block directly into the `status` variable.

- **Safe `null` Handling**: older Java switches would crash with a `NullPointerException` if you passed a `null` object. Java 21 allows you to combine `case null, default` cleanly to handle empty tray slots or missing data safely.

### "Fall-through" `switch`

In older Java, C, C++ and JavaScript, the `switch` statement acts like a multi-lane highway without stop signs.
By default, once Java finds a matching `case`, it executes that code and then keeps sliding straight down into every subsequent case until it finally hits a `break;` statement or the end of the block. This is known as `fall-through`.

This bugs is presented whenever `break;` statements are not properly written or not written at all.