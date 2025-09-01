# Lab: Sorting

## Objectives:
Sort an array 

## Assignment Code:
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

## This is my flowchart:
<img width="201" height="691" alt="Flowchart-Sorting drawio" src="https://github.com/user-attachments/assets/460a4270-0823-4e6d-9298-f30a4b14a893" />

## Why did I choose Bubble Sort?
As the assignment suggested, some believe the simplest to code is bubble sort which I believe is a good way to start. I also believe that bubble is easy to understand and implement and with a small dataset of 20 elements, it is a great choice. Moreoever, bubble sort is great for explaining in a flowchart.

## Challenges encountered while performing the lab:
For me, one of the biggest challenges was remembering all the little details such as like putting semicolons between code line, or making sure every opening parenthesis had a matching closing one. It was easy to forget a semicolon or misplace a bracket, which could break the whole program.


