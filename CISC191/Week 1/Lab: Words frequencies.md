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
        String[] words = line.split(" ");

        for (int i = 0; i < words.length; i++) {
            int count = 0;
            for (int j = 0; j < words.length; j++) {
                if (words[i].equalsIgnoreCase(words[j])) {
                    count++;
                }
            }
            System.out.println(words[i] + " " + count);
        }

        sc.close();
    }
}
```
