# Inheritance

## Objective
Understand how subclasses and derived from the superclass.

## Task
Assignment Code:
```java
// ===== Code from file Person.java =====
public class Person {
   private int ageYears;
   private String lastName;

   public void setName(String userName) {
      lastName  = userName;
   }

   public void setAge(int numYears) {
      ageYears = numYears;
   }

   // Other parts omitted

   public void printAll() {
      System.out.print("Name: " + lastName);
      System.out.print(", Age: "  + ageYears);
   }
}
// ===== end =====

// ===== Code from file Student.java =====
public class Student extends Person {
   private int idNum;

   public void setID(int studentId) {
      idNum = studentId;
   }

   public int getID() {
      return idNum;
   }
}
// ===== end =====

// ===== Code from file StudentDerivationFromPerson.java =====
package InheritanceLab;

public class StudentDerivationFromPerson {
    public static void main(String[] args) {
        Student courseStudent = new Student();

        courseStudent.setName("Smith");
        courseStudent.setAge(20);
        courseStudent.setID(9999);

        courseStudent.printAll();
        System.out.println(", ID: " + courseStudent.getID());
    }
}
// ===== end =====
```

## Expected output
```Name: Smith, Age: 20, ID: 9999```

## This is my flowchart:
<img width="121" height="461" alt="Lab_ Inheritance drawio" src="https://github.com/user-attachments/assets/3cfc7c35-2fbb-490b-959f-a0aa1752ac08" />


## Challenges encountered while performing the lab:
I kept forgetting that Student inherits the methods from Person, so I was trying to write new setters for name and age inside Student.java instead of just using the ones already there.  
