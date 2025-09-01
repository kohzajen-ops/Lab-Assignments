# Lab: Sorting

## Objectives
Sort an array 

## Assignment Code
```Java
import java.util.Scanner;

public class SortArrayLab {
    public static void sortArray(int[] myArr, int arrSize) {
        for (int i = 0; i < arrSize - 1; i++) {
            for (int j = 0; j < arrSize - i - 1; j++) {
                if (myArr[j] < myArr[j + 1]) {
                    int temp = myArr[j];
                    myArr[j] = myArr[j + 1];
                    myArr[j + 1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int arrSize = sc.nextInt();
        int[] myArr = new int[arrSize];

        for (int i = 0; i < arrSize; i++) {
            myArr[i] = sc.nextInt();
        }

        sortArray(myArr, arrSize);

        for (int i = 0; i < arrSize; i++) {
            System.out.print(myArr[i]);
            if (i < arrSize - 1) {
                System.out.print(",");
            }
        }
    }
}
```
