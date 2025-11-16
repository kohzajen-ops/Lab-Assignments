# Activity: Merge Sort

## Objective

Write a code and implement merge sort

## Task
Assignment Code:
```java
import java.util.Scanner;

public class MergeSortLab {

    static int comparisons = 0;

    public static void merge(int[] array, int left, int middle, int right) {
        int n1 = middle - left + 1;
        int n2 = right - middle;

        int[] leftArray = new int[n1];
        int[] rightArray = new int[n2];

        System.arraycopy(array, left, leftArray, 0, n1);
        System.arraycopy(array, middle + 1, rightArray, 0, n2);

        int i = 0, j = 0, k = left;
        while (i < n1 && j < n2) {
            comparisons++;
            if (leftArray[i] <= rightArray[j]) {
                array[k] = leftArray[i];
                i++;
            } else {
                array[k] = rightArray[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            array[k] = leftArray[i];
            i++;
            k++;
        }

        while (j < n2) {
            array[k] = rightArray[j];
            j++;
            k++;
        }
    }

    public static void mergeSort(int[] array, int left, int right) {
        if (left < right) {
            int middle = (left + right) / 2;
            mergeSort(array, left, middle);
            mergeSort(array, middle + 1, right);
            merge(array, left, middle, right);
        }
    }

    public static void printArray(int[] array) {
        for (int i = 0; i < array.length; i++) {
            System.out.print(array[i] + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int size = scanner.nextInt();
        int[] array = new int[size];

        for (int i = 0; i < size; i++) {
            array[i] = scanner.nextInt();
        }

        System.out.print("unsorted: ");
        printArray(array);

        mergeSort(array, 0, array.length - 1);

        System.out.print("sorted: ");
        printArray(array);

        System.out.println("comparisons: " + comparisons);
    }
}

```

## This is my flowchart:
<img width="121" height="661" alt="MergeSortLab drawio" src="https://github.com/user-attachments/assets/71699f71-dfbe-42df-bf54-df7c3d8642aa" />

## Challenges encountered while performing the lab:
This one went smoother than the previous lab, I did not run into any major problems, only some minor typos. However, after a few output, I quickly spotted the typos and fixed them.
