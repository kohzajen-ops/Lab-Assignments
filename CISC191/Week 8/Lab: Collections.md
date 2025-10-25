# Collections

## Objective
Identify palindrome and implement using deque

## Task
Assignment Code:
```java
import java.util.Deque;
import java.util.LinkedList;
import java.util.Scanner;

public class CollectionsLab {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter a string to check if it is a palindrome:");
        String input = scanner.nextLine();

        System.out.println(isPalindrome(input));

        scanner.close();
    }

    public static String isPalindrome(String input) {
        String cleanedInput = input.replaceAll("[^a-zA-Z]", "").toLowerCase();
        Deque<Character> deque = new LinkedList<>();

        for (char ch : cleanedInput.toCharArray()) {
            deque.add(ch);
        }

        while (deque.size() > 1) {
            if (deque.pollFirst() != deque.pollLast()) {
                return "No, \"" + input + "\" is not a palindrome.";
            }
        }

        return "Yes, " + input + " is a palindrome.";
    }
}
```

## This is my flowchart:
<img width="321" height="961" alt="CollectionsLab drawio" src="https://github.com/user-attachments/assets/a2687b51-7b59-4b41-beb8-da8dcc1b061a" />

## Challenges encountered while performing the lab:
I encountered a few challenges during this lab, the first problem is making sure that the program treats characters as case-insensitive. The other problem is making sure the input string can contain spaces, punctuation, or numbers, which shouldn't affect whether the string is a palindrome or not.
