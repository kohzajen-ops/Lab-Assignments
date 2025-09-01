# Lab: Words frequencies

## Objectives:
Count number of words

## Assignment Code:
```Java
import java.util.Scanner;

public class WordFrequency {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String line = sc.nextLine(); 
        String[] wordsList = line.split(" "); 
        int listSize = wordsList.length;

        for (int i = 0; i < listSize; i++) {
            int freq = getWordFrequency(wordsList, listSize, wordsList[i]);
            System.out.println(wordsList[i] + " " + freq);
        }

        sc.close();
    }

    public static int getWordFrequency(String[] wordsList, int listSize, String currWord) {
        int count = 0;
        for (int i = 0; i < listSize; i++) {
            if (wordsList[i].equalsIgnoreCase(currWord)) {
                count++;
            }
        }
        return count;
    }
}
```
