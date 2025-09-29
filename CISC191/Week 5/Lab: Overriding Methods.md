# Change contents in a text file

## Objective
Understand how to use overriding methods.

## Task
Assignment Code:

Book.java:
```java
package OverridingMethodsLab;

public class Book {
    private String title;
    private String author;
    private String publisher;
    private String publicationDate;

    public Book(String title, String author, String publisher, String publicationDate) {
        this.title = title;
        this.author = author;
        this.publisher = publisher;
        this.publicationDate = publicationDate;
    }

    public String getTitle() { return title; }
    public String getAuthor() { return author; }
    public String getPublisher() { return publisher; }
    public String getPublicationDate() { return publicationDate; }

    public void printInfo() {
        System.out.println("Book Information: ");
        System.out.println("   Book Title: " + title);
        System.out.println("   Author: " + author);
        System.out.println("   Publisher: " + publisher);
        System.out.println("   Publication Date: " + publicationDate);
    }
}
```

Encyclopedia.java:
```java
package OverridingMethodsLab;

public class Encyclopedia extends Book {
    private String edition;
    private int numberOfPages;

    // Constructor
    public Encyclopedia(String title, String author, String publisher, String publicationDate,
                        String edition, int numberOfPages) {
        super(title, author, publisher, publicationDate);
        this.edition = edition;
        this.numberOfPages = numberOfPages;
    }

    public String getEdition() { return edition; }
    public void setEdition(String edition) { this.edition = edition; }

    public int getNumberOfPages() { return numberOfPages; }
    public void setNumberOfPages(int numberOfPages) { this.numberOfPages = numberOfPages; }

    @Override
    public void printInfo() {
        super.printInfo(); // Print basic book info
        System.out.println("   Edition: " + edition);
        System.out.println("   Number of Pages: " + numberOfPages);
    }
}
```

OverridingMethodsLab.java:
```java
package OverridingMethodsLab;

import java.util.Scanner;

public class OverridingMethodsLab {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String bookTitle = sc.nextLine();
        String bookAuthor = sc.nextLine();
        String bookPublisher = sc.nextLine();
        String bookPubDate = sc.nextLine();
        Book book = new Book(bookTitle, bookAuthor, bookPublisher, bookPubDate);

        String encTitle = sc.nextLine();
        String encAuthor = sc.nextLine();
        String encPublisher = sc.nextLine();
        String encPubDate = sc.nextLine();
        String encEdition = sc.nextLine();
        int encPages = Integer.parseInt(sc.nextLine());
        Encyclopedia enc = new Encyclopedia(encTitle, encAuthor, encPublisher, encPubDate, encEdition, encPages);

        book.printInfo();
        enc.printInfo();

        sc.close();
    }
}
```

## This is my flowchart:
<img width="161" height="881" alt="Lab_ Overriding Methods drawio" src="https://github.com/user-attachments/assets/a67c5607-78c1-4ce8-a4fc-34ac618ae068" />

## Challenges encountered while performing the lab:
I had difficulty managing multiple lines of input, as mixing nextLine() and nextInt() sometimes skipped entries. Additionally, keeping the output format exactly was also a bit tricky.
