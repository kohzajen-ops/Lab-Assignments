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
## This is my flowchart:
<img width="121" height="581" alt="Flowchart-WordFrequency drawio" src="https://github.com/user-attachments/assets/f046e11e-9e23-44f9-9282-732616b5fbf6" />

## How I will perform a frequency analysis of a website?
To perform a frequency analysis of a website, I would first extract the site's text using a web scraper or by copying the visible content. After that, I would clean up the data by removing HTML tags and punctuation. Next, I would split the text into individual words and count how often each word appears using a loop. Finally, I would sort and display the results, highlighting the most frequent words.

## Challenges encountered while performing the lab:
During the Word Frequency Lab, I ran into a few challenges like handling case sensitivity so that “Hi” and “hi” counted as the same word, and figuring out how to read input properly without the program getting stuck. I had to debug small syntax errors too, like missing semicolons or parentheses.
