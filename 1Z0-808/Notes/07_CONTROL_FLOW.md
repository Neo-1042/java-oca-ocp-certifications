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