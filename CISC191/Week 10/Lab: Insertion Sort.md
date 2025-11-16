# Activity: Insertion Sort

## Objective

Write a code and implement insertion sort

## Task
Assignment Code:
```java
import java.util.Scanner;

public class InsertionSortLab {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String input = scanner.nextLine();
        String[] inputArray = input.split(" ");

        int n = inputArray.length;
        int[] array = new int[n];

        for (int i = 0; i < n; i++) {
            array[i] = Integer.parseInt(inputArray[i]);
        }

        int comparisons = 0;
        int swaps = 0;

        for (int i = 1; i < n; i++) {
            int current = array[i];
            int j = i - 1;

            boolean swapped = false;

            while (j >= 0 && array[j] > current) {
                comparisons++;
                array[j + 1] = array[j];
                j--;
                swapped = true;
            }

            if (swapped) {
                array[j + 1] = current;
                swaps++;
            }

            printArray(array);
        }

        System.out.println("comparisons: " + comparisons);
        System.out.println("swaps: " + swaps);
    }

    private static void printArray(int[] array) {
        for (int i = 0; i < array.length; i++) {
            System.out.print(array[i] + " ");
        }
        System.out.println();
    }
}

```
## This is my flowchart:
<img width="121" height="661" alt="InsertionSortLab drawio" src="https://github.com/user-attachments/assets/4869ac66-f024-41d0-b958-189f13553a35" />

## Challenges encountered while performing the lab:
I was missing some spaces between elements when printing the array at first but that error was evident after being printed out so I quickly fixed it.
