# Derived classes

## Objective
Use inheritance to store user data.

## Task
Assignment Code:

Course.java:
```java
package DerivedClassesLab;

class Course {
    private String courseNumber;
    private String courseTitle;

    public void setCourseNumber(String number) {
        courseNumber = number;
    }

    public void setCourseTitle(String title) {
        courseTitle = title;
    }

    public String getCourseNumber() {
        return courseNumber;
    }

    public String getCourseTitle() {
        return courseTitle;
    }

    public void printInfo() {
        System.out.println("Course Information:");
        System.out.println("   Course Number: " + courseNumber);
        System.out.println("   Course Title: " + courseTitle);
    }
}
```

OfferedCourse.java:
```java
package DerivedClassesLab;

class OfferedCourse extends Course {
    private String instructorName;
    private String location;
    private String classTime;

    public void setInstructorName(String name) {
        instructorName = name;
    }

    public void setLocation(String loc) {
        location = loc;
    }

    public void setClassTime(String time) {
        classTime = time;
    }

    public String getInstructorName() {
        return instructorName;
    }

    public String getLocation() {
        return location;
    }

    public String getClassTime() {
        return classTime;
    }

    @Override
    public void printInfo() {
        super.printInfo();
        if (instructorName != null && location != null && classTime != null) {
            System.out.println("   Instructor Name: " + instructorName);
            System.out.println("   Location: " + location);
            System.out.println("   Class Time: " + classTime);
        }
    }
}
```

DerivedClassesLab.java:
```java
package DerivedClassesLab;

import java.util.Scanner;

public class DerivedClassesLab {
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);

        String c1Number = scnr.nextLine();
        String c1Title = scnr.nextLine();

        String c2Number = scnr.nextLine();
        String c2Title = scnr.nextLine();

        String instrName = scnr.nextLine();
        String loc = scnr.nextLine();
        String time = scnr.nextLine();

        Course c1 = new Course();
        c1.setCourseNumber(c1Number);
        c1.setCourseTitle(c1Title);

        OfferedCourse c2 = new OfferedCourse();
        c2.setCourseNumber(c2Number);
        c2.setCourseTitle(c2Title);
        c2.setInstructorName(instrName);
        c2.setLocation(loc);
        c2.setClassTime(time);

        c1.printInfo();
        c2.printInfo();
    }
}
```

## This is my flowchart:
<img width="121" height="681" alt="Lab_ Derived Classes drawio" src="https://github.com/user-attachments/assets/885130e0-8ee5-456b-9d96-8e719d6572bb" />


## Challenges encountered while performing the lab:
A challenge that I had during the lab was making sure the program printed the information in the exact format expected, since even a small difference in spaces or line breaks could cause the output to be marked incorrect. Another challenge was organizing the code into the right classes and keeping the public class name matched to the file name was important to avoid compilation errors. 
