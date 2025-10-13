# Exceptions

## Objective
Create Step counter exceptions

## Task
Assignment Code:
```java
import java.util.Scanner;

public class ExceptionsLab {

    public static double stepsToMiles(int steps) throws Exception {
        if (steps < 0) {
            throw new Exception("Exception: Negative step count entered.");
        }
        return steps / 2000.0;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int steps = sc.nextInt();

        try {
            double miles = stepsToMiles(steps);
            System.out.printf("%.2f", miles);
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }
}
```

## This is my flowchart:
<img width="161" height="961" alt="Lab_ Exceptions drawio" src="https://github.com/user-attachments/assets/ca96d129-8420-4fa2-b73a-d9b23134c78d" />

## Challenges encountered while performing the lab:
A silly mistake that took me awhile to notice was that I accidentally used integer division steps / 2000 at first so initially, the fractional miles were lost.
